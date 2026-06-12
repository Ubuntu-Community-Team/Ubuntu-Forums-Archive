---
title: "migrating app from upstart to systemctl failing with 'dead'"
date: 2023-11-19
forum: Ubuntu Application Development
---

### Post by nmparmar on 2023-11-19
hi, 

new to this area, and trying to setup this project on Ubuntu 20.04.6 LTS

[https://github.com/thoukydides/heatmiser-wifi](https://github.com/thoukydides/heatmiser-wifi)

the project is no longer maintained, but the instructions talk about using upstart to register a daemon. I understand that upstart is deprecated and is replaced by systemctl. I have setup a systemctl file as below based on the current upstart file.

> [Unit]
Description=HeatmiserDaemon
After=mysql.service

[Service]
ExecStart=/usr/bin/perl /usr/local/bin/heatmiser_daemon

[Install]
WantedBy=multi-user.target

I have saved this to /etc/systemd/system/heatmiser-daemon.service, and am able to register the service and start it. Checking its status shows the following: 

> heatmiser-daemon.service - HeatmiserDaemon     Loaded: loaded (/etc/systemd/system/heatmiser-daemon.service; enabled; vendor preset: enabled)     Active: inactive (dead) since Sun 2023-11-19 15:41:40 UTC; 15s ago    Process: 2213 ExecStart=/usr/bin/perl /usr/local/bin/heatmiser_daemon (code=exited, status=0/SUCCESS)   Main PID: 2213 (code=exited, status=0/SUCCESS)

However, upon querying the running services, it is not shown. It is shown when I run systemctl --type=service --state=dead as below:

  heatmiser-daemon.service                     loaded    inactive dead HeatmiserDaemon


So it seems to me that the service is running and calling the related .pl file, but that is exiting. 

I'm at a point where I'm not sure how to troubleshoot further, so asking for suggestions on if there are any log files etc that can help me to see what the daemon is doing. The app log file doesn't give any help either at this point. 

Any suggestions or pointers welcome. 

thanks

---

