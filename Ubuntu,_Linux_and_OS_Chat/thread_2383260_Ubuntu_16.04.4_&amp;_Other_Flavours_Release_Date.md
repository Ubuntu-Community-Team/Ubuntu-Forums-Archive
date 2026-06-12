---
title: "Ubuntu 16.04.4 &amp; Other Flavours Release Date"
date: 2018-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by exhile on 2018-01-22
I recently was unable to install Lubuntu 16.04.3 on an Acer Aspire laptop which previously I was able to do since Ubuntu 16.04.3 came out in August of 2017. I'm not sure what happened but all of a sudden the installation process freezes after entering the password section of the wi-fi connection part and the operating system just won't install. I am hoping that Lubuntu 16.04.4 will be more successful when it comes out but I won't know for sure until it is released and available for download.

Ubuntu 16.04.4 and other flavors are set to be released next month but I don't think anyone knows the exact date since the thread is still a week away from February. Most likely a Thursday???

---

### Post by cruzer001 on 2018-01-22
You may of downloaded 16.04.1 before which uses a different kernel.  You could still download that iso and then upgrade it to 16.04.3; keeping you on the 4.4 kernel.  For lubuntu:

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

and download "lubuntu-16.04.1-desktop-amd64.iso" for the 64bit release or "i386" for the 32bit iso.

Just a suggestion, but may be worth a try.

---

### Post by exhile on 2018-01-22
> **cruzer001 said:**
> You may of downloaded 16.04.1 before which uses a different kernel.  You could still download that iso and then upgrade it to 16.04.3; keeping you on the 4.4 kernel.  For lubuntu:

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

and download "lubuntu-16.04.1-desktop-amd64.iso" for the 64bit release or "i386" for the 32bit iso.

Just a suggestion, but may be worth a try.

Thanks for your help. I downloaded a amd64 image of 16.04.1 and tried to install it but the problem remains. Perhaps the laptop has seen its end of life cycle and should be disposed of. I doubt the problem could be the installation media of 2 different versions of the O/S.

---

### Post by kansasnoob on 2018-01-23
Have you tried installing without selecting "install proprietary software" and "download updates" during installation. Unless you install using a wired connection it's best to just skip that until after the installation is complete.

---

### Post by deadflowr on 2018-01-23
> Ubuntu 16.04.4 and other flavors are set to be released next month but I don't think anyone knows the exact date since the thread is still a week away from February. Most likely a Thursday???
Expected date is February 15th.
[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule")
As always that can be changed.

---

### Post by exhile on 2018-01-23
> **kansasnoob said:**
> Have you tried installing without selecting "install proprietary software" and "download updates" during installation. Unless you install using a wired connection it's best to just skip that until after the installation is complete.

Selecting and or unselecting "install proprietary software" and "download updates" during installation doesn't improve the process. The circular mouse cursor just keeps on rotating forever and the laptop just stalls.

---

### Post by exhile on 2018-01-23
> **deadflowr said:**
> Expected date is February 15th.
[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)
As always that can be changed.

Ah, thanks... that was the web page I was searching for.

---

### Post by kansasnoob on 2018-01-23
> **exhile said:**
> Selecting and or unselecting "install proprietary software" and "download updates" during installation doesn't improve the process. The circular mouse cursor just keeps on rotating forever and the laptop just stalls.

It really shouldn't be asking for a wireless password unless you select one (or both) of those options :(

You could also try an Lubuntu alternate image:

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

The alternate images use the Debian installer instead of ubiquity. Are you performing an "entire disc" install where Lubuntu will be the only operating system on that machine? If so it's pretty straight forward - it's just text based. I'd personally use the 16.04.1 images to avoid HWE EOL:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support)

What was the last version of Lubuntu you were able to install on that laptop?

---

### Post by exhile on 2018-01-23
> **kansasnoob said:**
> It really shouldn't be asking for a wireless password unless you select one (or both) of those options :(

You could also try an Lubuntu alternate image:

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

The alternate images use the Debian installer instead of ubiquity. Are you performing an "entire disc" install where Lubuntu will be the only operating system on that machine? If so it's pretty straight forward - it's just text based. I'd personally use the 16.04.1 images to avoid HWE EOL:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support)

What was the last version of Lubuntu you were able to install on that laptop?

The setup process asks to enter a Wi-Fi password to connect to the Internet then goes to the 2 options. I don't think the image is the problem. Lubuntu is the sole O/S on the laptop.

Lubuntu 16.04.3 was the last version that was install-able. The laptop is somewhat old. Assembled in 2011 with Windows 7 installed originally. The laptop is more of a backup and so I'm able to part ways with it.

---

### Post by kansasnoob on 2018-01-24
What happens if you just don't enter any password? That's not really an old laptop to many of us. Most of the hardware I buy and work on is 9 to 12 years old.

---

### Post by exhile on 2018-01-24
> **kansasnoob said:**
> What happens if you just don't enter any password? That's not really an old laptop to many of us. Most of the hardware I buy and work on is 9 to 12 years old.

I am able to skip the Wi-Fi password part of the installation but the problem still remains. The circular mouse cursor keeps on rotating and the setup stalls. Yeah, if the free upgrade from Windows 7 to Windows 10 had successfully installed I wouldn't be using Lubuntu but Windows 10 just kept on crashing the laptop. Windows 7 extended support ends in 2020 so there's going to be a lot of laptops/desktops being turned over to use Linux. To me 5 years of mainstream support from Microsoft for Windows is already old.

---

### Post by vasa1 on 2018-01-27
[https://lists.ubuntu.com/archives/ubuntu-release/2018-January/004270.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-January/004270.html)> Due to the ongoing evolution of the fixes for the recently announced
Meltdown and Spectre security vulnerabilities [1], we are delaying the
16.04.4 point release, originally scheduled for the week of February
15.  ...

We are currently unable to set a new firm date for the release, but we
do not expect the schedule to slip more than a few weeks.


---

### Post by vasa1 on 2018-02-15
[https://lists.ubuntu.com/archives/ubuntu-release/2018-February/004287.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-February/004287.html)> 
As announced previously the release of the 16.04.4 point release has
been delayed. Seeing that things are now settling in, we have set the
1st of March as the new planned date release date. We expect to have
all the required pieces available in the archive by that time and will
provide images with all the necessary security fixes in place.


---

### Post by exhile on 2018-02-28
Has anyone updated to 16.04.4 yet?

---

### Post by vasa1 on 2018-03-01
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:        16.04
Codename:       xenial
$
```

---

