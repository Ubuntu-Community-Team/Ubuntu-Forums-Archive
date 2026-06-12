---
title: "My horrible Saucy experience"
date: 2013-10-13
forum: Ubuntu Development Version
---

### Post by akf-mike-nw2 on 2013-10-13
Do not upgrade to saucy if you care in the least about losing services or anything you have installed.

First I run the dist upgrade and all looks good it boots and everything was there. THEN, I could not install remove or otherwise use software center because of the permissions issue  (yes the service was running yet it would not allow my user to run it) I tried to run it as root. Sure it loaded and acted like it was doing as I asked yet nothing really happened.

I then went to reinstall the permissions tool and dbus to fix it as others suggested. no better

I decided to try a fresh install 2 out of 3 were ok at initial boot and one complained apparmor failed but let me in with a bug report request me in the face.

Then I got a fresh install working only to find anytime I specified a bridge and issued service networking restart my x session completely bailed or my favorite killed my desktop until the next restart.

I mean GKSUDO WAS EVEN MISSING FROM THE BASE INSTALL *face Palm* that's just embarrassing.

I am very good at computers been in them since I was 3 (now over 30 doing server support) and after a WHOLE day of shaking my fist at every turn I still have yet to have any kind of usable computer running Saucy.

I get the whole beta deal, but seriously if I have these problems I fear for many others out there. Let's not even talk about when I search for saucy forums the moderators and or devs are more worried about what to call their new version which is scheduled to be released very soon and it is soo buggy a Linux guru can't get it running after 12 hours WOW.

Trust me my computer can run it, and I tried EVERYTHING to get it going nicely.

I had to use my tablet to find this forum and write a warning I hope reaches both unsure users and the developers as a SEVERE word of caution, shock, and disbelief. This is obviously still in alpha and doesn't deserve to be labeled even beta yet.

---

### Post by Toz on 2013-10-13
*Moving to the **Ubuntu+1** forum (though since its not really a request for help, it might be better served in the General Chat.)*

Written from my fully functional saucy install.

---

### Post by cariboo on 2013-10-13
I hoipe you at least reported the bugs, when you got the apport messages.

---

### Post by craig10x on 2013-10-13
Again...don't know why people avoid using the live iso's installer method of upgrading...that is how i moved from 13.04 to 13.10 development 3 months ago and it went superbly....as i described in another thread of mine here...and 13.10 has been running great ever since...it is probably the BEST way to upgrade and also for some strange reason...the most AVOIDED...
A pity i say :(

---

### Post by akf-mike-nw2 on 2013-10-13
Of course, just shocking to download a beta 2 to find it is in use maybe barely out of alpha stage if we stretch the definition. Looks like another case of the OS trying to jump too far ahead too fast (Android did it too with 4.3). Just wish developers would recognize when there are issues and it may not be a bad thing to acknowledge that and push the time table for release back so they can squash bugs and get it truly to the stage it is stated to be (I mean even with Raring beta 2 was fully production ready with only small issues saucy has some real issues (not big and like Android mostly surrounding security), but those problems while small are having massive effects when you can't install/remove software or just restarting your network interface causes the xsession to bail to login screen. Not to mention missing a core piece of software in a base install is just shocking to see from ubuntu community.

---

### Post by PJs Ronin on 2013-10-13
I'm a linux noob so I treat new versions with a great deal of scepticism.   To prepare for the worst I created two new partitions.   In the first partition I did a DD copy of my Raring partition and then did the in-place dist-upgrade.   In the second partition I did a fresh install from a daily iso.   Both went as smooth as silk... so smooth that Saucy is now my production environment c/w postgresql databases and Win 7 Pro in Virtualbox VMs.

It's good to be the King.

---

### Post by vasa1 on 2013-10-13
> **akf-mike-nw2 said:**
> ...
I mean GKSUDO WAS EVEN MISSING FROM THE BASE INSTALL *face Palm* that's just embarrassing.

I am very good at computers been in them since I was 3 ....
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095) ?

---

### Post by mc4man on 2013-10-13
> **vasa1 said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095) ?
That bug's not really about the user getting gksu default installed, it  was as good as  gone in 13.10+ anyway.

If someone wants gksu they can simply install it or have it installed from an app that depends on. 
Wouldn't describe it as "core" by any means.

---

### Post by kansasnoob on 2013-10-14
> **craig10x said:**
> Again...don't know why people avoid using the live iso's installer method of upgrading...that is how i moved from 13.04 to 13.10 development 3 months ago and it went superbly....as i described in another thread of mine here...and 13.10 has been running great ever since...it is probably the BEST way to upgrade and also for some strange reason...the most AVOIDED...
A pity i say :(

+1!

At the very least it's much faster!

---

### Post by ventrical on 2013-10-14
> **akf-mike-nw2 said:**
> 

I am very good at computers been in them since I was 3 (now over 30 doing server support) and after a WHOLE day of shaking my fist at every turn I still have yet to have any kind of usable computer running Saucy.




It gets better from here on in. :) lol

---

### Post by grahammechanical on 2013-10-14
Up until a week or two ago I would have agreed with you if you were commenting on the running of the Live Session or the working of the Installer. I see the live session/installer as a separate entity to the version of Ubuntu under development. In the past some of us have made comments about the live session/installer. The thing that has given me a bad live session/installer experience in recent weeks was the Ubuntu One login. 

I have a better opinion of the distribution called Saucy Salamander than you do and I have been using it as a normal working OS since the beginning of the development cycle all those weeks ago. That makes me more informed about Ubuntu 13.10 than you. 

Why are you expecting beta software to be perfect? Yet you do not advise people to avoid installing beta software but to avoid installing the released version of the software, which you have not yet tested. Nobody has yet installed Ubuntu 13.10 (released). I cannot consider you as an unbiased expert.

Ubuntu is not a distribution for Linux gurus, such as yourself. It has been from the beginning a distribution for humans. I can understand why the developers think that humans would not have a need to edit system scripts. They don't. 

Ubuntu 13.04 does not have gksu installed by default. I have not noticed very many people posting on Ubuntu forums wondering why gksudo gedit not longer works. In fact when we run the gksudo command we get the advice that gksu is not installed along with the command on how to install it. What is so wrong with that? The same situation applies in Saucy Salamander. If you know it should be there, then you will know how to get it there. You will be told how to get it there. You raise a trivial issue.

Thank you having such concern for our welfare that you had to search to find this forum just to give us your warning. You need not of troubled yourself. Had you looked around this forum a bit you would have seen the Ubuntu+1 section where the state of the development release is discussed openly all though the development cycle.

Regards to all Ubuntu+1 testers.

---

### Post by craig10x on 2013-10-14
> **kansasnoob said:**
> +1!

At the very least it's much faster!

Oh yes! and probably better too (can't quite say since i never tried the software updater upgrade method but i just get a "sense" that it is probably true)....
For my last test, as i will now be leaving ubuntu development testing (it has been a fun and interesting run) when 13.10 final is released on thursday, i am going to download the iso and over the weekend (actually probably on friday) i will be upgrading my 13.10 development to 13.10 final (using the iso installer upgrade method again)...

I figure if all goes well it should clean out my system and be essentially like a fresh 13.10 final install..."fingers will be crossed" of course ;)

Worse case: I have to do a clean install....but if it works out well then i plan to continue using the method to "roll" from each final version into the next one...
I always love having the latest ubuntu but i was getting a bit tired of doing clean installs every time...and spending all the time adding my "stuff" back in again (apps and data)....

I will post a thread about it after it is done... :D

---

### Post by richardsdma on 2013-10-14
today, i have had upgraded my 13.04 to 13.10 via update manager and noticed that screen does not turn off anymore. whatever the time i set.....it just does't turn off. 
and i have had some nm-applet crashes too, even worse than in 13.04. 
in this moment, for me, it is a big mess. 
still, i will try a clen install later this month.

---

### Post by craig10x on 2013-10-14
@richardsdma: sorry to hear that...but this is just why i am such a proponent of doing the upgrade by using the option to do an upgrade on the live iso installer...my upgrade using that method went great (only 2 things had to be re-installed, Chrome and MS fonts) and it was fast...for all intensive purposes, while it was going on it looked just like a clean install with slide shows and everything and super fast too...It seems i read so many experiences where people have used the update manager to do it and had some kind of bork or mess as a result...

i don't know if this will work (since you have kind of a mess on your hands) but before doing that clean install, you might try using the live iso installer upgrade option to see if it can possible re-do it for you and straighten things out...you really would not lose anything by trying since the worse case would be you will have to re-do as a clean install...If you do it, let us know how it worked out for you...

---

### Post by richardsdma on 2013-10-14
thanx
is it possible to upgrade via liveUSB even if you have multipme OS? in this moment, i have 12.04 and wind seven......along with 13.10.

but still, i dont know if tha problem is with tha way of upgrading or in the ubuntu 13.10 itself.

---

### Post by ventrical on 2013-10-14
Ok.. I took up the task to manually upgrade from an old version of Quantal to Saucy by editing the sources.list. After the upgrade I got this 

```

 subprocess installed post-installation script returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 libkfile4
 libsyndication4
 python-aptdaemon
 kdepimlibs-kio-plugins
 gstreamer1.0-plugins-good:i386
 gdm
 kde-workspace-bin
 libkdewebkit5
 python3-pyqt4
 libkblog4
 kde-window-manager-common
 libedataserver-1.2-17
 libkidletime4
 unity
 libsoup2.4-1:i386
 libsoup-gnome2.4-1:i386
 libakonadi-calendar4
 libkdnssd4
 libedata-cal-1.2-20
 libkmbox4
 libkmime4
 libkrossui4
 libgail-3-0:i386
 unity-services
 plasma-widgets-addons
 libgweather-3-3
 libgdk-pixbuf2.0-0:i386
 libgdk-pixbuf2.0-dev
 plasma-widgets-workspace
 libkpimtextedit4
 gstreamer1.0-plugins-base:i386
 libktnef4
 libpango1.0-dev
 libgstreamer-plugins-good1.0-0:i386
 gnome-panel
 accountsservice
 xserver-xorg-core
 plasma-dataengines-addons
 libgoa-1.0-0:i386
 gnome-contacts
 libkldap4
 libakonadi-contact4
 libmicroblog4
 libkntlm4
 python3-gi
 evolution-data-server
 libgtk-3-dev
 python-aptdaemon.gtk3widgets
 plasma-netbook
 libunity9:i386
 gnome-font-viewer
 initramfs-tools
Processing was halted because there were too many errors.
camel2@ubuntu:~$ 

```

but now I am about to reboot and see whats up with this old install.

 brb

---

### Post by craig10x on 2013-10-14
@ richardsdma: Never did a usb install so not sure...perhaps someone else can advise if it offers the upgrade option on there the way the iso on dvd does...or could you perhaps run a live session on the usb to check it yourself?  Keep in mind you can start up the installer to have it look at what you got and then offer it's various options just to LOOK AT IT...and you aren't actually installing unless you hit that "install now" button...
That is how i checked the options myself...after seeing what the installer would do for me automatically, i simply backed out and went back to the live session and then left it....

---

### Post by kansasnoob on 2013-10-14
> **richardsdma said:**
> thanx
is it possible to upgrade via liveUSB even if you have multipme OS? in this moment, i have 12.04 and wind seven......along with 13.10.

but still, i dont know if tha problem is with tha way of upgrading or in the ubuntu 13.10 itself.

You will not be offered the upgrade option from the live image if you have more than one **buntu based distro installed.

---

### Post by craig10x on 2013-10-14
Oh darn...well for me it's ok because i only have one ubuntu installed (actually, that is all i have installed...lol) so in that case, i can only suggest this as a better way of upgrading IF you only have one ubuntu installed...otherwise, if you want to use the upgrade method, you have to use either the software updater or the terminal methods and hope for the best...

Would be nice if they would have it offer the upgrade option on the ubuntu live installer if you have more then one ubuntu....but perhaps that is not possible...

---

### Post by philinux on 2013-10-14
There's no perhaps about it. It's a feature of ubiquity at the moment.

---

### Post by ventrical on 2013-10-14
I was able to upgrade succesfully to 13.10 via the network. It was an older, experimental install of QQ and I used the terminal method. It did not go all smoothly. Thankfully I had fvwm-crystal DE installed and I was able to go there, use synaptic and complete the upgrade while fixing several borked depends.

  I'd rather use SDC and "live" USB ! :) lol.. It is so much more expedient :) lol

---

### Post by buzzingrobot on 2013-10-14
Saucy works fine for me. Bugs? Yes. I file them.  They're all known.

i never do in-place distribution updates. I keep /home on a separate drive and backup every config file I edit.

All automated updates must make assumptions about the system they are updating.  The more a user has tweaked and altered his system, the greater the chances the update will fail.

---

### Post by patrickscarroll on 2013-10-14
I went back to Windows 7 and Ubuntu 13.04.  Forum support is lacking, bugs persist, having to plug and unplug and replug your keyboard to make an OS work is just silly, having to click countless windows just to plug in your iPhone is frustrating, inability to support 32-bit Linux programs is a show-stopper.  Not worth the "upgrade".

---

### Post by deadflowr on 2013-10-15
> **patrickscarroll said:**
> I went back to Windows 7 and Ubuntu 13.04.  Forum support is lacking, bugs persist, having to plug and unplug and replug your keyboard to make an OS work is just silly, having to click countless windows just to plug in your iPhone is frustrating, inability to support 32-bit Linux programs is a show-stopper.  Not worth the "upgrade".

You should go back to your other thread and edit it down to one issue.

SOP is one issue , one thread.

And multiple issue threads get confusing, because the answers get mingled post to post.

I, myself, have ran 13.10 since development started and haven't had a problem, aside from update issues early on.

---

### Post by patrickscarroll on 2013-10-15
> **deadflowr said:**
> You should go back to your other thread and edit it down to one issue.

SOP is one issue , one thread.

And multiple issue threads get confusing, because the answers get mingled post to post.

I, myself, have ran 13.10 since development started and haven't had a problem, aside from update issues early on.

Thanks for the help.  My issues are resolved now with your help. I'm glad your system is working just fine. Mine wasn't.

---

### Post by kansasnoob on 2013-10-15
> **philinux said:**
> There's no perhaps about it. It's a feature of ubiquity at the moment.

It would undoubtedly be incredibly complex to try and have ubiquity offer upgrades if more than one **buntu install exists ;)

But those who multi-boot are likely to just use the manual partitioning option anyway ............ or I'd at least hope so :)

---

### Post by philinux on 2013-10-15
> **kansasnoob said:**
> It would undoubtedly be incredibly complex to try and have ubiquity offer upgrades if more than one **buntu install exists ;)

But those who multi-boot are likely to just use the manual partitioning option anyway ............ or I'd at least hope so :)

Indeed.

---

### Post by buzzingrobot on 2013-10-15
> **patrickscarroll said:**
> I went back to Windows 7 and Ubuntu 13.04.  Forum support is lacking, bugs persist, having to plug and unplug and replug your keyboard to make an OS work is just silly, having to click countless windows just to plug in your iPhone is frustrating, inability to support 32-bit Linux programs is a show-stopper.  Not worth the "upgrade".

You get what you pay for on forums. 

32-bit Linux programs work fine on 32-bit Linux, and, as well, on 64-bit Linux with the correct libraries installed.  Much, much better than they work on Windows. ;)

A total of 7 posts here isn't much to go by.  In my experience, requests for specific help with specific issues coupled with information usually prompt responses here.

At the least, you should consider that since the scale and variety of issues you are experiencing far exceed those reported by other users, perhaps there is something on your end that is the cause.

---

### Post by craig10x on 2013-10-15
@phillinux and kansasnoob:  Yes, i can certainly understand that...it would be very complicated to offer an upgrade option if you are running multiple ubuntus...

But here is an interesting question: What if someone is...for example: dual booting with windows...or multi booting with some combination of either windows or/and other non ubuntu linux distros...whatever combination...BUT only has ONE ubuntu on his system...in that situation, would the installer STILL offer the Upgrade option or would it not?

Inquiring minds want to know ;) :D

---

### Post by OGpmpdog on 2013-10-15
> **craig10x said:**
> @phillinux and kansasnoob:  Yes, i can certainly understand that...it would be very complicated to offer an upgrade option if you are running multiple ubuntus...

But here is an interesting question: What if someone is...for example: dual booting with windows...or multi booting with some combination of either windows or/and other non ubuntu linux distros...whatever combination...BUT only has ONE ubuntu on his system...in that situation, would the installer STILL offer the Upgrade option or would it not?

Inquiring minds want to know ;) :D

Hi, I'm multi-booting Windows7, Saucy, and Mageia.:P.

This is news to me: using the Live CD to upgrade instead of install.  I usually see the "upgrade" option when the OS is at EOL.  

I dont believe I answered your question, but I wonder: 

Is the Live CD upgrade faster than upgrading the Software Sources to next (TT) version?

---

### Post by craig10x on 2013-10-15
The Upgrade using the live cd is very fast...mine took only about 5 minutes longer then a normal "clean" install...i would say 25 minutes...
That is how i went to 13.10 development from 13.04....it can be used as a means to go to the next development...you would do that when the first daily builds arrive for 14.04...then you could use that method instead of changing the source lists...

Hey...by the way...since you are multi-booting...but only have one ubuntu...try popping in a live cd of 13.10 if you have one and see if the installer offers you the option to upgrade to 13.10....
i am running 13.10 by itself and if i put in a disc of 13.10 it offers to clean install 13.10 or upgrade to it...(yes even though i am already running it...lol)...you know you can check it like that, just don't hit the "install now" button...lol

So, if you can check it or anyone else here who is multi booting (but only with 1 ubuntu) i would be curious to know...

---

### Post by oldos2er on 2013-10-15
Closing this thread that began as a misinformed rant and is now off-topic. craig10x, please start a new thread for your valid questions.

---

