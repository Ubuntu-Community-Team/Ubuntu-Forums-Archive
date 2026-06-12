---
title: "Proposal to drop Ubuntu alternate CDs for 12.10"
date: 2012-08-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-08-27
Maybe I'm misunderstanding this, seems an interesting time to propose when the live image hardly works, I guess it should be good to go soon

> Dear developers,

As part of ongoing efforts to reduce the number of images we ship for
Ubuntu, and to make the desktop image more useful in a variety of scenarios,
Dmitrijs Ledkovs has been hard at work in quantal adding support for LVM,
cryptsetup, and RAID to ubiquity.

The good news is that this means today we already have support in ubiquity
for cryptsetup and LVM in the guided partitioner, with manual partitioning
support soon to follow.  The somewhat bad news is that we will not have
support for RAID setup in ubiquity this cycle.

I would like to propose that, in spite of not reaching 100% feature parity,
we drop the Ubuntu alternate installer for 12.10 anyway.

The arguments that I see in favor of this are:

 - RAID is relatively straightforward to turn on post-install.  You install
   to one disk, boot to the system, assemble a degraded RAID with the other
   disks, copy your data, reboot to the degraded RAID, and finally merge
   your install disk into the array.  It's not quick, but it's *possible*.
 - Desktop installs on RAID will still be supported by other paths: using
   either netboot or server CDs and installing the desktop task.
 - RAID on the desktop really is a minority use case.  Laptops almost never
   have room for more than one hard drive; desktops can but are rarely
   equipped with them.  So the set of affected users is very small.  Some
   rough analysis of bug data in launchpad suggests a very liberal upper
   bound of .8% of desktop users.
 - RAID on the desktop correlates with conservatism in other areas:  we can
   probably continue to recommend 12.04 instead of 12.10 for the affected
   users.
 - It lets us tighten our focus on making the desktop CD shine: fewer images
   to QA, fewer different paths to get right (like the CD apt upgrader case)
   means more time to focus on the things that matter.

So my opinion is that we should drop the Ubuntu alternate CDs with Beta 1. 
Other flavors are free to continue building alternate CDs (i.e.,
"debian-installer" CDs) according to their preference, but we would drop
them for Ubuntu and direct users to one of the above-mentioned alternatives
if they care about RAID on desktop installs.

Please note one implication here that, with the possibility of not having
i386 server CDs for 12.10, the only install option for an i386 user wanting
RAID on a desktop would be to install via netboot or with the mini ISO.

Do any of you see reasons for not making this change, and dropping the
alternate CDs?  Are there shortcomings to the proposed fallback solutions
that we haven't identified here?

---

### Post by paul_in_london on 2012-08-27
Well I hope they're going to keep the minimal (boot-only) images! Not that I've done a fresh install for a while, but I always prefer to use a minimal image and that way I can just install what I want/need.

---

### Post by ronacc on 2012-08-27
[quote] The good news is that this means today we already have support in ubiquity
 for cryptsetup and LVM in the guided partitioner, with manual partitioning
 support soon to follow. The somewhat bad news is that we will not have
 support for RAID setup in ubiquity this cycle.[quote]

what in heck is he smoking ? ubiquity won't even handle a straight forward multi drive ( no raid,  no crypt , no LVM ) setup right much of the time .

---

### Post by jerrylamos on 2012-08-27
> **ronacc said:**
> what in heck is he smoking ? ubiquity won't even handle a straight forward multi drive ( no raid,  no crypt, no LVM ) setup right much of the time.Right on.  I've a pc with an IDE and a SATA drive.  Grub2, Ubiquity, and Ubuntu get totally confused as to which is a and which is b, even changing from hd0 to hd1 part way during boot and losing track of which one they did what to.  Grub2 is frantically searching for a UUID on one drive while Ubiquity had installed that UUID on the other drive and Grub2 absolutely will not look on the correct drive.  Bugs written, Development not interested.  I straighten the mess out by booting Lucid and re-installing Grub2.

I have no idea what sample of installs they try to decide to remove Alternate.  It has saved me any number of times.  Minimal I've tried took a v e r y long time, I don't have 4G internet speeds and it was a mess installing then finding out a major piece was missing, apt-get didn't solve it, so re-install all over.

---

### Post by kansasnoob on 2012-08-27
I asked about this some time ago at Lubuntu QA and I was told that Lubuntu will still have an alternate image.

The alternate images can be used for a variety of things, even performing a minimal CLI install if you know what you're doing.

---

### Post by nm_geo on 2012-08-27
Well I hope Lubuntu keeps it Kansas but just in case I just did a entire drive encrypted install using the current daily 20120827 Lubuntu amd64 desktop image and it did complete.

I am feeling kinda of freaky-lucky today and might try a Ubuntu install as i have the current daily amd64 running right now in all it's Unity glory on my Dell D620.. Well no I will try it on this Lenovo with the nvidia-xorg issues that will be a true test.. :p

Looks like they need to add some new test cases on the qa-tracker too.

---

### Post by oldfred on 2012-08-27
Just recently (12.04.1?) we seem to be getting a lot of installs that we cannot figure out an issue. We then suggest alternative installer & it just works.

Also lots more with RAID. Every Smart Response system seems to to be some sort of RAID. Also seems best to not use the Smart Response and just use the SSD anyway.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

I am not a fan of RAID on desktops but I am seeing more and more users with RAID.

---

### Post by effenberg0x0 on 2012-08-27
> The somewhat bad news is that we will not have
support for RAID setup in ubiquity this cy.cle

Way to go, what a nice deed. Why not drop the whole kernel then. 




**EDIT:** *I have edited my post because it was not pleasant to read.*

Well, I don't feel like supporting this anymore. It's been some years since Dapper... and I have invested a lot of time and dropped a lot of other projects because I trusted Ubuntu would be different. I have lobbied this thing to gov. (and succeeded) for God sake.  It's not different. This is just sad.

I'd appreciate if anyone could post some delirious CoC-Friendly ramble next... 

Regards,
Effenberg

BTW, it would be nice for our Ubuntu Olympus people to talk to Seagate/Samsung & WD/Hitachi. New HDD/SSD are thinner than current 2,5" units (7mm). Ultrabooks will ship with RAID 1 as the standard by 2013...................................

---

### Post by mc4man on 2012-08-27
I guess from a slightly self-centered view this appears premature (have no raid, ect.

Atm the live images cannot be used here for install or even a live session if there is any other Ubuntu/grub/lightdm  install on the HD.

The symptoms are very similar to what happened last cycle with lightdm/unity-greeter in terms of the video degradation & how it could change depending on what partition grub was configured on.

I know I'm not the only one seeing this though again could be hardware related.

Maybe this is fixed tomorrow or next week but if anything like last cycle it took awhile to resolve.

Assuming it is a 'known' issue may be as shortsighted as assuming that the nvidia/xserver issue was  known 'upstairs' 
(apparently it wasn't

So atm the alt. is the best means to install..

---

### Post by ronacc on 2012-08-27
I gave up even trying the daily's about a week ago . SDC has been completely useless to me this cycle and burning DVD coasters gets old after awhile .

---

### Post by sffvba[e0rt on 2012-08-27
With my current desktop setup I have not been able to get the Live CD to work at all... my screen goes out of resolution and the only method I have found to install Ubuntu has been the alternative installer.

This would suck on many levels.


404

---

### Post by jbicha on 2012-08-27
I successfully installed Ubuntu with today's daily CD so it is possible.

The warning about things being less stable this week due to imminent UI freeze still stands though.

---

### Post by nm_geo on 2012-08-27
Yeah I got the Ubuntu to install too and did the encrypted entire drive install just to see if it would be viable.  It is buggy as noted the nvidia-xserver issue make it difficult on my Lenovo T61p but I did get it to install and run.

With that said it is almost criminal in my mind to not keep the d-i ... It just works without nomodeset and Ctrl-Alt-Del during the Plymouth scrolls..

I will continue to test but as i decided some time ago Lubuntu will get the majority of my efforts

---

### Post by kansasnoob on 2012-08-27
> **nm_geo said:**
> Well I hope Lubuntu keeps it Kansas but just in case I just did a entire drive encrypted install using the current daily 20120827 Lubuntu amd64 desktop image and it did complete.

I am feeling kinda of freaky-lucky today and might try a Ubuntu install as i have the current daily amd64 running right now in all it's Unity glory on my Dell D620.. Well no I will try it on this Lenovo with the nvidia-xorg issues that will be a true test.. :p

Looks like they need to add some new test cases on the qa-tracker too.

I really think the alternate images are an absolute requirement for the Lubuntu and Xubuntu target audience.

I have an old Micron with a PII that won't begin to run a live installer but I can use an alternate image to perform a minimal install, then add the xserver, lightdm, and lubuntu-core.

The netboot isos won't work on it due to the way the BIOS recognizes the PCI ethernet card.

I also haven't been able to get anything to work with my circa 2007 VIA P4M800 graphics since Ubuntu dropped Unity-2D. Hopefully it's just a simple xserver issue.

I'm trying to help troubleshoot this bug right now:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

Fun times ahead ;)

---

### Post by mc4man on 2012-08-28
> **jbicha said:**
> I successfully installed Ubuntu with today's daily CD so it is possible.

The warning about things being less stable this week due to imminent UI freeze still stands though.
Who knows - maybe it gets squared up shortly.
Can say that todays image is the same thing, either a mosaic or art deco.
This is with nvidia chipset on a multi-boot (Ubuntu 12.04/12.10), I'm sure some will find attached screens somewhat familiar 
(sorry about poor quality, battery was almost dead in camera..
The variation  in what is displayed comes from moving where grub is configured

---

### Post by arpanaut on 2012-08-28
Interesting, although I knew this was coming, I was hoping it would not happen until all the options available in the alternate iso became avaliable in the live-cd.

Last cycle I would have been cut out of testing the LTS release if not for the alt.iso. I was hit with the ubuiquity-slideshow-ubuntu crash and had no way to get a fresh install until I found out that the slideshow could be removed from the live session. Which I didn't discover until after release and I am still seeing people affected by this with the 12.04 iso, I am not sure if it has been corrected with 12.04.1 but I hope so.  

I can appreciate the effort to streamline the efforts of the developers, but until the live-cd works flawlessly I have to wonder if this move is the best way to proceed.
Up until Lucid and Maverick I used the alternate exclusively because it was reliable and could also be used as a rescue cd, but for the purpose of "testing" and in the spirit of testing the mainstream method of installation I have used the "Desktop" iso for the most part. BUT, the past two cycles I have found it to be "flakey" to say the least.

I realise that the LTS +1 release has historically been for the most part  somewhat out of the norm  and radical in what is added and removed, I'm cool with that, but if I am closed out of my ability to install, test, and be a part of the community's efforts, I become a little "put-off".

If the Desktop.iso can be made reliable enough to offer the options of and the flexibility of the Alt.iso I'm all for it but if not I have to question the advisability of this move.  Maybe even a "fallback" mode to text mode  incorporated into the iso if the specs of the target machine prove to be sub-optimal.

I love Ubuntu & support what the developers are trying to accomplish, yet sometimes I wonder about their perspective related to the common user.

My question is, what are the options IF the live-cd fails the user?
Other question: Who is the author of this "Dear Developer" posting?

---

### Post by kansasnoob on 2012-08-28
> My question is, what are the options IF the live-cd fails the user?
Other question: Who is the author of this "Dear Developer" posting?

Good questions :)

---

### Post by cariboo on 2012-08-28
> My question is, what are the options IF the live-cd fails the user?
Other question: Who is the author of this "Dear Developer" posting?

If you are subscribed to the ubuntu-devel mailing list, you'd know that the author is [Steve Langasek]("https://wiki.ubuntu.com/SteveLangasek")

---

### Post by lykwydchykyn on 2012-08-28
[quote=Steve Langasek]

- RAID is relatively straightforward to turn on post-install. You install
to one disk, boot to the system, assemble a degraded RAID with the other
disks, copy your data, reboot to the degraded RAID, and finally merge
your install disk into the array. 
[/quote]

This word "straightforward"... I do not think it means what you think it means... :confused:

---

### Post by dino99 on 2012-08-28
*****  Dmitrijs Ledkovs has been hard at work   ***** :p

dont stop mate :D ubiquity is so buggy, maybe rebuilt it from scratch ;)

and in a far future maybe we could trust that installer  ):P

i'm surprised they does not think to drop the "desktop" iso instead of the "alternate". Wonder if that clever guy have made installation before writing its prose.

note: as compiz/unity, the ubiquity team seems to need some skilled devs .

---

### Post by arpanaut on 2012-08-28
> **cariboo907 said:**
> If you are subscribed to the ubuntu-devel mailing list, you'd know that the author is [Steve Langasek]("https://wiki.ubuntu.com/SteveLangasek")

Touché! 
Although the OP should have included, No?
No biggie.Thanks for the info.

---

### Post by jerrylamos on 2012-08-28
> **kansasnoob said:**
>  I also haven't been able to get anything to work with my circa 2007 VIA P4M800 graphics since Ubuntu dropped Unity-2D. Hopefully it's just a simple xserver issue.

Fun times ahead ;)
My workaround is 
sudo apt-get install lxde
lxde is a Debian desktop so it doesn't depend on Ubuntu/Unity/Compiz development support.

Now the problem is Ubiquity install uses some variant of Unity desktop which is frequently broken, at least partially so.  A non-Unity Ubiquity would be great don't hold your breath, Development isn't interested that's loud and clear. 

I've tried mini.  Takes hours over my cheap 1.5 MB internet and difficult to remember all the Ubuntu stuff I use like Samba, SSH, wireless WPA, Office, Office, LXDE, all kinds of accessories & preferences.  I'm hardly cli versatile so getting wireless WPA connected on mini is a bear for me. 

Once up with lxde hopefully you can try some things for your hardware.

I switch desktops with logout for testing.

Jerry

p.s.  I haven't been running Lubuntu with LXDE for two reasons.  One is I use Firefox, Libre, gedit, etc. so I install all those on top of Lubuntu much easier to start with Ubuntu then install LXDE which is what I do.

Second, vibes from Ubuntu development since Lubuntu doesn't need the latest and greatest hardware that they use, they are likely to drop support just like they did 2D.  But I still have choices.

---

### Post by qamelian on 2012-08-28
> **jerrylamos said:**
> My workaround is 
Now the problem is Ubiquity install uses some variant of Unity desktop which is frequently broken, at least partially so.  A non-Unity Ubiquity would be great don't hold your breath, Development isn't interested that's loud and clear. 

I think you might be a bit confused here. Ubiquity has no dependency on Unity or even Compiz. It's a separate, unrelated application and has existed before Unity even appeared. It runs under Unity if you boot to the desktop environment then run the installation icon, but if you just choose to install from the boot menu, Ubiquity runs by itself, not with any form of Unity. You can verify that it is not dependent on Unity [here]("http://packages.ubuntu.com/quantal/admin/ubiquity").

---

### Post by ventrical on 2012-08-28
> **jerrylamos said:**
> My workaround is 
sudo apt-get install lxde
lxde is a Debian desktop so it doesn't depend on Ubuntu/Unity/Compiz development support.

Now the problem is Ubiquity install uses some variant of Unity desktop which is frequently broken, at least partially so.  A non-Unity Ubiquity would be great don't hold your breath, Development isn't interested that's loud and clear. 

I've tried mini.  Takes hours over my cheap 1.5 MB internet and difficult to remember all the Ubuntu stuff I use like Samba, SSH, wireless WPA, Office, Office, LXDE, all kinds of accessories & preferences.  I'm hardly cli versatile so getting wireless WPA connected on mini is a bear for me. 

Once up with lxde hopefully you can try some things for your hardware.

I switch desktops with logout for testing.

Jerry

p.s.  I haven't been running Lubuntu with LXDE for two reasons.  One is I use Firefox, Libre, gedit, etc. so I install all those on top of Lubuntu much easier to start with Ubuntu then install LXDE which is what I do.

Second, vibes from Ubuntu development since Lubuntu doesn't need the latest and greatest hardware that they use, they are likely to drop support just like they did 2D.  But I still have choices.


I have been basically doing the same thing and it has worked well on most older machines that I have been testing. I have  a 750 MHz Celeron and a 1.2GHz Athelon  in my arsenal of towers which also include processing speeds of 3GHz. Dell Dimension 3100 with Intel Graphics works best with Unity 3d. It actually runs faster with compiz enabled . Same with Intel Based motherboard with Nvidia GeForce210/218. runs faster with compiz but LDXE also works just as well.  It is a nice, banal and stable desktop for those who want stability in testing .I prefer (choices) of Unity 3D which allows me to test the maximum capacity and endurance of my hardware (is what I do as a tester). LDXE , although great in it's own right , is too feeble  to max out my hardware for *high* performance  testing.

---

### Post by kansasnoob on 2012-08-28
Received this message from Lubuntu's lead dev:

> Le 08/28/2012 09:10 AM, Lance a écrit :
> I'd think both Lubuntu and Xubuntu will suffer from this greatly since
> we do tend to target older low end computers.
Just to make it clear, Lubuntu will keep alternate for 12.10.

Regards,
Julien Lavergne

---

### Post by effenberg0x0 on 2012-08-28
> **kansasnoob said:**
> Received this message from Lubuntu's lead dev:

> > I'd think both Lubuntu and Xubuntu will suffer from this greatly since
> we do tend to target older low end computers.
Just to make it clear, Lubuntu will keep alternate for 12.10.

Regards,
Julien Lavergne


That's good news Kansasnoob :) From a more positive perspective, IMO we will have many users that had never tried Ubuntu flavors switching Ubuntu for Lubuntu when QQ is released (assuming Ubuntu really drops the alternate ISO, I'm not sure it will happen yet, it makes no sense to me). 

By release week, Blogs, other boards and Ubuntu-related sites will probably post tutorials about installing Lubuntu (for users that fail to use Ubuntu default installer). I think this is a good thing. The flavors are mature and will benefit from increased awareness from end-users and adoption.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-08-29
I have found it! This is the link that I have been looking for.

[http://ubuntuforums.org/showthread.php?t=2047451]("http://ubuntuforums.org/showthread.php?t=2047451")

Does this post sound familiar to anyone?

Here are a couple of others.

[http://ubuntuforums.org/showthread.php?t=2049549]("http://ubuntuforums.org/showthread.php?t=2049549")

[http://ubuntuforums.org/showthread.php?t=2049103]("http://ubuntuforums.org/showthread.php?t=2049103")

Anyone care to guess what the most asked questions on Ask Ubuntu will be over the coming months?

lol, just does not come anywhere near it!

Regards.

---

### Post by EgoGratis on 2012-08-29
The main problem i see for majority of Ubuntu user that download Ubuntu and want to try it by installing it is GUI installer just doesn't work all  the time.  Or better it doesn't work a lot of times! It was easy to suggest just use alternate CD until now but now this is gone. The result? 

 Ubuntu installation won't work a lot of times! That's plain and simple fact and add Unity 2D won't be available anymore and i think it's reasonable to suggest "CPU" based Unity 3D won't work a lot of times in a way user would like it to work... Now add Wayland/Weston that will probably be available next release in some form and new machines where user will have to deal with "Microsoft Security"...

It will probably be hard to succeed and install Ubuntu on the hardware. This is not complaining because i think Unity 3D and Wayland will make things better in long term but time in between will be challenging.   

I was always thinking in direction why don't have both option on one CD? If GUI installer fails just start again and select "text installer" that usually just works!

---

### Post by vexorian on 2012-08-29
> **EgoGratis said:**
> The main problem i see for majority of Ubuntu user that download Ubuntu and want to try it by installing it is GUI installer just doesn't work all  the time.  Or better it doesn't work a lot of times! It was easy to suggest just use alternate CD until now but now this is gone. The result? 

 Ubuntu installation won't work a lot of times! That's plain and simple fact and add Unity 2D won't be available anymore and i think it's reasonable to suggest "CPU" based Unity 3D won't work a lot of times in a way user would like it to work... Now add Wayland/Weston that will probably be available next release in some form and new machines where user will have to deal with "Microsoft Security"...

It will probably be hard to succeed and install Ubuntu on the hardware. This is not complaining because i think Unity 3D and Wayland will make things better in long term but time in between will be challenging.   

I was always thinking in direction why don't have both option on one CD? If GUI installer fails just start again and select "text installer" that usually just works!
That would be way too practical.

---

### Post by wconstantine on 2012-08-29
I was upset when I read about this. I use the alternate ISO due to the very nice option of full disk system encryption. Then there's the thing where the desktop ISO doesn't even install on my system. I haven't investigated why, but it has always been that way for me. 

A simple way to configure full system disk encryption is a must for me. I will have to choose another distro if this option is removed, which pains me, I like Ubuntu a lot.

---

### Post by vexorian on 2012-08-29
I think this might be a good thing.

The alternate CD is too many times an excuse not to fix issues with the live CD. "So what? Just use the alternate CD".

Also, if people are really having issues, they can use the lubuntu alternate cd and then install ubuntu-desktop. It is likely they might need lxde or xcfe anyway.

---

### Post by effenberg0x0 on 2012-08-29
Wouldn't it make more sense to:

1) Improve the Live CD, focus on it. Fix as much bugs as possible. Ask testers to test it in-depth. I'm not talking about ISO-testing and basic test-cases here: Real testing, installing and using the OS for daily tasks. Become more confident about Ubiquity doing successful installs in diverse hardware, etc. Keep testers focused on it (installing/using/testing/reporting) until Beta 2.

2) Then, by Beta 2, if results are good, we can evaluate the *possibility* of dropping the Alternate ISO.

Otherwise we face the risk of - for yet another cycle - burn the brand because of installation problems ordinary users can't handle. 

I don't want to sound like a broken record (and I know I do), but it all goes down to what we have been discussing for some cycles already. Ubuntu will be considered as a real alternative for users, OEMs, companies, etc if, and only if, at least 3 basic factors are reliable. 

IMO, this "tripod of success" for Ubuntu is:
**1)Ubiquity:** Bug-free install.
**2)Grub/Plymouth:** Bug-free boot/splash.
**3)Drivers/Working Desktop:** Bug-free automatic detection of hardware and installation of basic drivers: VGA and Wired/Wireless NIC.

If we don't have that, all the rest (like cool applications, visual enhancements, effects, etc) is irrelevant: Users won't get to even try these stuff/features.   

Right now I don't think we can say that these 3 factors are stable and reliable. 

Regards,
Effenberg

---

### Post by vexorian on 2012-08-29
Bug free installer, bug free boot and splash and bug free destection of drivers are all things windows does not have. Yet it was successful with users, OEMs and companies.

---

### Post by mc4man on 2012-08-29
The fact that the alt. installer is history is a foregone conclusion.
I did suggest to the mailing list that dropping next week might be premature as many 'seemed' to be having issues getting the current live images to boot to a usable condition.
(myself will only get the mosaic or similar corrupted though there could be a workaround to get to the desktop
They asked for that to be justified - I guess I can't do so other than seen here which doesn't much matter

Unless this was more widespread, either the corrupted or something else preventing an install (or good install), then it would appear they'll drop for beta 1.

---

### Post by EgoGratis on 2012-08-30
> **vexorian said:**
> I think this might be a good thing.

The alternate CD is too many times an excuse not to fix issues with the live CD. "So what? Just use the alternate CD".

Also, if people are really having issues, they can use the lubuntu alternate cd and then install ubuntu-desktop. It is likely they might need lxde or xcfe anyway.

No plain and simple fact is Ubuntu installation won't work a lot of times. That's it. And suggestion to install Xubuntu and then Ubuntu desktop on top of it i don't know about that but i think it's unprofessional.

---

### Post by jerrylamos on 2012-08-30
> **vexorian said:**
> Bug free installer, bug free boot and splash and bug free destection of drivers are all things windows does not have. Yet it was successful with users, OEMs and companies.Difference is most "windoze" were bought by customers when they bought a new faster computer that is capable of running the new version of "windoze".  "Windoze" is installed by the pc manufacturer with most of the bugs worked out.  

Ubuntu entirely different - users most of them with casual pc expertise are expected to install ubuntu with largely no kinks on lots of different hardware configurations.

Now typically with ubuntu in Alpha development among the things that break first are install, ubiquity, "x", desktop, ... because of all the changes in process.  So us testers do get to deal with half baked ubuntu because it isn't out of the oven yet.

I would hope ubiquity and install would be rock solid by RC time "on lots of different hardware".  Not usually...

So I do what I can, test install/ubiquity/"x"/...with frequent of installs on a tower, notebook, netbook internal hard drive and USB hard drive.  Each have been getting different bugs.  Yes I'm retired and squeeze in time.  

Jerry  

p.s. Unity buffs can test unity.  I boot ubuntu, install a wallpaper picture of my wife on an Australian beach, then apt-get a different desktop.

---

### Post by vexorian on 2012-08-30
> **EgoGratis said:**
> No plain and simple fact is Ubuntu installation won't work a lot of times. That's it. And suggestion to install Xubuntu and then Ubuntu desktop on top of it i don't know about that but i think it's unprofessional.
I think the idea of the alt install is unprofessional by design, so I don't see what the problem is.

Thanks to this, bugs with ubiquity in modern computers will be a priority to fix, rather than having the devs say "just use the alt installer".

---

### Post by mörgæs on 2012-08-30
The alternate ISO serves a lot of other purposes than RAID installation. Please keep it.

If I'm guiding someone through the Buntu install over the phone and something does not work, what are my options? Only one, and that is 'try the alternate ISO'. More often than not it does magic.

Also in a world-wide perspective I would like to keep the alternate. There could be heaps of old hardware out there on which the alternate ISO is necessary. Please don't only focus on the developer part of the equation.

---

### Post by EgoGratis on 2012-08-30
> **vexorian said:**
> I think the idea of the alt install is unprofessional by design, so I don't see what the problem is.

Thanks to this, bugs with ubiquity in modern computers will be a priority to fix, rather than having the devs say "just use the alt installer".

Why would powerful text installer be unprofessional by design especially if it's often used when everything else fails? About fixing bugs in GUI installer i don't have any objections to that but that doesn't change anything in regards that in foreseeable future Ubuntu installation (GUI) will fail a lot of times and that is plain and simple fact and the only difference will be alternate CD will not be there anymore.

And about "mini ISO" install mentioned as alternative  good luck with that to succeed installing Ubuntu with it if alternate CD works, GUI doesn't work a lot of time then "mini ISO" is probably below all available options but in the end i will not try to find sense in this because i tried to make sense in decision to drop Dodge Windows i read all "arguments" why and i did the same with Nautilus and "dual pane" mode and i read all the "arguments" and i didn't buy any of them an i don't buy this one that GUI installer will from now on just work.

---

### Post by mcellius on 2012-08-30
> I think the idea of the alt install is unprofessional by design, so I don't see what the problem is.

Thanks to this, bugs with ubiquity in modern computers will be a  priority to fix, rather than having the devs say "just use the alt  installer".I agree witih this.  

I can easily imagine a project leader or manager saying, "Okay, guys, it's time to have a solid installer and get rid of all these alternates.  We've had to use them in the past because we have had too many problems with the standard installer, but we now need to make these bugs a priority so we can get this stuff more user-friendly.  Newcomers to Ubuntu find these problems frustrating and annoying and unnecessarily techie."

Of course, it only makes sense if they do actually address Ubiquity's problems.

---

### Post by lykwydchykyn on 2012-08-30
I wonder: why not just include it as a boot option on the normal CD?  DI surely takes up very little space.

---

### Post by effenberg0x0 on 2012-08-30
> **mcellius said:**
> I agree witih this.  

I can easily imagine a project leader or manager saying, "Okay, guys, it's time to have a solid installer and get rid of all these alternates.  We've had to use them in the past because we have had too many problems with the standard installer, but we now need to make these bugs a priority so we can get this stuff more user-friendly.  Newcomers to Ubuntu find these problems frustrating and annoying and unnecessarily techie."


I agree, but I'm not sure there's enough people, skills, time, etc to fix and improve Ubiquity to the point we can feel safe without the Alt. 
> **mcellius said:**
> 
Of course, it only makes sense if they do actually address Ubiquity's problems.
Yea, that's my main concern... We have seen bugs go from release to release for a while. 

I agree with everyone that defends we should have a single installer. But although having a single, GUI-Based, user-friendly, WYSIWYG-like, stable, very reliable, full-featured installer would be fantastic, I think we're far from it technically. And release is too close now. I hope they choose to play it safe this cycle. I'd fully support it if they choose to start RR publicly focused on dropping Alt and improving Ubiquity, starting from Day-1. Testing should be strongly involved in this strategy. I'd like to see a full review of open bugs, etc. I don't feel like enough was done in this sense this cycle and, IMO, we're out of time at this point.

That's just my 2 cents anyway. I believe this is not really a proposition.

Regards,
Effenberg

---

### Post by ventrical on 2012-08-30
Removing the alternate.iso seems to be a move designed  to corral testers and unsuspecting noobs to fit the more formal testers q&a profile. This way the bean counters and number crunchers can  extrapolate and end result and economize the bug reporting processes, if not eliminate it altogether.  That would more or less deprecate ubuntuforums to acceptable line-noise only.

  With the global economy the way it is atm, I can see the  short term logic to save time, money and human resources, but, consequentialy , also  that the long term goal of the  proposed (200 million users) is reduced to a pipe-dream and becomes less and less a real number for Canonical as a whole.

  I think we should "pipe-up" as loud as we can while this forum is still recognized with the high level of respect that it currently enjoys.

Just my 2 cents worth.

---

### Post by EgoGratis on 2012-08-31
> **mcellius said:**
> I agree witih this.  

I can easily imagine a project leader or manager saying, "Okay, guys, it's time to have a solid installer and get rid of all these alternates.  We've had to use them in the past because we have had too many problems with the standard installer, but we now need to make these bugs a priority so we can get this stuff more user-friendly.  Newcomers to Ubuntu find these problems frustrating and annoying and unnecessarily techie."

Of course, it only makes sense if they do actually address Ubiquity's problems.

It's not the question GUI vs. text installer because Ubuntu desktop users should be able to use GUI installer that just works it's the question of being realistic.

Are open source video drivers there already and dropping text installer makes sense or not and if not how to install Ubuntu on the hardware when GUI installer fails.

There probably should be an answer how to install Ubuntu 12.10 on hardware where GUI installer fails and until Ubuntu 12.10 the answer was try alternate CD and it usually worked. Now the answer is you can't but we will try to make GUI installer work better? The problem as i see it is not GUI vs. text installer but what should be the answer when GUI installer fails? Will GUI installer gain new "compatibility mode"? How to install Ubuntu 12.10 on hardware if GUI installer fails and you know Ubuntu will probably work once you install it and enable additional drivers i solved this issues until Ubuntu 12.10 with **alternate CD** and how should i solved them until GUI installer improves and does not fail a lot of times? No real answer i guess and at least OK i hope until Ubuntu 14.04 GUI installer will just work!

---

### Post by kansasnoob on 2012-09-04
Running through Beta 1 testing I'm still miffed that this isn't fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

And replacing clear messages with nonsensical little icons seems counterproductive:

[ATTACH]223645[/ATTACH]

Not to mention that the window that opens after clicking on the "gears" says, "Create partition", even if your intention is to edit or change a partition!

Also, how the hell do you enter an HTTP proxy if required?

Dumb, dumb, dumb ](*,)](*,)](*,)

---

### Post by EgoGratis on 2012-09-04
> **kansasnoob said:**
> Running through Beta 1 testing I'm still miffed that this isn't fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

And replacing clear messages with nonsensical little icons seems counterproductive:

[ATTACH]223645[/ATTACH]

Not to mention that the window that opens after clicking on the "gears" says, "Create partition", even if your intention is to edit or change a partition!

Also, how the hell do you enter an HTTP proxy if required?

Dumb, dumb, dumb ](*,)](*,)](*,)

I looked at bug report and it is fixed and OK now more time will be used on improving GUI installer and that is something that will make things better in the future and i guess Ubuntu 14.04 could have GUI installer that just works in majority of cases!

---

### Post by effenberg0x0 on 2012-09-04
What is the status? Was this "proposal" accepted?

---

### Post by Stinger on 2012-09-04
> **kansasnoob said:**
> 
Not to mention that the window that opens after clicking on the "gears" says, "Create partition", even if your intention is to edit or change a partition!

Dumb, dumb, dumb ](*,)](*,)](*,)

LOL.
+1 for that, it definitely needs some improvement :rolleyes:

---

### Post by EgoGratis on 2012-09-04
> **effenberg0x0 said:**
> What is the status? Was this "proposal" accepted?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

I was talking about this bug. About new fetures in GUI installer and adding some of features that only alternate CD provided until now... Probably this will take time but OK the pressure is on now and and let's hope by the time of Ubuntu 14.04 it will turn out dropping alternate CD was a good thing.

---

### Post by kansasnoob on 2012-09-04
> **effenberg0x0 said:**
> What is the status? Was this "proposal" accepted?

Apparently yes. At least there are no Ubuntu alternate images on the qa tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/232/builds](http://iso.qa.ubuntu.com/qatracker/milestones/232/builds)

---

### Post by effenberg0x0 on 2012-09-04
> **kansasnoob said:**
> Apparently yes. At least there are no Ubuntu alternate images on the qa tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/232/builds](http://iso.qa.ubuntu.com/qatracker/milestones/232/builds)

I see, thanks.

I bet it was a close one, like 50,1% Yea, 49,9% Nay. 
Just kidding.

Regards,
Efenberg

---

### Post by martijntje on 2012-09-04
I would hate to see the alternate CD go. The graphical installer is a pain to work with, I much prefer to just use a fast, text-based installer instead.

---

### Post by jerrylamos on 2012-09-04
> **martijntje said:**
> I would hate to see the alternate CD go. The graphical installer is a pain to work with, I much prefer to just use a fast, text-based installer instead.Yea, verily.  I've hand and am having problems with quantal ubiquity GUI.  Menu's appearing and disappearing and jumping around and even a current case click on a menu selection and Ubiquity vanishes.  No fix for me yet.

---

### Post by kansasnoob on 2012-09-04
> **effenberg0x0 said:**
> I see, thanks.

I bet it was a close one, like 50,1% Yea, 49,9% Nay. 
Just kidding.

Regards,
Efenberg

Well, I'm officially out of iso-testing now:

[http://ubuntuforums.org/showthread.php?t=2053135](http://ubuntuforums.org/showthread.php?t=2053135)

More and more "changes" are actually becoming "barriers" and I just refuse to subject myself to it any longer.

After a simple surgery I'm getting a bit more oxygen to my brain, and I feel better, but I need less desk time and more foot time :D

And many of the recent changes are just nonsensical to me.

---

### Post by effenberg0x0 on 2012-09-04
> **kansasnoob said:**
> Well, I'm officially out of iso-testing now:

[http://ubuntuforums.org/showthread.php?t=2053135](http://ubuntuforums.org/showthread.php?t=2053135)

More and more "changes" are actually becoming "barriers" and I just refuse to subject myself to it any longer.

After a simple surgery I'm getting a bit more oxygen to my brain, and I feel better, but I need less desk time and more foot time :D

And many of the recent changes are just nonsensical to me.

I know of your fights in the two aspects you mentioned. Your health is obviously more important and you are right to focus on it. 

I think QQ cycle was, for many of us, an experiment. It carried a possibility of change. Everyone stopped questioning and started supporting things blindly in hopes of seeing these potential changes come true. However, as you have just mentioned, things are happening in ways many of us can't understand or accept. I completely agree with you.  

Once QQ is released and the RR cycle is started, everyone will have an opportunity to look back. We will be able to compare the opinions and demands testers have transmitted over the cycles to what was done/accepted/implemented/rejected during QQ. And we will see how it reflected (positively, negatively) in QQ quality. 

Summarizing, I feel QQ is the tipping-point. It is unfortunately needed so we can have RR be a turning-point. 

Anyway, we know Ubuntu won't thank you for your huge efforts in ISO-Testing throughout the development cycles, so I will: As a Ubuntu supporter and, more importantly, a user, thank you for everything you have done so far. 

In the near future, when QA/testing organically changes (I'm 100% sure it will happen), I hope Ubuntu still has supporters like you (and many others we both know) to undertake testing tasks in a more transparent environment. I'm confident you will do a lot more for Ubuntu. If not in ISO-Testing, in any other area of contribution.

Regards,
Effenberg

---

### Post by ventrical on 2012-09-04
+1 for kansasnoob and jerrylamos, two tireless Ubuntu warriors.
+1 for effenberg, Ubuntu advocate and brainstormer  par excellance
.

---

### Post by nm_geo on 2012-09-04
> **kansasnoob said:**
> Well, I'm officially out of iso-testing now:

[http://ubuntuforums.org/showthread.php?t=2053135](http://ubuntuforums.org/showthread.php?t=2053135)

More and more "changes" are actually becoming "barriers" and I just refuse to subject myself to it any longer.

After a simple surgery I'm getting a bit more oxygen to my brain, and I feel better, but I need less desk time and more foot time :D

And many of the recent changes are just nonsensical to me.

I, as one of the testers you taught and brought into the fold, will miss you; but I am glad you are feeling better and I hope the very best for you. Your friend
Greg Faith (nm_geo)

---

### Post by jerrylamos on 2012-09-04
> **kansasnoob said:**
> Well, I'm officially out of iso-testing now:

[http://ubuntuforums.org/showthread.php?t=2053135](http://ubuntuforums.org/showthread.php?t=2053135)

More and more "changes" are actually becoming "barriers" and I just refuse to subject myself to it any longer.

After a simple surgery I'm getting a bit more oxygen to my brain, and I feel better, but I need less desk time and more foot time :D

And many of the recent changes are just nonsensical to me.

BTW, we're in our 70's, exercise, concentrate on health for the complete detail on what's going on and pointers what to do highly recommend the book "The China Study" by Cornell nutritional biochemist prof. T. Colin Campbell.  Amazon, B&N, bookstores everywhere.  I'm no follower of Rosie O'Donnel she recently had a scary heart attack and is being very pro-active, or at least says she is on food and exercise.  People are designed for foot time.  Labor day parade in quaint New Hampshire town for us yesterday campaign banners everywhere.

---

### Post by kansasnoob on 2012-09-05
> **nm_geo said:**
> I, as one of the testers you taught and brought into the fold, will miss you; but I am glad you are feeling better and I hope the very best for you. Your friend
Greg Faith (nm_geo)

I'll still be around, for sure on the Lubuntu QA mailing list, and I'll watch these new ubiquity bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I didn't get that first one reported on the QA tracker, but it should be. Not being able to specify whether you want to create a primary or logical partition seems like borkage to me :(

I probably will continue to do some testing, and report bugs, but these 3 and 4 day milestone testing marathons are just too much for me now.

In other words, I'll still be involved, just to a much lesser extent ;)

---

### Post by smartboyhw on 2012-09-05
Oops

1. I do think that it it time to abandon the Ubuntu alternate CDs. KVM and encrypted installation has been adding difficulties to it. So...

2. effenberg0x0: Sorry, what happened to the U+1 team? I don't see any updates these days. I like to help you know in testing a lot;) Look at my signature. Thanks kansasnoob BTW.

---

### Post by The Cog on 2012-09-05
I think it would be far mode sensible to drop the graphical installer from the live CD. Just refer to the "alternate" CD as the "installer" CD. This way, the live CD can be used purely as a live CD - testing that things work etc. And the installer CD will be a rock-solid full-featured installer. If you want to test, use the live CD. If you want to install then use the installer CD. 

I really don't understand why they want to enforce using the less reliable and less feature rich graphical installer, unless it is in order to sell advertising space on the graphical installer's slide show.

---

### Post by ronacc on 2012-09-05
> **The Cog said:**
> I think it would be far mode sensible to drop the graphical installer from the live CD. Just refer to the "alternate" CD as the "installer" CD. This way, the live CD can be used purely as a live CD - testing that things work etc. And the installer CD will be a rock-solid full-featured installer. If you want to test, use the live CD. If you want to install then use the installer CD. 

I really don't understand why they want to enforce using the less reliable and less feature rich graphical installer, unless it is in order to sell advertising space on the graphical installer's slide show.

unfortunately I have run into many cases where the graphical installer runs just fine but an install from it fails to boot or boots to a console window and needs additional tweaks to get to desktop  . A situation like that is almost guaranteed to lose a new potential user so they need to test the graphical installer even more intensely since that is the one most of the "public" will choose . IMHO there should be NO difference in what the graphical installer offers and  what the alternate offers , why should one be more capable than the other ?

---

### Post by bailout on 2012-09-05
I don't know whether it has been mentioned yet but afaik it still isn't possible to update an installed system from the live cd. I have 5 kubuntu systems and even with broadband that is a lot of downloading to update those over the net. Instead I can dl one alt cd and run the update from that.

---

### Post by grahammechanical on 2012-09-05
Regarding this worry:

> There probably should be an answer how to install Ubuntu 12.10 on hardware where GUI installer fails and until Ubuntu 12.10 the answer was try alternate CD and it usually worked. Now the answer is you can't but we will try to make GUI installer work better? The problem as i see it is not GUI vs. text installer but what should be the answer when GUI installer fails? Will GUI installer gain new "compatibility mode"? How to install Ubuntu 12.10 on hardware if GUI installer fails and you know Ubuntu will probably work once you install it and enable additional drivers i solved this issues until Ubuntu 12.10 with alternate CD and how should i solved them until GUI installer improves and does not fail a lot of times? No real answer i guess and at least OK i hope until Ubuntu 14.04 GUI installer will just work!

I have just had a confirmation email that the Precise Alternate CDs will still be available and updated with point releases. So, it will be possible to install Precise (which is LTS for 5 years anyway) using an Alternate CD and then do a distribution update to 12.10.

I just hope that someone sensible is taking note of all these concerns and is going to put clear directions about all of this on the download page.

People get so used to working a process that they become part of the process and cannot respond to situation changes but continue in the same old way. I hope that is not happening here.

Ubuntu is changing and the way it is developed needs to change.

Regards.

---

### Post by mips on 2012-09-05
I did a netinstall yesterday and for me it's not ideal.

Something that would be great though is an alternate cd that just contains the minimal stuff to get a base system running without pulling all those packages of the net (my netinstall bombed once and I hit the roof). You can even add a option to the menu to pull down the full *buntu-desktop meta package of your choice if you so desire.

---

### Post by jerrylamos on 2012-09-05
> **grahammechanical said:**
> Ubuntu is changing and the way it is developed needs to change.Regards.So far as I can tell, it has never occurred to Development that install should be lead pipe simple and iron bound solid.  Do its job and get out of the way.  Otherwise people will move on.

My impression is they are decorating Ubiquity to be a fancy (well, relatively) marketing tool with usual exposure the gui's will fail on some configurations since Ubiquity doesn't have nearly the full support and recovery that the installed Ubuntu does.  I guess Ubuntu isn't interested in those people.

Now in the depths of Alpha-Beta-RC it can be hard to see how it will all come out.

For me over the last 6 years I've been able to find some way to work around whatever and keep going - but as a tester I'm far from their target market whatever that is.  I'd really like lead pipe simple and iron bound solid so I can get on to testing Ubuntu itself, not Ubiquity.

---

### Post by stoneguy on 2012-09-05
> **jerrylamos said:**
> but as a tester I'm far from their target market whatever that is

Jerry raises a disturbing point. Why are the likes of us doing testing? When I worked for a scientific development organization, we didn't use clerical staff to test products. We used scientists and engineers.

I suspect that we testers are more like one another than members of the target market that Canonical seems to be aiming for. I'm not saying they have a bad idea. It's their decision on how to best monetize their efforts, and it's unlikely that the path is by targetting the likes of us. The Linux bundlers and upstreams would be better off testing using their intended market.

---

### Post by vexorian on 2012-09-05
Power users are always the guys who do all the beta testing for the OS/X, the windows, the androids and the ioses. The choice to take this sample bias into consideration or to completely miss it, is up to the guys making the decisions.

---

### Post by ramsharan065 on 2012-09-05
RAID is not bad thing to have in Desktop.

---

### Post by sammiev on 2012-09-06
Well it's Sept 06 here. So we will soon find out with Beta1. :) ( I can't wait )

---

### Post by cariboo on 2012-09-06
> **sammiev said:**
> Well it's Sept 06 here. So we will soon find out with [s]Alpha1[/s]. :) Beta 1 ( I can't wait )

Fixed that for you. :)

---

### Post by sammiev on 2012-09-06
> **cariboo907 said:**
> Fixed that for you. :)

Thank You Sir!!! So sorry. :( Bring on Beta1. ):P

---

### Post by mörgæs on 2012-09-06
> **The Cog said:**
> I think it would be far mode sensible to drop the graphical installer from the live CD. Just refer to the "alternate" CD as the "installer" CD. This way, the live CD can be used purely as a live CD - testing that things work etc. And the installer CD will be a rock-solid full-featured installer. If you want to test, use the live CD. If you want to install then use the installer CD. 

I really don't understand why they want to enforce using the less reliable and less feature rich graphical installer, unless it is in order to sell advertising space on the graphical installer's slide show.

+1

Yes, why is so much effort being put into Ubiquity, which serves the user for about 20 minutes during install? Giving Ubiquity even more attention while so many other packages could use some does not seem logical to me.

---

### Post by jerrylamos on 2012-09-06
> **mörgæs said:**
> +1

Yes, why is so much effort being put into Ubiquity,... 
I beg to differ.  Apparent to me development exhibits relatively little effort to getting Ubiquity to run on most any configuration that will run ubuntu.  Many times for many of us alternate has worked when Ubiquity was flat on its face (your choice of anatomy).  As in the case of Unity looks like there's a lot of attention on eye candy instead of function. "If it doesn't run our code run something else" to paraphrase development.  So I do.  Oh, well, their code, their choice.

---

### Post by mips on 2012-09-06
> **jerrylamos said:**
> Many times for many of us alternate has worked when Ubiquity was flat on its face (your choice of anatomy).

The alternate is my personal choice for this very reason.

---

### Post by ronacc on 2012-09-06
I have made this point before and I will make it again . I think that the entire live installer needs a rework from the ground up . I have tested Ubuntu almost from the start and without a doubt the greatest grief I have had over the years has been from Ubiquity . The partitioner in particular has been a very sore point with me , to the point that I will only use it to actually partition a drive on a completely clean box with no other install that I would not want to lose . Another glaring problem I have had is that often the live session will perform perfectly but an install from it won't even boot or if it does only works correctly after further configuration , this is an inconstancy that makes no sense . Another little annoyance is that an aborted install (before the actual install begins IE during selection ) requires a reboot to start over from scratch ( the previous settings are not forgotten and may not be changeable ) . In short it is best IMHO to scrap the whole thing and do a complete rewrite .

---

### Post by kansasnoob on 2012-09-06
Something I thought worth mentioning, in case someone else wants to file a bug regarding it, the live installer lacks a clear option to "Use largest continuous free space" whereas that option is present in the alternate ;)

---

### Post by vexorian on 2012-09-06
Question: Can't the most tech proficient guys who still want alternate to work volunteer to develop it?

Anyway, I like ubiquity because it has gparted. Gparted is better at that partion stuff than both alternate and ubiquity's partitioner.

---

### Post by cariboo on 2012-09-06
> **vexorian said:**
> Question: Can't the most tech proficient guys who still want alternate to work volunteer to develop it?

Anyway, I like ubiquity because it has gparted. Gparted is better at that partion stuff than both alternate and ubiquity's partitioner.

I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.

---

### Post by mips on 2012-09-06
> **cariboo907 said:**
> I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.

I did that for 12.10 in the wee hours of yesterday morning. I prefer the alternate image though. The process is basically almost identical.

---

### Post by paul_in_london on 2012-09-06
> **cariboo907 said:**
> I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.

That's exactly what I do whenever I install from scratch.

The other benefit IMHO is that you can build up the system using only the packages you want/need.

EDIT: I saved this command as a "template" at one point (some of the packages have been renamed or superseded since then):

```
aptitude install --without-recommends xserver-xorg-core gdm gnome-session gnome-panel gnome-terminal \
gnome-themes gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork light-themes nvidia-current \
synaptic flashplugin-nonfree app-install-data gnome-applets gnome-panel-bonobo  gvfs-backends\
indicator-applet-appmenu  indicator-applet-complete indicator-application libasound2-plugins \
libgtk2-perl libpam-ck-connector notification-daemon notify-osd nvidia-settings \
pulseaudio python-gconf software-properties-gtk python-software-properties \
gnome-keyring indicator-appmenu indicator-me indicator-messages indicator-session \
indicator-sound notify-osd-icons pulseaudio-esound-compat pulseaudio-module-x11 \
appmenu-gtk indicator-applet-session libpam-gnome-keyring python-indicate
```

---

### Post by jerrylamos on 2012-09-06
> **cariboo907 said:**
> I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.
Been a while since I tried the mini-iso.  At my relatively inexpensive 1.5 MB internet connection it took much much longer than a zsync does.

Plus there were a pile of packages and I forgot some for the usual ubuntu build.

Well, maybe Beta Ubiquity will work, maybe not.

---

### Post by kansasnoob on 2012-09-06
> **cariboo907 said:**
> I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.

The one major problem with the mini.iso is the lack of wireless support. In those cases where no wired connection is available I find performing a CLI install using an alternate image is a better option.

And alternate images do still exist for Xubuntu and Lubuntu. So there are still fairly adequate options :)

---

### Post by vexorian on 2012-09-06
> **cariboo907 said:**
> I just used the mini.iso to do an install, it works exactly the same way as the alternate install iso, except the packages are downloaded from the repositories instead of the CD, or USB drive. I'm in the process of posting a run through on my blog, I'll post a link when I'm done.
Hmnn. I might use the mini-iso the next time. It is tiresome to uninstall all packages I don't use and thanks to updates you are going to download everything again anyway.

---

### Post by ronacc on 2012-09-06
> **mörgæs said:**
> +1

Yes, why is so much effort being put into Ubiquity, which serves the user for about 20 minutes during install? Giving Ubiquity even more attention while so many other packages could use some does not seem logical to me.

because that 20 minutes is THE MOST CRITICAL to a new user , if the installer doesn't work flawlessly we have probably lost them forever . I started using linux back in the mid ninety's with Caldera open linux 1.0 . You got a bunch of cd's with the kernel LILO and a few libs and several disks of sources , so why do I bother about the graphical installer ? because that is the first thing that most 1st time users will interact with . Can you really see a prospective convert from windows , who may never have even seen a console window in his life , dealing with a cmd line installer ?

---

### Post by vexorian on 2012-09-06
> **ronacc said:**
> because that 20 minutes is THE MOST CRITICAL to a new user , if the installer doesn't work flawlessly we have probably lost them forever . I started using linux back in the mid ninety's with Caldera open linux 1.0 . You got a bunch of cd's with the kernel LILO and a few libs and several disks of sources , so why do I bother about the graphical installer ? because that is the first thing that most 1st time users will interact with . Can you really see a prospective convert from windows , who may never have even seen a console window in his life , dealing with a cmd line installer ?
Few people seem to figure this out, but the text installer is new-user-repellent. Yes, it works, and that is very cool when you are already a veteran Linux guy. But for new users, the first impression will be "this not looking very modern right now" and the second impression will be "how do you even use this awful MSDOS thing!!!???"

---

### Post by cariboo on 2012-09-06
> **jerrylamos said:**
> Been a while since I tried the mini-iso.  At my relatively inexpensive 1.5 MB internet connection it took much much longer than a zsync does.

Plus there were a pile of packages and I forgot some for the usual ubuntu build.

Well, maybe Beta Ubiquity will work, maybe not.

I used to do net installs using dialup before broadband was available in my area, it is doable.

> **kansasnoob said:**
> The one major problem with the mini.iso is the lack of wireless support. In those cases where no wired connection is available I find performing a CLI install using an alternate image is a better option.

And alternate images do still exist for Xubuntu and Lubuntu. So there are still fairly adequate options :)

I just did a quick walk through in vbox, and posted it [here]("http://cariboo907.blog.com/"), or you can have a look at it on the [Planet]("http://planet.ubuntu.com/"). 

I'm going to create some room on a mostly unused hard drive, and try the install using a supported wireless device. If it doesn't work, it's time to create a bug. I noticed the Debian netinst image is about 168MiB so I'm assuming it has wireless support built-in, so Ubuntu should have it too.

---

### Post by kansasnoob on 2012-09-06
> **cariboo907 said:**
> I used to do net installs using dialup before broadband was available in my area, it is doable.



I just did a quick walk through in vbox, and posted it [here]("http://cariboo907.blog.com/"), or you can have a look at it on the [Planet]("http://planet.ubuntu.com/"). 

I'm going to create some room on a mostly unused hard drive, and try the install using a supported wireless device. If it doesn't work, it's time to create a bug. I noticed the Debian netinst image is about 168MiB so **[COLOR="Red"]I'm assuming it has wireless support built-in, so Ubuntu should have it too.[/COLOR]**

Quite true! That's really the only problem I'm aware of with the mini.iso. Otherwise it's a very practical option because once the installation is complete you already have the newest packages available :D

---

### Post by ventrical on 2012-09-06
@ cariboo

Looks almost identical to alternate.

Thanks!

---

### Post by mips on 2012-09-06
> **cariboo907 said:**
> I noticed the Debian netinst image is about 168MiB so I'm assuming it has wireless support built-in, so Ubuntu should have it too.

[http://www.debian.org/CD/netinst/#businesscard-stable](http://www.debian.org/CD/netinst/#businesscard-stable)
> What types of network connections are supported during installation? 

The network install assumes that you have a connection to the Internet. Various different ways are supported for this, like analogue PPP dial-up, Ethernet, WLAN (**with some restrictions**), but ISDN is not — sorry!

No idea what those restrictions are though.

---

### Post by cariboo on 2012-09-06
> **mips said:**
> [http://www.debian.org/CD/netinst/#businesscard-stable](http://www.debian.org/CD/netinst/#businesscard-stable)


No idea what those restrictions are though.

I actually have a copy of the Debian netisnt iso here, I haven't had a chance to try it to see if my wireless devices work with it. 

I tried the mini.iso a bit earlier with a supported wireless device, and it was a failure. I created a bug report, and I am currently dealing with the Brad Figg bot.

Bug #[lpbug]1047092[/lpbug]

---

### Post by mips on 2012-09-07
Anybody know how hard it is to remaster the mini/netinstall iso?

Here is what I want to do, once 12.10 is official I would like to copy all my packages in /var/cache/ap to the cd so I can do a full install of the cd without it having to pull them off the net.

Is this possible and how would one do it?

---

### Post by cariboo on 2012-09-07
This is a little update on my experiment. Wireless won't work with the mini.iso or the Debian netinst iso due to missing firmware for wireless devices. I will continue to pursue this, as even if we try to discourage new users from using them, there is still a need for it in order to get a working desktop on some of the newer hardware.

I've also found that at least one laptop that I know of is sold without an ethernet port (my fathers Acer laptop). The company I work for sells computers, so I'll do a survey at work to see how prevalent this is amongst new laptops.

---

### Post by cariboo on 2012-09-15
This is an update on the status of wireless and the mini/netinst iso. Bug #[lpbug]1047092[/lpbug]

> This bug was fixed in the package linux-firmware - 1.92

---------------
linux-firmware (1.92) quantal; urgency=low

  * Add zd1201.fw and zd1211/* to nic-firmware.lst
    -LP: #1047092
 -- Leann Ogasawara <leann.ogasawara@canonical.com> Fri, 14 Sep 2012 06:22:04 -0700

---

