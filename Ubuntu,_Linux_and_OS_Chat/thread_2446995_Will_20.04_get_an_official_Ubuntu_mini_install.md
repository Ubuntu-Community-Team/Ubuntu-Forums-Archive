---
title: "Will 20.04 get an official Ubuntu mini install?"
date: 2020-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by contrast9390 on 2020-07-10
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


It has Bionic and Xenial listed but not 20.04. Will Focal be included soon?

---

### Post by wildmanne39 on 2020-07-10
There is no way of knowing, the wiki is updated by volunteers so it depends if someone has the time to update it however you have the option to install 20.04 as a minimal install from the normal installation media.

---

### Post by kansasnoob on 2020-07-10
You now have to use the New Ubuntu Server Installer:

[http://cdimages.ubuntu.com/netboot/focal/](http://cdimages.ubuntu.com/netboot/focal/)

[https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510](https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510)

I don't like it but that's the way it is.

---

### Post by yetimon_64 on 2020-07-11
> **kansasnoob said:**
> You now have to use the New Ubuntu Server Installer:..

Not quite yet, a 64 bit focal mini.iso is still available [[COLOR=#0000ff]--here--[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/") 3rd one down the list.

It is getting much harder to find with this release for a reason. I have read recently that 22.04 may be the last ever release to have the mini.iso made for it, IF one is made for it (from what I've read I'm not sure if one will be made at all). Seems someone has made a decision not to fix the uefi issue and are phasing use of the mini.iso out altogether, hence none of the pages for the mini installer or even the netboot images you linked to have it added for this release. I did read some of the reasons and can understand why the decisions have been made. I think it was on the Ubuntu discourse site a while back, but I didn't save any links to the discussion so unfortunately can't post a link here. There were plenty of complaints though over there, as is usual for any changes like this :). 

It also has to be altered to use for a UEFI installation. Some instructions for how to do that is [[COLOR=#0000ff]--here--.[/COLOR]]("https://www.onetransistor.eu/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html")
This link was last udated 3 years ago (2017). I gave it another try recently for a focal UEFI installation, it will work but can be quite difficult to get it up and running, takes a bit of fiddling around to get it going.

Personally I will miss it, my best performing and most long lived install was done with the old mini.iso installer. My Trusty install done with the mini.iso lasted about 4 years before being "mothballed". That by far was my most stable set up and definitely the longest I have run any release of Ubuntu since I started with Gutsy Gibbon in 2007. 

Like all good things it is coming to an end, sadly the mini.iso is now on the way out it seems.

Cheers, yeti.

---

