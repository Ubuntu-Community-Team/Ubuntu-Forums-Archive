---
title: "What version of Ubuntu is best to install .."
date: 2018-11-07
forum: Server Platforms
---

### Post by daniel228 on 2018-11-07
At the minute I currently have Ubuntu Server installed on two systems being 18.4 ..

The problem I have is I just can not get my head around the network interfaces . I think Ubuntu Server 18.4 from 16.4 had its network manager or network interfaces changed and no longer uses network manager.

I have several desktop systems hear I want to install Ubuntu Server on to run them as a Server set-up as my primary hobby and interest is networking but I dont know if I should install 18.4 or 16.4 ..

The objective is to set-up a home lab of some sort and learn scripting for ansible .

How long is 16.4 supported for and can anyone tell me how to modify the Network Interface for 18.4 ..

I have been struggling to get my head around .YAML files ..

I know very little and I'm still having to learn the likes of Debian syntax ..

Thanks.

---

### Post by darkod on 2018-11-07
LTS versions of ubuntu are supported for 5 years. So, the 16.04 LTS will be supported until April 2021.

But if you are installing new servers now I would do it with 18.04. Netplan is not that difficult to learn and there are already many tutorials on the internet. Plus the official ubuntu help pages ([https://help.ubuntu.com/](https://help.ubuntu.com/)). 18.04 will be supported until April 2023.

---

### Post by howefield on 2018-11-07
Both 16.04 and 18.04 are supported for 5 years, so you have until April 2011 till 16.04 goes end of life and April 2023 for 18.04.

---

### Post by TheFu on 2018-11-08
Ubuntu Server doesn't use network-manager.  It has always used text config files to setup networking.  If you have a GUI, you aren't on Ubuntu Server.  Over the years, the settings were modified and since 17.10, netplan has been used by default.  Prior to that, we could make most settings in the **interfaces** file. Around 12.04, DNS control was moved from the /etc/resolv.conf into the interfaces file too ... by inserting another controlling system called "resolvconf" to solve a problem that desktop users had.

I for one miss the simplicity of network management under Ubuntu 10.04.

And I don't think 18.04 is ready for production use at this point.  We had hoped to migrate a few systems this fall, but there are just too many issues in the release still.  Those issues will be fixed, perhaps in the 18.04.2 release?  For now, 16.04.5 is what we bring new servers up using.

For an understanding of Ubuntu Support - [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) spells it out.   [https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle) explains things too.  Perhaps it is pedantic, but 18.4 is incorrect.  It is 18.04. Be certain to scroll down to understand how the specific kernel being used matters. 

YAML can be a little funky at first, but it isn't hard.  Indentation matters.  Learning by example is easy.  Just pay attention to spacing and indentation.

---

