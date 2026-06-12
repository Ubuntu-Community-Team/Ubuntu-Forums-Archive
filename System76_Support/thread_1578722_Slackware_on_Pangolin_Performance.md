---
title: "Slackware on Pangolin Performance"
date: 2010-09-20
forum: System76 Support
---

### Post by pilbender on 2010-09-20
Does anyone have any experience with running Slackware on the recent System 76 Pangolin Performance Laptops?

I am thinking of purchasing one because I need a more powerful system than my current system.
[FONT=Courier New]
Current System: 
- Dell Latitude D630 
- Core 2 Duo 2.2 GHz processor 
- 4 GB RAM 

[/FONT]Right now I'm using Slackware 13.1 on the above hardware and everything runs perfectly.  Suspend works perfectly, I never shut down my system.  Wicd and wireless network changes are seamless and automatic.  The system I'd like to go to is listed below.

[FONT=Courier New]System 76 Pangolin Performance:
- Core i7-620M processor
-  8GB of RAM[/FONT]

I don't want to make the purchase if I'm going to run into a bunch of hardware configuration problems.  I'm looking to solve my performance problems not create a whole host of new ones.

I already contacted sales at System 76 and they pointed me to this forum.  I have also found nothing recent on the Internet to indicate whether purchasing this for Slackware is a good idea.

Any experience anyone has to share along these lines would be greatly appreciated.

---

### Post by msrinath80 on 2010-09-21
I don't have any first hand experience on Slackware or the Pangolin for that matter, but I am running Debian (squeeze) on the Lemur right now. Basically, if the hardware works with one distro, it should work with any other. You might need to tweak around a little at first, but that should be all. For instance, I had to rebuild the webcam drivers from source in order to get it to work on Debian (Just a ./configure && make && make install thing). The same thing is done by the System76 driver, except that it is packaged neatly and deployed effortlessly in a single click! If you are good enough to be using Slackware, I'd assume that you certainly are good enough to handle things like this :) It takes a little time (maybe 10 odd minutes) to figure out what the System76 python scripts do, and then you're ready to do the same for your distro of choice!

---

### Post by msrinath80 on 2010-09-21
Also, If you're interested in real "rock-solid" stability, you'd know that Ubuntu is not the surefire way to go. Debian (lenny for old hardware, squeeze for the more recent ones) is more like it.

---

### Post by pilbender on 2010-09-24
msrinath80,

Thanks for the reply.  This is good information.  It was enough to understand what I might need to do.  If those scripts are written in Python, I'm sure I can figure out how to repackage those into something for Slackware.  I am actually a maintainer for some official Slackbuids ;-)

I would have to agree on the Ubuntu comment.  I've tried using several other distributions over the years and I come back to Slackware because Ubuntu (and others for that matter) was a royal pain to customize and it runs like molasses in winter.  Slackware is the only distribution I've ever used that doesn't cause blood to shoot out of my eyeballs.

Any others with experience to share?  Also, more specifically, anyone what uses xrandr to switch dual display on and off one the fly?

---

### Post by pilbender on 2010-10-03
Since no one seems to have any experience with dual display, I'm actually thinking about going to the Serval Professional.  It has this graphics card:
Nvidia GeForce GTX 460M Graphics with 1.5GB GDDR5 Video Memory 

Whereas the Pengolin Performance has this one:
 ATI Mobility Radeon HD 4570

In the past, I've had problems with ATI graphics cards on Linux.  Nvidia has always been good to me.  Unless anyone has some other info, I'm going to take the "safe" route and get the Serval Professional.  I'd rather spend the extra $300 to ensure I don't have headaches in the future, than be sorry when ATI screws me again.

---

### Post by pilbender on 2010-10-03
I went ahead and ordered the Serval Professional.  I'm just not going to take another chance with ATI on a purchase this big.  I need this system to work.  It's vitally important.

I'll probably post back my experience to others once I've received the unit and I've had a chance to take it for a test drive.

---

### Post by pilbender on 2010-10-17
Well... I received my Serval Professional and it has been less than fun.  I checked that all the hardware was operational and then blew away Ubuntu.  Then I put in Slackware 13.1.  It didn't even see the wireless card.  That was the main sticking point.  Otherwise, most things appeared to work okay.

Not having wireless is a no-go.  So I reinstalled Ubuntu and did the system restore.  Ubuntu started pissing me off right away.  I just hate the way they do things.  So I'm downloading Slackware Current.  I'm going to see if a newer kernel, which Ubuntu has already, will see the wireless card.

I'm not that thrilled with running "current" but in the past it has normally been pretty good.  I think, at a minimum, I'm going to run dual boot.  I guess I *need* Ubuntu right now, but I *want* Slackware.  

Man, this is such a pain.  If this makes the wireless card work, I'll be happy.  With Ubuntu I feel like I'm back putting the pieces together like the old days and working around stuff.  Slackware requires some configuration, but it's pretty much ready to go with the things I do and the way I like doing them.

So, my experience with Ubuntu is typical from my past experience.  Things work, but it's such a kludge.  It doesn't help that I'm a total Gnome hater.  I put in Fluxbox but that doesn't really get me where I need to be.  

My list of gripes:
 - Work around the wireless, it sucks in Gnome too, but it works.
 - Search, search, search for stuff, like MySQL
 - Install Sun's Java (no one doing serious development uses OpenJDK)
 - Install all my IDEs (okay, I have to do this in Slackware too)
 - Install Latex (Anyone who doesn't use Latex for documents is really missing out)
 - Install Dolphin (I love that file manager)
 - Install and configure Fluxbox
 - Install Thunderbird (I hate Evolution)
 - Install Pidgin
 - The Gnome power management sucks
 - The Gnome desktop chooser sucks (Actually the whole UI experience is a pain, I'd use KDE, XFCE, or Fluxbox any day over Gnome)
 - I've spent a ton of time trying to figure out how to do trivial tasks
 - Install Konsole although Gnome terminal seems pretty good
 - Install Apache Httpd
 - I hate sudo
 - LVM with encryption, can Ubuntu even do this??  Encrypting home is not enough.  I use other parts of the system.  Those need to be secure too.
 - Suspend doesn't work, but I think that's Nvidia's fault.  The display doesn't come back

I'm not a Gnome guy, but you probably already figured that out.  I'm not an Ubuntu guy either, but that's probably no mystery.  I should talk about some good things.

The Serval Professional is an awesome piece of hardware.  The keyboard is really good.  I like it.  I'm pretty picky because I touch-type.  The display is the best I've ever seen on a laptop, hands down.  It's really crisp and clear.  Very pleasing on the eyes.  The laptop is fast, I mean *really* fast.  Top even shows 8 CPUs because it's a quad-core with that hyperthreading.  It's a real beast and I really like it overall.  I also thought it would feel heavier, weight wise.  It's not too bad.

In all seriousness, if you like Ubuntu and you like Gnome, this laptop rocks!  It is, without a doubt, the nicest machine I've ever bought.

---

### Post by jml on 2010-10-17
As you work through the issues with Slackware on your Serval, You may want to consider dual booting Debian Testing (a.k.a. Squeeze,)  In my experience, Debian runs much faster than Ubuntu.  I have it running quite well on both my first and second generation Darter laptops from S76.  I did have to enable third party repositories for the proprietary drivers.  Good luck in your quest to install Slackware on your Serval.

Joe

---

### Post by pilbender on 2010-10-18
I've now done several installs, Slackware and Ubuntu.  Right now I have both distributions running in a dual boot configuration.  I am using Slackware Current to have the latest kernel.

I consider this a stop gap until I can get everything working in Slackware.  I am using Lilo to boot Ubuntu with Grub installed on the root super block of the Ubuntu install.

I have a terrible partitioning scheme going here:
/dev/sda1 - Slackware /boot
/dev/sda2 - Ubuntu /boot
/dev/sda5 - LVM with Luks AES 256 encryption /dev/cryptvg/root, /dev/cryptvg/home, and /dev/cryptvg/swap
/dev/sda6 - Ubuntu / (root)
/dev/sda7 - Ubuntu swap
/dev/sda8 - Ubuntu /home

I hacked open the drivers from the System76 restore repositories and I was unable to get the wireless card to be recognized by Slackware.  I compiled the modules, installed them and loaded them, but they still did not work on Slackware.  I could not get the actual hardware to be seen.  I located the driver for the wireless card from Realtek.  I will try to  compile that module into the kernel for Slackware this evening.  

The upshot is the Nvidia driver I installed for Slackware is better than the one from the Ubuntu repositories.  I wish they would make the restore files available as regular source as well as that .deb file.  Sometimes the Ubuntu repos leave a little to be desired.  I know they are good in general, but I always end up doing custom stuff.  They never seem to give me exactly what I want.

I haven't looked at the built in camera or the card reader.  They run in Ubuntu, but I haven't tried from Slackware.

If I am able to get the wireless working in Slackware, there will be little to no reason to use Ubuntu.  I need that install though to reference the configuration as I go through getting the hardware working in Slackware.

Other notes.... Suspend does not work.  The display does not come back.  In Slackware it does, but the Ubuntu install does not.  The power management in KDE is better than Gnome.  Gnome will not tell you how much battery is left.  KDE from Slackware will give you battery levels.  Actually, with the exception of the wireless card, things work better with Slackware.

This shouldn't be surprising to those who are steeped in Slackware goodness and have been jerked around by Ubuntu.  As much of a pain as Slackware can be in these sorts of situations, it usually does not need to be messed with once the initial pain is endured.

More to come on this as I find out more stuff.

---

### Post by pilbender on 2010-10-18
> **jml said:**
> As you work through the issues with Slackware on your Serval, You may want to consider dual booting Debian Testing (a.k.a. Squeeze,)  In my experience, Debian runs much faster than Ubuntu.  I have it running quite well on both my first and second generation Darter laptops from S76.  I did have to enable third party repositories for the proprietary drivers.  Good luck in your quest to install Slackware on your Serval.

Joe

Thanks for the suggestion.  I will consider this if I have some insurmountable challenges with Slackware.

---

### Post by isantop on 2010-10-18
> **pilbender said:**
> I hacked open the drivers from the System76 restore repositories and I was unable to get the wireless card to be recognized by Slackware.  I compiled the modules, installed them and loaded them, but they still did not work on Slackware.  I could not get the actual hardware to be seen.  I located the driver for the wireless card from Realtek.  I will try to  compile that module into the kernel for Slackware this evening.  

The upshot is the Nvidia driver I installed for Slackware is better than the one from the Ubuntu repositories.  I wish they would make the restore files available as regular source as well as that .deb file.  Sometimes the Ubuntu repos leave a little to be desired.  I know they are good in general, but I always end up doing custom stuff.  They never seem to give me exactly what I want.

The source from the System76 Driver Application is written in Python, and you should be able to view it in any distribution by extracting it (As an archive) to a directory. In that, there should be a filesystem structure with only /opt. In that, is all of the python source, specifically in /opt/system76/src/.

If you need, I could probably upload an archive with all of the source files included.

---

### Post by 3Miro on 2010-10-18
@pilbender: I know hat you mean about.

This is bad news about the wireless driver. I though system76 came with Intel cards that have FOSS drivers. Good to know in the future, I will have to double-check for my next purchase. As far as Linux drivers go, Ubuntu is the best, due to its size, it provides nicer support for all drivers available or Linux.

Gnome should show you the battery left, if not, something is not setup correctly (or there is a bug).

Someone from System76 should be able to help with the suspend/hibernate under Ubuntu.

Ubuntu alternate install has more options about encryption and installing a minimal system from "scratch" (similar to Arch and Gentoo, but it is not as customizable).

I don't see much difference between Gnome and XFCE, you can easily adjust one UI to look/work like the other, though I understand it, if you don't like Gnome. You can try Xubuntu or Kubuntu for basically replacement of Gnome. Those are almost the same in any way other than the DE (due to the Gnome-centric nature of Ubuntu, there are occasional issues, especially for KDE, but overall those are great options).

There are "unofficial" ppa repositories that you can connect to get newer Nvidia drivers and such for Ubuntu. Also, in terms of easy to install, Ubuntu Software Center is the best in the business (other distros are slacking on that part).

---

### Post by bill516 on 2010-10-19
It would be nice if pillbender would do a piece on what it took to get Slackware running once he has it configured.  I am curious and I think others would be.

I am running Ubuntu 10.4, Debian Squeeze and Mepis 8.5.  Everything works save tht Mepis will suspend but it refuses to come out of hibernation properly.  Debian Squeeze is fine.

For Squeeze it might be necessary to download and install firmware for wireless, depending on the chips involved.  I did it from the Debian repos with no difficulty at all using the ethernet connection on my Pangolin.

Might be a similar situation for Slackware?

Ubuntu 10.4 will stay on this machine as the "go to, always works" distribution while I fool around with other things.  But I have to say that Debian Squeeze is impressively stable and pleasantly quick even in its present "frozen" configuration.

---

### Post by pilbender on 2010-10-19
I can't disagree with some of the sentiment here.  To say the Gnome is not a good desktop environment is to say Linux is not a good OS because I can't get it configured correctly.  It's totally ridiculous.  But I'm a Gnome hater right down to the core because I can't seem to get around the UI very effectively.  It has always been unintuitive and frustrating for me :-)

And I am aware of Kubuntu and the other Ubuntu variants.  I was not aware of the alternate option for installing to LVM with Luks encryption.  Interesting option, but I'm mostly frustrated with the way Ubuntu pidgin holes the user into a certain way of doing things.  That's my biggest gripe.  While it seems to be the best distribution out of the box (I give it strong props for that), it always gets in my way as I try to change things.  I end up wasting vast amounts of time trying to get it to do what want.  Not so with a more power user centric type of distro like Slackware.

About the FOSS driver comment.  I can't say the drivers are not FOSS, except for the Nvidia driver, which I know is not FOSS.  I'm not sure about the wireless.  And I can't criticize System 76 for not using drivers that are in the main kernel development tree.  They are selling a complete system, and a very good one at that.  I'm not a typical user.  I've been using Linux for over 15 years so I'm pretty set in my ways.  To the extent that I can't follow my own way, I can get pretty frustrated.

I did get wireless working on the Serval Professional.  I consider this that last and most important thing.  I was able to identify the hardware with my dual boot configuration in Ubuntu.  Here is the thread that helped me identify the location of the driver from Realtek:
[http://www.linuxquestions.org/questions/linux-hardware-18/wireless-is-not-working-on-toshiba-l500-laptop-790732/](http://www.linuxquestions.org/questions/linux-hardware-18/wireless-is-not-working-on-toshiba-l500-laptop-790732/)

And here is the direct download of the original driver:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The one I chose was the RTL8192SE download.  Then I did a make, make install, and reboot as suggested in the readme.txt from said download.

There are still other things to test under Slackware, like suspend, the built in web cam, and the card reader.  I will post back my experiences with that if I'm successful on getting those items working.  It was said here earlier, but I'll say it again.  The Serval Professional is awesome machine and it does work well if you use it the way System 76 ships it.  It also has hardware that works under Linux.  These are big important things and a few years ago, we had no options like this.  So I'm grateful for System 76 and the work they do and I'm more than happy to endorse and support them.

---

### Post by pilbender on 2010-10-19
> **bill516 said:**
> It would be nice if pillbender would do a piece on what it took to get Slackware running once he has it configured.  I am curious and I think others would be.

I intend to do this.  I looked all over the internet and did a lot of research before I bought the Serval Professional.  I think I made a good decision despite my disappointments with getting certain hardware working.  This is how it used to be in Linux and I was hoping to avoid some of it altogether.  Not because I mind, but because of time.  In fact, I haven't really been able to use the system because I have to get other work done.  I currently have 2 development jobs so my days are pretty full.

I was notified, yesterday, that one of my jobs will end at the end of November, so I will lose my corporate issued laptop, that's running Slackware of course ;-)  So I'm pretty motivated to get my Serval working the way I need it because it is my livelihood.

One of the great things about the Linux landscape now is that hardware companies are making drivers for Linux.  So we have a lot of options that we didn't have even a couple of years ago.  In general, it looks like I'm going to be able to get things working off the original drivers for the hardware.  Right now I've only done this with 2 things: Nvidia and Realtek for the graphics card and wireless respectively.

I think there are a lot of people looking for that good hardware at a decent price with full Linux support.  I know I've been waiting over a decade for it.

---

### Post by 3Miro on 2010-10-19
Driver support has improved tremendously under Linux, however, there is more to be desired. Also, I am holding the proprietary wireless driver as a point against System 76 (it is still a great company, I am just pointing out one thing that they can improve).

When it comes to video, only Intel video cards have free (as in freedom) drivers and those are messed up sometimes. Intel video falls short of ATI and NVIDIA in all but power consumption, so if one wants great quality video, then one is stuck with prop-driver. (AMD has new FOSS driver for their 5xxx series, but it hasn't made its way to Ubuntu and Sys76 works with Ubuntu only)

On the other hand, there is plenty of good wireless chips that have free drivers.

Reasons why I think System76 should try to ship hardware with free drivers:
1. Prop drivers often break during updates. Drivers that are free get tested along with all the modules in a kernel update, which means that they are far less likely to break, which means less maintenance for Sys76, which means happier customers.
2. For wireless in particular, after reinstall/clean upgrade, one is forced to find a wired connection to get the prop drivers and this can be hard for some people.
3. Those of us that don't use Ubuntu may have hard time setting things up. I think Sys76's choice to support Ubuntu and Ubuntu only is 100% percent correct in the sense that they cannot provide support/packages for every single distro out there, however, with "free" hardware, they can implicitly do that.
4. We already payed money for the hardware, it is ridiculous for manufacturers to put restrictions on the drivers. We should all use our money against them, buy only fully supported hardware and thus force all manufacturers to give FOSS drivers. If Sys76 provides only "free" hardware, then they will support the community in that effort.

I have a Sys76 laptop and it only need the NVIDIA driver. I also have a non-Sys76 laptop and I so wish I had the money and the time to do better research on the wireless. I mean it works, but it is always couple of extra hours of reading/downloading/compiling/setting up.

Argh ... enough ranting. I am glad pilbender got everything working and I am glad that I have to also research Sys76 before my next purchase (cross fingers for Santa).

---

### Post by pilbender on 2010-10-21
I typed up a nice, well thought out update to post here.  Then I picked up my laptop and hit some mouse buttons by accident and lost it.

I'll just try and list out what I remember.  Things not working: 
[LIST]
[*]Skype microphone, although the microphone itself works.  Might just need to roll back to an earlier version of Skype.
[*]Suspend
[*]Mouse Scrolling (using the right edge of the touch pad)
[/LIST]
Things that are working that I haven't mentioned:

[LIST]
[*]The SD card reader, pops right up in Dolphin.  Works like a dream.  This hasn't always been the case for me with other laptops.
[*]DVD RW
[*]USB
[*]Dual Display, Oh yeah baby!
[*]Sound, which is really good through my Bose headphones :-) External speakers, built-in microphone.
[*]Web Cam, yep and nothing special had to be done either.  It just worked.
[/LIST]
Things I don't know and really don't care about:

[LIST]
[*]Finger print reader.  I encrypt my hard disk with Luks AES 256 encryption.  I don't need to dink around with a reader that might give me trouble.  Plus, my RAM and all my data and configurations are secured no matter where the disk ends up.
[*]I don't own a firewire device
[*]I don't have an E-SATA device
[*]I doubt I'll ever use a modem again based on several years of not even hearing about them let alone needing one.  Side note, do you all remember BBS's?  I did my time on 1200 baud, believe me.
[*]Bluetooth, I have a phone I could try and couple with it, but I really don't use Bluetooth.  Might buy a Bluetooth mouse now.  It'd be cool not to have that sticking out the side anymore.
[*]HDMI, I don't even know what it is let alone if I need to have it working.  I might be a developer by trade, but I really don't try to keep up with the latest consumer electronics.  I'm sure it's some handy dandy interface that kicks ***, but think Allegory of the Cave and you'll understand what I mean.
[/LIST]
A couple of other things worth mentioning.... I am still on Slackware current as I was trying give myself the best odds of getting the wireless card working.  So I'm running Linux kernel version 2.6.35.7.  It didn't work so I don't see a need to use current, but it's too much trouble to roll back.  Things are stable and I don't want to go back right now.

I also used Alien Bob's multilib setup from 13.1.  Again, no problems here... Well maybe that's the problem with Skype because it's 32 bit, who knows?  I'll have to look into that some more.

This thing burns through battery like nobody's business.  Seriously, it lasts about an hour even when I'm not hammering it.  That's okay with me because I bought this laptop to be mobile and have speed, not necessarily to have long battery life.  But for those that think it's important, keep that in mind.

I might test Ubuntu to see if it's any better or there's something more I can do to extend the battery.  2 hours would be nice.

I did some nasty partiition hackery to get Ubuntu working.  I load it with Lilo (the one true boot loader :-) and put Grub in the root super block for Ubuntu.  I had to mount the boot partition for Ubuntu to get Lilo to see it from Slackware.  At least now I can reference Ubuntu or apply firmware updates if I need to in the future.  Firmware updates always seem to be supplied for Ubuntu and not generically to be used with other distros.

If anyone needs specific help with any of this, I'll be more than happy to assist.  I'm not promising a fast response, but I will respond eventually.  I'm just warning people ahead of time; I'm pretty busy.

Suspend.  I really want that working at some point.  When I do figure it out, I'll post that solution as well.  I really consider Suspend that last big thing.  Once that's working, I'll be totally happy.

---

### Post by isantop on 2010-10-21
Actually, I think Mouse Scrolling might actually work. It's not a synaptics touchpad, and thus, the scrolling is different. In Ubuntu, to scroll up, you touch the upper right corner of the pad, and to scroll down, you touch the lower right corner. You might try this out, as it probably works fine for you.

---

### Post by pilbender on 2010-10-22
Got Skype working.  I figured it was a matter of finding the right volume and audio settings.  It was a little weird in kmix, but I have it now.  Just needed to play around with it some more.

The scrolling sort of works.  I tried touching the corner and it doesn't work.  I can get to move by dragging up and down on the right edge but it's not right. I'll play with some more settings for this.

Suspend is still not working.  I haven't spent much more time on it.  Maybe I will this weekend.

scott

---

### Post by pilbender on 2010-10-27
I've spent some time with suspend and it is not looking good.  I don't boot Linux too often on any machine and I'm not used to waiting for the kernel to load.  It takes a really long time, on both Slackware and Ubuntu.  I think the original install had some sort of caching thing going to make if faster.  I can't remember for sure.  I only booted it a couple of times.

This means I can't go to the coffee shop and just open the lid and go.  I have to go through the boot up process.  With the short battery life, it really takes away from my convenience.  I do a lot of work from the coffee shop.  We have meetings at least a couple of times a week at coffee shops.  So, not having a working suspend on this system is really quite inconvenient for me and my work flow.

I've been communicating with System76 support and despite my running a non-standard, unsupported configuration, they have been helpful.  I've been tinkering with various boot parameters.  Here are the 2 that were suggested:

acpi_os_name=Linux
acpi_psi="Linux"

I had some luck with the second one.  But I was unable to get the display back.  Ended up doing a hard reset.  Nvidia might be getting in the way here.  I may try switching to the nv driver or that nouveau driver.  Then I'll have to check dual display again to see if that works in this configuration.  I need to be able to switch the second display on for overhead presentations.  Plus I like using 2 displays when I'm coding.

So that's the update.  If I'm able to get through the suspend problem, I'll post the solution.

---

### Post by pilbender on 2010-10-28
This is a typo, according to the suggestion from System76:
acpi_psi="Linux"

It should be:
acpi_osi="Linux"

It makes sense as this is actually a valid option from my kernel sources.  But it did not help.  Suspend still does not work.  I have a few other things i can try, but it appears to be a lost cause.  Extremely disappointing.

scott

---

### Post by val67 on 2010-10-28
> **pilbender said:**
> This is a typo, according to the suggestion from System76:
acpi_psi="Linux"

It should be:
acpi_osi="Linux"

It makes sense as this is actually a valid option from my kernel sources.  But it did not help.  Suspend still does not work.  I have a few other things i can try, but it appears to be a lost cause.  Extremely disappointing.

scott

Is there any confirmation from s76 that suspend works at least for ubuntu, which they officially support?

Val.

---

### Post by isantop on 2010-10-28
Suspend in Ubuntu on all of our laptop models is working *nearly* flawlessly. Plus, with the improvements they've made to the process in Ubuntu, it takes all of a second from power on to unlock screen. 

pillbender: Ubuntu boots in around 10-15 seconds on my machine, including BIOS time, grub, and logging in. After this, the system is ready to use. The Ubuntu devs have done a lot recently to get the boot process as streamlined as possible, resulting in super fast boots.

---

### Post by pilbender on 2010-11-01
> **isantop said:**
> Suspend in Ubuntu on all of our laptop models is working *nearly* flawlessly. Plus, with the improvements they've made to the process in Ubuntu, it takes all of a second from power on to unlock screen. 

pillbender: Ubuntu boots in around 10-15 seconds on my machine, including BIOS time, grub, and logging in. After this, the system is ready to use. The Ubuntu devs have done a lot recently to get the boot process as streamlined as possible, resulting in super fast boots.

You may be right, but that's not he case when you chain load and put Grub in the root superblock.  It takes forever to load as the kernel does its BIOS probing.  

Glad suspend is working for you, but that's not the case on my Ubuntu install or my Slackware install.

Furthermore, the wireless card is glitchy.  It fails once in a while and the only fix to get it back is to reboot.  It usually works for several hours (even days) before this happens.

With the exception of these 2 items, I love the laptop.  Unfortunately these are extremely irritating shortcomings.  I would highly recommend that other buyers not touch the default install on the Serval Professional.  If you plan on doing what I'm doing, be prepared for disappointment and frustration.

---

### Post by pilbender on 2010-11-01
I just had the wireless card go down again in only a few minutes and I was able to remove the module and reload it using:

rmmod r8192se_pci
modprobe r8192se_pci

That brought it back up without a reboot.  Just in case anyone else is running into this. 

I will also post the solution, if I ever find one, to the suspend problem.  I really don't care of the boot up time is slow if I never have to boot the laptop.

---

### Post by 3Miro on 2010-11-01
Did you get the default wireless on the serval or the "Intel Centrino Ultimate-N 6300 - 802.11A/B/G/N Wireless LAN Module" upgrade. Supposedly the Intel one should work out of the box with 2.6.35 kernel without glitches.

---

### Post by pilbender on 2010-11-01
I ordered the default wireless.  I still have a G series router :-)  I have a B series one somewhere that still works too.  

I just find I don't need any more speed than that.  I'm either searching the Internet for something, committing source code, or making transfers of only a few hundred MB's now and then to servers.

I have kernel 2.6.35.7 on my Slackware instance.  Perhaps a module was missing from that, but stock Slackware is normally pretty good about including all possibilities.  It was not recognized in my case without the download I mentioned in an earlier post.

There are a few other downloads on that Realtek page that might work more reliably.  I'll try them if things get too messy with this one.

Sometimes brand new hardware is like this on Linux and I'm hopeful that eventually this laptop will be supported flawlessly in the future.  

It has been fantastic for the programming I'm doing because the turn around times are amazing.  This thing really chews up anything I throw at it from a raw crunching standpoint.  I really like the performance and it makes my work so much more enjoyable.  I can focus on knocking tasks down rather than waiting for memory to swap and processors to churns while I execute deployments.

I'm not regretful of my purchase.  Just disappointed on the suspend front mostly and the wireless front to some degree.  It's still worth it in my case.  The difficulties may not be a proper trade off for other people who prefer to run Linux distributions besides Ubuntu.

---

### Post by pilbender on 2010-11-03
I just did another update of Slackare Current, reinstalled multilib, and installed a new wireless driver again.

Realtek just updated their driver on 10-25-2010:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Remember, I am using: RTL8192SE on the download page.

We'll see if this one has any more trouble.  Hopefully this will work without dropping once in a while.

---

### Post by pilbender on 2010-11-04
So far the wireless has been flawless since that new driver update.  I'm not completely convinced it's perfect, but it is definitely better.  If it lasts for a few days, I'll know it's totally perfect.

I'm so elated. So one more thing left.  Suspend.  If I can get that working things would be perfect.  I'll post back in a few days with a wireless update, good or bad.

scott

---

### Post by pilbender on 2010-11-05
I'm still having periodic problems with the wireless.  I'd say it's better overall, but it's still glitchy and I have to

rmmod r8192se_pci
modprobe r8192se_pci

to reset it.  This seems to happen sporadically, just as before.  Sometimes it happens after a few minutes, sometimes it happens after sitting all night.  

I'll keep watching for another update and I'll rebuild it if there is one.

---

### Post by pilbender on 2010-11-07
The wireless has been about the same the last few days.  Once in a while, like every few hours or couple of days, I have to remove and reload the module.

I also have a bluetooth mouse now.  It works very well.  On Slackware your user has to be in the plugdev group and the /etc/rc.d/rc.bluetooth has to be made executable.  Also I am using the Bluetooth Device Manager applet.  It's pretty nice as well.  No problems at all with this hardware on the Serval Professional.

---

