---
title: "Advice for Ubuntu Server"
date: 2010-01-18
forum: Server Platforms
---

### Post by Fire$torm on 2010-01-18
Hello,
I'm looking for help/suggestions.

I want to run Ubuntu Server on my IBM ThinkCentre M52:
Intel Pentium 4 3.0Ghz CPU
512Megs PC-4200 Ram

I wish to run the following services/clients/apps:
**1)** Samba for file sharing with a dedicated partition
**2)** Boinc for distributed computing
**3)** Webmin for remote administration from a windows machine
**4)** Bittorrent client like KTorrent
**5)** VNC like service for remote access to the GUI
**6)** FTP server for local network & internet

I have several questions:
**A)** Do I need to run a GUI to use Boinc & Ktorrent?
**B)** Can the GUI be started and shutdown as required?
**C)** Can any app be autostarted without autologin or, can Ubuntu Server be configured to autologin to start apps and then lock so that access to the server would require login?
**D)** Since Webmin is used for system management, what app/client would I use for remote access to Boinc & Ktorrent?
**E)** Which version of Ubuntu Server should I be looking at, LTS or Karmic?

Please note that my reason for wanting to run Ubuntu Server over Desktop is mainly to conserve system memory.
Also, all the above mentioned apps and services (except GUI & FTP) will be running 24/7.

I currently have my ThinkCentre setup with:
Win2K Pro w/SP4
Boinc for Windows
Azureus as my BT client
UltraVNC for remote access
Cerberus for FTP (The Free Beta version)

I would like to switch to Ubuntu because I am getting really tired of microsoft
and I need to start working on the switch now because support for Win2K ends in July.

Thanks in advance,
Fire$torm

---

### Post by Cheesemill on 2010-01-18
> **Fire$torm said:**
> 
Please note that my reason for wanting to run Ubuntu Server over Desktop is mainly to conserve system memory.

If you are going to install a GUI on Ubuntu Server then you may as well install the Desktop version. Server edition doesn't come with a GUI installed.

---

### Post by tlsarles on 2010-01-18
You should do some reading on runlevels and init. Basically, when you boot the OS, init is the master process that loads all other processes. It first determines a runlevel. Based on the runlevel init will start a bunch of apps/services. One runlevel may be set to load X/GUI at startup, and another may not. You may switch between runlevels at any time.

[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

If security isn't an issue for you, I recommend Ubuntu desktop, because you will likely want a gui at some point if you are asking these questions.

---

### Post by Fire$torm on 2010-01-18
**[COLOR=Red]@[/COLOR]Cheesemill:** At first I was considering running Karmic Desktop but I have read elsewhere on this forum that you can install a GUI on Ubuntu Server and that there are several different GUI's I could use with varying resource requirements. 

**[COLOR=Red]@[/COLOR]tlsarles:** Thanks for the link. Actually, security is a major concern for me. I just didn't realize that a GUI was a security risk. Anyhow, I should have phrased my first question as:
**A)** Is an OS GUI required to run apps that are primarily GUI operated?

Thanks for the input.
Peace.

---

### Post by HermanAB on 2010-01-18
Howdy,

You are on the right track.  Use webmin and SSH for remote administration.  

Do not use VNC, since it is insecure and will get your machine hacked.  These forums are full of tales of hacker woe and they are all due to VNC.

---

