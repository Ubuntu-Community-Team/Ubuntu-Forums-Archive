---
title: "USB problem with VirtualBox"
date: 2007-03-25
forum: Virtualisation
---

### Post by bmralex on 2007-03-25
Hi,
I'm using VirtualBox to run Windows XP as a Guest OS over Ubuntu Edfy host.
However, my virtual Windows doesn't recognize my usb flash drive, although USB mouse works fine.

When I mounted this device from VM menu,  I received an error message  
"Not permitted to open the USB device, check usbfs options".
I understand that it is a common problem in virtual OS and tried to use recommendations for solving the similar problems in vmware.
([http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=10535760&stateId=0%2](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=10535760&stateId=0%2))

I added the line 
```
usbfs  /proc/bus/usb  usbfs  auto  0  0
``` 
to the /etc/fstab file, however, it did not help.

What shall I do?

Thanks
Alex

---

### Post by tgalati4 on 2007-03-25
Did you look at /proc/bus/usb?

I have /proc/bus/usb/001/001 as an actual device.  Perhaps you need to plug the device in and see what shows up in /proc/bus/usb and use that in your fstab.

Good luck.

ps:  I have 

procbususb /proc/bus/usb usbfs rw 0 0

in my fstab.

---

### Post by bodhi.zazen on 2007-03-25
I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) **/etc/udev/rules.d/40-permissions.rules** (I use vim, you can use nano, gedit or whatever)

Change this line :

SUBSYSTEM=="usb_device",              MODE="0664"

To :

SUBSYSTEM=="usb_device",              MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

FYI : I am working on a Virtual Box How-to for Ubuntu here : [noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox[/noparse]

Feel free to give feedback :)

---

### Post by bmralex on 2007-03-28
Thank you for your reply. I have the same proc/bus/usb/001/001 as an actual device.  However, editing fstab directly did not help.  I solved the problem using the method proposed by bodhi.zazen.

Thank you for your help,
Alex

---

### Post by bmralex on 2007-03-28
Bodhi.zazen,
I will name my son after you.
Your solution worked nicely!!!! Thanks!

---

### Post by gapplewagen on 2007-04-09
Very good.  Works great.  Now able to sync my Samsung Blackjack with my XP and Vista vbox installs.

---

### Post by rabideau on 2007-04-22
Thank you bodhi!!!!!! 

It works splendidly on Fiesty.:guitar:

---

### Post by GSF1200S on 2007-04-23
> **bodhi.zazen said:**
> I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) **/etc/udev/rules.d/40-permissions.rules** (I use vim, you can use nano, getid, or whatever)

Change this line :

SUBSYSTEM=="usb_device",              MODE="0664"

To :

SUBSYSTEM=="usb_device",              MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

Im getting quite angry very quickly. This doesnt work.

None of the other crap works. I cant share between my virtual machine and linux at all no matter how many hours I spend trying to figure it out. I get the same message as the original post when trying to mount USB, and I cant setup a network. If I follow the virtualbox user guide, I get an error by step 2.

---

### Post by bodhi.zazen on 2007-04-23
> **GSF1200S said:**
> Im getting quite angry very quickly. This doesnt work.

None of the other crap works. I cant share between my virtual machine and linux at all no matter how many hours I spend trying to figure it out. I get the same message as the original post when trying to mount USB, and I cant setup a network. If I follow the virtualbox user guide, I get an error by step 2.

LOL

If you are getting angry, time to give it a break !

First, make the above change, be careful of typos. Then reboot and try again.

Networking should work out of the box, that is you should have internet access.

If you want to ssh or share files directly I wrote a how to here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

The documentation on Virtual Box is shall we say lacking. I am trying to maintain an information data base for Ubuntu on that above link. If anyone is having problems or has better solutions, PLEASE POST THEM and I will try my best to maintain the wiki.

---

### Post by GSF1200S on 2007-04-23
> **bodhi.zazen said:**
> LOL

If you are getting angry, time to give it a break !

First, make the above change, be careful of typos. Then reboot and try again.

Networking should work out of the box, that is you should have internet access.

If you want to ssh or share files directly I wrote a how to here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

The documentation on Virtual Box is shall we say lacking. I am trying to maintain an information data base for Ubuntu on that above link. If anyone is having problems or has better solutions, PLEASE POST THEM and I will try my best to maintain the wiki.

Thanks for you help.. I may get angry, but that only makes me research more. I managed to fix it, using a post in the Mepis Linux forums.

[http://www.mepislovers.org/forums/showthread.php?t=5152](http://www.mepislovers.org/forums/showthread.php?t=5152)

I wish I had seen your link before.. haha

---

### Post by marklid on 2007-04-24
> **bodhi.zazen said:**
> I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) **/etc/udev/rules.d/40-permissions.rules** (I use vim, you can use nano, getid, or whatever)

Change this line :

SUBSYSTEM=="usb_device",              MODE="0664"

To :

SUBSYSTEM=="usb_device",              MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

You are an absolute star ! Cheers !

---

### Post by Scribbleaz on 2007-05-01
Let me also add my thanks to Bodhi Zen. Your solution worked great, and saved me aggravation to boot. You rock!
Dan

---

### Post by Scribbleaz on 2007-05-01
Whoops! Make that "Bodhi.Zazen"

---

### Post by scottvan on 2007-06-09
Wow thanks Bodhi!!!!! I'm a LOT closer to just running Ubuntu without dual booting into Windows now....

---

### Post by tombott on 2007-10-15
Many thanks, this worked a treat!

---

### Post by realvz on 2007-10-15
So why not make this USBFS thing to  default to 666  in UBUNTU??? 

Is there any restriction....

---

### Post by tombott on 2007-10-24
Just to confirm this fix also work for Gutsy, running the closed version of VirtualBox and not the OSE from the repo's

---

### Post by fabiomb on 2007-10-24
the same worked for me! :D i'm happy ;)

the OSD version does not have USB support, you must to use the free but not open version.

someone has problems with v4l2 support?  i have problems with a lot of apps wich only uses v4l not v4l2

---

### Post by jespdj on 2007-10-25
> **realvz said:**
> So why not make this USBFS thing to  default to 666  in UBUNTU??? 

Is there any restriction....
Because by doing this you give the whole world access to your USB devices, which is a security problem, as the VirtualBox manual says.

---

### Post by Portable_Jim on 2007-11-10
> **bodhi.zazen said:**
> I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) **/etc/udev/rules.d/40-permissions.rules** (I use vim, you can use nano, gedit or whatever)

Change this line :

SUBSYSTEM=="usb_device",              MODE="0664"

To :

SUBSYSTEM=="usb_device",              MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

FYI : I am working on a Virtual Box How-to for Ubuntu here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Feel free to give feedback :)
Worked for me. Thanks (Ubuntu Feisty Fawn)

---

### Post by siralphred on 2007-11-11
thanks Bodhi your help made my built in webcam work in vbox aswell.....btw those of you still having problems after Bodhi hint, you have to actually add the usb device in the General settings of Virtualbox and restart your computer (Computer itself not virtualbox)

---

### Post by bwdease on 2008-02-08
OK!  I run vbox on a windows xp machine.  I had been trying for a while to get my USB flash card to work on a ubuntu 7.10 virtual machine.  This is what I found to help.  

     First, dsconnect the USB device.  Then, start the virtualbox program.  Then, connect the USB device.  Then, go to the USB settings in vbox.  In USB filters, add the USB device.  Under remote, select any or yes.  Then start the virtual machine.  The USB device should be present in the virtual machine.

     It seems that the device cannot be connected untill after the vbox program is running.  It worked with my situation on the USB flash card reader.  I'll try it with others to see if this holds true.  Hopefully this will work for you.  GOOD LUCK!!!

---

### Post by jefferystone on 2008-02-09
I was getting this error:

 Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The
 service might be not installed on the host computer.

Added the following lines to /etc/fstab:

```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---------

This worked fine for me.  Taken from [[COLOR="Blue"]**Message #40 here.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=341740&page=4")

Sincerely,

Jeffery Stone

---

### Post by redunbar on 2008-02-24
I see a lot of people having trouble with accessing USB drives in virtualBox, but it is really quite easy, and if you do it the easy way, it will work even with the OSE version of VBox. All you have to do is use the shared folder feature of virtualBox. This is what you do for a virtual XP in a Ubuntu host.

1. Make sure that the Guest Additions are installed. To do this, start your virtual XP system, then select Devices > Install Guest Additions. Sometimes it's a little slow, and sometimes it ignores you, but be patient or try it again if nothing happens. Once it's installed, then...

2. Set up a shared folder. You don't have to make a special folder for this in Ubuntu, you can use any existing folder, including a mounted USB drive. And you don't need to use ANY command line instructions to do it. In your virtual XP or W2K window, select Devices > Shared Folders. This will bring up the Shared Folders dialog box. Click on the Add A New Shared Folder button, which is in the upper right corner of the dialog box, with a + symbol on it. This will bring up the Add Share dialog box. In the Folder Path field, enter the Ubuntu path of the folder you want to share, for example: /media/USBdrive (if you have a USB drive mounted in Ubuntu as /media/USBdrive) or whatever the path to the folder is. In the Folder Name field, put in whatever name you want to use for the share in Windows. This name doesn't have to match the Ubuntu folder name. Once these fields are filled in, click on OK to exit the Add Share box, click on OK to exit the Shared Folders box, and your shared folder is set up. Now, to access the shared folder in Windows...

3. Find My Network Places, either on the Windows desktop if you put it there, or in the Start menu. Right click on it and select Map Network Drive from the menu that comes up. This will bring up the Map Network Drive dialog box, which contains a Drive field and a Folder field. The Drive field will have a suggested drive letter already entered, but if you don't like it, you can change it. The Folder field will be blank. You can either enter the shared folder name directly in it, for example \\VBOXSVR\FolderName (where FolderName is the same name you used in the Folder Name field in step 2, or you can use the browse option to select your folder. You will find your shared folder in the VirtualBox Shared Folders folder. The browse interface is a little slow and flakey on my system, so you have to select the one you want, then select something else, then select the one you want again before you can click on OK to get back to the Map Network Drive box. Once your folder is selected, check the Reconnect at logon box unless you want to do step 3 every time you bring up Windows. Then click on OK, and your shared folder/drive is set up. Go to My Computer and you will see it as a network drive which you can use like any other drive or folder.

---

### Post by statto1977 on 2008-02-25
> **redunbar said:**
> I see a lot of people having trouble with accessing USB drives in virtualBox, but it is really quite easy, and if you do it the easy way, it will work even with the OSE version of VBox. All you have to do is use the shared folder feature of virtualBox. This is what you do for a virtual XP in a Ubuntu host.

1. Make sure that the Guest Additions are installed. To do this, start your virtual XP system, then select Devices > Install Guest Additions. Sometimes it's a little slow, and sometimes it ignores you, but be patient or try it again if nothing happens. Once it's installed, then...

2. Set up a shared folder. You don't have to make a special folder for this in Ubuntu, you can use any existing folder, including a mounted USB drive. And you don't need to use ANY command line instructions to do it. In your virtual XP or W2K window, select Devices > Shared Folders. This will bring up the Shared Folders dialog box. Click on the Add A New Shared Folder button, which is in the upper right corner of the dialog box, with a + symbol on it. This will bring up the Add Share dialog box. In the Folder Path field, enter the Ubuntu path of the folder you want to share, for example: /media/USBdrive (if you have a USB drive mounted in Ubuntu as /media/USBdrive) or whatever the path to the folder is. In the Folder Name field, put in whatever name you want to use for the share in Windows. This name doesn't have to match the Ubuntu folder name. Once these fields are filled in, click on OK to exit the Add Share box, click on OK to exit the Shared Folders box, and your shared folder is set up. Now, to access the shared folder in Windows...

3. Find My Network Places, either on the Windows desktop if you put it there, or in the Start menu. Right click on it and select Map Network Drive from the menu that comes up. This will bring up the Map Network Drive dialog box, which contains a Drive field and a Folder field. The Drive field will have a suggested drive letter already entered, but if you don't like it, you can change it. The Folder field will be blank. You can either enter the shared folder name directly in it, for example \\VBOXSVR\FolderName (where FolderName is the same name you used in the Folder Name field in step 2, or you can use the browse option to select your folder. You will find your shared folder in the VirtualBox Shared Folders folder. The browse interface is a little slow and flakey on my system, so you have to select the one you want, then select something else, then select the one you want again before you can click on OK to get back to the Map Network Drive box. Once your folder is selected, check the Reconnect at logon box unless you want to do step 3 every time you bring up Windows. Then click on OK, and your shared folder/drive is set up. Go to My Computer and you will see it as a network drive which you can use like any other drive or folder.

That's a really snazzy way of doing it (the only way that's worked for me as I'm using OSE). My problem is that I needed USB connectivity for my Sony mp3 player to sync with sonicstage, and unfortunately it doesn't seem to realize that it's plugged in, just viewing it as a hard drive.

If anyone knows of an easy way around this that would be great.

---

### Post by jpnuzzo on 2008-03-05
Here's my twist on the USB issue: I have USB keyboard and wireless-usb mouse. My VM starts. Problem is that I can't install XP (and therefore can't install the Guest Additions).

XP setup launches in the VM, but I lose control of my mouse & kbd. <right-ctrl> does **not** restore control of mouse/kbd. XP setup reaches the prompt: "press enter to continue or F3 to abort", and I can't do either!

I've tried all of the tricks to make my USB work... FSTAB using devmode=666, usbfs group created with all users added to it...I've gone through the litany of stuff recommended on any google-able page I've been able to find.

Any ideas are welcome, else I'll be relegated to vmware or parallels.

---

### Post by detlef2 on 2008-03-19
> **bodhi.zazen said:**
> I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) **/etc/udev/rules.d/40-permissions.rules** (I use vim, you can use nano, gedit or whatever)

Change this line :

SUBSYSTEM=="usb_device",              MODE="0664"

To :

SUBSYSTEM=="usb_device",              MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

FYI : I am working on a Virtual Box How-to for Ubuntu here : [noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox[/noparse]

Feel free to give feedback :)
Thanks to bodhi.zazen. 
But I was not glad with the security-problem (the usb-device will be visible for any user).

This solved the problem on my system
(host is Kubuntu feisty, VirtualBox 1.5.6, guest WindowsXP home, with guest-system installed):
In the file
/etc/udev/rules.d/40-permissions.rules
Change this line :
SUBSYSTEM=="usb_device",  MODE="0664"
To :
SUBSYSTEM=="usb_device",  GROUP="vboxusers", MODE="0664"

The user has to be part of the group vboxusers too - like prescribed in the manual.

Note: Editing the file as bodhi.zazen prescribes, doesnt work on my system.
I edit the file as user with an editor. Then save the file on the desktop.
In the konsole I type "sudo konqueror" (ignore the errormessages in the console).
The konqeror-widow starts as root. Change to the directory of the file.
Use drag and drop for putting the file from the desctop to this directory - best renaming the original file before doing this (for easier undoing, if it doesn work).

Thaks to this forum and bodhi.zazen, which helped me getting this solution.

---

### Post by aks2008 on 2008-05-08
Hi this solution doesn't seem to work in hardy heron.
Error message I get on attaching my USB bluetooth dongle is

"Not permitted to open the USB device, check usbfs options."

I am using ubuntu hardy and virtual box version 1.5.6-28266

40-permissions.rules file seems to different in hardy
It reads 

# USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"

Any advice what should I do?

---

### Post by bodhi.zazen on 2008-05-08
More recently I add this line to /etc/fstab :

```
[FONT=Times New Roman][SIZE=2]# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0[/SIZE][/FONT]
```[FONT=Times New Roman][SIZE=2]

It works like a charm. Typically I need to reboot after adding that to fstab, although you can *try* to re-mount your usb devices ...
[/SIZE][/FONT]

---

### Post by aks2008 on 2008-05-09
Thanks Bodhi-zazen.
I also followed Paco758's suggested tutorial at 
[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)
Now it is working.
Thanks

---

### Post by Portable_Jim on 2008-05-30
Just a(n) (offtopic) note: You need to enable scripts for "yahoo.aips.com" on NoScript for posting to work properly. Other wise it will keep failing and loosing your message, which can be annoying.
Now back on topic...
> **aks2008 said:**
> Thanks Bodhi-zazen.
I also followed Paco758's suggested tutorial at 
[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)
Now it is working.
Thanks
I got to the same website, but using google. The solution listed there works on Ubuntu Hardy.

---

### Post by seuzy13 on 2008-06-03
> **aks2008 said:**
> Hi this solution doesn't seem to work in hardy heron.
Error message I get on attaching my USB bluetooth dongle is

"Not permitted to open the USB device, check usbfs options."

I am using ubuntu hardy and virtual box version 1.5.6-28266

40-permissions.rules file seems to different in hardy
It reads 

# USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"

Any advice what should I do?

I just attached "MODE=0666" onto the end of the line, like this:
SUBSYSTEM=="usb_device", GOTO="usb_serial_start", "MODE=0666"
It worked like a charm. :-)

My problem is that my USB flash drive doesn't automatically mount, and I don't know where it is located so that I can mount it manually. Any ideas? (That is, if anyone is still watching this thread)

EDIT--well, it did work like a charm, until I tried to start her up the next time, and I got the same dialog box again. =/

---

### Post by Tigrillo on 2008-07-12
That works great! I just had to restart my computer after changing 0664 to 0666.

Thanks a lot

---

### Post by zwanzig on 2008-07-15
I solved it this way...

checking group id of vboxusers
```
more /etc/group | grep vboxusers
```

edit fstab
```
sudo nano /etc/fstab
```

added lines to fstab
```
# 1008 is my virtualbox group id
none     /proc/bus/usb usbfs devgid=1008,devmode=664 0 0
```

and made a fresh mount of all fstab devs
```
sudo mount -a
```


no need to even restart Virtualbox.

---

### Post by Kablooie!! on 2008-08-06
Hi all,

I've got USB working fine (thanks the all the thread posters), but I've found that VirtualBox "steals" the USB keyboard when I launch it.  

Is there any way to make it so that the host and VM can "share" the keyboard?  When I work from home I use a USB keyboard, and at work I use a PS/2 connector.  Launching VirtualBox at work is fine - the keyboard is usable in my Ubuntu host and my hosted Windows XP session.  However at home I have a USB keyboard, so when I launch VirtualBox, it "grabs" the USB keyboard and I can't use it on the host, which is really annoying.

Thanks for any help.

---

### Post by Deadmode on 2008-11-04
> **zwanzig said:**
> 
and made a fresh mount of all fstab devs
```
sudo mount -a
```


no need to even restart Virtualbox.

Wow...That is all I needed to do and I couldn't find it anywhere! Thanks.

---

### Post by chinchillart on 2008-11-11
Well, have had the same problem with the bloatware SonicStage by Sony.

Need to use it in a VBox VM with XP.
So I've added a specific conf. string in the file:

    /etc/udev/rules.d/40-permissions.rules

First of all, check the device info (usb device plugged in):
```

rob@ubuntu:~$ lsusb
Bus 003 Device 009: ID 054c:0269 Sony Corp. 
Bus 003 Device 002: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 059f:1010 LaCie, Ltd 

```

My mp3 player is the first in the list above.
We can read:

    Bus 003 Device 009: ID 054c:0269 Sony Corp

The last numbers are, respectively: idVendor and idProduct.

Now unmount the device.

Then:
```

rob@ubuntu:~$sudo nano /etc/udev/rules.d/40-permissions.rules

```

Now search for the string: LABEL="usb_serial_start" 

And add a line with device-specific permissions:
```

ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0269", \
					MODE="0664", GROUP="vboxusers"

```

Now the entire section looks like this:
```

LABEL="usb_serial_start"
ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0269", \
					MODE="0664", GROUP="vboxusers"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"

```

You may also use this tecnique for other specific devices.

No need to modify /etc/fstab

Just run VBox, run the XP guest, plug in the mp3 player. Now it works for me.
:popcorn:

PS. Obviously you MUST add a USB filter to the guest settings in VirtualBox.

---

### Post by anewguy on 2008-11-13
First, just a comment, then second a question!

(1) Starting in 8.04 the udev permissions did change.  The recommended way to specify specifics for a device are to:

a. leave 40-permissions as-is - make no changes in it
b. create device-specific permissions files starting with a number above 40 (i.e., 41-xxxxx) and put the information for the specific device in that file.

These recommendations are actually inside 1 of the permissions files in udev - I just don't remember which one.  I had to do this to get things like digital cameras, etc., working in Hardy.  Since a VM is running as if Hardy is the OS, it shouldn't make any difference if you are in a VM or not.

A sample of this can be found in my thread about problems with my usb cameras in Hardy:

[http://http://ubuntuforums.org/showthread.php?t=784639&page=2]("http://http://ubuntuforums.org/showthread.php?t=784639&page=2")


(2) My question:  I'm running Windows XP Pro SP3 as my host OS, and Hardy 8.04 as the guest.  I tried putting in a blank filter in the usb settings for the vm (blank supposedly allows all), and I tried putting in device-specific filters in the usb settings for the VM.  Nothing seems to work.  I tried the change to fstab as mentioned above, no go.  I only see 2 busses, no devices, for usb.  lsusb shows only the busses, no devices.  If lsusb is unaware of the devices, I would assume they aren't know Ubuntu at all.  Therefore I would assume the fstab and the udev (permissions can't be a problem yet as the devices aren't even seen by the OS) permissions have nothing to do with my problem at this point.  I believe this is still some simple set up problem I doing wrong for the VM in VirtualBox itself.  Has anyone else had no devices show on a lsusb, but were eventually able to get them to work?

I'm trying 2 different USB thumb drives and 3 different cameras, all which never show in a lsusb.  I've tried plugging them in before and after the VM is started.  I have several USB ports on my system.  I tried using the front USB but still not seen.  Tried through a hub connected through one of the rear USB ports - still no go.  Tried removing hub and connecting directly the one of the rear USB ports - still nothing.

Any ideas?? (I know I've got to be doing something stupid!!)

Thanks in advance!!
Dave:)

---

### Post by sharat87 on 2008-12-10
@chinchillart, i have the same need as you... i need my iPod working with vista and eventually itunes. :)

i did what you suggested, I want to point out tow things,
1. its still not working :(. I believe I did exactly what you told.
2. there is not USB options in my preferences dialog... am I missing something?

I am on ubuntu Intrepid, running Vista on VirtualBox OSE installed from the default repositories.

any help appreciated... am really getting frustrated with this :'(

---

### Post by Portable_Jim on 2009-01-23
> **zwanzig said:**
> I solved it this way...

checking group id of vboxusers
```
more /etc/group | grep vboxusers
```edit fstab
```
sudo nano /etc/fstab
```added lines to fstab
```
# 1008 is my virtualbox group id
none     /proc/bus/usb usbfs devgid=1008,devmode=664 0 0
```and made a fresh mount of all fstab devs
```
sudo mount -a
```no need to even restart Virtualbox.
Thanks. This seems like a more elegant solution than editing /etc/udev/rules.d/40-permissions.rules, and as an added bonus it works too.

---

