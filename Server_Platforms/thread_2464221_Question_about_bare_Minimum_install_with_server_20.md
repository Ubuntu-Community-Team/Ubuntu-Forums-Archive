---
title: "Question about bare Minimum install with server 20.04.2 LTS"
date: 2021-06-26
forum: Server Platforms
---

### Post by mos6502mos on 2021-06-26
Folks,
It has a been a very long time since I had to use Ubuntu Server or install. So long, that I totally forgot my old account; however, I have been requested to start migrating servers to Ubuntu Server. In the past, I know there was a super minimum install, which had the basics, then you 'added' what you wanted. However, just installed 20.04.2 LTS, and noticed you can add items, but not take away. In addition, looks like 'snap' and 'cloud-int' all come standard, which can be argued a good thing, but I would like the basic packages to be installed that will get me basic going, and I can add what I need. I do not need 'snap' nor the 'cloud' stuff and in my case would be easier to add what I need, oppose to 'take away' what I don't want.

Is there any mini/net installed still or is there a new path or method for a BASE install? Again - I have been out of the Ubuntu loop for a few years now.

Thank you

---

### Post by sudodus on 2021-06-26
You find the 20.04 LTS netboot alias mini.iso file at [this link](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot). The checksum is in the parent directory.

There will be no newer versions, and Ubuntu Server will come with another lnstaller, 'curtin'. Some of us would rather keep the old server iso files with the debian installer, but I guess there are advantages with the new one too. See also the discussion in [this thread](https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510).

---

### Post by LHammonds on 2021-06-26
You can find the [Network installer here](https://ubuntu.com/download/alternative-downloads#network-installer).

I had a [similar question](https://ubuntuforums.org/showthread.php?t=2436947) a while back when 18.04 was current.

LHammonds

---

### Post by MAFoElffen on 2021-06-26
Why do people NOT talk about provisoning Servers with MAAS anymore? Set up once, upkeep, and provision to your infrastructure... Ubuntu Server pushed that hard for years... Did the interest and marketing die out on that?

---

### Post by LHammonds on 2021-06-26
> **MAFoElffen said:**
> Why do people NOT talk about provisoning Servers with MAAS anymore? Set up once, upkeep, and provision to your infrastructure... Ubuntu Server pushed that hard for years... Did the interest and marketing die out on that?
I have never used MAAS.  My infrastructure uses ESXi / Nutanix with VMware on top of it and once I setup a generic server, I convert it to a template and whenever I need a new server, I deploy from template and change the static IP, name and hostname.  But regardless, if you want a minimal install, you still need a mini-type ISO image.

LHammonds

---

### Post by mos6502mos on 2021-06-26
Thank you all for the links and support. This is spot on what I needed.

---

