---
title: "Setting up a ubuntu server via network"
date: 2010-11-06
forum: Server Platforms
---

### Post by Slicksilver555 on 2010-11-06
Hey, I'm trying to set up a home server with ubuntu. This will be a LAMP webserver. I've been looking around on a lot of sites for help, but I can't find much. My main glaring problem is, all the setup tutorials seem to require you to *have a screen and keyboard*.

I need to be able to access this fully via SSH or any other protocol from my computer's command line. I can't say I know a lot about SSH, but I am willing to figure it out if I can find a way to even install ubuntu without a screen. I saw a tutorial that appeared helpful ( [https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole) ) however this says things that require having a screen and keyboard like "press escape as soon as the installer presents you the first question."

Is there any way for me to SSH into the setup utility to set it up via command line, or any other Linux distro that allows this? Thanks for the help in advance.

---

### Post by HermanAB on 2010-11-07
Howdy,

SSH requires a running system, so you can only use it after the system is installed.

On Redhat, Suse and Mandriva systems, you can make an automated installation system that will install a machine unattended over a network, but Debian systems are still lacking in this regard, although there has been some effort to port the Redhat installer to Debian.

---

