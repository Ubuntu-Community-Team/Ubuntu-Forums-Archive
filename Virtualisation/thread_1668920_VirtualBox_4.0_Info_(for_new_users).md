---
title: "VirtualBox 4.0 Info (for new users)"
date: 2011-01-17
forum: Virtualisation
---

### Post by slooksterpsv on 2011-01-17
In reading some of the threads on here about questions people have about VirtualBox 4, I thought I would try to answer some of them.

Any instructions assumes you know where to go to get to specific areas such as modifying users and groups, or accessing terminal, having virtualbox 4.0 downloaded, etc.

**WHAT'S NEW IN VIRTUALBOX 4.0**
They've changed the interface, fixed a few bugs, and added some new features.
- CD/DVD/BDROM Drives can now be SATA, they're not limited to ATA
- Live Previews on the VirtualBox main screen
- Addition of JRockITVE under other OSes
- Better (still buggy) 2D and 3D Acceleration
- Intel HD Audio
- More...

**HOW DO I INSTALL VIRTUALBOX 4.0 FROM THE TERMINAL?**
Open Terminal and cd to the directory where the DEB is located at. Type in the following:
sudo dpkg -i ./virtualbox-4.0_4.0.0-69151~Ubuntu~maverick_amd64.deb && sudo apt-get install -f

What that does is it tries to install VirtualBox, sees what's missing (libqt stuff) and installs it, thus finishing the installation of VirtualBox.

**HOW DO I GET USB SUPPORT TO WORK!?**
Open your users and groups area, by default (on Gnome) it's Settings -> Administration -> Users and Groups 

Now click your name -> Click Manage Groups -> Click vboxusers -> Click Properties -> Click a check on your name -> Click OK -> Authorize
 
Close all of your programs, save your stuff, log out, then log back in. USB support should work now.

**I NEED USB 2.0 SUPPORT** - UPDATE
I apologize I thought I had this in here before. USB 2.0 support is not included by default anymore. The only way to get USB 2.0 support (as well as PXE and RDP) is by downloading the VirtualBox Extension pack, via: 
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

After you download the file on that page, go ahead and open VirtualBox. Go to File -> Preferences -> Extensions - click on the button that looks like a diamond with an orange downward arrow (triangle). Locate the package and click on OK. Afterwards, make sure it's listed there with a green check.

Finally, you'll have to shutdown your VM to enable USB 2.0 Support. You go to the properties of the VM -> USB -> and put a check in Enable USB 2.0 (EHCI) Controller. Choose OK and startup your VM.

It may be beneficial to reinstall the Guest Additions on some machines. Others will pick up the USB 2.0 automatically.

You will need this especially if you need to sync iPods with Windows.

**THE RESOLUTION IN WINDOWS <VERSION> IS LOW**
Click on Device -> Install Guest Additions

Follow through and restart.

**THE RESOLUTION IN LINUX <VERSION> IS LOW**
This varies depending on Linux distrobution, as it requires dkms, kernel headers, etc. But to install you would do the following:

Open Terminal -> cd /media/VBOXADDITIONS/ -> execute the program as root for either 32-bit or 64-bit - e.g.:
sudo ./VBoxLinuxAdditions.run

There used to be a different version for x86 and amd64. This may also require you to install dkms and build-essential (if using Ubuntu). Which you can install via:

```

sudo apt-get install dkms build-essential

```

**AUDIO ISN'T WORKING**
Go to the settings on the VM, click on Audio on the left-hand side. Change it to Intel HD Audio or Soundblaster for Audio Controller. Make sure you're using the correct Host Audio Driver - mine is Pulse Audio - yours may differ. If it still fails, refer to VirtualBox documentation.

**HOW DO I ACCESS SHARED FOLDERS?**
NOTE: You can now have Shared Folders automatically mount/try to mount on the OS. To do this, when you create the Share via Devices -> Shared Folder, there's an option called Auto-mount - try this option if you're having trouble mounting shared folders.

Depending on the OS, you would do the following:
Windows, navigate to: \\VBOXSVR
Linux, mount it via (after installing Guest Edition), in terminal:

sudo mount -t vboxsf SHARENAME /path/to/mount/to

Where SHARENAME is the name of the share (you typed it in when setting up the in VirtualBox via Devices -> Shared Folder)
And /path/to/mount/to - is the location where you want to mount it to. E.g. you could make directories under /media to have it mount to.

**I'M GETTING AN IP OF 10.0.2.15 I WANT AN IP LOCAL TO MY NETWORK**
Click on Devices -> Network Adapters...
Change Attached To from NAT to Bridged
Change the Name to coincide with the Adapter you use for internet (mine I use wlan0 (wireless)).

**WHERE CAN I GET ADDITIONAL HELP**
Post here on the forums, google it, look through VirtualBox website documentation, etc.

---

### Post by priteshthakkar on 2011-01-22
I am trying to configure shared folder but everytime it gives below error message
I have installed virtualbox 4.0 on windows 7 host and have ubuntu 10.10 64bit as a guest.

pritesh@easyweb:~$ sudo mount -t vboxsf Shared /home/pritesh/Desktop/Sharedstuff/
/sbin/mount.vboxsf: mounting failed with the error: Invalid argument

I have installed guest additions and i know it works.

Any help ?

Thanks,

---

### Post by slooksterpsv on 2011-01-22
> **priteshthakkar said:**
> I am trying to configure shared folder but everytime it gives below error message
I have installed virtualbox 4.0 on windows 7 host and have ubuntu 10.10 64bit as a guest.

pritesh@easyweb:~$ sudo mount -t vboxsf Shared /home/pritesh/Desktop/Sharedstuff/
/sbin/mount.vboxsf: mounting failed with the error: Invalid argument

I have installed guest additions and i know it works.

Any help ?

Thanks,

Sounds like the Guest Additions didn't install properly, make sure you have dkms and build-essential installed. To install them run (in terminal):
sudo apt-get install dkms build-essential

Then reinstall the guest additions (mount the Guest Additions cd first via Devices -> Install Guest Additions) via: sudo /media/VBOXADDITIONS<version may be here>/VBoxLinuxAdditions.run

try that.

---

### Post by CharlesA on 2011-01-23
Just a note: It's far easier to just add the repo to sources.list and install it that way. In any case, you'd have to purge Virtualbox 3.x if it's installed.

---

### Post by bkelly65us on 2011-02-02
I'm running Kubuntu 10 in vb on a windows xp machine. Everything is working fine (so far!) except usb support. I'm trying to mount my ipod classic in kubuntu but everytime I click on the usb icon on the bottom right and click the ipod virtualbox crashes. I've added myself to the vbox group, i/o apic off and on, added and removed device fileters in the usb section, you name it. No joy!  Anyone?

---

### Post by slooksterpsv on 2011-02-02
> **bkelly65us said:**
> I'm running Kubuntu 10 in vb on a windows xp machine. Everything is working fine (so far!) except usb support. I'm trying to mount my ipod classic in kubuntu but everytime I click on the usb icon on the bottom right and click the ipod virtualbox crashes. I've added myself to the vbox group, i/o apic off and on, added and removed device fileters in the usb section, you name it. No joy!  Anyone?

You may need the Extension pack for USB 2.0, then you have to enable USB 2.0 in the USB area. I haven't tried this but I found this information via: 
[http://forums.virtualbox.org/viewtopic.php?f=7&t=37493](http://forums.virtualbox.org/viewtopic.php?f=7&t=37493)

---

### Post by bkelly65us on 2011-02-03
Got the latest extensions and installed. Same issue occurs. Thanks for the lead, though. Very appreciated.

---

### Post by MickSulley on 2011-04-25
I am on 10.10 64 bit and I can't get vb to run at all.  If I start it from a terminal I get the error - 
> VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libGL.so.1: cannot open shared object file: No such file or directory


I have just tried removing vb 4.0 and installing vb 3.2 and I get the same error with that.

I found many hits on the vb forum but nothing that fixes it for me.  Any ideas?

Thanks
Mick

---

### Post by slooksterpsv on 2011-04-26
> **MickSulley said:**
> I am on 10.10 64 bit and I can't get vb to run at all.  If I start it from a terminal I get the error - 


I have just tried removing vb 4.0 and installing vb 3.2 and I get the same error with that.

I found many hits on the vb forum but nothing that fixes it for me.  Any ideas?

Thanks
Mick

Ubuntu or Kubuntu? If Ubuntu do the following, reinstall the virtualbox 4.0, then go to the terminal and type in:
sudo apt-get install -f

If any dependencies haven't been installed it should pick them up and install it. if that doesn't work, let me know. (It does require Qt4)

---

### Post by MickSulley on 2011-04-27
Fixed it!!

It couldn't find libGL.so.1 so I found it in a different directory and copied it to /usr/lib/virtualbox/ and now it works!!

Thanks for your help
Mick

---

### Post by Sunships on 2011-06-05
I am running Ubuntu 10.10 as a host, with a Windows XP guest in Virtualbox. I need to share a folder between the guest and the host, but do not want the Windows XP guest to have any internet access. If I disable the network adaptor in the Virtualbox settings then I cannot access the shared folder from the guest.

What is the best way to isolate the guest from the internet while still maintaining access to the shared folder?

Thank you.

---

### Post by jerrrys on 2011-06-05
I recently upgraded to 4.x.  the guess that i brought with me work fine.  but when i create a new guess in 4.x, the guess performance slows and cpu stays a 50% usage at idle.  its xserver eating it up.  any thoughts

and 2/3d turned off

---

### Post by roadrawts on 2011-06-05
> **slooksterpsv said:**
> In reading some of the threads on here about questions people have about VirtualBox 4, I thought I would try to answer some of them.

Any instructions assumes you know where to go to get to specific areas such as modifying users and groups, or accessing terminal, having virtualbox 4.0 downloaded, etc.

**WHAT'S NEW IN VIRTUALBOX 4.0**
They've changed the interface, fixed a few bugs, and added some new features.
- CD/DVD/BDROM Drives can now be SATA, they're not limited to ATA
- Live Previews on the VirtualBox main screen
- Addition of JRockITVE under other OSes
- Better (still buggy) 2D and 3D Acceleration
- Intel HD Audio
- More...

**HOW DO I INSTALL VIRTUALBOX 4.0 FROM THE TERMINAL?**
Open Terminal and cd to the directory where the DEB is located at. Type in the following:
sudo dpkg -i ./virtualbox-4.0_4.0.0-69151~Ubuntu~maverick_amd64.deb && sudo apt-get install -f

What that does is it tries to install VirtualBox, sees what's missing (libqt stuff) and installs it, thus finishing the installation of VirtualBox.

**HOW DO I GET USB SUPPORT TO WORK!?**
Open your users and groups area, by default (on Gnome) it's Settings -> Administration -> Users and Groups 

Now click your name -> Click Manage Groups -> Click vboxusers -> Click Properties -> Click a check on your name -> Click OK -> Authorize
 
Close all of your programs, save your stuff, log out, then log back in. USB support should work now.

**I NEED USB 2.0 SUPPORT** - UPDATE
I apologize I thought I had this in here before. USB 2.0 support is not included by default anymore. The only way to get USB 2.0 support (as well as PXE and RDP) is by downloading the VirtualBox Extension pack, via: 
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

After you download the file on that page, go ahead and open VirtualBox. Go to File -> Preferences -> Extensions - click on the button that looks like a diamond with an orange downward arrow (triangle). Locate the package and click on OK. Afterwards, make sure it's listed there with a green check.

Finally, you'll have to shutdown your VM to enable USB 2.0 Support. You go to the properties of the VM -> USB -> and put a check in Enable USB 2.0 (EHCI) Controller. Choose OK and startup your VM.

It may be beneficial to reinstall the Guest Additions on some machines. Others will pick up the USB 2.0 automatically.

You will need this especially if you need to sync iPods with Windows.

**THE RESOLUTION IN WINDOWS <VERSION> IS LOW**
Click on Device -> Install Guest Additions

Follow through and restart.

**THE RESOLUTION IN LINUX <VERSION> IS LOW**
This varies depending on Linux distrobution, as it requires dkms, kernel headers, etc. But to install you would do the following:

Open Terminal -> cd /media/VBOXADDITIONS/ -> execute the program as root for either 32-bit or 64-bit - e.g.:
sudo ./VBoxLinuxAdditions.run

There used to be a different version for x86 and amd64. This may also require you to install dkms and build-essential (if using Ubuntu). Which you can install via:

```

sudo apt-get install dkms build-essential

```

**AUDIO ISN'T WORKING**
Go to the settings on the VM, click on Audio on the left-hand side. Change it to Intel HD Audio or Soundblaster for Audio Controller. Make sure you're using the correct Host Audio Driver - mine is Pulse Audio - yours may differ. If it still fails, refer to VirtualBox documentation.

**HOW DO I ACCESS SHARED FOLDERS?**
NOTE: You can now have Shared Folders automatically mount/try to mount on the OS. To do this, when you create the Share via Devices -> Shared Folder, there's an option called Auto-mount - try this option if you're having trouble mounting shared folders.

Depending on the OS, you would do the following:
Windows, navigate to: \\VBOXSVR
Linux, mount it via (after installing Guest Edition), in terminal:

sudo mount -t vboxsf SHARENAME /path/to/mount/to

Where SHARENAME is the name of the share (you typed it in when setting up the in VirtualBox via Devices -> Shared Folder)
And /path/to/mount/to - is the location where you want to mount it to. E.g. you could make directories under /media to have it mount to.

**I'M GETTING AN IP OF 10.0.2.15 I WANT AN IP LOCAL TO MY NETWORK**
Click on Devices -> Network Adapters...
Change Attached To from NAT to Bridged
Change the Name to coincide with the Adapter you use for internet (mine I use wlan0 (wireless)).

**WHERE CAN I GET ADDITIONAL HELP**
Post here on the forums, google it, look through VirtualBox website documentation, etc.
Thanks for all of that info.  My questions are:  I have Ubuntu and Windows installed as bootable OS's with GRUB.  I want Ubuntu to be the base OS.  Should I remove Windows first, install Virtual Box, and then add Windows back in as a guest OS?  Is that the best way to do it?  Windows is Windows 7 Home Premium, but I would resintall XP since I don't like Windows 7.  Also, the Windows 7 is 64 bit, whereas Ubuntu is 32 bit.

---

### Post by SeijiSensei on 2011-06-05
> **Sunships said:**
> What is the best way to isolate the guest from the internet while still maintaining access to the shared folder?

Add an iptables rule to the host.  Suppose the guest has IP address 10.10.10.2.  Then run these commands:

```

sudo iptables -A INPUT -s 10.10.10.2 -d 10.10.10.0/24 -j ACCEPT
sudo iptables -A INPUT -s 10.10.10.2 -j REJECT

```

The first rule allows the guest to talk to the host; the second blocks all other traffic from the guest.

I'm assuming you're using the default NAT method on the guest.  If you are using bridging, the problem is more complicated since the guest appears to be directly on the network.

---

### Post by slooksterpsv on 2011-06-05
> **Sunships said:**
> I am running Ubuntu 10.10 as a host, with a Windows XP guest in Virtualbox. I need to share a folder between the guest and the host, but do not want the Windows XP guest to have any internet access. If I disable the network adaptor in the Virtualbox settings then I cannot access the shared folder from the guest.

What is the best way to isolate the guest from the internet while still maintaining access to the shared folder?

Thank you.

You could do it as Internal Network only which won't allow internet but allow access to any computers on the internal network.

---

### Post by slooksterpsv on 2011-06-05
> **jerrrys said:**
> I recently upgraded to 4.x.  the guess that i brought with me work fine.  but when i create a new guess in 4.x, the guess performance slows and cpu stays a 50% usage at idle.  its xserver eating it up.  any thoughts

and 2/3d turned off

Do you have compiz installed? If so, I would try disabling compiz effects. It may not just happen with VirtualBox though. I keep thinking theres an issue with Xorg overall and compiz causing issues.

> **roadrawts said:**
> Thanks for all of that info.  My questions are:  I have Ubuntu and Windows installed as bootable OS's with GRUB.  I want Ubuntu to be the base OS.  Should I remove Windows first, install Virtual Box, and then add Windows back in as a guest OS?  Is that the best way to do it?  Windows is Windows 7 Home Premium, but I would resintall XP since I don't like Windows 7.  Also, the Windows 7 is 64 bit, whereas Ubuntu is 32 bit.

1st are you wanting to boot Windows that's installed on its own partition in VirtualBox? If so I do not know how to do that, but there are threads that will show you how.

2nd if you install XP or 7 or what not, you won't be able to play games or do high-end multimedia stuff, even with the 2d/3d accelerations enabled. I would just try XP on a VirtualBox VM and see if it's going to work for what you're wanting to do.

3rd you couldn't do Windows 7 64-bit on a 32-bit machine. You'd have to use Ubuntu 64-bit. At least not AFAIK, maybe you can, if so I haven't heard of a way yet.

---

### Post by roadrawts on 2011-06-05
I think I have what I need now. Thanks. I didn't understand how Virtual Box worked but I think I do now.  Appreciate the help.

---

### Post by Sunships on 2011-06-06
Thank you so much SeijiSensei and slooksterpsv! I am indeed using the standard NAT method. slooksterpsv's suggestion seems to be doing the job for now :D

---

### Post by tiggsy on 2011-06-06
I'm using right control as the host key, but it doesn't work once windows has started up, for some reason. [This is on my Toshiba Satellite laptop. As my router died and I've yet to get a replacement (rarely needing to use more than 1 computer at once), I can't use my desktop (where it does work), which only has 1gb ram anyway (can't expand - it always fails :(( ).]

Thinking Tosh might have a non-standard right control key, I went into settings and selected it in there, but this made no difference.

If i wanted to be stuck in windows , I would have set up a partition, rather than mucking about with vb.

---

### Post by CharlesA on 2011-06-06
You can change the host key.

---

### Post by aveeshkumar on 2011-08-13
thank you thank you thank you.

---

### Post by Morbius1 on 2011-08-13
> **HOW DO I ACCESS SHARED FOLDERS?**
NOTE: You can now have Shared Folders automatically mount/try to mount  on the OS. To do this, when you create the Share via Devices ->  Shared Folder, there's an option called Auto-mount - try this option if  you're having trouble mounting shared folders.

Depending on the OS, you would do the following:
Windows, navigate to: \\VBOXSVR
Linux, mount it via (after installing Guest Edition), in terminal:

sudo mount -t vboxsf SHARENAME /path/to/mount/to

Where SHARENAME is the name of the share (you typed it in when setting up the in VirtualBox via Devices -> Shared Folder)
And /path/to/mount/to - is the location where you want to mount it to.  E.g. you could make directories under /media to have it mount to.You do realize that the manual or fstab mount is no longer necessary, right? When you have it automount it mounts it automatically to:

Linux Guest: /media/sf_share-name
Windows Guest: \share-name on 'vboxsrvr'

---

### Post by slooksterpsv on 2011-08-16
> **Morbius1 said:**
> You do realize that the manual or fstab mount is no longer necessary, right? When you have it automount it mounts it automatically to:

Linux Guest: /media/sf_share-name
Windows Guest: \share-name on 'vboxsrvr'

In some situations it may still be necessary. Nothing is guaranteed to work 100% of the time. If it works, great! If not, still need to follow the information.

---

### Post by Morbius1 on 2011-08-16
I would respectfully suggest you include in your original post the location of the default mount points when "Auto-Mount" is selected. If they don't know where to look they may not realize it's already mounted and they will edit fstab or do a manual mount for no reason.

---

