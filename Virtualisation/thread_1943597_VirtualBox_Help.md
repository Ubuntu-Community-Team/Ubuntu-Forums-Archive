---
title: "VirtualBox Help"
date: 2012-03-19
forum: Virtualisation
---

### Post by bman on 2012-03-19
So I am having the same issue in reference to this posting.

[http://askubuntu.com/questions/85568/cpu-is-not-compatible-with-64-bit-mode-error-trying-to-install-windows-7-64-b](http://askubuntu.com/questions/85568/cpu-is-not-compatible-with-64-bit-mode-error-trying-to-install-windows-7-64-b)

I checked my BIOS and the feature is enabled, and made sure I choose 64bit when creating it. Still have the same issue.

Any ideas?

---

### Post by haqking on 2012-03-19
> **bman said:**
> So I am having the same issue in reference to this posting.

[http://askubuntu.com/questions/85568/cpu-is-not-compatible-with-64-bit-mode-error-trying-to-install-windows-7-64-b](http://askubuntu.com/questions/85568/cpu-is-not-compatible-with-64-bit-mode-error-trying-to-install-windows-7-64-b)

I checked my BIOS and the feature is enabled, and made sure I choose 64bit when creating it. Still have the same issue.

Any ideas?

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

---

### Post by bman on 2012-03-19
I read that before. If you are referring to being on a 32bit OS, I am not. 64bit.

And the second thing, pretty sure that is set. Where can I find that though?

---

### Post by QIII on 2012-03-19
Is your install disk an OEM or retail disk?

---

### Post by BertN45 on 2012-03-19
Dell I have a 64 bit Dell Inspiron 1521 and have enabled the BIOS setting for virtualisation, but it does not work. Dell messed it up.
Not all 64 bit machines support HW virtualisation and not all machine with that BIOS setting really work.

It was confirmed when I looked on Google for "Inspiron 1521 virtualisation" Nobody has positive news. For a moment I blamed virtualbox and tried KVM, but that had the same problem.

---

### Post by bman on 2012-03-19
It's Retail.

---

### Post by QIII on 2012-03-20
Good.  Sometimes the OEM disks are problematic in virtual machines - besides the fact that sometimes the MS EULA forbids the use of OEM disks in virtual machines.

How many cores do you have?  Can you spare two cores for the VM while leaving some for your host?

If so, give that a try and let us know what happens.

---

### Post by nothingspecial on 2012-03-20
*Thread moved to **Virtualization**.*

---

### Post by bman on 2012-03-20
Failed to open a session for the virtual machine Windows 7.

VT-x features locked or unavailable in MSR. (VERR_VMX_MSR_LOCKED_OR_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

I am getting this error now, if i put it back to 1 CPU its back to the other problem.

---

### Post by haqking on 2012-03-20
> **bman said:**
> Failed to open a session for the virtual machine Windows 7.

VT-x features locked or unavailable in MSR. (VERR_VMX_MSR_LOCKED_OR_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

I am getting this error now, if i put it back to 1 CPU its back to the other problem.

you sure you have hardware vt-x turned on ?

the check box on the acceleration tab of system which was mentioned on the link i referred you to earlier, it is required for x64

---

### Post by bman on 2012-03-20
100% sure it's checked. This is why I posted here. Everything should be working.

---

### Post by QIII on 2012-03-20
Did you provide machine specs?  Am I even more blind than I thought?

---

### Post by bman on 2012-03-20
Can you elaborate please? What exactly. I filled out all the specs.

---

### Post by QIII on 2012-03-20
My bifocals may be a bit dirty.  Which post number includes your machine specs?  Help an old man out.

---

### Post by bman on 2012-03-20
I didn't post them here if that is what your talking about. Did not think it made any difference. It's a powerful enough system.

Radeon 5850
Quad core 2.4GHz Old gen
lots of hard drive space
8GB DDR2 Memory
Dont remember my motherboard type.

---

### Post by QIII on 2012-03-20
I think the motherboard is going to be the key.

If you do 

```
sudo dmidecode
```you'll get a bunch of info.

Scroll down a bit and you should find "Base Board Information".

---

### Post by bman on 2012-03-20
Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer:  EVGA 
	Product Name: 132-CK-NF78
	Version: 2
	Serial Number: 1

---

### Post by QIII on 2012-03-20
What version of VirtualBox are you using?

---

### Post by QIII on 2012-03-20
Try setting "Trusted Execution" to off in your BIOS.

[https://forums.virtualbox.org/viewtopic.php?f=7&t=45491&p=206350#p205105](https://forums.virtualbox.org/viewtopic.php?f=7&t=45491&p=206350#p205105)

---

### Post by bman on 2012-03-20
I am running the latest version. Just installed it. Can't seem to find version number.

I also can't find Trusted Execution in my BIOS. But I am running Compiz, could that be using VT-x and causing it to be locked?

---

### Post by QIII on 2012-03-20
Never caused me any problems.

I think that link mentioned some other things some manufacturers my call it and a couple of other settings.

I'll read through it again and also see if I can find anything more on the VirtualBox forum.

By the way, I didn't find anything specifically mentioning your model of motherboard.

---

### Post by bman on 2012-03-20
Yea I noticed the different names for it but none are in my BIOS.

---

### Post by QIII on 2012-03-20
OK.  I'm going to do some searching over the next day or two.  I'll check back in on this thread and see how you are coming along.

This is going to be something so obvious we'll both slap ourselves, I suspect.

---

### Post by bman on 2012-03-20
Sounds like a plan.

I just checked to see if I had kvm running, nope. And disabling Compiz of course didn't do anything.

---

### Post by bman on 2012-03-20
See if I set it to only 1 CPU, this is the error I get. It starts to load after this, and then does nothing.

VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.

Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.

---

### Post by Insomn1a on 2012-03-21
here is something i found that might be useful. This is from the virtualbox forums.

[https://forums.virtualbox.org/viewtopic.php?t=8669](https://forums.virtualbox.org/viewtopic.php?t=8669)
> Another hint: after enabling VT-X/AMD-V in the BIOS you might need to switch the PC off completely, unplug it, or remove laptop battery for a minute. Ea:
Reboot the Host and go into the BIOS
disable vt-x, save BIOS settings, pause machine after bios boot messages
power down the Host (unplug power cord!)
start the Host and go into the BIOS
enable vt-x, save BIOS settings, pause machine after bios boot messages
power down the Host (unplug power cord!)
Boot the Host.



Some more info:

[https://forums.virtualbox.org/viewtopic.php?f=4&t=18685](https://forums.virtualbox.org/viewtopic.php?f=4&t=18685)

---

### Post by bman on 2012-03-21
Umm if I understand that correct.

Basically disable the feature in the BIOS, and then re-enable it? I have doubts that will make a differnce lol. But I guess worth a shot.

---

### Post by Insomn1a on 2012-03-22
> **bman said:**
> Umm if I understand that correct.

Basically disable the feature in the BIOS, and then re-enable it? I have doubts that will make a differnce lol. But I guess worth a shot.


> 
A common misconception about 64bit hardware: Having 64bit hardware/cpu does NOT mean you have VT-X/AMD-V as well, in other words: yes you can run a 64bit OS on 64bit hardware as a HOST, but a 64bit GUEST NEEDS VT-X/AMD-V to be active and enabled.

Also make sure another virtualizer isn't installed or running like KVM or Hyper-v. See also, click here.

HowTo: determine if VT-X/AMD-V is really activated and used by VirtualBox.

Another hint: after enabling VT-X/AMD-V in the BIOS you might need to switch the PC off completely, unplug it, or remove laptop battery for a minute. Ea:
Reboot the Host and go into the BIOS 
disable vt-x, save BIOS settings, pause machine after bios boot messages
power down the Host (unplug power cord!)
start the Host and go into the BIOS 
enable vt-x, save BIOS settings, pause machine after bios boot messages
power down the Host (unplug power cord!)
Boot the Host.
This section mentions powering the system down after you disable the vtx feature, then unplugging the workstation or laptop and removing the battery. If you know where the CMOS battery is located on you motherboard and you know how to remove it, I would do that as well.

If its a laptop just removing the main battery should do it.

the CMOS battery looks like this 
[IMG]http://www.computerhope.com/jargon/c/cmos.jpg[/IMG]

If you know already disregard lol

---

### Post by bman on 2012-03-22
Thanks I understood that post.

The problem is that feature was already enabled, has been since I bought the computer years and years ago. Which is why I knew disabling it and re-enabling it would do nothing, and it didn't.

---

### Post by bman on 2012-03-22
I went ahead and installed a 32bit version of Windows.

I am trying to install guest additions to it, but the read me for VirtualBox makes no sense to me. Anyone?

---

### Post by CharlesA on 2012-03-22
> **bman said:**
> I went ahead and installed a 32bit version of Windows.

I am trying to install guest additions to it, but the read me for VirtualBox makes no sense to me. Anyone?
Mount the ISO on the virtual machine then double click the cd drive to start the setup.

---

### Post by bman on 2012-03-22
Oh so it's a download, thought it was like an option within the program.

---

### Post by CharlesA on 2012-03-22
> **bman said:**
> Oh so it's a download, thought it was like an option within the program.
The ISO is included with virtualbox and you should be able to select "install guest additions" from the devices or machine menu inside virtualbox.

---

### Post by bman on 2012-03-22
There are no menus in VirtualBox on Linux.

---

### Post by CharlesA on 2012-03-22
Are you running it headless?

---

### Post by bman on 2012-03-22
It's all defaut. I don't know.

---

### Post by CharlesA on 2012-03-22
> **bman said:**
> It's all defaut. I don't know.
Check this out then:
[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

---

### Post by bman on 2012-03-22
I don't know about menus, but I mounted it and installed it.

Not reading before that has nothing to do with USB stuff. I am trying to connect my phone (Amaze 4G) and the guest won't see it.

---

### Post by QIII on 2012-03-22
Are you saying that when you select and start your Windows virtual machine, there are no menu items in the upper left of the window that contains it?

---

### Post by bman on 2012-03-22
Here is how it looks.

And not important at the moment, phone not being seen?

---

### Post by CharlesA on 2012-03-22
Interesting. Try hitting right control then alt and see if the menu bar shows up.

---

### Post by QIII on 2012-03-22
Hopefully CharlesA's suggestion will work because you won't see that phone until you get the guest additions installed and do a couple of other things to get your USB support going.

---

### Post by CharlesA on 2012-03-22
> **QIII said:**
> Hopefully CharlesA's suggestion will work because you won't see that phone until you get the guest additions installed and do a couple of other things to get your USB support going.
Yeah. If the menubar doesn't show up, you can always mount the ISO manually and install it that way, but it's more work.

---

### Post by bman on 2012-03-22
Nope, that does not work. No combination of Alt & Crtl work. :(

Well that is what I did, mounted the ISO within the guest, installed it. But did it work, I don't know... USB still not working.

---

### Post by QIII on 2012-03-22
You still have to add yourself to the vboxusers group.  On my cell phone, so a bit hard to give instructions.

---

### Post by bman on 2012-03-22
Found this.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

But, I don't have a Users & Group option, just users, and all I can do is add user. ARRrrgg!!

**Followed this to add myself to group. [http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/)

Testing now.

***Still not working.

---

### Post by QIII on 2012-03-22
Did you log out and back in?

---

### Post by bman on 2012-03-22
Logged out and in, and it's working.

But now the guest (windows) said driver was not successfully installed.

---

### Post by QIII on 2012-03-22
The Windows driver for your phone?

---

### Post by bman on 2012-03-22
Yea I believe that is what it is. Should have installed it automatically, its the driver needed for the USB Mass Storage.

---

### Post by QIII on 2012-03-22
You'd think so.  Does your phone have any settings for charge/disk?  

Do you have a thumb drive you can test?

---

### Post by bman on 2012-03-22
Yes it has that option, I know which to choose.

Plugged in a thumb drive, same issue. Basically doesn't install driver properly, and so they don't show up.

---

### Post by QIII on 2012-03-22
Go back to virtualbox.org to download and install the extension pack.

---

### Post by bman on 2012-03-22
Did that, still won't install drivers. WTF!

*checked the option for usb 2.0 devices, testing now.

YEP! Everything is working great now! Thank you so much for the help.

Now, back to the 64bit original issues/questions.

---

### Post by QIII on 2012-03-22
Hey, that's what we're here for.

As for the 64bit thing, I admit I am totally stumped!

---

### Post by bman on 2012-03-23
This is problably the wrong topic now, and place but.

Anyone know if it's possible to get USB Debugging Mode on Android phones to work with Virtualization?

---

### Post by CharlesA on 2012-03-23
> **bman said:**
> This is problably the wrong topic now, and place but.

Anyone know if it's possible to get USB Debugging Mode on Android phones to work with Virtualization?
Not a clue. It might be possible, but you'd be going thru the VM software so I don't know how accurate it would be.

---

### Post by bman on 2012-03-23
Darn, I guess I will be borrowing a friends system. I guess I only need Windows one time, to flash the recovery, after that it's quite easy.

Thanks again.

---

### Post by shoebshatil on 2013-03-19
Hey I have faced similar problem today and it was fixed in below way- [Hope it will help]

1st I tried to execute this command as suggested by VirtualBox while crashing-
**$ sudo /etc/init.d/vboxdrv setup**
But it returned and error like this-
 * Stopping VirtualBox kernel modules                                         [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 3.5.0-26-generic cannot be found.
Please install the linux-headers-3.5.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

So, next what I did is- tried to install linux-headers-3.5.0-26-generic package by
**$ sudo apt-get install linux-headers-3.5.0-26-generic**

And it was installed successfully. Then again I tried to execute previous command-
[B]$ sudo /etc/init.d/vboxdrv setup

[/B]Butnow I've got different scenario- * Stopping VirtualBox kernel modules                [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                                              [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                              [ OK ] 
 * Starting VirtualBox kernel modules                                                                 [ OK ] 

So, here is the conclusion from my side. It happened due to auto update virtual box by ubuntu. I guess there could be some problem with linux kernel.
But anyway, as it is fixed in the above way within a short period of time, I am happy.[B]

FYI-[/B] I am using **Ubuntu 12.10**

---

### Post by Elfy on 2013-03-19
Please don't post answering people's queries from a year ago.

---

