---
title: "Server keeps restarting every 10 minutes"
date: 2019-10-01
forum: Server Platforms
---

### Post by ejach2000 on 2019-10-01
Hello,
I am running Ubuntu Server 18.04, I mainly use it as a Plex Media Server.
After the most recent update that was released today (1.17.0.1841-d42cfa161), I have noticed that the server either crashes or loses LAN or internet connection periodically every 10 minutes.
I say LAN **or** internet connection because there have been times where I have been accessing the server via SSH and Plex goes down, but I can still maintain connection via SSH. 
In these instances I attempt to ping something like google.com and it returns full packet loss.
And sometimes it is the reverse, sometimes I can access Plex just fine, but the terminal throws the following when I attempt to connect to it:
```
ssh: connect to host x.x.x.x port 22: Resource temporarily unavailable
```
[Here]("https://pastebin.com/85tfWXTW") are my logs, please direct me to a better source for my logs if these are insufficient, was not too sure where I should look (and I have limited access because SSH is turning off and on periodically as it is.)
I am not sure if the update itself is causing this, or if it is an error in the system itself. The only thing that points to the update itself is the fact that in less than an hour after I updated Plex, the problem started occurring.
I am at loss for what to do here, I am away from where the server is, so my best bet right now is the limited SSH access that I have.
I can provide any additional information upon request.
Thanks!

---

### Post by Skaperen on 2019-10-01
i see times in the log file.  at what time(s) is it failing?

---

### Post by ejach2000 on 2019-10-02
> [COLOR=#000000]i see times in the log file. at what time(s) is it failing?[/COLOR]
I am not sure,
I let it sit overnight and it seems to be fine and not crashing.
If it happens periodically again, I will be sure and get the timestamps right. Do you have any recommendations for a better log that I could use?
I thought about using the Plex logs, but it contains the public IP of both my home and my university, so I stayed away from putting it on pastebin.
Are there any ways that I can prevent this from happening again?

---

### Post by ejach2000 on 2019-10-02
Ok, so it happened again, and I think I finally pinned down the timestamp when it happened.
[This]("https://pastebin.com/LSenYXwS") is according to the [FONT=courier new]var/log/syslog [/FONT]
As of right now, the Plex connection is down (despite it saying it is running via systemctl), but I can still maintain access via SSH.
If there is any other log that you would need, please let me know.

EDIT:
[Here]("https://pastebin.com/p8BPG17Y") are the logs according to [FONT=courier new]/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/Logs/Plex Media Server.log[/FONT][FONT=courier new][/FONT]

---

