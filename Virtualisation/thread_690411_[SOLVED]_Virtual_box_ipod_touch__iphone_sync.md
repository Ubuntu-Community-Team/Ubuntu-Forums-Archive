---
title: "[SOLVED] Virtual box ipod touch / iphone sync"
date: 2008-02-07
forum: Virtualisation
---

### Post by asphixmx on 2008-02-07
Hello everyone. I am trying to sync my iPod Touch with iTunes, using Virtualbox, also with Parallels 2.2 and no luck. WIndows can see the iPod, but when I open iTunes, it says can't sync with iPhone because of an unknown error. I tried to stop the Apple Mobile Device Service, then started again... iTunes says the same.
I have been reading and searching a lot trying to find a solution with no luck. Is there anyone working with Ipod touch / iphone AND iTunes in a virtual machine? VMWare, Wine, Virtual Box, Parallels...anything?
I just don't want to use my windows partition anymore... I am using it just for sync.

Yes, yes... I can sync my songs with Amarok, but since it is wireless, it is sooo slow. Also my contacts and appoinments don't sync. That is why I need iTunes and Outlook.

Any idea? Any one?

Thanks!

---

### Post by azanutta on 2008-02-07
same problem.
no solution jet =((

---

### Post by myusername on 2008-02-07
Exactly my problem...

---

### Post by fdelosrios on 2008-02-11
Mine even crashes when I plug it. I hope someone comes up with a solution because wireless sync is too slow.

---

### Post by AndThenWhat on 2008-04-29
I also have this problem on hardy.  While browsing online I saw that someone submitted a ticket on the virtual box website for this exact problem on April 14th.  Hopefully, they will be working on this and fix it soon. :(

---

### Post by ajkiwi88 on 2008-07-04
hey
sorry to bump an old thread was wondering if their is a solution to this problem yet i am using ubuntu 8.04 and the latest virtual box

---

### Post by asphixmx on 2008-07-07
ajkiwi, I am syncing with gtkpod (music, videos), funambol (contacts) using wireless. At this time, there is not yet a solution with itunes (vbox).

---

### Post by Im_Original on 2008-09-24
Hey everybody, 

I just got an iPod touch, so I'm wondering about this too. I found this: 

[http://docs.info.apple.com/article.html?artnum=61683](http://docs.info.apple.com/article.html?artnum=61683)

Which basically says "you can't use the iPod with iTunes in a VM" and doesn't say why. So, it looks like a problem with iTunes which means . . . it will never be fixed. 

Oh well.

---

### Post by asphixmx on 2008-09-24
I can sync now, with VMWARE Workstation 6.04 (instead of Virtual Box), in a virtual machine of Windows XP & iTunes. I activated USB 2.0 support in the Vmware. No problems at all, ipod touch is recognized with no problems, everything runs fine now with VMware. Sorry for VirtualBox, VMWare won this time!

---

### Post by Im_Original on 2008-09-24
well, that's good news. VMWare, here I come!

---

### Post by jack frost on 2008-09-26
> **Im_Original said:**
> well, that's good news. VMWare, here I come!
did it work for you in vmware?

---

### Post by trmentry on 2008-09-26
not to hijack this.. but i had a similar issue with a vpn program for work.  it used a usb dongle to auth the software to run.  the dongle would be seen in virtualbox, but software in the virtualbox xp vm didn't like it.

changed over to vmware workstation and dongle worked and software was happy.  

so there is something about usb2.0 in virtualbox that isn't quite right.

the $ for vmware workstation was worth it in my mind for this functionality.

i'd much prefer free though....

---

### Post by jack frost on 2008-09-26
Isn't there a free version of vmware in ubuntu.. or is that just the 30 day eval? I think I remember installing it in 7.04 with automatix but couln't remember if it was free or not. In virtual box there is a box under usb that says enable usb2 support. that didn't work for you?.. I just bought my iphone today online and have to wait for it to be shipped to me, so i can't test that out.. but my printer any everything else usb works ok in virtual box.. I had to use a fix though.. that I found in the forums:
 
Lets Install the essential build utilities so the vbox kernel module builds.
sudo apt-get install build-essential linux-headers-`uname -r`
Install i386 VirtualBox without repository:
wget [http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb
Install amd64 Virtualbox without repository:
wget [http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb
 
Check Here for updated Virtualbox Packages since the repository isnt added yet
Alternate install with Gutsy repository as some people have suggested works fine, just copy/paste these exact commands into the terminal:
sudo sh -c 'echo "# VirtualBox repository for Ubuntu Gutsy
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free" \
> /etc/apt/sources.list.d/gutsy-virtualbox.list'
wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install virtualbox
Now you Must add your self to the vboxusers group:
sudo adduser $USER vboxusers
Adding user `ionstorm' to group `vboxusers' ...
Adding user ionstorm to group vboxusers
Done.
 
Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
 
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
 
Ok now logoff, then log back in so the vbox driver see's you are logged in to the vboxusers group.
If the above doesnt work try rebooting, if that doesnt enable usb you can try this:
Grab the vboxusers group id:
grep vbox /etc/group
vboxusers:x:124:ionstorm
Edit the fstab with the group id # in bold:
sudo gedit /etc/fstab
Append this to the fstab then save/exit:
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
Now lets edit the mountkernfs.sh file with the gid in bold:
sudo gedit /etc/init.d/mountkernfs.sh
Paste the 2 lines below above the line: "# Mount spufs, if Cell Broadband processor is detected"
## Mount the usbfs for use with Virtual Box
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=124,devmode=664
You may not need to reboot, try doing:
sudo /etc/init.d/mountkernfs.sh

---

### Post by jack frost on 2008-10-08
> **Im_Original said:**
> well, that's good news. VMWare, here I come!
[I]I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")

In particular, I did this:

[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT][/I]

---

### Post by jamesmcq24 on 2008-10-10
confirmed this works!! i am very happy to be able to sync my iPhone 3g on Windows XP through virtualbox. AMAZING!!

> **jack frost said:**
> [I]I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")

In particular, I did this:

[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT][/I]

---

### Post by leonardoxiao on 2008-10-14
> **jamesmcq24 said:**
> confirmed this works!! i am very happy to be able to sync my iPhone 3g on Windows XP through virtualbox. AMAZING!!

Just wondering are you guys using virtualbox ose version or non-free version? Or it doesn't matter?

---

### Post by jack frost on 2008-10-14
> **leonardoxiao said:**
> Just wondering are you guys using virtualbox ose version or non-free version? Or it doesn't matter?
 
 
I am using the the debian package version 2.0..I just downloaded it from their site..  free ose... version..    just a reminder .. my kernel updated and I had to recompile the virtual box kernerl and run the iphone  fix again after I updated..

---

### Post by Macchia on 2008-10-19
Just as a reminder:

** DON'T TRY UPGRADING OR RESTORING FIRMWARE WITHIN VIRTUALBOX **

as you may think, yes, i ****** up my iphone :D

---

### Post by cisoprogressivo on 2008-10-21
This fix doesn't work for me with Ubuntu Intrepid, VirtualBox 2.0.2 and iPod Touch 1G.

---

### Post by jack frost on 2008-10-21
> **cisoprogressivo said:**
> This fix doesn't work for me with Ubuntu Intrepid, VirtualBox 2.0.2 and iPod Touch 1G.
 
 
For me it worked on hardy 8.04  amd64 x2  2g iphone.. latest virtual box

---

### Post by cisoprogressivo on 2008-10-21
May the new kernel (2.6.27) be a problem?

---

### Post by jack frost on 2008-10-21
> **cisoprogressivo said:**
> May the new kernel (2.6.27) be a problem?
 
 
it may be.. I noticed Ihad to re-apply the usb fix and the usb iphone fix after i updated my kernel.. but it still worked after..

---

### Post by bruce449 on 2008-10-22
does it work ??

---

### Post by jack frost on 2008-10-22
> **bruce449 said:**
> does it work ??
is has been for me..  i have been syncing for about a month now with itunes in virtual box.. 
2g iphone.. firmware 2.1..unlocked/jailbroken.. xp pro virtual machine/itunes.. i am going to try and get my other box as a osx86

---

### Post by gupi-gupi on 2008-10-24
hello, tried on hardy 2.6.24.21.23 virtualbox 2.0.2, guest: xp sp3, did the > sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot thing, but itunes 8 complaines about not beeing able to connect iphone (3g jailbreack)
any suggestion? :(

---

### Post by jack frost on 2008-10-24
> **gupi-gupi said:**
> hello, tried on hardy 2.6.24.21.23 virtualbox 2.0.2, guest: xp sp3, did the thing, but itunes 8 complaines about not beeing able to connect iphone (3g jailbreack)
any suggestion? :(
 
 
I will have to check what version of itunes I am running.. I don't think I am running 8. 
 
Did you already do the virtualbox usb fix? 
 
I did that first prior to running the iphone usb syn fix. 
 
If your other usb devices were seen by virtualbox, you don't need to.. also when I want to sync in itunes, I always cancel it when Fspot in ubuntu wants to import pics as soon as I plug it in. Then I just click on devices in virtual box and check box the iphone. I also already have itunes up and running first prior to plugging in the ipone.
 
I really would prefer to sync straight in ubuntu.. I am sure something will come along soon. I know you can sync with amarok via bluetooth, but I heard it is very slow and does not sync everything.

---

### Post by gupi-gupi on 2008-10-25
hello jack frost, so tried the 7.7 itunes, but the error still the same (itunes error 0xe8000035) has to do with usb port , seams I cannot solve this right now. thanks anyway :)
(i just did the fix I posted, are there any othe fix to do for usb? virtualbox and the guest is mounting correctly usb, and iphone is recognized as a camera by xp who can import pictures with it's defaullt camera prog.?)

---

### Post by jack frost on 2008-10-25
> **gupi-gupi said:**
> hello jack frost, so tried the 7.7 itunes, but the error still the same (itunes error 0xe8000035) has to do with usb port , seams I cannot solve this right now. thanks anyway :)
(i just did the fix I posted, are there any othe fix to do for usb? virtualbox and the guest is mounting correctly usb, and iphone is recognized as a camera by xp who can import pictures with it's defaullt camera prog.?)
Did you update your kernel?  I noticed that my fix did not work after the recent kernel update from ubuntu and had to do my fixes again...plus do a re-compile of the virtualbox kernel with this

/etc/init.d/vboxdrv setup

once I did that it worked again. .not sure if this is your issue or not.. hopefully the pwnplayer that is being developed will work to the point that we do not have to even sync with xp... the iphone is one last thing then I can say by to windows.  I also checked.. I am running itunes 8

---

### Post by loveandequality on 2008-12-09
> **asphixmx said:**
> Hello everyone. I am trying to sync my iPod Touch with iTunes, using Virtualbox, also with Parallels 2.2 and no luck. WIndows can see the iPod, but when I open iTunes, it says can't sync with iPhone because of an unknown error. I tried to stop the Apple Mobile Device Service, then started again... iTunes says the same.
I have been reading and searching a lot trying to find a solution with no luck. Is there anyone working with Ipod touch / iphone AND iTunes in a virtual machine? VMWare, Wine, Virtual Box, Parallels...anything?
I just don't want to use my windows partition anymore... I am using it just for sync.

Yes, yes... I can sync my songs with Amarok, but since it is wireless, it is sooo slow. Also my contacts and appoinments don't sync. That is why I need iTunes and Outlook.

Any idea? Any one?

Thanks!

in the newest virtualbox it works its that u need to enable USB 2.0 in the settings.

before all that if you get an USB error just go to my post its solved there.:KS:KS:KS:

---

### Post by loveandequality on 2008-12-09
fix in the new version.

also i got the way how to errase that USB error if any got it is in 1 of the threds.

---

### Post by loveandequality on 2008-12-09
> **asphixmx said:**
> Hello everyone. I am trying to sync my iPod Touch with iTunes, using Virtualbox, also with Parallels 2.2 and no luck. WIndows can see the iPod, but when I open iTunes, it says can't sync with iPhone because of an unknown error. I tried to stop the Apple Mobile Device Service, then started again... iTunes says the same.
I have been reading and searching a lot trying to find a solution with no luck. Is there anyone working with Ipod touch / iphone AND iTunes in a virtual machine? VMWare, Wine, Virtual Box, Parallels...anything?
I just don't want to use my windows partition anymore... I am using it just for sync.

Yes, yes... I can sync my songs with Amarok, but since it is wireless, it is sooo slow. Also my contacts and appoinments don't sync. That is why I need iTunes and Outlook.

Any idea? Any one?

Thanks!

fix in new version. if you get an USB error in the settings i got the awnser in my thred.

---

### Post by jepong on 2009-08-23
any update with iPhone sync using virtualbox 3 and ubuntu jaunty?

---

### Post by soulsurfa on 2009-09-08
Works well with Virtualbox 3 and 8.04 LTS with latest Kernal

[http://ubuntuwarrior.blogspot.com/2009/09/iphone-sync-in-ubuntu.html](http://ubuntuwarrior.blogspot.com/2009/09/iphone-sync-in-ubuntu.html)

---

### Post by driven1 on 2009-09-10
I just installed virtualbox 3 with a Windows xp guest with iTunes 9, and I can sync to an iPod Touch with 3.0 software. Sometimes it takes a couple of tries for iTunes to see the iPod, but once it does, everything works. My music and video are stored on my Ubuntu home folder and accessed by folder sharing.

---

### Post by Chronon on 2009-09-10
I just got this going too.  This is the first time I have synced the device in 3 months.  (It is not my favorite audio player, so it doesn't get too much action these days.)

---

### Post by driven1 on 2009-09-10
> **Chronon said:**
> I just got this going too.  This is the first time I have synced the device in 3 months.  (It is not my favorite audio player, so it doesn't get too much action these days.)

What's your main audio player? Since I am switching to Ubuntu, I want a more Linux-friendly player.

---

