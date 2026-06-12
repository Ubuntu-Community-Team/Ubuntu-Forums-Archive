---
title: "Installing virtualbox"
date: 2013-09-23
forum: Virtualisation
---

### Post by qwerty3656 on 2013-09-23
I have a ubuntu headless server (12.04) and want to run virtualbox.  It just seems like they go out of their way to make it difficult to get installed and up and running.  When I google how to install it, it is always like 10-steps and then you still don't have support for USB access or a GUI (neither of which are straight forward to get working - I'm referring to phpvirtualbox for the gui).  I've already blown up my server once trying to get virtualbox working - I'm sure it was some stupid error on my part, but I don't understand why I'm having so much trouble.  Now I've completely reinstalled ubuntu and as I'm trying to get virtualbox installed I feel this eerie deja vu occuring.

Isn't there a one stop process somewhere like do a,b, and c and virtualbox will be full installed, upto date, and fully functional?

---

### Post by sudodus on 2013-09-23
See these threads about KVM
[URL="http://ubuntuforums.org/showthread.php?t=2176189"]
[/URL][http://ubuntuforums.org/showthread.php?t=2174975](http://ubuntuforums.org/showthread.php?t=2174975)[URL="http://ubuntuforums.org/showthread.php?t=2176189"]
http://ubuntuforums.org/showthread.php?t=2176189[/URL]

---

### Post by JKyleOKC on 2013-09-23
Your best bet, since there's so much obsolete information around on the web, is to go directly to the official VirtualBox manual at [https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html) and read the very first chapter. It spells out exactly how to install the package, and what additional steps are necessary (and why they are extra) to get USB and RDP working.

Note that the "standard" VirtualBox user interface requires a GUI and all of the step-by-step instructions are written around that interface. However, the program CAN be installed and controlled from the command line, via its VboxManage utility that's fully described in Chapter 8 of the user manual. With a headless server as the host, you'll definitely need to use this approach, unless you install an X Windows server package on the host and ssh into it for a remote desktop -- which can be a serious security risk.

The on-line manual includes examples of the VBoxManage commands that can get you started. This approach, though, can be tedious for a beginner, and if it's possible I'd recommend that you install first on a desktop system rather than a headless server. Once you've become comfortable with VBox, the command-line approach will be much easier to master. Once you've created a VM and its associated virtual disk, you can copy it to other systems quite easily.

Using VBoxManage, it will take one command to create a VM, another to assign it memory, a few more to create a virtual disk for it and connect that disk to the VM, and so on. However, once that's done, you can access the VM remotely through VRDP (remote desktop protocol). I run my email program in a headless VBox VM here, and access it from any station on my LAN quite easily.

---

### Post by qwerty3656 on 2013-09-23
Thanks - any reason you didn't recommend to phpvirtualbox?  It appears to be a good "gui like" way to run virtualbox.

---

### Post by JKyleOKC on 2013-09-23
Simply that I've never used it so have no idea how well it works. Since it's php, that implies that I'd have to have Apache or something similar on my system, and I don't. Using the native GUI is simplest, but VBoxManage is ideal for creating scripts to automagically start and/or save VMs at power up or power down, or even to force a reset if a VM happens to freeze (which is a relatively frequent event for some of my older Windows VMs, after installing updates).

---

### Post by qwerty3656 on 2013-09-23
So now I've read the first chapter of the Virtualbox Manager and it is still seems to me to be this crazy process to get to the finish line (as opposed to installing webmin, or ssh, or apache, or filezilla, or Mobaxterm, or Plex, or any number of other things - which were all relatively straight forward).  I guess I'm just shocked with all the helpful blogs out there that there isn't an easy to follow step by step process that gets you Virtualbox, USB/RDP access, and a GUI/Web interface.  Its not that I don't want to do the work - I just don't want to screw it up (I've already screwed it up once).

---

### Post by Old_Grey_Wolf on 2013-09-23
@qwerty3656,

Oracle bought VirtualBox; so, if you don't like how it works you can contact them.

---

### Post by Kevin_Arnold on 2013-09-23
Pretty sure I installed it through the software center. I definitely didn't go through some long process.

---

### Post by qwerty3656 on 2013-09-23
> **Kevin_Arnold said:**
> Pretty sure I installed it through the software center. I definitely didn't go through some long process.

Are you running a headless server?  If so, do you have USB/RDP access and a GUI?  I realize I probably have no business installing a linux server.  I'm sure that anyone with an ounce of linux know-how can make this happen - but what I have found with virtualbox which I have not found with any other "package" is that there isn't a simple step by step process in one place that gets it installed.  The rest of my server was built on a "explain this to me like I'm a 5 year old" type process.  As I said above, I've installed and used webmin, ssh, somba, apache, filezilla, Mobaxterm, and Plex.

---

### Post by JKyleOKC on 2013-09-23
Have you read the page at [http://www.howtoforge.com/phpvirtualbox-running-virtual-machines-with-virtualbox-4.2-and-phpvirtualbox-on-a-headless-ubuntu-12.04-server](http://www.howtoforge.com/phpvirtualbox-running-virtual-machines-with-virtualbox-4.2-and-phpvirtualbox-on-a-headless-ubuntu-12.04-server) which provides step-by-step instructions for installing with phpvirtualbox?

I've not actually tried it, but have read through it carefully, and it all looks as if it should "just work" once you finish all of the steps. It does include the procedure for installing Apache, so if you already have Apache installed you can just skip over that step; the rest of it seems quite reasonable.

I also came across a line-by-line series of commands for creating a new VM entirely via the command line, using VBoxManage, but bookmarked that page on another machine that I'm not using at the moment. If you want that link let me know and I'll log in from the other machine and pass it on to you.

EDIT: Here's that set of commands:```
VBoxManage createvm --name "Ubuntu 12.04 Server" --register
VBoxManage modifyvm "Ubuntu 12.04 Server" --memory 512 --acpi on --boot1 dvd --nic1 bridged --bridgeadapter1 eth0
VBoxManage createhd --filename Ubuntu_12_04_Server.vdi --size 10000
VBoxManage storagectl "Ubuntu 12.04 Server" --name "IDE Controller" --add ide
VBoxManage storageattach "Ubuntu 12.04 Server" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium Ubuntu_12_04_Server.vdi
VBoxManage storageattach "Ubuntu 12.04 Server" --storagectl "IDE Controller" --port 1 --device 0 --type dvddrive --medium /home/ubuntu-12.04-server-amd64.iso
```You can change the names, of course, to whatever you like. --END EDIT

The reason for VBox being so much more complicated to install is that the USB2.0 and RDP modules are not open source, and because of that, require different license conditions. You *could* "just install" VBox itself (using phpvirtualbox or the apt-get commands from the prompt), but would not be able to use USB2 devices or the Remote Desktop capability, which would pretty much render it useless for most folk although the virtual machine's command line would still be available.

You might look at VMPlayer as a possible alternate program. I abandoned VMWare's products some six years ago (because of serious problems in maintaining their configurations) in favor of VBox, but earlier this year had to install VMPlayer on my wife's Win8 machine because VBox was having problems with its USB3.0 implementation, and it was much improved, although still not as smooth as VBox is on my Xubuntu hosts...

---

### Post by qwerty3656 on 2013-09-23
Thank you.

---

### Post by squakie on 2013-09-23
** removed **  What I posted here was wrong - don't want to confuse any other readers.  Sorry

---

### Post by JKyleOKC on 2013-09-24
> **squakie said:**
> I've never had a problem just going to Oracle's site, downloading Virtualbox (I forget what exactly they call it, but it's the "non-open" version, complete with USB support.  Install it, create 1 blank USB filter, and I'm set to go.  At least that has always worked for me.Just for the record, they changed things slightly when they went to Version 4. There's only one binary now for vbox itself, and it includes support for USB1 but not for USB2. There's also an "extension pack" that must be downloaded separately, and it includes the non-free modules that enable USB2, RDP, PAE, and possibly other unspecified goodies that enable the Guest Additions to work.

Installing that extension pack converts a basic vbox installation (once called the Open Source Edition or OSE) into what was formerly the Personal Use and Evaluation License or PUEL edition.

All this is spelled out in the first chapter of the on-line user manual that I linked earlier, but it's horribly confusing to newcomers and even to long-time users of vbox who haven't needed to study the manual carefully!

Now if they would just provide support for USB3 (which appears to be encumbered by patents) I wouldn't have to use any VMWare products...

---

### Post by Jonathan Precise on 2013-09-24
> **JKyleOKC said:**
> There's also an "extension pack" that must be downloaded separately, and it includes the non-free modules that enable USB2, RDP, ***PAE***...

Not exactly ***PAE***, as it comes included with virtualbox (you just need to activate it on the machine). However, you are right about USB-2, RDP, and others.

---

### Post by Jeevantha_Kule on 2013-09-24
never had a problem running VM on ubuntu..

---

### Post by squakie on 2013-09-25
** removed **  my previous post was wrong

---

### Post by Bucky Ball on 2013-09-25
*Thread moved to **Virtualisation**.*

---

### Post by JKyleOKC on 2013-09-25
> **qwerty3656 said:**
> Thank you.This thread got me interested in exploring VBoxManage in even more depth, and I've adapted that list of commands to create a new VM into a shell script, which I've tested here. It requires VBox version 4.x and will not work with older versions, but 4.1 is in the repositories. If anyone is interested I'll post it in this thread for reference. Basically, I converted all of the repeated strings to use temporary variables instead, so that names can be set in just one location, and added quite a few more options when setting the parameters for the new VM.

I hope you've got your server going by now!

---

### Post by sudodus on 2013-09-25
> **JKyleOKC said:**
> This thread got me interested in exploring VBoxManage in even more depth, and I've adapted that list of commands to create a new VM into a shell script, which I've tested here. It requires VBox version 4.x and will not work with older versions, but 4.1 is in the repositories. [COLOR=#006400]**If anyone is interested I'll post it in this thread for reference**.[/COLOR] Basically, I converted all of the repeated strings to use temporary variables instead, so that names can be set in just one location, and added quite a few more options when setting the parameters for the new VM.

I hope you've got your server going by now!
[B]
[COLOR=#006400]Yes, please :-)[/COLOR][/B]

---

### Post by JKyleOKC on 2013-09-25
Here it is:```
#!/bin/bash
#
# create virtual machine - jk - 24 Sep 2013
#	for use with VirtualBox 4.x; older
#	versions have different directory paths

# define names to be used; change these to suit your own needs
#	the VMdir will be created automatically, first time
#	a script runs. the ISOs directory is unique to me
#	and WinLite.iso is my slipstreamed WinXP file
VMdir="~/VirtualBox VMs"
VMname="scripted"
VDIname="$VMdir/$VMname/$VMname.vdi"
CtrlName="IDE_Controller"
CDname="$VMdir/ISOs/WinLite.iso" 

# create VM, set its parameters, and attach disk controller
#	use "vboxmanage list ostypes" at a command line to
#	get the list of types; there are many of them!
# this sets RAM to 512 MB and network to NAT
VBoxManage createvm --name "$VMname" --register
VBoxManage modifyvm "$VMname" \
  --memory 512 \
  --ostype WindowsXP \
  --acpi on \
  --boot1 dvd \
  --boot2 disk \
  --boot3 none \
  --boot4 none \
  --clipboard disabled \
  --nic1 nat \
  --usb on \
  --usbehci on
VBoxManage storagectl "$VMname" --name "$CtrlName" --add ide

# create and attach 10-GB virtual disk
VBoxManage createhd --filename "$VDIname" --size 10000
VBoxManage storageattach "$VMname" --storagectl "$CtrlName" --port 0 --device 0 \
 --type hdd --medium "$VDIname"

# attach CD/DVD
VBoxManage storageattach "$VMname" --storagectl "$CtrlName" --port 1 --device 0 \
 --type dvddrive --medium "$CDname"

# launch the new VM
VBoxManage startvm "$VMname"

```As written, it installs my slipstreamed WinXP into a 10-GB virtual drive. I've added comments to explain what each group of commands achieves, and to point out places where you need to customize it before running it.

Feedback and comments will be appreciated!

---

### Post by sudodus on 2013-09-26
[COLOR=#006400]**Thank you :-)**[/COLOR]

---

### Post by cF6RHpL on 2013-10-18
i find vmplayer or virt-manager to be much more robust then virtualbox... imho

---

### Post by KillerKelvUK on 2013-10-21
Have you considered using KVM instead of Virtualbox?  Or Xen? Or Proxmox?

I personally use KVM on a headless server, host & guest management is then either through cli using virsh or if you have a GUI desktop elsewhere to use which has network connectivity to the server you can use virt-manager as the admin application.

KVM installation is simple...

sudo apt-get install tasksel
sudo tasksel
"put a check next to 'Virtual Machine Host'" and hit okay.
Installation is then automated, reboot once done.

Depending on your requirements the networking setup can get a little more complicated but KVM out-of-the-box plugs in a basic setup for you.  Configuration using virsh is pretty heavy, lots of reading but for a simple requirement again the subset of commands you need to learn is significantly reduced.  Virt-manager on the other hand gives you a nice little gui which gives similar functionality to that of VirtualBox and removes all the hassle of having to learn virsh.

KVM is the virtualisation solution that Ubuntu directly supports, guides are all-over the net but check out this one...[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

