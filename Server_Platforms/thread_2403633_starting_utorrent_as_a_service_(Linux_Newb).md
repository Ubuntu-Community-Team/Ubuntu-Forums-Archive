---
title: "starting utorrent as a service (Linux Newb)"
date: 2018-10-14
forum: Server Platforms
---

### Post by wart101 on 2018-10-14
Hi, i am really new to Linux/ubuntu so i am going through a bit of a learning curve one that i am enjoying but as a consequence i lack terminology and sometimes due to comparisons asume things work differently. i am using Ubuntu server 18.04 and i am trying to get utorrent working as a .service. i can get it to work fine if i run it straight from the CLI.

```
./utserver
```

i can access it from my web browser no worries but i am trying to set it up so when my server boots it runs in the background, i have been trying to do this using systemd but i can seem to get it working. this is what i used,  there is a lot there that i just don't understand. i grabbed this from the ssh.service file and tried to modify it to get it to work but it doesn't. 

P.S. i have been trying to get this to work for a few days now using various online Tuts but i feel i am missing some fundamental concepts.

```
#[Unit]
#Description=utorrent
#After=network.target


#[Service]
#Type=simple
# Another Type option: forking
#User=adam
#WorkingDirectory=/home/adam
#ExecStart=/home/adam/utorrent/utorrent-server-alpha-v3_3/utserver.service  --option=123
#Restart=on-failure
# Other Restart options: or always, on-abort, etc


#[Install]
#WantedBy=multi-user.target




[Unit]
Description=utorrent service
After=network.target auditd.service
#ConditionPathExists=!/etc/ssh/sshd_not_to_be_run


[Service]
#EnvironmentFile=-/etc/default/ssh
#ExecStartPre=/usr/sbin/sshd -t
Type=simple
User=adam
ExecStart=/home/adam/utorrent/utorrent-server-alpha-v3_3/utserver
#ExecReload=/usr/sbin/sshd -t
#ExecReload=/bin/kill -HUP $MAINPID
KillMode=process
Restart=on-failure
RestartPreventExitStatus=255
#RuntimeDirectory=sshd
RuntimeDirectoryMode=0755


[Install]
WantedBy=multi-user.target
Alias=utorrent.service


systemctl status output.

adam@homeserver:~/utorrent/utorrent-server-alpha-v3_3$ sudo systemctl status utorrent
&#9679; utorrent.service - utorrent service
   Loaded: loaded (/lib/systemd/system/utorrent.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2018-10-14 08:02:29 UTC; 49min ago
 Main PID: 13215 (utserver)
    Tasks: 6 (limit: 7372)
   CGroup: /system.slice/utorrent.service
           &#9492;&#9472;13215 /home/adam/utorrent/utorrent-server-alpha-v3_3/utserver


Oct 14 08:02:29 homeserver systemd[1]: Started utorrent service.
```

---

### Post by wart101 on 2018-10-15
Is no one answering me because i am asking about utorrent? can you just help me with and application if it conflicts with your morals?

---

### Post by slickymaster on 2018-10-15
Thread moved to **Server Platforms** for a better fit

---

### Post by mastablasta on 2018-10-15
looks like you commented out (the # sign) plenty of things: 
[https://askubuntu.com/questions/976906/how-to-configure-to-start-my-application-at-boot-time](https://askubuntu.com/questions/976906/how-to-configure-to-start-my-application-at-boot-time)

[https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux](https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux)

---

### Post by nlee2 on 2018-10-15
Check this out

[https://github.com/vortex-5/utorrent-ubuntu-service](https://github.com/vortex-5/utorrent-ubuntu-service)

---

### Post by wart101 on 2018-10-16
> **nlee2 said:**
> Check this out

[https://github.com/vortex-5/utorrent-ubuntu-service](https://github.com/vortex-5/utorrent-ubuntu-service)

Thanks mate, sorry if this is a stupid question but i want to understand the code in the script below, there just to much i don't understand and i would like to be able to write my own scripts for whatever reason in the future, is there a learning resource that can tell me what is happening here i can write basic code with c#/c++/python (Less with Python) so if you i can be pointed in the right direction i should be able to figure things out. i thought you could run utorrent from a service unit file but this doesn't seem to be the case?

```

#!/bin/sh
#Starts the uTorrent as a service to be executed from upstart or systemd

# Location of the log file (must be by the current user writable)
LOGFILE=/var/log/utorrent.log

# Path to the utorrent server (usually sym linked)
UTORRENT_PATH=/path/to/utorrent-server_alpha_v3_0

# Name of the utorrent server binary (you usually don't need to change this)
EXEC=utserver

# Pre-start cleanup of last run
if [ -e $LOGFILE ]; then
    rm $LOGFILE
fi

$UTORRENT_PATH/$EXEC -settingspath $UTORRENT_PATH -logfile $LOGFILE

```

---

