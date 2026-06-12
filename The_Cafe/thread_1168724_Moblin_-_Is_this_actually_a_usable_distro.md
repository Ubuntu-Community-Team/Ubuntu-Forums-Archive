---
title: "Moblin - Is this actually a usable distro?"
date: 2009-05-24
forum: The Cafe
---

### Post by kevdog on 2009-05-24
Ive heard a lot of good things about Moblin for netbooks, however just wondering if the new release v2 beta is actually a usuable distribution?  I'm not quite sure how moblin works, however really just need access to internet (through firefox preferably) through a wireless connection.

If wireless isn't working through the GUI with WPA(which the moblin website has thousands of posts with complaints), I suppose its possible to drop to the command shell and make a manual connection?

Can someone tell me about the moblin repositories?  Are these rpm based (fedora) or something else?  Just wondering the ability to compile programs if necessary and pick up dependencies if need be.

Thanks.  I'm really interested in first dual booting after partitioning with grub on the Asus A0751h.

---

### Post by gnomeuser on 2009-05-24
If you are concerned about available software you can use the openSUSE moblin build, that will give you a backend with lots of software and enginnering from the openSUSE community and Novell.

[http://news.opensuse.org/2009/05/19/moblin-v20-beta-on-opensuse/](http://news.opensuse.org/2009/05/19/moblin-v20-beta-on-opensuse/)

---

### Post by stmiller on 2009-05-24
It's still early, so I'd say beta means beta this time. You can download the image and try it out in virtualbox. Looks fantastic. Browser is chromium / google chrome.

But it's a little rough changing to the different screens and starting those apps.

---

### Post by snowpine on 2009-05-24
It shows promise but is not there yet in my opinion. More of an alpha than a beta at this point. :) It needs the following features before I would even consider using it on my Dell mini 9: wireless, battery meter, shutdown/suspend/hibernate, right click menu, flash, mp3, a browser that lets you download files, openoffice, the ability to install to usb/sd, and something other than twitter as the most prominent application. ;)

---

### Post by bigbrovar on 2009-05-24
> **stmiller said:**
> It's still early, so I'd say beta means beta this time. You can download the image and try it out in virtualbox. Looks fantastic. Browser is chromium / google chrome.

But it's a little rough changing to the different screens and starting those apps.

Yeah moblin is still very beta, lots of features are yet to be implemented and and most if the issues and bugs are already known to the devs.

BTW the Browser is based on Firefox not chromium

---

### Post by celticbhoy on 2009-05-24
It depends what you want to use it for, as said it is still early in development. If you just want to browse, and a little IM (assuming you use the right protocols) then fine. It is however worth a look if you are on an atom netbook, everything runs & links very smooth.

---

### Post by kevdog on 2009-05-24
I'm wondering with the responses here if I should just go with crunchbang right now rather than moblin.

Any knowledge on a reasonable boot time with #!?

---

### Post by hanzomon4 on 2009-05-24
Moblin is not really a distro, right? I mean Intel intends for distros like Suse and Ubuntu to incorporate Moblin in to their distros. Things like package management and packages are not Moblins bag. No? Yes?

---

### Post by Warpnow on 2009-05-24
Moblin is very usable interface wise if you can deal with the lack of any good programs.

---

### Post by Sashin on 2009-05-24
Can't you get Open Office, blender etc on it? Just like any other linux distro.

---

### Post by michael37 on 2009-05-24
I tried it, looks so-so in VM (virtualbox).  The graphics performance is too slow to really appreciate it.

Will try it on my mini 12, see how it works on a real netbook.

Given that I've been using Android for half a year, Moblin is definitely behind Android.

---

### Post by gnomeuser on 2009-05-24
> **hanzomon4 said:**
> Moblin is not really a distro, right? I mean Intel intends for distros like Suse and Ubuntu to incorporate Moblin in to their distros. Things like package management and packages are not Moblins bag. No? Yes?

Moblin is a proper distro, it is built on a mix of openSUSE and Fedora. They use the Open Build Service Novell built and work closely with upstream for many projects.

Now other distros also can take their work and their new UI and do their own Moblin version but the Linux Foundation most certainly intends to continue development and build a product for users and OEMs as well. Consider it the reference implementation.

---

### Post by snowpine on 2009-05-24
> **kevdog said:**
> I'm wondering with the responses here if I should just go with crunchbang right now rather than moblin.

Any knowledge on a reasonable boot time with #!?

Crunchbang is my very favorite Ubuntu derivatve, and I cannot recommend it highly enough.

Boot time is identical to Ubuntu from power on to the login screen, and from login to the Openbox desktop noticably quicker than to Gnome on a standard Ubuntu install.

---

### Post by kevdog on 2009-05-25
I guess it depends on machine, but what kind of boot time are we talking about here from on to desktop? (If it takes like a second or two to type in the username/password).

---

### Post by dcherryholmes on 2009-05-25
> **kevdog said:**
> I guess it depends on machine, but what kind of boot time are we talking about here from on to desktop? (If it takes like a second or two to type in the username/password).

The default install of the moblin beta has automatic login, so no passwords required.  I just stopwatched mine from cold boot to the display of the m_zone page (basically, the desktop), and the time was 16.537 seconds on my eee 900A.  The responsiveness of the interface and opening apps is also much sped up from other OS's I've run on the same hardware.  The new custom web browser (based on the gecko engine) is also blisteringly fast, although that is the one area of this beta that is not finished enough to be usable for me, so I've stuck with firefox, which is pre-installed.  Firefox loads pages faster on moblin than the other OS's as well.

The interface is gorgeous, and the most usable I've seen yet.  I've gone through stock ubuntu, easy peasy, eeebuntu 2.0 and 3.0, and UNR, and this is the best OS I've seen yet.  It is a different interface, though, and may not be to everybody's taste.  If you like the NBR interface at all, it may be up your alley.  The only disappointment for me is that they ditched ubuntu and based it on a mix of red hat and suse, forcing me to dust off my yum skills.

---

### Post by kevdog on 2009-05-25
dcherryholmes

Great feedback.

16.5 seconds?  Anyway to get that down under 10?  That seems like a long time to me.  But great review none the less.

Suse -- yum.  Yes in my opinion disappointing but since I'm a nobody who really cares anyway!

---

### Post by dcherryholmes on 2009-05-25
> **kevdog said:**
> dcherryholmes

16.5 seconds?  Anyway to get that down under 10?  That seems like a long time to me.  But great review none the less.



You know, on the face of it I thought "Man, that guy is demanding."  But then I thought about how disappointingly slow the SSD in this thing is, and what a huge influence disk speed is on boot times.  With better ssd tech, you probably *could* get that time down near ten seconds.

The boot time is mostly a moot point, though.  Suspend works, and when you are finished using it you just close the lid and it suspends.  One of the first questions you ask when using moblin is where the damn logout/reboot button is hidden.  The answer is, there isn't one (yet).  When you close the lid, it suspends.  If you want to turn it off you.... wait for it..... press the power button, which initiates a shutdown.  The whole thing brings it a lot closer to an appliance kind of feel.

Another moblin tip for anyone trying it is, make sure you go into Software Sources and tick "development packages for the next moblin release to enabled."  It could potentially impact the stability of your *beta* OS, but  I picked up quite a few updates -- including a kernel update -- and it actually made the thing run better (most notably smoothing out resume from suspend).

---

### Post by Sashin on 2009-05-26
I've tried it now, it's very glitchy. They should have released this as an alpha not a beta.

---

### Post by Warpnow on 2009-05-26
If you are timing boot with a stop watch a large portion of a quick boot time will be the bios loading, which I don't think can be sped up.

---

### Post by gordebak on 2009-05-26
It's a live usb image, you can test it live. I fell in love with the interface and boot time of Moblin, so I installed it on my Eee PC 1000H. 

Yes, there are some issues, but it works fine, and I guess in no time the actual release will come. Btw, when it's released, I think Fedora packages will be  available to install on Moblin. 

Don't be afraid to dual boot and test the beta release. This is what community can do the most.

---

### Post by nothingspecial on 2009-05-26
I`ve installed it on a little partition on my Samsung NC10. 

While I love the interface, it`s not for me.

However it will be perfect for my wife's aspire one. Until there`s a decent array of software available, especially all the codecs needed to play her music and vids, though I wouldn`t dare.

I`ll keep testing though.

---

### Post by celticbhoy on 2009-05-26
A quick question for anyone who has installed this to a HD. did you install as a dual boot or as a stand alone system. If you installed a dual boot I presume that you are still using the grub on you Ubuntu install, and if so can you post the grub entry for the Moblin install?


Cheers.

---

### Post by nothingspecial on 2009-05-26
> **celticbhoy said:**
> A quick question for anyone who has installed this to a HD. did you install as a dual boot or as a stand alone system. If you installed a dual boot I presume that you are still using the grub on you Ubuntu install, and if so can you post the grub entry for the Moblin install?


Cheers.

What I did is during the install when it asks you if/where to install grub. I selected /dev/sda3 which is where moblin resides, rather than /dev/sda1 which is ubuntu. I then copied the entry from moblin`s grub to ubuntu`s. As long as ubuntu is on your first partition this will work.

Any way since you ask here it is

```
title Moblin (2.6.29.3-13.1.moblin2-netbook)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.29.3-13.1.moblin2-netbook ro root=/dev/sda3 quiet
```

---

### Post by celticbhoy on 2009-05-26
Thanx, will give it a try. I have been using it on a USB key for now, but I would like to see the performance on my AAO with a proper install.

---

### Post by nothingspecial on 2009-05-26
Of course anyone embarking on a grub tinker would back up his/her original first.  :wink:

---

### Post by celticbhoy on 2009-05-26
HD install works fine, done the updates and I am now using it for general browsing and playing about with some media files. It is far from complete but I still think the look and feel on my AAO is the best of the netbook specific distro's or interfaces I have tried.

---

### Post by aeiah on 2009-05-26
> **kevdog said:**
> I'm wondering with the responses here if I should just go with crunchbang right now rather than moblin.

Any knowledge on a reasonable boot time with #!?

on my acer aspire one 1GB / 160GB i get the openbox desktop in about 20 seconds, suspend is about 8 seconds and hibernate is somewhere in between. everything works on it except cheese (the webcam does, i just cant be bothered to mess with cheese). it would probably go faster but ive made the desktop look pretty at the behest of my girlfriend.

---

### Post by Regenweald on 2009-05-26
The thing about where operating systems are going... They all seem to want to centralize online social activities and the venerable 'cloud', but what about persons who do not facebook, twitter or blog ? The first thing that i would need to do with moblin is remove all the online cruft from my gui. If at all possible.

More and more people like me are going to have to spend time adjusting GUI's and killing unnecessary services on this new online-centric OS market.

---

### Post by hanzomon4 on 2009-05-26
> **Regenweald said:**
> The thing about where operating systems are going... They all seem to want to centralize online social activities and the venerable 'cloud', but what about persons who do not facebook, twitter or blog ? The first thing that i would need to do with moblin is remove all the online cruft from my gui. If at all possible.

More and more people like me are going to have to spend time adjusting GUI's and killing unnecessary services on this new online-centric OS market.

Resistance is futile... I didn't even use IM or really email that much until I started using Ubuntu. I wanted to make use of everything like pidgin and getting help from a forum kinda eased me in. Now I'm an addict! No but I do feel more connected with the goings on in my city and with my friends (the flesh and blood type). I think the proliferation of  tools such as the ones in moblin will make it more appealing to holdouts or unavoidable. Sooner or later... like the net, it will get you... hehe "the net", I made a funny

---

### Post by dcherryholmes on 2009-05-28
Just an FYI: if you have the development repo enabled like I do, there are 170 updates available today.  I'm installing them now, and will report back any major improvements.

---

### Post by dcherryholmes on 2009-05-29
Quick follow up to my last post.  The only overt thing I noticed is that the problem with coming out of hibernate appears to be fixed.  Sound is still disappointingly low, though.

---

### Post by celticbhoy on 2009-05-29
What you using it on - on my AAO the sound is a lot louder than Ubuntu or Linpus ever were.

---

### Post by michael37 on 2009-05-29
> **michael37 said:**
> I tried it, looks so-so in VM (virtualbox).  The graphics performance is too slow to really appreciate it.

Will try it on my mini 12, see how it works on a real netbook.

Given that I've been using Android for half a year, Moblin is definitely behind Android.

Tried Moblin Live on Mini 12.  Doesn't work.

---

### Post by dcherryholmes on 2009-05-30
> **celticbhoy said:**
> What you using it on - on my AAO the sound is a lot louder than Ubuntu or Linpus ever were.

I'm using a eee 900a.  One of the unexpected surprises when I bought this thing was just how loud the sound was coming out of it.... easily better than my thinkpad.  I've checked alsamixer and recall seeing only one channel, so it's probably the case that the bottom speaker isn't recognized.

---

### Post by dcherryholmes on 2009-06-05
Sound automagically came back up to full volume (i.e. the bottom speaker started working) on one of the recent updates.  eee pc 900A.

---

