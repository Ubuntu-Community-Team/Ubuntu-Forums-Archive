---
title: "Run script on shutdown via systemd on 16.04LTS"
date: 2017-07-07
forum: Server Platforms
---

### Post by jager966 on 2017-07-07
Hi all,

On a 16.04LTS AWS ec2 instance I am;
[LIST]
[*]running one script as my instances comes into service. 
[*]attempting (but seemingly failing) to run a script as my instances terminate. 
[/LIST]

After upgrading from 14.04LTS and trying to be a good Ubuntu citizen, I have been trying to make this happen with systemd, rather than SysV.
I used this helpful person's guide;

[http://userscripts4systemd.blogspot.com.au/](http://userscripts4systemd.blogspot.com.au/)

Startup service;

```
[Unit]
Description=Start sequence

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/root/start.sh

[Install]
WantedBy=multi-user.target
```


Shutdown service;

```
[Unit]
Description=Shutdown sequence
RequiresMountsFor=/mnt/objectivefs/somefolder

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/bin/true
ExecStop=/root/shutdown.sh

[Install]
WantedBy=multi-user.target
```

When I SSH into the instance, both services are enabled, running and show no errors. The scripts are executable, have the right permissions and work from the command line. /mnt/objectivefs/somefolder can be read and written to.
The startup service does its thing, which is mounting the ObjectiveFS share. All is well and the startup service status shows it has spawned an objectiveFS mount process;
```

$ systemctl status start.service

...

CGroup: /system.slice/start.service
           &#9492;&#9472;1388 mount.objectivefs xxxx xxxx xxxx xxxx 

```

However, upon shutting down the instance, the action performed in /root/shutdown.sh (writing "hello world" to a file in /mnt/objectivefs/somefolder) is not visible on the ObjectiveFS share.
Coming from a SysV mindset, I'm thinking I might be stuffing up the priorities somehow. Maybe the ObjectiveFS share is unmounted (or worse - has its process unceremoniously killed) before the shutdown script tries to do its thing? 
Any pointers would be greatly appreciated!

EDIT: tried
```
Before=shutdown.target reboot.target halt.target
```
No dice...

---

### Post by aromo2 on 2017-07-07
Not sure if I uderstood correctly but I think you need to insert the line:

```
ExecStop=/root/shutdown.sh
```

In start.service. So when you are done and want to execute /root/shutdown.sh, you just have to stop the service:

```
systemctl stop start.service
```

---

