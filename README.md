## Overview ##

A Docker Container to read metrics from a Fritzbox and place them into an influx db (via telegraf). Initially based on the work of this (repo)[https://github.com/harmjan/fritzbox-metrics] by user (harmjan)[https://github.com/harmjan].

## Enviroment Variables

Following variables must be set:

FRITZ_ADDRESS=*YOUR-FB-IP*  
FRITZ_USERNAME=*YOUR-FB-MONITORING-USER*  
FRITZ_PASSWORD=*YOUR-FB-MONITORING-USER-PASSWD*  
FRITZ_TYPE=cable *(or dsl)*  
FRITZ_USE_TLS=False  
TELEGRAF_HOSTNAME=*YOUR-TELEGRAF-HOST*  
TELEGRAF_PORT=8092  
INFLUX_METRIC=Fritzbox  
SAMPLE_PERIOD=60  

Following variables can be set (below shows their default value)

PRINT_DATA=false
FRITZ_USE_TLS=false

## Telegraf Setup

I use the follwing section in my telegraf.conf:

    ##############
    # FB-Metrics #
    ##############
    [[inputs.socket_listener]]
      service_address = "udp://:8092"
      data_format = "influx"

