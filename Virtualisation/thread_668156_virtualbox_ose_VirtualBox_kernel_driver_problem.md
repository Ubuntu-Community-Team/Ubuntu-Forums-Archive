---
title: "virtualbox ose VirtualBox kernel driver problem"
date: 2008-01-15
forum: Virtualisation
---

### Post by jcer93705 on 2008-01-15
Ok, I want to just boot linux, not dual boot xp, but I'm having problem
with virtualbox OSE, Program do start, yet when i try to run
it to install an os this comes up. How do i fix this?


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by rechick on 2008-01-15
2 things:
1 - reboot after Virtualbox OSE installed
2 - Make sure you are a member of the virtualbox group under groups and users.

---

### Post by rax_m on 2008-01-18
i've just installed virtualbox and am having the same issues. 

@rechick - neither of those is the problem (in my case) 

@jcer93705 - I think in my case it might be b'cos I have a custom kernel.. so I don't really know what to do know.. more googling to do. 

Do you have a custom kernel?

---

### Post by gvartser on 2008-01-18
You need to install the virtualbox-ose  kernel modules.

Im guessing that you are using  generic kernel and not a server.

1) Find out what type of kernel you are using:
#) [COLOR="SeaGreen"]uname -r[/COLOR]


2) Then install the correct kernel module for virtualbox:

NOTE!
Change the kernel version to the one that you are using.

GENERIC: 
#)  [COLOR="SeaGreen"]sudo apt-get install virtualbox-ose-modules-2.6.xx-xx-generic[/COLOR]

SERVER:
#) [COLOR="SeaGreen"]sudo apt-get install virtualbox-ose-modules-2.6.xx-xx-server[/COLOR]

Best regz,
/G

---

### Post by jcer93705 on 2008-01-19
All i needed to do is sudo vitrualbox enter the password and then it works, try that.

---

### Post by RealG187 on 2008-01-30
The bootloaders dont go for me... (See screenshot)

---

### Post by balachandarlinks on 2008-06-08
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose-modules-2.6.24-18-generic


  For me the outpit is like this....What will i do....

---

### Post by pellea on 2008-06-09
The package virtualbox-ose-modules-2.6.24-18-generic is not released yet but is available as a proposed package. Wait a few days and you will be able to install it or enable hardy-proposed as a package source.

To enable hardy-proposed, open System->Administration->Software Sources and click on the Updates tab. Check the box for Pre-released updates.

Your package-list should be updated when you close the Software Sources window. If not do a: 
[FONT="Fixedsys"]sudo apt-get update[/FONT]

Now you should be able to install the correct package with:
[FONT="Fixedsys"]sudo apt-get install virtualbox-ose-modules-2.6.24-18-generic[/FONT]
or preferable the meta package pointing to the current version:
[FONT="Fixedsys"]sudo apt-get install virtualbox-ose-modules-generic[/FONT]

Unless you want to run proposed versions of everything you should go back into Software Sources and uncheck the box for Pre-released updates.

---

### Post by Jensss on 2008-06-09
> **jcer93705 said:**
> Ok, I want to just boot linux, not dual boot xp, but I'm having problem
with virtualbox OSE, Program do start, yet when i try to run
it to install an os this comes up. How do i fix this?


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


I have exactly the same problem but with the Sun closed version.
How do I instal the kernel modules for that one?
Thanks

---

### Post by Jensss on 2008-06-09
> **Jensss said:**
> I have exactly the same problem but with the Sun closed version.
How do I instal the kernel modules for that one?
Thanks

I've just found a solution!
There is no /etc/init.d/vboxdrv
But there is /etc/init.d/vboxdrv.dpkg-list
Just do:

```
sudo /etc/init.d/vboxdrv.dpkg setup
```

Then VB should work fine!

---

### Post by Svartalf on 2008-06-09
> **pellea said:**
> Unless you want to run proposed versions of everything you should go back into Software Sources and uncheck the box for Pre-released updates.

The big problem is...  We've went to -19 on things, with the suggested settings- and NO VirtualBox drivers at the time of the update.  

If it's a set of kernel modules, I don't care WHAT the purpose is, and if it's part of the supported stuff, it needs to come out at the same time- unless there's some seriously pressing security bug fixing being done to the kernel.

This has happened twice already with Hardy as best as I can tell- with the suggested settings.  I don't mind having a high level of churn on package updates, just make sure that if you're touching the kernel that it's a unified rollout of EVERYTHING impacted by it.

---

### Post by Svartalf on 2008-06-11
> **pellea said:**
> Unless you want to run proposed versions of everything you should go back into Software Sources and uncheck the box for Pre-released updates.

After the proposed release version of the kernel pretty much made my laptop deaf and dumb (No wireless, no wireline LAN...) with a pretty much vanilla, supported set of chipsets (Intel...) for the same, I think it's probably a GOOD idea unless you're willing to take big chances on things to NOT run with proposed versions on.  After turning it off and backing down to -18 from -19, things all started working again- including VirtualBox.

One wonders if there's any solid auditing of these updates or not based on the problems with VirtualBox's kernel modules and what I just encountered right now with my laptop.

---

### Post by honse246 on 2008-06-30
> **jcer93705 said:**
> Ok, I want to just boot linux, not dual boot xp, but I'm having problem
with virtualbox OSE, Program do start, yet when i try to run
it to install an os this comes up. How do i fix this?


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

im getting the exact same message 
ive done everything in this form and non of it works!
i rly want this working!!!!

---

### Post by starcannon on 2008-06-30
I don't use the OSE, I use the monetarily free CSE, no problems.
You can get it here:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by HestGrise on 2008-10-06
> **gvartser said:**
> You need to install the virtualbox-ose  kernel modules.

Im guessing that you are using  generic kernel and not a server.

1) Find out what type of kernel you are using:
#) [COLOR="SeaGreen"]uname -r[/COLOR]


2) Then install the correct kernel module for virtualbox:

NOTE!
Change the kernel version to the one that you are using.

GENERIC: 
#)  [COLOR="SeaGreen"]sudo apt-get install virtualbox-ose-modules-2.6.xx-xx-generic[/COLOR]

SERVER:
#) [COLOR="SeaGreen"]sudo apt-get install virtualbox-ose-modules-2.6.xx-xx-server[/COLOR]

Best regz,
/G

OK, I think I figured out my issue, sorry for all of the editing

---

### Post by Dareajoe on 2008-12-05
he Intel Graphics Kernel Mode Driver is really slowing down my computer, according to performance information, but the problem is I don't know what it is, or if it would be wise to uninstall it.Can someone help me out here?Should I uninstall this?I have to do SOMETHING though, because my computer is too slow for my liking...

---

### Post by hyburn on 2010-01-07
thanks it was fixed for me

---

