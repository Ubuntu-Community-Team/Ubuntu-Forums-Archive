---
title: "ubuntu on vmware"
date: 2013-09-28
forum: Virtualisation
---

### Post by shahin on 2013-09-28
Greetings-
I just installed Ubuntu SS within VMware workstation. I can only see a command line interface. How do I access the desktop please? My host OS is Windows 7. Do I need to use VNC? Just for my edification, what other applications or tools can I use? Can I use cgiwin? What is the differences between vnc and vnclight? 
Thanks

---

### Post by drmrgd on 2013-09-28
Not sure what Ubuntu SS is.  Can you elaborate on what version of Ubuntu you did install?  

Assuming you did install something other than the server version (which may not include a GUI), you may also need to run the VMware Tools scripts in order to properly configure things (although I don't quite remember having to do this in order to load a desktop environment before).

---

### Post by TheFu on 2013-09-28
> **drmrgd said:**
> Not sure what Ubuntu SS is.  Can you elaborate on what version of Ubuntu you did install?  

Assuming you did install something other than the server version (which may not include a GUI), you may also need to run the VMware Tools scripts in order to properly configure things (although I don't quite remember having to do this in order to load a desktop environment before).

At an installfest a few weeks ago, someone used Workstation to load stock Ubuntu desktop and the guest additions were auto-magically loaded. It was impressive to me, but the person wiht the Workstation didn't notice the GUI integration was working ... guess he was just used to that with Windows guestOSs.

I don&#8217;t know what UIbuntu SS is either. If you installed Ubuntu Server ... well, there isn't a GUI. It is a shell-only OS by default. Running a server usually means doing things manually or though automation tools like puppet, chef, rexify, ansible ... or any of the other 10+ F/LOSS options.  Using these automation tools is generally only performed when there are 5-50,000 servers to be managed.  Less than 5, manually will be easier.  
There is good news.  You can load a desktop Linux OS and treat it like a "server" if you like, just be aware that system stability will be reduced. Normally that doesn't matter, since even running a desktop the stability will still be on the 4-6 months timeframe and kernel patches come every 1-3 months for all supported releases anyway.  Without the GUI stuff, I've had Linux servers running for multiple years (not facing the internet) - which is pretty good stability for a non-$100K+ OS.  The "server" version can also support a GUI - normally a lite one like LXDE would be selected.  Just know that it will not come with the full desktop GUI management tools - so networking is manually handled, not using a GUI. This can be a hassle if you aren't used to it and really want/need a GUI.  I prefer the manual way, so even my desktops are built using the server releases and I'll add a window-manager myself.  **sudo apt-get install lxde** will load a lite DE.

On Linux, almost every problem will leave a trace in the log files, so if you did install a desktop OS, check the logs for warnings and  errors - copy/paste those here and we can probably help.

BTW, I did google "ubuntu ss" ... nothing relevant was returned.

Anyway, I hope this babbling has helped.

---

