---
title: "Convert physical XP to virtual for Virtualbox"
date: 2009-03-25
forum: Virtualisation
---

### Post by virgil_machine on 2009-03-25
Background:  Machine#1 is triple boot (ubuntu 8.10 32-bit/windows--windows 7/xp), Machine#2 is Ubuntu 8.10 64-bit running virutalbox.

I have a windows 7 vm up and running under virtualbox on #2.

I want to get the physical XP machine (#1) running as a VM on #2 so I can free up #1 for other use.

I've tried to create a .vmdk from xp using VMWare converter.  The process failed ("Can't reconfigure a soure that does not have system volume").  

While I research that, I thought I'd see if anyone has had any luck with "VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
     -rawdisk /dev/sda" as described in the Vbox user manual section 9.10.

Theoretically, that will let me access the physical XP from Vbox on the same machine.  That would get me part way there--now, if I could migrate the resulting virtual machine #2 that would be the whole deal.  Or, if I could run the createrawvmdk on #2 and point to #1 that would be even better.  

Any thoughts?

---

### Post by BkkBonanza on 2009-03-26
They have an extensive sticky post on this topic in the virtualbox.org forums. See the Windows Guest section.

---

### Post by virgil_machine on 2009-03-26
Thank you. I am pursuing this on the virtualbox forum also.

The solution may be to clone the xp with acronis true image (because I have it, could be clonexzilla or something else) and go through some gyrations.

More here after I try.

---

### Post by virgil_machine on 2009-04-07
Here's an update for anyone who is interested.

On the VMWare forum, someone with exactly the same error I got isolated the problem as dual boot.  He fixed it by going back to a windows-only machine and converting that.  I'm not ready to do that.

I tried clonezilla, but it does not recognize the image it creates when I try to load it into a Vbox VM.  That problem nay be the dual boot setup, too.

I took another computer with only XP home on it, backed it uo with Acronis True image, booted the VM from the acronis cd, and restored the VM from the image.  I was able to start the VM, but it hangs on booting...which is a common problem.

Next, I created a new hardware profile on the XP Home machine, rebooted, and used device manager to disable all the devices I could (except the USB mouse and keyboard).  I'm cloning that, and we'll see how it works.

More to come.

---

### Post by virgil_machine on 2009-04-13
I can create a vm, but it doesn't boot. Hangs on loading Mup.sys.

Tried copying hal.dll and ntoskrnl.exe from an xp pro vm...only difference is now I get BSOD instead of hanging.

I'm still working on it.

---

### Post by virgil_machine on 2009-05-07
Just an update in case any one is interested.  

I've spent a lot of time on this over the past month.  I've learned a lot about vbox, windows, ubuntu, and a few other things, but I do not have a virtual machine.

I've copied files from a working VM, I've restored the registry files, renamed   a bunch of drivers, played with vm settings, etc.  I'm still hanging and/or BSODing at Mup.sys.

I've followed every tutorial and the guidance from helpful people on the vbox forum.  

I'm not giving up.

---

### Post by zenithdave on 2009-05-07
Thats the spirit :D

Having a look at the problem of mup.sys hanging on a native Windows system may give you some insight and i NO WAY mean this link as as SHALL I GOOGLE THAT FOR YOU. :P

[http://www.aitechsolutions.net/mupdotsysXPhang.html](http://www.aitechsolutions.net/mupdotsysXPhang.html)

Are you using the latest Virtualbox with USB support ?

Good luck

---

### Post by virgil_machine on 2009-05-07
Thanks. I've been researching the Mup.sys stuff.  I am in a  [long thread on the vbox forum]("http://forums.virtualbox.org/viewtopic.php?f=2&t=15834").

I think I'm down to "7.BIOS\ESCD\Motherboard chipset driver conflict with a component, its driver, or its registry data."

The physical machine is an Intel P4. The Server is an AMD Athlon X2. IDE on the physical, SATA on the server.  

My next step will be to go back to the physical, boot into a third hardware profile, go into device manager and delete everything, and rune MergeIDE (I've been through this already, but I'm trying to do everything I've learned in a proper sequence).  Then I'll clone the physical and restore it to the vm, then copy hal.dll, ntoskrl.exe, and ntkrnlpa.exe from a working vm, and copy registry files default, security, etc. from \windows\repair...and give it a go.

More results when I have them.

[I am using the release before 2.2.2, with USB support.]

---

### Post by djpandemonium on 2009-05-16
Did you ever get this working?

Just FYI:
Yesterday I used the VMWare converter to convert a Windows XP physical box to virtual for Virtualbox.  It worked perfectly, and booted on my first try.

I purchased a new computer and wanted to re-purpose my old box, yet still wanted access to my old files and programs.  My solution was to convert it to a VM and run it inside my new machine.  My old machine was an old, bogged-down P4 system, and XP had been seeing daily use for about two years.  It was also set to dual boot Ubuntu (though, I only wanted to image/access the Windows boot).  I used the VMWare tool, converted it to a VMWare Server 2.x image, and it booted right up.  I had read the wiki article [here]("http://www.virtualbox.org/wiki/Migrate_Windows"), though the only thing I had to was to enable the IO APIC option in the settings in Virtualbox.  It wouldn't boot at all until I had done that.  After that, Windows booted, informed me that there were significant hardware changes, forced me to re-register with Microsoft, and then booted up and worked flawlessly.

---

### Post by virgil_machine on 2009-05-16
Thank you for the update.

My first try was with VMWare converter.  What you did was what I expected would happen, but it failed.  See the first post in this thread: "I've tried to create a .vmdk from xp using VMWare converter. The process failed (Can't reconfigure a soure that does not have system volume)."

In the VMWare forum someone pointed out that the problem was dual boot(see post#4). 

Did you run converter on the dual boot configuration or did you revert to single boot XP first?

Also, you say the source is a P4 system--what processor on the new host?

---

### Post by djpandemonium on 2009-05-18
It was dual boot when I converted it.  Interestingly, I also had a second NTFS hard drive in the machine that I did not want to be part of the image.  I unselected it, and it gave me some warning about not being able to boot if I didn't select all attached drives.  I ignored it, and it worked fine anyway.

My new system is an AMD Phenom X3 720 BE.  It has all the optimizations for virtualization (AMD-V and PAE/NX).  The only settings I changed in Virtualbox were to enable those optimizations, IO APIC, and point Virtualbox at the VMWare image.

---

### Post by virgil_machine on 2009-05-18
Thanks.

I can convert my single boot machine, but I run into problems when I try to use it in Vbox.  The directions tell me that first I need to use vmware disk manager.  I've installed vmware 2.0.1both on windows and ubuntu, but I can't get it to do anything useful.

I have a bunch of 2GB segments, and vbox won't do anything with that's why I'm going back through vmware.

Did you have to do that?

---

### Post by djpandemonium on 2009-05-18
Nope, I didn't have to do any of that.

However, I told the converter not to split the target image into the smaller (2GB) segments.  I selected the option to have it create a single image file (37GB in my case).  I had it create the image on an external USB hard drive, which I then plugged into my new machine and copied to the internal hard drive.  I then created the VM in Vbox, pointed it at the image, and away I went.  Is it possible that Vbox doesn't like having the image split into 2GB chunks?

---

### Post by virgil_machine on 2009-05-18
Vbox definitely does not like that. I did not see an option to create a single file, and I looked. I'll try again. Meanwhile, I got VMWare-vdiskmanager to work. Now I'll see how Vbox likes that.

---

### Post by djpandemonium on 2009-05-18
When you are setting up the conversion, once you get to View/Edit Options then take a look under "Data to Copy" options.  I believe the option for splitting the target image is in there somewhere (though I don't currently have access to look at it.)

---

### Post by virgil_machine on 2009-05-18
I created a single filw with vmware-vdiskmanager, and was able to boot it in vbox.

Now I'm back where I started: hangs on Mup.sys.

I've experimented a little with vbox settings...no difference. I'll try some more.

Thanks for your help.

---

### Post by djpandemonium on 2009-05-18
I'm sure you have, but did you found this site in your googling?
[http://www.aitechsolutions.net/mupdotsysXPhang.html](http://www.aitechsolutions.net/mupdotsysXPhang.html)

It's a rather different scenario, so not everything applies, but it might have useful information.  Much of it has to do with hardware, and it sounds like you've been trying a lot of that.  In particular, have you tried using sysprep?  It's a Windows 2000/XP utility that prepares a windows install for being imaged.  I've never used it personally, but my understanding is that it removes a lot of machine-specific configuration and drivers so that the install can be imaged out to a number of machines without conflicts.  It comes on the XP CD and on MS's site, and you can find tutorials by googling.  Like I said, I haven't used it so I'm not completely sure if it applies, but it's worth a look.

---

### Post by virgil_machine on 2009-05-19
I've been there.

My understanding is that sysprep is for imaging new systems for multiple destinations.  I may be way off on that.  

Also, I do not have windows cds. The system I'm testing on is an XP Home machine that was given to me. I'm sure the windows is legal (the person I got it from wouldn't know how to pirate and she got it from Dell). I downloaded a cd from depositfiles.com, and when I tried a repair install it would not take the product code on the case.  I ran one a utility I found on the web and the code it comes up with different but also not accepted. I don't know if that's the cd or something else.

The XP Pro machine came as XP Home and I purchased an upgrade to Pro. Can't find the CD (7 years old and I've moved since then). I borrowed a CD, but it doesn't like the XP Home product code from the box.  I haven't tried the utility to get the code (can't remember the name--it's something silly)...I'll see if that works (just thought of that, I've been focused on other things).

That's a long way of saying that anything that gets me to entering product codes is a problem.  My systems are legal, but I have to get by this.

Thanks.

---

### Post by djpandemonium on 2009-05-19
That's probably the Magic Jellybean keyfinder.  I've used it, and it works:
[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)

Sysprep is for preparing an installation for imaging when the target image is destined for multiple systems of varied hardware.  As such, the idea is that it tries to make the installation as hardware independent as it can.  That link suggests to me that hanging on mup.sys is often due to hardware and/or driver issues, as most of the solutions they outline involves those things.  That's why I thought sysprep might be handy in this case.  I know I saw it suggested at least once elsewhere when I was doing my initial googling to see what trouble I would run into with this whole process.

But, as you can see, I'm just shooting in the dark because I'm out of other ideas.

---

### Post by virgil_machine on 2009-05-31
With guidance on the Virtualbox forum, I found a simple answer:
1. Make a copy of hal.dll in windows\system32 (so you can copy it back if you want to boot the machine again)
2. Find a hal.dll in an install directory (mine was in windows\cab\sp3) and copy it to windows\system32. 
3. Shutdown
4. Clone the system (I used Acronis True Image)
5. Restore the clone to a vm in virtualbox
6. Boot the vm and activate windows
7. You're done

I found a lot of dead ends before I found this.  Very simple and straightforward. I learned a lot in the process, but it sure did take a while.

---

### Post by stevenwscott on 2009-09-15
I have a serious suspicion that the issue w/mup.sys is due to residual vmware drivers, even after removing vmware tools.

---

### Post by virgil_machine on 2009-10-23
The problem occurs without VMWare in the picture. There may be issues there, but that's not this problem. 

I just tried VMWare as a way to create a .vmdk that I could use...because I got the mup.sys problem--before VMWare was even installed. I successfully converted by physical machine, but all I had was a VMWare image that I didn't care about.  

After the following the steps above, I have my physical XP machine running as a VM under Vbox.  I don't know why Vbox wants it to be such a pain to do.

---

