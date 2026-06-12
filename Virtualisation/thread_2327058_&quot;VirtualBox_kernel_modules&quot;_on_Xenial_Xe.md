---
title: "&quot;VirtualBox kernel modules&quot; on Xenial Xerus failed"
date: 2016-06-07
forum: Virtualisation
---

### Post by zeusys on 2016-06-07
Hi. 
I want to install virtualbox on Ubuntu 16.04. I downloaded virtualbox .deb file from its official website.
Here is the output of the installation : 
```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done


Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Do you want to install the software package? [y/N]:y
Selecting previously unselected package virtualbox-5.0.
(Reading database ... 384862 files and directories currently installed.)
Preparing to unpack virtualbox-5.0_5.0.20-106931~Ubuntu~xenial_amd64.deb ...
Unpacking virtualbox-5.0 (5.0.20-106931~Ubuntu~xenial) ...
Setting up virtualbox-5.0 (5.0.20-106931~Ubuntu~xenial) ...
Adding group `vboxusers' (GID 129) ...
Done.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)
Processing triggers for systemd (229-4ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160523-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...

```

As you can see, "modprobe vboxdrv" failed.
And when I run virtualbox, here is the output :
```

$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (4.4.0-22-generic) or it failed to
         load. Please recompile the kernel module and install it by


           sudo /sbin/rcvboxdrv setup


         You will not be able to start VMs until this problem is fixed.
$ sudo /sbin/rcvboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)

```

Please guide me how I can fix this issue?
Thank you

---

### Post by Fire_Chief on 2016-06-07
What output does dmesg show after you run the setup?

---

### Post by MAFoElffen on 2016-06-10
+1...

Because the output said:
> 
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. [COLOR=#ff0000]Please use 'dmesg' to find out why[/COLOR])


---

### Post by Gafanhoto on 2016-07-05
I'm having the same problem and this is what I got from dmesg

vboxdrv: module verification failed: signature and/or required key missing - tainting kernel

---

### Post by MAFoElffen on 2016-07-06
Correction to VirtualBoxes error message. Try:
```

sudo /usr/lib/virtualbox/vboxdrv.sh setup

```

---

### Post by fjgaude on 2016-07-12
Exactly the same issue here.

frank

---

### Post by fjgaude on 2016-07-12
Can't run the command because there is no vboxdrv.sh

frank

---

### Post by QDR06VV9 on 2016-07-12
> **fjgaude said:**
> Can't run the command because there is no vboxdrv.sh

frank

Is the linux-headers && dkms installed?

---

### Post by fjgaude on 2016-07-12
They are as a clean install, AFAIK.

---

### Post by QDR06VV9 on 2016-07-12
Is this error you recive
```
/usr/lib/virtualbox/vboxdrv.sh: command not found
```

---

### Post by fjgaude on 2016-07-12
Yes!

---

### Post by QDR06VV9 on 2016-07-12
Frank try this for me will you?
```
sudo /sbin/virtualbox setup
```

---

### Post by fjgaude on 2016-07-12
sudo /sbin/virtualbox setup

sudo: /sbin/virtualbox: command not found

I can't install vbox because of the conflict, of which I don't know. I've tried both Software and sofeware-center to install. I've tried 5.0 to 24 version, latest. I'm on UEFI install.  All work fine in BIOS install.

---

### Post by QDR06VV9 on 2016-07-12
Seems like you found the bug: [https://www.virtualbox.org/ticket/14646](https://www.virtualbox.org/ticket/14646)

---

### Post by fjgaude on 2016-07-12
This is so old, has little to do with what we are installing now, with 16.04 and UEFI.

---

### Post by QDR06VV9 on 2016-07-12
> _**I can't install vbox because of the conflict, of which I don't know.**_  I've tried both Software and sofeware-center to install. I've tried 5.0  to 24 version, latest. I'm on UEFI install.  All work fine in BIOS  install.
This is new or the first I have seen this...^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The only other thing that was advised to me by them (Oracle) was this:
> Some need to enable hardware-v in the PCs bios. This is a requirement for running 64-bit guests.

Some only needed to reinstall with
```
apt-get --reinstall install virtualbox virtualbox-dkms
```
this one is also important:
```
apt-get install linux-headers-`uname -r`
```

I am running:
```
VirtualBox Graphical User Interface
Version 5.0.24 r108355
Copyright © 2016 Oracle Corporation and/or its affiliates. All rights reserved.

```
But I had to run the command that MAFoElffen offered.

---

### Post by fjgaude on 2016-07-12
Thanks for all the suggestions. will keep trying things until I get it fixed.

frank

---

### Post by Bucky Ball on 2016-07-13
[QUOTE=zuesys]I downloaded virtualbox .deb file from its official website.[/QUOTE]

If I'm reading this correctly, just wondering: why did you download Virtualbox from a third-party and install from a .deb file? Virtualbox is in the repositories and has been for years. I had a quick look through the posts and not sure anyone's mentioned that. Simply install it from Software Centre, terminal, Synaptics, whatever your preferred mode of installation is.

Never had an issue with it. Installed from repos last week in 16.04 and had WinXP up and running as a guest and sharing partitions, printer, LAN in a bit less than an hour ...

---

### Post by fjgaude on 2016-07-13
Bucky Ball, is your 16.04 install UEFI? That's the whole issue with me. Installing as BIOS VBox works just fine, .deb or not.

frank

---

### Post by Bucky Ball on 2016-07-13
Ah, ha. My mistake. Will give that a go and see what I come up with. I did that last year from memory and don't remember what hoops I jumped through and how.

Away from that machine until next week, though, but will sniff when I'm with it ...

---

### Post by QDR06VV9 on 2016-07-13
> **Gafanhoto said:**
> I'm having the same problem and this is what I got from dmesg

vboxdrv: module verification failed: signature and/or required key missing - tainting kernel

That message is nothing to worry about, and has absolutely NOTHING to do with secure boot or UEFI. All that means, is that you're loading a kernel module that hasn't been fully tested/integrated with the kernel you're running. This message was intended to identify conditions which may make it difficult to properly troubleshoot a kernel problem. For example, loading a proprietary module can make kernel debug output unreliable because kernel developers don't have access to the module's source code (like the nVidia or ATI proprietary drivers), and can't determine what that module may have done to the kernel. Likewise, if the kernel had previously experienced an error condition or if a serious hardware error had occurred, the debug information generated by the kernel may not be reliable.

The WORST case, is that any kernel errors you encounter will be ignored by the kernel developers, until the authors of that module have fixed it. If things are running fine, you're in good shape, and there's nothing really to worry about. This is covered with a better explanation:
[https://www.kernel.org/doc/Documenta...ps-tracing.txt](https://www.kernel.org/doc/Documenta...ps-tracing.txt)
Source:[http://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/module-verification-failed-signature-and-or-required-key-missing-tainting-kernel-4175533442-print/](http://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/module-verification-failed-signature-and-or-required-key-missing-tainting-kernel-4175533442-print/)

---

### Post by fjgaude on 2016-07-13
Thanks, this is all well and good, but I don't have a working VBox.

So I wait until someone fixes either VBox or 16.04 under UEFI. <sigh>

---

### Post by QDR06VV9 on 2016-07-13
_*****This I had from around the time 12.04 came to life with my EFI Bios laptop.*****_
VirtualBox tends to forget its EFI boot entries. I know of two solutions to this problem:

    Move/rename the boot loader you're using (probably EFI/ubuntu/grubx64.efi on the EFI System Partition (ESP)) to EFI/BOOT/bootx64.efi. This is the default/fallback filename, and so VirtualBox will boot from it by default if there are no other entries.
    Use the VirtualBox EFI's menus to locate the boot loader you're using (again, probably EFI/ubuntu/grubx64.efi) and add it as a boot option. I don't recall the precise steps, and the menus aren't exactly user-friendly, but if you poke around in the menus, the options are there.

Doing either of these things should get GRUB starting, but then you've got the second issue, of X not starting. To solve this problem, try this:
Do a text-mode login.
    Type sudo su to acquire root privileges.
    Type Xorg -configure. This should create a file called /root/xorg.conf.new, IIRC.
    Copy that newly-create file to /etc/X11/xorg.conf.
   _** Optionally, edit**_ /etc/X11/xorg.conf. This may or may not be required. Personally, I edit the file to set the fbdev driver as the default, but you may prefer something else. There are lots of online guides to xorg.conf, but I don't have any URLs handy, and it can be pretty complex, so completely describing it here is impractical.
I had Credit to Rod Smith with the notes.
And the Source came from here: [http://askubuntu.com/questions/428789/uefi-boot-in-virtualbox-ubuntu-12-04](http://askubuntu.com/questions/428789/uefi-boot-in-virtualbox-ubuntu-12-04)
And on one of my test systems I actually had created a document by way of
```
sudo nano /etc/modules-load.d/virtualbox.conf
```
And add these lines to it:

```
vboxdrv
vboxnetadp
vboxnetflt
vboxpci

```
But bear in mind this was a few years ago...so your mileage may vary with xenial (16.04)
And on my Acer Laptop with UEFI And Xenial it just installed with no problems.

---

### Post by QDR06VV9 on 2016-07-13
> **fjgaude said:**
> Thanks, this is all well and good, but I don't have a working VBox.

So I wait until someone fixes either VBox or 16.04 under UEFI. <sigh>
That was not necessarily posted for you...that is why I quoted **Gafanhoto**

---

### Post by fjgaude on 2016-07-13
Somehow I'm not getting through. I boot 16.04 under UEFI. Then I try to install VBox, it fails. There no booting of VBox involved.

frank

---

### Post by QDR06VV9 on 2016-07-13
> **fjgaude said:**
> Somehow I'm not getting through. I boot 16.04 under UEFI. Then I try to install VBox, it fails. There no booting of VBox involved.

frank
Again not necessarily posted for you. But maybe someone else...
Regards

---

### Post by MAFoElffen on 2016-07-14
> **fjgaude said:**
> Somehow I'm not getting through. I boot 16.04 under UEFI. Then I try to install VBox, it fails. There no booting of VBox involved.

frank
Frank- He heard you. He was talking to the OP <-- The original Poster who is having his problem. You took it as if he was talking to you. He is booting differently than you. He is not having a problem of installing VBox on a clean install as you are, he is having a problem of multiple versions of pieces on an older install, as indicated when his oputput in post #1 says "upgrading an older version..." of the vbox dkms, (which it doesn't really upgrade)... Which you said, was "exactly like you" ... which really isn't like you, which you also indicate you are not.

So *@Frank). yes, you boot EFI, but don;t understand that you say you are having a "kernel module" load problem.. You are jalso umping between 2 treads. This one and your own. Between those two threads, you are saying conflicting things, when you compare that you are having the same problem...

Let's get you back to your own thread, where we can focus on your problem in your thread. Please? I'll jump back and try to remember what I want to post yesterday, before we couldn't post for 6 hours...

---

### Post by fjgaude on 2016-07-14
Thanks for setting me straight.

frank

---

