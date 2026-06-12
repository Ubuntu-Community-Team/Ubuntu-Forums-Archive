---
title: "After todays updates - Bang"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bardu on 2012-03-06
After downloading and installing todays updates I can't access Ubuntu anymore:

[B]null in the ring
Aborted. Press any key to exit.[/B]

Is showing on the screen after restart, but nothing happens if I press any key.

---

### Post by ventrical on 2012-03-06
sudo apt-get install lightdm
sudo apt-get install unity-greeter
sudo apt-get install ubuntu-desktop
sudo reboot

 err .. what type of video card do you have .?

---

### Post by matt_symes on 2012-03-06
Hi

Is this a problem with grub ? I take it you cannot boot into an older kernel ? Can you even get to the kernel selection screen.

Kind regards

---

### Post by bardu on 2012-03-06
no I can't

---

### Post by matt_symes on 2012-03-06
Hi

Try reinstalling grub from a LiveCD/USB (I would purge it and reinstall). You could post the grub config file.

Kind regards

---

### Post by paul_in_london on 2012-03-06
Not @ home right now, but I'm not seeing that error here in my VM after applying the latest updates and rebooting.

Are you able to boot previous kernels and/or boot into recovery mode?

If you can at least get into recovery mode, run fsck, check for further updates, apply any that may be available and then run:

```
update-grub
```

(as root).

HTH

EDIT: Apologies. I see from a previous post that you apparently can't even access the grub menu.

---

### Post by Elfy on 2012-03-06
Any idea if that was after thge grub updates I'm holding onto ?

---

### Post by paul_in_london on 2012-03-06
> **forestpiskie said:**
> Any idea if that was after thge grub updates I'm holding onto ?

I remember seeing some grub updates among the ones that I've already applied and all is still ok here in the VM at least.

---

### Post by Gregory Lee on 2012-03-06
There were some grub changes in the updates I applied an hour or so ago:
```
Setting up grub-common (1.99-16ubuntu1) ...
Installing new version of config file /etc/grub.d/00_header ...
Installing new version of config file /etc/grub.d/10_linux ...
Installing new version of config file /etc/grub.d/20_linux_xen ...
Installing new version of config file /etc/grub.d/30_os-prober ...
Installing new version of config file /etc/bash_completion.d/grub ...
Setting up grub2-common (1.99-16ubuntu1) ...
Setting up grub-pc-bin (1.99-16ubuntu1) ...
Setting up grub-pc (1.99-16ubuntu1) ...
Installation finished. No error reported.
Generating grub.cfg ...
```
I haven't seen a problem yet, but then I haven't rebooted, either.

---

### Post by bardu on 2012-03-06
> Try reinstalling grub from a LiveCD/USB (I would purge it and reinstall). You could post the grub config file.

Could someone please guide me through the proceedure?

---

### Post by wojox on 2012-03-06
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by matt_symes on 2012-03-06
> I haven't seen a problem yet, but then I haven't rebooted, either.

Ditto.

---

### Post by Skyflyer4life on 2012-03-06
I'm out.  New user to Kubuntu and had to set up new account just to post here.  Quite a funny saying really... "null in the ring" . Reminds me of lord of the rings... Lord Sauron has taken over my computer.  I was alpha 1 testing ubuntu for awhile... never expected this with Beta 1.  Went from Alpha 1, to Mint 12 Gnome, to openSUSE KDE and back to Kubuntu.  Very happy with it until today.  I just spent the last 5 days getting it set up exactly how I want it and now this!  Am I going to have to do a compete re-install?

---

### Post by matt_symes on 2012-03-06
? Duplicate ?

---

### Post by matt_symes on 2012-03-06
@Skyflyer4life

Check out wojox's post. That may give succor. If not then more digging is required.

---

### Post by Skyflyer4life on 2012-03-06
Wojox post does not look like a whole lot of fun.  Downloading boot-repair-disk.iso now but won't have a chance to play with it until tomorrow.  Hopefully by then there will be  a more detailed explanation of what happened.  Like my stupid Android phone, this pushes me away from ever running updates in the future.  If it ain't broke, why update it?

---

### Post by bardu on 2012-03-06
> HOWTO: Purge and Reinstall Grub 2 from the Live CD

Doesn't work for me, because of GUID Partition Table (GPT) .

Is there an instruction for that?

---

### Post by alphacrucis2 on 2012-03-06
Should I be holding off allowing the grub updates to install?

---

### Post by larrypg on 2012-03-06
Hello,

I did the updates a bit ago.  It will give you multiple options such as...go with the package version...see what the changes are..about 6 different options.  I chose the package maintainers version (the first one) and it gave me a warning sort of along the lines that future versions might have a problem because (I think) it was writen to the mbr.  I chose to install anyways and have had no problems.

---

### Post by ventrical on 2012-03-06
> **bardu said:**
> Could someone please guide me through the proceedure?

What are you using .. ie; USB .. CD .. what version of Ubuntu?

What type of PC? Is it on a network?



thanks

---

### Post by bardu on 2012-03-06
> What are you using .. ie; USB .. CD .. what version of Ubuntu?

What type of PC? Is it on a network?

A brand new HP  Pavillion HPE, with Ubuntu 12.04 Beta 1 as the only OS on it, CD and network.

But as I said earlier the provided instruction to rescue GRUB from LiveCD didn't work because of the GUID Partition Table (GPT).

---

### Post by bardu on 2012-03-06
These are the steps I have tried to rescue GRUB from LiveCD and the error message:

sudo parted /dev/sda print
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  20.0MB  20.0MB  fat16                 boot
 2      20.0MB  992GB   992GB   ext4
 3      992GB   1000GB  8572MB  linux-swap(v1)

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

---

### Post by myoldhouse on 2012-03-06
Does that HP HPE computer have a UEFI (Unified Extensible Firmware Interface) on top of a traditional BIOS (or maybe even replacing it)? If so, that could be a souce of problems vis a vis GRUB2. This link: [[COLOR="DarkOrchid"]https://help.ubuntu.com/community/UEFIBooting[/COLOR]]("https://help.ubuntu.com/community/UEFIBooting") contains a whole lot of information on the pains and pitfalls of installing Ubuntu, or any other linux distro, on a UEFI based system.

You might find something there that will help. Personally, I'm hanging on to my old hardware until this UEFI stuff and GRUB2 gets sorted out...

---

### Post by bardu on 2012-03-06
Thanks for the link, not sure about UEFI.

Have installed Ubuntu 12.04 Beta 1 three days ago and everything worked just fine, until installing todays update.

---

### Post by Gregory Lee on 2012-03-06
> **alphacrucis2 said:**
> Should I be holding off allowing the grub updates to install?
After the first reports of trouble, I checked the updates I had just done and found that there had been some Grub updates to my system.  But later, I saw more Grub updates, so it could be that some problem with Grub has been fixed.  I still have not rebooted and still have seen no problem.

I have no immediate plans to reboot.

---

### Post by Skyflyer4life on 2012-03-06
Awesome..this is so much fun!  I am running Kubuntu 12.04 on an Asus P8z68v-lx mobo with uefi bios.. My machine is dead in the water and I don't see a whole lot of resources for this issue on the net.  Everything was going great until update this afternoon.  I don't mind a re-install..but would like to know what happened so I can avoid this in the future.

Advanced noob here.. So easy instructions would be great.

---

### Post by Skyflyer4life on 2012-03-06
Of all the Ubuntu 12.04 beta 1 users there are only a couple people with this issue?  Just my luck! :-O

---

### Post by arpanaut on 2012-03-06
I have just this evening updated 4 different installs of 12.04 b1 on two different machines, Normal BIOS, both i386.
Rebooted into each multiple times, and am seeing no problems whatsoever.

Just wanted to chime in about this.  

Seems the OP's issue is probably due to GPT, 
Oldfred is pretty fluent with that stuff, hopefully he'll stop by and see this.

---

### Post by VinDSL on 2012-03-06
> **arpanaut said:**
> I have just this evening updated 4 different installs of 12.04 b1 on two different machines, Normal BIOS, both i386.
Did you do "Default" or "Smart" updates?!?!?

---

### Post by Skyflyer4life on 2012-03-06
To provide more info...running 64-bit Kubuntu 12.04 beta 1 on i5-2500k/Asus p8z68v-lx mobo with patriot torqx 64gb ssd.  It has uefi bios with no problems installing from usb pen drive a couple days ago.  Any help on fixing this would be much appreciated.

---

### Post by arpanaut on 2012-03-06
> **VinDSL said:**
> Did you do "Default" or "Smart" updates?!?!?

Through Synaptic, no issues, nothing held back.  
A hundred fifty some updates on each install, and that's since yesterday afternoon.
With that many packages getting uploaded, could just be bad timing for the affected users.

Chrooting into the installs and update/dist-upgrade might help.
Don't know, Just know that my 2 old DFI motherboards are running things just fine ATM.
Tomorrow, who knows, this is Beta testing Ya' Know!

---

### Post by Gregory Lee on 2012-03-06
> **bardu said:**
> A brand new HP  Pavillion HPE, with Ubuntu 12.04 Beta 1 as the only OS on it, CD and network.
I also have a new recent model HP Pavilion.  I don't *think* this is going to be helpful, but I did manage to get over some sort of incompatibility with the 12.04 Live CD by interrupting the HP boot sequence, and selecting, over the default UEFI boot from CD, the "legacy" atapi boot from CD.

---

### Post by VinDSL on 2012-03-06
> **arpanaut said:**
> Through Synaptic, no issues, nothing held back.[...]
Oh, okay, "Smart" update then...  ;)

I use Synaptic, too, and have it setup to ask me which update method to use, each time I click "Apply".

I noticed that the "Default" update was holding packages back, but not "Smart" update.

I updated, this morning (about 14 hours ago) with no probs, so I'll try another update in a few minutes.

You're probably right... bad timing (for those affected).  It's happened to all of us...

---

### Post by bardu on 2012-03-06
> I also have a new recent model HP Pavilion. I don't think this is going to be helpful, but I did manage to get over some sort of incompatibility with the 12.04 Live CD by interrupting the HP boot sequence, and selecting, over the default UEFI boot from CD, the "legacy" atapi boot from CD.

Booting from LiveCD actually isn't the issue. I can't rescue GRUB due to GPT partition.

---

### Post by alphacrucis2 on 2012-03-07
> **bardu said:**
> Booting from LiveCD actually isn't the issue. I can't rescue GRUB due to GPT partition.

Can you chroot into the install and just dist upgrade? That might repair the problem.

---

### Post by Skyflyer4life on 2012-03-07
[www.rodsbooks.com/gdisk/booting.html](www.rodsbooks.com/gdisk/booting.html)

this link might help.  I'm really new to linux  so this is all a bit foreign to me.  Never tried to chroot before but ill read up on it tomorrow and give it a shot.  thanks for the help.

---

### Post by bardu on 2012-03-07
How should I do that?

---

### Post by alphacrucis2 on 2012-03-07
> **bardu said:**
> How should I do that?

You boot into the Live CD I assume you have. Select try Ubuntu rather than install. You follow the same chroot scheme you would use for reinstalling grub2 but instead of doing that, do these commands from the chrooted shell 

```
apt-get update
apt-get dist-upgrade
```

If your problem occurred because you picked up a bad grub package that was subsequently superceded in the repos then doing the above might help. You need to have networking going in your chroot environment for apt-get to work.


Edit. See this guide by drs305



[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Edit. Not sure why you think GPT is a problem. This is normal for the last few years AFAIK.

---

### Post by VinDSL on 2012-03-07
> **VinDSL said:**
> I updated, this morning (about 14 hours ago) with no probs, so I'll try another update in a few minutes.
Alrighty, then...

Just did another update, and it restarted just fine.  ;)

---

### Post by alphacrucis2 on 2012-03-07
> **VinDSL said:**
> Alrighty, then...

Just did another update, and it restarted just fine.  ;)

I got brave too and let the new grub packages install. No problems on reboot.

---

### Post by ventrical on 2012-03-07
> **bardu said:**
> Booting from LiveCD actually isn't the issue. I can't rescue GRUB due to GPT partition.

  Perhaps you can try this method  and then send us a screenshot while in live CD. 


[http://ubuntuforums.org/showpost.php?p=11744119&postcount=3](http://ubuntuforums.org/showpost.php?p=11744119&postcount=3)

---

### Post by Elfy on 2012-03-07
> **forestpiskie said:**
> Any idea if that was after thge grub updates I'm holding onto ?

Sort of made it look like I was waiting to see - wasn't actually the case, I'd just not done it yet :)

As it was I had no issue then - nor with the further updates to grub later. 

Never let it be said I'm not brave enough to foolhardily battle onwards :p

---

### Post by VinDSL on 2012-03-07
> **forestpiskie said:**
> Never let it be said I'm not brave enough to foolhardily battle onwards :p
We've never accused you of being a coward, forestpiskie!  :D

---

### Post by VinDSL on 2012-03-07
> **arpanaut said:**
> Through Synaptic, no issues, nothing held back.  
A hundred fifty some updates on each install, and that's since yesterday afternoon.
With that many packages getting uploaded, could just be bad timing for the affected users.

Chrooting into the installs and update/dist-upgrade might help.
Don't know, Just know that my 2 old DFI motherboards are running things just fine ATM.
Tomorrow, who knows, this is Beta testing Ya' Know!

> **VinDSL said:**
> Oh, okay, "Smart" update then...  ;)

I use Synaptic, too, and have it setup to ask me which update method to use, each time I click "Apply".

I noticed that the "Default" update was holding packages back, but not "Smart" update.

I updated, this morning (about 14 hours ago) with no probs, so I'll try another update in a few minutes.

You're probably right... bad timing (for those affected).  It's happened to all of us...
You know, I was just thinking...

Usually, at some point in the discussion, someone brings up the possibility of "the dreaded partial update".

Could a partial update have taken place, unknowingly?!?!?

**Edit**

Sometimes a pic is worth 1000 words.

This is what I'm 'talking' about... "Default" vs "Smart" updates in Synaptic:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-mar-2012-1.png")[/INDENT]


What I do is look at the results of both methods, before applying updates.

In the most recent case, e.g. a few hours ago, if I had chosen "Default" update, Synaptic would have done a partial update.

"Smart" update, on the other hand, rolls the dice, takes a *best guess* and installs/updates everything. ;)

---

### Post by Quackers on 2012-03-07
It seems likely to me that this is a UEFI/Bios boot partition kind of problem due to the GPT partitioning and the grub updates.
When you installed 12-04 did you make any seperate arrangements for the installation of grub? I thought that was the norm in your circumstances. If so, it may be that the grub updates have interfered in some way.

---

### Post by Skyflyer4life on 2012-03-07
Still having an issue here... here is what I've tried so far.  I'm a total noob so bear with me on my post and formatting. 

Followed the instructions at 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

>Boot from LiveCD
>Click on "Try Kubuntu"
>Open Terminal
$sudo mkdir /mnt/temp
$sudo mount /dev/sda2 /mnt/temp
$for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
$sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
$sudo chroot /mnt/temp
$apt-get update
$apt-get dist-upgrade  
#Removed packages libasound2:i386 skype:i386  
#New: xbitmaps
#Upgraded: (too many to list)
$exit
$for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
#error message:device is busy
>shutdown
>remove USB
>Boot
NULL IN THE RING error

Second Attempt
>Boot from LiveCD
>Try Kubuntu
>Open Terminal
$sudo mkdir /mnt/temp
$sudo mount /dev/sda2 /mnt/temp
$for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
$sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
$sudo chroot /mnt/temp
$apt-get update
$apt-get purge grub-pc grub-common
#grub not installed and grub-pc not installed
#following to be removed grub-common, grub-efi, grub-efi-amd64, grub-efi,amd64-bin, grub2-common
$apt-get install grub-common
$update-grub
$apt-get install grub2-common
$update-grub
$exit
$for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
>reboot
NULL IN THE RING

Any thoughts on what I can try next?

---

### Post by Quackers on 2012-03-07
This line ```
#following to be removed grub-common, grub-efi, grub-efi-amd64, grub-efi,amd64-bin, grub2-common
``` would indicate that you don't have the normal grub files installed, but rather the grub files which enable a UEFI system to boot through grub.
Normally the files to be removed are just grub-common and grub-pc.

When grub tries to install during the 12-04 install procedure what messages or options do you get given? Would there be any referring to grub-EFI, or similar?

---

### Post by oldfred on 2012-03-07
I have not updated my 12.04 which is in a gpt flash drive with BIOS boot since Beta. Once installed I have not had any differences with gpt that I know of since 10.04.

May be best to post boot_info script from Boot-Repair. 

If your first partition is efi then you are booting in UEFI mode, otherwise it will be BIOS mode even if you have a new system with UEFI.

---

### Post by VinDSL on 2012-03-07
> **Quackers said:**
> This line [...] would indicate that you don't have the normal grub files installed, but rather the grub files which enable a UEFI system to boot through grub.
Maybe I'm missing something...

Based on the title of this thread, and the posts I've relegated to memory, it seems that Ubu 12.04 is installing correctly, but borks during subsequent updating.

Is this correct :confused:

---

### Post by Skyflyer4life on 2012-03-07
@Quackers
I did a normal install giving the entire drive to Ubuntu to automatically set it up.  No manual drive partitions.  I don't remember anything about grub or grub-options while setting it up.  It was wonderfully simple and easy to do if there were options for it I don't remember them.

I'll try playing around with Boot-Repair later on this afternoon and report back.

Thanks again for the help and it has been fun learning how to "chroot" :)

---

### Post by Quackers on 2012-03-07
It seems so Vin, yes. However the updates to grub could be over-writing or replacing grub-efi, or even losing the link to it. Maybe, perhaps :-)

---

### Post by Skyflyer4life on 2012-03-07
> **Quackers said:**
> It seems so Vin, yes. However the updates to grub could be over-writing or replacing grub-efi, or even losing the link to it. Maybe, perhaps :-)

Should I try again... this time after chroot into sda2  run the command

$apt-get grub-efi?

# and/or apt-get grub-efi-amd64  / apt-get grub-efi-amd64-bin ?

---

### Post by VinDSL on 2012-03-07
Oh, okay.  I just wanted to make sure I wasn't barking up the wrong tree.

I wonder which tool(s) are you guys using:

[LIST]
[*]Update Mangler
[*]Synaptic
[*]Aptitude
[*]apt-get
[*]etc
[/LIST].

---

### Post by Quackers on 2012-03-07
It may be worth a try to chroot in and purge grub again then run ```
apt-get install grub grub-common grub-efi grub-efi-amd64 grub2-common
``` and when all are installed run ```
update-grub
``` Then after umounting everything, try a reboot - and hope :-)

EDIT this is only my summation, no guarantees. I'm not certain that the grub-efi files will install in the correct place from a chroot. Largely guessing on my part. But as it won't boot anyway it's my best guess.

second edit Sorry, have removed the commas

---

### Post by Skyflyer4life on 2012-03-07
root@kubuntu:/# apt-get install grub grub-common grub-efi grub-efi-amd64 grub2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 grub : Conflicts: grub-efi-amd64
        Conflicts: grub-efi-amd64:i386
 grub-efi-amd64 : Conflicts: grub but 0.97-29ubuntu65 is to be installed
 grub2-common : Conflicts: grub (< 0.97-54) but 0.97-29ubuntu65 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Quackers on 2012-03-07
Hmm, try again without the grub entry at the start and see how that goes.
Also which live cd are you using?

---

### Post by Skyflyer4life on 2012-03-07
root@kubuntu:/# apt-get install grub-common grub-efi grub-efi-amd64 grub2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  sni-qt:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-efi-amd64-bin
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,776 kB of archives.
After this operation, 7,392 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

Well that seemed to work.  What about the suggested packages?  Are those needed?

root@kubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-18-generic
Found initrd image: /boot/initrd.img-3.2.0-18-generic
Found linux image: /boot/vmlinuz-3.2.0-17-generic
Found initrd image: /boot/initrd.img-3.2.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@kubuntu:/# 

Re-booting now... got my fingers crossed.

---

### Post by Quackers on 2012-03-07
Good luck :-)  I wouldn't worry about the suggested ones for the moment.

---

### Post by Skyflyer4life on 2012-03-07
null in the ring
Aborted. Press any key to exit. alloc magic is broken at 0xdf41bca0

Damn you Lord Sauron!!  I don't see why this shouldn't work.  I think I should try Boot-Repair next.

---

### Post by bardu on 2012-03-07
> You boot into the Live CD I assume you have. Select try Ubuntu rather than install. You follow the same chroot scheme you would use for reinstalling grub2 but instead of doing that, do these commands from the chrooted shell

Code:

apt-get update
apt-get dist-upgrade

If your problem occurred because you picked up a bad grub package that was subsequently superceded in the repos then doing the above might help. You need to have networking going in your chroot environment for apt-get to work.


Didn't help either. So I gave up and reinstalled from LiveCD, with Ubuntu the only OS on the box. After that used UpdateManager to install 336 available updates, including grub-pc and grub-common and this time everything went well.

Have no idea what went wrong yesterday.

---

### Post by Quackers on 2012-03-07
bardu, it looks like that may be the way to go then. Maybe the grub update damaged something first time round.
Thanks for the update.

Skyflier4life, in light of bardu's post can you backup anything you need and try a re-installation?

---

### Post by Skyflyer4life on 2012-03-07
> **Quackers said:**
> bardu, it looks like that may be the way to go then. Maybe the grub update damaged something first time round.
Thanks for the update.

Skyflier4life, in light of bardu's post can you backup anything you need and try a re-installation?

Sure but wanted to try that as last resort.  Lots of hours spent settting it up just perfect and I thought this would be the final time after 5 other experimental installs. (Ubuntu 10.04LTS, Zyntial, Ubuntu 11.10, Mint 12 Gnome, openSUSE KDE, Kubuntu 12.04 beta 1)  But I enjoy this stuff and don't mind.  Have two other computers lined up behind this  .. a server and an htpc... but those will have to wait. :)

---

### Post by Quackers on 2012-03-07
Ah, the life of a tester :-)

---

### Post by Skyflyer4life on 2012-03-07
Let the re-install commence.  Many Thanks for all the help!

---

### Post by Quackers on 2012-03-07
Sorry I couldn't help more, but never having used GPT or EFI before I'm not very knowledgable.
You could wait to see if there are further updates (or whether a bug has been reported) which you could get via chrooting.

---

### Post by ventrical on 2012-03-07
> **bardu said:**
> Didn't help either. So I gave up and reinstalled from LiveCD, with Ubuntu the only OS on the box. After that used UpdateManager to install 336 available updates, including grub-pc and grub-common and this time everything went well.

Have no idea what went wrong yesterday.

well at least there is some good news :)

---

### Post by ventrical on 2012-03-07
Found this at Ubuntu Brainstorm:

[http://brainstorm.ubuntu.com/idea/29307/](http://brainstorm.ubuntu.com/idea/29307/)

---

### Post by paul_in_london on 2012-03-07
> **ventrical said:**
> Found this at Ubuntu Brainstorm:

[http://brainstorm.ubuntu.com/idea/29307/](http://brainstorm.ubuntu.com/idea/29307/)

Hi ventrical. That's interesting. I don't imagine it'll be done for 12.04 though. Could mean fun and games with the new machine I'm thinking of getting. :lolflag:

---

### Post by ventrical on 2012-03-07
Honestly Paul.. for the past 4 months I have had 8 machines in front of me with Precise installs . I'm Ubuntupoopered :) and may soon  just focus on one (new) tower and 2 laptops.. but I got the beta-bug in my system  ya know  .. :) so it's going to be tough to parse down.

  Hope all goes well with your new machine.

---

### Post by paul_in_london on 2012-03-07
I had a different problem with yesterday's grub updates.

On this machine I have 3 partitions:

```
Install 1: /dev/sda1 oneiric (32 bit) ext4
Install 2: /dev/sda2 precise (64 bit) ext4
Install 3: /dev/sda3 precise (64 bit) btrfs
```

The controlling grub was initially on Install 3 (btrfs) - the most recent install.

Updated Install 2 - the controlling grub then became the one on Install 2.

This was a problem: the grub update on Install 2 didn't see the btrts partition (I think this is an os-prober issue) so I was tempporarily unable to boot Install 3.

I first tried to chroot from Install 2 (ext4) into Install 3 (btrfs) to run update-grub. Had some problems with that because I'm not very familiar with btrfs so I resorted to copying the original /boot/grub/grub.cfg from Install 3 to Install 2 and then I was able to boot Install 3 again and update that. This meant that the controlling grub was back on Install 3 and everything was ok again.

I wanted to find out how to get the chroot into the btrfs partition working properly though so after a bit of digging around this is what I did from Install 2:

```
sudo mount /dev/sda3 -o defaults,subvol=@ /mnt/lubuntu
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/lubuntu/$i; done
sudo cp /etc/resolv.conf /mnt/lubuntu/etc/resolv.conf # had to remove dangling symlink first
sudo chroot /mnt/lubuntu
```

I was then able to run update-grub successfully from the chroot and to run aptitude update/upgrade.

Finally I also realised that to make /mnt/lubuntu/home accessible I needed an additional mount command:

```
sudo mount /dev/sda3 -o defaults,subvol=@home /mnt/lubuntu/home
```

---

### Post by paul_in_london on 2012-03-07
> **ventrical said:**
> Honestly Paul.. for the past 4 months I have had 8 machines in front of me with Precise installs . I'm Ubuntupoopered :) and may soon  just focus on one (new) tower and 2 laptops.. but I got the beta-bug in my system  ya know  .. :) so it's going to be tough to parse down.

  Hope all goes well with your new machine.

You must have been busy! I've got two machines, but I mainly stick to one of them (I have 2 precise installs on that one). Haven't quite decided about getting a new one yet. Times are hard so I'm on a tight budget! Will try and post details tomorrow (it's a bit late here now).

Cheers,

Paul

---

