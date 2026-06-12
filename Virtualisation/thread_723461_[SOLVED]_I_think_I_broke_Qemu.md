---
title: "[SOLVED] I think I broke Qemu"
date: 2008-03-13
forum: Virtualisation
---

### Post by patrickaupperle on 2008-03-13
I ran puppy linux in qemu and it worked great. I was enjoying being able to do virtualization.  :) Then I decided to try my debian iso  and when I tried to boot it this came up (screenshot).:(:( Then anytime I tried to boot anything it came up. I tried puppy again and same message. Any suggestion on fixing it? Should I move to different software?

	:cry:	:cry:	:cry:


Edit: If I should switch software, I want one that can boot ISOs as well as normal images.

---

### Post by patrickaupperle on 2008-03-13
Bump

---

### Post by patrickaupperle on 2008-03-13
If this is unfixable (or if you don't know how)  please post something. I also need to know how to remove qemu and what software would be suggested if this is the case.

---

### Post by ruibernardo on 2008-03-13
Hi patrick,

you are trying to boot QEMU with an ISO file, but you are not telling QEMU to boot from it. The option is "-boot d" to boot from the cd-rom.

I see that you are also using "sudo" to launch QEMU. You should NOT do this. It is not needed and is certainly not advisable in any circumstances, unless you really want to because for some mysterious reason.


A very good page about QEMU, setting it up and use it is [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo). From there you can enable kqemu accelerator, virtual networking and usb.

---

### Post by patrickaupperle on 2008-03-13
-boot d didnt work, but -cdrom  did

Thank you, any idea on how to  get debian working? I posted that somewhere else, ill go get the link.

edit: [http://ubuntuforums.org/showthread.php?t=719055](http://ubuntuforums.org/showthread.php?t=719055)

---

### Post by ruibernardo on 2008-03-13
Sorry, about that :)

My actual complete command line to boot a debian testing/lenny is (copy/paste to a text editor, adapt it, save it a file and make it executable - chmod +x scriptname):
```
#/bin/sh
qemu -m 384 \
    -localtime \
    -hda '/home/myuser/qemu/lenny/lenny.ovl' \
    -hdb '/home/myuser/qemu/lenny/hdb.raw' \
    -boot c \
    -cdrom '/home/myuser/Desktop/CDs/mini-debian-testing.iso' \
    -net none \
    -usb 

```EDIT:change "-boot d" to boot from the "-cdrom iso_file".

---

### Post by ruibernardo on 2008-03-13
Here some GUI tools to deal with QEMU options and make your life easier with QEMU: [qemu-launcher]("http://projects.wanderings.us/qemu_launcher") and [qemulator]("http://qemulator.createweb.de/"), both on the Ubuntu repositories.

---

### Post by patrickaupperle on 2008-03-13
> **epimeteo said:**
> Sorry, about that :)

My actual complete command line to boot a debian testing/lenny is (copy/paste to a text editor, adapt it, save it a file and make it executable - chmod +x scriptname):
```
#/bin/sh
qemu -m 384 \
    -localtime \
    -hda '/home/myuser/qemu/lenny/lenny.ovl' \
    -hdb '/home/myuser/qemu/lenny/hdb.raw' \
    -boot c \
    -cdrom '/home/myuser/Desktop/CDs/mini-debian-testing.iso' \
    -net none \
    -usb 

```EDIT:change "-boot d" to boot from the "-cdrom iso_file".

Can you explain what this does?

---

### Post by ruibernardo on 2008-03-13
```
qemu -m 384 \
    -localtime \
```Starts a qemu VM with 384 MB of RAM and its BIOS clock set to the time of the clock in the host...
```

    -hda '/home/myuser/qemu/lenny/lenny.ovl' \

```... with a hard disk connected to hda. The file for hda is lenny.ovl, which is an overlay of another disk file (lenny.img), so any changes in the VM are not saved on the original disk file. You have to use the command qemu-img to create disk files (type "man qemu-img" for more info).
```

    -hdb '/home/myuser/qemu/lenny/hdb.raw' \

```This line adds a second hard disk to hdb. The file for this disk is hdb.raw and is in RAW format, created by qemu-img. I use it to save files in it and later I mount the disk file in the host and use it as another mount point to retrieve the files. 
```

    -boot c \

```Boot from the hard disk.
```

    -cdrom '/home/myuser/Desktop/CDs/mini-debian-testing.iso' \

```Use the iso file as a cdrom.
```

    -net none \
    -usb

```No network, but usb enabled (need to add usb devices by pressing Alt+Ctrl+2 on the VM and type "info usbhost" and then add "usb_add host:1234:5678"). Remove the "-net -none" line to have network.

Read the docs to know more about QEMU.

The GUI tools that I posted before - qemu-launcher and qemulator - handle all this options for you with a GUI. 

Here is a link to a video file with qemulator: [http://qemulator.createweb.de/content.php4?theme=Qemulator+first+run+tutorial&haupt=Qemulator+first+run+tutorial&typ=richdoc](http://qemulator.createweb.de/content.php4?theme=Qemulator+first+run+tutorial&haupt=Qemulator+first+run+tutorial&typ=richdoc)

Try it (or qemu-launcher), it's more simple and less confusing for the start.

---

### Post by patrickaupperle on 2008-03-13
Thankyou for all the trouble you went to. I tried with these options on Qemu-launcher and it still did not work. Maybe it would be easier to duel boot.

---

### Post by ruibernardo on 2008-03-13
I took a look on the screenshots you have on [your other thread]("http://ubuntuforums.org/showthread.php?t=719055") (should have looked before). Your problem may be because of the version of QEMU you are using, since you use Gutsy. I had some problems booting my VM when I upgraded to Gutsy, and had to "downgrade" the qemu packages to Feisty to have QEMU working again. Take a look here about this problem: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368).

To do it (worked for me):
- Removed the kqemu module:
```
sudo modprobe --remove kqemu
```- Uninstalled qemu gutsy packages:
```
sudo apt-get remove qemu kqemu-sources kqemu-common kqemu-modules

```- Opened my sources.list file with sudo permissions
```
gksudo gedit /etc/apt/sources.list &
```- Replaced every "**gutsy**" word with "**feisty**" and saved the file (don't close gedit).
- Updated APT to use Feisty repositories:
```
sudo apt-get update
```- Installed qemu back again from Feisty repository:
```
sudo apt-get install qemu kqemu-source
```- Installed qemu again **[as described here]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo#head-c75594fe6a7fc43fca1bd0195b5356a994f82962")** (make sure you remove the actual kqemu module from memory and load the new one). 
- **IMPORTANT**: changed back the repositories. In the text editor (gedit), click "Undo" until you have _replaced all "feisty" back to "gutsy"_. Save the file and close gedit.
- Open Synaptic and click "Update". You should have some updates for qemu. Don't upgrade! Block this feisty version. Select both packages "qemu" and "kqemu-source" and _in Synaptic menu select "Package"->"Block version"_. Now feisty qemu packages will not be upgraded.

Then try to boot Debian again.

If Debian still fails to boot, with the "busybox" error, even with "**-no-acpi**" option in QEMU, (with Feisty packages, this should not happen) then consider using VirtualBox OSE (on the repositories).

---

### Post by patrickaupperle on 2008-03-13
is all of this really necassary? Are you sure there is not some .deb or something that would be easier? maybe it would be easier to use virtualbox. I never installed kqemu.

---

### Post by ruibernardo on 2008-03-13
On the bug page some people say that just changing the bios (bochsbios) package can make it work. It didn't for me.

I just was trying to help you to get QEMU working. Definitely much more easy to install and use is VirtualBox.

To install VirtualBox, from the repositories: [https://help.ubuntu.com/community/VirtualBox#head-4864eba9f3e39b9139a1615a696676368ca69977](https://help.ubuntu.com/community/VirtualBox#head-4864eba9f3e39b9139a1615a696676368ca69977)

---

### Post by patrickaupperle on 2008-03-13
What all do I  need to do to completely remove qemu? and is removing VirtuaBox easy?

> Add yourself to the vboxusers group. You can add more usernames after "whoami" if you wish.

sudo gpasswd -a `whoami` vboxusers


This won't effect my administration abilities, will it?

---

### Post by ruibernardo on 2008-03-14
> **patrickaupperle said:**
> What all do I  need to do to completely remove qemu?
To remove qemu:
> **epimeteo said:**
> - Uninstalled qemu gutsy packages:
 ```
sudo apt-get remove qemu kqemu-sources kqemu-common kqemu-modules
 
```
 
> **patrickaupperle said:**
> 
 and is removing VirtuaBox easy?
With the Debian package system it's very simple.
> **patrickaupperle said:**
> 
This won't effect my administration abilities, will it?
No, it just adds your username (the output of "whoami", try it) to the "vboxusers" group, so you can use/connect/whatever to the devices and VM that have only permissions to be used by users of the "vboxusers" group. 

You can have more users on your system, and not all the users should use VirtualBox. If they aren't on the "vboxusers" group, they can't use VirtualBox.

---

### Post by patrickaupperle on 2008-03-14
Thankyou for everything. You have been most helpful.  I am adding Virtual box right now. I will let you know of the results. Just one more question, How much ram should I give during the vm install process? Is it changeable at a later time?

are updates ok?

---

### Post by patrickaupperle on 2008-03-14
Read the above post also.

I installed kubuntu kde 4 hardy on virtual box. I then did a full upgrade from adept. It downloaded some 200 packages and started installing then them. At a samba update it just stopped. What should I do?

---

### Post by fjgaude on 2008-03-14
From my testing experience with Hardy, it is presently broken, unless you have updated on a dailing basis from about Alpha 2. If you installed from, say Alpha 5 or 6, and then updated: it is broken.

Go back to Gutsy or Feisty.

---

### Post by patrickaupperle on 2008-03-14
Ok, I will delete this machine and wait for final.

---

### Post by ruibernardo on 2008-03-14
Good to see you got it working!

> **patrickaupperle said:**
> How much ram should I give during the vm install process? Is it changeable at a later time?

are updates ok?

The RAM depends on the guest OS requirements and the host available memory. It depends. Verify how much RAM the OS you're going to boot will need and give it to the guest. Virtualbox have a GUI to set the RAM of the guest. Check its options (it is explained in the [wiki page]("https://help.ubuntu.com/community/VirtualBox")):

[IMG]https://help.ubuntu.com/community/VirtualBox?action=AttachFile&do=get&target=04_Screenshot-Create_New_Virtual_Machine-2.png[/IMG]

About the upgrades, they are OK. As long you **only** use the Ubuntu repositories, you're safe. If you use other external  repositories, it's your responsibility.

> **patrickaupperle said:**
> I installed kubuntu kde 4 hardy on virtual box. I then did a full upgrade from adept. It downloaded some 200 packages and started installing then them. At a samba update it just stopped. What should I do?

That depends. As the guest is Kubuntu and the upgrade process broke, you should boot it (with a livecd if it doesn't boot) and try to fix the problem. You'll have to check the logs in /var/log/dmesg, /var/log/dpkg.log ond others (browse all the files in /var/log/ if needed) to see how much of the upgrade was accomplished, what's left to upgrade and why it stopped. 

I don't know the size of the disk you created to install Kubuntu, but probably (I'm guessing here) it wasn't enough and now the disk is full, so the upgrade process can't write changes. If that's the case, try to give a bigger size to the guest disk - for example Ubuntu uses 2.5 GB in the guest disk on install. To be able to upgrade it I must have free disk space in the guest. If the disk size is set to 4 or 5 GB, you'll have 1 or 2 GB of available space for the upgrade.

Again, because the previous paragraph was a guess, check the log files on the guest OS to know what happen.

---

### Post by patrickaupperle on 2008-03-14
Someone else said that It was broken and that I should just go back to 7.10. I will just wait for the final release. Thankyou for all of your help.

---

### Post by patrickaupperle on 2008-03-15
About my last few posts, the freezing ones, I fixed the problem. All I did was close the window, which messed everything up. After that I ran "sudo apt-get install amarok" and it told me that something was messed up and all I had to do to fix it was to run a command. I ran the command specified and everything works great.

---

