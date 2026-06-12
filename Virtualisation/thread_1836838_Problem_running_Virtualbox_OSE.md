---
title: "Problem running Virtualbox OSE"
date: 2011-08-31
forum: Virtualisation
---

### Post by Scottty on 2011-08-31
Ubuntu 11.04 is my Primary system

Well I installed Virtual OSE last night successfully with Windows XP on it.

I was able to run Windows XP and it bought up the XP desktop in a small screen

I decided to call it a night and I would install the VBoxAdditions to change the screensize the next day.

The next day I did the following to install VBoxAdditions
> 
sudo apt-get update
sudo apt-get install virtualbox-ose-guest-utils


Everything seemed to install well until.....

I tried to run the Virtualbox with XP and now I recieve the following message

Kernel driver not installed (rc=-1908)
Please install  virtualbox-ose -dkms package and execute
modprobe 'vboxdrv' as root.

Scott

---

### Post by Scottty on 2011-08-31
I uninstalled Virtualbpx OSE and rebooted.

I reinstalled Virtualbox OSE and it runs Windows XP again

There are no longer any error messages

Can you give me a suggestion on how to run VBoxAdditions.

The one issue I have with running Windows XP in virtualbox is the mouse doesn't move very well I'm hoping that VBoxAdditions will fix the issue

Scott

---

### Post by CharlesA on 2011-09-01
You install the guest additions from inside the VM from the machine menu IIRC.

---

### Post by Scottty on 2011-09-01
> You install the guest additions from inside the VM from the machine menu IIRC.

I can't find where IIRC is located.

I looked all over the VirtualBox OSE Manager
and the menu bar at the top of the screen which I believe is Unity.

Can you tell me where to find it?

Thanks
Scott

---

### Post by CharlesA on 2011-09-01
When you launch the VM, it'll have a menu bar inside the window and there should be one that says install guest additions.

---

### Post by Scottty on 2011-09-05
Hi 

I have installed and uninstalled several versions of virtualbox and none have had the install guest additions option

Right now I have gone into the Ubuntu Software Centre and located and installed  Oracle VM VirtualBox 4.1. I have also rebooted the computer.

I believe the desktop that I have installed is called Unity. When I try to launch Oracle VM Virtualbox I get the window where you have the choice to create a NEW vm or Change Settings,Start or Discard.

If I go to the very top of the screen where it says Oracle VM VirtualBox there are some choices they are

File --> Machine --> Help

and no where in that list is an option for installation of guest additions.

With this new install of Oracle VM VirtualBox I have not yet created a new VM. Do I have to have a new VM configured in order to display the option for installing the guest additions?

Please help

Scott

---

### Post by CharlesA on 2011-09-06
Start the VM, then go to the devices menu and select "install guest additions"

You need to have a VM created since the guest additions are installed on the guest, not the host.

---

### Post by Scottty on 2011-09-10
Thanks CharlesA

I used these two Tutorials 

1. [http://www.youtube.com/watch?v=F7w0JUHPiIw&NR=1](http://www.youtube.com/watch?v=F7w0JUHPiIw&NR=1)

2.[http://www.youtube.com/watch?v=WomzxDT3izw&feature=related](http://www.youtube.com/watch?v=WomzxDT3izw&feature=related)

Everything seems to be working

Wait till you try Seamless mode. "very cool"

Scott

---

### Post by CharlesA on 2011-09-10
Awesome. Glad you got it working. :)

---

