---
title: "Selecting a tool to create USB boot drives from ISO files"
date: 2015-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by sudodus on 2015-08-24
Which tool to create USB boot drives from ISO files would you like to include in Ubuntu and the Ubuntu family of operating systems?

There have been problems for years with the Ubuntu Startup Disk Creator alias usb-creator-gtk. There is also Disks, but it is not advertized much for this purpose. And there are cp and dd, if you want to do it 'without safety belt'. These alternatives can only make 'live only' pendrives.

So ***please participate in this poll in order to prepare for a discussion*** at the ubuntu-desktop mailing list and the corresponding forums ***where it can be decided*** for Kubuntu, Lubuntu, Ubuntu Gnome ... Xubuntu

You find the corresponding discussion in the following thread [Discussion: Selecting a tool to create USB boot drives from ISO files](http://ubuntuforums.org/showthread.php?t=2289225)

***Edit:*** You may want to select two alternatives, one which only makes 'live only' pendrives, and one which can make 'persistent live' pendrives.

---

### Post by ajgreeny on 2015-08-24
I have used SDC, unetbootin, dd and what you have called "Grub-n-iso Boot" with complete success, though the way I use the latter, it is limited only to certain iso files, mostly related to Ubuntu in some way; perhaps other iso files also work fine if you fully understand the way in which that system works and make appropriate changes, which I am happy to admit, I do not know enough about to do.

Overall I would think that unetbootin is probably the easiest to use for beginners, but I've never tried any of the others you mention so it is not for me to either choose them in the poll, or make comments here in this post; I can only "speak as I find".

I note the poll does not even offer the possibility of getting SDC to work properly as it used to;  I am pretty sure from what I recall that it still does fine in 14.04, but I can't really remember when I last used SDC so I may be wrong about that.

---

### Post by sudodus on 2015-08-24
> **ajgreeny said:**
> I have used SDC, unetbootin, dd and what you have called "Grub-n-iso Boot" with complete success, though the way I use the latter, it is limited only to certain iso files, mostly related to Ubuntu in some way; perhaps other iso files also work fine if you fully understand the way in which that system works and make appropriate changes, which I am happy to admit, I do not know enough about to do.

Overall I would think that unetbootin is probably the easiest to use for beginners, but I've never tried any of the others you mention so it is not for me to either choose them in the poll, or make comments here in this post; I can only "speak as I find".

I note the poll does not even offer the possibility of getting SDC to work properly as it used to;  I am pretty sure from what I recall that it still does fine in 14.04, but I can't really remember when I last used SDC so I may be wrong about that.

In your situation, I would vote for Unetbootin. When you write that voting is not for you, I think very few people will feel that they know enough to vote.

Or maybe the poll is set up in a bad way?

There are still bugs with the Startup Disk Creator, SDC. It has been buggy for several years now in spite of many efforts to debug it by dedicated people. If you know how to use it, it works, but some things do not work. I think it was made in such a way, that when Ubuntu changes between versions, there are things that stop working in the SDC.

---

### Post by PaulW2U on 2015-08-24
I'm not sure I have much that I can add here but I too would like to see the option of SDC being retained with obviously a major overhaul so that as many bugs are fixed as possible. I'm used to its GUI having used it for five years now but appreciate the problems that have been seen when creating live USBs for versions of Ubuntu other than in which they were created.

I've just downloaded a couple of Wily images and used UNetbootin, mkusb and mkusb-nox to have a look at the latest Xubuntu and Ubuntu GNOME development version. I much prefer the GUI for Unetbootin but both the outdated version in the repository and the latest version in the official PPA produced something that I could not boot.

Both mkusb and mkusb-nox worked perfectly. I like the simplicity of the console version although I think I need to use it a few times to be confident of actually writing to my USB device and not my hard drive :)

As I've never heard of most of the other options in the poll I'll vote for mkusb and Unetbootin (on the basis that it has always worked previously).

---

### Post by QDR06VV9 on 2015-08-24
Kind of fun here to see different results using unetbootin 
In precise12.04)   unetbootin would work 80 to 90% of the time on trusty(14.04) I am lucky to get any thing to boot installer or live.
@sudodus I am assuming our votes were counted from the other thread!
If not I will come back and vote.
Regards

---

### Post by sudodus on 2015-08-24
> **PaulW2U said:**
> I'm not sure I have much that I can add here but I too would like to see the option of SDC being retained with obviously a major overhaul so that as many bugs are fixed as possible. I'm used to its GUI having used it for five years now but appreciate the problems that have been seen when creating live USBs for versions of Ubuntu other than in which they were created ...

This option (to wait for the SDC to be debugged) has been selected and worked along for years (longer than the time since Trusty was released). Many of us have given up the hope that the SDC will ever work properly. But on the other hand, the result of this poll will not automatically make any change. People can and will argue for the SDC at the deciding forums (for standard Ubuntu, Kubuntu, ..., Xubuntu).

Maybe the result of these efforts at the Ubuntu Forums will be that the SDC is replaced, maybe the result will be much more emphasis on really debugging and back-porting the SDC, so that it will work from older versions to newer versions, and both of these results are good.

---

### Post by sudodus on 2015-08-24
> **runrickus said:**
> Kind of fun here to see different results using unetbootin 
In precise12.04)   unetbootin would work 80 to 90% of the time on trusty(14.04) I am lucky to get any thing to boot installer or live.
@sudodus I am assuming our votes were counted from the other thread!
If not I will come back and vote.
Regards

I have tried to extract all alternatives mentioned in the other thread. I could count the 'votes', but I cannot add them into this poll, because I can only enter my own vote. So please come back and vote here.

I will try to keep the discussion alive (here and/or in the other thread) and posts discussing details will certainly count, when we try to come to a conclusion. We cannot rely blindly on the result of poll.

---

### Post by sudodus on 2015-08-24
> **ajgreeny said:**
> ...

I note the poll does not even offer the possibility of getting SDC to work properly as it used to;  I am pretty sure from what I recall that it still does fine in 14.04, but I can't really remember when I last used SDC so I may be wrong about that.

> **PaulW2U said:**
> I'm not sure I have much that I can add here but I too would like to see the option of SDC being retained with obviously a major overhaul so that as many bugs are fixed as possible. I'm used to its GUI having used it for five years now but appreciate the problems that have been seen when creating live USBs for versions of Ubuntu other than in which they were created.

...

I found out that I could edit the poll and add the option "Edit: Keep the Startup Disk Creator, it is the best alternative". It will be interesting to find out how many votes it will get :-P

Edit: I added this SDC option, when (only) 7 people had voted.

---

### Post by cariboo on 2015-08-24
I use dd and Disks, most of the time, I'm not really happy with the results using unetbootin, but it does work every time.

---

### Post by ventrical on 2015-08-24
I pointed out once before - that I do use SDC in a MM 10.10 ubuntu - install and it works just fine there. In the meantime I use 'disks' (as which was recommended during the Utopic cycle), is very reliable and I can also 'restore' a complete and bootable *snappy* image to harddrive using a USB docker and then take that hard drive and boot it on any PC with the appropiate graphics hardware. Also mkusb for installing 'live' and persistent selectable .ISOs side by side.

Regards..

---

### Post by sudodus on 2015-08-28
Bump :-)

There must be more people who want to share their opinion about tools to create USB boot drives from ISO files, and help us suggest a good tool (to replace the Startup Disk Creator, or tell us that you like it and want to keep it).

If you haven't voted in the poll and/or replied yet, please vote and let us know what you use and why you prefer that tool. It helps if you also tell us what tool you would recommend to a beginner.

---

### Post by mikodo on 2015-08-28
Hmm ...

I have never used any of these tools, to make a boot-able USB drive. For some unknown reason, this machine doesn't provide USB .iso booting. Yep, I'm familiar with the [PLOP]("https://www.plop.at/en/ploplinux/index.html") utility but, I get along fine with using CD/DVD's on this desktop machine.  So, I just use those.

That, makes me a beginner then. Yay!  I get to choose what I would like to see, used.

I would like to see dd used, with a succinctly smallish guide.

---

### Post by kansasnoob on 2015-08-28
> **sudodus said:**
> This option (to wait for the SDC to be debugged) has been selected and worked along for years (longer than the time since Trusty was released). Many of us have given up the hope that the SDC will ever work properly. But on the other hand, the result of this poll will not automatically make any change. People can and will argue for the SDC at the deciding forums (for standard Ubuntu, Kubuntu, ..., Xubuntu).

Maybe the result of these efforts at the Ubuntu Forums will be that the SDC is replaced, maybe the result will be much more emphasis on really debugging and back-porting the SDC, so that it will work from older versions to newer versions, and both of these results are good.

I doubt we'd convince Ubuntu to change but we might be able to push for replacing S-D-C as a default app in some of the flavors. The flavor leads are much more likely to listen to common sense, or one of them might just take on the task of rebuilding S-D-C.

---

### Post by kurt18947 on 2015-08-28
Unetbootin has an advantage IMO in that it is multi-platform. The curious don't have to use one app to download and create using Windows and another using Ubuntu.

---

### Post by C.S.Cameron on 2015-08-28
I have always liked UC/SDC as it is right there when Ubuntu is downloaded.
Sometimes old UNetbootin does not work with latest Ubuntu
I wish that usb-creator.exe still came on the disk though to make it easier for Windows users to try Ubuntu.
MultiBootUSB is handy for making multi disks.

---

### Post by flocculant on 2015-08-29
> **kansasnoob said:**
> I doubt we'd convince Ubuntu to change but we might be able to push for replacing S-D-C as a default app in some of the flavors.

Unlikely to happen when it's from a PPA or a random place on the internet.

> **kansasnoob said:**
>  The flavor leads are much more likely to listen to common sense, or one of them might just take on the task of rebuilding S-D-C.

Most flavours are not blessed with an enormous amount of people available to do what they want for them - why would they fix something for Canonical?

---

### Post by flocculant on 2015-08-29
> **sudodus said:**
> ...

Maybe the result of these efforts at the Ubuntu Forums will be that the SDC is replaced, maybe the result will be much more emphasis on really debugging and back-porting the SDC, so that it will work from older versions to newer versions, and both of these results are good.

How many people have responded? 

Is there a sensible bug on Launchpad about this? 

Given that the general comment is "This is run and used by volunteers not Canonical" - why do you think this is actually going to make any difference?

---

### Post by kansasnoob on 2015-08-29
> Is there a sensible bug on Launchpad about this? 

Yep:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

But the proposed "fix" resulted in this:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646)

My final comment on that bug was here:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146)

S-D-C is borked - it's useless to create live USB's of either older or newer versions of Ubuntu than the version you're running S-D-C on. And the proposed fix that made it into Vivid and got backported into Utopic resulted in S-D-C being able to only produce live USB's of the same architecture.

---

### Post by kansasnoob on 2015-08-29
> **flocculant said:**
> Unlikely to happen when it's from a PPA or a random place on the internet.



Most flavours are not blessed with an enormous amount of people available to do what they want for them - why would they fix something for Canonical?

Unetbootin is already in the repos, and some (possibly all) flavors have gnome-disk-utility installed by default so those two are true options. Each would just require some rewriting of "help" docs, wiki pages, etc.

The flavors can fairly easily swap Ubuntu's default apps with apps of there liking. Of course the process is more complex if the new app needs to be added to the repos, but it happens all the time.

---

### Post by sudodus on 2015-08-29
> **flocculant said:**
> [QUOTE=kansasnoob;13346232]I doubt we'd convince Ubuntu to change but we might be able to push for replacing S-D-C as a default app in some of the flavors.
Unlikely to happen when it's from a PPA or a random place on the internet.
[/QUOTE]
I think the tool that would replace the Startup Disk Creator must be wrapped into an official package and maintained in a reliable way. And this can happen if there is a decision to do it - to put the effort into a new tool, that is likely to work better and with less maintenance due to a better basic concept, instead of putting more effort into the Startup Disk Creator, which does not work in spite of trying hard to repair it for years.

Right now ***Unetbootin*** is leading in the poll. The version in the developer's PPA works well, but the version in the Ubuntu repositories is old and buggy. I think it would be a rather small effort for Canonical to keep Unetbootin up to date in the repositories.

I am developing and maintaining ***mkusb***, and I intend to continue. If Canonical wishes, I could even make a simplified version, which is easier to maintain, but keeps the all the important features. mkusb is programmed in bash and uses standard tools and is easy to maintain across Ubuntu versions, much easier than the SDC.

The alternative to 'advertize ***Disks***' as the main tool to create USB boot drives is very straightforward and would be the most convenient way to go for Canonical. Then the users who want persistent live systems can use the available tools like today, but without getting frustrated with the SDC before they find a working tool.

-o-

I am also aware of the bugs described by kansasnoob. Furthermore, the SDC has also failed to erase the target drive. I don't know if that bug has received an own bug report, and I think it is not squashed yet.

---

### Post by flocculant on 2015-08-29
> **kansasnoob said:**
> Yep:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

But the proposed "fix" resulted in this:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646)

My final comment on that bug was here:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146)

S-D-C is borked - it's useless to create live USB's of either older or newer versions of Ubuntu than the version you're running S-D-C on. And the proposed fix that made it into Vivid and got backported into Utopic resulted in S-D-C being able to only produce live USB's of the same architecture.

Sorry - I didn't make myself clear :) I meant something somewhere to start the 'get rid of sdc and replace it' ball rolling. 

As you're more than aware, a thread here is not ever going to be sufficient.

---

### Post by flocculant on 2015-08-29
> **kansasnoob said:**
> ...
The flavors can fairly easily swap Ubuntu's default apps with apps of there liking. Of course the process is more complex if the new app needs to be added to the repos, but it happens all the time.

> **sudodus said:**
> I think the tool that would replace the Startup Disk Creator must be wrapped into an official package and maintained in a reliable way. And this can happen if there is a decision to do it - to put the effort into a new tool, that is likely to work better and with less maintenance due to a better basic concept, instead of putting more effort into the Startup Disk Creator, which does not work in spite of trying hard to repair it for years.

...

I am developing and maintaining ***mkusb***, and I intend to continue. If Canonical wishes, I could even make a simplified version, which is easier to maintain, but keeps the all the important features. mkusb is programmed in bash and uses standard tools and is easy to maintain across Ubuntu versions, much easier than the SDC...

I know you are :) 

Yes. 

But having something people can add to *test* is a completely different thing than something which could need to be in seed for at least 3 years (in the case of at least one flavour LTS) 

Not sure how other flavours do so - but we'd discuss it within the team and make a decision. Something in a PPA is going to start disadvantaged.

All I'm saying is that for this (if you want to try) to be used in flavours seeds - it really needs to not be in PPA, which means getting it into repos.

---

### Post by Mike_Walsh on 2015-08-29
Hi, sudodus. Thought I'd add my two-penn'orth here. 

I've always found UNetbootin to work fine. I used it to install Xubuntu on the old Dell.....and you're aware how smoothly that went.

The other one I like using is Multi-Boot. It's the only one that would work for when I wanted to try out ZorinOS a year or so ago.....none of the others seemed to function for me at the time. I've used it a few times since.

Another one we use on the Puppy Forums is isobooter. I don't know if you've come across this one?


Regards,

Mike. ;)

---

### Post by sudodus on 2015-08-29
> **flocculant said:**
> Sorry - I didn't make myself clear :) I meant something somewhere to start the 'get rid of sdc and replace it' ball rolling. 

As you're more than aware, a thread here is not ever going to be sufficient.

We know, but we start here. This is a good place to find out what works for different people and different tasks. We can also find out if there is actually a silent majority of people who use the Startup Disk Creator and are happy with it ;-) How important are the known bugs?

When we are ready we can approach the forums that decide what software to use in standard Ubuntu and any of the Ubuntu flavours.

-o-

- It is a surprise for me that ***cp*** and ***dd*** 'without safety belt' get such high score. I would guess that the percentage will decrease, when the number of votes increases.

- ***Disks*** is probably not known (and used) for this purpose by many people. It is doing the same cloning as cp, dd and mkusb, safer than cp and dd, but with less bells and whistles than mkusb. There is no way to make persistent live systems, but maybe that is not necessary. Maybe it is enough that it is safe (very few drives overwritten by mistake), reliable (high success rate making working boot drives) and easy to use.

- I am not surprised that ***Unetbootin*** has the highest score. It is well known and used by many people for several years.

---

### Post by kansasnoob on 2015-08-29
> **flocculant said:**
> Sorry - I didn't make myself clear :) I meant something somewhere to start the 'get rid of sdc and replace it' ball rolling. 

As you're more than aware, a thread here is not ever going to be sufficient.

The purpose of this poll and [its predecessor]("http://ubuntuforums.org/showthread.php?t=2289225") in the dev section of the forums is to get opinions and ideas. Then we can introduce those ideas through the proper channels. Such "proper channels" vary from flavor to flavor. Sudodus does a lot of testing for Lubuntu whereas I do a lot of testing for Ubuntu GNOME, so we have a pretty good idea who (and how) to approach with such an issue.

ATM I've yet to even convince myself which way is the right way to go. I'm leaning towards just including [instructions for using gnome-disk-utility]("http://fedoramagazine.org/how-to-make-a-live-usb-stick-using-gnome-disks/") to create a live USB and then recommending unetbootin for creating live w/persistence.

---

### Post by sudodus on 2015-08-29
> **Mike_Walsh said:**
> Hi, sudodus. Thought I'd add my two-penn'orth here. 

I've always found UNetbootin to work fine. I used it to install Xubuntu on the old Dell.....and you're aware how smoothly that went.

The other one I like using is Multi-Boot. It's the only one that would work for when I wanted to try out ZorinOS a year or so ago.....none of the others seemed to function for me at the time. I've used it a few times since.

Is this ***Multi-Boot*** the same as MultibootUSB in the poll, or another tool? [MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk](http://ubuntuforums.org/showthread.php?t=1518273)
> 
Another one we use on the Puppy Forums is isobooter. I don't know if you've come across this one?

Regards,

Mike. ;)

Is Puppy's ***isobooter*** a cloning tool, or does it create partition(s) and file system(s), copy files from the ISO file and edit the boot configuration (like for example Unetbootin)?

---

### Post by Mike_Walsh on 2015-08-29
Hallo, sudodus.

Yes, sorry about that; didn't quite make myself clear there.

Multi-Boot USB as mentioned in the poll.

As for isobooter, I'll give you a link to the thread on the Puppy Forums, and you can have a read up about it yourself. I forget off the top of my head just how it** does** work, now; never worried too much about it as long as it **did** the job. I find it has about a 70% success rate; it's really picky about the flash drive in use.....it's even turned its nose up at the SanDisk Cruzer 'Blades' that I favour on more than one occasion...!

Here you go:-

[http://www.murga-linux.com/puppy/viewtopic.php?t=67235](http://www.murga-linux.com/puppy/viewtopic.php?t=67235)

Bill (rcrsn51) can explain it a lot better than I can. There's mention of what I told you about once before; the on/off project for booting isos directly from their iso files, using GRUB2. I'm really not certain what's happening with that; after over a year there's still sizeable chunks of the forum that I haven't explored yet..!

The 'Universal Installer' included with every Puppy does a marvellous job of installing the system to USB stick in 'frugal' mode (just a handful of squash filesystem 'files', installed in 'read-only' mode; BK (Barry Kauler) perfected that **years** ago).....but it won't create a Live USB. The LiveCD works in exactly the same way as the 'buntu ones.

I use UNetbootin in Puppy for this **very **reason. Download the zip package from SourceForge, extract, and simply run the single executable.....couldn't be simpler; and run it from the terminal.


Regards,

Mike. ;)

---

### Post by sudodus on 2015-08-29
Thanks Mike :-)

[QUOTE=Bill (rcrsn51)]ISObooter is a procedure for booting many Linuxes, including Puppy, directly from their ISO files. It is based on Scooby's work here.

ISObooter is primarily intended for use with USB drives, but also works on hard drives. It uses Grub4Dos as the bootloader. [/QUOTE]

OK, it seems to be what I call a 'grub-n-iso' system which identifies several distros and applies the correct boot commands in grub.cfg :-)

---

### Post by Mike_Walsh on 2015-08-29
Hi again, sudodus.

Y'see, this is where I come unstuck..! Grub4DOS, which is what's used widely with the Puppy systems, is nice'n'simple; even a complete fool like me can understand it. GRUB2, by comparison, is, ummm.....complicated. (I'm **not** going to swear, although trying to figure it out has had me on the point of doing so more than once...) :lol:

Perhaps I'm not 'logically minded'... :roll::D

BTW: My mistake, in the last post. I meant Multisystem, NOT MultibootUSB. In point of fact, I believe it was you who recommended I try it; at the time, I was getting no joy on the Zorin forums, although I've since discovered that it's the same one they recommend themselves for a USB install. And it did work, nicely.....after the mini-nightmare of actually getting it installed ( but that's a **whole** 'nother story.....and this thread isn't the place for it.)

MultiSystem was originally obtained from here:-

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

My original problems centred around not, at the time, being able to get a translation from the French..!


Mike.

---

### Post by monkeybrain20122 on 2015-08-29
As far as I know if you use dd you can only put one OS in the usb stick and afterwards to reuse it you have to dd again (merely reformat doesn't work) Unetbootin has the same problem of one OS only and it would be a waste if I have a big usb stick (at least 8 G nowadays) and as far as I know it is not easy to make live usb with persistence with unetbootin. Startup disk only supports Ubuntu. 

So my choice is multisystem overwhelmingly. You can make a multiboot usb with as many OS as can be fitted into the stick. It supports a lot of different distros, it is easy and safe to use (unlike dd) It allows persistence but only for one of the OS, so that may be a small shortcoming but still more powerful than all the other tools mentioned above.

---

### Post by monkeybrain20122 on 2015-08-29
> **Mike_Walsh said:**
> 

My original problems centred around not, at the time, being able to get a translation from the French..!
.

The website is in French but the interface of multisystem is in English. You can read the website using google translate addon for Firefox or use Chrome.

But really what you need is [http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)
the commands hardly need translation
 
I was told about multisystem some years ago by the dev of LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) I just started using Ubuntu and was interested in trying out different distros and LILI seemed to be a perfect tool, but it works only on Windows. I wrote him to ask why there was no Linux version, his reply was that there was already something better in Linux, which was multisystem :) (at that time it had a different name)

---

### Post by sudodus on 2015-09-04
Bump :-)

Maybe you have returned from summer holiday now and want to share your opinion. Help us suggest a good tool to create USB boot drives from ISO files (to replace the Startup Disk Creator, or tell us that you like it and want to keep it)!

If you haven't voted in the poll and/or replied yet, please vote and let us know what you use and why you prefer that tool. It helps if you also tell us what tool you would recommend to a beginner.

---

### Post by kansasnoob on 2015-09-04
> **sudodus said:**
> Bump :-)

Maybe you have returned from summer holiday now and want to share your opinion. Help us suggest a good tool to create USB boot drives from ISO files (to replace the Startup Disk Creator, or tell us that you like it and want to keep it)!

If you haven't voted in the poll and/or replied yet, please vote and let us know what you use and why you prefer that tool. It helps if you also tell us what tool you would recommend to a beginner.

+1 :D

I was just going to check and see what was up, but you beat me to it.

---

### Post by sudodus on 2015-09-04
By the way kansasnoob,

There is a 'console window' in mkusb. Do you think it scares beginners and those who are used to pure GUI interfaces?

---

### Post by timothylegg on 2015-09-05
I never could comprehend why not just release a .img file and skip the installer process and eliminate a lot of forum space on people asking why the conversion didn't work on their [OS] [Version] running on [Hardware] with a [name of expensive video card].

Especially considering that CD/DVD drives on computers are becoming less common.  I personally haven't owned one for two years.

Look, debian.org is even doing it (and that really pisses me off):

[https://www.debian.org/distrib/netinst](https://www.debian.org/distrib/netinst)

I find it very annoying that they are competing by providing an additional service that Ubuntu won't.  Ubuntu is superior in so many ways and I want it to be easier for new users.  I have tried a number of those image conversion techniques and found poor results in their effectiveness.  The emulator approach is the only one I found failsafe.  The last three installations were actually done emulating a CD-ROM in qemu, installing onto a 8GiB image, dd that file onto the hard disk and then grew the ext partition to the whole disk.

If it's about hard disk space on the webserver, I'm willing to just buy the drive for you because storage can be expensive.  I remember very well how expensive 600MiB was back in 1995, but prices have gone down a little since then.  But it shouldn't affect the upstream data that much since people would likely download one of the other, depending on need.  If it is about storage, I recall seeing a half-terabyte WD passport at walmart on clearance last month.

---

### Post by sudodus on 2015-09-05
@timothylegg

Have you checked what is available the this link: [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com)? There is a netboot version of Ubuntu too :-) I haven't tried all alternatives, but maybe you can find something similar to what Debian can offer.

Anyway, I see your point. I have even supplied some compressed images of already installed systems. You find some of them at

[http://phillw.net/isos/linux-tools/compressed-images/](http://phillw.net/isos/linux-tools/compressed-images/) and [http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

They are easy to install with [mkusb](https://help.ubuntu.com/community/mkusb).

I have also created tarballs from installed systems, and they can be installed with the [One Button Installer](https://help.ubuntu.com/community/OBI). This method is developed further in [ToriOS](http://torios.net/) where it is used instead of the standard debian installer or ubiquity. But there is still a ToriOS ISO file to make it possible to install from a CD drive in old computers, that cannot boot from USB.

-o-

But I think the method with ISO files is standard since a long time, and it will probably survive for several more years.

---

### Post by nargaroth_reg on 2015-09-07
I use disks and unetbootin on linux. It would be nice to have a tool that supports multiboot available from the the official repositories but I think any of those two can already replace Startup Disk Creator. The best one I've found is called YUMI for windows ([http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)), it easily let me create a bootable usb with Fatdog, Tahrpup and Clonezilla, which are the distributions I use from live session most frequently. Unfortunately the linux version doesn't yet match the windows one. I didn't know about Multisystem, I'll try it.

---

### Post by sudodus on 2015-09-12
Bump :-)

How do you create your USB boot drives? Help us suggest a good tool to create USB boot drives from ISO files (to replace the Startup Disk Creator, or tell us that you like it and want to keep it)!

If you haven't voted in the poll and/or replied yet, ***please vote*** and let us know what you use and why you prefer that tool. It helps if you also tell us what tool you would recommend to a beginner.

---

### Post by sudodus on 2015-09-17
@ kansasnoob, mc4man, ventrical and everybody else willing to ***check for Startup Disk Creator bugs*** in various versions of *buntu and report the result:

> **Marc Deslauriers at Canonical]

On 2015-09-17 11:26 AM, Nio Wiklund wrote:
> Den 2015-09-17 kl. 16:35, skrev Marc Deslauriers:
>> Hi!
>>
>> On 2015-09-17 10:24 AM, Nio Wiklund wrote:
>>> Hi subscribers to the ubuntu-quality mailing list,
> ,,,
>
>> Care to elaborate what the many bugs are? I use it every single day for testing
>> security updates on real hardware and since bug 1279987 got fixed it's been
>> working great for me.
>>
>>>
> ...
>
>> Ideally it would also have both gtk and kde frontends, like usb-creator
>> currently has.
>>
>> Marc.
>
> Hi Marc,
>
> Elaborating on bugs and strange behaviour:
>
> kansasnoob:
>
> 1. Aside from SDC being badly borked one of the most annoying design
> flaws has always been the 10 minute timeout for installing the
> bootloader. I'm sure I'm not the only one that multi-tasks constantly,
> and not just at the desk. Watching and waiting for SDC to ask if you
> want to install the bootloader is about like watching paint dry
> ............... but if you get distracted for more than 10 minutes after
> SDC asks about bootloader installation you have to start all over again

[COLOR="#aa0000"]That's a one-line fix. Is there a bug opened for that issue?[/COLOR]

>
> 2. Bug numbers
>
> [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
>
> But the proposed "fix" resulted in this:
>
> [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1446646)
>
> My final comment on that bug was here:
>
> [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/146)
>
> S-D-C is borked - it's useless to create live USB's of either older or
> newer versions of Ubuntu than the version you're running S-D-C on. And
> the proposed fix that made it into Vivid and got backported into Utopic
> resulted in S-D-C being able to only produce live USB's of the same
> architecture.

[COLOR="#aa0000"]Bug 1325801 is being actively worked on.

Interesting, I can't reproduce bug 1446646. I can create both amd64 and i386
bootable usb disks for trusty and vivid on my vivid amd64 laptop.

Is there something special I need to do to reproduce your issue?[/COLOR]
>
> mc4man:
>
> s-d-c worked ok here on 14.04.1 but fails now on installing bootloader
> with 14.04.2/3. s-d-c does currently work in 15.10 (trying to create
> 14.04.3 image)
>
> sudodus - alias me, Nio:
>
> There is also a bug that makes it impossible to 'erase a disk'. I don't
> know if it has a bug number, but it is there at least in some of the
> current versions.

[COLOR="#aa0000"]That's probably a udisks issue. It would help to actually have a bug filed for it.[/COLOR]
>
> You see, there are too many bugs, that minor bug like the 'erase a disk'
> was not even reported. Once we thought it would be squashed when a bug

You've listed 4 bugs, two of which weren't even reported. I don't think that's
too many to simply fix.

> was being debugged, but it turned out to be independent of that bug, and
> I don't know of any bug report directed against it.
>
> -o-
>
> Concerning front-ends, they can be more or less independent of gtk and kde.
>
> mkusb uses bash + zenity + pv, which are available without importing
> heavy stacks of gtk or kde packages.

[COLOR="#aa0000"]I do hope you're not proposing to replace s-d-c with a bash script that needs
admin privileges and doesn't use udisks or policykit. That would be a non-starter.
[/COLOR]
>
> Disks belongs to gnome, I don't know if there is any corresponding
> built-in cloning tool in kde (not counting cp and dd).
>
> I don't know about Unetbootin and Multisystem and the other tools, how
> many packages they will bring. But we can find out.
>
> Unetbootin has versions for Windows and Mac OS too, which is an advantage.
>
> Best regards
> Nio
>

Marc.
[/QUOTE]

@ kansasnoob:

[I]1. "That's a one-line fix. Is there a bug opened for that issue?"

2. "Bug 1325801 is being actively worked on.

Interesting, I can't reproduce bug 1446646. I can create both amd64 and i386
bootable usb disks for trusty and vivid on my vivid amd64 laptop.

Is there something special I need to do to reproduce your issue?"
[/I]
@ mc4man:

*"That's probably a udisks issue. It would help to actually have a bug filed for it."*

@ sudodus (myself) :

[I]"I do hope you're not proposing to replace s-d-c with a bash script that needs
admin privileges and doesn't use udisks or policykit. That would be a non-starter."[/I]

-o-

It is not enough to ***tell*** the developers about the problems. We have to ***file bug reports***. Yes, we know.

He first blames ***udisks*** for the problems in the Startup Disk Creator, and then states that a tool that should replace it must use it (udisks). And why is it a non-starter to use ***sudo -H*** instead of ***policykit***? (I have seen that there are several problems, that are caused by the complicated policykit in more than one of the Ubuntu flavours.)

[QUOTE=Mathieu Trudel-Lapierre]
Le 2015-09-17 15:21, Nio Wiklund a écrit :
> Den 2015-09-17 kl. 19:08, skrev Mathieu Trudel-Lapierre:
[...]

> It seems that a fair fraction of those who have bothered to vote in the
> poll and / or written a detailed reply prefer Unetbootin. And I know
> that many of them have used it in many situations.
>
> There have been problems with it, for example the gfxboot.c32: not a
> COM32R Image boot bug (corresponding to #1325801 for the SDC). But it
> was quickly fixed by the developer and a working version was available
> at the developer's PPA. Unfortunately the version of Unetbootin in the
> Ubuntu repository is lagging behind.

[COLOR="#aa0000"]Then please file a bug report to have it synced or whatever, as
appropriate to get a recent version in the archive.[/COLOR]
[...]

> The remainder, when people want persistence or use the rest of the drive
> space for carrying data between computers, or who want a multiboot
> pendrive, can be managed with Unetbootin or Multisystem, but also with
> some other tools that 'participate' in the poll at the Ubuntu Forums.
> LXLE replaced the SDC with MultibootUSB in the current release. They
> have tested several tools before selecting it. ToriOS will soon release
> its first official version, and it uses mkusb.

I don't think we want to have different tools for different features.
The purpose of SDC is to be an application on the default install and on
the images, so that users can write a new version to USB to try it
before installing. It's still satisfying this primary purpose.

FWIW, I'm not opposed to change, but I'd like to see people coming
forward with something that is proven to work correctly, and that has
more backing than a small poll on Forums. It's also not only my
decision, but rather the decision of Ubuntu users and developers in general.

[COLOR="#aa0000"]Already looking after usb-creator, it seems like it's by far simpler to
just fix the bugs.
[/COLOR]
So, request a session at UOS, discuss it there, and see if people are
willing to do the work to support it *in Ubuntu*, looking at the bugs,
etc. From there, we used to have a "defaults" session where default
applications on images were "picked". If I was you I'd at least bring up
your alternative on ubuntu-devel, see if there is interest.
-- 
Mathieu Trudel-Lapierre[/quote]


[I]1. "Then please file a bug report to have it synced or whatever, as
appropriate to get a recent version in the archive."
[/I]
Yes, yes, I'll do that.

[I]2. "Already looking after usb-creator, it seems like it's by far simpler to
just fix the bugs."[/I]

If it is so simple, why this never ending stream of bugs that cripple the SDC?

[QUOTE=from the bug #1325801 report, comments 161-165]
sudodus (nio-wiklund) :

The poor Startup Disk Creator has been suffering from many bugs for many years now, and in spite of great efforts, our developers have not managed to make it work properly. There are still several bugs and strange features.

At the Ubuntu Forums we started a discussion about replacing the Ubuntu Startup Disk Creator with another tool. See these links,

[http://ubuntuforums.org/showthread.php?t=2289225](http://ubuntuforums.org/showthread.php?t=2289225)

[http://ubuntuforums.org/showthread.php?t=2291946](http://ubuntuforums.org/showthread.php?t=2291946)

I suggest that we look for a tool that is

- reliable

- easy to use for a beginner

- easy to maintain, for example more likely to work without tweaks (or with few and simple tweaks) between Ubuntu versions.

Mathieu Trudel-Lapierre (mathieu-tl) :

How about instead we just fix the bugs, given that it mostly works for people? We however can't do this unless the individual bugs are reported, and it helps a lot like people like Yu Ning provide patches too when it's very specific corner cases. There is no other tool which satisfies all of the "reliable", "easy to use" and "easy to maintain" requirements -- it's not like usb-creator is very hard to maintain, we're just dealing here with corner cases.

This particular issue here we've been at for a while, and this is simply because while I'm happy to test things and to sponsor things, usb-creator isn't the only thing I look after. Given that this isn't my top priority, I was relying on Yu Ning to complete the fixes. I did not see there was a new branch. Thankfully, we have Timo who also chimed in to help with the SRU.

As it's been mentioned previously, there are other issues which may affect behavior and make a SRU fail verification, something that we might not have thought of -- the answer to this is to iterate over these fixes, just as we've been doing now.

Can we please summarize the current state of this?

- Verification fails on Trusty and Precise.
- Does it work properly on Vivid? Presumably not because of the requirement for the architecture to be the same?

Given the same issue, it will also need to be fixed in Wily before the fix can make it to the stable releases. I'm still happy to review and sponsor proposed fixes.
Mathieu Trudel-Lapierre (mathieu-tl) :

Yu Ning, please confirm that this works properly as it is in Wily and Vivid -- it seems to me like it mostly should, and we can deal with other issues in separate bugs so as not to confuse the matters worse than it already is.
Changed in usb-creator (Ubuntu):
status: 	Fix Released &#8594 said:**
> That's simply false. Sure, there are some gotchas, but it largely works modulo this bug report. You're not answering the question I asked.[/COLOR]

As you may have noticed I've reset the statuses for this bug to
something I think is closer to reality, and we'll close things as
appropriate. We also have to consider architecture matching issues
separately -- those are in bug 1446646.

[COLOR="#aa0000"]Architecture matching is unfortunately an unavoidable issue.[/COLOR] Either we
run the syslinux from the system, and then you'll get the COM32R error
when you boot an >utopic image written from a Trusty system, or we run
the syslinux from the image about to be written and we have to match
architecture or pick in-between and run the system syslinux if an i386
system tries to write a 64-bit image, and the image syslinux otherwise.
Some careful application of syslinux parameters or copying additional
files on the image may help too.

So I got these results from Marc Deslauriers:
- Vivid amd64 can write images from Precise and up, amd64 or i386.

I think we also should strongly suggest that users run usb-creator on a
recent enough system if they don't want this bug here to happen. I'll
see how release notes can be updated accordingly.

In light of all this, this bug should be Triaged/Critical for all
supported releases -- we'll do another upload to -proposed to re-do the
changes from Yu Ning (which appear to be fine), along with a fix for bug
1446646.

*That's simply false. Sure, there are some gotchas, but it largely works modulo this bug report. You're not answering the question I asked.*

I'll try to answer that question ...

*"Architecture matching is unfortunately an unavoidable issue."*

Yes, for the SDC. But it does not create any problems at all for tools which use dd or cp under the hood (like mkusb and Disks). And I think the other tools in our poll can manage this issue. At least Unetbootin from the developer's PPA can manage it.

---

### Post by sudodus on 2015-09-19
Now I have tested the Ubuntu Startup Disk Creator, SDC.

I made a spreadsheet wíth columns for

[LIST]
[*]Host system
[*]Live/Installed
[*]Mode (BIOS/UEFI)
[*]Target system
[*]Live-only/Persistent
[*]Target pendrive's original status
[*]Result (Success/Failure)
[*]Error output (if any)
[*]Comment
[*]Bug number
[/LIST]


and tested with current versions of the Ubuntu family operating systems as hosts and as targets. See the attached ods file.

I hope these test results will help in the discussion, and also help improve the quality of the software :-)

1. It supplies substance to the statement that there are several cases where the SDC does not work. I think that we have more problems than some 'corner cases'.

2. It supplies input for those of us who want to debug the SDC and the program packages, that it depends on (for example udisks).

***Edit***: The attached spreadsheet (ods file) is updated with tests on Wily beta 2, bug [#1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746).

---

### Post by sudodus on 2015-09-19
I was asked to file a report against old versions of Unetbootin in the repos. Here it is. Please mark 'affects me too' (if you use it, I think it might affect you)!

"The Unetbootin versions in the Ubuntu repos are old. [Bug #1497604](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/1497604)"

Current unetbootin version from the developer's PPA is **613-1** uploaded 2015-07-20

Versions of unetbootin in the Ubuntu universe repo

```

Ubuntu-version    Unetbootin-version
[HR][/HR]
12.04.5 LTS       **565-3** probably uploaded 2012
14.04.2 LTS       **585-2** probably uploaded 2013
14.04.3 LTS       **585-2** probably uploaded 2013
15.04             **608-1** probably uploaded before the 'gfxboot.c32: not a COM32R image' bugfix
15.10             **608-1** probably uploaded before the 'gfxboot.c32: not a COM32R image' bugfix
[HR][/HR]

```

---

### Post by sudodus on 2015-09-19
> **sudodus said:**
> Now I have tested the Ubuntu Startup Disk Creator, SDC ... See the attached ods file.

I hope these test results will help in the discussion, and also help improve the quality of the software :-)

1. It supplies substance to the statement that there are several cases where the SDC does not work. I think that we have more problems than some 'corner cases'.

2. It supplies input for those of us who want to debug the SDC and the program packages, that it depends on (for example udisks).

@ kansasnoob

Please file a bug report about your timeout bug in the SDC (when you don't want to watch paint dry, and forget about it until it is too late). I was affected by that bug during these tests, because I had dinner instead of 'watching paint dry' :-P

***Edit***: The attached spreadsheet (ods file) is updated with tests on Wily beta 2, bug [#1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746).

---

### Post by sudodus on 2015-09-20
[QUOTE=Marc Deslauriers at Canonical]That's a very interesting spreadsheet, thanks for doing that. It seems most
issues are:

- A known bug in udisks that prevents the erase function from working reliably
(LP: #1460602)

- A mismatch between syslinux versions between the host system creating the usb
key and the version being installed (LP: #1325801)

- A limitation of the fix for the syslinux issue that prevents amd64 images from
being created on i386 systems (LP: #1446646)


I believe a simple way to eliminate every one of these issues at once in UDC
would be to get rid of the persistence functionality. All of the currently
supported images can now be written directly to a usb device as-is.

The syslinux and boot loader mangling that is currently required for persistence
and used to be required for older end of life releases is a constant source of
problems each time a new release come out and is difficult to get working
properly on mismatched architectures.

Removing persistence would also simplify the user interface and would remove the
need of having the "Erase Disk" button, therefore eliminating the known udisks
issue as a side effect.

Advanced users who require generating a usb key with persistence can simply use
one of the other tools that are available. Perhaps in the future persistence
could be added back by creating a partition in the free space left over after
copying over the image.

Changing UDC to remove persistence and to copy images as-is is a trivial change,
and I am willing to volunteer to do it.

Marc.[/QUOTE]

The dialogue at the ubuntu-quality mailing list is continuing and improving. My spreadsheet was appreciated :-)

[B][I]Now what do you think of this idea: to make the SDC reliable by removing its ability to create persistent live drives?
[/I][/B]
1. As a temporary solution to make it work again

2. In the long perspective

- Should persistence be added afterwards, when a reliable method is found (for example the method, that was developed by Andre Rodovalho and modified by me in mkusb)?

- Or is it enough that the SDC is creating 'live-only' pendrives?

***Edit:*** ... and I almost forgot to write

If you have not voted in the poll yet, please do :-)

If you re-visit this thread:

3. Or do you still think that it better to replace the SDC by a tool that is already working?

---

### Post by ventrical on 2015-09-20
The key words are 'mismatched architectures' .  Home built systems used for swap outs and swap ins will always be unreliable in making perfect matches for most open source software with , perhaps, the exception of Debian.  It would be nice if all the components of SDC would work on home builts with non original OEM hardware  swapped in but that is a high expectation. mkusb does not seem to have a problem with this.  So why cannot Canonical use some of the flowchart modules you are using?


Regards..

---

### Post by sudodus on 2015-09-21
Maybe they can, if we let them do it their way ;-)

---

### Post by sudodus on 2015-09-25
Bump

If you have not voted in the poll yet, please do :-)

-o-

What do you think of this idea: to make the SDC reliable by removing its ability to create persistent live drives?

1. As a temporary solution to make it work again

2. In the long perspective

- Should persistence be added afterwards, when a reliable method is found (for example the method, that was developed by Andre Rodovalho and modified by me in mkusb)?

- Or is it enough that the SDC is creating 'live-only' pendrives?

If you re-visit this thread:

3. Or do you still think that it better to replace the SDC by a tool that is already working?

---

### Post by PaulW2U on 2015-09-25
Hi sudodus, unfortunately I voted before you added SDC to the poll but I still stand by my [first post]("http://ubuntuforums.org/showthread.php?t=2291946&p=13344182&viewfull=1#post13344182") in this thread, i.e. SDC should be made to work.

Several of the alternatives might currently work better or be more reliable than SDC but they don't look as if they are part of Ubuntu. The flavours might have their own views on what might be included in future releases but Canonical will always want what integrates best with existing applications and themes for the main Ubuntu flavour.

---

### Post by v3.xx on 2015-09-25
Nothing seems to work all the time, but I have my best luck with Unetbootin.  If that fails me, I go to cd/dvd :)  I have no need for persistence, iso is used for install only.

---

### Post by sudodus on 2015-09-25
> **PaulW2U said:**
> Hi sudodus, unfortunately I voted before you added SDC to the poll but I still stand by my [first post]("http://ubuntuforums.org/showthread.php?t=2291946&p=13344182&viewfull=1#post13344182") in this thread, i.e. SDC should be made to work.

Several of the alternatives might currently work better or be more reliable than SDC but they don't look as if they are part of Ubuntu. The flavours might have their own views on what might be included in future releases but Canonical will always want what integrates best with existing applications and themes for the main Ubuntu flavour.

I see your point, and others have said the same thing at the Ubuntu Quality mailing list. What do you think of making the SDC reliable by removing its ability to create persistent live drives? Would it be OK, or should the current functionality be restored? In that case, how can it be done?

The problem is that the SDC has not worked properly for four years, and patching never seems to reach the goal. The beta 2 version that was released yesterday has inherited some old bugs but also a new or recently discovered (?) bug, so that the SDC cannot even make a working pendrive of itself (of the same version and architecture as the host operating system), [bug #1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746).

---

### Post by sudodus on 2015-09-25
> **v3.xx said:**
> Nothing seems to work all the time, but I have my best luck with Unetbootin.  If that fails me, I go to cd/dvd :)  I have no need for persistence, iso is used for install only.

I think that many people have no need for persistence, just like you. I hope we can get more sure about it before suggesting to remove the ability to create persistence from the Startup Disk Creator.

On the other hand, replacing it with Unetbootin would preserve the ability to create persistent live drives.

---

### Post by PaulW2U on 2015-09-25
> **sudodus said:**
> What do you think of making the SDC reliable by removing its ability to create persistent live drives? Would it be OK, or should the current functionality be restored?
I wonder how many want, need or use the persistence functionality? I just download, transfer to USB, test or install and then re-use the USB stick at a later date.
> **sudodus said:**
> The beta 2 version that was released yesterday has inherited some old bugs but also a new or recently discovered (?) bug, so that the SDC cannot even make a working pendrive of itself (of the same version and architecture as the host operating system), [bug #1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746).
I know. I saw that bug as well. I've marked that one as affecting me too.

---

### Post by sudodus on 2015-09-25
> **PaulW2U said:**
> I wonder how many want, need or use the persistence functionality? I just download, transfer to USB, test or install and then re-use the USB stick at a later date.

Yes that is the question - we can guess (guided by the feedback we can get), and we can test by removing the persistence functionality, and find out 'the real feedback' :-)
> 
I know. I saw that bug as well. I've marked that one as affecting me too.

It helps convincing those who do not want to see any problems with the SDC, that we must do something :-)

---

### Post by mystics on 2015-09-25
> **sudodus said:**
> On the other hand, replacing it with Unetbootin would preserve the ability to create persistent live drives.

My issue with Unetbootin is that, from my experience, the live USB can never boot from an Apple computer, and everything I've read indicates that this is a very common problem with it. The USB never shows up in the boot menu, and even if I go through with booting from GRUB, it often doesn't work properly. Then again, a vast majority of the tools I've come across, including SDC, don't work well with Apple hardware. mkusb is the only one that seems to work very well for me, in that it both shows up in the boot menu and boots properly even with persistence.

---

### Post by sudodus on 2015-09-25
> **mystics said:**
> ... Then again, a vast majority of the tools I've come across, including SDC, don't work well with Apple hardware. ...

Are you talking about Apple hardware with Intel CPUs or old PowerPCs or both?

---

### Post by mystics on 2015-09-25
Intel-based ones. I haven't tried with a PowerPC one.

Edit: Actually, come to think of it, SDC works OK with official Ubuntu flavors. I've still had some trouble with it not being 100% consistent, but it has at least worked with Xubuntu and Ubuntu GNOME on multiple computers. That said, anything outside of official Ubuntu flavors, even distros based on Ubuntu, often have trouble booting even if they show up in the boot menu.

---

### Post by v3.xx on 2015-09-25
> **mystics said:**
> Intel-based ones. I haven't tried with a PowerPC one.

Edit: Actually, come to think of it, SDC works OK with official Ubuntu flavors. I've still had some trouble with it not being 100% consistent, but it has at least worked with Xubuntu and Ubuntu GNOME on multiple computers. That said, anything outside of official Ubuntu flavors, even distros based on Ubuntu, often have trouble booting even if they show up in the boot menu.
Also, unless it has changed:

SDC will not work with the mini iso, but unetbootin will.

---

### Post by sammiev on 2015-09-25
For me and the family we use mkusb as it just works.

---

### Post by sudodus on 2015-10-02
Bump

If you have not voted in the poll yet, please do

[hr][/hr]
If you have not discussed this idea, please do: What about making the SDC reliable by removing its ability to create persistent live drives?

1. As a temporary solution to make it work again

2. In the long perspective

- Should persistence be added afterwards, when a reliable method is found (for example the method, that was developed by Andre Rodovalho and modified by me in mkusb)?

- Or is it enough that the SDC is creating 'live-only' pendrives?

If you re-visit this thread:

3. Or do you still think that it better to replace the SDC by a tool that is already working? 

[hr][/hr]
The dialogue at the ubuntu-quality mailing list is continuing:

[QUOTE=Nicholas Skaggs, continuing dialogue at the ubuntu quality mailing list]```
On 09/28/2015 08:22 AM, Nio Wiklund wrote:
> Den 2015-09-28 kl. 13:56, skrev Marc Deslauriers:
>> On 2015-09-28 07:48 AM, Nio Wiklund wrote:
>>> Den 2015-09-21 kl. 18:03, skrev Nicholas Skaggs:
>>>> On 09/19/2015 07:29 AM, Marc Deslauriers wrote:
>>>>> On 2015-09-19 07:04 AM, Nio Wiklund wrote:
>>>>>> Hi Marc,
>>>>>>
>>>>>> My standard ISP's mail server is down. So I tried to send this mail
>>>>>> via Google's
>>>>>> web mail interface. In my saved version of the mail, there is an
>>>>>> attachment
>>>>>> "SCC-test.ods", size 17692 bytes. I'll try again ...
>>>>>>
>>>>>> Best regards
>>>>>> Nio
>>>>>>
>>>>> That's a very interesting spreadsheet, thanks for doing that. It seems
>>>>> most
>>>>> issues are:
>>>>>
>>>>> - A known bug in udisks that prevents the erase function from working
>>>>> reliably
>>>>> (LP: #1460602)
>>>>>
>>>>> - A mismatch between syslinux versions between the host system
>>>>> creating the usb
>>>>> key and the version being installed (LP: #1325801)
>>>>>
>>>>> - A limitation of the fix for the syslinux issue that prevents amd64
>>>>> images from
>>>>> being created on i386 systems (LP: #1446646)
>>>>>
>>>>>
>>>>> I believe a simple way to eliminate every one of these issues at once
>>>>> in UDC
>>>>> would be to get rid of the persistence functionality. All of the
>>>>> currently
>>>>> supported images can now be written directly to a usb device as-is.
>>>>>
>>>>> The syslinux and boot loader mangling that is currently required for
>>>>> persistence
>>>>> and used to be required for older end of life releases is a constant
>>>>> source of
>>>>> problems each time a new release come out and is difficult to get working
>>>>> properly on mismatched architectures.
>>>>>
>>>>> Removing persistence would also simplify the user interface and would
>>>>> remove the
>>>>> need of having the "Erase Disk" button, therefore eliminating the
>>>>> known udisks
>>>>> issue as a side effect.
>>>>>
>>>>> Advanced users who require generating a usb key with persistence can
>>>>> simply use
>>>>> one of the other tools that are available. Perhaps in the future
>>>>> persistence
>>>>> could be added back by creating a partition in the free space left
>>>>> over after
>>>>> copying over the image.
>>>>>
>>>>> Changing UDC to remove persistence and to copy images as-is is a
>>>>> trivial change,
>>>>> and I am willing to volunteer to do it.
>>>>>
>>>>> Marc.
>>>>>
>>>>>
>>>> Marc, this sounds like a great way to accomplishes two things at once.
>>>> It both simplifies the application for users,  while making the process
>>>> more robust. I'm in support.
>>>>
>>>> Nicholas
>>>>
>>> Hi Nicholas and Marc,
>>>
>>> I have added two test cases to the spreadsheet, now updated to
>>> 'SDC-test1.ods'. You find it via the following link
>>>
>>> [http://ubuntuforums.org/showthread.php?t=2291946&page=2&p=13358864#post13358864](http://ubuntuforums.org/showthread.php?t=2291946&page=2&p=13358864#post13358864)
>>>
>>> Would it be possible to remove persistence and to copy images as-is
>>> already in Wily? Or will Wily be released with the most acute bugfix but
>>> with some remaining serious bugs in the SDC, or maybe even without any
>>> bugfix, if the limited time will only allow for more important
>>> bug-fixes? Anyway, I can volunteer to help testing, what you develop, Marc.
>>>
>>> I have assumed that we are talking about 'removing persistence' in the
>>> next release, 16.04 LTS, because there must be a formal decision. Is it
>>> like this, Nicholas, or can we 'save the SDC is Wily' with Marc's
>>> suggestion?
>>>
>> Hi Nio,
>>
>> I'm currently working on SDC in my free time. You can track progress here:
>>
>> [https://code.launchpad.net/~mdeslaur/usb-creator/imaging-rework](https://code.launchpad.net/~mdeslaur/usb-creator/imaging-rework)
>>
>> I still have a few things to fix, and then I'll build test packages to try out.
>>
>> It's likely too late to have any rework in Wily, as we're already past feature
>> freeze and UI freeze. That being said, I'd definitely like it to get SRUed into
>> all releases when I'm done.
>>
>> Marc.
>>
> Hi Marc,
>
> That's great news, that you have already started
>
> I did not know how it works. Please send a mail directly to me, when you
> have something to test, and I will test it and give you feedback as soon
> as possible.
>
> It is as I feared, too late for the Wily release. But the next LTS will
> be the important one, and SRU should be accepted. I'm thinking of the
> previous LTS versions. to provide a reliable built-in tool to install
> the next [LTS] version.
>
> Best regards
> Nio
I'm sure Marc will have everyone on this thread give feedback as soon as something is ready As Marc said,
since this will look to be SRU'd (which will also need everyone's help with getting accepted!), all the stable
versions of ubuntu will benefit. So we needn't think of being "late" for wily as a large issue. The next LTS
as well as the previous will get the update.

Thanks again everyone. I can't wait to see the results of this effort.

Nicholas
```[/QUOTE]

---

### Post by sudodus on 2015-10-17
Bump

It is way too late to change the Wily ISO files, but we can prepare for the next version, 16.04 LTS.

If you have not voted in the poll yet, please do

[hr][/hr]
If you have not discussed this idea, please do: What about making the Ubuntu Startup Disk Creator, SDC, reliable by removing its ability to create persistent live drives?

1. As a temporary solution to make it work again

2. In the long perspective

- Should persistence be added afterwards, when a reliable method is found?

- Or is it enough that the SDC is creating 'live-only' pendrives?

3. Do you think that it is better to replace the SDC by another tool?

---

### Post by mikodo on 2015-10-17
I wish I could change my selfish vote. Being someone that never has ever had a computer that had the BIOS setting to boot from usb (I know I could easily do that with PLOP), I just haven't bothered with trying it.

When this poll came up, I selfishly voted for what I would like. I like the cli, so I choose the cp & dd ... one. Now, that I have been reading this thread and links on usb booting, I think it would have been best to have voted for one that is reliable and useable from gui and cli, for other users. I should have thought it through from the perspective of people who need those. Now, I would vote mkusb, from reading about the other alternatives and having a more informed knowledge base. 

Not that my vote counts for anything anyway. I'm just saying ...

---

### Post by sudodus on 2015-10-23
Bump :-)

This poll will close on October 28th, 2015, five days from now.

And it will be time soon to draw conclusions and decide what to suggest for the Start Disk Creator in Xenial Xerus to become 16.04 LTS.

So please let us know your opinion, vote and post!

---

### Post by sammiev on 2015-10-23
Voted way back when but I still must say that mkusb is the best I used to date...

---

### Post by PaulW2U on 2015-10-23
> **sammiev said:**
> Voted way back when but I still must say that mkusb is the best I used to date...
But does it look like that it's an Ubuntu/Gnome application? 

I don't think it does, in which case I'm sure a major re-write will needed for it to be even considered by the Ubuntu developers as a replacement for USB Creator.

---

### Post by sammiev on 2015-10-23
> **PaulW2U said:**
> But does it look like that it's an Ubuntu/Gnome application? 

I don't think it does, in which case I'm sure a major re-write will needed for it to be even considered by the Ubuntu developers as a replacement for USB Creator.

I don't worry about looks.

I just want software that works. :)

---

### Post by mikodo on 2015-10-24
> **PaulW2U said:**
> But does it look like that it's an Ubuntu/Gnome application? 

I don't think it does, in which case I'm sure a major re-write will needed for it to be even considered by the Ubuntu developers as a replacement for USB Creator.

Yes. I'm guessing that is a consideration.

 I know of one important app, that was developed outside of Canonical that, still needed a lot of work fixing bugs. I believe it was chosen over others that today still, have much less problems. But, it looked the part, and could be modified to what Canonical was pushing hard with at the time, to generate revenue.

Nuff said but, I'm pretty sure appearance and presentation played a part, in it being chosen.

---

### Post by sudodus on 2015-10-29
The poll is closed, and we are in the beginning of the developement period for *Xenial Xerus* to become 16.04 LTS.

[SIZE=4]Summary[/SIZE]

1. ***Unetbootin*** 'won' the poll with 14 votes. (I had expected Unetbootin to win the poll by a bigger margin, because it is well known and used by many people.)

2. ***cp and dd*** "without safety belt" and ***mkusb*** share the second place with 10 votes. (I had not expected cp and dd "without safety belt" to get so many votes.)

4. ***Disks*** (gnome-disks) reached 7 votes. (I had expected it to get some of the votes that were given to cp and dd. Maybe this feature of Disks is not very well known.)

5. ***Multisystem*** reached 6 votes. (I had expected more votes for Multisystem.)

6. "Keep the ***Startup Disk Creator***" reached 5 votes, but a couple of users wrote that they would have voted for it, if it had been there in the very beginning, so a fair share might be 7-8 votes.

[SIZE=4]My personal comments[/SIZE]

The result of the poll and particularly the detailed discussion in the replies are very valuable. Thanks for participating :-)

I had expected and hoped that more people would have participated in this poll and thread. As it is now, there is no huge opionion, that can force a replacement of the Startup Disk Creator. Instead it can be claimed that a few people, maybe 'advanced users' are telling us that the Startup Disk Creator is not working well, and the majority of us want to replace it with another tool. Even ***cp and dd*** "without safety belt" received more votes than the Startup Disk Creator, but I think most of us would not really want to recommend tools "without safety belt" to beginners, even if we use them ourselves.

During this poll, there has also been a discussion at the ***Ubuntu Quality mailing list***, and it has been made very clear that none of the available alternatives can be accepted as a replacement for the Startup Disk Creator, even when it is very obvious that the Startup Disk Creator does not work. Instead Marc Deslauriers at Canonical volunteered to ***revamp the Startup Disk Creator*** to use cloning, which will make it much simpler and much easier to keep working. It also means that it will be limited to creating 'live-only' pendrives, at least in the beginning (in Xenial Xerus). This revamped Startup disk Creator can be SRU'd and ported back to previous versions of Ubuntu too.

The intention is to recommend other tools to create a persistent live system and to prepare a pendrive to be re-used with a new partition table and file system.

-o-

You are very welcome to draw other conclusions and to continue this discussion :-)

---

### Post by sudodus on 2015-12-17
The version of the Ubuntu Startup Disk Creator by Marc Deslauriers has reached the xenial daily isos now. The idea is to make a version that is very reliable by using the cloning method, and it seems to work well for the desktop iso files and also Ubuntu Server.

But it cannot clone the Ubuntu mini.iso. See this bug report:

[Bug #1527086 'new Startup Disk Creator cannot clone mini.iso'](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1527086)

There is probably some kind of logic, that checks if the source file is the correct kind of file, and this logic should accept also Ubuntu mini.iso.

---

### Post by buzzingrobot on 2015-12-17
Mint's USB burning tool is excellent. Works fine on Ubuntu in my experience.   I've always thought Canonical should smile and just adopt it.:D

---

### Post by sudodus on 2015-12-17
You missed the poll. Someone suggested mintStick, but nobody voted for it.

I think several of the tools in this poll are good (at least much better than the faulty Ubuntu Startup Disk Creator). But those who decide about Ubuntu didn't want any of them.

The current revamped version should be simple enough to get robust after some initial debugging, and I think it will be a big improvement: we will get a working Ubuntu Startup Disk Creator in Xenial, and we can hope it will be backported to Trusty.

---

### Post by v3.xx on 2015-12-17
Didn't see that one coming, oh well.

---

### Post by sudodus on 2016-01-26
***A. Great good news: After fixing a couple of minor bugs, the new Ubuntu Startup Disk Creator alias usb-creator-gtk works,*** and I think it is likely to continue to work, because it clones the iso file now.

This is usb-creator-gtk version 0.3.2, which arrived at the Xenial daily iso files yesterday. Thanks Marc Deslauriers :-)


***B. Minor bad news: Bug #1537836, papercut level infrastructure fixes***

The infrastructure around it is not updated:

1. man usb-creator-gtk

2. usb-creator-gtk --version

3. the help text (there is no persistence now) and screenshot in the Ubuntu Software Center and Synaptic

See this bug report

[Bug #1537836](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1537836/)


***C. When we want a persistent live drive, we can use another tool, for example mkusb***

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Nuno_Abreu on 2016-01-26
I'd go for Easy2Boot - you just need to place the ISO file in your USB stick and you're good to go! The problem with this script is the fragmentation - does anyone know how to fight against this problem? I already tried to boot from an ext2 filesystem (unfortunately, Grub4Dos does not work with ext4) and I still note some fragmentation. I know there is a defrag script, but when I run out of space, it overwrites data due to the lack of it.

---

### Post by sudodus on 2016-01-26
@Nuno_Abreu,

It might be a good idea to limit the percentage of the partition that is allowed for files. The standard in ext file systems is 95%. But if you limit it more, the fragmentation will be reduced. You can try with 90% (reserve 10%) or 80% (reserve 20%) depending on the size of the partition in relation to the iso files.

From ```
man tune2fs
``` you find

```
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by  privileged  processes.   Reserving some number of filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem  fragmentation,  and  to  allow system daemons, such as sys&#8208;
              logd(8), to continue to function correctly after  non-privileged
              processes  are  prevented  from writing to the filesystem.  Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.

```

-o-

***grub2*** works with ***ext4***, so you can use a tool that uses ext4 or create an own pendrive system with grub2 and ext4.

If you have a separate EFI partition with FAT32, there should be no booting problem to have the iso files in an ext4 partition. And there are no problems to use an ext4 partition for persistence (with the label casper-rw). It is often recommended to modify the ext4 file system in order to reduce wear by turning off journaling and using the mount option noatime.

---

### Post by Nuno_Abreu on 2016-01-26
Can I reserve blocks in a FAT32 partition for instance? If yes, how? I just hate to have to defrag every single time I insert an ISO file on my USB drive. Or if not, does it work on an ext2/ext3 one?
 What I really wanted is an automatic process of updating the configuration files, and that happens on Easy2Boot - I can't figure out how to do this with Grub2.

I'm open-minded for alternatives, though.
Thank you for your response!

---

### Post by sudodus on 2016-01-27
I don't know a way to reserve blocks in FAT32. Maybe there is, but FAT32 is a primitive file system, so maybe there is no way to do it. Of course, you can watch the usage manually and keep enough free blocks manually, but FAT32 is notorious for fragmentation.

I think the method with tune2fs works with all ext file systems (ext2,3,4). Try it :-)

---

### Post by Nuno_Abreu on 2016-01-27
> **sudodus said:**
> I don't know a way to reserve blocks in FAT32. Maybe there is, but FAT32 is a primitive file system, so maybe there is no way to do it. Of course, you can watch the usage manually and keep enough free blocks manually, but FAT32 is notorious for fragmentation.

I think the method with tune2fs works with all ext file systems (ext2,3,4). Try it :-)


I only use the FAT32 filesystem because I need to insert my flash drive on Windows for university and/or projects that don't support the ext natively - I know there is a driver for it, but people are not willing to install it nor let me boot in a Live-CD just for a presentation.

I will try - the only problem I can have is if I have 0,0001 % of fragmentation in the filesystem, it will not boot - why does Grub4Dos do this?

One odd thing I discovered is if I format a partition in XFS and afterwards format in FAT32, it won't have as much fragmentation as it normally does... Just like as if there was an XFS filesystem layer inside the FAT32 one. It just has fragments when it reaches like <= 1.5 GB of free space.

---

### Post by sudodus on 2016-01-27
If you use mkusb, you can create a persistent live system of the Ubuntu flavours and Debian. This system has a GUID partition table and ***partition #1 has an NTFS file system for exchange of data with Windows***. There is also an ext4 file system for the persistence. I don't think you will have problems with fragmentation, if you use that system and keep the iso files in an ext partition.

See this link,

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

where you can see the partition table and file systems. This is not a multiboot system, but you can rather easily add some menuentries to grub.cfg pointing to iso files and make it a multiboot system. You can find how to make the menuentries from the following link to a 'grub-n-iso' system (post #6 and the following posts)

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by PaulW2U on 2016-03-27
sudodus, in bug report [https://bugs.launchpad.net/bugs/1562391](https://bugs.launchpad.net/bugs/1562391), you said:
> I have seen indications that it makes a difference which tool or method was used to create the USB boot drive. So please tell us which tool was used when this bug appeared, as if you get different results when trying to shut down, when the USB drive was created with different tools or methods.
This was in response to **my** bug report that I had marked as being invalid having previously reported a bug against the current Lubuntu daily ISO. For the benefit of others reading, the bug report referred to the live session not being able to be shut-down or rebooted. I was using a rather old 1GB USB drive whereas subsequent tests were made using two much newer 8GB drives. 

Were you saying that had I used mkusb or unetbootin then I might have been able to shut-down or reboot out of the live session?

---

### Post by sudodus on 2016-03-27
Hi PaulW2U,

I did some testing today with Lubuntu Xenial i386 with the same USB boot drive, a simple but reliable Sandisk Cruzer Blade 4 GB pendrive. It seems that live systems booted from cloned drives do not shutdown correctly, but grub-n-iso systems are not affected by this bug. I tested in two very different computers.

Examples:
- A ***live-only*** drive made with mkusb is cloned and it is ***affected*** by that shutdown bug.
- A ***persistent live*** drive made with mkusb boots via grub and it is ***not*** affected.

[See this link to the current bug report #1552985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985)
[and to my comment, #17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985/comments/17)

Cloning is a well defined general method, which means that the shutdown bug affects drives prepared with the new Ubuntu Startup Disk Creator 0.3.2, gnome-disks and dd too. In BIOS mode the cloned systems boot via syslinux.

Unetbootin boots via grub, and might not be affected.

---

