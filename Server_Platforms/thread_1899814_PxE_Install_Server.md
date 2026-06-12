---
title: "PxE Install Server?"
date: 2011-12-24
forum: Server Platforms
---

### Post by arrrghhh on 2011-12-24
Hey guys,

I've been wanting to setup a PxE install server for a while - not CloneZilla, but a way to install fresh builds of Linux as well as Windows.

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

Is a fantastic guide, which seems to be exactly what I want - however, the bottom has a tiny section for Windows, and just says go to this other site.  Well, I've been to that site ([http://oss.netfarm.it/guides/ris-linux.php](http://oss.netfarm.it/guides/ris-linux.php)) and I'm lost.

I also found this

[http://www.ultimatedeployment.org/win7pxelinux1.html](http://www.ultimatedeployment.org/win7pxelinux1.html)

Which again seems like just what I need, but unfortunately the guy who made the guide customized it a little too much I think... as I can't get it to work.

So, has anyone set this up before?  Is there a relatively simple or at least clear guide on how to do this?  Every guide I've tried is very custom, and I can't seem to tailor it to my setup.  I'd rather not rip out my server and rebuild it just for this project, I should be able to work this setup into my existing server.

Any help is appreciated, thanks.

Edit - [this guide](http://www.savelono.com/linux/how-to-install-windows-7-over-a-network-using-linux-pxe-dnsmasq-and-samba.html) actually seems to be EXACTLY what I want.  I just lose the guy when he starts talking about AIK...

---

### Post by arrrghhh on 2011-12-26
So I've made some progress, but not really where I want to be.  The PXEInstallMultiDistro linked above didn't really apply, I couldn't get it to work after trying to adapt it to modern Ubuntu and modern Fedora.

So I found this page:

[http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10-p3](http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10-p3) - skipped ahead to page 3, step 8... I already have dnsmasq setup and configured, working as dhcp dns and tftp.  Anyhoo, I got the steps from that page to work flawlessly - but 2 downsides - I don't see a way to have a choice between systems, and this required not only a net connection but a fast one (even on my 30mbps cxn it was kind of slow...)

So that isn't ideal.  How can I adapt that netboot method to iso's?  I'd like to just be able to download copies of Ubuntu, Kubuntu etc and drop them in to folders, do a little menu editing and be able to install whatever I want basically.

I'd like to eventually get this to work with WinXP, Vista, 7 - people come over and need a reinstall but they never have media.  So long as the machine has the sticker and the code works - and I have a version that matches, of course... then it's perfectly legal.  I won't be doing installs without serial numbers for Windows, obviously - so let's leave that discussion out of this.  Thanks!

---

