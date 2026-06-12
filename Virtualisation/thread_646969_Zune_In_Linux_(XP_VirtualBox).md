---
title: "Zune In Linux (XP VirtualBox?)"
date: 2007-12-21
forum: Virtualisation
---

### Post by Ian505 on 2007-12-21
I have a second generation Zune that I really like. However, Microsoft- being microsoft- has not made a Linux version of their Zune and has made it very hard for hackers to unlock the ability to emulate it.

So I have a VirtualBox with a valid copy of Windows XP. (I'm connected. ;)) I have the Zune software installed- now I want to know how to forward the USB port with the Zune attached to the VirtualBox. I also would like to know how to share a folder between Linux and the VirtualBox. (I tried tinkering with both of these things, but I am very tired of tinkering on a friday.)

Many thanks!
-Ian

---

### Post by Seefizzle on 2007-12-24
This is something I'm trying to figure out as well. I'd rather not do it through a virtual box, because that would probably be a pain in the ***. Also, I'm not worried about running the zune software, just transferring my library to Ubuntu and listening to it. If you figure it out send me a PM and tell me how you did it.

---

### Post by bharadwaj on 2007-12-24
all you need to do is just plug your USB while working in you VBox.
File sharing can be done using SAMBA . These two links would really help you in doing that [https://help.ubuntu.com/community/SettingUpSamba#head-8e150e1996272f3eb37363c960274baed221513e](https://help.ubuntu.com/community/SettingUpSamba#head-8e150e1996272f3eb37363c960274baed221513e)
[http://www.samba.netfirms.com/addusers.htm](http://www.samba.netfirms.com/addusers.htm)



or just hang on for VMware to directly copy and paste any file between your host and guest OS like you normally do it in one OS environment.

---

### Post by Ian505 on 2007-12-27
Currently busy doing other things to tinker, but it looks like this will help thanks! (Will edit if I get around to actually trying this,)

---

### Post by Ian505 on 2008-01-14
Yea... I am not so busy any more and when I try working in the VM and connecting... Ubuntu rips me out of the VM and displays an empty "Music Player" window. (Pointless, as you can only access a Zune through windows because of the encrypted firmware.)

What's wrong?

---

### Post by ripperzane on 2008-02-04
I am attempting Virtual Box and am currently installing the dreaded Vista (dont ask). I am hoping to install it and get the zune player up on the vpc so i can get it workin. All in all, I simply want to get it syncing. Ho Hum...
Will update with progress.
RZ
*edit* Oh need to mention I am running it on  7.10/Ubuntu. x32. only sporting 1G Ram, so vista will run even more like a bloiatware snail than .. well that it already is...

---

### Post by brokencrystal on 2008-02-15
> **ripperzane said:**
> I am attempting Virtual Box and am currently installing the dreaded Vista (dont ask). I am hoping to install it and get the zune player up on the vpc so i can get it workin. All in all, I simply want to get it syncing. Ho Hum...
Will update with progress.
RZ
*edit* Oh need to mention I am running it on  7.10/Ubuntu. x32. only sporting 1G Ram, so vista will run even more like a bloiatware snail than .. well that it already is...

Any progress yet?  Please update either way...

---

### Post by Luinfana on 2008-02-17
You can do folder sharing between Ubuntu and your Windows VM really easily. You go to "settings" for your guest OS on the main VirtualBox screen, and go to "shared folders." Add the folder you want to share under "machine folders." Then boot Windows. Open Command Prompt. Enter the following:

net use x: \\vboxsvr\path

Where "x" is the drive letter you want your share to be assigned, and "path" is the path that you chose to share earlier.

You should see the text "the command completed successfully." Restart Windows, and your share should appear in My Computer as a network drive.

And as an extension of this, you can use your new share with the Zune software. So for instance if you shared your home folder, you can point the Zune software at X:/Music (assuming you chose the drive letter X), and if you add music to your normal Ubuntu music folder, it'll show up in your Zune library.

---

### Post by ripperzane on 2008-03-11
Regarding the previous post.
I attempted to install Vista Business in VirtualBox.
I succesfully installed Vista, but it kept locking on USB Sync.

I even tried putting it in USB 1.1 mode, and it kept locking up.

I have a XP Pro install, and while it syncs MUCH better, it is a bit twitchy, but I have found that a clean XP Pro install did the trick much better than a old VM XP Pro install I had.

All in all, it is doable, but I reverted to installing XP Home that came with a hand me down Dell that I am sadly using for the dedicated purpose of syncing my zune and it will likely be used for other things. (Dual boot with Ubuntu Studio or a 8.04 Alpha install test perhaps) We shall see.

:)
@ Luinfana: I setup the VBox addons, shared the folders, and after mapping the drives (mapping the "network shared") it kept saying it was unable to find the music. That was frustrating. So all be warned and plz lemme know if you figured an alternate method around it.

---

### Post by Luinfana on 2008-03-21
@Ripperzane:

I have to agree with you...I probably should have indicated that it doesn't work perfectly, and that syncing a Zune through VirtualBox is really a tightrope walk at best.

I use XP Pro in VBox, and if I do certain things in the software (try to drag-and-drop videos into the library from folders, for instance), not just the application, but the *entire virtual machine* crashes. I get a mostly-black screen with smears of colored pixels all over it; it looks horrifying. And if I haven't given up at that point, I have to do an ACPI shutdown and try again, and if I have given up, then I just shamefully boot into Vista (I'm on dual-boot), and do it the MSFT way.

Sorry for the false sense of security...

---

### Post by ripperzane on 2008-03-31
I heard some one say in an alternate install back before VB had fixed their USb issue that he synced via the wireless sync. Slower than USB, and not absolutely stable, but I wonder if this is a better option.

The final results for me are that I had a PC with enough space to dualboot XP Home and Xubuntu. In runs like a snail in XP, but I can sync it in XP (which I do like bi weekly) and then It sits as a kickaround xubuntu test PC. I keep my NAS mounted as a local drive (mapped drive rather) and I set all my media on it, which slows sync and playback, but has little to no impact of the local drive. That way the Zune software can (slowly) sync up the data and even playback over the network and I get to atleast keep it semi current.

I recommend try the VM route, see if you have better luck. After all, a portable VM (PC Independant) that is backed up is handy should your PC go down (Hardy Heron test gone awry for me :)  )

RZ

---

### Post by firedrow on 2008-04-01
For anyone trying to do syncing with a VM of Vista, you will probably hit a wall that isn't completely connected to VirtualBox.  Vista doesn't have a Zune sync program install last I knew, and those of us who use Vista (strictly for gaming I promise) have had to cobble together an XP program for Vista.  It's not perfect and is slow to transfer over USB2.0.  So if you're trying to use Vista on VirtualBox, you will probably hit problems with Vista's Zune program AND VirtualBox's USB mapping.

Now as of writing this I don't know if Microsoft has put out a Zune for Vista program, all I know is my program is a crippled XP version that will allow me to sync video and music.

---

### Post by aslamp on 2008-04-08
I got my user folder set up as the drive "L:", and told the Zune software to look to "L:\Music\" for music, but Zune won't recognize the music (.mp3). It gives me an error: c00d1197. I also tried setting "M:" to the Music folder itself, but it wouldn't even accept that as a folder.

However, when I copy the .mp3's over to a folder within the Windows installation, it plays fine. 

Is there anyway that I can enable the drive to be an actual drive, not a network drive? Or are there any other possible solutions?

EDIT: I also tried changing the registry path to My Documents to the drive, but that didn't work either. =/

EDIT: I tried running virtualbox as sudo, and gave unlimited permissions to everyone to the folder that contains music. Didn't work either =/

---

### Post by Etheral_Reality on 2008-04-14
I'm having the same problem too

---

### Post by Etheral_Reality on 2008-04-19
-bump-

---

### Post by aslamp on 2008-04-22
Try this: [http://www.dbstalk.com/showthread.php?t=75142](http://www.dbstalk.com/showthread.php?t=75142)

---

### Post by Etheral_Reality on 2008-04-27
nope..still doens't solve my problem...ugh any other ideas?

---

### Post by Belgorm on 2008-04-30
Hello my wonderful support team!

I can connect my Zune through Virtualbox and it appears under "My Computer" as Zune, i can browse through the directories but if i try to copy a folder from the zune to my desktop, i get a " Access is Denied" Error

Anyone else came across this and able to help me resolve?

Thanks peeps

---

### Post by nystud162 on 2008-05-26
> **aslamp said:**
> I got my user folder set up as the drive "L:", and told the Zune software to look to "L:\Music\" for music, but Zune won't recognize the music (.mp3). It gives me an error: c00d1197. I also tried setting "M:" to the Music folder itself, but it wouldn't even accept that as a folder.

However, when I copy the .mp3's over to a folder within the Windows installation, it plays fine. 

Is there anyway that I can enable the drive to be an actual drive, not a network drive? Or are there any other possible solutions?

EDIT: I also tried changing the registry path to My Documents to the drive, but that didn't work either. =/

EDIT: I tried running virtualbox as sudo, and gave unlimited permissions to everyone to the folder that contains music. Didn't work either =/

This might be caused due to the different file systems.  Maybe XP has a hard time recognizing your ext3 or ext2 partition in ubuntu shared over to your virtualbox.  I have the same problem and thats the only thing that I can think of.

Just a guess though.

---

### Post by ryokea on 2008-05-27
I just installed the binary version of VBox 1.6 and I can add a VBox share to the Zune program and it recognizes it straight away and starts adding the files to the library. I will test syncing once I get new media to add to my Zune.

---

### Post by darth_indy on 2008-05-27
> **Belgorm said:**
> Hello my wonderful support team!

I can connect my Zune through Virtualbox and it appears under "My Computer" as Zune, i can browse through the directories but if i try to copy a folder from the zune to my desktop, i get a " Access is Denied" Error

Anyone else came across this and able to help me resolve?

Thanks peeps

That's actually a Zune thing. Microsoft's crazy copyright protection - you're not allowed to move songs from the Zune to your computer. In other words, if all your music is on your Zune and you lose it on your computer, you're screwed unless you know a way to get it back (i.e. download [legally, for the sake of argument.]).

---

### Post by ryokea on 2008-05-28
Just a quick update, I had a no go on the sync from network drive deal. I have to transfer all the music I have to another hard drive vdi file attached to the VM then sync it all. So close to getting it working too :(

---

### Post by Etheral_Reality on 2008-05-28
ah that sucks, if you get it to work, let us know, =)

---

### Post by Luinfana on 2008-06-02
Looks like the latest release of the Zune software as of April 6 (version 2.5.447.0) is MUCH more stable with VirtualBox. I can now sync music without sluggish performance or crashes...pretty much flawless. Anyone else updated to 2.5?

---

### Post by darth_indy on 2008-06-02
@Luinfana - I have a quick question. Does it work with USB 2, or just 1.1?

I tried a while back with a XP VirtualBox, but it didn't work with my (1st Gen) Zune. I'll be sure to try again tonight! I had almost broken down and installed an XP dual boot simply for the Zune. This would be MUCH easier.

---

### Post by Etheral_Reality on 2008-06-02
i can't even get the zune to recognize my secondary hard drive, where my music an dpictures are stored

---

### Post by darth_indy on 2008-06-03
OK, so here's my problem. I've installed XP (Pro) in VirtualBox 1.6.0, and installed the Zune 2.5 software. it recognizes my Zune, I can delete songs, play songs, add songs to the collection, but NOT sync the songs. ANy ideas where I went wrong? It comes up with error code C00D11CD, which is a vague error code that means "We, the developers, have no idea what the hell is wrong either. So reboot. Yeah, that'll do the trick."

---

### Post by bertwagner on 2008-06-03
> **darth_indy said:**
> OK, so here's my problem. I've installed XP (Pro) in VirtualBox 1.6.0, and installed the Zune 2.5 software. it recognizes my Zune, I can delete songs, play songs, add songs to the collection, but NOT sync the songs. ANy ideas where I went wrong? It comes up with error code C00D11CD, which is a vague error code that means "We, the developers, have no idea what the hell is wrong either. So reboot. Yeah, that'll do the trick."


Are the songs you are trying to sync on the virtual hard disk with windows on it or somewhere else?

I experienced the same problem because I was trying to sync files that were being read off of my Ubuntu partition and Zune wouldn't allow it.  Once I copied some music to the virtual drive desktop and loaded them in the Zune software, I was able to sync.

---

### Post by darth_indy on 2008-06-03
Yeah, the songs are in Ubuntu. Darn, that's the one problem I hoped to avoid; I can't move all my files to the virtual drive - I have well over 30 gigs, and (a) I didn't want multiple copies of my music, and (b) I don't have enough space on my drive for a 30 gig virtual drive, if I could even make one (last time I tried to go over 10 gigs for a virtual drive it crashed and wouldn't work, and I had to reinstall the VM).

I just received my external HDD in the mail (to replaced the b0rked one - luckily it was under warranty). Maybe I'll try copying the files there and see if it'll sync from a USB drive. Wish me luck!

---

### Post by bertwagner on 2008-06-03
> **darth_indy said:**
> Yeah, the songs are in Ubuntu. Darn, that's the one problem I hoped to avoid; I can't move all my files to the virtual drive - I have well over 30 gigs, and (a) I didn't want multiple copies of my music, and (b) I don't have enough space on my drive for a 30 gig virtual drive, if I could even make one (last time I tried to go over 10 gigs for a virtual drive it crashed and wouldn't work, and I had to reinstall the VM).

I just received my external HDD in the mail (to replaced the b0rked one - luckily it was under warranty). Maybe I'll try copying the files there and see if it'll sync from a USB drive. Wish me luck!

Currently I have my Zune software scan my virtual xp desktop for new files to sync.  Whenever I want to add more files to my Zune I just copy them onto the desktop and they get synced.  Then I delete the folder off the desktop in order to save space.  It's not the most elegant method around but it stops me from having to have two music libraries.

And let me know if the external drive idea works, I am looking for a better way of getting around this.

---

### Post by darth_indy on 2008-06-03
I don't want to jinx it... but it's syncing from the external drive as I type. I already did a test sync of an album ot two to make sure it would work, and now it's doing the whole collection. Yay!

On a side note, I spent HOURS in Amarok and EasyTag getting the ID3 tags JUST as I wanted them... and the f$%@ing Zune software doesn't recognize them as valid. I have to do it all again. For all 5000+ songs (and counting). *sigh* I wish I had the free time.

---

### Post by darth_indy on 2008-06-04
OK, status update: I am currently listening to my favorite song on my Zune, courtesy of my VM's sync. Yes, it worked!

For anyone looking to sync their Zune, here's what I did. The guide below assumes you have Hardy Heron, you've copied your music to your external drive, and have a copy of XP and an internet connection. I don't know if it works with a Vista VM, or with Gutsy or older. Feel free to test if you're not too afraid of it getting a little b0rked, and let us know. :)

1) Fresh install of the latest Virtual Box (I hadn't reinstalled since I installed Hardy - I'm sure it would work if you did an update, or maybe even with an older VirtualBox) (PLEASE NOTE - This will not work with the Open Source Virtual Box, as it does not support USB)
2) Fresh install of XP Pro (May not be necessary to do a fresh install, I dunno) and run Windows Update. (you need to run Update for the Zune software to work)
3) Install Guest Additions
4) Fix USB:

In Terminal, type or paste:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Find the following text:

```
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
```

Uncomment the lines to look like this:

```
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

4) Download and install latest Zune software (2.5)
5) After any restarts, plug in external hard drive. It might not show up in the virtual box; you may have to mount it manually (in the VM window, go to Devices > USB > your drive, and make sure it's checked). 
6) Start Zune software
7) Under Settings, change the "My Music" folder to scan to the directory on your external drive. Do the same with videos, pictures, etc. if you want. If you don't want it to mess with your artwork/genres/etc. make sure to uncheck automatically filling in media info
8) Wait. Depending on the size of your collection, it might take a looooong time for it to recognize your music. 
9) Once it's done, plug in your Zune, and wait; it may take a while to recognize it.
10) Test sync an album to make sure it works
11) (recommended) Unless there's music on your Zune you don't have elsewhere, or you sync to multiple computers, I suggest wiping it (under Settings > Device) and doing a fresh sync; it will make sure you don't have duplicate songs, and other quirks.
12) Sync. I had about 5,000 songs to sync, and it took a long time; I started it around midnight, and it wasn't done when I woke up at 6:30, but your mileage may vary.
13) Rock on! :guitar:

Overall, it was slower than doing it straight in XP, but not by much, especially since my XP machine is sloooooow anyways.

Good luck, and if I didn't make it clear enough, please let me know!

---

### Post by Luinfana on 2008-07-13
@darth_indy:

Great job with the guide...looks good to me. 

To answer your question from a few posts back: only USB 1.1 appears to be working right now (terrible, I know) - and I assume that's why it took you 6.5+ hours to sync 5000 songs. Maybe someone can instruct me otherwise, but when I check the box "Enable USB EHCI controller" in Machine Settings (which enables USB 2), XP completely borks out when I try to connect the Zune. Just refuses to work entirely.

Recently I've been using the VM less and less for Zune syncing (usually I only use it for individual songs now and then). If I have several albums or videos and podcasts to sync, I just boot Vista. It's a shame this kind of workaround is still required in the first place - I'd really like to see some work done with USB traffic analysis to determine how the Zune and its software do the "handshake" (same principle the 6G iPods use - and that scheme was cracked soon after release). So why not for the Zune? As soon as someone figures out that byte sequence, we can all ditch our bulky VMs and use a little Python script with Amarok or any other Linux-native music manager. I suppose one can only wait and hope...

---

### Post by Luinfana on 2008-07-13
@darth_indy:

Ah, and one more thing - you'll be really happy about this.

A couple posts back you said that you're "screwed" if you lose your collection on your computer; you can't get it off the device.

Although this is the case with iPods, the exact opposite is true of Zunes. You CAN transfer any content you like back from the device at any time - through a process called "Reverse Syncing."

There's a tutorial [here]("http://zuneinsider.com/archive/2007/02/23/reverse-sync.aspx"), although it's outdated (the instructions are for the old software) the same principle applies with the new app.

To reverse sync, go to the Device tab in the software while your Zune is connected. Then just drag and drop anything you want to copy from it onto the little computer icon in the bottom left-hand corner - and that content will be copied to your hard drive. This even works on computers that aren't linked to the device at all - you could go to a friend's house, install the software, connect the zune as a guest, and copy content off. Songs go to My Music, videos to My Videos, and pictures to My Pictures (unless you've changed the default folders).

I've found that the progress indicator does NOT work well at all while reverse syncing - it may not move at all, or stay at 100% for a while - even though your files are being copied just fine. It should be done when it says Sync Complete, though. If you really want to check progress on large videos (movies, etc) you can repeatedly check the filesize of the video in Explorer while it's being copied, and compare that to the total size.

This works for anything on your Zune except DRM'd content from Zune Marketplace.

So, I hope that cheers you up - as it turns out Zune is a lot more lax about copying files than iPod is. Not many people have heard of reverse syncing, either. Microsoft should make a bigger deal about it; it's a great feature.

---

### Post by asmugone on 2008-07-20
Im doing a friends zune on ubuntu hardy heron, i installed virtualbox and fresh xp, sp3, installed zune got usb working, i even updated the firmware, BUT i cant get music onto the damn thing!!!! it fails and when i try and sync wma files it kicks them out as corrupted, i coppied everything onto my windows xp virtual drive and still no love, im ready to just throw this thing at the wall!!! someone please help.

---

### Post by EoRaptor013 on 2008-08-15
One more question: Why is everybody using VirtualBox when KVM is, supposedly, the approved/supported VM software for Ubuntu? Oh, and one more question, assuming I can figure out how to get a WinXP VM to even see the Zune, would configuration for KVM be similar to VirtualBox?
Thanks.
Randy

---

### Post by darth_indy on 2008-08-15
> **Luinfana said:**
> @darth_indy:

<snip>You CAN transfer any content you like back from the device at any time - through a process called "Reverse Syncing."<snip>

Thanks for the info. I honestly hadn't tried it before posting that - it was something I'd read in the Amazon reviews before I'd bought the thing. Guess that'll show me to believe Amazon reviews at face value, huh? :-)

And sorry for not replying earlier; I've had this thread as a subscribed thread, but for some reason it didn't say there were new posts until today. *shrugs*

@asmugone: I've had problems with music added to the virtual drive, as well. The only way I've gotten it to work is via an external USB drive.

---

### Post by ripperzane on 2008-09-04
Wow, you guys have been quite busy!
(**babbling**) It's been a while yet and I havent retried a Windows OS in a VM (virtual box is my pref.) to attempt to get Zune working. I have a laptop that only seems to run well in XP with the discs that came with it (truuuuuust me, I have tried 3 flavors of ubuntu, a OSX86 projext (not recommended) and even  Vista Home x64. The VIsta gave me the oh so not pleasant issue of not being able to get my sound working, as the driver is ONLY for x86 32 bit....)


ANY HOW: SO I am seeing you all got it ok on XP/Vista working with teh 2.5 Zune software? I stopped attempting even wireless sync due to Virtual NIC bridging issues.
Lemme know and good luck all.
RZ

---

### Post by darth_indy on 2008-09-04
> **ripperzane said:**
> ANY HOW: SO I am seeing you all got it ok on XP/Vista working with teh 2.5 Zune software? I stopped attempting even wireless sync due to Virtual NIC bridging issues.
Lemme know and good luck all.
RZ

I can confirm that my personal experience with the Zune 2.5 software and XP in VirtualBox, that at least the wired sync does work (I never tested wireless sync - I always had to charge it anyways, as I'm usually running it all day then charge/sync overnight.). Your mileage may vary, and I have no clue if it'll work with Vista or other VMs. I just know it works with the tools I have :) Good luck!

---

### Post by Dejavou42 on 2008-09-05
**If you have problems syncing your zune via usb, read this it may help!**

I had to disable the USB 2.0 on Ubuntu (ehci_hcd problems). I couldn't get my device to reverse sync using the usb method, and I even tried the windows registry hack on the VM + make the zune device stay in sync mode method. I couldn't get anything to work, and I thought I was screwed out of all of my media....until I found the trick to wireless sync.

Need: Virtual machine, wireless router / access point, and possibly enable the local network to your VM. 

 1. Turn Wireless on your Zune on ; Settings > Wireless > Wireless: On

 2. Set up wireless sync in zune software ; Settings > Device > Wireless Sync > Enable Wireless Sync & follow instructions.

 3. On zune device select Settings > Wireless > Sync Now

 4. On software once sync begins, select device and the media that you want to reverse sync (I.E. Music, Videos, etc.) Start dragging artist names, song names, etc. to the Computer collection icon in the lower left hand corner.

Your zune should wirelessly sync all files back to your computer.  Also, I noticed that it's easier to select several artists at one time and sync instead of one by one. 

Note* Zune Firmware Version: 2.5

Zune Software Version: 2.5.447.0

I think my problem was the disabled USB 2.0, but hopefully this will help some of you.

---

### Post by Super Jamie on 2008-09-13
hi guys

just so you know, you don't have to mess around copying files from physical to virtual machine to put them on your zune

follow the instructions here: [http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)
to get a vmdk file you can add to your virtual machine, which will give access to an actual physical drive

for example:

**sudo usermod -a -G disk superjamie**
(replace superjamie with your username, you only need to do this once)

i have a 500gb physical disk, formatted NTFS, which is /dev/sdb, and mounted at /media/500, so i go

**VBoxManage internalcommands createrawvmdk -filename /home/superjamie/.VirtualBox/500Gb.vmdk -rawdisk /dev/sdb -register**

This gives me a "500Gb.vmdk" file, which when loaded into a virtualbox windows virtual machine as a second drive, makes my 500Gb appear as E: in My Computer

(i still do the OS install on a virtual disk within a different vmdk image file)

i'm pretty sure virtualbox 2.0 (available as a deb package, and repo, from the sun virtualbox site) has proper USB2 proxy working as well, it's certainly very fast syncing over cable. now i just need to get wireless sync working...

zune 3.0 software is out in 4 days too!

---

### Post by darth_indy on 2008-09-13
Thanks, Super Jamie! I hadn't known about that fix. I'd been copying my songs to an external USB drive, since I didn't have nearly enough space to have 2 copies of my songs on my computer. But that seems like it'd be a lot easier, especially so you can sync without lugging the external drive around (which is a problem for me, as my main computer is a laptop and I do a lot of travelling).

Question: Would it be possible to mount just a directory as a folder that way? i.e. if my music folder is /home/user/music, could it be mounted as a vdmk?

One can hope that Zune 3.0 software works in VirtualBox too. Methinks I shall have to test for th sake of this thread...

---

### Post by ManMythLegend on 2008-09-15
i have been looking everywhere for a way to wirelessly sync Zune to a virtual Windows Machine but afaik there is no device to simulate a wireless connection in VirtualBox.

I've been looking at a lot of Wireless bridging posts here but it looks very involved and I'm not even sure if that would work properly...anyone know for sure? Tested and Working???

Thanks in advance!

---

### Post by ManMythLegend on 2008-09-16
Okay UbuZuners...anyone updated to 3.0 and got it working successfully?

I updated this morning and every time I start the program it freezes before doing anything.

I don't want to reinstall it because it takes BALLS long to re-sync all my files...and usually doesn't even do it successfully.

Any Answers?

---

### Post by hiyaegagagm1 on 2008-09-16
[size=2][font=Times New Roman][size=3]hi,everyone,need guitar effects pedals? take a look at [guitar effects pedals shop](http://www.myguitarpedals.com/), may be u will find ur favorite...This is an excellent thread!**The good:** The optional Bowers and Wilkins audio system in the 2009 Jaguar XF offers exceptional separation and clarity for music playback. We like the interior materials in the XF, along with the tech touches. The engine offers a good amount of power for the car while delivering acceptable fuel economy.[runescape gold](http://www.runescapecoin.net/) **The bad:** The touch-screen interface for audio, navigation, and other car systems is too slow, and it is not well organized. The navigation system is unremarkable.[age of conan gold](http://www.buy-age-of-conan-gold.com/)**The bottom line:** The 2009 Jaguar XF offers a lot of luxury for the money, with many unique high-tech touches and an exceptional audio system. But it doesn't always deliver on its apparent promise, [color=#008000][age of conan money](http://www.ageofconanmoney.net/) [/color]with a run-of-the-mill suspension and navigation system.[runescape money](http://www.runescapemoney.ws/). [/size][/font][/size]

---

### Post by parabolee on 2008-09-17
So I just updated my Zune software in Virtualbox 1.6.2 (non open source version).

The update to the Zune software went fine, I then connected my Zune and proceeded with the firmware update, it sat on the "please wait while your firmware is being updated this may take a few minutes" for about 10 minutes. At which point I became nervous I was corrupting my Zune, so I clicked CANCEL.

Once I disconnected my Zune I was all updated to 3.0, games were there but marketplace was not.

BUT when I connect to my computer I get an error that it can no longer connect to my Zune! Looks like I will have to reset my zune and reinstall and resync everything.

Got the same error when attempting to connect to a real Vista PC too!

So in summary - DO NOT INSTALL 3.0 FIRMWARE VIA VIRTUALBOX!

The Zune software seems to update just fine but the firmware update will (kinda) brick your Zune!

---

### Post by Luinfana on 2008-09-17
@parabolee

I updated my software in VirtualBox just fine, although I used my real Vista install to update the firmware, so I can't corroborate your problems. However I'm almost certain that the reason Marketplace isn't displayed is because you didn't link your Zune to a Zune Card (account). The Marketplace menu option won't appear unless you've linked your device and account.

I wouldn't reformat it just yet; try uninstalling and reinstalling the software on your Vista machine, then connecting it - it *should* work.

Post back with any updates...

---

### Post by parabolee on 2008-09-17
> **Luinfana said:**
> @parabolee

I updated my software in VirtualBox just fine, although I used my real Vista install to update the firmware, so I can't corroborate your problems. However I'm almost certain that the reason Marketplace isn't displayed is because you didn't link your Zune to a Zune Card (account). The Marketplace menu option won't appear unless you've linked your device and account.

I wouldn't reformat it just yet; try uninstalling and reinstalling the software on your Vista machine, then connecting it - it *should* work.

Post back with any updates...

Tried that, it didn't work. Got the same error message that said it could not connect to my Zune anymore.

You are right about the Marketplace. I cleared my Zune and updated the firmware via my real Vista PC and everything works fine again now, it was then I noticed that I had to approve use of the marketplace in the software. 

Not a big deal, re syncing my music is just a case of telling to sync and walking away for a few hours. No biggie.

Love the new firmware, shame we can't download audiobooks or podcasts via the marketplace though.

So for clarification for those that want to do this. I STRONGLY suggest updating your firmware via a real XP or Vista PC, it will do this fine even if you are just a guest on that PC.

---

### Post by Luinfana on 2008-09-21
@parabolee:

Would you mind taking a screenshot of this error, or the error code number (if you're still having the problem) and uploading it somewhere?

Just curious...

---

### Post by parabolee on 2008-09-21
Sorry mines working fine after i updated my fw with a vista pc.

---

### Post by Super Jamie on 2008-10-03
I'm using XP in VirtualBox 2.0.2, and with Zune 3.0 I can get wireless sync working fine.

The Zune 3.0 install worked fine, I removed zSuite and Zune 2.5 with Add/Remove Programs before installing Zune 3. Firmware upgrade also went thru first time without a hitch.

---

### Post by Luinfana on 2008-10-08
@Super Jamie:

VBox 2 is good stuff, amirite? Shiny new Qt interface, and looks like Sun took over the project...no more Innotek.

Unfortunately, I messed up my installation...the Zune software no longer works. I used [XPLite]("http://en.wikipedia.org/wiki/Xplite") to remove some Windows components (to save some much-needed space), and subsequently the Zune software throws an error whenever I try to start it. Something must have been required - I could go back piece-by-piece and figure out what it was, but I think I'll just be using my Vista install for the moment.

Moral of the story: it's probably a bad idea to try to trim down your XP install if you want to keep using your Zune with it.

Also, if you're interested in further progress with Zune+Linux compatibility and device hacking in general, we've got a thread going over at the [Rockbox Forums]("http://forums.rockbox.org/index.php?PHPSESSID=55e8f775bb7d60f6bfe015381255dc85&topic=6848.0"). A lot of it is old news, but we're starting to discuss some new ideas. Gotta start replaying those USB captures...

---

### Post by darth_indy on 2008-10-08
Have you tried reinstalling the Zune software? It would probably reinstall all dependencies since it checks MS Update when it installs. I don't know from experience, but it might be worth a shot. Apologies if you already tried it.

---

### Post by Luinfana on 2008-10-13
@darth_indy:

Yup, already tried that. No dice. :(

---

### Post by Super Jamie on 2008-11-23
VirtualBox 2 is pretty good, it has advantages and disadvantages over VMWare, though I'd rather see it built on GTK.

And yeah, Sun bought Innotek in February. It was on Slashdot :)

---

### Post by kiselblat on 2009-10-12
I'm running Ubuntu 9.04 64-bit, with VirtualBox 3.0.8 running WinXP with Zune 4 software.
The machine and the software run fine, but getting the machine to see the Zune is fussy at best.  They do eventually talk to one another, but what I sync the device it takes an achingly long time.
When I looked in /etc/init.d/mountdevsubfs.sh it didn't include the quoted code, should I add it?
Are there any other tricks, or am I trying to make the impossible happen?

---

### Post by Axess_Denied on 2009-12-11
> **Super Jamie said:**
> I'm using XP in VirtualBox 2.0.2, and with Zune 3.0 I can get wireless sync working fine.

The Zune 3.0 install worked fine, I removed zSuite and Zune 2.5 with Add/Remove Programs before installing Zune 3. Firmware upgrade also went thru first time without a hitch.

Super Jamie is your setup on a desktop or notebook? I setup the wireless connection through VB and the Zune software w/o a hitch. The Zune connects to the network but not the PC (desktop) any suggestions?

---

