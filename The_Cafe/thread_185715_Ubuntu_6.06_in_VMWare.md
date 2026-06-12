---
title: "Ubuntu 6.06 in VMWare"
date: 2006-06-01
forum: The Cafe
---

### Post by PenguinMan on 2006-06-01
[COLOR=Sienna]I was able to download the Ubuntu 6.06 ISO within an hour this evening. Not bad...:) 

I installed it in VMware Workstation 5.5.1, to test it out quickly, and I find it is very fast! I am quite impressed with this new version of Ubuntu. My hat goes off to the programming team... :mrgreen: 

This weekend and next week, I will be testing this new version on our systems. I will issue a press release on our website when we are ready to support Ubuntu, Kubuntu, Xubuntu on our SeaScape computers.
[/COLOR]

---

### Post by lex1 on 2006-06-01
Hi


thats good news for me I have 5.10 server with fluxbox and vmware bets server need to know how to upgrade?

Lex1

:)

---

### Post by Rackerz on 2006-06-01
Nice! Can VMWare locate and let me run Windows from my other drive in Linux?

---

### Post by imagine on 2006-06-01
[QUOTE=Rackerz]Nice! Can VMWare locate and let me run Windows from my other drive in Linux?[/QUOTE]
That may be possible but it's very difficult. Actually VMware was made to run *virtual* machines, ie you start VMware and then install the operating system in there.

---

### Post by Rackerz on 2006-06-01
[QUOTE=imagine]That may be possible but it's very difficult. Actually VMware was made to run *virtual* machines, ie you start VMware and then install the operating system in there.[/QUOTE]

Yeah I guessed that, Oh well I'll live with installing it virtually :D.

---

### Post by Brynster on 2006-06-01
Hey James

Good to see you here


6.06 looks very well when real world installed as well as virtual.

---

### Post by kanter on 2006-06-01
if you upgrade your vm-guest from breeze, X crashes if you had installed vmware-tools. to reconfigure X just replace xorg.conf by xorg.conf.BeforeVMwareToolsInstall (in /etc/X11). then you could start X and maybe reinstall vmwaretools.

---

### Post by PenguinMan on 2006-06-01
[quote=Brynster]Hey James

Good to see you here


6.06 looks very well when real world installed as well as virtual.[/quote]
[COLOR=Sienna]Hey Brynster!

I did not know you were over here. Usually I see you at the Linspire forums... :)

I am downloading Kubuntu 6.06 right now. 45 minutes to go... :-D I took a look at the screen shots from OSDir - wow! Kubuntu looks great now too! Before installing on a hard drive, I always test stuff out in VMWare completely. The speed of Ubuntu in a virtual environment is absolutely impressive IMHO.

This weekend, I will be testing these out on our DVD-ROM-only system - Live CD mode. Then I will test them on some other systems and see how they run. I expect all testing to go well... :mrgreen:

Regards,
James
[/COLOR]

---

### Post by PenguinMan on 2006-06-01
[COLOR=Sienna]I just finished looking at Kubuntu and Xubuntu, and I am quite impressed with both of them. Xubuntu's GUI is very fast IMO.
[/COLOR]

---

### Post by nalmeth on 2006-06-01
[COLOR=Sienna]> I just finished looking at Kubuntu and Xubuntu, and I am quite impressed with both of them. Xubuntu's GUI is very fast IMO. 
[COLOR=Black]Couldn't agree more. Finally supporting desktop icon's and all the included panel applet's are terrific.

My old laptop is a viable, useful computer thank's to Xubuntu.

BTW just browsing you site, never heard of your company before. It's nice to see corporate support and use of linux!

I must say that woman talking on the homepage is a little weird though. Just first impression, that's all :)
EDIT: Kind of like how she follows the cursor with her eye's!
[/COLOR][/COLOR]

---

### Post by lex1 on 2006-06-02
got 6.06 up and running  as per the 2nd post in this thread but all sorts of problems with vmware


here are two points here WRITELOCK and READLOCK there also seems to be two instances of win20003 server?


I removed WRITLOCK only to find it appers again not as a vmdk extension but as a
vmem extension?

--------------------------------------------------------------------------------------------------------



-rw------- 1 vmadmin vmadmin 96260096 2006-05-17 07:25 core
-rw------- 1 vmadmin vmadmin 8664 2006-05-28 05:56 nvram
-rw-r--r-- 1 vmadmin vmadmin 66010 2006-05-28 05:16 vmware-0.log
-rw-r--r-- 1 vmadmin vmadmin 22606 2006-05-28 01:24 vmware-1.log
-rw-r--r-- 1 vmadmin vmadmin 74510 2006-05-27 20:31 vmware-2.log
-rw-r--r-- 1 vmadmin vmadmin 39960 2006-05-28 06:06 vmware.log
-rw------- 1 vmadmin vmadmin 15034548224 2006-05-28 06:08 Windows Server 2003 S
tandard Edition-000001.vmdk
-r--r--r-- 1 vmadmin vmadmin 11 2006-05-28 05:56 Windows Server 2003 S
tandard Edition-000001.vmdk.WRITELOCK
-rw------- 1 vmadmin vmadmin 16106127360 2006-05-08 13:59 Windows Server 2003 S
tandard Edition-flat.vmdk
-rw------- 1 vmadmin vmadmin 327155712 2006-05-08 14:00 Windows Server 2003 S
tandard Edition-Snapshot1.vmem
-rw------- 1 vmadmin vmadmin 17913153 2006-05-08 14:00 Windows Server 2003 S
tandard Edition-Snapshot1.vmsn
-rw------- 1 vmadmin vmadmin 377 2006-05-08 13:56 Windows Server 2003 S
tandard Edition.vmdk
-r--r--r-- 1 vmadmin vmadmin 11 2006-05-28 05:56 Windows Server 2003 S
tandard Edition.vmdk.READLOCK
-rw------- 1 vmadmin vmadmin 502 2006-05-08 13:59 Windows Server 2003 S
tandard Edition.vmsd
-rwxr-xr-x 1 vmadmin vmadmin 1188 2006-05-28 05:56 Windows Server 2003 S
tandard Edition.vmx
vmadmin@xstation:/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition$ cd /var/lib/vmware/Virtual\ Machines/Windows\ Server\ 2003\ Standard\ Edition/Windows\ Server\ 2003\ Standard\ Edition-000001.vmdk.WRITELOCK
bash: cd: /var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition/Windows Server 2003 Standard Edition-000001.vmdk.WRITELOCK: Not a directory
vmadmin@xstation:/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition$ rm /var/lib/vmware/Virtual\ Machines/Windows\ Server\ 2003\ Standard\ Edition/Windows\ Server\ 2003\ Standard\ Edition-000001.vmdk.WRITELOCK
rm: remove write-protected regular file `/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition/Windows Server 2003 Standard Edition-000001.vmdk.WRITELOCK'? yes
vmadmin@xstation:/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition$ ls -la
total 30908772
drwxr-xr-x 2 vmadmin vmadmin 4096 2006-05-28 06:12 .
drwxrwxrwt 3 root root 4096 2006-05-08 10:10 ..
-rw------- 1 vmadmin vmadmin 482344960 2006-05-28 05:56 564dc83d-83fa-7495-a504-89ddbe97818a.vmem
-r--r--r-- 1 vmadmin vmadmin 11 2006-05-28 05:56 564dc83d-83fa-7495-a504-89ddbe97818a.vmem.WRITELOCK
-rw------- 1 vmadmin vmadmin 96260096 2006-05-17 07:25 core
-rw------- 1 vmadmin vmadmin 8664 2006-05-28 05:56 nvram
-rw-r--r-- 1 vmadmin vmadmin 66010 2006-05-28 05:16 vmware-0.log
-rw-r--r-- 1 vmadmin vmadmin 22606 2006-05-28 01:24 vmware-1.log
-rw-r--r-- 1 vmadmin vmadmin 74510 2006-05-27 20:31 vmware-2.log
-rw-r--r-- 1 vmadmin vmadmin 41279 2006-05-28 06:11 vmware.log
-rw------- 1 vmadmin vmadmin 15034548224 2006-05-28 06:12 Windows Server 2003 Standard Edition-000001.vmdk
-rw------- 1 vmadmin vmadmin 16106127360 2006-05-08 13:59 Windows Server 2003 Standard Edition-flat.vmdk
-rw------- 1 vmadmin vmadmin 327155712 2006-05-08 14:00 Windows Server 2003 Standard Edition-Snapshot1.vmem
-rw------- 1 vmadmin vmadmin 17913153 2006-05-08 14:00 Windows Server 2003 Standard Edition-Snapshot1.vmsn
-rw------- 1 vmadmin vmadmin 377 2006-05-08 13:56 Windows Server 2003 Standard Edition.vmdk
-r--r--r-- 1 vmadmin vmadmin 11 2006-05-28 05:56 Windows Server 2003 Standard Edition.vmdk.READLOCK
-rw------- 1 vmadmin vmadmin 502 2006-05-08 13:59 Windows Server 2003 Standard Edition.vmsd
-rwxr-xr-x 1 vmadmin vmadmin 1188 2006-05-28 05:56 Windows Server 2003 Standard Edition.vmx
vmadmin@xstation:/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition$ rm /var/lib/vmware/Virtual\ Machines/Windows\ Server\ 2003\ Standard\ Edition/Windows\ Server\ 2003\ Standard\ Edition-vmdk.READLOCK
rm: cannot remove `/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition/Windows Server 2003 Standard Edition-vmdk.READLOCK': No such file or directory
vmadmin@xstation:/var/lib/vmware/Virtual Machines/Windows Server 2003 Standard Edition$






lex1:(

---

### Post by PenguinMan on 2006-06-02
[quote=nalmeth][COLOR=Sienna] [COLOR=Black]
BTW just browsing you site, never heard of your company before. It's nice to see corporate support and use of linux!

I must say that woman talking on the homepage is a little weird though. Just first impression, that's all :)
EDIT: Kind of like how she follows the cursor with her eye's!
[/COLOR][/COLOR][/quote] [COLOR=Sienna]hehehe I love SitePal - very cool idea IMO.

We started with Linspire late last year, added Xandros (mostly for business customers), then added PCLinuxOS. I am going to be testing the new versions of Ubuntu, Kubuntu, Xubuntu (maybe Edubuntu) for more choice in the Linux area. Once I finish testing we will issue a press release on our site for Ubuntu, etc.
[/COLOR]

---

### Post by Mathias-K on 2006-06-02
Perhaps it won't be long before they release a virtual appliance on the VMWare site? That's kinda convenient to have it preinstalled :)

---

### Post by Zenyatta13 on 2006-06-02
>  	if you upgrade your vm-guest from breeze, X crashes if you had installed vmware-tools. to reconfigure X just replace xorg.conf by xorg.conf.BeforeVMwareToolsInstall (in /etc/X11). then you could start X and maybe reinstall vmwaretools.

Supposing I didn't know how to fix that ](*,) and instead wiped out breezy and did a fresh install of Dapper in my vm-guest... 

Were you able to get vmware-tools working again in Dapper?  I tried installing, compiling the modules and such, which seemed to work okay, but then my network connection stopped working (even after reboots) and the VMware script said there was no X server so it didn't bother updating it... so I only can view at 1024x768.

Has anyone gotten VMware tools working with a Dapper guest?

Thx!

-Z

---

### Post by B0rsuk on 2006-06-02
Please, can you clarify ? I don't exactly understand the capabilities of Vmware Player versus paid versions of this software.

Would it be possible to run some windows games with it ? (assuming another OS can be installed inside vmware player). Games are very important.

---

### Post by ubuntu_demon on 2006-06-02
warning about vmware-player and possible fix
[http://www.ubuntuforums.org/showthread.php?t=186313](http://www.ubuntuforums.org/showthread.php?t=186313)

---

### Post by Zenyatta13 on 2006-06-02
[QUOTE=Zenyatta13]Were you able to get vmware-tools working again in Dapper?  I tried installing, compiling the modules and such, which seemed to work okay, but then my network connection stopped working (even after reboots) and the VMware script said there was no X server so it didn't bother updating it... so I only can view at 1024x768.[/QUOTE]

In case anyone else is having this problem... here's what I found:

For the X issue, it is because the X server is version 7.  vmware-config-tools.pl is only aware of versions up to 6.  This link was helpful in modifying the script enough to make it happy.  Note that I just did the patch and the vmmouse thing.  I did not download their code as they suggested.

[http://www.clendenen.net/index.php?option=com_content&task=view&id=14&Itemid=28](http://www.clendenen.net/index.php?option=com_content&task=view&id=14&Itemid=28)

Regarding the networking thing, it seems that if you follow the suggestion from the vmware-config script, it works itself out...

/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/networking start

I am guessing that depmod -a is important.

Hope this helps someone...

-Z

---

