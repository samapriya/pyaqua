# pyaqua: Simple CLI for Aqualink API

[![Twitter URL](https://img.shields.io/twitter/follow/samapriyaroy?style=social)](https://twitter.com/intent/follow?screen_name=samapriyaroy)
[![Hits-of-Code](https://hitsofcode.com/github/samapriya/pyaqua?branch=main)](https://hitsofcode.com/github/samapriya/pyaqua?branch=main)
[![CI pyaqua](https://github.com/samapriya/pyaqua/actions/workflows/package_ci.yml/badge.svg)](https://github.com/samapriya/pyaqua/actions/workflows/package_ci.yml)
![PyPI - License](https://img.shields.io/pypi/l/pyaqua)
![PyPI](https://img.shields.io/pypi/v/pyaqua)
[![Downloads](https://pepy.tech/badge/pyaqua/month)](https://pepy.tech/project/pyaqua)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6562816.svg)](https://doi.org/10.5281/zenodo.6562816)


Aqualink is a philanthropic engineering organization working on building ocean conservation technology. Read more about their [inspiration, smart buoy, and web application](https://aqualink.org/about). This tool is designed to help interact programmatically with the [Aqualink.org map](https://aqualink.org/map) and is not based on any official API so expect features to break once in a while. This tool is designed for only only those sites associated with a spotter or a hobo sensor.

Disclaimer: This is an unofficial tool. Is not licensed or endorsed by Aqualink org. It is created and maintained by Samapriya Roy.

#### Citation

```
Samapriya Roy. (2022). samapriya/pyaqua: Simple CLI for Aqualink Org (0.0.9).Zenodo.
https://doi.org/10.5281/zenodo.6562816
```

Readme Docs [available online](https://samapriya.github.io/pyaqua)

## Table of contents
* [Installation](#installation)
* [Getting started](#getting-started)
* [pyaqua Simple CLI for Aqualink API](#pyaqua-simple-cli-for-aqualink-api)
    * [site list](#site-list)
    * [site-alert](#site-alert)
    * [site info](#site-info)
    * [site live](#site-live)
    * [site-daily](#site-daily)
    * [site-timeseries](#site-timeseries)
    * [site-argo](#site-argo)

## Installation
This assumes that you have native python & pip installed in your system, you can test this by going to the terminal (or windows command prompt) and trying

```python``` and then ```pip list```

**pyaqua only support Python v3.7 or higher**

To install **pyaqua: Simple CLI for Aqualink API** you can install using two methods.

```pip install pyaqua```

or you can also try

```
git clone https://github.com/samapriya/pyaqua.git
cd pyaqua
python setup.py install
```
For Linux use sudo or try ```pip install pyaqua --user```.

I recommend installation within a virtual environment. Find more information on [creating virtual environments here](https://docs.python.org/3/library/venv.html).

## Getting started

As usual, to print help:

```
usage: pyaqua [-h] {site-list,site-info,site-live,site-daily,site-timeseries} ...

Simple CLI for Aqualink API

positional arguments:
  {readme,site-list,site-alert,site-info,site-live,site-daily,site-timeseries,site-argo}
    readme              Go to the web based pyaqua readme page
    site-list           Print lists of Site Name and ID with spotters
    site-alert          Print site alerts for sites with spotters
    site-info           Print detailed information for a site
    site-live           Get most recent/live info from a site
    site-daily          Print daily data info for a site
    site-timeseries     Exports timeseries data for a site
    site-argo           Exports coincident argofloat data for a site

optional arguments:
  -h, --help            show this help message and exit
```

To obtain help for specific functionality, simply call it with _help_ switch, e.g.: `pyaqua site-live -h`. If you didn't install pyaqua, then you can run it just by going to *pyaqua* directory and running `python pyaqua.py [arguments go here]`

## pyaqua Simple CLI for [Aqualink API](aqualink.org)
The tool is designed to interact with the Aqualink.org API, for now this is focused only on the all device endpoints (spotter & hobo sensors) including satellite only sites.

### site list
This allows you to get existing sites with spotters or hobo sensors and print Site Name and ID. These could be in different status of application including maintenance, deployed, lost, shipped and so on. The tool also applies a fuzzy search and allows you to look for a specific site to get site id. You can now filter using status as well so status types like maintenance, deployed, shipped or lost

![site_list](https://user-images.githubusercontent.com/6677629/168004255-968e5320-c53d-460c-b230-3a6dc75dfa6e.gif)


### site alert
The site alert tool parses data from each device type or all sites keeping in consideration the temperature alert level data.

![site_alert](https://user-images.githubusercontent.com/6677629/168003775-d9369380-791e-4462-b1c9-fc7211c77d2a.gif)


### site info
The site info tool uses the site ID to get detailed information about the setup, location, time zone, status information to name a few. Historical means are dropped along with admin data for ease of parsing and since they do not add a large amount of value for general purpose users directly. The user does have the option to get to the complete admin or historical data if needed

![site-info](https://user-images.githubusercontent.com/6677629/145769759-9c09dab3-4b45-472a-a62c-2d327ea2255c.gif)

### site-live
This allows to get the most updated/live information about a site based on a site ID from the idlist. The tool parses the output as an indent JSON object.

![site_live](https://user-images.githubusercontent.com/6677629/145728182-db54c3ce-3a4d-4b45-852b-5c1ae5a97376.gif)

### site daily
This allows to get the most daily data for a site based on a site ID from the idlist. The tool parses the daily output as an indented JSON and you can specify months since today as well as data type like wind/wave/temp.

![site_daily](https://user-images.githubusercontent.com/6677629/145728380-11b0acaf-8a9c-4c90-904a-675f8364a5f6.gif)

### site timeseries
This allows to get the most daily data for a site based on a site ID from the idlist. The tool exports the time series data for both NOAA and spotter datasets as CSV to a given folder. It attaches the site_id to the CSV filename **spotter_dhw_siteid** for example **spotter_dhw_1113**

![site_timeseries](https://user-images.githubusercontent.com/6677629/145728547-c724f911-4301-4887-a9e8-dbbce4b28174.gif)

### site argo
This tool uses the argofloats CLI to get coincident argofloats data per site. It uses the start and end date specified and a search radius around the site latitude and longitude. Default search radius is a 1000 kilometers and the exports are in a CSV format with format **argofloats_profileID**

![pyaqua_site-argo](https://user-images.githubusercontent.com/6677629/152304351-0375871b-e80e-46f5-a74b-56c76f094c9a.gif)


### Changelog

#### v0.0.9
- now includes support for hobo sensors
- added site list filter for device type breakdown
- modified site alert tool to pull from all sites and by device type
- general improvements

#### v0.0.8
- added site-argo tool for argofloat exports for sites

#### v0.0.7
- added readme tool to CLI for browser redirect

#### v0.0.6
- added site alert tool

#### v0.0.5
- added status filter to site-list tool
- added lat long for site-timeseries export

#### v0.0.4
- Fixed tool descriptor for timeseries tool.

#### v0.0.3
- Added site info tool for detailed information on site.

#### v0.0.2
- Added readme and created new branch.
