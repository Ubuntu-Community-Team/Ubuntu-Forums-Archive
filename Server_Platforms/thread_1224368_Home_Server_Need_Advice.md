---
title: "Home Server Need Advice"
date: 2009-07-27
forum: Server Platforms
---

### Post by oliv2915 on 2009-07-27
I am looking to build a Linux server for my home. I like to set it up as a DHCP, FTP, and Proxy. I have been looking around the web and have desided to use Squid for Proxy and VSFTPD for FTP. I am asking, are those ok for what I am wanting to do or is there anything better to use? Also, does Webmin have modules that I can use to configure and manage my server or is ISPconfig better?

---

### Post by grantemsley on 2009-07-27
If you don't have much linux experience, you might want to check out eBox - it is based on ubuntu and configures all that from a nice webui.

[http://ebox-platform.com/](http://ebox-platform.com/)

---

### Post by SpaceBas on 2009-07-27
> **grantemsley said:**
> If you don't have much linux experience, you might want to check out eBox - it is based on ubuntu and configures all that from a nice webui.

[http://ebox-platform.com/](http://ebox-platform.com/)

I'm very very comfortable in the command line but I have to say, the screen shots of ebox make me wonder if that GUI is available outside of their distro?
Its really slick looking. There are times (read: iphone) when I'd like to be able to configure things without doing an ssh ...

Anyway, don't want to hijack the thread - but if folks feel that the ebox gui is secure, then it looks quite nice for a home server.

I've found that Ubuntu Server + the XFCE gui is also fairly easy to get up and running. You can transition yourself to the CLI over time and use VNC to get at the gui tools.

---

### Post by grantemsley on 2009-07-27
Actually, ebox can be installed from within ubuntu.  It's in universe.

It's still a fairly standard ubuntu server - the only catch is that you can't (easily) edit the config files that are controlled by ebox, because they will get overwritten.

I set mine up, logged in through SSH, and apt-get install'ed ubuntu-desktop for a GUI, and a few other programs.

---

