---
title: "upgraded from mint lisa to ubuntu 12.04, not possible??"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hojjat12000 on 2012-03-12
hi

I have Linux Mint 12 (lisa), I upgraded my kernel to 3.2 and I was happy. Yesterday I changed "software sources" and changed "lisa" to "precise", so using that trick I was able to download ubuntu 12.04 packages.

after running "sudo apt-get dist-upgrade" and downloading 1Gb of packages, it started to install those packages... suddenly:

```
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Preconfiguring packages ...
(Reading database ... 333697 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5.1 (using .../libc6_2.15-0ubuntu5_amd64.deb) ...
De-configuring libc6:i386 ...
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /usr/bin/locale)
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/bin/locale)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by whiptail)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /lib/libnewt.so.0.52)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /lib/libnewt.so.0.52)
debconf: whiptail output the above errors, giving up!
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.13-20ubuntu5.1 (using .../libc6_2.15-0ubuntu5_i386.deb) ...
De-configuring libc6 ...
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /usr/bin/locale)
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/bin/locale)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by whiptail)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /lib/libnewt.so.0.52)
whiptail: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /lib/libnewt.so.0.52)
debconf: whiptail output the above errors, giving up!
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu5_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


now I can not install/remove/upgrade/purge nothing!!

What should I do? how can I make apt to forget about everything and just go back to where it was?! or something like that.

Any ideas??

---

### Post by Perfect Storm on 2012-03-13
Moved to Ubuntu +1

---

### Post by hojjat12000 on 2012-03-13
I tried to remove all packages in /var/cahche/apt/archive and try to fix broken packages but I'm not able to remove broken packages, same error.
any ideas??

---

### Post by winh8r on 2012-03-13
The first thing you should do is back up all your data to external media before you try and do anything else.

Mint 12 was based on Ubuntu 11.10 Oneiric Ocelot, the 12 may have led you to believe that it was based on Precise Pangolin 12.04, but this is not the case as 12.04 is still in beta testing stages and is not officially released until April.

It is not a good idea to alter repositories in the way you did as each different "flavour" of Ubuntu has specific requirements and has its own repositories as a result.

If you wish to run Ubuntu Precise Pangolin 12.04 then it would be best to download and install it entirely from scratch, although bear in mind it is beta software and although quite stable it may have bugs which are being worked on before the official release. You should not use beta releases as your main or only operating system, they are released for testing purposes and can in some cases be unstable.

If on the other hand you decide to stay with the stable Linux Mint 12 , then you would probably save yourself a whole lot of trouble by doing a full backup of your data and doing a fresh installation of Mint 12.

Hope this helps you

---

### Post by hojjat12000 on 2012-03-13
thanks for your reply.

how can I backup my softwares?? I don't like downloading them again.

---

### Post by winh8r on 2012-03-13
You could try the following:

Make sure all the changes you made to the software sources are reversed and that there are no references to Ubuntu Precise Pangolin 12.04 in that file. 

restart your machine in recovery mode by holding down the shift key before you switch it on and keep the shift key pressed down until you see the Grub Menu screen.

The first entry should be the newest kernel on your machine, the next entry should have (Recovery Mode) written after it.

Select this option and when it gets to the next screen select "fix broken packages"
Once this has run select "resume normal boot"

Alternatively, you could use an older version of the kernel to boot from if there are older versions listed in the Grub Menu, as these will not have been affected by the changes you made to the newer kernel.
This should take you back to where you were before your last kernel upgrade and retain most of your installed software.
However this will require you to remove the newest kernel version and then update the older one you are now using in order to get rid of the messed up kernel.

You should read up a lot about this before attempting it as a mistake could render your system unusable, so MAKE SURE YOUR PERSONAL DATA IS BACKED UP NOW!.

Have a look here :
[http://forums.linuxmint.com/viewtopic.php?f=90&t=63493]("http://forums.linuxmint.com/viewtopic.php?f=90&t=63493")
hope this is of some help.

---

### Post by mailc on 2012-03-13
You can do it as suggested, but this requires quite a bit of knowledge and even so,  a mistake can be made easily.

- So as an alternative, start out by making a back-up of your personal data.

- Download Unetbootin for Linux and use it to place a Linux Mint  iso file on a USB stick or a CD .

- Install your Linux Mint and make sure that everything works fine.

- Make a separate partition (10 GB )  , use the same Unetbootin to install the  iso of Ubuntu 12.04 Precise on a USB and install it on this partition.

You will have a dual boot on your box/

---

### Post by grahammechanical on 2012-03-13
You have shown me why Linux Mint is not called Ubuntu Mint. It may be built on Ubuntu but there are differences and those differences are so great that the word Ubuntu cannot be used as part of the distribution name.

Regards.

---

### Post by hojjat12000 on 2012-03-13
I switched to older kernels but the problem exist. My Problem is glibc_6 which is required while installing new glibc6 1.5.
It seems that this is a bug, Some body reported it.
I reinstalled mint, when I was installing I just selected not to format this partition, and mint didn't delete my "home" folder, and kept lots of softwares I've installed.
but there is no sound card and waireless detected on my laptop.
mint did detect them in the past, but now every thing is ruined!

I made a copy of my home folder and am going to install a fresh copy, thanks for your support.

I don't have time to waste on learning how to make my drivers work again, I believe that Linux is the only operating system that doesn't need to be re-installed, and every thing can be fixed, but it's a matter of time!

thanks. ;)

---

### Post by sysone on 2012-03-13
> **hojjat12000 said:**
>    ...
 I believe that Linux is the only operating system that doesn't need to be re-installed, and every thing can be fixed, 
....   ;)

Actually neither the first  nor the second statement are completely true.

Nevertheless,   if you do want to try out the new Precise , setting up a dual boot on your computer is the way to go. 

This is neither that difficult nor that time consuming.

---

### Post by jbicha on 2012-03-13
By the way, Linux Mint's official policy is to always do clean installs and never upgrade from one version to the next. It's also not supported to try to upgrade from Linux Mint to Ubuntu; you should do a clean install for that unless you like fixing broken things. :)

---

