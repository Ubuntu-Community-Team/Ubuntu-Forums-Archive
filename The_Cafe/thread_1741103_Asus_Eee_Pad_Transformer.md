---
title: "Asus Eee Pad Transformer"
date: 2011-04-27
forum: The Cafe
---

### Post by dsfitzpat on 2011-04-27
I'm intrigued by the Asus Eee Pad Transformer, which is now hitting the North American market - it's an Android tablet that docks into a netbook-sized keyboard.  I've had great results with Ubuntu on Eee PCs in the past and I think this thing could be a good platform for Unity, if it's possible to get it running properly.
Has anyone had a go at this yet?  (I know there's a similar product from Always Innovating that supports Ubuntu, but Asus seems to have them beat on price and specs.)

---

### Post by Paqman on 2011-04-27
If it's running Android it's probably got an ARM chip inside it, so might be far from straightforward to get Ubuntu running on it.

The fact the tablets run on ARM chips is the reason they all run on slightly lame phone OSes, instead of something a bit gruntier.

---

### Post by ve4cib on 2011-04-27
You can get ARM versions of many distros, including Ubuntu and Debian.  Blaming the CPU for "lame phone OSs" seems like a cop-out to me.

---

### Post by Paqman on 2011-04-27
> **ve4cib said:**
> You can get ARM versions of many distros, including Ubuntu and Debian.  Blaming the CPU for "lame phone OSs" seems like a cop-out to me.

Indeed, and yet that's the way they've gone.

---

### Post by ve4cib on 2011-04-27
Yes, but I doubt it's the CPU that's driving the decision to use Android.  I have a feeling it's more a case of "We want to make an Android tablet.  What hardware can we get for cheap?  ARM chips?  Sounds good.  Use those."

---

### Post by NormanFLinux on 2011-04-27
Its priced the same with the accessory keyboard as Acer's Iconia which includes it in the price.

They are notvertibles - that is notbooks with a detachable display.

They're designed for the crowd that can't decide between a true notbook or a tablet PC.

---

### Post by Johnsie on 2011-04-27
I'm a big fan of eeepc's in fact I'm using one right now. Very portable and it has taken a good beating over the last year. I normally replace my netbooks after 6 months because it's critical for my job that i have a stable netbook. 

The eeepad looks good, but it seems very expensive. It'll be interesting to see how much of a beating it can take. I had an Archos 70 pad and it got a badly cracked screen after less than a month. I'm not getting another pad until I can find one that can take a beating like my netbook. I love some of the android apps but my netbook is way more powerful and customisable.

---

### Post by dsfitzpat on 2011-04-27
The Eee Pad is priced at $399 USD, which is less than an iPad or a Xoom, but I see now that the keyboard is extra (and not for sale until next month).  Under the hood it's got an Nvidia Tegra 2 and 1GB RAM.
I don't see myself going for a tablet anytime soon - I like having a keyboard - but Unity seems to be begging for a touchscreen!
I like my EeePC 1005HA - it's cheap, it travels easily, and with the extra EeePC support in the kernel shipping with 11.04, Ubuntu works out of the box (except for a couple of function keys).  The downside is that it sucks at playing flash video - any embedded clips I come across tend to be pretty choppy.

---

### Post by Copper Bezel on 2011-04-27
I'm more impressed with the Slider, which is basically a Xoom with a pop-out stand with a keyboard. Damned thin even still. 

Android has more name recognition, more active development for enduser apps, etc. than Ubuntu, and it's a little simpler to use. It's also an easy switch for someone who already uses an Android phone. Of *course* Ubuntu has more free software, more desktop-scale applications, and actual customization options. It's no surprise if tablets continue to ship primarily with Android (and no surprise if we all have to get used to the first step on getting a new computer being "replace Android with Ubuntu" instead of "replace Windows with Ubuntu.") = D

I love my Eee, incidentally. I've never been happier with a computer, and I haven't had a computer happier with Ubuntu, either.

Edit: An S101, the girly model with the chrome and the rhinestones, in Graphite.

---

### Post by NormanFLinux on 2011-04-27
Android 3.0 Honeycomb is customized for a tablet. Windows 7 and Ubuntu aren't quite there yet.

---

### Post by rdnetto on 2011-04-28
I plan to get one (not available in my region yet, plus I hear there'll be a 3G version next quarter) and install Ubuntu on it, albeit with KDE/Gnome instead of Unity.
There's not technical reason it can't run Ubuntu, it's just a matter of getting the boot loader working. [The instructions]("https://wiki.ubuntu.com/ARM") seem simple enough, although dual booting with Android might be a little more challenging.
If anyone does get one and install Ubuntu on it, please let us know how it goes.

---

### Post by paoletto on 2011-04-29
I think that the biggest drawbacks of this solution, otherwise great, are:

1) lack of at least one USB port on the tablet
2) lack of the possibility of having a 2.5" hard drive on the dock
3) only 10.1


if they will make a 12" (like eee's 12xx) with some more resolution, usb on the tablet and the possibility of having an hard drive on the dock, then it would really be a must hard to beat


In any case, ubuntu would be a must on such device. even though not made for tablets, i think it would be perfectly usable (even without unity, but with a simple gnome and some kind of popping up on screen keyboard) on the touch.
And after all, if you have the dock, you would use it as a tablet just to read, wouldnt you?

---

### Post by dsfitzpat on 2011-04-29
Yeah, I was thinking of things like typesetting in LaTeX - with keyboard attached you can write up the source, and once the PDF is generated, you could pop off the tablet and lean back for comfortable proofreading :)

---

### Post by gunfyter on 2011-04-30
I wouldn't mind using the Android system with the keyboard detached, and then booting Ubuntu from an SD card or USB.     I am carrying an EEE 900A and an IPad now... syncing files though DropBox.

---

### Post by clegends on 2011-05-08
I've been trying to hack Ubuntu onto the Adam tablet, and it's really difficult. I mean exceedingly so. Firstly, Ubuntu supports native arm installations... with an omap4 board. This is from texas instruments, more open, and a different kettle of fish. Nvidia, incidentally, has stoped developing actively for Linux, though they have mentioned (in their unsupported software forums) that another release is coming. The last one, linux4tegra was based on ubuntu 9.04, and wasn't a particularly full installation. 

Mot of the android tablets coming out (including both the Adam and the Transformer) have tegra 250 chipsets. This is great.... providing you can get graphics acceleration working. The folks with the vega tab have so far gotten the furthest, with more or less a working unity interface (2d) with graphics acceleration. There is no sound, which seems to be a big problem with arm. 

Yes, Ubuntu 11.04 runs on arm. But it's very, very different to installing on an intel platform. I'm not writing this to discourage people, but to share a lot of work trying to get this to run. For more info, search "Ubuntu on Adam, XDA", and "Ubuntu 11.04 on Vega". You'll get an idea of what I mean.

Lastly, I'd encourage people who do have some of these tablets to stop talking about how great it would be to get Ubuntu running on them, and actually do something. These forums are full of people waiting for others to do the work. Everyone can help, lets get Ubuntu running on tegra. Cheers.

---

### Post by NormanFLinux on 2011-05-08
A notvertible... what's not to love? ;-)

---

### Post by NormanFLinux on 2011-05-08
You could run Ubuntu off an external USB drive... or Windows. What you attach to it would be up to you!

---

### Post by PDiddlyDoodlyDo on 2011-05-19
I've managed to get my hands on one, so I'll try booting 11.04 with the Unity interface from a USB as a start.

Only thing that concerns me is what I should do if I screw up the Android Honeycomb installation - how do I reinstall the OS that it ships with?.. I'd like to have this backup before I mess around too much, just in case I can't get Ubuntu to work on it.

Stilll a bit of n00b, but everyone's got to start somewhere right?

---

### Post by rdnetto on 2011-05-20
> **PDiddlyDoodlyDo said:**
> I've managed to get my hands on one, so I'll try booting 11.04 with the Unity interface from a USB as a start.

Only thing that concerns me is what I should do if I screw up the Android Honeycomb installation - how do I reinstall the OS that it ships with?.. I'd like to have this backup before I mess around too much, just in case I can't get Ubuntu to work on it.

Stilll a bit of n00b, but everyone's got to start somewhere right?

Once you boot Ubuntu off the USB, you can create an image of the hard drive with: dd if=/dev/sda of=/media/My_USB/HD0.img bs=1M
(Replace sda with whatever the hard drive is called).
To restore the image, swap if and of.

---

### Post by Copper Bezel on 2011-05-21
> Lastly, I'd encourage people who do have some of these tablets to stop talking about how great it would be to get Ubuntu running on them, and actually do something. 
Can't really afford to, but it's working so far for me - I'm waiting and PDiddlyDoodlyDo is working. = P

I'm awaiting your results eagerly and with much gratitude for your efforts, PDDD. = )

---

### Post by WACOMalt on 2011-06-03
So has anyone got this to work? I am kinda skeptical it will be as straight forward as just booting from the USB.

I will try once I get my dock, but no idea when that will be. (sold out everywhere)

---

### Post by BrokenKingpin on 2011-06-04
My boss picked up one... very cool device. Although I wouldn't want it to just run Android, I would prefer a normal Linux distro on it.

---

### Post by Copper Bezel on 2011-06-04
With the dual-core processor and a gig of RAM, it certainly has the power to run a perfectly ordinary Ubuntu install, and it's the same chip as that Toshiba "smartbook" that can run Ubuntu ARM, but God knows the touch experience would be disappointing in comparison to that under Android. I wonder if something like MeeGo would effectively split the difference?

---

### Post by RastaCalavera on 2011-06-16
I just got my keyboard for my transformer and am loving it. There isn't really a scroll option when reading the page so you still have to touch the screen. The keyboard also has specific keys and certin things dont work on it like ctrl arrow to skip between words. there is also a lot of lag when typing. I would like to use Ubuntu on this tablet but haven't looked into the arm issue yet. I loved ubuntu on my 1005ha eeepc and would like to see an android and ubuntu icon in the berg boot loade. If anyone has progress or if there is something i can do to help speed up the process on this project let me know. I am not a developer or very experienced but will always be willing to ry something

---

### Post by xiztrn on 2011-06-17
I'm in the UK and should be getting myself one of these next week.

Found this page whilst searching to see if it was possible to install a linux distro on the eee pad, something I would really like to be able to do!

Not a massive linux boff and wouldnt have a clue where to start with try to get it to work :P

I did however find the following links which I believe would be of interest :)

**Linux + android on the Asus eee pad transformer TF101 Coming SOON**
[http://androidflip.com/linux-android-asus-eee-pad-transformer-tf101-coming/](http://androidflip.com/linux-android-asus-eee-pad-transformer-tf101-coming/)

And the the more interesting link:
**Workaround to run Ubuntu now**
[http://tegradeveloper.nvidia.com/tegra/forum/workaround-run-ubuntu-now](http://tegradeveloper.nvidia.com/tegra/forum/workaround-run-ubuntu-now)

Hopefully some of you clever folk can take this info and get it working? Im keen to be able to get ubuntu up and running on the Pad.

---

### Post by Giantyak on 2011-06-19
I add my vote to the dualboot option: android plus ubuntu. Ill go single boot ubuntu the moment its touch screen support is equal to android. Ill be watching this space :-)

---

### Post by Lucradia on 2011-06-19
I've had bad results with ubuntu on EeePCs actually, so I'd stay away to be honest.

The bad part I'm having trouble with is that my ralink wireless adapter will refuse to get an IP Address from my library CISCO Routers.

---

### Post by RastaCalavera on 2011-06-19
> **Lucradia said:**
> I've had bad results with ubuntu on EeePCs actually, so I'd stay away to be honest.

Thats a shame :( I ran 9.4 and 10.4 plus mint and puppy on my EeePc 1005HA and had wonderful results. slight update with my Tf101, keyboard is still laggy, scrolling down a webapage is a pain in the @$$!!!! External Usb drive is not reonginzed, it is a WD and powered by the usb port. I also inserted a 8gb sd into the keyboard and it did not come up. So far I am impressed with the tablet but a little let down on the keyboard option. the lag is the worst part. I cant imigine myself trying to write a term paper with this computer which is a huge dissapointment. It also makes me wonder if there are this man problems in the native android, Ubunut or Mint might be un-usable :(

---

### Post by rdnetto on 2011-06-20
> **Giantyak said:**
> I add my vote to the dualboot option: android plus ubuntu. Ill go single boot ubuntu the moment its touch screen support is equal to android. Ill be watching this space :-)

While I haven't used it, Gnome 3 looks pretty well suited to touch. You could probably still use uTouch as well.

I'm plan to go dual boot because apparently Android is needed to do firmware updates to the keyboard - apparently there's a lower level of software than just the OS. Probably something to do with battery charging.

---

### Post by RastaCalavera on 2011-06-21
[http://www.techhackz.com/2011/06/root-your-asus-eee-pad-transformer.html](http://www.techhackz.com/2011/06/root-your-asus-eee-pad-transformer.html)
[http://androidflip.com/primordial-v31-custom-rom-asus-eee-pad-transformer-tf101/](http://androidflip.com/primordial-v31-custom-rom-asus-eee-pad-transformer-tf101/)

Some sites i thought people might be interested in:)

---

### Post by Copper Bezel on 2011-06-21
Like RastaCalavera, I've had a nothing but excellent experience with my Eee (S101) on Ubuntu. I had some hardware support problems early on, but every feature is fully supported with 10.10.

Too bad about the problems with Ubuntu on the Transformer. I suppose it's not quite powerful enough for a full OS, even apart from the (bizarre) USB issue. (I mean, seriously, the U stands for what again?) Still a neat gadget, though.

---

### Post by asdfuogh on 2011-06-21
Hmm, it'd be so very nice to be able to dual-boot ubuntu (without rooting it or going through something complicated). I haven't got the keyboard yet so I don't know about keyboard lag, but is that something to do with the software and not the hardware? Would booting ubuntu fix that?

Also, I think I saw some rumors going around that the Transformer-V.2 will be able to dual-boot ubuntu and android!

---

### Post by RastaCalavera on 2011-06-22
> **asdfuogh said:**
> Also, I think I saw some rumors going around that the Transformer-V.2 will be able to dual-boot ubuntu and android!

What's this? I did a Google search and nothing came up. Yah the lag would be software that may or may not be an issue in ubuntu depending on drivers and such. On a side note, the tablet has a great swipe to type feature that I believe ships with honeycomb. I did this post with the swipe feature and if worked well.

---

### Post by asdfuogh on 2011-06-22
Yeah, icant remember whih forum i saw it in..

I dont have the dock, but ive gotten kinda used to typing on the virtual keyboard for now.

---

### Post by rdnetto on 2011-06-23
> **asdfuogh said:**
> Hmm, it'd be so very nice to be able to dual-boot ubuntu (without rooting it or going through something complicated). I haven't got the keyboard yet so I don't know about keyboard lag, but is that something to do with the software and not the hardware? Would booting ubuntu fix that?

Also, I think I saw some rumors going around that the Transformer-V.2 will be able to dual-boot ubuntu and android!

The Transformer 2 will be able to run Windows 8 and Android. It'll be able to dual boot Ubuntu only because by the time it comes out, we'll have figured out how to get the v1 to do so.

Also, it's a USB keyboard - it's far too simple for the lag to be hardware induced - definitely a software issue.

---

### Post by asdfuogh on 2011-06-23
Oh yeah, youre right. It wasnt ubuntu, it was the new windows :-x my bad

---

### Post by rdnetto on 2011-06-23
It also looks like it'll be released in October this year, which is much earlier than I expected. Since Ubuntu doesn't work perfectly yet and the Tegra 3 will be 4x 1.5 GHz, I think it'll be better to just wait for it...
(at least, that's what I'm going to do)

---

### Post by RastaCalavera on 2011-06-26
Where are you guys fidimg info on the transformer 2? Anyone have a link they can post?

---

### Post by rdnetto on 2011-06-27
> **RastaCalavera said:**
> Where are you guys fidimg info on the transformer 2? Anyone have a link they can post?

[http://www.asuseeepad.net/blog/](http://www.asuseeepad.net/blog/)

---

### Post by RastaCalavera on 2011-06-30
Thanks for the link! Little sad to think that they are already making a machine that could be better. I do really like mine so far, the slider looks interesting as well

---

### Post by IcyEyeG on 2011-07-07
I've just found some useful information about this:

- [Linux for Tegra release 12 alpha 1 released]("http://tegradeveloper.nvidia.com/tegra/forum/linux-tegra-release-12-alpha-1-released")

- [ASUS *Eee Pad Transformer* Running *Ubuntu* 11.04]("http://www.techdrivein.com/2011/07/asus-eee-pad-transformer-running-ubuntu.html")

---

### Post by rdnetto on 2011-07-08
Here's the actual dev thread: [http://forum.xda-developers.com/showthread.php?t=1147062](http://forum.xda-developers.com/showthread.php?t=1147062)

They're making amazingly fast progress (by my estimate they'll probably be done in a month), but it's still a work in progress, so try not to bug them for help unless you think you can contribute.

Personally, I'll probably wait until there's a bootloader so we can dual boot.

---

### Post by pitbullthe1st on 2011-07-21
That is because the general public are on the most part a simple lot and android offers a small device and works faster than most peoples PC's, and what with windows bloating out there OS with every update its not surprising.  90% of people use a computer for web surfing, wordprosesing, spreadsheets, powerpoint and emails and not a lot else for them android 3 (more specifically eee pad transformer) is perfect and I have to admit that although I'm a power user in Ubuntu I can do 90% of my stuff on my transformer including ssh'ing in to my server. The reason I like a tab is that it's fast, stable and has a very long battery life (the first day I had it, I was playing with it a lot and I got 13 hours (suppose to be 9.5Hours) from just the tab no dock).  And correct me if I'm wrong but this is what people want from a mobile device.

---

### Post by IcyEyeG on 2011-08-08
> **rdnetto said:**
> Here's the actual dev thread: [http://forum.xda-developers.com/showthread.php?t=1147062](http://forum.xda-developers.com/showthread.php?t=1147062)


[ ]("http://forum.xda-developers.com/member.php?u=3354403")Jhinta's development stopped. However, development continues here:

[http://forum.xda-developers.com/showthread.php?t=1191141](http://forum.xda-developers.com/showthread.php?t=1191141)

---

### Post by Giantyak on 2011-08-15
Yeah lilstevie has built on Jhinta's work.

A few people have got dual boot going for Android and Ubuntu. I'd love to be able to get this setup going but i'm a linux newb and i don't quite have enough time to learn how to do it. I'm very tempted to make some time, but i know i'd probably break it :)

---

### Post by dyltman on 2011-08-16
Hopefully I'll have one for my birthday. I wonder why there hasn't been much fuzz around it because it looks and sounds fantastic.

Also it certainly will be interesting to try and install ubuntu on it.

---

### Post by allanh46 on 2011-08-27
Hello every one  

I am looking for the ubuntu.img I need to dual boot my transformer..  I m not able to figure out which one I need.  the link given ubuntu.img just was not there
I have the rest of the needed files.:(

---

### Post by Copper Bezel on 2011-08-27
So far as I can tell, only 9.04 UNR was released as a .img. There's ostensibly some way to turn a .iso into a .img, but I know as little about that as I do about installing on Android devices.

---

### Post by forrestcupp on 2011-08-27
I've been looking at the Transformer just to use as an Android tablet only. I don't care about the keyboard, and I don't care about installing Ubuntu on it.

There's one thing I'm wondering about that isn't clear. Is there a USB port on the tablet part, or is the USB only on the keyboard part. I would probably buy the tablet without the keyboard, and I can't tell if that side has USB or not.

---

### Post by markp1989 on 2011-08-27
> **forrestcupp said:**
> I've been looking at the Transformer just to use as an Android tablet only. I don't care about the keyboard, and I don't care about installing Ubuntu on it.

There's one thing I'm wondering about that isn't clear. Is there a USB port on the tablet part, or is the USB only on the keyboard part. I would probably buy the tablet without the keyboard, and I can't tell if that side has USB or not.

No usb port on the tablet, only on the keyboard. 

on the tablet you get a mini hdmi port, a micro sd slot, head phone plug and a 40pin custom plug for charging, connection to a pc or connecting to a keyboard.

---

### Post by allanh46 on 2011-08-28
> **forrestcupp said:**
> I've been looking at the Transformer just to use as an Android tablet only. I don't care about the keyboard, and I don't care about installing Ubuntu on it.

There's one thing I'm wondering about that isn't clear. Is there a USB port on the tablet part, or is the USB only on the keyboard part. I would probably buy the tablet without the keyboard, and I can't tell if that side has USB or not.
 
No  but  there is the microchip  the key board  is  handy way to protect the screen..  you might consider waiting till the transformer 2 comes out as you will be able to get a 3g model.

Personally I am not impressed with honeycomb..  get tired of having it treated as a mobile phone,,  I do not want a mobile phone..

---

### Post by allanh46 on 2011-08-28
> **Copper Bezel said:**
> So far as I can tell, only 9.04 UNR was released as a .img. There's ostensibly some way to turn a .iso into a .img, but I know as little about that as I do about installing on Android devices.

:confused: I have found an iso in the archive.. but the new release was out for less than a day before it pulled a vanishing act..  I am hoping to be dual  boot before long,, after they pulled the release  will work through it with techie friends  (if I still have any left.):)

I do have all the files to make my own img   if I can figure out how,,

---

### Post by forrestcupp on 2011-08-28
> **markp1989 said:**
> No usb port on the tablet, only on the keyboard. 

on the tablet you get a mini hdmi port, a micro sd slot, head phone plug and a 40pin custom plug for charging, connection to a pc or connecting to a keyboard.That sucks that they didn't put USB on the tablet. So does it come with a cord to connect it to a PC. I guess between that and a micro sd I would be ok.

> **allanh46 said:**
> No  but  there is the microchip  the key board  is  handy way to protect the screen..  you might consider waiting till the transformer 2 comes out as you will be able to get a 3g model.

Personally I am not impressed with honeycomb..  get tired of having it treated as a mobile phone,,  I do not want a mobile phone..I probably won't buy anything before Transformer 2 comes out, but I don't really want or care about 3G. Also, for my needs, I don't really mind if it is a giant version of my cell phone. I want it for a tablet, not a netbook. The only reason I'm even looking at this one is because I heard it's one of the best tablets, and it's interesting that I could turn it into a netbook if I ever wanted to.

---

### Post by dyltman on 2011-08-28
Just got mine yesterday, it's pretty darn sweet. The challange now is to get ubuntu on it!

---

### Post by rdnetto on 2011-08-29
> **allanh46 said:**
> :confused: I have found an iso in the archive.. but the new release was out for less than a day before it pulled a vanishing act..  I am hoping to be dual  boot before long,, after they pulled the release  will work through it with techie friends  (if I still have any left.):)

I do have all the files to make my own img   if I can figure out how,,

Why do you want UNR - hasn't Unity replaced it? The image provided by lilstevie on the XDA forum has Unity 2D on it.
Even if it didn't, the easiest way to install a different desktop manager is to just take the existing image, uninstall Unity 2D (it interferes with non-Gnome desktops) and run 'apt-get install kubuntu-desktop' or whatever - I can't imagine what you'd do with an ISO.

> **allanh46 said:**
> Personally I am not impressed with honeycomb..  get tired of having it treated as a mobile phone,,  I do not want a mobile phone..

Agreed - it drives me insane how you have so little control over whether or not the program is closed.

---

### Post by RastaCalavera on 2011-08-29
> **forrestcupp said:**
> 
I probably won't buy anything before Transformer 2 comes out, but I don't really want or care about 3G. Also, for my needs, I don't really mind if it is a giant version of my cell phone. I want it for a tablet, not a netbook.

What do you mean by this? The second one will run a different OS than android? Also the transformer aims for tablet/ netbook market. If you want a USB port maybe plug a female to female adapter into the end of the power cord?

---

### Post by forrestcupp on 2011-08-29
> **RastaCalavera said:**
> What do you mean by this? The second one will run a different OS than android? Also the transformer aims for tablet/ netbook market. If you want a USB port maybe plug a female to female adapter into the end of the power cord?

No. According to its official web site, it will be running Android Ice Cream Sandwich. Everyone was trying to figure out how to get Ubuntu installed on the first Transformer. Someone suggested that I wait for the Transformer 2 to come out, which I didn't know anything about, so I just was saying that I'm probably not going to buy anything before then anyway. Also, I was trying to clarify my question by saying that I'm not trying to install Ubuntu, and for my needs, I don't mind that it's like a giant version of a cell phone running Android. I'm not trying to make it into an Ubuntu computer; I'm wanting it to just be an Android tablet, which is what it is meant to be.

Since it has MicroSD, if it can be connected to a PC through the proprietary port to transfer files, I probably don't really need a USB port.

---

### Post by RastaCalavera on 2011-08-31
Ah I understand now. Yeah it is a very nice android tablet,i have done all of my posts with it. You can use the computer like you said for transferring files or there are a couple good FTP apps as well

---

### Post by forrestcupp on 2011-08-31
> **RastaCalavera said:**
> Ah I understand now. Yeah it is a very nice android tablet,i have done all of my posts with it. You can use the computer like you said for transferring files or there are a couple good FTP apps as well
Cool. I think I'd probably hook it up to my computer for large files, and maybe use DropBox for everything else. I found out DropBox has an Android app, which is pretty convenient.

---

### Post by RastaCalavera on 2011-09-05
Hey question for anyone who has a transformer, have you solved the short power cord issue? I just picked up a USB 2.0 cord that is an extension and it seems to charge the dock/tablet only when the tablet is docked. I don't know why it wouldn't charge the dock on its own..... anyone else experienc this? (stock honey comb not running ubuntu)

---

### Post by rdnetto on 2011-09-06
> **RastaCalavera said:**
> Hey question for anyone who has a transformer, have you solved the short power cord issue? I just picked up a USB 2.0 cord that is an extension and it seems to charge the dock/tablet only when the tablet is docked. I don't know why it wouldn't charge the dock on its own..... anyone else experienc this? (stock honey comb not running ubuntu)

Look at the actual plug - it's a USB 3 connector. While it may or may not charge via USB 2, it's going to be very slow. I've had no problems charging mine with a USB 3 extension cable.

---

### Post by forrestcupp on 2011-09-06
I've been looking online at a bunch of different tablets trying to figure out which one I want to get. I could either get a cheaper one now, like a Viewsonic G Tablet for $250, or wait and get a better one.

Last night I held a Transformer in my hands. I think I've decided to wait until I have the money and get one of these. The screen is pretty amazing on the Transformer. I'm glad I actually went and looked at them.

---

### Post by BeRoot ReBoot on 2011-09-06
This is precisely why I'm reluctant to buy a tablet - the only way to get them here appears to be through some online store from China or the USA/UK. People would be a lot more receptive if these things were actually in physical stores, since it's a product that relies heavily on what they call "user experience".

---

### Post by RastaCalavera on 2011-09-07
> **rdnetto said:**
> Look at the actual plug - it's a USB 3 connector. While it may or may not charge via USB 2, it's going to be very slow. I've had no problems charging mine with a USB 3 extension cable.

Ah its a usb 3.0? I read in another forum that it is a 2.0 thanks!

---

### Post by rg4w on 2011-09-07
> **forrestcupp said:**
> I've been looking online at a bunch of different tablets trying to figure out which one I want to get. I could either get a cheaper one now, like a Viewsonic G Tablet for $250, or wait and get a better one.

Last night I held a Transformer in my hands. I think I've decided to wait until I have the money and get one of these. The screen is pretty amazing on the Transformer. I'm glad I actually went and looked at them.
I absolutely love mine.  I have an iPad 2 and a good netbook, and the Transformer has replaced them both for me.

At this point you may want to wait until next month when the next version of the Transformer comes out.  Pretty much the same package, but it'll use the more recent Nvidia Tegra processor and is expected to sell for the same price as the current Transformer.

---

### Post by forrestcupp on 2011-09-07
> **BeRoot ReBoot said:**
> This is precisely why I'm reluctant to buy a tablet - the only way to get them here appears to be through some online store from China or the USA/UK. People would be a lot more receptive if these things were actually in physical stores, since it's a product that relies heavily on what they call "user experience".Best Buy sells tablets that you can try out, but you probably don't have Best Buys if you don't live in the US.

> **rg4w said:**
> I absolutely love mine.  I have an iPad 2 and a good netbook, and the Transformer has replaced them both for me.

At this point you may want to wait until next month when the next version of the Transformer comes out.  Pretty much the same package, but it'll use the more recent Nvidia Tegra processor and is expected to sell for the same price as the current Transformer.It's good to hear a testimony from someone who has one. I'm kind of hoping that when the new one comes out, the price for the current one will drop.

---

### Post by techgreen on 2011-09-28
The new one would be Transformer2, wouldn't it? It's rumored the T2 is going to adopt a quad-core processor. That's awesome!

---

### Post by lancest on 2011-09-29
Thought I posted here before. Too lazy to check.
Posting from my ASUS Transformer on (lag-free) Firefox 7.
TF is an awesome device, I keep it running all the time like a phone.
Keyboard is worth the money, very tactile for S-M fingers.
Using a 3G MIFI with it,I consider the TF best as a cloud computing device.
16 GB strage is adequate, using Google Music, UbuntuOne, Google docs.
Polaris Office included is also great.  
I will certainly buy the Quad Core. ASUS hardware is prime.

---

