---
title: "Vista forced me to try Ubuntu"
date: 2007-01-25
forum: Testimonials &amp; Experiences
---

### Post by thevinn on 2007-01-25
Well here is my story.

The more I heard about Windows Vista, the less I liked. When I quit playing PC games a few months ago, I got the strong urge to leave Windows for good. So I try out this web page that asks you a few questions and suggests a Linux distro. While I am quite technical, my preference for desktops is towards ease of use. The web page recommended Ubuntu.

I have largely ignored Linux because it didn't run games. So I was delighted to learn about "Live CDs". I downloaded Ubuntu 6.06 and 6.10 ISOs and cut a couple of CDs. I try booting 6.06 from the CD and the experience was incredible. All local devices recognized. This is promising! DHCP/Internet is working! I can surf! I explore deeper...

Insert my Sony Memorystick into my system's integrated media card reader and it is automatically mounted and recognized (wow). However, the MPG movies I have placed on there don't work. A little research thanks to the great community help files and I have the necessary libraries installed. Home made movies play back without a hitch. What, my Excel spreadsheet files open automatically in OpenOffice? Hello! So far this is looking very promising. 

My 6.10 download completes, I have all my data backed up so on a leap of faith I decide to install Ubuntu seriously. Some research shows me that my motherboard's "RAID" feature is really just some software emulation. No problem, hit up BIOS and split the two internal drives into individual devices and I am on my way to installing Ubuntu.

I finally get everything working, and its been three Ubuntu fresh installs and two Windows XP Professional fresh installs and several hours. Pain in the *** getting Windows to boot from a second hard drive, and making it all work from Grub. Live/learn I guess.

Ubuntu is intalled now its time to get those updates. Oh wait, the download is taking forever...I hit up "Software Sources" from the Administration Menu and change the download location (more on this later). Re-try the system update and I am on the information superhighway at over 400 KB/s.

So far so good now its time to get that printer working. HP has a nice native driver for Linux that supports all the bells and whistles. So I install it. Unfortunately, it hangs. And hangs. And hangs. Three hours later I figure out the problem. The HP installer is trying to download required packages. However it is getting them from the "slow" place (what Ubuntu defaults to on install). Alright I'm a clever chap I cancel the install process, carefully take stock of what packages the HP installer is trying to get and then try to get them myself using Synaptic Package Manager. Eventually I get an error about some locked file during the download. Probably because I had to terminate the HP installer process in the middle of something. Okay on a hunch I use sudo to delete some 0 byte file that I dug out of the error details and it continues on. Eventually it gets stuck again, and the only cure is a reboot, followed by attempting to continue with the package downloads. Finally I get all the packages installed, run the HP installer again, and it notices that all the depedencies are already present. It finishes up and I get my test page.

Now I'm pretty stoked despite taking several hours to get a printer driver installed. Time for a bigger challenge, get my two monitors working. My setup:

[B]Two  nVidia GeForce 7800GTX
Two Dell 2405FPW 24" LCD Displays[/B]

Each card drives a display. Two hours later after fiddling with Xorg.conf I get it working. So I start browsing and I am noticing...less than desirable behavior from GNOME applications (not sure where the blame is). Whenever Firefox opens a new window, it opens on a particular screen instead of opening near the previous window. This is pretty annoying. When I launch applications that have a splash screen, the splash screen comes up with each half on a different monitor. For example, OpenOffice applications.

I begin to notice, that my system is freezing up. My spider sense tells me its the nVidia driver, so I spend another hour putting together non nvidia driver versions and single-monitor versions of my Xorg.conf file. Running with the open source nVidia driver eliminates the crash. However I cannot run 1920x1200. Some more searching on the Internet and I find a magic line that hopefully will fix the problem, setting the "Compositing" feature off. This seems to work.

**I have attached my Xorg.conf files (nvidia driver and nv driver) in case anyone is interested in seeing it.**

Unfortunately however, it seems that in the transition from 6.06 to 6.10, the MPG movies on my Sony MemoryStick that used to work, are no longer playing. They open without video and produce screeching noises. I double check and triple check my installed packages, check all available Internet information sources to no avail. This is a bummer, playing back my home made movies is one of the main things i use the computer for.

Alright its 5AM and I stayed up way too late on this.

For the next two weeks, I am trying to stay in Ubuntu as long as possible but I do need to use QuickBooks for my personal finances and that makes me reboot into Windows XP. I want to access my videos so I have to boot into Windows XP for that as well. A long time ago, I tried Firefox for Windows as a replacement for Internet Explorer. Firefox was SO COOL! Until, it started crashing. I told my cousin about the crashes and he said he noticed it too, so he stopped using it. I figured that Firefox on Linux would not crash. I was wrong. Firefox closes unexpectedly at least once a day. That program needs more polish. The Firefox crashes make me run back to Windows XP. I wish it didn't crash.

During these two weeks I am looking for a replacement for Quickbooks. Turns out there is none. Gnucash is way too rough for end-users and the commercial account solutions are either unpolished (non graphical UI, no thanks), overly complex (I dont really need client/server) or overpriced. I try getting Wine to work with Quickbooks but its not having it. Finally I order an old copy of Quickbooks 2003 and manage to get it working with Crossover Office. Its not the smoothest ride but it works. I didn't bother with VMWare because quite frankly, that requires a Windows license (to run Quickbooks)  and is completely unimpressive. I want to show the world that I can do without Windows, not run it in an virtual machine.

Now that Quickbooks kind of works (still haven't used it fully but it runs and prints and I can make journal entries), I spend a few hours getting my Network Attached Storage device working. Couldn't seem to get the NFS mount to work so I installed the SMB tools and got it to work using that. Sometimes the mount mysteriously stops functioning and my whole Linux system hangs. 

Conclusions

**The Good**
Ubuntu has an impressive community, it gives me warm fuzzies to run this distro.
The install was mostly a breeze, all my devices worked.
I have a solution for Quickbooks, this was my biggest obstacle.
Package manager took all the pain out of OS configuration.
Some of my video content was playable.
All my MP3 files are playable.

**The Bad**
The multiple display support needs work.
A lot of my video content is unplayable, especially the videos I recorded onto Memorystick media using a Sony digital camera.
Some font rendering in Firefox is inferior to Internet Explorer.

**The Ugly**
Firefox crashes!
SMB network mount hangs sometimes.
Apparently there are two APIs for developing windowed applications. KDE and Gnome. Programs written for one will not work for the other. Some apps are only available in one flavor of GUI API. This is a mess.

**Thanks to everyone involved in bringing Ubuntu to the masses, its truly amazing. I am going to try to stay in it as long as possible, and try to address any issues or reasons to switch back to XP. I hope I can say goodbye to Windows forever. I think that the possibility of Ubuntu, and Linux in general, becoming a viable desktop solution for the average person is very real and could be here soon. However it is not quite ready yet. I hope I can make some contributions to the community to bring Ubuntu closer to that goal.**

---

### Post by seijuro on 2007-01-26
> **thevinn said:**
> 
**The Ugly**
Firefox crashes!
SMB network mount hangs sometimes.
Apparently there are two APIs for developing windowed applications. KDE and Gnome. Programs written for one will not work for the other. Some apps are only available in one flavor of GUI API. This is a mess.


Sorry to hear about the troubles with your system the good news is this is the exception and not the rule, most systems install with out a hitch. As far as the movies not playing you most likely just need the proper codecs you should find several how-tos in the forums with some searching. I don't know why you and your friend are having trouble with firefox but I have been using it for 4 years and I haven't had it crash once. Actually there is a lot more than just Gnome or KDE however I'll skip the semantics on that. But a bit more good news Gnome applications will run in KDE and KDE apps will run in Gnome when you use apt-get or aptitude to install said application(technically synaptic should do it too but its had problems in the past) it also installs all the required libraries to run. However they will run a fraction faster in their native DE.

---

### Post by meng on 2007-01-26
And there is an increasing number of DE-agnostic applications (Firefox is one example). So the differences between KDE and GNOME are more a matter of personal preference than of restricting application choice or limiting performance.

---

### Post by nalmeth on 2007-01-26
You are made for linux dude :)

Check out [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) for your video files, unless of course they have the DRM plague :-&

I think I must be one of the only people that doesn't have problems with Firefox crashing. Its a non-issue for me.
There are other browsers out there if you really can't enjoy firefox.
Lots of people love Opera (I don't). Epiphany is a much lighter browser, now with some preliminary plugins like adblock.

You can install IE6 in Ubuntu, but that would defeat the purpose I should think.

Anyway, thanks for sharing your experience!

EDIT:
> Apparently there are two APIs for developing windowed applications. KDE and Gnome. Programs written for one will not work for the other. Some apps are only available in one flavor of GUI API. This is a mess.Where'd you hear that? Most KDE apps have no problem running in Gnome, and visa-versa. You will have some extra libraries running, but thats about it. Things aren't so concrete as you think.

And what do you mean about fonts? Are you looking for the Microsoft fonts or something? You will find those on the restricted formats page.

---

### Post by blastus on 2007-01-27
[quote=thevinn]A lot of my video content is unplayable, especially the videos I recorded onto Memorystick media using a Sony digital camera.[/quote]

There are three separate issues here.

1. You are trying to use your digital camera (with the MemoryStick in it) in Ubuntu and can't transfer files from the camera to your computer.

Your best bet for a digital camera is one that supports the Picture Transport Protocol or USB mass storage standard:

[http://en.wikipedia.org/wiki/Picture_Transfer_Protocol](http://en.wikipedia.org/wiki/Picture_Transfer_Protocol)
[http://en.wikipedia.org/wiki/USB_mass_storage_device_class](http://en.wikipedia.org/wiki/USB_mass_storage_device_class)

I'm guessing your Sony camera doesn't support PTP or USB mass storage. Try searching the forums for your camera model and see if others have it working. I have a Kodak camera that supports PTP and works fine in Ubuntu. I did have to configure one thing to get it to work due to a bug in Edgy.

2. You are trying to use your MemoryStick directly in Ubuntu and can't transfer files to your computer or can't playback/view files that exist on the MemoryStick.

I've never used a MemoryStick but if it does work in Ubuntu I would be surprised. The MemoryStick is a proprietary storage device and there is no public documentation for it. I haven't tried using my SD card outside of the camera with Linux but I'm guessing it may not work because SD is a closed proprietary standard, but it is more open than the MemoryStick. 

It's all about standards and formats. The more open a standard and format is the more likely the device that supports that standard and format is going to work on Linux.

If you just want a storage device, you should get a USB flash key/drive that uses the USB mass storage standard and works on all operating systems. All you have to do is plug it in and it works.

3. You have multimedia playback problems.

There is a ton of information and help about multimedia in Ubuntu on the forums. It may be that your system is not configured properly, it may be that you need a codec etc... Try searching the forums.

---

### Post by blastus on 2007-01-27
[quote=thevinn]Some font rendering in Firefox is inferior to Internet Explorer.[/quote]

If you are running Ubuntu Edgy, you should enable FreeType fonts in Firefox/Epiphany:
about:config
font.FreeType2.autohinted = true
font.FreeType2.enable = true

Fonts are a personal preference and those preferences change over time. I used to love the MS TrueType core fonts. MS fonts were one of the very first things I installed when I first converted to Linux. I can tell you for a fact that Ubuntu renders MS fonts exactly the same way that Windows XP does without ClearType turned on. Now I could care less about having MS fonts. Ever since I bought an LCD monitor, I've found the native fonts included in Ubuntu and subpixel rendering to be everything I wanted.

[quote=thevinn]Firefox crashes![/quote]

This is a problem a lot of people, including myself, have experienced and it can be very annoying. Firefox has stability issues and they have only gotten worst on Ubuntu Edgy. Firefox really needs to be rebuilt such that unstable plugins and extensions don't bring down the whole browser. Hopefully they will resolve these issues over time.

---

### Post by blastus on 2007-01-27
[quote=thevinn]Apparently there are two APIs for developing windowed applications. KDE and Gnome. Programs written for one will not work for the other. Some apps are only available in one flavor of GUI API. This is a mess.[/quote]

KDE and GNOME are two different desktop environments. KDE uses QT while GNOME uses GTK. They are incompatible APIs but there are bridges between the two so that you can run KDE applications in GNOME and vice versa. I don't know of a single application written in KDE that can't be run in GNOME and vice versa. Obviously an application's look and feel, and how it integrates with its environment is going to be defined by the desktop environment the application is natively written in. 

This is not a mess. This is choice. Linux is far more customizable than Windows. In Windows the only choice you have is Luna for Windows XP or Aero for Windows Vista. If you don't the way Windows looks and behaves then tough because there's not much you can do about it. Actually, Luna and Aero aren't desktop environments at all, they are more like window managers.

---

### Post by thevinn on 2007-01-28
> **blastus said:**
> 
I've never used a MemoryStick but if it does work in Ubuntu I would be surprised. The MemoryStick is a proprietary storage device and there is no public documentation for it.


The MemoryStick works fine as a storage device. My Dell came with one of those "14 in 1" card reader devices that can accept SD, MD, Memorystick, Compact Flash, and some other format cards. Both the LiveCD and my hdd install of Ubuntu recognized the hardware and installed a driver for it. When I insert a memorystick it appears right on the Gnome desktop as a mounted usb storage device. It even has a similar looking icon!

I can access the files fine, the problem is playing back the videos (images are ok). Originally, I could not get the videos to work at all. They were opening in the Totem Movie Player. It tried to play them but there was no video and the sound was corrupted, no trace of anything recognizable.

I tried installing the recommended proprietary binary codecs but that did not help. Recently I tried launching gxine instead of MPlayer to to view the videos and now the video appears and the sound is almost right except for a high pitched sound not present when I play back under Windows.

Note, this is all under 6.10.

What is interesting is that the 6.06 LiveCD was able to play the videos just fine with Totem, after installing the proprietary binary codecs.

---

### Post by asnd16 on 2007-01-29
Got to be honest with the current position that Microsoft has on the market and the type of computer that I have.  I choose to use Ubuntu because of the coming of Vista and me not being able to run it on my laptop, and I have used Ubuntu for roughly 3 months and love it.  A couple customizations take a bit to decide on but other than that it is a awesome distro!

---

### Post by spockrock on 2007-01-29
umm......about the openoffice splash etc, I get get that too.....running nvidias twinview.......I am not sure but the amarok splash open on my primary monitor in the center....so I am thinking its app based why certain splashes one in the middle.

Also can I ask why you are using two 7800GTX cards to drive those monitors, one would suffice??

Or did you have an sli setup before.....

---

### Post by TheMono on 2007-01-29
You know what really impresses me here - a new guy to Ubuntu, who has gone through the effort to read up and learn everything he needs from restricted formats to video drivers etc.

I'm impressed, my friend. Give you another few months and you'll be a pro! You've obviously got the willingness to learn which is the most important part of making linux work for you - once you are past the initial setup of working for linux!

---

### Post by sloggerkhan on 2007-01-29
I agree that multi-monitor is a pain, particularly for laptops and presentations. Video works fine so long as you get ALL the plugins. Font rendering isn't really firefox's fault. I'd make sure you have MS fonts installed. The window api things is being worked on, though I've never met a program that wouldn't run on either, even if uglier on one.

---

### Post by thevinn on 2007-01-29
> **spockrock said:**
> why you are using two 7800GTX cards to drive those monitors, one would suffice??

For gaming mainly.

**Well its been 7 full days of running under Ubuntu!**

---

### Post by thevinn on 2007-01-29
> **sloggerkhan said:**
> I agree that multi-monitor is a pain, particularly for laptops and presentations. Video works fine so long as you get ALL the plugins. Font rendering isn't really firefox's fault. I'd make sure you have MS fonts installed. The window api things is being worked on, though I've never met a program that wouldn't run on either, even if uglier on one.

My machine still crashes with the nVidia driver. I'm using the nv driver and settling for  1600x1200 letterboxed on each screen (versus 1920x1200). If thats the cost of not being forced into Vista, so be it.

The videos are working except that there is a very high pitched sound coming from the audio portion. I haven't looked into it yet. I'm using a Sound Blaster Audigy 4. Not sure if that is a fully supported card.

I added the MS fonts and changed the settings in about:config as recommended but I don't really see a change. Here is the site that is giving me a problem

[http://www.fidelity.com](http://www.fidelity.com)

If you click on "Accounts & Trade" there is a pop down navigation bar that has the last two items cut off because of rendering. Internet Explorer running under Ubuntu (from a Crossover Office installation) renders it correctly. I'm not sure if this is a problem with the site.

---

### Post by beniwtv on 2007-01-30
Just my 2 cents..

Did you try to use VLC or Xine to play your videos?

They're both available form Add/Remove programs or Synaptic.

---

### Post by thevinn on 2007-01-30
> **beniwtv said:**
> Just my 2 cents..

Did you try to use VLC or Xine to play your videos?

They're both available form Add/Remove programs or Synaptic.

Very interesting. I tried VLC and it works better.

To summarize:

- Totem in Ubuntu 6.06 with restricted codecs plays my MPG files just fine
- Totem in Ubuntu 6.10 with restricted codecs does not play my MPG files at all
- Gxine in Ubuntu 6.10 with restricted codecs plays the MPG files but the audio has a high pitched noise added to it.
- VLC in 6.10 with restricted codecs plays the MPG files, and the audio is correct if both the application volume level and operating system level is set correctly (to avoid clipping).

I find it interesting that the same codecs work correctly in some applications but not others?

Well this is not going to stop me from using Ubuntu but to be honest, this experience with multimedia was a bumpy ride to say the least.

---

### Post by beniwtv on 2007-01-30
> **thevinn said:**
> 
I find it interesting that the same codecs work correctly in some applications but not others?

Well, this is not exactly true. They do not use the same codecs. Totem, as it comes in Ubuntu, is based on the gstreamer framework. VLC or Xine use their own, built-in frameworks (Xine-ui is built on libxine).

While it is true that both frameworks may share the same system libraries, but it's at application level how they use these libraries.

So, installing parts of gstreamer or libxine does not mean both frameworks can use the codecs you installed for the other one.

The only codecs that are really shared, are the w32codecs, as these are in fact, windows dll's, and both xine and gstreamer have wrappers for them, AFAIK, at least xine does.

> **thevinn said:**
> 
Well this is not going to stop me from using Ubuntu but to be honest, this experience with multimedia was a bumpy ride to say the least.

These are good news! :D  Agreed, Ubuntu may have some problems, but after all it's still better than the Windows nightmare (don't ask me why I call it this way..).

What we can do is file bug reports, do feature suggestions, to help our Ubuntu child to grow even more mature :p

But every day Ubuntu is going better, personally I can't wait until Feisty, which looks really promising!

---

### Post by happy-and-lost on 2007-01-30
You are going to be one heck of a Ubuntu Power User :)

The pain is worth it in the end. Wait 'till you find Compiz/Beryl ;)

---

### Post by thevinn on 2007-01-30
> **happy-and-lost said:**
> Wait 'till you find Compiz/Beryl ;)

Actually I'm fine with the default GNOME desktop. What really matters to me is that my applications work (Quickbooks), Firefox doesn't crash, and my multimedia files play correctly. Having the video cards work in 1920x1200 would be nice too.

The latest problem is the mouse button doesn't work in this game (but it works in windows) give it a try, its web based:

[http://gprime.net/game.php/neon](http://gprime.net/game.php/neon)

---

### Post by thevinn on 2007-01-30
Well I tried to install Java and failed, got these errors:

error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_10-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_10-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_10-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_10-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_10-fcs.i586
        /bin/sh is needed by jre-1.5.0_10-fcs.i586

Why is it so hard to install Java? It should be a matter of a one or two clicks. This is disappointing.

---

### Post by me1on on 2007-01-30
If you want to easily install Java, the codecs you're missing, and a few other things, I recommend using [[COLOR="Blue"]Automatix[/COLOR]]("http://www.getautomatix.com/"). Also try checking out the [[COLOR="Blue"]Ubuntu Guide[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"), it has tons of information and tips for using Ubuntu. Good luck and hopefully your Ubuntu issues get solved quickly. :)

---

### Post by thevinn on 2007-02-01
I'm getting source code to some small system tools to get the hang of retrieving source and compiling it, debugging, etc... to see if maybe I can fix some of the less desirable dual monitor behaviors of the apps I use.

---

### Post by thevinn on 2007-02-02
Well now I can't print to my HP 2430. I submit the job (printing a web page from Firefox) and it goes into the queue but the Printing mananger says "can't connect to device" even though its on and working.

---

### Post by thevinn on 2007-02-03
Printer fixed. Problem was that the printer was on DHCP and after several reboots / network resets, the printer got a different IP address. I turned off all the network naming services so everything is referenced by Ip. I will configure the printer to use a static private IP address.

Unfortunately, I had to reboot into Windows so I could write a VBA script in a spreadsheet. Whats the equivalent for Ubuntu? OpenOffice + ??

---

### Post by BoyOfDestiny on 2007-02-03
> **thevinn said:**
> Well I tried to install Java and failed, got these errors:

error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_10-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_10-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_10-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_10-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_10-fcs.i586
        /bin/sh is needed by jre-1.5.0_10-fcs.i586

Why is it so hard to install Java? It should be a matter of a one or two clicks. This is disappointing.

Hmm, are you trying to install java from synaptic? If not give that a go. Search for sun-java or jre. It should be 2 clicks tops ;)
Ah video drivers, I use the open source ones, less of a headache than the little black boxes that are binary drivers. 
My laptop has intel, for my desktop (exact monitor you have) I can get 1920x1200 with an ati radeon 9250 (using the open source ati driver, out of the box with ubuntu.) 
Not fantastic, but the card should be about $50. Not sure if that could handle such a huge res dual monitor wise though... 
There is also an open source nvidia driver in the works, but I have no idea how that's going... May be worth looking into though.

As for Open Office macros, google yields this

[http://www.ooomacros.org/](http://www.ooomacros.org/)

Best of luck to you.

---

### Post by thevinn on 2007-02-03
> **BoyOfDestiny said:**
> Hmm, are you trying to install java from synaptic?

Well I finally tried Automatix as per the suggestion and it worked.

My beef, is that when you install Ubuntu, you get Firefox installed automatically. When you go to a page that has a Java applet, it renders as "Plug in missing, click here to get it". Now I clicked and after sputtering for a few seconds looking for the plugin, Firefox gave up and basically told me I had to install it manually. It was considerate enough to provide a link. Unfortunately the link was to

[http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp)

Trying to install Java from this link is extremely painful for the non Linux-initiated. Now this is just my opinion but Firefox should have a smoother experience for getting the plugin for one of the most popular cross platform development languages.

> Ah video drivers, I use the open source ones, less of a headache than the little black boxes that are binary drivers. 

I'm using the nv driver (open source I think) because the nvidia driver crashes every once in a while no matter what I do. The open source driver won't run in 1920x1200. Or at least I can't get it to work. I already have two nvidia cards and I'm not buying an ATI card(s). I guess I will just keep my fingers crossed that either the nv driver or the binary driver will get fixed.

> 
As for Open Office macros, google yields this

[http://www.ooomacros.org/](http://www.ooomacros.org/)


Open Office runs VBA scripts? That is amazing!!!

---

Still working on trying to get sources compiling and debugging, not having much luck there. I will try to locate some kind of users group or something in miami and see if someone can help me.

---

### Post by BoyOfDestiny on 2007-02-03
> **thevinn said:**
> Well I finally tried Automatix as per the suggestion and it worked.

My beef, is that when you install Ubuntu, you get Firefox installed automatically. When you go to a page that has a Java applet, it renders as "Plug in missing, click here to get it". Now I clicked and after sputtering for a few seconds looking for the plugin, Firefox gave up and basically told me I had to install it manually. It was considerate enough to provide a link. Unfortunately the link was to

[http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp)

Trying to install Java from this link is extremely painful for the non Linux-initiated. Now this is just my opinion but Firefox should have a smoother experience for getting the plugin for one of the most popular cross platform development languages.



I'm using the nv driver (open source I think) because the nvidia driver crashes every once in a while no matter what I do. The open source driver won't run in 1920x1200. Or at least I can't get it to work. I already have two nvidia cards and I'm not buying an ATI card(s). I guess I will just keep my fingers crossed that either the nv driver or the binary driver will get fixed.



Open Office runs VBA scripts? That is amazing!!!

---

Still working on trying to get sources compiling and debugging, not having much luck there. I will try to locate some kind of users group or something in miami and see if someone can help me.

Right, well I've heard automatix can cause some "breakage" going from one ubuntu release from the other... 

As a general rule (well more like changing of a habit) try and use the repositories to install something, vs grabbing it off a webpage. I'm sure Ubuntu will keep improving things (as of the next release, clicking on an mp3 or what have you prompts you to enable "universe" and fetch the codeces) For regular users (I think you qualify as at least power user in my opinion :)) Add/Remove should cover the bases, even having flash in there now, with the preferences allowing you to show proprietary and non.

Anyway with the drivers, hopefully the next release will have it covered.

I think you are doing fine, Vista scared me, rather longhorn did, so I've been with Ubuntu since 2004. It may seem a tad annoying to go with the official repos, but I tell you, when you've updated from one Ubuntu release to the next, and then again to the next... And all the software gets updated, configured, with almost zero interaction from me... Has made it worth while. 

Any suggestions and criticisms may be worth while to file bug reports. The few I've pointed out a while back are currently fixed, and I'm a happy camper. (If you were to pick up Ubuntu warty from '04, be prepared for nautilus to not have a search, no gui way to dist-upgrade, and hitting your cd eject button does nothing...) So I assure you the software will improve, and that you can actually have some influence on the development, without writing a line of code (unless you are so inclined.) :)

Keep at it!

EDIT: What are you trying to compile? I guess it varies, but in general make sure you have build-essential installed. Run ./configure, look for missing libraries, pick them out in synaptic usually with -dev on the end... Keep at it until no errors. Then make. Then sudo make install (or you can do checkinstall). It's a little tedious, but once you have the dependencies, at least in my experience you can just download the next version, and do ./configure && make
As I'm using feisty (alpha of next ubuntu) they've added essentially all the apps I need, I only compile zsnes, uade, and sdlmame. :)

---

### Post by thevinn on 2007-02-03
I don't really know what I'm trying to compile. I would be happy compiling anything. My goal is to fix a bug in Firefox although that has a ton of dependencies. VLC media player has a bug as well.

The development process confuses me, can you suggest a good starting point for reading?

I have build-essential installed (from Synaptic).

---

### Post by BoyOfDestiny on 2007-02-04
> **thevinn said:**
> I don't really know what I'm trying to compile. I would be happy compiling anything. My goal is to fix a bug in Firefox although that has a ton of dependencies. VLC media player has a bug as well.

The development process confuses me, can you suggest a good starting point for reading?

I have build-essential installed (from Synaptic).

Hmm, actually it's mostly these forum folks that helped me out and googling.

sudo apt-get install apt-build 

sudo apt-build install nameofapp

Will help you get the dependencies you need if that app is in the repo, and you want to try and build your own version...

I think your best bet is post a specific question in these forums. Just learning little by little.

It's possible your bugs may already be fixed in later releases (has happened to me), do you have backports enabled (you can choose it from system->administration->software preferences, synaptic, or from commandline: nano /etc/apt/sources.list

Those two apps you mentioned, I have a feeling are trickier to build (especially VLC due to codecs and the like)

I'd say just google them specifically, you may find a nice tutorial...

Barring all that, you can try searching launchpad for a bug report, or add one. See if it is resolved or has a known work-around.

Or, you can try going to the irc channel for that app, I've done that with audacious for example, and the devs may help you out. In one case a bug I mentioned was fixed within minutes, and I was able to download the update and build from svn (subversion). Some devs, really really amaze me! Actually with VLC years ago, the bug took a little longer to fix. But I submitted a small portion of the file giving me trouble to their ftp (worked in a previous vlc) in the next release all was well again...

---

### Post by sloggerkhan on 2007-02-04
OOO doesn't run all VBA scripts, i think it's more standards oriented torwards basic or something. I does run some of them, though.

---

### Post by thevinn on 2007-02-04
Ok I gave the chroot environment another shot. I found this guide:

[http://ubuntuforums.org/showthread.php?p=904320#post904320](http://ubuntuforums.org/showthread.php?p=904320#post904320)

I set up the chroot environment as root. I did

apt-get update
apt-get install dpkg-dev

This generated some errors but they were fixed by copying some stuff out of /etc/apt into my chroot file system.

I did

cd /src

then

apt-get source celestia

Celestia is a small stand-alone gui app that simulates stars in the universe, I thought it would be a good candidate to build since it is not a system utility. I was wrong. I got the sources but can't figure out how to build it.

Can someone recommend an easy to get and easy to build executable that I can play with?

---

### Post by BoyOfDestiny on 2007-02-04
> **thevinn said:**
> Ok I gave the chroot environment another shot. I found this guide:

[http://ubuntuforums.org/showthread.php?p=904320#post904320](http://ubuntuforums.org/showthread.php?p=904320#post904320)

I set up the chroot environment as root. I did

apt-get update
apt-get install dpkg-dev

This generated some errors but they were fixed by copying some stuff out of /etc/apt into my chroot file system.

I did

cd /src

then

apt-get source celestia

Celestia is a small stand-alone gui app that simulates stars in the universe, I thought it would be a good candidate to build since it is not a system utility. I was wrong. I got the sources but can't figure out how to build it.

Can someone recommend an easy to get and easy to build executable that I can play with?

Celestia is in the repos, did you try apt-get build (to fetch the dependencies) and give it a whirl?

Hmm, you found my old script... Are you using a chroot just to have a separate build environment? You don't need to... Anyway, I've found uade easy to compile.

[http://zakalwe.fi/uade/](http://zakalwe.fi/uade/)

If you have build-essential, you should have all the dependencies it needs. Now if you want some amiga tunes

Check their page for links, or you can have an instant collection with

rsync -avz zakalwe.fi::chip /local/path/ 

replace /local/path with wherever you want it /home/yourusername/uade for example. 
You have rsync already installed with ubuntu, it's pretty sweet. lets you copy files and then if you run it again, just the changes (vs sending/ re-downloading the entire file(s) over again) I use it for backing up my data to another couple of machines, definitely saves on bandwidth...

Hope this does the trick.

---

### Post by MetalMusicAddict on 2007-02-04
Have you got the GFX/LCD issue fixed? What brand of card do you have? Theres been tons of issues with my EVGA card. I have the same card and screen you have but only one of each. I was looking at going to 2 LCDs but I think Im just gonna go for the 3007.

---

### Post by MoonBlossom on 2007-02-04
I'm also relatively new to linux (less than 6 months). I use Kubuntu because I found KDE more appealing to me. In the beginning I couldn't play most of my videos until a friend tip me about [Automatix]("http://www.getautomatix.com/") which is a program that makes the installation of several programs very easy. Automatix can install most of the codecs you need to play videos.

I use [Kmymoney ]("http://kmymoney2.sourceforge.net/index-home.html") as my finance manager, if you don't like it there is also this site [http://linuxappfinder.com/windows](http://linuxappfinder.com/windows) which has a list of Windows software alternatives in Linux. Very useful specially for new people moving to linux!!:)

---

### Post by thevinn on 2007-02-05
> **MetalMusicAddict said:**
> Have you got the GFX/LCD issue fixed? What brand of card do you have? Theres been tons of issues with my EVGA card. I have the same card and screen you have but only one of each. I was looking at going to 2 LCDs but I think Im just gonna go for the 3007.

The LCD is kind of working. The nvidia binary driver crashes so I am using the open source nv driver. Dual LCD support works great, except that I can't run in 1920x1200. So I am using 1600x1200 on both screens for now and keeping my fingers crossed that the issue gets resolved some day. In the OP I have attached my Xorg.conf file in case anyone wants to see how I did it.

I have two GeForce 7800 GTX 512mb

---

### Post by thevinn on 2007-02-05
> **MoonBlossom said:**
> I use [Kmymoney ]("http://kmymoney2.sourceforge.net/index-home.html") as my finance manager

But I am using Gnome (?). People say KDE apps will work. Which package should I download? Do I need to download anything else? Do I have KDE installed?

---

### Post by Kemik88 on 2007-02-05
[QUOTE=thevinn]What really matters to me is that my applications work (Quickbooks)[/QUOTE]


Did you check out Eqonomize ? I'm using that to help manage my University funds. Gotta make sure I'm not spending myself in to too much debt this semester ;)

You can find info to install it [here]("http://www.ubuntugeek.com/manage-your-personal-accounts-with-eqonomize.html"). Honestly the interface colours are backwards on that screenshot. Here's one from my PC...

[[IMG]http://img457.imageshack.us/img457/5121/screenshot1lz1.th.png[/IMG]](http://img457.imageshack.us/my.php?image=screenshot1lz1.png)

Sorry for the black lines. There's numbers under there if u haven't guessed ;)

---

### Post by thevinn on 2007-02-05
> **Kemik88 said:**
> Did you check out Eqonomize ?

Thanks. I installed it, it is a nice looking application. Unfortunately it is missing these features:

- Balance Sheet Report
- Profit and Loss Statement
- Multiline General Journal entries

---

### Post by Kemik88 on 2007-02-06
You need a P&L and BS for your personal accounts? Are you self employed?

There's a fairly large difference between doing personal accounts and business accounts.

---

### Post by bmartin on 2007-02-06
I'm amazed there haven't been more suggestions on here as to how to fix Firefox.

I had problems using Firefox in Fedora. They were remedied only when I removed my Mozilla settings folder in my home directory.

Before removing the settings folder, you should know that doing so will require you to reinstall all of your plug-ins. Flash (32-bit only) and Java can be easily installed using EasyUbuntu ([http://easyubuntu.freecontrib.org/index.html)](http://easyubuntu.freecontrib.org/index.html)).

Rather than completely removing your settings, I'd advise you to move them. You can do this by opening a terminal and moving the .mozilla directory in your home directory -- I'd rename it to something like .mozilla-old. Restart Firefox; it should look like it did the first time you loaded it.

Plug-ins are usually the culprit when it comes to Firefox crashes. I use AdBlock, DOMInspector, Download Statusbar, FireFTP, ForecastFox, and NoScript with Firefox and they seem to play nicely.

I hope you get FF to work properly. The abundance of high-quality FOSS like Firefox is what brought me to Linux in the first place. Most of the software I use either runs on Google or was ported to Windows from Linux; it made the transition easy.

---

### Post by MoonBlossom on 2007-02-08
> **thevinn said:**
> But I am using Gnome (?). People say KDE apps will work. Which package should I download? Do I need to download anything else? Do I have KDE installed?

I believe Synaptic (Aptitude in Kubuntu) would install the additional packages you need in order to run a KDE application in Gnome. :)

---

### Post by CheeseEatingBulldog on 2007-02-08
Have you had a look at GNU-cash ([http://www.gnucash.org/]("http://www.gnucash.org/")).

It's also in the repos.

---

### Post by thevinn on 2007-02-08
> **CheeseEatingBulldog said:**
> Have you had a look at GNU-cash ([http://www.gnucash.org/]("http://www.gnucash.org/")).


Interface is way too primitive and unfriendly.

I'm using Crossover Office for now. Sometimes Quickbooks crashes on launch but usually I can get it working by running it over and over until it loads.

---

### Post by mr.blacke on 2007-02-10
What about vista theme? That's like emerald theme on beryl. Should that be a coincidence? 
Don't think so...

---

### Post by ubuntu27 on 2007-02-11
> **thevinn said:**
> Well I tried to install Java and failed, got these errors:

error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_10-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_10-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_10-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_10-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_10-fcs.i586
        /bin/sh is needed by jre-1.5.0_10-fcs.i586

Why is it so hard to install Java? It should be a matter of a one or two clicks. This is disappointing.

Java is in the Repository...
It should be just one two clicks like you said.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Bu the way what's your computer like? What hardware aspe. does it have?

Also, did you do a fresh install of Edgy Eft (Ubuntu 6.10) or did you do a distro upgrade from Dapper Drake (Ubuntu 6.06) ?

It's always better to do a fresh install than do a distro-upgrade.

---

### Post by rko618 on 2007-02-11
I would like to congratulate you on being a prime Linux user.  You ran into several difficult challenges but you sought out the solution and didn't give up.  Good job!

---

### Post by graigsmith on 2007-02-12
this is basically why i quit using microsofts os's.  i was interested in vista before i heard about these reasons.

1.  i *actually* read their eula for windows xp.  talk about a restrictive and scary legal document.  For one it says you didn't actually buy it. you only bought the license and that the software still belongs to Microsoft.

2.  I do not want DRM.  i definately DONT want to be forced to buy new monitor and videocard.  building an expensive drm thing into vista and passing the cost onto customers.  This is perhaps the WORST decision they have ever made.   And it's probably why alot of the cool vista features that were slated to be in vista never made it in. like WinFS.

those 2 reasons alone caused me to look for alternatives.  So glad i found ubuntu.

---

### Post by lamalex on 2007-02-12
> **blastus said:**
> There are three separate issues here.

1. You are trying to use your digital camera (with the MemoryStick in it) in Ubuntu and can't transfer files from the camera to your computer.

Your best bet for a digital camera is one that supports the Picture Transport Protocol or USB mass storage standard:

[http://en.wikipedia.org/wiki/Picture_Transfer_Protocol](http://en.wikipedia.org/wiki/Picture_Transfer_Protocol)
[http://en.wikipedia.org/wiki/USB_mass_storage_device_class](http://en.wikipedia.org/wiki/USB_mass_storage_device_class)

I'm guessing your Sony camera doesn't support PTP or USB mass storage. Try searching the forums for your camera model and see if others have it working. I have a Kodak camera that supports PTP and works fine in Ubuntu. I did have to configure one thing to get it to work due to a bug in Edgy.

2. You are trying to use your MemoryStick directly in Ubuntu and can't transfer files to your computer or can't playback/view files that exist on the MemoryStick.

I've never used a MemoryStick but if it does work in Ubuntu I would be surprised. The MemoryStick is a proprietary storage device and there is no public documentation for it. I haven't tried using my SD card outside of the camera with Linux but I'm guessing it may not work because SD is a closed proprietary standard, but it is more open than the MemoryStick. 

It's all about standards and formats. The more open a standard and format is the more likely the device that supports that standard and format is going to work on Linux.

If you just want a storage device, you should get a USB flash key/drive that uses the USB mass storage standard and works on all operating systems. All you have to do is plug it in and it works.

3. You have multimedia playback problems.

There is a ton of information and help about multimedia in Ubuntu on the forums. It may be that your system is not configured properly, it may be that you need a codec etc... Try searching the forums.

SD cards work. I actually just transferred in a bunch of pictures from a friends party with my internal card reader :) xD is in development, and I stay away from sony so I don't know there.

---

### Post by thevinn on 2007-02-12
> **ubuntu27 said:**
> Java is in the Repository...
It should be just one two clicks like you said.

Yeah the last thing I did was try installing it from the repository.

The problem I see is that Firefox comes with Ubuntu, and when you try a page with a Java applet for the first time, Firefox' handling of the missing Java plugin leads you to an unfriendly installation as I mentioned in my other post. This is a rough spot that needs to be polished.

> Bu the way what's your computer like? What hardware aspe. does it have?

Dell Dimension XPS600, dual core 3.2ghz intel, 2gb RAM, 2xGeForce 7800gtx, SB Audigy 4.

> Also, did you do a fresh install of Edgy Eft (Ubuntu 6.10) It's always better to do a fresh install than do a distro-upgrade.

Fresh install.

> **graigsmith said:**
> this is basically why i quit using microsofts os's.  i was interested in vista before i heard about these reasons.

Yep same here, the EULA for Vista made me upset and DRM is not useful to me. I could have just stayed with Windows XP, but it makes me uncomfortable to accept the Microsoft security updates.

My plan was to get Ubuntu working but keep using Windows until the last minute. I got Ubuntu working but then I changed my plan, now I try to run in Ubuntu as much as possible. Since I got everything in Ubuntu working, I have not switched to Windows except to use Adobe Photoshop. At first, I tried using GIMP but the interface frustrated me greatly. Later, I got Photoshop working in Crossover Office.

--------------

A lot of little details in many of the applications need polish. A short list comes to mind:

- VLC media player cuts off the movie total running time in the status bar
- Totem doesn't hide all interface in full screen mode
- Creating a new window in Firefox doesn't clone the current window's navigation history and current page the way IE does.
- I keep getting asked if I want to run photo editor when I insert a memory stick, even after checking the box to remember my choice from now on.
- Can't rename files and folders on the desktop or in the file browser by just clicking in the text
- Many other little details
- Many system utilities apply the changes made to controls immediately instead of having an "OK, Cancel, Apply" paradigm.

---

### Post by rko618 on 2007-02-12
> **thevinn said:**
> 
A lot of little details in many of the applications need polish. A short list comes to mind:

1. VLC media player cuts off the movie total running time in the status bar
2. Totem doesn't hide all interface in full screen mode
3. Creating a new window in Firefox doesn't clone the current window's navigation history and current page the way IE does.
4. I keep getting asked if I want to run photo editor when I insert a memory stick, even after checking the box to remember my choice from now on.
5. Can't rename files and folders on the desktop or in the file browser by just clicking in the text
6. Many other little details
7. Many system utilities apply the changes made to controls immediately instead of having an "OK, Cancel, Apply" paradigm.

First I'd like to congratulate you on making the switch to Linux.  Good work.

I'd like to point out however that just because a program behaves a certain way in Windows that doesn't mean _that's the right way_.  I believe that your suggestions 3, 5, and 7 are actually intended to be that way.

---

### Post by ubuntu27 on 2007-02-13
> **thevinn said:**
> 

My plan was to get Ubuntu working but keep using Windows until the last minute. I got Ubuntu working but then I changed my plan, now I try to run in Ubuntu as much as possible. Since I got everything in Ubuntu working, I have not switched to Windows except to use Adobe Photoshop. At first, I tried using GIMP but the interface frustrated me greatly. Later, I got Photoshop working in Crossover Office.


Glad you made it! :KS 
Congratulation and welcome to the Ubuntu & GNU/Linux Community. :popcorn: 

> **thevinn said:**
> 
A lot of little details in many of the applications need polish. A short list comes to mind:

- VLC media player cuts off the movie total running time in the status bar
- Totem doesn't hide all interface in full screen mode
- Creating a new window in Firefox doesn't clone the current window's navigation history and current page the way IE does.
- I keep getting asked if I want to run photo editor when I insert a memory stick, even after checking the box to remember my choice from now on.
- Can't rename files and folders on the desktop or in the file browser by just clicking in the text
- Many other little details
- Many system utilities apply the changes made to controls immediately instead of having an "OK, Cancel, Apply" paradigm.

Some of those things are just preference or behavior made by the Desktop Environment.
Like the "Rename files and folder with just one click" that is a default behavior in KDE, but not in GNOME. 

For more, take a look at [here]("http://www.psychocats.net/ubuntu/kdegnome"):

[KDE and Gnome Comparison]("http://www.psychocats.net/ubuntu/kdegnome")


Also, did you try the browser called Epiphany? It's much simpler and smaller than Firefox and it doesn't have so many option regarding extensions/plug-ins for now, but it serves it has not failed me in regards to perfomance.

the package name is "epiphany-browser"
there is another package in the repository with the name of epiphany, but it is a game.

---

### Post by Vivix729 on 2007-02-19
Couple of suggestions:

Have you tried Swiftfox?  It's Firefox that's designed for specifically for your CPU.  You can get it using Automatix or from Ubuntu's repos.

Also, have you tried configuring xorg.conf and manually adding 1920x1200 resolution?

---

### Post by garybrlow on 2007-02-19
You can also use the Official Firefox Installer from [http://www.mozilla.com/en-US/firefox/]("http://www.mozilla.com/en-US/firefox/"). It come pre-compiled and ready executable. Just unzip it to your home directory/folder or a subdirectory/subfolder. You do have to manually put shortcuts via the Application menu or your own shortcut somewhere else. Just like in windows, all program files for firefox are placed in one folder unlike the one that debian/(K/X)Ubuntu has. It can update itself as the official version gets updated. the repositories tend to update their on a later. Just run the script executable and you're good to go. I have found this version more stable and have been using it ever since. Plugins like Java runtime and flash have to be placed manually in the plug-ins folder either by copying the system supplied ones or providing symbolic links. This is non standard debian/(K/X/E/U)buntu installation but it is the official standard firefox installation. Debian, Ubuntu's mother distro tends to change installation folders for some applications. This also true for official versions the Apache Web Server, the OpenOffice.org and the Squid Proxy Server if your planning to use them. You might be confused when reading official manuals as they might refer to a different locations from what is actually there in your computer. This is a common difference for Debian/Ubuntu deb installers located in the repositories and official installers.

Using official installers as to the debs has its advantages especially when the Feature Freeze for a distro version is in place, there are no backports available, and you need to update to the latest version either for bugfixes or newer features. Automatic updates from repositories do not cover nondeb-based installations. You have to update them manually. But as usual, whatever you need and whatever floats your boat is always fine. Its a matter of preference. 

Ubuntu does grow on you. I have been using Xubuntu  for 8 months now. It has been my best Linux experience ever. Way back I had a not so nice experience with Redhat and Mandrake(Mandriva now) that included a hard disk crash and bizzare sound and video problems. That discouraged me to use Linux at that point. But when is used Ubuntu it ran out of the box for me. Though I do dual boot with windows xp which i use for windows games, anything midi related(since linux midi is a work in progress,  definitely needs more attention from developers in general and should be available out of the box like in windows), and chkdsk utility for the NTFS-3G(am sure you'll be using this one later) NTFS read/write interface. :P

Welcome to Linux!!! Welcome to the (K/X/E/U)buntu Universe!!!

Cheers!!!

GaryBrlow ):P

---

### Post by PineGroveDave on 2007-02-19
I'm posting this one on behalf of one of my employees who has been a MS advocate for a very long time. You see, he's a sharp guy and I've taken every opportunity to plant the "Linux Seed" in his brain. I've been running Linux now for over 4 years (1st Gentoo, now Ubuntu) and have never looked back. Anyway, he recently got his Vista and I stated that he may have problems with a lot of his music and video files playing...let alone running Aero on a PC only 1 year old.

So last night I get the call...
Rick: "Well you were right. All my music won't play even though I own all the CD's!!!"
Me: "Whoa...So what I warned you about is true, yeah?"
Rick: "Yep. Pisses me off. I'm downloading Ubuntu as we speak and blowing away Vista."
Me: "Welcome to the Dark Side my son."

:lol:

He'll have a learning curve, but I pointed him here and I'll help him when I can. Like I said, he's a sharp guy and I'm sure he'll do fine.

Thank you Microsoft for Vista. The ranks of Linux converts are growing thanks to you. 8)

---

### Post by ve9cbc on 2007-02-19
I'm new to Ubuntu as well, thanks to Microsoft. 

I signed up to beta test Beta 2 and RC1 of Windows Vista. I tried 32 bit and 64 bit on my AMD 64 bit computer with 1GB of memory ,a 10000 rpm Western Digital drive, and a ATI Radeon X1600 Pro video card. 

Looks a lot like Apple; no suprise though - one of Apple's top programmers went to Microsoft. I was vastly disappointed on how the OS performed (very limiting, memory hungry (1 GB just to run smooth- ouch!), and more than likely filled with spyware from Microsoft who possibly reports it to the proper authorities. 

There are a few things that I have to get used to with Ubuntu; but man the freedom is truly worth it. Choice is a beautiful thing.:-D

---

### Post by nick.inspiron6400 on 2007-02-20
I was close to buying Vista. But i am very unhappy how Microsoft has put 4 versions and they all have different uses.o, no network security
Business: 

Home Basic: XP New theme no areo
Home Premium: MCE new theme areo, no network security
Business: Areo, no multimedia
Ultimate: The whole works!

I think $400 for Vista is horrible price and not woo, no network security
Business: rth it. I wont pay for that then $300 for Office.

Microsoft is going to loose market share.

Nick.

---

### Post by maestrobwh1 on 2007-02-25
[www.getautomatix.com](www.getautomatix.com)

I only got this to work on a fresh install.  It is a free package that installs all of those things without hassle, like Java, Flashplayer, Acrobat, codecs for media, including the Apple iPod AAC files.  

I do agree that there is some annoyance between KDE and Gnome.  I am a KDE fan, and generally, I have had lots of luck with Gnome apps working under KDE, although, I would suspect that would not be true so much in reverse.

---

### Post by thevinn on 2007-02-27
Well I think I am giving up on Ubuntu, I just rebooted back into Windows XP.

My Crossover Office trial expired so I couldn't run Quickbooks. I went to Codeweavers and bought the full version but I had trouble getting it to work.

First I tried "Register and unlock" from the Crossver menu but after putting in my email and password it said that it couldn't connect to the Internet.

Then I tried installing the package but it kept saying that it conflicted with the existing installation.

So I wiped the existing installation (including all bottles), opened the package and installed it. Seemed to work but when I tried to install Quickbooks, first it said that Quickbooks already existed. Then when I said go ahead and install a new copy anyway I got an error "missing COMMAND.COM".

Screw this, way too much trouble. Linux is not ready for the desktop yet.

Now I'm back in XP and I can enjoy 1920x1200 again (this resolution didn't work with the nv driver, and the nvidia driver crashed). No more issues with surfing websites in Firefox and suddenly things going very slow or crashing the browser. Photoshop is running nice and fast again.

Maybe in another 6 or 12 months things will be better? I can only hope.

---

### Post by pkbutrfli on 2007-02-27
Noooooooo don't go baaaaack!!!!

I just installed Ubuntu and I'm online for the first time ever with Linux.  Don't go back to XP!  It's nothing but planned obsolescence.  If manufacturers suddenly told you had to buy a new stove, washing machine, sofa every year or two - would you?????  It's an equivalent amount of money.  You pay about the same for friggin stove as you do a new fault-filled computer with MS on it!  It would be less headache to install a new stove in your kitchen every other year.  I just remodeled, I'm speaking from experience!

I just installed Ubuntu 5 friggin minutes ago after reading, studying and sweating for a week!!!!!  I thought it would be harder!  I thought I had to compile stuff!  I thought I'd have to go back to my techie days and actually remember some of it!  I thought I had to make sure my hardware... all of it... would work with whatever flavor.  I was frustrated when I found Ubuntu and didn't even look to see if it was compatible.  Screw it... INSTALL!  

Don't go back to MS.  They're evil!!!!!!!!!  Your XP will fail you soon enough... just like mine did bwahahahahahahaha  Then you're stuck with Vista, just like I was... that's true hell, you're only in the apprentice-to-hell stage.... bwahahahahahaha  MS wants your soul!

Don't go baaaaaack!!!!!!!!

---

### Post by seijuro on 2007-02-27
> **thevinn said:**
> Well I think I am giving up on Ubuntu, I just rebooted back into Windows XP.

My Crossover Office trial expired so I couldn't run Quickbooks. I went to Codeweavers and bought the full version but I had trouble getting it to work.

First I tried "Register and unlock" from the Crossver menu but after putting in my email and password it said that it couldn't connect to the Internet.

Then I tried installing the package but it kept saying that it conflicted with the existing installation.

So I wiped the existing installation (including all bottles), opened the package and installed it. Seemed to work but when I tried to install Quickbooks, first it said that Quickbooks already existed. Then when I said go ahead and install a new copy anyway I got an error "missing COMMAND.COM".

Screw this, way too much trouble. Linux is not ready for the desktop yet.

Now I'm back in XP and I can enjoy 1920x1200 again (this resolution didn't work with the nv driver, and the nvidia driver crashed). No more issues with surfing websites in Firefox and suddenly things going very slow or crashing the browser. Photoshop is running nice and fast again.

Maybe in another 6 or 12 months things will be better? I can only hope.

You know you could have installed VM Ware server for nothing and set up a VM XP machine to run your quickbooks and photoshop from INSIDE Linux. But if that is too much work for you and you can't live with out those two programs then windows is probably better for you. I'd say keep checking back in the future though perhaps new software will come up that will serve as a viable alternative or some other solution to the programs you need to run will present itself.

good luck

---

### Post by mysticrider92 on 2007-02-27
> **thevinn said:**
> **The Bad**
The multiple display support needs work.
A lot of my video content is unplayable, especially the videos I recorded onto Memorystick media using a Sony digital camera.
Some font rendering in Firefox is inferior to Internet Explorer.

**The Ugly**
Firefox crashes!
SMB network mount hangs sometimes.
Apparently there are two APIs for developing windowed applications. KDE and Gnome. Programs written for one will not work for the other. Some apps are only available in one flavor of GUI API. This is a mess.

Linux has inherent problems with things like media support, graphics and things like that, mostly because the developers don't have access to good source code and some media requires propriety formats that make licensing very complicated (basically, legally gray). About Firefox, if you think it is a bit unstable now, try it with Beryl. That sometimes causes the window or process to not run properly and you pretty much have to a least restart X. There are actually a good 40-50 or so desktop environments. They are all fairly compatible (for example Fluxbox is built similar to Gnome and makes things look about the same), you just need a few extra packages.

---

### Post by tht00 on 2007-02-27
> **thevinn said:**
> Screw this, way too much trouble. Linux is not ready for the desktop yet.

This is one of the most inaccurate 'myths' floating around, for a multitude of reasons, and it is often said out of a bad personal experience of one new to Linux.

Something to consider -- the easiest type of person to be able to move to Linux would be a basic computer user (not installing, though).  The only things they really need to relearn is where the 'Internet' and 'Email' buttons are.  Next up would likely be advanced users -- while it would take a while to 'relearn' things, an advanced user would (so long as they stick with it) learn to harness and appreciate the power and tweakability of Linux.  The hardest to move would be the intermediates -- the ones who know how to do things in Windows, but not necessarily how or why things work the way they do.  Certainly still do-able, but there will likely be frustrations in the learning process.


> **thevinn said:**
> Now I'm back in XP and I can enjoy 1920x1200 again (this resolution didn't work with the nv driver, and the nvidia driver crashed). No more issues with surfing websites in Firefox and suddenly things going very slow or crashing the browser. Photoshop is running nice and fast again.

I'm sorry things worked so lousy for you.  I, too, had an issue with a nvidia driver when installing Ubuntu, and that kept me from diving straight into Linux.  I went back and forth between Ubuntu and XP for a while, but I did come back and as I learned, was able to deal with it.  That computer still gives me fits when I put Ubuntu on it... I think it's either an issue with that card, the mobo, or the combo.

So yeah, hardware issues can really be the biggest pain in getting Linux setup and can give a very false impression of the average experience.

> **thevinn said:**
> Maybe in another 6 or 12 months things will be better? I can only hope.

Linux is always getting better, but some areas are going slower than others.  Will the areas you find weak be better?  Probably a bit.  Don't expect a major change though.

If you're willing, I'd suggest dual booting (if you don't have that setup already).  It isn't very hard to do, and you can keep learning/tweaking Linux until you are comfortable to take the plunge.  Heck, I still keep Windows around to play games on, but that's all it's there for.

And yeah, a VMware Server setup would be a sure-fire way to get Windows apps to run.  No 3d acceleration, a little awkward, and will be a marginally slower, but will work.

---

### Post by SonicSteve on 2007-02-27
> **PineGroveDave said:**
> I'm posting this one on behalf of one of my employees who has been a MS advocate for a very long time. You see, he's a sharp guy and I've taken every opportunity to plant the "Linux Seed" in his brain. I've been running Linux now for over 4 years (1st Gentoo, now Ubuntu) and have never looked back. Anyway, he recently got his Vista and I stated that he may have problems with a lot of his music and video files playing...let alone running Aero on a PC only 1 year old.

So last night I get the call...
**_Rick: "Well you were right. All my music won't play even though I own all the CD's!!!"_**
Me: "Whoa...So what I warned you about is true, yeah?"
Rick: "Yep. Pisses me off. I'm downloading Ubuntu as we speak and blowing away Vista."
Me: "Welcome to the Dark Side my son."

:lol:

He'll have a learning curve, but I pointed him here and I'll help him when I can. Like I said, he's a sharp guy and I'm sure he'll do fine.

Thank you Microsoft for Vista. The ranks of Linux converts are growing thanks to you. 8)

OK so I've heard alot about DRM and trusted computing etc. etc.
Is this really true though about the music? Was he trying to play the CD's or were they plain self ripped MP3's or what? I would really like to know because if it won't let you play your own self ripped music that's horrible! 
I'm wondering if it was an issue of certain versions of Vista not having support for certain kinds of media. They've been scaling the versions and it's hard to keep track.
Could you please find out what kind of error he encountered. I would like to be able move past the hearsay that surrounds Vista and move toward truth about it. Good, Bad or indifferent.

---

### Post by Dylnuge on 2007-02-27
With new Microsoft DRM, you cannot play ripped CDs unless you re-rip them and MS tags them with a DRM tag, which still prevents you from:
1. Using them on too many computers (I believe 5)
2. Using them on too many Mp3 Players (I believe 3)
3. Using them at all on unauthorized computers.

Similar to iTunes DRM.

---

### Post by tht00 on 2007-02-27
> **SonicSteve said:**
> OK so I've heard alot about DRM and trusted computing etc. etc.
Is this really true though about the music? Was he trying to play the CD's or were they plain self ripped MP3's or what? I would really like to know because if it won't let you play your own self ripped music that's horrible! 
I'm wondering if it was an issue of certain versions of Vista not having support for certain kinds of media. They've been scaling the versions and it's hard to keep track.
Could you please find out what kind of error he encountered. I would like to be able move past the hearsay that surrounds Vista and move toward truth about it. Good, Bad or indifferent.

Sounds like FUD about Microsoft (rather than the typical FUD *from* Microsoft ;) ).

DRM is most commonly a wrapper around a media file that can prevent certain functions.  .wma files are the most common anymore (and most applicable to Windows).  My guess is that if this story is true, this guy ripped his music in protected wma (DRMed).  Should something happen to the 'license' that allows the playing of the file (or however it works anymore), then the music will suddenly be unplayable.

Anyway, the .wma format is horrible, DRMed or not.  Rip your music in a decent non-DRMed format, and you'll be fine -- mp3, aac/m4a, ogg, flac, etc.  Take your pick.  Just stay away from wma.  If you get locked out of your own music, it's really your own fault (though, you could claim ignorance).

---

### Post by PineGroveDave on 2007-02-27
> **SonicSteve said:**
> Was he trying to play the CD's or were they plain self ripped MP3's or what? I would really like to know because if it won't let you play your own self ripped music that's horrible!  My friend literally has hundreds of CD's,all original and legally purchased. When he built his house he wired it so that his PC would be his "Music Server" for his home sound system. As a result, he's ripped all his CD's to to MP3 format so that he can simply throw on a playlist and listen to it throughout the house. He can't play his MP3 files on Windows Vista even though he owns the CD's. Of course he can play the original CD, but that would mean that he'd have to constantly be changing the CD from his player. Unbelievable. Way to go Microsoft! :roll:

---

### Post by PineGroveDave on 2007-02-27
> **SonicSteve said:**
> Could you please find out what kind of error he encountered. I would like to be able move past the hearsay that surrounds Vista and move toward truth about it. Good, Bad or indifferent. Well, according to my friend he states that Windows Media Player simply will not play the MP3 file...No error...no sound...nada. I haven't seen it with my own eyes, but I've no reason to doubt him seeing that he's been a MS fanboy for a long time and is quite sharp.

---

### Post by slayerboy on 2007-02-27
> **thevinn said:**
> Well I think I am giving up on Ubuntu, I just rebooted back into Windows XP.

My Crossover Office trial expired so I couldn't run Quickbooks. I went to Codeweavers and bought the full version but I had trouble getting it to work.

First I tried "Register and unlock" from the Crossver menu but after putting in my email and password it said that it couldn't connect to the Internet.

Then I tried installing the package but it kept saying that it conflicted with the existing installation.

So I wiped the existing installation (including all bottles), opened the package and installed it. Seemed to work but when I tried to install Quickbooks, first it said that Quickbooks already existed. Then when I said go ahead and install a new copy anyway I got an error "missing COMMAND.COM".

Screw this, way too much trouble. Linux is not ready for the desktop yet.

Now I'm back in XP and I can enjoy 1920x1200 again (this resolution didn't work with the nv driver, and the nvidia driver crashed). No more issues with surfing websites in Firefox and suddenly things going very slow or crashing the browser. Photoshop is running nice and fast again.

Maybe in another 6 or 12 months things will be better? I can only hope.

Accounting software is undoubtedly a problem in Linux, or lack of it.  MoneyDance is about the only solution that I can think of, as I stated in my PM to you.

My parents ran into the same issue and I had to reinstall windows for them to use MSMoney.  I tried getting them to change to MoneyDance but they never even wanted to try it.  Some are just stuck in their ways and don't want to accept that sometimes change can be good.

You've done all that work setting up your system just to throw it away and reinstall windows.  It's not wasted time because you've learned a lot about linux.  What other major showstopper is causing you to go back to windows besides the accounting?

---

### Post by SonicSteve on 2007-02-28
> **PineGroveDave said:**
> Well, according to my friend he states that Windows Media Player simply will not play the MP3 file...No error...no sound...nada. I haven't seen it with my own eyes, but I've no reason to doubt him seeing that he's been a MS fanboy for a long time and is quite sharp.

I'm pretty much speechless!! That is entirely horrible. 

I have 2 thoughts
1. will another media player work or does the windows Vista codec base have the DRM limitation
2. will vista only play restricted codec media that it itself created? (as well as DRM purchased music with proper license)

The fact that I'm having to ask these questions is enough incentive to not want Vista

---

### Post by SonicSteve on 2007-02-28
I never thought I would say this because I have used and been quite happy with MS stuff over the years. But...
It's almost tempting to go buy a copy, play with it, then ask for a refund directly from MS.  You can do that, I used to work for them.(hopefully this policy hasn't changed) Please don't throw eggs at me8-[

 I was part of the Windows XP canadian help centre when XP was released. Seems like a lifetime ago. I really want to get to the bottom of this. Perhaps I'll see if I have any old acquaintances still at MS.

---

### Post by SonicSteve on 2007-02-28
I've sent off a few emails to a few of my old friends maybe in a day or two I'll have some answers right from the horses mouth.

---

### Post by SonicSteve on 2007-02-28
I found this Windows Vista Team Blog site myself, so no answers from my old friends yet.
However check it out.

The blog seems to indicate that Vista should function the same as XP in regards to any media you currently have. The article doesn't discuss CD's much, it mostly focuses on DVD's.
[http://windowsvistablog.com/blogs/windowsvista/archive/2007/01/20/windows-vista-content-protection-twenty-questions-and-answers.aspx](http://windowsvistablog.com/blogs/windowsvista/archive/2007/01/20/windows-vista-content-protection-twenty-questions-and-answers.aspx)[LEFT][/LEFT

This article states that any OS that doesn't include DRM will eventually not be able to play it. Essentially they blame the MPAA or most if not all the mess that is happening with DRM.
[http://www.dasmirnov.net/blog/2006/12/31/windows_vista_drm_nonsense](http://www.dasmirnov.net/blog/2006/12/31/windows_vista_drm_nonsense)

This DRM stuff is murky and scummy. Very hard to find the facts, like trying to prove the existence aliens.

---

### Post by Dylnuge on 2007-03-01
[http://badvista.fsf.org/what-s-wrong-with-microsoft-windows-vista](http://badvista.fsf.org/what-s-wrong-with-microsoft-windows-vista)

Thats another one, linked from the FSF themselves.

---

### Post by ragadanga63 on 2007-03-01
> **slayerboy said:**
> Accounting software is undoubtedly a problem in Linux, or lack of it.  MoneyDance is about the only solution that I can think of, as I stated in my PM to you.

My parents ran into the same issue and I had to reinstall windows for them to use MSMoney.  I tried getting them to change to MoneyDance but they never even wanted to try it.  Some are just stuck in their ways and don't want to accept that sometimes change can be good.

You've done all that work setting up your system just to throw it away and reinstall windows.  It's not wasted time because you've learned a lot about linux.  What other major showstopper is causing you to go back to windows besides the accounting?


Almost ALL of the FOSS software comes up short compared to their proprietary counterparts.  For example, the latest Open Office can only come close to MS Office 97, and GIMP? Oh, well forget it if you are in the printing business.   

The short-handedness of FOSS applications in the light of proprietary/Windows apps, is one reason why i'm keeping my XP and perhaps is the reason why Linux has not dominated the pc market yet.  Too bad the FOSS community is putting more time developing Linux distros(most of which go to the dustbins), rather than putting together killer apps.  The latter would have been the way to go  for Linux to gain a more dominant foothold in the pc software market.

Really frustrating when you want to get rid of MS ASAP.

---

### Post by slayerboy on 2007-03-02
I agree that the amount of distros and forks is enough to cause someone to think that there's no need for more developing software in linux.  There IS a need.

BUT, here's the issue.  Most developers who contribute to FOSS software are not getting paid for it.  While closed-source software developers DO get paid.  With this being the case, we will NEVER see FOSS be as good as closed source because people have to eat.  It's much easier to fork a distro than it is to help in the development of an application for a lot of people, which is sad.

I would say maybe GIMP, accounting software, and OpenOffice, need the most work right now.  I wish there was a way that we could setup like a developer's charity or group.  One part of a time is donated from all developers to improve accounting software.  After we get accounting software ready to take on Quicken/Quickbooks, then we need to focus on OpenOffice and getting that to be BETTER than MS Office.  Then we need to focus on GIMP to be better than Photoshop.  Then we can focus on other applications, one at a time.

The whole problem is where is the money going to come from?  We could create a company that focuses on these specific tasks to help open source, but how would a pay scale be devised?  What about people like Linus and kernel devs who don't get paid while others do?

We could do a donation clearinghouse where we can pool donation money and donate to projects, a different one each month.  The problem is money isn't free.  The real way to solve this is to get people to see that donating to these projects makes them better.  How about the $100 a year you spend on security software on your windows pc?  If you install Linux, you should be donating that money.  But the real problem is that you shouldn't have to spend that money on your computer in the first place if it works right.

I'm not sure if there even is a solution to all this.  Until these software and hardware vendors see Linux as a valid OS, things won't change.  It doesn't matter that GIMP is free, because you can install it in Windows, so there's no problem with FOSS vs closed source software, IMHO.  If Adobe and Intuit would have Linux alternatives to their software, you'd have a LOT more people converting to Linux.

---

### Post by ragadanga63 on 2007-03-02
There's one.  Pray for more Shuttleworth's to join the Linux bandwagon.

---

### Post by Dylnuge on 2007-03-03
> **ragadanga63 said:**
> Almost ALL of the FOSS software comes up short compared to their proprietary counterparts.  For example, the latest Open Office can only come close to MS Office 97, and GIMP? Oh, well forget it if you are in the printing business.

I aggree that FOSS software may not be as nice as Proprietary software. However, I think that Commercial, non-GPL software for Linux is a must. Eventually people will see Linux as a more prominent desktop and develop such software for it. No programmer makes a living from Open Source. Perhaps a modified GPL-like license that removes all free beer aspects from Open-Source but keeps other aspects would be nice. 

IE: You own a license of this software for use on an unlimited number of personal systems or one (1) commercial system that you or your company owns. Under the terms of this license, you are entitled to use and modification of the software source code, and can release your changes on the <software> website so long as you do not profit from these changes or release any portion of the software to un-registered users.

Keeps some aspects of Open-Source while making it profitable.  The conversion will take a while. Major companies will need to be first-small companies can't support Linux while it is a less profitable venue.

I have sent e-mails to Adobe, pointing out the prominence of Linux. 3.3% of desktop users have Linux, Mac only recently surpassed that number.

Here are the main steps that will make Linux prominent

1. Advertising. Make people aware that Linux is not harder, just different.
2. Hardware Bundling. Dell, Gateway, etc. must start offering Linux desktops. Most Windows users have never really thought about Linux, since it does not come bundled on their syste,
3. Software Crossing. Office, Macromedia Studio, AutoCAD,  Photoshop, and Quicken/Quickbooks are the most common software missed by Linux users. If major compaines started developing cross-platform solutions, then things would move a lot faster. (Yes, people say Microsoft will never develop for Linux, but remember that there are versions of Office for the Mac).
4. Commercialized Versions of Gratis Distros. Sounds weird, but imagine this-buy Ubuntu boxed edition for $200-get documentation and technical support. Many Distros already do this. Even though community support and documentation is good, many people want something similar to what they get with Windows.
5. Linux Switch Website-Links to vendors, distro choosers, videos about Linux, and online guides. The ultimite resource for ex-Windows and ex-Macintosh users.
6. Advertise the Cutting Edge!!! Beryl and Compiz effects existed for much longer then Vista and MacOS effects. 

Thats the short term. Now, lets say Linux share has risen to about 10%, and Windows share is about 80%. (That makes Mac share also about 10%, a little less to accommodate for other OSs). Now we will see small companies including Linux in their list of platforms to develop for. Perhaps a cross-OS platform similar to Java but developed for C++ will come along.

I can never truly see Linux taking over the market. What I can see is people truly considering Linux as an option-realizing their choices.

---

### Post by ragadanga63 on 2007-03-03
> **Dylnuge said:**
> I aggree that FOSS software may not be as nice as Proprietary software. However, I think that Commercial, non-GPL software for Linux is a must. Eventually people will see Linux as a more prominent desktop and develop such software for it. No programmer makes a living from Open Source. Perhaps a modified GPL-like license that removes all free beer aspects from Open-Source but keeps other aspects would be nice. 

IE: You own a license of this software for use on an unlimited number of personal systems or one (1) commercial system that you or your company owns. Under the terms of this license, you are entitled to use and modification of the software source code, and can release your changes on the <software> website so long as you do not profit from these changes or release any portion of the software to un-registered users.

Keeps some aspects of Open-Source while making it profitable.  The conversion will take a while. Major companies will need to be first-small companies can't support Linux while it is a less profitable venue.

I have sent e-mails to Adobe, pointing out the prominence of Linux. 3.3% of desktop users have Linux, Mac only recently surpassed that number.

Here are the main steps that will make Linux prominent

1. Advertising. Make people aware that Linux is not harder, just different.
2. Hardware Bundling. Dell, Gateway, etc. must start offering Linux desktops. Most Windows users have never really thought about Linux, since it does not come bundled on their syste,
3. Software Crossing. Office, Macromedia Studio, AutoCAD,  Photoshop, and Quicken/Quickbooks are the most common software missed by Linux users. If major compaines started developing cross-platform solutions, then things would move a lot faster. (Yes, people say Microsoft will never develop for Linux, but remember that there are versions of Office for the Mac).
4. Commercialized Versions of Gratis Distros. Sounds weird, but imagine this-buy Ubuntu boxed edition for $200-get documentation and technical support. Many Distros already do this. Even though community support and documentation is good, many people want something similar to what they get with Windows.
5. Linux Switch Website-Links to vendors, distro choosers, videos about Linux, and online guides. The ultimite resource for ex-Windows and ex-Macintosh users.
6. Advertise the Cutting Edge!!! Beryl and Compiz effects existed for much longer then Vista and MacOS effects. 

Thats the short term. Now, lets say Linux share has risen to about 10%, and Windows share is about 80%. (That makes Mac share also about 10%, a little less to accommodate for other OSs). Now we will see small companies including Linux in their list of platforms to develop for. Perhaps a cross-OS platform similar to Java but developed for C++ will come along.

I can never truly see Linux taking over the market. What I can see is people truly considering Linux as an option-realizing their choices.

Nice, incisive post.   Star Office is already taking steps in that direction (70$ and you can install Star Office on five pc's and it's free for educational institutions).  I guess that's the next best thing to free beer.

Pixel32, a potential Photoshop replacement is also slowly developing (38$ from existing Beta release to their release 1) although right now it's so full of bugs that it is unusable.

Let's hope for more developers esp. the major ones to port their apps to LInux.  That will bring about an explosion of LInux users the world over.  (and i can finally remove XP from my PC for good).

---

### Post by SonicSteve on 2007-03-18
> **PineGroveDave said:**
> I'm posting this one on behalf of one of my employees who has been a MS advocate for a very long time. You see, he's a sharp guy and I've taken every opportunity to plant the "Linux Seed" in his brain. I've been running Linux now for over 4 years (1st Gentoo, now Ubuntu) and have never looked back. Anyway, he recently got his Vista and I stated that he may have problems with a lot of his music and video files playing...let alone running Aero on a PC only 1 year old.

So last night I get the call...
Rick: "Well you were right. All my music won't play even though I own all the CD's!!!"
Me: "Whoa...So what I warned you about is true, yeah?"
Rick: "Yep. Pisses me off. I'm downloading Ubuntu as we speak and blowing away Vista."
Me: "Welcome to the Dark Side my son."

:lol:

He'll have a learning curve, but I pointed him here and I'll help him when I can. Like I said, he's a sharp guy and I'm sure he'll do fine.

Thank you Microsoft for Vista. The ranks of Linux converts are growing thanks to you. 8)

OK so here is a possiblity,
Please understand that this is not for sure and my friend speculated and guessed a bit. 
If the CD's were ripped with windows media player the MP3's or WMA's or whatever would likely have been tagged with DRM even if it didn't seem active. Then during the Vista upgrade the licenses for the ripped music would have been lost. Since DRM is active in Vista it would play them anymore.
He said this because that's what happened to him. If this is the case here is the long and short of it. Windows Media player is OK for playing non DRM content. Just don't rip with it. 

I've always used a program called CDEX for ripping MP3 of my CD's. I have a few Gb of music.

---

