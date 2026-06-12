---
title: "Virtual Box HDD Duplication?"
date: 2010-03-27
forum: Virtualisation
---

### Post by Tamalin on 2010-03-27
I just recently installed Ubuntu 9.10 on an HP computer I have.  In order to use certain media features (i.e. Netflix, iTunes) I have to have Windows running in a virtual machine.  I chose WinXP, grabbed my ancient disk, and proceeded to install in VB.  Soon I got the familiar "activate in 30 days OR ELSE" message.  Unfortunately, I lost the product key and MS won't give me another this time.

Since I already have a working XP VirtualBox installation on a different computer running Ubuntu 8.04, can I simply copy the virtual machine over?  I was thinking maybe I could just copy the virtual HDD, and load it into the new VB, but I have never done this before and would like some suggestions as to how well this would work, and what I need to do.  Any suggestions are greatly appreciated!  Thanks

---

### Post by wilee-nilee on 2010-03-27
I think you will have to experiment with it. That being said I pulled the vdi files off my W7 running sun virtual box 3.1.6 of XP and Lucid and have them running on the same vbox version in Lucid. 

I think you can transfer them but, but I have no clue if the build version of vbox is going to make a difference.

I just put the vdi in home on lucid and loaded them in the initial build of the virtual HD. I suspect if a person wanted to do the same in MS it would work.

You can also scan for the key in the virtual xp you have running and save it in case a reinstall is allowed. ;)

---

### Post by Tamalin on 2010-03-27
> **wilee-nilee said:**
> You can also scan for the key in the virtual xp you have running and save it in case a reinstall is allowed. ;)

Are you joking, or could I actually find the key I used in my install?  MS can't be that generous...  That would be so convenient!

---

### Post by the yawner on 2010-03-27
> **Tamalin said:**
> Are you joking, or could I actually find the key I used in my install?  MS can't be that generous...  That would be so convenient!

If the Windows installation already has a product key activated it is possible with a utility program. Otherwise, no.

Regarding your question about copying Virtualbox HDDs, there is a command to do this:

```

VBoxManage clonehd "DiskToClone.vdi" "ClonedDisk.vdi"

```
DiskToClone.vdi - Source virtual disk. You can specify the complete location of the vdi file i.e. "/path/to/file/DiskToClone.vdi"
ClonedDisk.vdi - your copy that you can then transfer to your other workstation.

---

### Post by wilee-nilee on 2010-03-27
> **Tamalin said:**
> Are you joking, or could I actually find the key I used in my install?  MS can't be that generous...  That would be so convenient!

Keys are a easy find.
[http://magicaljellybean.com/keyfinder/](http://magicaljellybean.com/keyfinder/)

---

### Post by HermanAB on 2010-03-28
The nice thing about VMs is that you can back them up to DVDs for later use.  I create standard VMs pre-installed with whatever software  I need and then simply copy one as and when needed, thus avoiding the whole install and activate rigmarole.

In general, you just make a tar ball of the whole VM directory.  VMware.com even has a web site where you can download pre-configured VMs.

---

### Post by TheFu on 2010-03-29
Yes, moving a VM with Windows is possible. There are lots of howtos out there. I even wrote a very short summary on my blog. [http://jdpfu.com:82/2008/09/02/how-to-clone-a-virtualbox-domu](http://jdpfu.com:82/2008/09/02/how-to-clone-a-virtualbox-domu)
[B]
Overview of the steps:[/B]

VBoxManage clonevdi Master.vdi Clone.vdi
cp Master.vdi Clone.vdi 
VBoxManage internalcommands setvdiuuid Clone.vdi

I've done this to switch from Vista x64 as the host to Windows7 x32. Then, because I didn't change any directory/file locations, I've migrated from Win7-32 to Win7-64 by just copying the VDI and XML over.  I only used those vboxmanage utilities once to accomplish this. I think they are only necessary when cloning a HD that will run under the same VM physical host. 

Basically, you have a HD image file and an XML file describing the VM environment. If your setup is simple like mine, copy those two files to the new machine and edit the XML file to point to the new location of the VM img file. Be certain the vbox GUI doesn't show any differences in the hardware environment too. Also be certain you don't do any damage to the original files until you're certain the migration worked.

I can't guaranty any of this will work for you. I just know it did work for me.

---

### Post by Tamalin on 2010-03-29
> **the yawner said:**
> If the Windows installation already has a product key activated it is possible with a utility program. Otherwise, no.

Great!  I already have a working activation for it in another VM.  I see that apparently these activations keys are stored in the registry.  Does anyone have any idea where?

I would try [QUOTE=wilee-nilee]http://magicaljellybean.com/keyfinder/[/QUOTE], but I've never heard of this project before, and I'm just not sure how much I trust it yet.  This website, however, does contain some useful info.

---

