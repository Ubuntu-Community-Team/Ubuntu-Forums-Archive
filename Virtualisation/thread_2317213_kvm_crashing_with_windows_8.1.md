---
title: "kvm crashing with windows 8.1"
date: 2016-03-14
forum: Virtualisation
---

### Post by Jose_L on 2016-03-14
Hello all, 

I'm trying to setup a windows 8.1 VM on kvm and it keeps on crashing. I'm not sure if it's because I'm downloading the wrong drivers or just setting it up incorrectly. I'll post some screenshots of the errors that I'm getting. It gets stuck[ATTACH=CONFIG]267810[/ATTACH] at this screen and the following happens:

[ATTACH=CONFIG]267808[/ATTACH][ATTACH=CONFIG]267809[/ATTACH]

So the first error that I get is on the left, and then it goes away and then I get the second error whenever the vm tries to startup again. I have tried this with a windows 8.1 pro iso and a windows 8.1 enterprise iso. I have tried to virtualize windows xp on kvm and it worked correctly, so i believe that kvm itself is working correctly -- the problem probably lies with windows 8.1
I have also tried to use the windows virtio drivers, although I'm not sure which ones I should be downloading.

Here is where I get my windows images from:
[http://getintopc.com/?s=windows+8.1](http://getintopc.com/?s=windows+8.1)

and the virtio drivers: 
[https://launchpad.net/kvm-guest-drivers-windows/+download](https://launchpad.net/kvm-guest-drivers-windows/+download) (for ubuntu)
I have also tried the ones from fedora project here:
[https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download)

I'm new to kvm coming from using virtualbox so any help would really be appreciated!

---

### Post by KillerKelvUK on 2016-03-14
Hey, so good idea to post your virtual machine configuration when requesting a little support, that way we can tell if there is an error with that.  if you aren't sure on how to do this, open up a terminal (CTRL + T) and type 'virsh dumpxml *nameofyourwindowsvm*'.  Just copy/paste the resulting text into a response here and make sure you use the post editing tools to mark the text as CODE (the # symbol on the editing toolbar).

Things you might want to consider...
[LIST]
[*]Use OVMF for an EFI boot.  Basically your screenshots show you are using Seabios which is the standard/legacy bios installed with qemu.  This is fine but Windows 8.1 prefers a UEFI boot which you can only get from using OVMF...have you any experience with this or will you need a little more support should you get to trying this?
[*]Virtio...ditch the Ubuntu launchpad repo, its way out of date...you found the correct ones at the fedoraproject.org site so stick with these.
[*]Your Windows installation image/iso...the link you shared kinda looks well bad, if this isn't a legal source then there is a good chance you have a bad installation image with rootkits and all sorts of bother potentially involved.  Lets just say you won't get any support in locating a 'copy' of windows here, just a pointer on the legalities and the zero tolerance stance this forum will take on discussions about it (and rightly so).  All I can qualify is that I have legally purchased retail disk based copy of Windows 8.1 and it works with KVM absolutely fine, so if we rule out everything else then its a good chance your image is the source of the problems if it isn't reputable.
[/LIST]

---

### Post by MAFoElffen on 2016-03-15
Since I have Windows 8.0 through 10 desktop guests... Windows Server 2008 through 2016... I've experienced those errors...

Why the virtio drivers? You know that the [FONT=Ubuntu][COLOR=#333333]rtl8139 NIC type comes up fine for recent Windows guests. I do that NIC if I'm just putting up a quick guest.[/COLOR][/FONT]


[FONT=Ubuntu][COLOR=#333333]So your first pic is an error The second is not ... well sort of not. Explanation-- You seem to be deleting and reinstalling? You really do not need to. (Assumption). When you install and it goes to the first reboot, it ejects the virtual CD (ISO) from the VM. I get around that by mounting the iso to the CD and changing the boot order of the VM to the CD, then VM Disk.  [/COLOR][/FONT]

[FONT=Ubuntu][COLOR=#333333]On Win VM's I use IDE, SCSI or SAT as a disk controller. I use either BIOS. Those things are not the challenge...[/COLOR][/FONT]

[FONT=Ubuntu][COLOR=#333333]Next is the your first pic... which is probably the most common error when installing a recent version of Windows in KVM or Xen... what it is crashing on is the CPU type in the VM. Win 8.x on needs to have an xor flag in the CPU for 64bit. The challenge is which CPU. to use. My host cpu (2 x Core2Quad Penryn's) will run all those native. If I set VM host to my host type, it fails... but If I set the VM to a Core2 type (next highest CPU type below a copy of the host type) then it succeeds. Then I set the VM topology to 1 cpu, 2 cores, 2 threads. If you have a problem with booting, try another cpu type below that.  You can only use the same type of branding that the host has... and only equal to and below the capabilies that it has. Meaing an Intel cannot emulate an AMD.  and a i3 cannot emulate an i7.[/COLOR][/FONT]

[FONT=Ubuntu][COLOR=#333333]On using virtio drivers, I temporarily pre-install a second virtual CD player with the Virtio drivers iso mounted to it... That way, during the install, if using virtio divices, if it needs to find one of the virtio device driver files, it can find it and go on. [/COLOR][/FONT]

---

### Post by Jose_L on 2016-03-15
Hello, thank you for your reply.

I'm working on a project with a team and we decided to use windows 8.1 64-bit instead of the 32-bit. So I tried setting up a vm with the 64-bit and it worked just fine!

Thanks for your help though.

---

### Post by Jose_L on 2016-03-15
Hello, thank you for your reply.

I'm working on a project with a  team and we decided to use windows 8.1 64-bit instead of the 32-bit. So I  tried setting up a vm with the 64-bit and it worked just fine!

But if you have time, I will post the dumpxml that you recommended. Also, I downloaded the windows 8.1 enterprise trial version from the microsoft website, so now it should be pretty safe!

Here is the dump of the vm. 
[ATTACH]267821[/ATTACH]

Also, would you know how to create a snapshot of a live running vm in kvm? 
Thanks!

---

### Post by MAFoElffen on 2016-03-16
4 ways off the top of my head:

1. Turn on remote desktop (an RPDP)  the guest > Connect to RDP from another windows client > that a snip of the screen from the host you are connecting from.

2, If from a Linux remote client, install virt-manager. You can create, maintain and run your KVM guests from within it, with a GUI interface ... connected to your KVM server remotely. Look under screenshot under "View". Qemu Manager is the Windows Equivalent to virt-manager.

3. Connect with any other VNC or Spice client software. Some have screenshots, some you just get those from the client's host OS from where you are connected from.

4. Connect from Client to VM via an RDP. Logically, think of connecting to a VM guest, whether it has a native GUI desktop or text console... just as if it was another on-metal PC. 

Thing is, there is so many options in how you can do it, you just have to select one that you are comfortable with. I use a lot of different ones, but I do a lot of testing, so have varied requirements. But hard to beat virt-manager... For ease and simplicity.

---

