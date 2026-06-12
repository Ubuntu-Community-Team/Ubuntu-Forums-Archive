---
title: "How I Got vmware server working in feisty 64bit"
date: 2007-04-21
forum: Server Platforms
---

### Post by borahshadow on 2007-04-21
Wow it was more difficult then I ever imagined but I finally got it installed I have not tested a vm in it yet but I don't see why it won't work
I got most of these things from various places but mostely  [this thread]("http://ubuntuforums.org/showthread.php?t=338305&highlight=feisty+vmware+server") and I got one command from the vmware server forums

I tried marceloshima's suggestion but it didn't work for me at first but you should be able to use that instead of the any any patch but make sure you follow step 1 which ever way you do

**Thanks handband2 as most  of these commands are copied from your post I hope you don't mind I just had to add a few things**

ok
Step 1 install nessassary packages
> sudo apt-get install build-essential xinetd vmware-server-kernel-modules **ia32-libs**    (this was the key for me)
Step 2 download and extract vmware
> wget [http://download3.vmware.com/software/vmserver/VMware-server-1.0.2-39867.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.2-39867.tar.gz)
> tar -zxvf VMware-server-1.0.2-39867.tar.gz
Step 3 Change Directory and start install
> cd ./vmware-server-distrib
> sudo ./vmware-install.pl
just let it get to the error with modules and quit
Step 4 any any update (this is where you could try marceloshima's suggestion starting at step 3 if you want to)
> cd ~
> wget [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz)
> tar -zxvf vmware-any-any-update109.tar.gz
> cd ./vmware-any-any-update109
> sudo ./runme.pl
now when i was experimenting to find out what my problem was (the ia32-libs) it would give me an error about kernel sources don't match with kernel I just ran it again and it would work for me but the ia32-libs might have fixed that
Step 5 start it up
> vmware

I did this on version 1.02 but it should work on others too

I hope this helps someone and I hope I don't anger anyone by adding to their fix but that thread is buired and very full anyway so I thought i would start a newone rather then post in that thread (I think it was closed anyway)

---

### Post by chatuser on 2007-04-22
If use Ubuntu 7.04 (32 bits) and I just need:

sudo apt-get install build-essential xinetd

The packages vmware-server-kernel-modules ia32-libs are not necessary for 7.04 32 bits.

I have create a personalized launcher on the top panel because the program icon has disappeared after the path, I have done this:

Add to panel --> personalized launcher
Type: Application, Name: VMware Server, Command: vmware, comment: Run and manage virtual machines
Press "No icon" button and select /usr/share/icons/hicolor/48x48/apps/vmware-server.png

Thanks for your help

---

### Post by Rambie on 2007-04-24
Thanks guys!  I was having a **** of a time getting VMWare installed on my Feisty 32bit.  I decided to try VMWare instead of XEN because I heard it was easier to setup than XEN.   

VMWare worked great on Edgy but on Feisty I wonder if XEN wouldn't have been easier to setup.  :)

---

