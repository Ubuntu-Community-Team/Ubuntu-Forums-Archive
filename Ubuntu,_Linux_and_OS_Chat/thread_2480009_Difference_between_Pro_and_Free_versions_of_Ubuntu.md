---
title: "Difference between Pro and Free versions of Ubuntu?"
date: 2022-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by forrestcupp on 2022-10-15
Just out of curiosity, what does paying for the Pro version give you that you don't get in the free version?

---

### Post by DuckHook on 2022-10-15
To my knowledge, the free version comes only with the published support durations (9 months for standard, 3-5 yrs for LTS) whereas the pro version has extended support (10 yrs for LTS, I don't know if standard has any extended support). I assume that the paid Pro version also entitles one to formal Canonical support (versus only community support for the free version), though I can't claim to really know about this last one because I don't use the Pro version. I also believe that the Pro version allows for livepatch updates, a useful feature for servers. I'm not very sure about this last feature and am basing my understanding on the fact that Pro is supposed to inherit the features of the old Ubuntu Advantage which I tried out for that very feature.

Here is Canonical's page describing Pro's features: [https://ubuntu.com/pro](https://ubuntu.com/pro)

---

### Post by grahammechanical on 2022-10-16
Ubuntu Pro is a progression from Ubuntu Advantage and a replacement for it. 

[https://ubuntu.com/legal/ubuntu-advantage](https://ubuntu.com/legal/ubuntu-advantage)

[https://ubuntu.com/blog/ubuntu-pro-beta-release](https://ubuntu.com/blog/ubuntu-pro-beta-release)

Both offered the service free for personal use. With Pro it is up to five machines. More than that and a tiered pricing system applied. Canonical developers provide support for all supported Ubuntu versions. For Ubuntu LTS versions if we sign up to Advantage we get Extended Security Maintenance for an additional five years. But it is only for

> Continue to receive security updates for the Ubuntu **base OS, critical  software packages and infrastructure components** with Extended Security  Maintenance (ESM). ESM provides five additional years of security  maintenance, enabling an organization&#8217;s continuous vulnerability  management. ESM is available through an Ubuntu Advantage for Infrastructure  subscription for physical servers, virtual machines, containers and  desktops, and is free for personal use. 

Whereas, with Pro we get

> ESM is also included in the  Ubuntu Pro **premium images that are optimised for [the public cloud]("https://ubuntu.com/cloud/public-cloud"),**  and these also provide **security maintenance for high and critical CVEs  for the entire collection of software packages shipped with Ubuntu.**

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)


[https://ubuntu.com/cloud/public-cloud](https://ubuntu.com/cloud/public-cloud)

It seems that Ubuntu Pro expands the security support for software packages and includes public cloud images of Ubuntu.

Regards

---

### Post by forrestcupp on 2022-10-16
Thanks, guys. So just to be clear, if you're using Ubuntu for personal use, you're ok with upgrading every 9 months (or whatever it is), and you're good with community support, there's really no reason to go with Pro. Is that right?

---

### Post by DuckHook on 2022-10-16
> **forrestcupp said:**
> Thanks, guys. So just to be clear, if you're using Ubuntu for personal use, you're ok with upgrading every 9 months (or whatever it is), and you're good with community support, there's really no reason to go with Pro. Is that right?
Essentially, yes.

Some have gone pro just on whatever servers they run because the livepatch update feature is very useful (never having to reboot a server is really cool). And since anyone is entitled to 5 pro machines for free, well… it's a nice, generous offer from Canonical.

I like to reboot my servers from time to time just on general principles, but then, I don't need guaranteed uptime and all that other stuff because my servers are only for my own private use. If I were running production servers in a collaborative environment, Pro would be a very real advantage.

---

### Post by lammert-nijhof on 2022-10-17
I have 3 machines run at Ubuntu Pro. 

My desktop Host OS updates the kernel without the need to reboot, so I don't have to close the VMs and reboot the host.   As far as I understand and noticed, the update will be prepared and at an appropriate time the kernel replacement will be actually executed. I expect it will be on the next normal reboot. For me that reboot will automatically occur after one of the 2 to 20 power fail / automatic restarts per week. 

I still use my Ubuntu 16.04 VM with Extended Security Maintenance (ESM) for my Banking and PayPal, probably I use it till April 2026. I use 16.04 ESM together with the latest snaps for Firefox and LibreOffice. I also subscribed to the ESM updates for my Ubuntu 14.04, just out of respect for my good time with Unity :) :)   I will not repeat that operation with 18.04 nor with 20.04, I feel no personal attachment with gnome. 

Another equally good facility are the repositories from "old-releases.ubuntu.com".  I used it for my Ubuntu VMs 12.04; 10.04 and 8.04 and after changing the corresponding /etc/apt/sources.list I still received a lot of updates say ~150 or so per release.  It solved a number of smaller issues and for 8.04, it allowed me to install gcc needed to install the VBox Guest Additions.  For those 32- bit VMs I use VBox Guest Additions 5.2.44, because I have the  impression, that it gives the best results for 32-bits and FreeBSD  agrees with me and does the same. All those VMs have now full support for all VBox functions like; shared libraries; full audio support; copy/paste to and from the host and last but not least the VBox Video driver with a completely variable VM window. I did the same for the 6.06 release, but there VBox complained. that Linux 2.6.15-57 was to old for the VBox video driver, however all the other functions did work.   I even tried VBox 4.1.44, but that had the same result :(   However I did find in the Ubuntu repository a standard video driver from VMware that supported a nice 1440x960 resolution for Ubuntu 6.06 LTS. Note that all other VBox functions did work in 6.06. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291139&stc=1[/IMG]

I also tried those tricks on Ubuntu 4.10 the first Ubuntu and on 5.04 my first Ubuntu, but they were too old and I left them as installed some years ago without the VBox Guest Additions.

---

### Post by mIk3_08 on 2022-10-17
> **DuckHook said:**
> I assume that the paid Pro version also entitles one to formal Canonical support (versus only community support for the free version), though I can't claim to really know about this last one because I don't use the Pro version. I also believe that the Pro version allows for livepatch updates, a useful feature for servers. Agree, I believe Pro is supported by ESM up to 10 years of livepatch. Regards and cheers.

---

