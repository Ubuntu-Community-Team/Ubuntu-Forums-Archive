---
title: "My Prayers have been answered"
date: 2008-07-14
forum: Testimonials &amp; Experiences
---

### Post by MaindotC on 2008-07-14
I'm not religious but it seemed a fitting title.  I was having some video display issues - mostly choppiness when going full screen with videos or even wine'ing GTA Vice City:

Abit AV8 Socket 939
AMD Athlon 4000+
4GB Corsair PC-3200
ATI x850
Samsung Synchmaster 213t

The rest seems negligible.  I followed the [ATI Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") and I had to enter some commands that I found by Googling error messages.  It didn't really seem like it worked, but I rebooted expecting to get the LGMSOD (low-graphics mode screen of death) and lo and behold it booted right into perfect 1600x1200 resolution.  My main concern was running NHL96 on Dosbox.

Before, I was using the restricted driver in the repositories (in fact in System-Administration-Hardware Drivers it says it's still enabled) and NHL96 was unbelievably choppy in full-screen.  I knew my hardware was good - it HAD to be a driver issue.  I followed that guide I mentioned above, and now I've got perfect gameplay :)  GTA Vice City makes my screen go haywire but at least it starts instead of the "unhandled exception" error.  I'll try re-installing GTA Vice City (though I doubt that would make any difference).

Unfortunately, porn still is choppy at the presence of large organic and in-organic objects flailing while occupying a majority of the media player window.  I think it's just the quality of the clip.

Anyone w/ a similar setup feel free to ask any questions.  Sens are winning the 96 cup on Hardy baby!

Update: Desktop effects are a no-go until I figure out what to do with this blank white screen :(

---

### Post by MaindotC on 2008-07-14
Spoke way too bleeping soon.  Well, now I'm stuck in 800x600 mode, I can't reinstall the restricted drivers from the repos because fglrx is blacklisted and I can't seem to unblacklist it, every other game or purpose for me using Ubuntu crashes or changes the resolution to something freaky.  It's probably going to take me way too long to fix it than re-image so I'll have to re-image.  Screw NHL96.

---

### Post by Kilz on 2008-07-14
What happened between its perfect and your second post? What did you change or edit?

---

### Post by MaindotC on 2008-07-14
I rebooted. (*!)(*$!)($#@@

---

### Post by MaindotC on 2008-07-14
I'm in the LiveCD re-imaging right now.  I'm going to try 32-bit.  After that I think I'll dual-boot and put 64-bit Hardy on a small partition and use that for learning when and how to configure the ever-sensitive video driver issues. I'm nowhere near as knowledgable as I assume you are, Kilz, but I'm not gonna get there today and I need my UrbanTerror :(

---

### Post by Kilz on 2008-07-14
The thing is, you are going to run into video driver issues regardless of what version you install.  There is a learning curve, especialy with ATI.. Bite the bullet and fix the 64bit partition. You are not going to save time or headache and will end up with a slower install.

---

### Post by MaindotC on 2008-07-14
Sorry already installed :( I saved my /home folder. If I copy it and its contents to the /home folder I have in the new installation, will it bring with it anything to do with the video driver?

Btw, I did try fixing the partition from a previous 32-bit installation and I followed the directions just as the wiki stated.  I want to find the link for you but Hardy is running its updates and Firefox is being weird till my next reboot and I wanna get this post up.

---

### Post by Kilz on 2008-07-14
> **strAlan said:**
> Sorry already installed :( I saved my /home folder. If I copy it and its contents to the /home folder I have in the new installation, will it bring with it anything to do with the video driver?

Btw, I did try fixing the partition from a previous 32-bit installation and I followed the directions just as the wiki stated.  I want to find the link for you but Hardy is running its updates and Firefox is being weird till my next reboot and I wanna get this post up.

OK, but the first thing to do is install those video drivers. If it messes up just wipe and install the 64bit version.

---

### Post by MaindotC on 2008-07-14
Dude this sucks - I am so sorry but everything is running fine (so far) in 32-bit.  I could play NHL96 full-screen no problems, and GTA Vice City installed and runs perfectly in Wine.

I know that what I did doesn't really solve the problem and it annoys me that I took this route and everything is working well.  I don't see how 64-bit addressing could really make that much difference - but until I become a gosu developer I won't understand and I'll be just like the other newbs :(  I felt so good installing the amd64 version - it was pretty much perfect and I felt like I was accomplishing something.

Well, for the remainder of the summer I need to prepare for some web-development classes in the fall so unfortunately I can't devote much time to learning C or the book I have on the Linux kernel.  I hope someday to join you among the 64-bit ranks (or perhaps 128 or higher).  I pm'd you - please let me know if you'd be interested in helping me get the amd64 version working and in the meantime I'll create a separate partition and see if I google it to work.  However, three times I've tried installing that ATI proprietary driver by the documentation, and it has always resulted in problems.

---

### Post by markbuntu on 2008-07-14
I got the ATI driver to run with my HD3650 1GB on Hardy 64 by using this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use method 2. It has special instructions for 64 bit users. Read all the way through before you start. I tried other guides but this is the only one that actually worked for 64 bit.

Then I used this to tweak it:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by MaindotC on 2008-07-15
Hi, mark.  I followed that guide as well as it is stated in my first post and that's how I got where I am :(  I'm going to re-install the 64-bit version on another partition so I can play with it and hopefully figure out what I need to do to get it to work.

The video drivers are a mystery to me.  For example, if I already have the restricted drivers enabled by going to System-Administration-Hardware Drivers, then I should see it in Applications-Other-Screens & Graphics, right?  Well, instead I see an unknown monitor with resolution set to 640x480, and the Graphics Card setting shows two drivers selected: ati, and vesa.  I'm assuming it shows that because the dvi-out is connected to my Samsung SynchMaster 213t - that must be the ati driver, and the other output, a special video-out, is plugged into a TV - that must be the vesa driver.

So why doesn't it show the restricted driver I downloaded and installed when I initially enabled it in System-Administration-Hardware Drivers?

---

### Post by markbuntu on 2008-07-15
No no no, do not use Screen and Graphics. 

It will screw things up for you. Screens and Graphics is for vesa and ati and radeon drivers, not for fglrx. It will replace the fglrx driver if you open it. Hide it and never think about it again.

Check in your xorg.conf file and if the driver section says ati or vesa change it back to fglrx.

Then run aticonfig -f again.

If that does not work then you may need to reinstall the driver from ati.

Use only the Catalyst Control Center for fglrx or make changes in xorg.conf and use this command to load them into fglrx.

aticonfig --input=/etc/X11/xorg.conf

---

### Post by MaindotC on 2008-07-16
Right now it says fglrx, but when I re-install is when the fun begins.  I understand your advice about Screens & Graphics and I won't use it.  Doesn't the situation I described seem odd, though?  I had fglrx selected in Hardware Drivers, but Vesa was showing up in Screens & Graphics.  Well, that time is past so it's no biggie.  I'll let you know when I'm ready to try this again.  For right now, I have what I need.  Thanks for staying w/ the thread :)  You too, Kilz.

---

### Post by Tuxaby on 2008-07-16
Solved my 64 bit video driver problems with EnvyNG. Learn about it here [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A).  You will find it in the package manager, make sure  the universe and multi universe repos are loaded.  It will detect your hardware, download, and install the approrpriate driver.

---

### Post by markbuntu on 2008-07-16
Well yes, envy is quick and convenient but it does not provide the 8.6 driver which has a lot of fixes over the 8.47.3 driver which envy provides last time I checked.

---

### Post by MaindotC on 2008-07-16
I've seen this "envy" program.  I guess it's just an interface that automates the installation of the fglrx driver, is that right?  If I download the latest driver from the ATI website can you specify to use that driver instead of something else?

---

### Post by darkknight045 on 2008-07-17
AActually imho, Envy is a bit better than running the *latest drivers*  it will install the latest Stable drivers.  In addition it seems to run quite a few commands, and handles the downloads and installation completely.  

To install:
```
sudo apt-get install envyng-gtk
```

---

### Post by Kilz on 2008-07-17
> **darkknight045 said:**
> AActually imho, Envy is a bit better than running the *latest drivers*  it will install the latest Stable drivers.  In addition it seems to run quite a few commands, and handles the downloads and installation completely.  

To install:
```
sudo apt-get install envyng-gtk
```

While I will agree with the fact that 8.6 had some issues, the latest drivers from ati are stable. There is no official "stable" release of the drivers. Bugs are fixed with the next release. So what you are in fact saying is someone picks out what they think is stable and doesnt install the newer versions.

---

### Post by darkknight045 on 2008-07-17
> **Kilz said:**
> While I will agree with the fact that 8.6 had some issues, the latest drivers from ati are stable. There is no official "stable" release of the drivers. Bugs are fixed with the next release. So what you are in fact saying is someone picks out what they think is stable and doesnt install the newer versions.

Yes and No, in my experience (which is limited) always upgrading to the latest Graphics Driver, **when your current one is working fine**, does not guarantee that it will be working fine thereafter.  Not all driver updates are 'stable', these are usually fixed quickly but nevertheless I'd rather not be the one finding out at that the latest release hoses X for me.

Your mileage will vary.

---

### Post by markbuntu on 2008-07-17
I usually read the release notes, they tell you a lot about what is fixed and not fixed. the release notes for the 8.6 driver are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

The release notes for the 8.5 driver are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

If you read these, you will see a lot of significant changes and fixes over the 8.4 driver that envy installs.

The 8.5 and then 8.6 driver have made a significant difference for me. 

These are not beta releases. ATI has its own closed beta testing program.

---

### Post by MaindotC on 2008-07-29
Sorry, all - I haven't taken the 10 mins to install amd64 on a new parition - been too lazy.  I have to work tomorrow so I plan to have it done on Thursday.  Just don't wanna reboot right now!  RIght now I'm 136.204.203.1 - I'm the first in that subnet!  If I reboot I might get a new address and I just can't bear the thought - at least not till Thursday.

Even on this, the 32-bit edition, the video is still wierd.  It works, and I'd be perfectly happy if this is just how it is, but video full screen is extremely choppy, and even if I bring the resolution down to 1024x768 I still see horizontal breaks from time to time.  Again, maybe that's just how it is and if it is oh well at least I'm not using blasted windoze (well I am in a VM), but just wondered if this was common.

Stay subscribed!

---

### Post by markbuntu on 2008-07-29
Well, you can get the latest ATI driver from here, the directions have been updated for the 8.7 driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Also, you can try some of the tweaks here, they are not official but have improved performance for many:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Also, you can use the Catalyst Control Center options to improve 3D performance and reduce/remove the tearing problem. Try them out.

---

### Post by MaindotC on 2008-07-30
Thanks, Mark.  I believe I stated earlier that I did download the latest driver and install it per the wiki but I still had issues :(  Again, I'll keep you updated when I re-install amd64 Hardy and I'm ready to install the driver.  Thanks for keeping in touch :)

---

### Post by MaindotC on 2008-07-31
Man do I hate the topic that I made this thread.  Guys, I'm prepping for my partitioning and layout because I'd like to install 32 and 64 bit versions on separate partitions.  I read a blogpost about putting the /home folder on a separate partition and have some general questions [here]("http://ubuntuforums.org/showthread.php?p=5500300#post5500300").  I am going to get to that video driver, but before I do I wanted to know if I could have one partition for /home and share it between the 32 and 64 bit installations.  If you don't know, I'll gladly be the guinea pig.

Explanation if you're interested:  I'm reinstalling the 32-bit vers b/c I messed up my /home part.  I stored the /home folder from my previous 64-bit installation on a network share, installed the 32-bit ver, then tried copying my /home folder on the network share to overwrite the /home folder on my new 32-bit installation.  Of course there were permissions issues that I didn't know about and some files were copied and some weren't (I didn't know this would happen).  Then I tried copying them all over as root and did more damage.  You can see my [issues w/ evolution here]("http://ubuntuforums.org/showthread.php?t=859898") and how it was resolved, but it's not really resolved b/c each time I start Evolution I have to re-enter my account information.  (What I've been doing in the meantime is just saving a backup file before I close it and restoring from that.)  So I want to start fresh and just not mess w/ the /home partition this time but still try and get the ATI driver working in the process and that's why I was wondering if I could use the /home partition for both 32 and 64 bit installations.  It would be a dual boot so obviously both o/s's wouldn't access the same /home folder at the same time.

---

### Post by markbuntu on 2008-08-02
You cannot share a home partition between distros. The home directory has a lot of configuration files that would get all mixed up and create all sorts of fun nightmarey type problems. If you just want a partition for your personal stuff, make a partiton called /personal or something and mount it under /home on both installations. If you use the same name and password, you won't have to worry about permission problems.

---

### Post by MaindotC on 2008-08-02
I have 250 gigs - I'll just have different partitions for the 32 bit and 64 bit /home directories.  Sorry I've still be shilacking on getting that 64-bit version installed - I had to work a double at work and I've been beat tired :(

---

### Post by Vorian Grey on 2008-08-02
I have an ATI X1300 video card and the newest drivers never work for me. I've tried many distros and I always need the legacy drivers. On PcLinuxOS I needed the legacy 8.4 drivers for it to work properly. I guess my point is don't assume the newest drivers work for you, because they may not. 

That's what I like about Envy, it gets the proper driver and sets it up for you.

---

### Post by MaindotC on 2008-08-03
Vorian, I completely agree with you.  Newer is not always better, especially if you have no reason for upgrading other than the fact that the version number is incremented.  I'm sure some of the reasons for later drivers are increased interoperability, smarter or more efficient design, or new features, but sometimes you're the holder of one of the cards or chipsets that the developers must ignore in order to serve the greater need.  And that could be for any of millions of reasons which are way beyond my understanding.  I've googled several stories of success for the 1300 and several horror stories with people left searching for answers.  You'd think "if it isn't broke, don't fix it" would apply.

Btw, when you say legacy drivers, do you mean by enabling the restricted driver in System -> Administration -> Hardware Drivers and checking the box for the video driver?

---

### Post by Vorian Grey on 2008-08-03
No. I think that gets you the newest driver. By legacy I mean "older." If the 8.7 is the newest driver, then the 8.4 is legacy. You can still download version 8.4 from ATI. 

I know Envy installs xorg-driver-fglrx-envy for ATI cards. Look it up in Synaptic. It supports a lot of cards. I'm not sure what version of ATI driver it is, but I'm willing to bet it's the 8.4 series or earlier. 

When I ran PCLinuxOS, the legacy driver plainly said it was the 8.40.4 driver.

---

### Post by MaindotC on 2008-08-04
K well I'm doing the installation now.  Will it mess up my system if I enable the restricted driver and THEN download and install the ATI driver and follow the installation instructions?  I don't really mind experimenting but thought I'd ask before I continue.  Installing now.

---

### Post by MaindotC on 2008-08-04
Good news.  I installed the driver per the instructions and everything went smoothly and any output was almost as the wiki had predicted.  I installed GTA Vice City in wine and it installed and ran unlike my previous amd64 installation.  However, the play is very chopppy - I know this is a common problem so I'll research it.  Video still can't seem to be fluid for 1600x1200 resolution.  I played a clip of [Where the hell is Matt?]("http://vimeo.com/1211060") and it's still choppy at full screen.  I'll check out the tweaks when I get a chance.  Going to bed now - thanks for all your guidance and help and I'll keep you updated.

---

### Post by Vorian Grey on 2008-08-04
Glad to know it worked. You can have some real fun now.

The only way I could get rid of the choppiness was to cut off desktop effects. Try that and see if it helps.

---

### Post by MaindotC on 2008-08-04
I didn't have on desktop effects :(  I can't believe this to be true but it's possible that the x850 is just not powerful enough for full screen?  I think it is, so I'm going to install a copy of XP and try it out in winblows.  If it runs perfectly in winblows I"ll be sad :(  I'll let you know.

---

### Post by MaindotC on 2008-08-12
God I cannot stand the name of this thread - one of my biggest regrets.  I'm going to reinstall and install the driver from ATI's website.  Once I have it installed, how can I change the driver being used from the one from the ATI site to the one in System -> Administration -> Hardware drivers?  I want to use the one I can download from their site, but I want to be able to switch back to the one in the repositories just in case.  To be specific - I know you can check the box next to the ATI driver in Hardware Drivers (or uncheck it) but I want to make sure if I uncheck it that it will properly go back to using the one I install from the ATI site.  Make sense?  How can I ensure that I can switch between these two properly?

---

### Post by Kilz on 2008-08-13
> **strAlan said:**
> God I cannot stand the name of this thread - one of my biggest regrets.  I'm going to reinstall and install the driver from ATI's website.  Once I have it installed, how can I change the driver being used from the one from the ATI site to the one in System -> Administration -> Hardware drivers?  I want to use the one I can download from their site, but I want to be able to switch back to the one in the repositories just in case.  To be specific - I know you can check the box next to the ATI driver in Hardware Drivers (or uncheck it) but I want to make sure if I uncheck it that it will properly go back to using the one I install from the ATI site.  Make sense?  How can I ensure that I can switch between these two properly?

I dont think its possible to switch between them like that, but I could be wrong. Besides the one in the repositories (the check box) is the ATI driver only its about 5 versions old. I prefer the driver you download from ATI as its the most up to date.

---

### Post by Vorian Grey on 2008-08-14
I don't think you can swap like that either.I think you have to choose one or the other.

---

### Post by MaindotC on 2008-08-15
Well I just got done moving and once I have it all set up I'll probably go w/ the driver from the ATI site.

---

