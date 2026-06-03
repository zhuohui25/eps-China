---
title: Technical note of Start Year Capacity
author: Zhuohui Huang
tags: [technical note]
data: 2026-06-02   

---

# Abstract

# US Model

## Data source

The US model uses the [EIA Form 860 ](https://www.eia.gov/electricity/data/eia860m/) to extract the Summer Capacity in Column V, disaggregated by vintage year and plant technology. 

## Method

The US model uses the Summer Capacity as the benchmark of Start Year Capacity. The choice of Summery Capacity rather than Nameplate Capacity is because the Summer Capacity reflects the maximum electricity load a generator can support at the point of interconnection with the electricity transmmission and distribution system, and the Nameplate Capaicity is determined by the generator's manufacturer and indicates the theoritical maximum output within the design thermal limits. [What is the difference between electricity generation capacity and electricity generation?](https://www.eia.gov/tools/faqs/faq.php?id=101&t=3)

The Vintage Year covers from 1891 to 2020.

The plant technologies include biomass, geothermal, hard coal, hydro, lignite, municipal solid waste, natural gas combined cycle, natural gas peaker, natural gas steam turbine, nuclear, offshore wind, onshore wind, solar PV, solar thermal, petroleum, and others.

## Targeted Plant Technology

The technologies in the EPS model contain hard coal, natural gas steam turbine, natural gas combined cycle, nuclear, hydro, onshore wind, solar PV, solar thermal, biomass, geothermal, petroleum, natural gas peaker, lignite, offshore wind, *crude oil*, *heavy or residual fuel oil*, municipal solid waste, *hard coal w CCS, natural gas combined cycle w CCS, biomass w CCS, lignite w CCS, small modular reactor, hydrogen combustion turbine ,hydrogen combined cycle*

# China Model

## Data Source

- [China Electricity Council Electricity Statistics]([年度数据](https://cec.org.cn/menu/index.html?217, "中电联电力统计基本数据")

- China Electric Power Statistical Yearbook

- National Energy Administration - Renewable energy grid connection status in [2024](https://www.nea.gov.cn/20250221/e10f363cabe3458aaf78ba4558970054/c.html) and [2025](https://www.nea.gov.cn/20260212/742b8c6a078347b0b39de676c05c5d58/c.html)

- Offshore Wind (2013-2023): China Wind Energy Council - Global Offshore Wind Power Industry Chain Development Report

- EMBER Electricity Data Explorer - [Installed Capacity by Fuel](https://ember-energy.org/data/electricity-data-explorer/)

## Method

The China Model uses the "installed capacity" in the statistic yearbooks to represent the Start Year Capacity.

The availabe plant technologies include hard coal, natural gas, petroleum, biomass, nuclear, wind (2013-2025 with onshore and offshore wind), solar PV, solar thermal, and hydro w/o pumped storage.

From 2000 to 2008, China model directly quotes the EMBER data for all technology except the biomass and MSW

From 2009 to 2025, China model uses the data from CEC, NEA and CWEA.

<mark>**Data processing for Biomass and MSW**</mark>: 

- China model directly uses the CEC's data from 2009 to 2019, which provided dissaggregated biomass and MSW that larger than 6MW. 

- China model uses the YoY absolute change between 2008 and 2009, to calculate the data of 2008.

- China model allocates the combined data from 2020 to 2025, as per the ratio of biomass and MSW in 2019, since CEC and NEA only provided combined capacity for biomass and MSW after 2020,. 

**<mark>Data processing for hard coal, gas, and petroleum</mark>**: 

- China model calculates the total capacity of hard coal, gas and petroleum based on their share in thermal larger than 6MW from 2009 to 2012. Because CEC's offered the capacity of total thermal, thermal larger than 6MW (including coal, gas, petroleum, biomass and MSW).

- From 2013 to 2023, China model directly uses the CEC's data.

- For 2024 and 2025, China model uses NEA's data to calculate the capacity of coal and gas as per their shares in thermal in last year.

## Technology Mapping

To align with the data structure of the US model, the Chinese model split or merged the data for each technology.

| Available from China Data | Target to EPS model              |
|:------------------------- |:-------------------------------- |
| Hard coal                 | Hard coal - 100%                 |
|                           | Hard coal w CCS - 0%             |
| Natrual gas               | Natural gas steam turbine - 0%   |
|                           | Natural gas combined cycle - 70% |
|                           | Natural gas peaker - 30%         |
| Petroleum                 | Petroleum                        |
| Biomass >6MW plant        | Biomass                          |
| Solar                     | Solar PV - 100%                  |
|                           | Solar Thermal - 0% (only 2025)   |
| Onshore Wind              | Onshore Wind                     |
| Offshore Wind             | Offshore Wind                    |
| Nuclear                   | Nuclear - 100%                   |
|                           | Small modular reactor - 0%       |
| Hydro w/o pumped storage  | Hydro                            |
| *N/A*                     | ~~Geothermal~~                   |
| *N/A*                     | ~~Lignite~~                      |
| *N/A*                     | ~~Crude oil~~~                   |
| *N/A*                     | ~~Heavy or residual fuel oil~~~  |
| *N/A*                     | ~~Biomass w CCS~~~               |
| *N/A*                     | ~~Lignite w CCS~~~               |
| *N/A*                     | ~~Hydrogen combustion turbine~~~ |
| *N/A*                     | ~~Hydrogen combined cycle~~~     |
