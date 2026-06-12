---
title: "How to install Ubuntu on a Sun Enterprise 250?"
date: 2008-01-25
forum: Sun Sparc Users
---

### Post by jannik on 2008-01-25
Hi everybody ;-),

I have currently get, an very old Sun Enterprise 250 today to my test Apache server. So i think i want to use Ubutu 6 server. But to anyone knows how to install it on a Sun?

I have read at google hits, i just write "boot cdrom". But where can i write it? When a turn on my Sun SunOS 5.8 starts up, in the start can i go in mantaince mode or SunOS - i have try both of those options but without result.

Is anyone fresh to help.

Anyway, thanks a lot for your time

---

### Post by jannik on 2008-01-26
I have currently found out. When the memory has loaded - is the only job to press "STOP" (botton) and "A". after that write "boot cdrom".

Thanks anyway

---

### Post by tizzo513 on 2008-04-18
I was talking to a vender from sun that worked on these servers.

I was having the same problem installing Ubuntu on my server, it would not read the boot file from the Cd rom.  

He told me to try burning the Ubuntu ISO on the slowest speed possible or use an older cdrom drive to burn it on and then retry it.

I will let you know this weekend if it works.

Good luck let me know.

Tizzo513

---

### Post by robbith on 2008-05-09
> **tizzo513 said:**
> ...try burning the Ubuntu ISO on the slowest speed possible or use an older cdrom drive to burn it on and then retry it...

I used the SPARC version of Ubuntu Server 7.10 and burnt it at about 4x, this has done the job.

I would also recommend changing a few settings in OpenBoot before you go ahead with the install. I had a few problems getting a DHCP address and setting up the drives until I reset OpenBoot. The first thing I did was reset everything to default:

```
{0} ok set-defaults
```

Then I setup the default boot order, first I had a look at my device names:

```
{0} ok devalias
```

The above command gives you a list of device names in 'short form' so you don't have to type out the full name, eg: 'sbus/SUNW,hme@e,blah' has the name 'disk0'. Then, to set the boot order just use:

```
{0} ok setenv boot-device cdrom disk0
```

This will make the machine boot from the cdrom drive first, then move to disk0. Obviously you can choose other devices like net or tape etc.

Then make sure it's not going to auto-boot while you're trying to do the setup:

```
{0} ok setenv auto-boot? false
```

Run everything, make sure it's working to your requirements, then just set auto-boot to be active:

```
{0} ok setenv auto-boot? true
```

These steps worked for me. The only thing I've noticed is that the installer did not have any RAID options which is disappointing. I've got 4 x 18gb and 2 x 36gb drives in this machine and I would've liked to setup the RAID in the initial setup. I'm going to try doing it manually now that I've got the install up and running.

---

### Post by d@v3 on 2008-06-20
I've followed the above to install ubuntu 6.10 on an E250.

However, on (2) different E250s, the following is displayed:


 ... rtc_init: no PC rtc found
 * Activating swap...                                                    [ ok ]
 * Checking root file system...                                                 fsck 1.39 (29-May-2006)
/dev/sdc2: clean, 16952/1042432 files, 145136/2084575 blocks
                                                                         [ ok ]
 * Checking file systems...                                                     fsck 1.39 (29-May-2006)
/dev/sdc1: clean, 30/48480 files, 17701/96957 blocks
                                                                         [ ok ]


...and then the boot hangs.

I was able to install from this same CD onto a Netra T1.

Any suggestions?

---

### Post by d@v3 on 2008-06-20
I'm working with ubuntu 6.10 because of other applications' (VMware) support for this particular version.

---

### Post by d@v3 on 2008-06-21
E250 configuration:
 - 512MB RAM
 - 2 processors
 - 4x 9G disks

---

### Post by d@v3 on 2008-06-21
I'll try the debug options on boot to see if it shows where things are hanging up.

---

### Post by d@v3 on 2008-06-30
It appears the missing link was the input-device and output-device values in NVRAM:  I was still using the RSC module for console access.  After I reset NVRAM, and "console connected" to ttya instead, the boot completed without incident.

---

### Post by sarathytcs on 2008-07-15
Hello Friends,

I will tell you folks a quick hack to get installed with any flavours of guest Operating system you want to install on your native OS. The solution is  Sun's xVM VirtualBox - Desktop Virtualization Tool.

Using the above tool, I installed Ubuntu on my Lenovo laptop running Windows Vista so easily, so now I can play around with Ubuntu from my Vista, check out [my **_blog entry_**]("http://parth2020.blogspot.com/2008/06/sun-xvm-virtualization-story.html") , where in I have posted the snapshots of ubuntu running on my Vista.

You can try downloading Virtualbox from [www.virtualbox.org](www.virtualbox.org) on Enterprise 250 , alongside please do have a ubuntu iso image , then using Sun's xVM Virtualbox, create a Virtualdisk pointing to the Ubuntu iso image / DVD if any,configure the settings as mentioned in the usage guide, thats it done, you can enjoy the features of Ubuntu on the fly:)

Was it useful? , Did it anyone give a try?

Cheers,
Partha

---

