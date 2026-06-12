---
title: "How to run sudo command inside bash script? (when a daemon is calling the script)"
date: 2012-07-05
forum: Server Platforms
---

### Post by RicardoEscobar on 2012-07-05
Hello there. Here is the situation:

I installed a twitter client calles "Twidge" so my ubuntu server can tweet now (cool)

To tweet:

```
sudo twidge update "This is a test tweet"
```If I run it without sudo:

```
twidge update"This is a test tweet"
twidge: /home/user/.twidgerc: openFile: permission denied (Permission denied)
```On the other hand I have an script called **tuitTorrent.sh**, and here it is:

```
#!/bin/bash
#Este script se ejecuta desde /var/lib/transmission-daemon/info/settings.json
sudo twidge update "@MyTwitterAccount torrent downloaded.`date`"
```If I run the scrip as

```
sudo /home/user/scripts/tuitTorrent.sh
```it ask for my sudo password and I just type it in, then it works.

However I installed Transmission, a bit torrent client, on the configuration file: **var/lib/transmission-daemon/info/settings.json** I may set up the path to a script with runs after the torrent downloads successfully. So I set this on the configuration file:

```
"script-torrent-done-enabled": true,
"script-torrent-done-filename": "/home/user/scripts/tuitTorrent.sh",
```However when a torrent finishes downloading, the script never runs, I guess it's because the twidge command requires a sudo prefix, and I don't know how to give an script sudo execute level or how to enable twidge to run without needing a sudo password.

So there is my problem, I want to tweet after transmission finishes to download, I have the script but it does not run unless it have a sudo password, yet I don't execute the script directly, transmission daemon runs it.

---

### Post by markbl on 2012-07-06
You are going about "fixing" this problem the wrong way.

It seems you originally mistakenly configured twidge as root, not yourself. Just [FONT="Courier New"]sudo rm ~/.twidgerc[/FONT] and then configure twidge properly i.e. run [FONT="Courier New"]twidge setup[/FONT] as yourself.

---

### Post by RicardoEscobar on 2012-07-06
> **markbl said:**
> You are going about "fixing" this problem the wrong way.

It seems you originally mistakenly configured twidge as root, not yourself. Just [FONT=Courier New]sudo rm ~/.twidgerc[/FONT] and then configure twidge properly i.e. run [FONT=Courier New]twidge setup[/FONT] as yourself.

Ok, I'm gonna try that.

---

### Post by RicardoEscobar on 2012-07-06
Thanks a lot markbl, I finally did it.

Now I may tweet using my user (no sudo prefix) and transmission may tweet too, I can use tweets inside scripts too, thanks.:KS

---

