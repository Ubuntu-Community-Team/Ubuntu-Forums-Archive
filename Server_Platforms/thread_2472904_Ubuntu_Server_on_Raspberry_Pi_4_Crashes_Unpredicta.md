---
title: "Ubuntu Server on Raspberry Pi 4 Crashes Unpredictably"
date: 2022-03-16
forum: Server Platforms
---

### Post by tlaporta on 2022-03-16
I have a Raspberry Pi 4 that I'm using to run Ubuntu Server 20.04. On the system, I run a Plex server, Foundry VTT, and the smbd and NFS daemons (to share a couple of hard drives connected to the machine). Every 5-7 days (about) the server becomes unresponsive; I can't ssh into it, I'm unable to access the shared drives and I have to reboot before everything works again (but everything DOES seem to work after a reboot). What are some of the logs I should look out to help figure out what the machine was doing at the time it crashed, to assist with troubleshooting?

---

### Post by TheFu on 2022-03-16
I know nothing about running Ubuntu on ARM systems. Zero.

But google found these links related to "ubuntu logs" 
[https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files)
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)

All Unix systems deal with logs about the same.  Systemd inserted a middle-man and something called journalclt which can be used to search logs for everything or specific things based on which boot it was, which process it was and which machine the log originated.  systemd-journal has a remote logging capabilities that enterprises love. In the olden days, we'd use a log server to get logs onto a different system - it is a security thing.

Try **journalctl -p err** to see what that shows.

Anyway, seems like there is either a hardware or software issue with the pi.  No computer should crash, ever, unless there is a hardware failure.  Many months or running should easily occur on an Ubuntu server that is properly sized for the workload.  Plex can demand very high CPU, if you allow it to transcode video. I'd never do that on a raspberry pi.  I've run Plex on a dual Pentium box from 2015 for years and allowed it to transcode 1 stream at a time. The playback devices here r-pi v2 and v3 running OSMC. OSMC is a tuned version of Kodi just for the pi hardware. It works well.

---

### Post by tlaporta on 2022-03-17
I'll take a look at that logs next time it happens. Plex isn't transcoding any video (it's an audio server only); the crashes tend to happen when I'm not even using/accessing the server at all.

---

### Post by TheFu on 2022-03-17
> **tlaporta said:**
> I'll take a look at that logs next time it happens. Plex isn't transcoding any video (it's an audio server only); the crashes tend to happen when I'm not even using/accessing the server at all.

Plex is a terrible audio server.  Any interest in other option that don't destroy your privacy?

---

### Post by tlaporta on 2022-03-17
If it allows me to easily access my music outside my home, then I'll definitely take recommendations. I'm not too doctrinaire about my privacy, but I'd be happy to see something that's possibly a bit lighter.

---

### Post by TheFu on 2022-03-17
> **tlaporta said:**
> If it allows me to easily access my music outside my home, then I'll definitely take recommendations. I'm not too doctrinaire about my privacy, but I'd be happy to see something that's possibly a bit lighter.

There are lots and lots of those. 
But if you don't care about privacy, I won't waste my time. Just know that there are plenty of other options that take very little effort to setup. The hardest part is dealing with the hundreds of choices.  That includes the preferred client(s), since different clients only support specific protocols, which limits which servers would make sense.  For really stable connections, sshfs is handy. That would be good for a work desktop accessing music on a home computer, for example. Then the files would appear to be local and whatever client you have that plays local files will work.  If you use https, then a different set of clients and servers would be used.  If just any web browser is the client, then an ssh-socks5 proxy will be easy to use.  Many audio players can use a web proxy server, so that works for all of them too, without needing to have your music and playlists shared to the plex team.

---

### Post by ameinild on 2022-03-18
I would take a look at temperature readings. It sounds like maybe the Pi is getting too hot. Do you have a heatsink and fan on it, and proper airflow where it's installed? That's a good way to start nonetheless. But please report some temperature readings. ;)

---

