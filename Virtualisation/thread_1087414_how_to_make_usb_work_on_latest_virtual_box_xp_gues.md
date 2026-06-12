---
title: "how to make usb work on latest virtual box? xp guest"
date: 2009-03-05
forum: Virtualisation
---

### Post by shateredsoul on 2009-03-05
I got usb to work on my old version of virtual box.. then my ubuntu died. ACtually..  I killed it.  So I had to reinstall everything.  I used the following guide to get usb working on virtual box.. but now it doesn't work.

[http://www.blinkedph.com/2008/09/how-to-install-latest-version-of.html]("http://www.blinkedph.com/2008/09/how-to-install-latest-version-of.html")

When I go to edit the file.. the lines they ask me to edit are no longer exist in the document.  Any ideas on what would work on the newer version of vbox?


-a side question
--> is there a post on things NOT to do for newbies? I messed up my ubuntu installation when trying to make it recognise my ipod in vbox.

---

### Post by shateredsoul on 2009-03-06
anyone?

---

### Post by d3railur on 2009-04-12
Bump this.  I am having a problem getting my Windows Vista 32 bit guest to detect my SCR3310 USB smartcard reader while running on Virtualbox 2.2 (newest version downloaded off vbox website).  I am running Ubuntu 8.10.  If any more info is needed, let me know and I will provide it.  Thanks in advance.

---

### Post by ninjapirate89 on 2009-04-12
Don't hold me to this but I dont think the open source version of virtualbox supports usb. I will look into it.

Edit -> According to the VBox page USB support is only in the closed source version. On the VBox page under Virtualbox binaries you can download this version.

---

### Post by d3railur on 2009-04-13
Ninjapirate,

Thanks for the quick reply.  I do have the 'closed source' version of Sun Virtualbox.  

The options for USB are present, and I have them enabled - I've tried turning them on and off, enabling/disabling USB 2.0 support etc etc.

The guest (Vista) can only see the mouse (USB) but can't see any other USB devices - specifically my smartcard reader.

---

### Post by ninjapirate89 on 2009-04-13
Sorry but I can't be of much more help. I only used Virtualbox for a short time and switched to dualbooting instead because it was too slow for me. I'll keep searching the tubes for anything that may help though.

---

### Post by ninjapirate89 on 2009-04-13
Maybe you could try this. I never needed to have usb support in virtualbox when I used it so I don't know if it will work or not.

Edit -> Woops forgot the link. [http://stikiflem.wordpress.com/2008/08/30/enable-usb-support-in-virtualbox/]("http://stikiflem.wordpress.com/2008/08/30/enable-usb-support-in-virtualbox/")

---

### Post by d3railur on 2009-04-13
Ninjapirate,

Thanks again.  I have tried that fix already.  It is for an older version of Virtualbox I believe - Those settings are not in the file specified in the fix.  But I do appreciate the effort.

---

### Post by ninjapirate89 on 2009-04-13
Maybe if this thread is moved to the Virtualization section you'll find someone who can help more.

Edit-> I just asked the mods to have it moved.

---

### Post by RedSingularity on 2009-04-13
Did you install the restricted extras?

---

### Post by ninjapirate89 on 2009-04-13
> **Shadow121 said:**
> Did you install the restricted extras?

How would that help?

---

### Post by RedSingularity on 2009-04-13
Oh sorry i mean the Virtual Box guest additions.

---

### Post by ninjapirate89 on 2009-04-13
Oh yeah that might help.

---

### Post by d3railur on 2009-04-13
Yes I did.

---

### Post by d3railur on 2009-04-14
Any more ideas on this?  I have found a lot of resources for previous versions of Ubuntu / Virtual Box.  But they don't work / match with what I am seeing with Ubuntu 8.10 and Virtual Box 2.2

From what I am reading (keep in mind I am a Linux nub) I think that the host (Ubuntu) is 'using' the smart card reader and not making it available to the guest (Vista).  Is there a way for me to 'release' the device from Ubuntu - maybe through the terminal?

Any help would be much appreciated!  I will have to go to a dual boot if I can't get this USB issue resolved :(

---

### Post by bluefrog on 2009-04-14
if the following command doesn't answer you "busy" for each usb device then you have a permissions problem.
(vbox running or not, doesn't matter)

VBoxManage list usbhost

if permission problem, then make sure your user is a member of vboxusers and edit the file /etc/udev/rules.d/10-vboxdrv.rules and change
SUBSYSTEM=="usb_device", GROUP="root", MODE="0664"
to
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"

you will need to restart udev in order to have the correct permissions on 
/dev/bus/usb/00*/00*  (vboxusers group ownership).

If this is not it, then describe your problem.

---

### Post by uidb4056 on 2009-04-14
On 8.10 only is needed to add in /etc/fstab the next line

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

Obviously your user must be member of vboxusers group.

---

### Post by d3railur on 2009-04-14
> **bluefrog said:**
> if the following command doesn't answer you "busy" for each usb device then you have a permissions problem.
(vbox running or not, doesn't matter)

VBoxManage list usbhost

if permission problem, then make sure your user is a member of vboxusers and edit the file /etc/udev/rules.d/10-vboxdrv.rules and change
SUBSYSTEM=="usb_device", GROUP="root", MODE="0664"
to
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"

you will need to restart udev in order to have the correct permissions on 
/dev/bus/usb/00*/00*  (vboxusers group ownership).

If this is not it, then describe your problem.

I had already set up vboxdrv.rules in this manner.  

When I run 'VBoxManage list usbhost' all devices come back as - 
Current State:      Unavailable

Just to be safe, I ran this with Virtual box on and off - same result.

So based on your post, I believe this is a permissions issue.  The question, how to fix it?  

Thanks for your input and any more help you can provide on this.


> **uidb4056 said:**
> On 8.10 only is needed to add in /etc/fstab the next line

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

Obviously your user must be member of vboxusers group.

Already did this one done too.  But again, thanks for the input.

---

### Post by bluefrog on 2009-04-15
I gave you the answer in my previous post.

Stop fiddling with fstab and other crazy things.

what is the result of **ls -l /dev/bus/usb/00*/00***

/etc/udev/rules.d/10-vboxdrv.rules is a file created by vbox at install time.

Depending on the package used to install (deb, run...) that file could have root or vboxusers as GROUP. it needs to be vboxusers.

you need to be part of vboxusers (sudo gpasswd -a $USER vboxusers   .  logout/login)

---

### Post by d3railur on 2009-04-15
The result of ls -l /dev/bus/usb/00*/00* :


a@1:~$ ls -l /dev/bus/usb/00*/00*
crw-rw-r-- 1 root vboxusers 189,   0 2009-04-13 19:09 /dev/bus/usb/001/001
crw-rw-r-- 1 root vboxusers 189,   1 2009-04-13 19:09 /dev/bus/usb/001/002
crw-rw-r-- 1 root vboxusers 189, 128 2009-04-13 19:09 /dev/bus/usb/002/001
crw-rw-r-- 1 root vboxusers 189, 256 2009-04-13 19:09 /dev/bus/usb/003/001
crw-rw-r-- 1 root root      189, 257 2009-04-15 05:32 /dev/bus/usb/003/002
crw-rw-r-- 1 root vboxusers 189, 384 2009-04-13 19:09 /dev/bus/usb/004/001
crw-rw-r-- 1 root vboxusers 189, 512 2009-04-13 19:09 /dev/bus/usb/005/001
crw-rw-r-- 1 root vboxusers 189, 513 2009-04-13 19:09 /dev/bus/usb/005/002
crw-rw-r-- 1 root vboxusers 189, 640 2009-04-13 19:09 /dev/bus/usb/006/001
crw-rw-r-- 1 root vboxusers 189, 768 2009-04-13 19:09 /dev/bus/usb/007/001
crw-rw-r-- 1 root vboxusers 189, 769 2009-04-13 19:09 /dev/bus/usb/007/002
crw-rw-r-- 1 root vboxusers 189, 896 2009-04-13 19:09 /dev/bus/usb/008/001
crw-rw-r-- 1 root vboxusers 189, 898 2009-04-13 19:09 /dev/bus/usb/008/003

I am part of vboxusers.  And performed the fix on vboxdrv.rules previously.  I also checked it again and it matched what you have written.

---

### Post by naturalbornengineer on 2009-04-15
Have you created a filter that only lets your card reader device pass through from the host to the guest? Your usb mouse (which you previously mentioned) has nothing to do with usb devices being available to the guest, since the host takes care of mouse and keyboard availability to the guest. So don't create an empty filter. If you have already created a filter (maybe I'm stating something obvious but it wasn't mentioned anywhere before), then I'm sorry I couldn't help.

---

### Post by d3railur on 2009-04-15
> **naturalbornengineer said:**
> Have you created a filter that only lets your card reader device pass through from the host to the guest? Your usb mouse (which you previously mentioned) has nothing to do with usb devices being available to the guest, since the host takes care of mouse and keyboard availability to the guest. So don't create an empty filter. If you have already created a filter (maybe I'm stating something obvious but it wasn't mentioned anywhere before), then I'm sorry I couldn't help.

No I have not created a filter.  This is the first I've seen/heard of this possibility.  How would I do this?  Thanks in advance.

---

### Post by naturalbornengineer on 2009-04-15
BEFORE powering on your virtual machine (but after having selected the guest OS that concerns you), click on the USB link on the right side of the VirtuaBox window. Under the two options for USB there is an empty list of filters (if this is the first time you encounter this list). There is an option to add a filter on the right. Click on it and select the device of your choice. Click OK/Apply (currently I have VirtualBox removed and this is what I remember but I think you know the drill) and then start the virtual machine.

---

### Post by d3railur on 2009-04-15
Oh yes, I did do that. 

I have in fact 'fixed' this problem. I upgraded to Jaunty from Intrepid and reinstalled VirtualBox(it didn't work at all after the upgrade - although I still had my guest after the uninstall/reinstall of VB). 

Everything works fine now.  I do not know how it fixed it or if the fix could be recreated, but bottom line is I have the functionality I desire.

Thanks to all who have contributed to this thread.  Even though it was a simple OS upgrade that fixed the problem - your efforts are appreciated.

---

