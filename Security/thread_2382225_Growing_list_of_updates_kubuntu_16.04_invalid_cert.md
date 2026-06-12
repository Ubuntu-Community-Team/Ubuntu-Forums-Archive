---
title: "Growing list of updates kubuntu 16.04 invalid certificate"
date: 2018-01-10
forum: Security
---

### Post by MoeNeigh on 2018-01-10
Lately Discovery in kubuntu 16.04 has been showing an invalid certificate warning for updates, including some security updates. I can get some updates with sudo apt-get update and sudo apt-get upgrade. But those with the invalid certificate (i.e. unsigned) are always held back. In Discovery I have an option to ignore the invalid and unsigned certificate warning forever, but am afraid to do so. What is the problem with signing these update certificates. The server they show is 91.189.93.5 and location GB. Address shown is autoconfig.kde.org.

---

### Post by vasa1 on 2018-01-10
Please post the exact output of sudo apt-get update and sudo apt-get upgrade.

---

### Post by Max303 on 2018-01-11
Are you getting the warnings for packages from PPA's or from the official ubuntu repositories?

---

### Post by MoeNeigh on 2018-01-11
I'm assuming these are the official repositories but I don't know. If these are official, then why did someone lapse and not maintain signed certificates? Here is the message I see any time I open Discover (Software Center):
1. The server failed the authenticity check (reviews.ubuntu.com)
2. The certificate is not signed by any trusted certificate authority
I do have screen shots of what I see when I click "Details", but I'm not sure if and how I can upload them. Size of each screenshot is only about 60 kilobytes each. I have four of these screen shots.

What I have done so far, is try multiple times with sudo apt-get update to get some updates and I do get some, but up to 14 updates were held back. I finally went to Discover and selected allow current updates on those held-back updates for one time only. But it appears to get these any "held back" updates, I would have to do this over and over again until someone at ubuntu updates their certificates so that they are signed. I don't fully understand all that goes into the maintaining of signed certificates. Still, details seems to indicate that the sources are trusted, but I still need to manually allow the updates each time until the certificates are signed. I also have the option of clicking allow forever, but I am hesitant to do this.

How do I know if I'm getting packages from PPA's?

---

### Post by QIII on 2018-01-11
Hello!

We cannot help if you do not do as vasa1 asked.  That will give us the information we need to begin to help.

Cheers!

---

### Post by MoeNeigh on 2018-01-11
In Discovery (Software Center), I went ahead and allowed (this one time) those held-back updates. So in a terminal, those are no longer showing as held back or at all. I think most of them began libdrm... or mesa... Still wondering why even when there are no updates, Discovery still comes up saying:
1. The server failed the authenticity check(reviews.ubuntu.com) and
2. The certificate is not signed by any trusted certificate authority.
Is this a bug? It seems these messages are the price of entry now whenever Discovery is opened, even if there are no updates.

---

### Post by slickymaster on 2018-01-11
It has been asked several times to post the output you get from running in a terminal window the following```
sudo apt-get update && sudo apt-get upgrade
```Please do it so we can get the necessary information to help you solve your problem

---

### Post by MoeNeigh on 2018-01-11
Sudo apt-get update && sudo apt-get updrate no longer shows the held back updates because I allowed Discovery to update those held-back updates even though the certifcates were unsigned. These did appear to be normal libdrm and mesa updates. So they have been updated.
However, now the price for entering Discovery seems to be having to see the failed certificate warning as the price of entering Discovery even when there are no updates. Sudo apt-get upgrade from a terminal will get the updates, but will not get any unsigned failed certficate updates. Only Discovery will get these if you agree to ignore the failed certificates. Surely someone has reported this somewhere, but I can't find it. Why does ubuntu not maintain signed certificates for some updates like libdrm files and mesa files?

---

### Post by vasa1 on 2018-01-11
If you still have the screenshots, click on the paperclip icon and follow instructions to upload them.

Also, post the entire output of

```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by MoeNeigh on 2018-01-11
Here are the screenshots:
[ATTACH=CONFIG]278147[/ATTACH][ATTACH=CONFIG]278148[/ATTACH][ATTACH=CONFIG]278149[/ATTACH][ATTACH=CONFIG]278150[/ATTACH]

Here are the results from konsole re sudo apt-get update && sudo apt-get upgrade:```
gunderwood@gunderwood-GA-78LMT-USB3:~$ 
gunderwood@gunderwood-GA-78LMT-USB3:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/mc3man-ubuntu-avidemux1-xenial.list:deb http://ppa.launchpad.net/mc3man/avidemux1/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
gunderwood@gunderwood-GA-78LMT-USB3:~$
```

[ATTACH]278151[/ATTACH]

---

### Post by vasa1 on 2018-01-11
So what is the problem?

---

### Post by QIII on 2018-01-11
You still have not done what vasa1 asked.  We can only help to the extent tat you provide the diagnostic information requested.

Please post the terminal output of

```
sudo apt-get update && sudo apt-get upgrade
```

***here*** between code tags.

---

### Post by MoeNeigh on 2018-01-11
Yes I have done this. See above posts.

---

### Post by QIII on 2018-01-11
As far as I am able to determine, you have not yet posted the results of 

```
sudo apt-get update && sudo apt-get upgrade
```
as vasa1 requested in Post #2

> **vasa1 said:**
> Please post the exact output of sudo apt-get update and sudo apt-get upgrade.

---

### Post by MoeNeigh on 2018-01-11
> **QIII said:**
> As far as I am able to determine, you have not yet posted the results of 

```
sudo apt-get update && sudo apt-get upgrade
```
as vasa1 requested in Post #2

This is the second time I have posted this. Are you not reading the other previous posts? You are annoying me with you lies. Again, do you understand "already posted"?

```
gunderwood@gunderwood-GA-78LMT-USB3:~$ 
gunderwood@gunderwood-GA-78LMT-USB3:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/mc3man-ubuntu-avidemux1-xenial.list:deb http://ppa.launchpad.net/mc3man/avidemux1/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
gunderwood@gunderwood-GA-78LMT-USB3:~$
```

No one has explained why Discovery says that for me to have gotten those updates (which I finally did through Discovery), I had to agree to allow the updates with failed certificates to come through even though Discovery also says the site is trusted. This sounds like a bug that just won't go away.

---

### Post by MoeNeigh on 2018-01-11
> **vasa1 said:**
> So what is the problem?

The problem is Discover now constantly warns that the needed updates have a failed certificate, though details say that the site is trusted. This makes no sense, but was worrying me that the updates themselves might be unsafe. I went ahead and agreed to allow the updates to come through, and there was success. But still to this day, Discover warns of unsigned, failed certificates for what appears to be normal updates like libdrm and mesa. So I got the updates, but Discover still warns and doesn't seem to like the unsigned certificates. If I try to update via the konsole with sudo apt-get update && sudo apt-get upgrade, these updates are held back. So, as I have repeatedly said, I went back to Discover and agreed to let these updates through. The konsole method won't get these updates, but it will get other updates.

All said, all updates of any kind, with or without failed certificates have come through. But I had to jump through an additional hoop to get them. I am simply a little worried and curious as to who is responsible for the unsigned, failed certificate. The warning persists in Discover, regardless. A bug?

Thanks for your help.

---

### Post by QIII on 2018-01-11
You have posted the results of 

```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

You have not posted the results of 

```
sudo apt-get update && sudo apt-get upgrade
```

You have been asked to do this several times.  Do you understand the difference?  You have 3 non-Canonical repos/PPAs there.  We need to see specifically where the certificate issue lies.

Will you please read ***our*** posts?  Had you done so, you would have had no reason to be annoyed by any "lies".

---

### Post by lisati on 2018-01-11
Please post the output of the following, as requested:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by MoeNeigh on 2018-01-11
> **lisati said:**
> Please post the output of the following, as requested:
```
sudo apt-get update && sudo apt-get upgrade
```

Here are the results:

```

gunderwood@gunderwood-GA-78LMT-USB3:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for gunderwood: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease        
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                
Hit:4 http://ppa.launchpad.net/mc3man/avidemux1/ubuntu xenial InRelease                                    
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                 
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                                                 
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                              
Hit:9 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease                                     
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [699 kB]                     
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [424 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [653 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [384 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [227 kB]      
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [572 kB]             
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [533 kB]          
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [186 kB]      
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [231 kB]       
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]       
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [271 kB]             
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [16.2 kB]              
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [15.3 kB]               
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]       
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]           
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,712 B]     
Get:27 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.4 kB]              
Get:28 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [57.6 kB]
Get:29 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:30 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:31 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3,208 B]
Get:32 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [3,380 B]
Fetched 5,287 kB in 4s (1,116 kB/s)                        
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  flashplugin-installer                                                                                     
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                                              
Need to get 6,806 B of archives.                                                                            
After this operation, 0 B of additional disk space will be used.                                            
Do you want to continue? [Y/n] y                                                                            
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 flashplugin-installer amd64 28.0.0.137ubuntu0.16.04.1 [6,806 B]                                                                               
Fetched 6,806 B in 0s (28.4 kB/s)                                                                           
Preconfiguring packages ...                                                                                 
(Reading database ... 214289 files and directories currently installed.)                                    
Preparing to unpack .../flashplugin-installer_28.0.0.137ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (28.0.0.137ubuntu0.16.04.1) over (28.0.0.126ubuntu0.16.04.1) ...
Processing triggers for update-notifier-common (3.168.5) ...
flashplugin-installer: processing...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180109.1.orig.tar.gz
Get:1 http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180109.1.orig.tar.gz [30.5 MB]
Fetched 30.5 MB in 20s (1,508 kB/s)                                                                        
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20180109.1.orig.tar.gz
Flash Plugin installed.
Setting up flashplugin-installer (28.0.0.137ubuntu0.16.04.1) ...
gunderwood@gunderwood-GA-78LMT-USB3:~$

```

---

### Post by QIII on 2018-01-11
Thank you.

Unfortunately, since you used the GUI to set the package manager to disregard cert warnings before you posted that, there is nothing there to go on.  All of the images in your previous post indicate that the links are protected by SSL and are safe.

Can you post an image from the GUI giving you a cert warning?

---

### Post by MoeNeigh on 2018-01-11
This is the warning I get each time I enter the GUI Software Center (Discover):

[ATTACH=CONFIG]278154[/ATTACH]

---

### Post by QIII on 2018-01-11
I suspect that is a bug in Muon Discover, which would be reportable against the Muon package.  I've never had good luck with Muin.

Before we go there, let's install and test Synaptic:

```
sudo apt install synaptic 
```

Run Synaptic in Admin mode and try to update.

---

### Post by vasa1 on 2018-01-11
Could you try running```
plasma-discover
```from the terminal? Then post back the terminal output.

And please explain how you normally launch/use Discover and for what purpose. In the few times I've used it only to update software, I haven't encountered anything about certificates, unsafe or not.

But I, and a decent number of others, prefer to use the terminal to install, update or remove software. It's much quicker and lighter on resources. It's also easier to troubleshoot.

Another suggestion is to add *kubuntu-backports* to your system. I've done that on my Kubuntu 16.04 (see image). Most if not all your software will be replaced by newer (and mostly better) versions.

If you want to look at this further be warned it'll be a massive download. From [https://www.kubuntuforums.net/showthread.php/72006-Latest-round-of-backports-PPA-updates-include-Plasma-5-10-2-for-Zesty-17-04?p=401636&viewfull=1#post401636](https://www.kubuntuforums.net/showthread.php/72006-Latest-round-of-backports-PPA-updates-include-Plasma-5-10-2-for-Zesty-17-04?p=401636&viewfull=1#post401636)> 
The PPA can be added manually in the Konsole terminal with the command:

```
sudo add-apt-repository ppa:kubuntu-ppa/backports
```

and packages then updated with

```
sudo apt update
sudo apt full-upgrade
```If you're interested, please read the link.

---

### Post by vasa1 on 2018-01-12
I've been reading a bit about Discovery. There's a long piece on it here: [https://userbase.kde.org/Discover](https://userbase.kde.org/Discover). In there, you'll find> An Application Installer for the 22nd Century
My take is that, well-intentioned as its developers maybe, it isn't ready for general use in 16.04.

---

### Post by MoeNeigh on 2018-01-12
I mainly use Discover for convenience. It notifies me when updates are available. I used to send myself two email reminders each week and then do the updates via a terminal. In the case of the invalid certificates warning, if I went to a terminal, I got the message that 14 updates were being held back but no reason and no way to remedy this to get the updates. In Discover, an invalid certificate warning appeared, but I could choose to get the updates anyway if I waived the certificate warning. Also, Discover identified the updates as coming from a trusted server despite the warning. Weird! Again, the updates were libdrm and mesa updates. So I wonder why in a terminal, there was no option to get those updates that were being held back, but in Discover this option existed.

Additionally, I do have backports installed. I do need to get better at finding information via a terminal. Discover, by selecting "Configure sources" shows what sources I have installed. Backports shows up there.

---

