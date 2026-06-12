---
title: "Unable to mount shared folder with 12.10 guest on Win7 host with vmware player"
date: 2013-01-21
forum: Virtualisation
---

### Post by madHatterCutsTheChatter on 2013-01-21
Hey,

Hardware: Core i7, 16 gb, 500 gb hdd

I have a win7 host, ubuntu 12.10 guest. I installed guest additions.

On the host the share is at Desktop/vmShare

on the guest i cant see anything in /mnt (no hgfs)

I tried editing the fstab,

gksu gedit /etc/fstab
 
and added an entry

/host:{C:/Users/me/Desktop/vmShare} /mnt/hgfs vmgfs defaults, ttl=5,uid=1000,git=1000    0 0

but upon restarting it says that mount failed and i hav to skip it to load the guest OS

I cant find a way around this

---

### Post by meteorrock on 2013-01-22
I got a the new VMware workstation 9.0. It has options to install the vmware tools, you will need that package to get your file sharing up and going on from your host OS to your guest OS, which I assume is your ubuntu.

Download this code into your terminal if you do not have that vmware tools already.

```
sudo apt-get install open-vm-tools
```

And these tools along with the vmware tools you will need also for the modules.

```
sudo apt-get install open-vm-dkms
```
```
sudo apt-get install open-vm-toolbox
```

If you want an unlocked upgrade for that vmplayer check this link here. This is a working link where I got my vmplayer 9.0, its a good download and works as intended and described. It has more options to share files between the "host" OS and the "guest" OS. Vmware player is limited on filesharing in that way I think. [http://kat.ph/vmware-workstation-v9-0-0-812388-incl-keymaker-zwt-t6600847.html](http://kat.ph/vmware-workstation-v9-0-0-812388-incl-keymaker-zwt-t6600847.html)

~~~~~~~~~~~~~~~~~~~~```
:KS Don't forget development options up in XDA for their flagship device at this link here. [http://forum.xda-developers.com/forumdisplay.php?f=860](http://forum.xda-developers.com/forumdisplay.php?f=860)

---

### Post by madHatterCutsTheChatter on 2013-01-22
I undid the entry for fstab.

I ran the installer for vmwareTools again and it worked. 
It no longer got stuck trying to find the linux-kernel-headers. 

I looked around & this seemed to be the cause of vmware Tools not working properly.

The only change between now & previous was that i'd installed build-essential from the software center. 

I guess that must have done the trick.


i installed all the open-vm stuff like you suggested but the installer for vmware tools uninstalled them.

i had also installed kernel-headers manually but apt-get asked me to remove them. 

:guitar: :popcorn: :popcorn:

---

### Post by meteorrock on 2013-01-23
I am almost sure the free version of VMware player does not implement file sharing inbetween the host OS and the guest OS.

Its a feature only available in the paid Workstation 9.0 and up, even with vmware tools. Vmware tools does not work with the free 'player' version. There is the unlocked version in the link I gave above. {Followthrough for any lurkers in the thread.}

You have to set it up in the file sharing options on the workstation 9.0 itself in the options to file share, it sets it up with a onboard file sharing wizard, on the windows OS side. Provided you have vmware tools also installed through the CLI (command line interface) or terminal for your host OS. 

You should be able to drag and drop files straight from your host OS with the VMware workstation minimized in your Windows host OS tray. If not, try the workstation 9.0.

I tried the VMware player before I upgraded to that unlocked version I gave and could never get filesharing to work, as the options for it was not available in the menu itself for VMware. On mine its in the VM tab of the VMware itself for the options. VM tab >> settings >> options tab. Scroll down to the "shared folders." It should be marked "enabled." IF not click on it and another dialog box wizard will appear and set it up for you. Easy peasy. 

;) Take care.

---

### Post by madHatterCutsTheChatter on 2013-01-24
It wasn't available on the earlier versions of Player, but now they support copying using shared folders, (haven't tried drag-drop, will update accordingly). 

Copying was working with my earlier 9.02 guest on Win7 host, its just that when i created a new 12.10 guest things stopped working.

I would say now, the only 2 advantages of owning a workstation are snapshots and linux hosts, Virtualbox is nice too :popcorn:., though i haven't done a full comparison.

:guitar: :-({|=

---

### Post by meteorrock on 2013-01-25
Thats great :) I did not know that. Now others will be able to use that feature even on the free player version.

I tried Virtual box first, there was some sort of bug on the pulse audio that comes with virtual box, and I could not get audio to work on Ubuntu host OS with the Windows 7 OS guest. A google search showed its a kernel bug, the author of the pulse audio module had a blog asking Linus Torvalds himself if he could take care of it. Searching for a solution for that audio problem I found that blog online. Not sure if its fixed yet or not, the blog was dated in Dec 2012, IIRC.

):P

Glad to see you got your hypervisior up and going. I just found out about hypervisors a few months ago. No more dual boot and wait times. 

I find the VMware hypervisor is mostly smooth and fast. Once and a great while I will get a hang on it, even on a workstation. Just use the 3 finger salute < ctrl, alt, del, > if you have one, just open up that logout screen on your Windows OS host that way and kill that process on Windows task manager. There are about 3 or 4 tools that load up in the task manager you will have to kill to recover.

It only happened once or twice. The VMware seems to become more stable if you do not power off the hypervisor and just let it sit in the Windows OS tray, unless you have to restart the Windows OS side for the windows updates. I had my Ubuntu host OS sitting in the tray for a few weeks now, works good.

---

