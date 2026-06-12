---
title: "VMware Server vs. VMware Workstation"
date: 2007-07-05
forum: The Cafe
---

### Post by FoolsGold_MKII on 2007-07-05
I've been using the Workstation version for a while now, but not... legitimately, shall we say. However, I hear that the Server version is free and has the same functionality.

Now I'd like to correct the error of my ways, but I just want to know from others, what are the primary differences between the two? Does Server still have the VMWare tools? Does it just require a bit more work to install? If the Server can be interchanged so easily, why do they still charge for the Workstation?

Ta.

---

### Post by Vajra Vrtti on 2007-07-05
The server allow you to create new virtual machines.

---

### Post by juxtaposed on 2007-07-05
> 
The server allow you to create new virtual machines.

So does workstation...

Anyway, from my experiences, there isn't any difference that I noticed, except server lets you connect to different computers to use their VMs or something like that. Just connect to your own computer and go about your normal activity :P

---

### Post by starcraft.man on 2007-07-05
> **FoolsGold_MKII said:**
> I've been using the Workstation version for a while now, but not... legitimately, shall we say. However, I hear that the Server version is free and has the same functionality.

Now I'd like to correct the error of my ways, but I just want to know from others, what are the primary differences between the two? Does Server still have the VMWare tools? Does it just require a bit more work to install? If the Server can be interchanged so easily, why do they still charge for the Workstation?

Ta.

Shame on you Mr. not legitimate :p.

Uh, I haven't looked at server in a while. I been using Workstation for ages. I'm not sure about the differences, do they have the snapshot system in server (doubtful)? I think also the networking of multiple VMs (i.e. in teams) and cloning is part of the workstation. Mostly its management tools I believe (vmware tools is still in server I believe). If I got it wrong please correct, I've been spoiled to much by owning workstation :p.

IMO, I recommend neither. I assume your running 32 bit Ubuntu and wanting to install 32 bit os and thus the best solution is [Virtual Box.]("http://www.virtualbox.org/"). It has shared folders, mouse integration (bundled with vbox tools), RDP, good networking interface, snapshots and bidirectional clipboard integration. It is also most importantly free (legitimately so :D). There is no 64 version yet, thats a major failing if you need that you have to use VMware.

Anyway, give that a try. Best way to install it is to add the repo to your sources list, its under the binary downloads (in downloads section).

Oh and in case your wondering, I use both now. My workstation is on my new 64 bit OS machine, and I left VBox on my old p4 for occasional use of XP.

---

### Post by Eggnog on 2007-07-05
I tried VMware server first, in order to boot into XP from time to time for a few Win apps I can't seem to live without.  Unfortunately I couldn't figure out how to network it or share folders between the VM and the PC drives and partitions.  It was easy to set up and use, though.

Then I tried Virtualbox and it works great.  I can easily share back and forth between my VB VM and the rest of my PC, and the VB tools are terrific.  It's easy to set up and easy to use.  But that's just my opinion.

---

### Post by jrusso2 on 2007-07-05
I think Workstation is the only version of vmware that has vmware tools.  But I think you can use the vmware tools from the workstation demo if you want to.

---

### Post by thisllub on 2007-07-05
Server has tools.

I will try virtual box but so VMware is the best I have tried.
Qemu is slow and Xen doesn't support a GUI with Nvidia.

---

### Post by Vajra Vrtti on 2007-07-05
> [QUOTE]The server allow you to create new virtual machines.
So does workstation...[/QUOTE]

Of course, stupid me. ](*,)

I read it as if it were the *player* instead of *workstation.* Sorry. I'm awake now.

A big difference I see in the [VMware site]("http://www.vmware.com/download/") is that **VMware Server** if free and **VMware Workstation** is not.

---

### Post by FoolsGold_MKII on 2007-07-05
Alright, I'll have a look at VirtualBox.

I've heard of it before, just didn't know if it was particularly fast or not.

I might as well try out VMware Server while I'm at it.

---

### Post by crush304 on 2007-07-05
you can install vmware-tools to the client from vmware-server, you can also take / restore snapshots. I think you can also connect to other machines running vmware but I haven't tried it.

---

### Post by rrinker on 2007-07-05
Yes, the VMWare Console can connect to multiple VM's running on the network. I've been using Workstation and Server for a while now. My laptop has XP as the host OS and using VMWare Workstation I have Fiesty running (just upgraded it from Breezy). I also made a backup of my old slow laptop and created another VM with XP to load that - so if I find something I forgot to copy off the old laptop I can just fire it up on the current laptop, and it actually runs faster since at the end the old lappy was failing and using only 256MB RAM, which is death for XP. CD drive was dead or I would have probably installed Ubuntu on that. The VM for it has 512MB so it runs faster in emulation than it did on the old native hardware.
 I've set up VMWare Server on my desktop running 7.04 as the host OS, but I haven't gotten around to installing  any actually VMs yet.

                                               --Randy

---

### Post by matthinckley on 2007-07-06
I use VirtualBox as I have clock speed issues in the quest OS with VMware.. although I can't figure out how to get bridged networking to work with VirtualBox and DHCP.. but anyways..other than that VBox works great for me

---

### Post by Frak on 2007-07-06
Workstation is much faster than Server, due to an acceleration module only found in Workstation.

---

### Post by afljafa on 2007-07-06
Server will run quite happily without X.

---

### Post by zgornel on 2007-07-06
> **Eggnog said:**
> I tried VMware server first, in order to boot into XP from time to time for a few Win apps I can't seem to live without.  Unfortunately I couldn't figure out how to network it or share folders between the VM and the PC drives and partitions.  It was easy to set up and use, though.

Then I tried Virtualbox and it works great.  I can easily share back and forth between my VB VM and the rest of my PC, and the VB tools are terrific.  It's easy to set up and easy to use.  But that's just my opinion.
I can confirm that VBox works great but with newer guests (Windows XP, new linux distros). Older ones like Windows 95/98/me do not work so well (crashes). It does not have the customization options of vmware but its almost free (free to use at least) and it is much faster. I use it rarely for some Office related stuff.

---

### Post by tribaal on 2007-07-06
To me, the real difference between workstation and server is the ESX compatibility Workstation gives to VMs it creates... So basically, if you don't plan to build VMs for ESX servers, you might as well stick with server, it does the job just fine :)

- trib'

---

### Post by kc5hwb on 2007-07-14
I am surprised to see several of you say that VB is better than VMware for the sake of shared folders.  I have been using VB for a few weeks now and one of my complaints is that I cannot seem to figure out how to get the shared folders to work (maybe I am doing something wrong)

We use VMware at my job and it shares folder quite easily.  I also like the fact that you can simply click into and our of VMware without having to hit the Right CTRL button as you do with VB to get it to release your mouse. (thats a minor problem, but one that I noticed right-off)

It also seems easier to enable sound, cdrom and usd devices with VMware.  There is a simple button at the top of the VMware screen on my PC at work that you can turn on and off while VMware is running.  In VB, you seem to have to shut down the virtual machine in order to go into the properties of that machine and turn on a cd drive or usb drive.

---

### Post by starcraft.man on 2007-07-14
First to start off... [URL="http://www.virtualbox.org/download/UserManual.pdf"]the user manual.
[/URL]
> **kc5hwb said:**
> I am surprised to see several of you say that VB is better than VMware for the sake of shared folders.  I have been using VB for a few weeks now and one of my complaints is that I cannot seem to figure out how to get the shared folders to work (maybe I am doing something wrong)


Section 4.4 on Folder Sharing:
> 
- In a Windows guest, use the following command (open the command line with "cmd.exe in the run box):
```
net use x: \\vboxsvr\sharename
```
While vboxsvr is a fixed name, replace &#8220;x:&#8220; with the drive letter that you
want to use for the share, and sharename with the share name specified with
VBoxManage.
- In a Linux guest, use the following command (in any terminal):
```
mount -t vboxsf [-o OPTIONS] sharename mountpoint
```
Replace sharename with the share name specified with VBoxManage, and
mountpoint with the path where you want the share to be mounted (e.g.
/mnt/share). The usual mount rules apply, that is, create this directory first if
it does not exist yet.


In both cases it's a standard shared drive, nothing special. This is just simply the command to mount them.

> We use VMware at my job and it shares folder quite easily.  I also like the fact that you can simply click into and our of VMware without having to hit the Right CTRL button as you do with VB to get it to release your mouse. (thats a minor problem, but one that I noticed right-off)

VBox has full mouse integration, install the VBox additions and your mouse will seemlessly move from the host to the VM without needing to click at all. The right + ctrl is simply the standard binding before you install the additions. If I'm not mistaken it's about the same for VMware, once you install additions you get full mouse integration.
> 
It also seems easier to enable sound, cdrom and usb devices with VMware.  There is a simple button at the top of the VMware screen on my PC at work that you can turn on and off while VMware is running.  In VB, you seem to have to shut down the virtual machine in order to go into the properties of that machine and turn on a cd drive or usb drive.

In case you hadn't noticed at the bottom right is a selection of all hardware you can enable (including cds, floppys, sound and USB...) They can be mounted on the fly if my memory serves.

Any other trouble?

---

### Post by kc5hwb on 2007-07-14
I saw the icons on the bottom to add sound and usb, yes... and I have used those, but they didn't seem to want to become active until I restarted the session.  I only tried once, I will look at that again.

Thanks for the info on the drive mounting and especially on the additions, I hadn't seen that yet.  I'll go look for it right now.

---

### Post by kc5hwb on 2007-07-14
I am not finding anything on the VB site called "additions"  :confused:

---

### Post by starcraft.man on 2007-07-14
> **kc5hwb said:**
> I am not finding anything on the VB site called "additions"  :confused:

Boot into your OS of choice. Then when your logged in, go to the menu at the top Devices Menu > Install Additions. Then it will mount as a CD, install it however you install things in the OS of choice.

---

### Post by 56seeker on 2007-07-15
On the difference between VMworkstation and VM server:

Generally; as you go up the family of VMware products, from workstation all the way up to ESX; you lose functionality but gain stability and performance.

In this concrete example; VM workstation allows multiple snapshots, more flexible networking, supports more hardware better (i.e. USB dongles, parralel ports etc) and supports more OS's. On the negative side it runs as an application, so it'll close if you log off the host machine and it needs a machine with a full GUI system to run.

Server, on the otherhand, doesn't need any GUI to run (so it'll run on a bare bones Ubuntu server), allows multiple logins via the client software, can isolate a particular virtual machine to a particular user or user group, runs as a backgroup app so you never have to actually touch the host machine, you can just log in to the server app via the client software and offers more performance than Workstation.

As to installation: I've found that the canonical repository includes VMware server; so once the repository has been added to your /etc/aptsources list it can be installed and maintaned with apt-get; but that repository doesn't include the VMware server managment interface, the so-called "MUI" (multi user interface). As far as I can see this still has to be downloaded from VMware and installed "by hand".

Would any one know if this is correct; that for some reason the MUI is not in Canonical's repository? And if so, why? And lastly, will it be included at a later date?

---

