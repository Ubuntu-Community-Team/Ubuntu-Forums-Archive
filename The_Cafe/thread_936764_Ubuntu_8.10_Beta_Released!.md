---
title: "Ubuntu 8.10 Beta Released!"
date: 2008-10-03
forum: The Cafe
---

### Post by Jim! on 2008-10-03
[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

I'm going to install the Beta tonight since I'm on holidays at the moment and don't really need a stable machine:) The only problem is that it will probably take the entire night since I'm over my download limit:( Still, I'm excited that the latest release will be out on October 30th. Looking forward to it. 

Is anyone else here planning on giving the Beta release a try? Or even already installed the Beta?

---

### Post by billgoldberg on 2008-10-03
> **Jim! said:**
> [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

I'm going to install the Beta tonight since I'm on holidays at the moment and don't really need a stable machine:) The only problem is that it will probably take the entire night since I'm over my download limit:( Still, I'm excited that the latest release will be out on October 30th. Looking forward to it. 

Is anyone else here planning on giving the Beta release a try? Or even already installed the Beta?

I might download it to give it a try.

Some questions before doing so:

Is that intel driver bug already fixed (or blacklisted or something)?

Is it already gnome 2.24 or still 2.23.xx?

Does it come with Empathy instead of pidgin?

Is flash 10 available?

Are their already medibuntu repo's (or equivalent) available, or do the hardy repo's work?

And is the boot up time improved as promised?

Has PulseAudio improved compared to Hardy?

Are the new Ati Drivers working properly (better than hardy ones)?

Is the beta stable or are there still lots of issues with it?

---

### Post by Jim! on 2008-10-03
No Idea! I haven't been able to download/install it yet. I'm on a shared wireless connection and I'm over my bandwidth limit so I'm browsing at around 8-10kb/s:D I know that it's using the latest kernel which supposedly has much better hardware support then the previous one. If you plan on giving it a try I recommend you take a look at the known issues first.

---

### Post by billgoldberg on 2008-10-03
> **Jim! said:**
> No Idea! I haven't been able to download/install it yet. I'm on a shared wireless connection and I'm over my bandwidth limit so I'm browsing at around 8-10kb/s:D I know that it's using the latest kernel which supposedly has much better hardware support then the previous one. If you plan on giving it a try I recommend you take a look at the known issues first.

I feel your pain on the download limits.

Still have them here too.

---

### Post by Iceni on 2008-10-03
Is that intel driver bug already fixed (or blacklisted or something)?
- I noticed a fix for it in one of the update batches a few days ago

Is it already gnome 2.24 or still 2.23.xx?
- Been 2.24 for some days

Does it come with Empathy instead of pidgin?
- Mine has pidgin

Is flash 10 available?
- Aye flash 10 is with me

Are their already medibuntu repo's (or equivalent) available, or do the hardy repo's work?
- Don't know. I can play music and movies:)

And is the boot up time improved as promised?
- Haven't measured but it feels quite quick.

Has PulseAudio improved compared to Hardy?
- IT WORKS FINALLY!

Are the new Ati Drivers working properly (better than hardy ones)?
- This I don't know

Is the beta stable or are there still lots of issues with it?
- Been stable for me since alpha 2, except the usual fstab stuff.

---

### Post by Sealbhach on 2008-10-03
Can anyone confirm if the e1000e bug been fixed? That's a serious one that can fry your hardware.

.

---

### Post by Jim! on 2008-10-03
> **Sealbhach said:**
> Can anyone confirm if the e1000e bug been fixed? That's a serious one that can fry your hardware.

.

The Beta has only just been released It will probably be sometime before it's fixed. > A problem that could result in corruption of the firmware on Intel GigE ethernet hardware has led to the disabling of the e1000e driver in the Linux kernel included in Ubuntu 8.10 Beta. Since the issue hasn't been resolved they've just disabled the driver. So your hardware isn't in any immediate danger.:D

---

### Post by kernelhaxor on 2008-10-03
I jus upgraded  .. I had Ubuntu 8.04 with KDE installed too.. 
After the upgrade ended successfully, the system restarted and it didn't boot properly .. the motherboard gave a few beeps while my monitor was blank ..
After I power cycled the machine, it booted fine until almost login screen when it shows some KDE error .. then it gave a command prompt login .. so now I can only use the command prompt until I fix the issue ..

I will look into the error again and report a bug and post details here

EDIT: I have a nVidia 8400GS card .. and looks like the drivers hav issues .. I switched to generic configuration but still not able to get X up

---

### Post by eragon100 on 2008-10-03
> **Iceni said:**
> 


Has PulseAudio improved compared to Hardy?
- IT WORKS FINALLY!



Really?? It is stable now, no more sound system chrashes which force you to restart your pc to get sound again? You can use internet radio in the background while playing a game and have sound in both? Surround sound works by default??

I will even install a beta release for those improvements, if this is the case :) :popcorn: :guitar:

---

### Post by eragon100 on 2008-10-03
> **kernelhaxor said:**
> I jus upgraded  .. I had Ubuntu 8.04 with KDE installed too.. 
After the upgrade ended successfully, the system restarted and it didn't boot properly .. the motherboard gave a few beeps while my monitor was blank ..
After I power cycled the machine, it booted fine until almost login screen when it shows some KDE error .. then it gave a command prompt login .. so now I can only use the command prompt until I fix the issue ..

I will look into the error again and report a bug and post details here

EDIT: I have a nVidia 8400GS card .. and looks like the drivers hav issues .. I switched to generic configuration but still not able to get X up

Maybe that´s because x.org doesn´t include a xorg.conf file anymore by default, the Nvidia drivers need one to run.

---

### Post by Iceni on 2008-10-03
> **eragon100 said:**
> Really?? It is stable now, no more sound system chrashes which force you to restart your pc to get sound again? You can use internet radio in the background while playing a game and have sound in both? Surround sound works by default??

I will even install a beta release for those improvements, if this is the case :) :popcorn: :guitar:

I would not know about surround, sorry. However games and music from vlc works fine. I'll check with internet radio:)

EDIT: Last.fm + totem / wine game works for me.

---

### Post by Sef on 2008-10-03
I've been running Ibex since Alpha 4.

---

### Post by Sealbhach on 2008-10-03
> **kernelhaxor said:**
> 

EDIT: I have a nVidia 8400GS card .. and looks like the drivers hav issues .. I switched to generic configuration but still not able to get X up

Maybe you could try this:

```
nvidia-xconfig
```


.

---

### Post by Ms_Angel_D on 2008-10-03
> **Iceni said:**
> 
Has PulseAudio improved compared to Hardy?
- IT WORKS FINALLY!

I'm soo hoping that will fix my microphone issues, it seems to be a known bug with my audio, all I get is static when attempting to use the mic. It's very annoying.

---

### Post by jimi_hendrix on 2008-10-03
is there a security/bug possibility that will kill my machine?

---

### Post by Jim! on 2008-10-03
> **jimi_hendrix said:**
> is there a security/bug possibility that will kill my machine?

Kill your machine? No. Stop your system from running properly? Yes, that's why this is a beta release there are still bugs that need addressing (There always are). Although It's very likely to work quite nicely at this stage:D If your keen then you should give it a shot you'll probably learn a thing or two, just remember to backup any important data first!

I'm about to begin the upgrade! (It will probably take a few hours on my connection though:( )

EDIT: Greeeeat! "Fetching file 32 of 47 at 8019B/s" Yes you read that correctly 8019**B/s**. :'(

---

### Post by Sealbhach on 2008-10-03
> **Jim! said:**
> !

I'm about to begin the upgrade! (It will probably take a few hours on my connection though:( )



Isn't it better to do a clean upgrade from a CD?


.

---

### Post by billgoldberg on 2008-10-03
> **Sealbhach said:**
> Isn't it better to do a clean upgrade from a CD?


.

Yes.

--

I'm moving over data to my external hard drive now and will install the beta.

---

### Post by gorzka on 2008-10-03
When I start the Beta, the system freeze when GDM is starting. I have a NVIDIA FX 5200.

Have anyone a idea? What can I do?

---

### Post by Sef on 2008-10-03
> is there a security/bug possibility that will kill my machine?


Yes, if you have an [Intel e1000e Gigabyte Cards]("http://ubuntuforums.org/showthread.php?t=927943").

---

### Post by dracvs on 2008-10-03
Downloading Via BitTorrent

Instalilng in a virtual machine, then downloading the 64 bit version and installing at home

I wonder if my ATI Card will keep me from using it with houdini in IBEX

---

### Post by aaaantoine on 2008-10-03
I'll wait for the final release, wait a few days while the early adopters jump on the release and overload the server, and then try running my first dist-upgrade.

---

### Post by Ms_Angel_D on 2008-10-03
> **aaaantoine said:**
> I'll wait for the final release, wait a few days while the early adopters jump on the release and overload the server, and then try running my first dist-upgrade.

Yeah I'm waiting a bit too, I don't feel like taking it on right now. My system is working and I'm not quite ready to frack it up again....lol.

---

### Post by jimi_hendrix on 2008-10-03
when the stable release comes out will you be able to upgrade via updater if you have the beta installed or will i have to install ubuntu for the third time in 5 months :)

---

### Post by aaaantoine on 2008-10-03
> **jimi_hendrix said:**
> when the stable release comes out will you be able to upgrade via updater if you have the beta installed or will i have to install ubuntu for the third time in 5 months :)

Via Updater.  You probably won't even notice it went to final, except that the package downloads that day will be especially slow. ;)

---

### Post by Jim! on 2008-10-03
Installed the Beta, everything works great. Sound issues have been resolved and my system is definitely running a lot smoother than it was previously. I have a good feeling about the final release of Intrepid. Also, Good morning to you all! (7:56AM here)

---

### Post by jimi_hendrix on 2008-10-03
ill start downloading the iso now then...

---

### Post by Jim! on 2008-10-03
> **jimi_hendrix said:**
> ill start downloading the iso now then...

Hahaha:D Yeah It probably would have been a smarter decision for me to download the .ISO but I wanted to get it done as quickly as possible. Woke up this morning, 8.10 Beta was installed, Just awesome! What's even better is my Internet cap reset one day earlier then I expected so I'm back to full speed!:D

---

### Post by Ub1476 on 2008-10-03
> **Jim! said:**
> Installed the Beta, everything works great. Sound issues have been resolved and my system is definitely running a lot smoother than it was previously. I have a good feeling about the final release of Intrepid. Also, Good morning to you all! (7:56AM here)

Good night to you. 00.09 here.

---

### Post by Jim! on 2008-10-03
The Intel bug has been fixed. [http://blogs.computerworld.com/when_linux_does_well_the_e1000e_ethernet_bug_fixed](http://blogs.computerworld.com/when_linux_does_well_the_e1000e_ethernet_bug_fixed)

---

### Post by jimi_hendrix on 2008-10-03
quick question while i burn my liveCD...how do i unistall hardy?

---

### Post by nick09 on 2008-10-03
Uh... Use the new live CD to wipe hardy?

---

### Post by Polygon on 2008-10-03
i usually wait till beta 4 or 5 to install the next version, i dont like too much breakage =P

---

### Post by jimi_hendrix on 2008-10-03
uhhh how do i tell which partition to install on since im dual booting and i dont remember which is which lol or is there a  help thread somewhere

---

### Post by andrewabc on 2008-10-03
> **jimi_hendrix said:**
> uhhh how do i tell which partition to install on since im dual booting and i dont remember which is which lol or is there a  help thread somewhere

It should say the file system format. If you are using windows don't overwrite NTFS or FAT filesystems.
ext3 is linux filesystem.

But make sure you know for sure. Check the size of each partition so that you know which size is for what OS.

---

### Post by Twitch6000 on 2008-10-03
> **Jim! said:**
> [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

I'm going to install the Beta tonight since I'm on holidays at the moment and don't really need a stable machine:) The only problem is that it will probably take the entire night since I'm over my download limit:( Still, I'm excited that the latest release will be out on October 30th. Looking forward to it. 

Is anyone else here planning on giving the Beta release a try? Or even already installed the Beta?

I will try it soon :D.

---

### Post by wolfen69 on 2008-10-03
btw, [HERE]("http://releases.ubuntu.com/8.10/ubuntu-8.10-beta-desktop-i386.iso.torrent") is the torrent file for 8.10 beta. i suggest everyone that wants to download it, use this. it will probably be faster than ubuntu's overloaded servers anyway.

---

### Post by L815 on 2008-10-03
I have to give the Ubuntu devs a lot of credit. In comparison with OpenSuse and Fedora, I have less breakages with Ubuntu Alpha/Beta releases than the other 2. OpenSuse doesn't even release Live Cd's of their betas :/

---

### Post by wolfen69 on 2008-10-03
> **L815 said:**
> I have to give the Ubuntu devs a lot of credit. In comparison with OpenSuse and Fedora, I have less breakages with Ubuntu Alpha/Beta releases than the other 2. OpenSuse doesn't even release Live Cd's of their betas :/

i agree. believe me, if there was something out there that worked better than ubuntu for me, i would use it. mandriva comes in a close second. 

a little off topic, but intrepid is my last hope for one of my customers computers. i tried hardy, mandriva, and open suse so far. all were unusable. damn thinkpads! this guy really, really wants to ditch windows.

---

### Post by stmiller on 2008-10-03
8.10 boots very quickly for me, compared to the last two Ubuntu releases.

---

### Post by nkri on 2008-10-04
> **stmiller said:**
> 8.10 boots very quickly for me, compared to the last two Ubuntu releases.

Is this on a clean install, or an upgrade from a previous version?

---

### Post by myusername on 2008-10-04
x wouldnt start for me on the live cd (although login sounds worked). im running an intel video card so it should be good to go. what gives?

---

### Post by richg on 2008-10-04
I use removable IDE drives so I downloaded and installed to a spare drive. Quite nice. Faster than 8.04.
I have a 3.2g machine, integrated mobo, Biostar P4M80-M4, no fancy audio or video, with 2gb ram. 
Dell 17" LCD display. DVD CD burner. All usb devices seen. 
Canon Lide scanner works fine. 
Media reader works fine. 
Sound fine. 
Ekiga sees webcam, just no audio.
Have to see if there is a way to record audio and video with the webcam.

Firewire external hard drive works just fine including many windows files I mad some years ago using 98SE.
I use web mail so never ever any mail issues.

Disappointed, on You Tube cannot view videos.

Cannot play DVD movies. Followed instructions for downloading codec stuff.
I can view and hear avi files I have with video player.
These two items should work out of the box and not need fine tuning.

Maybe this stuff will work with complete release. 
I can handle hardware but not software.
Still seems to be an improvement over 8.04. This is free so no reason to complain.

Cheers:D

Rich

---

### Post by jimi_hendrix on 2008-10-04
> **andrewabc said:**
> It should say the file system format. If you are using windows don't overwrite NTFS or FAT filesystems.
ext3 is linux filesystem.

But make sure you know for sure. Check the size of each partition so that you know which size is for what OS.

is there a help page i can go to...the installer wants to use 200gb and i dont want it to

---

### Post by Jim! on 2008-10-04
> **jimi_hendrix said:**
> is there a help page i can go to...the installer wants to use 200gb and i dont want it to

Are you at the partitioning stage? I'm taking it that your harddisk is around 200gb? If your dual booting then you could just format your previous Ubuntu install (unless you haven't backed up your data for whatever reasons). As for a tutorial try doing a forum search;) Good luck!

---

### Post by Ub1476 on 2008-10-04
> **myusername said:**
> x wouldnt start for me on the live cd (although login sounds worked). im running an intel video card so it should be good to go. what gives?

Lots of problems with Intel on Intrepid. I'm using x4500 and it starts fine, but with wrong res and suspend does not work.

---

### Post by dracvs on 2008-10-04
So far so good

Running in a virtual machine and it kick ***. 

Has anyone seen the new Blackest than the darkest night theme? the new human?

I dont think I like it so much. It is too dark. Yet it looks kind of great!

What i don't like is the default background it reminds me of Opensolaris.

... I wonder what would it take to but an ibex chewing a windows logo.... haha

---

### Post by andrewabc on 2008-10-04
> **jimi_hendrix said:**
> is there a help page i can go to...the installer wants to use 200gb and i dont want it to

Yes there are help pages. I don't know where they are but google "ubuntu dual boot" or something like that.

When installing you have to make sure to go to manual partition editor so you can choose which partitions to use. Otherwise using default selection it will use entire hard drive.

Before installing make sure to backup any important information on both partitions since you are not familiar with this.

---

### Post by Polygon on 2008-10-04
wowwwww

the beta doesn't even work on my computer

the hardy live cd worked fine, but for this one:

the live cd won't even start up unless i hold down a button on the keyboard.....

and then when it does start up, it says "(EE) No devices found" so x fails to start up.

Im confused on what exactly to report a bug about since there are many things that could go wrong, any suggestions?

---

### Post by jimi_hendrix on 2008-10-04
> **andrewabc said:**
> Yes there are help pages. I don't know where they are but google "ubuntu dual boot" or something like that.

When installing you have to make sure to go to manual partition editor so you can choose which partitions to use. Otherwise using default selection it will use entire hard drive.

Before installing make sure to backup any important information on both partitions since you are not familiar with this.

my vista partitioned is backed up and i havnt written any major documents that will hurt me to lose but i will try now

---

### Post by Jim! on 2008-10-04
Post what you think once you've installed. So far the Beta is working almost perfectly for me. There is an issue with reboot (If I choose to "restart" then it will freeze on boot - Not really an issue though since my computer is on for days at a time and If I need to restart I can just shut down). Everything else works flawlessy and I've noticed a definite speed improvement. 8.10 is going to be an excellent release.

---

### Post by Sealbhach on 2008-10-04
I installed the Beta after trying out the Live CD. Seemed fine so I installed to the hard drive.

When I booted up and got to the login screen the mouse and keyboard would not respond. I could do nothing.

So, I've had to reinstall 8.04.

Oh well. It's been reported on Launchpad by somebody else as well.


.

---

### Post by sikevux on 2008-10-04
Downloaded and installed the AMD64 version today. It works like a charm. I like the small GUI changes ex Partition Manager during installation.
Well I write more when I've tested more.

---

### Post by fatality_uk on 2008-10-06
In the process of downloading now... :D

---

### Post by fatality_uk on 2008-10-06
Works very well on an old IBM ThinkPad R32 with a NetGear wifi card.

---

### Post by Mazza558 on 2008-10-06
I've been using it for a while now, upgraded from Hardy, so I have no idea what works out of the box now. All my settings have carried over, including ndiswrapper.

---

### Post by norgur on 2008-10-06
so how the hell did you manage to take over a kernel module like ndiswrapper to a new kernel?

---

### Post by sayantandas on 2008-10-14
i have an issue. my microphone doesnt work in ubuntu 8.10 beta.
it shows up , i can unmute it but it doesnt come into effect. mic always remains muted.
does any one have this problem?

---

### Post by andrewabc on 2008-10-14
> **sayantandas said:**
> i have an issue. my microphone doesnt work in ubuntu 8.10 beta.
it shows up , i can unmute it but it doesnt come into effect. mic always remains muted.
does any one have this problem?

I would suggest creating a thread in the intrepid forums with more details if you want help.

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by gjoellee on 2008-10-14
> **billgoldberg said:**
> I might download it to give it a try.

Some questions before doing so:

Is that intel driver bug already fixed (or blacklisted or something)?

Is it already gnome 2.24 or still 2.23.xx?

Does it come with Empathy instead of pidgin?

Is flash 10 available?

Are their already medibuntu repo's (or equivalent) available, or do the hardy repo's work?

And is the boot up time improved as promised?

Has PulseAudio improved compared to Hardy?

Are the new Ati Drivers working properly (better than hardy ones)?

Is the beta stable or are there still lots of issues with it?

It is GNOME 2.24
It still comes with pidgin
Flash 10 is the default flash player in intrepid
I don't notice any boot speed increase :(
I would say that the Alpha 3 was more stable the Hardy :)

---

### Post by Polygon on 2008-10-14
thank god it still uses pidgin. Empathy is still 'alpha ' stage. It actually goes back in features from what pidgin has. Until empathy can actually deliver on the promises that all the supporters rant about, i highly doubt that pidgin will be replaced.

and bah, i have to do a kernel bisect to figure out why hardy doesn't even work on my laptop. >.<

---

### Post by Saint Angeles on 2008-10-14
i was using the alpha and it worked fantastic until they upgraded xorg (version 7.4 i think) and fglrx doesnt support that yet.

lemme know when ATI gets their s*** together.

---

### Post by scouser73 on 2008-10-15
I did a clean installation and it's working seamlessly, I even installed OpenOffice 3 so I could have the "full Package" so to speak. They've done a great job.

---

