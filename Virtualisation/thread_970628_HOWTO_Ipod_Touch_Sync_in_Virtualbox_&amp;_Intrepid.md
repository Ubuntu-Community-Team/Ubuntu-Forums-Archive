---
title: "HOWTO: Ipod Touch Sync in Virtualbox &amp; Intrepid Ibex"
date: 2008-11-04
forum: Virtualisation
---

### Post by Baji on 2008-11-04
After days of trying to get the ipod touch working in ubuntu (ad-hoc wireless sync / wine itunes / qemu + winxp / kvm + winxp / virtualbox-ose + xp) I finally have it working using:

[B][Virtualbox-2.0.4 (PUEL)]("http://www.virtualbox.org/wiki/Linux_Downloads")
Recompile usbcore (Modify MAX_USBFS_BUFFER_SIZE to 128K in drivers/usb/core/devio.c) see [VirtualBox ticket #491]("http://www.virtualbox.org/ticket/491")[/B]
*This is a workaround --A fix is scheduled for Virtualbox 2.1.*

Ill share it here please respond with suggestions/improvements/comments. It should also work for the iPhone.

[SIZE="3"][I]1. Install VirtualBox-2.0
2. Configure Ubuntu for VirtualBox-2.0
3. Usb Filesystem fix
4. Kernel usbcore fix
5. Install Windows XP in VirtualBox
6. Running VirtualBox
7. Troubleshooting
8. Sources[/I][/SIZE]

[SIZE="4"]1. Install VirtualBox-2.0[/SIZE]

**Add repository to /etc/apt/sources.list**
```
echo "deb http://download.virtualbox.org/virtualbox/debian intrepid non-free" | sudo tee -a /etc/apt/sources.list
```
**Add sun public apt-get key**
```
 wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
**Install VirtualBox-2.0**
```
sudo apt-get update && sudo apt-get install virtualbox-2.0
```
*Beware: the virtualbox module vboxdrv conflicts with kvm. See troubleshooting for more info.*


[SIZE="4"]2. Configure Ubuntu for VirtualBox-2.0[/SIZE]

**Add yourself to the vboxusers group**
```
sudo gpasswd -a `whoami` vboxusers
```
**Startup vboxdrv module on boot by appending it to /etc/modules**
```
echo "vboxdrv" | sudo tee -a /etc/modules
```


[SIZE="4"]3. Usb Filesystem fix[/SIZE]

**Get the vboxusers group id**
```
cat /etc/group | grep vboxusers
```
> vboxusers:x:**128**:spirit

**Edit /etc/fstab to add these two lines and replace the devgid with the vboxusers group id**
```
#usbfs for virtualbox
none /proc/bus/usb usbfs devgid=**128**,devmode=664 0 0

```


[SIZE="4"]4. Kernel usbcore fix[/SIZE]

**check your current kernel version**
```
uname -r
```
> **2.6.27**-7-generic

**Get the sources for your kernel and fix usb/core/devio.c**
```
sudo apt-get build-dep linux-source-**2.6.27**
sudo apt-get install linux-source-**2.6.27** build-essential
tar -jxvf /usr/src/linux-source-**2.6.27**.tar.bz2
cd linux-source-**2.6.27**/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
```

**Reboot your system and check if vboxdrv is running**
```
lsmod | grep vbox
```
> vboxdrv                72472  0


[SIZE="4"]5. Install Windows XP in VirtualBox[/SIZE]

**Start VirtualBox using Applications->System Tools->Sun xVM Virtualbox or type "VirtualBox"  in a terminal**
Install Windows XP (SP2+) in a virtual machine.
This guide gives a rough idea howto. It is pretty much straightforward.
[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox#Using Virtual Box")


[SIZE="4"]6. Running VirtualBox[/SIZE]

[LIST]
[*]Enable usb and usb2 in the settings for you virtual machine
[*]install itunes inside the vm
[*]connect the ipod touch
[*]cancel f-spot
[*]in the top of the vm box click Devices and activate the apple ipod
[*]Run iTunes inside vm
[/LIST]


[SIZE="4"]7. Troubleshooting[/SIZE]

**vboxdrv cannot load because kvm is loaded**
*purge the kvm package*

```
sudo dpkg --purge kvm
sudo rmmod kvm
sudo modprobe vboxdrv
```

**howto rebuild the vboxdrv module**
```
sudo /etc/init.d/vboxdrv setup
```

**after upgrading it stopped working**
*You need to apply the kernel usbcore fix again, and rebuild the vboxdrv module (see above)*


[SIZE="4"]8. Sources[/SIZE]

[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")
[[SOLVED] Virtual box ipod touch / iphone sync]("http://tennessee.ubuntuforums.com/showthread.php?t=690411")
[http://www.virtualbox.org/ticket/491]("http://www.virtualbox.org/ticket/491")

---

### Post by rickatnight11 on 2008-11-04
This looks great!  I'm going to test this out *tonight*!  Thanks for the hard work.

---

### Post by ger_macaco on 2008-11-07
Did you try with iPod Touch 1G or 2G?

---

### Post by Baji on 2008-11-09
> **ger_macaco said:**
> Did you try with iPod Touch 1G or 2G?

I tried it with the iPod Touch 8GB but it should work with the iPhone aswel

---

### Post by ger_macaco on 2008-11-09
> **Baji said:**
> I tried it with the iPod Touch 8GB but it should work with the iPhone aswel

But was it an iPod Touch 1G (no speaker) or 2G (with speaker)? I am asking because there is no driver for linux (and no way of accesing it yet) for 2G.

---

### Post by obloxeon on 2008-11-11
Tried it and no dice...

---

### Post by huanix on 2008-11-11
I wrote a script that's working pretty well to allow people to sync pods in virtualbox:

[http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/](http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/)

---

### Post by AndThenWhat on 2008-11-12
I tried it and it didn't work.  I have Intrepid with the same uname as you.  I followed all steps but still get the error in iTunes about not being able to read the iPhone "" because of an unknown error.

---

### Post by Baji on 2008-11-12
> **AndThenWhat said:**
> I tried it and it didn't work.  I have Intrepid with the same uname as you.  I followed all steps but still get the error in iTunes about not being able to read the iPhone "" because of an unknown error.

Just to check, could you report the results of the following commands here:

grep 'vboxusers' /etc/group
grep '/proc/bus/usb' /etc/fstab
ls -al /proc/bus/usb/001/
lsmod | grep vbox
dpkg -l \* | grep virtualbox

If you have updated the kernel, you have to reapply the usbcore fix. Could you try reconfiguring the vboxdrv module (sudo /etc/init.d/vboxdrv setup) and restarting?

What iphone/ipod touch are you using? is it jailbroken?

---

### Post by b3n87 on 2008-11-15
So can anyone confirm if this works with the iPhone 3G?

---

### Post by huanix on 2008-11-15
It does work with iPhone 3g. I'm using it now, and i've had ~50 people confirm it on my blog. I wrote a script that i'm continuing to develop to make it as easy as possible.

[http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/](http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/)

---

### Post by b3n87 on 2008-11-16
Oh cool, thanks for the reply and link! So how well does it work? Do you run Windows XP in seamless mode (i think thats right), is it easy sharing your music from Ubuntu to Windows iTunes folder? Is it possible to make a symbolic link so that iTunes can see your music from the Ubuntu folder?

---

### Post by huanix on 2008-11-16
It's a funny story.. When I initially tried the fix and synced I was very excited, so I posted the "easy script" on my blog. Since then I've been so busy that I haven't had a lot of time to play with it. I haven't kicked into seamless mode, but i assume it works. I do store all of my music on an ext3 drive mounted in ubuntu and shared into windows; iTunes runs music from there quite well.I may investigate that more. I've spent the last week trying to make iTunes8 run in wine - i've had a lot of success, but no win. I think i'm ready to put that aside for a minute (it wore me out!)

At the moment i'm trying to add a case to the script to allow it to run in Fedora... oh.. and I have about 4 weeks of graduate school work that i need to catch up on!

---

### Post by b3n87 on 2008-11-16
lol, a very busy man than. I dont have an iPhone, but was thinking about buying one, still not sure if ethnicly I should buy one or not, and if running a virtual box will annoy me?

I've just installed virtualbox, so Ill have a play with that later this week. It could be that a symbolic link might work very well, saves you copy and pasting music from windows to Ubuntu every time.

Another thought, compiz and seamless mode in Virtualbox dont get alone? Unless this has been fixed. Also on the Virutalbox website, it says that Virtualbox 2.1 will solve the iPhone problems, which will be useful :)

---

### Post by huanix on 2008-11-16
Yeah, at the bottom of the virtualbox/iphone bug ticket ( [http://www.virtualbox.org/ticket/491](http://www.virtualbox.org/ticket/491) ) it says it's fixed in 2.1, but I haven't seen a release date. 

You know, if you haven't bought an iPhone yet, you might consider looking at the G1 (Google Phone). I don't know a lot about it - i haven't even seen one, but i do know that it's based on Android, open software that should play very well with linux. I'm locked into iPhone right now, but I'll be picking up a G1 as soon as the opportunity presents itself!

---

### Post by b3n87 on 2008-11-16
Yeah I had one of those, its an amazing piece of kit. But I couldnt get a signal at home, so I couldnt keep it. The phone itself is awesome tho, highly recommend getting it. What are you thoughts on the iPhone then? Should I "sell my soul" and be a freedom hater? lolz

---

### Post by huanix on 2008-11-16
I do truly enjoy the iPhone; I have the 16gb 3g, and I passed my old 8gb to my wife. I enjoyed jailbreaking and kicking around with it. It takes great video (with cycorder after jailbreak), and it works as a wifi access point over the cell network (also with jailbreak - PdaNet) The thing I really miss is an open platform - i'm irritated that instead of working with Apple, we're working around them to do things with our phones that Apple should support (i.e. sync in Linux). Apple's control over the phone is quite irritating. So, while I love the current technology, I wish it were more open source friendly. I'll be picking up a G1 or other open-platform phone on the next go-round.

---

### Post by b3n87 on 2008-11-17
It shoulds picky and annoying but would you be willing to record a video of the sync with virtualbox? I know its a pain, and ill understand if you do not want to, but im interesting in seeing the whole process, and how "well" it works. No worries if you dont have time tho, I completely understand.

---

### Post by huanix on 2008-11-17
I had actually been thinking of doing that myself.. but i figured i'd have to get a youtube account and do all that extra stuff.. and i'm supposed to be writing some stupid finance paper.. so I'll do it!

gimme a little while.

---

### Post by b3n87 on 2008-11-17
Thank you very much, please let me know when you think it will be done :D

---

### Post by huanix on 2008-11-17
i got the video done, but i need to edit it to hide my iPhone serial # and stuff. i'm probably going to drop it on my blog tomorrow night (11/18/2008 ) with an updated script for iphone/virtualbox .. look for virtualbox-iphone-r8.sh

---

### Post by james.wilde on 2008-11-18
Hi Baji:

First a big thank you for taking the trouble to not only make your iPod work in Virtualbox but making the process available to us others who don't have your competence in Linux.

Then, I have a problem after following your procedure.  I am unable to find anywhere in Virtualbox to enable usb and usb2 devices.  I have tried creating a second XP instance in the thought that I maybe couldn't add usb to the existing one, but I can't find any way to activate usb devices there either.

When I start my XP instance, I find under Devices an entry for USB Devices, but even after I connect my iPod, there is nothing here to be enabled.  Here are the results of the tests you suggested:

> **Baji said:**
> Just to check, could you report the results of the following commands here:

grep 'vboxusers' /etc/group
grep '/proc/bus/usb' /etc/fstab
ls -al /proc/bus/usb/001/
lsmod | grep vbox
dpkg -l \* | grep virtualbox

vboxusers:x:125:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
dr-xr-xr-x 2 root root       0 2008-11-18 12:54 .
drwxr-xr-x 9 root root       0 2008-11-18 12:54 ..
-rw-rw-r-- 1 root vboxusers 43 2008-11-18 12:54 001
vboxdrv                71576  0
un  virtualbox                                <none>                                (no description available)
ii  virtualbox-ose                            2.0.4-dfsg-0ubuntu1                   x86 virtualization solution - binaries
un  virtualbox-ose-guest-modules              <none>                                (no description available)
un  virtualbox-ose-guest-source               <none>                                (no description available)
ii  virtualbox-ose-guest-utils                2.0.4-dfsg-0ubuntu1                   x86 virtualization solution - guest utilitie
ii  virtualbox-ose-source                     2.0.4-dfsg-0ubuntu1                   x86 virtualization solution - kernel module 
un  virtualbox-source                         <none>                                (no description available)

If you have updated the kernel, you have to reapply the usbcore fix. Could you try reconfiguring the vboxdrv module (sudo /etc/init.d/vboxdrv setup) and restarting?

setup is not available.  I tried restart.

What iphone/ipod touch are you using? is it jailbroken?

It's a 30GB Classic model, about 3 years old I believe.  Don't know what jailbroken means.  I've been using it on my old XP box.

Thanks in advance if you can give me more help or suggestions.

//James

---

### Post by b3n87 on 2008-11-18
Im looking forward to this video :)

---

### Post by huanix on 2008-11-18
sorry again; the video is done but the accompanying virtualbox itunes sync script is not complete. It's pretty difficult for me to get this stuff done during the week - i may have to finish it this weekend ( 11/22/2008 ). Again, my apologies.

---

### Post by james.wilde on 2008-11-19
BTW, I've done some more research, and discovered that I needed the official version of Virtualbox, and not the ose version.  I have actually installed that now, and have a place to enable usb devices, but still no iPod contact.  I've got a thread going in the virtualbox.com forum, which seems very slow, incidentally.

Basically I've created four filters, one for each of my usb ports.  I can see the three devices I have connects, a wireless mouse, a keyboard and my iPod, but all three are greyed out when I click on Devices in the Virtualbox window.  They are shown as unavailable, which is strange as I can use both the mouse and keyboard.

If I hover over the usb icon at the bottom right of the Virtualbox window, I see a text which tells me again that no USB devices are available.  Everything seems to work except the iPod.  :(

Anyone any suggestions about what else I can try?

TIA

//James

---

### Post by james.wilde on 2008-11-19
Fixed!  The solution for me was in the following thread:

[http://ubuntuforums.org/showthread.php?t=828927](http://ubuntuforums.org/showthread.php?t=828927)

There is a command in there as follows:

echo "none /proc/bus/usb usbfs devgid="$(sed '/plugdev/!d;s/plugdev:x:\(.*\):.*/\1/' /etc/group)",devmode=664 0 0" | sudo tee -a /etc/fstab

This adds not the vboxuser groupid but the plugdev groupid (46 in my case).

I've just noticed that I still have the vboxuser groupid on a line above the new plugdev line in /etc/fstab.  Sometime I'll test removing that, and see if it breaks.

Thanks to all who have worked on this problem.

//James

---

### Post by w.m on 2008-11-19
Thank's for the tip.

It also worked for Nokia N95 usb connection.

---

### Post by james.wilde on 2008-11-20
Thanks, w.m.  I have a N95, too, and if it didn't work against Evolution in the host, I was going to have to start work on the Windows guest for that, too.  Now I know it should work.

//James

---

### Post by bennich on 2008-11-20
The USB Core fix worked like a charm - had already performed all the other steps.

Running 8.10, VirtualBox 2.0.4, Iphone 3G ver. 2.1, Itunes 8

Thanks a bunch.

Now we can only wait for VBox 2.1 - which should include a "native" fix.

---

### Post by huanix on 2008-11-22
> **b3n87 said:**
> Im looking forward to this video :)

I posted the newest version of the script, it will now detect and install the correct version of Virtualbox-2.0 (by adding the repository to your sources) and create a correct /etc/fstab listing for usb - that will assign the usb to the vbox group thanks to tauchris.

Okay - i did a video and put it up and got nothing but complaints for 24 hours... i did it, and i un-did it :)

[www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/](http://www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/)

---

### Post by zeus77 on 2008-11-23
There are conflicting reports on the virtualbox [trouble ticket]("http://www.virtualbox.org/ticket/491") that the latest vbox 2.0.6 may or may not fix the usbcore issue.  Anyone here give it a try (i.e. without the usbcore hack)?
zeus77

---

### Post by bvucinic on 2008-11-24
I can confirm the fix works also for Nokia n95.

good job!

---

### Post by b3n87 on 2008-11-24
All fixed now :D

Thanks for everyones help tho!

---

### Post by Quaxo76 on 2008-11-25
Not working for me. I updated to 2.0.6, I also updated iTunes to latest version, I rebuilt the virtualbox driver (don't know if it was needed), and rebooted host and guest, but I still have the same connection error. No luck for me...

EDIT: when I plug in the iPod (it's a touch) Windows sees it as a digital camera. But iTunes refuses to see it.

Cristian

---

### Post by b3n87 on 2008-11-25
That is all normal, you do have to start iTunes manually tho, and sometimes it takes awhile for iTunes to detect the iPod / iPhone. Might be worth leaving it for awhile?#

At out interest, how much virutal RAM are you all giving windows?

I am using Windows XP with 256mb Virtual RAM

---

### Post by huanix on 2008-11-27
I think the fix generally works, but I do know that some people have done everything right and are still having problems. One of those people (Patrick) told me that the problem appeared to be related to his motherboard. When he popped in a pci usb card everything worked fine.

[http://www.dynexproducts.com/pc-503-2-dynex-4-port-usb-20-pci-desktop-card.aspx](http://www.dynexproducts.com/pc-503-2-dynex-4-port-usb-20-pci-desktop-card.aspx)

I wouldn't necessarily endorse the dynex card, but he did say it did the trick!

---

### Post by Quaxo76 on 2008-11-28
Hmmm... I left it plugged for more than an hour, still iTunes didn't detect it. I suppose it's not going to work.
I wonder, why is this working for some people and not for others? By the way, many USB devices work on my setup, but an USB geiger counter I have, doesn't work. So it's not a purely iPod-related thing...

Cristian

---

### Post by b3n87 on 2008-11-28
have you enabled the iphone through the Device menu on Virtual box?

---

### Post by Quaxo76 on 2008-11-28
Yes, I have. And Windows actually "sees" it - I hear the "bing" sound when I plug it, and a popup window appears asking if I want to download the photos from the iPod (as it's seen as a digital camera). But iTunes still gives the same old error.

---

### Post by b3n87 on 2008-11-28
Seems like an issue with iTunes then, have you tried uninstalling it and downloading the latest version and installing that?

---

### Post by b3n87 on 2008-11-28
BTW everyone, after the new kernel update from Ubuntu, I had to recompile the virtualbox modules for it to work again

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Quaxo76 on 2008-11-28
Yes, tried that... Looks like some USB devices (i.e. the iPod and my USB geiger counter) use some non-standard protocol or something, that Virtualbox can only cope with on some machines and not others... ?!?

---

### Post by b3n87 on 2008-11-30
Hmm not sure about that. It should work, irrespective of what machine you have. Maybe you should completely remove virtualbox restart, and install and try it again. Its a pain tho, but I cant see any reason why it wont work.

---

### Post by huanix on 2008-11-30
Quaxo76 - what model motherboard are you using?

---

### Post by loveandequality on 2008-12-09
fix in new version. if you get an USB error in the settings i got the awnser in my thred.

---

### Post by Torille on 2009-02-05
Hi, i'm trying to do what you said but the terminal send a message what a type the following line "make -C /lib/modules/`uname -r`/build/ M=`pwd` modules"
the following is terminal message to send me

make: Entering directory `/lib/modules/2.6.27-11-generic'
make: *** No rule to make target `/build/'.  Stop.
make: Leaving directory `/lib/modules/2.6.27-11-generic'

Note. I had installed first the Win Xp on Vbox and i did not do this before it is the first time.

---

### Post by foxostro on 2009-02-05
I have a very similar issue to Torille:

```

$ make -C /lib/modules/`uname -r`/build/ M=`pwd` modules"
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
Makefile:1364: *** missing separator.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

```

I did try to build usbcore by doing the following:

```

$ cd ~/linux-source-2.6.27/
$ make mrproper
$ cp /usr/src/linux-headers-2.6.27-11-generic/.config ./
$ make modules

```

and then I install the module as described in the original post. Unfortunately, while this does build and install the patched usbcore module, the module refuses to load with modprobe. Something about an invalid module format.

Where might one find documentation on these things?

----------------------------------

UPDATE:

I was finally able to get iPod Touch sync working in VirtualBox, but I feel my solution is less than ideal. SinceI was having trouble compiling a kernel module for the stock kernel, I compiled my own vanilla kernel. Then, I was able to install and load the patched usbcore.ko. Finally, iPod Touch sync was working.

First, you'll need some stuff installed to begin your work:
```

sudo apt-get build-dep linux-source-2.6.27
sudo apt-get install linux-source-2.6.27 build-essential fakeroot kernel-package

```

Here's a summary of how to build kernel using Ubuntu's settings:
```

tar -jxvf /usr/src/linux-source-2.6.27.tar.bz2
cd linux-source-2.6.27/
make mrproper
sudo cp /boot/config-2.6.27-11-generic ./.config
make menuconfig
sudo make-kpkg --rootcmd fakeroot --initrd --append-to-version=-generic kernel-image 
sudo cp arch/i386/boot/bzImage /boot/bzImage-2.6.27-11-generic

```

Once that's finished, edit /boot/grub/menu.lst and add an entry for the bzImage-2.6.27-11-generic kernel image.
And, you might want to reboot right now and make sure the new kernel is bootable, everything still works, &c

Then, patch and install the new usbcore module:
```

cd linux-source-2.6.27
perl -pi.bak -e 's/16384/131072/' drivers/usb/core/devio.c
sudo make-kpkg --rootcmd fakeroot --initrd --append-to-version=-generic kernel-image 
sudo install -m644 -b drivers/usb/core/usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u

```

To install the module, you could either stop everything that is using usb and do rmmod followed by modprobe, or you could just reboot. Rebooting is easy.

----------------------------------

FYI: Increasing the max buffer size for usbfs (and not necessarily the 'building a new kernel' thing that I did) also allows Zune sync to work correctly in VirtualBox. Cool.

---

### Post by PaganImmolator on 2009-06-11
I am also getting an error. I am using 2.6.28-11-generic AMD64 flavor and I am following Huanix's instructions on the first page. When I get to this line:

```
strip --strip-debug usbcore.ko
strip: 'usbcore.ko': No such file

```

This is an output of the contents of /linux-source-2.6.28/drivers/usb/core
```

buffer.c   devio.c.bak  generic.c  hub.c    Makefile        Module.symvers   sysfs.c
config.c   driver.c     hcd.c      hub.h    message.c       notify.c         urb.c
devices.c  endpoint.c   hcd.h      inode.c  Module.markers  otg_whitelist.h  usb.c
devio.c    file.c       hcd-pci.c  Kconfig  modules.order   quirks.c         usb.h

```

While not a complete newbie, I still don't don't know a lot about Linux in general. Just trying to get my wifes Itouch working. From what I can tell, its looking for an object file. Did the naming conventions change or did something not get built? Are those instructions ok for 64 bit. 

Thanks in advance.

---

### Post by The Marsh Man on 2009-06-15
> Edit /etc/fstab to add these two lines and replace the devgid with the vboxusers group id
Code:

#usbfs for virtualbox
none /proc/bus/usb usbfs devgid=128,devmode=664 0 0

N00b question... adding these lines to /etc/fstab only gives me "Could not save the file /etc/fstab. You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again."
What am I doing wrong?

Thanks in advance.

---

### Post by jepong on 2009-07-18
use SUDO GEDIT /etc/fstab

---

