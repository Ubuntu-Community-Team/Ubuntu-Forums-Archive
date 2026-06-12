---
title: "Lubuntu Beta 2 - Testing."
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-03-24
[http://lubuntublog.blogspot.co.uk/2012/03/lubuntu-1204-beta-2.html](http://lubuntublog.blogspot.co.uk/2012/03/lubuntu-1204-beta-2.html)

---

### Post by andrewabc on 2012-03-24
Why is lubuntu beta2 almost a week ahead of normal ubuntu beta2?

Also not listed at
cdimage.ubuntu.com/lubuntu/releases/12.04/

??
I assume this is really just a test build of beta2 with final beta2 being this thursday?

Also why is every link on the link in your post point towards facebook (yet the facebook link also includes real link)?

Hmm, looks like iso testing of beta2, not final beta2.
iso.qa.ubuntu.com/qatracker/milestones/210/builds

---

### Post by LawrenceFriend on 2012-03-24
Good Question!!!!

---

### Post by cariboo on 2012-03-24
The announcement is not worded very well, maybe this quote helps?

> You can grab it here for testing

---

### Post by Rodney9 on 2012-03-25
I tried it as Live, can't see anything new. 

Pcfman and the software centre both crashed before even opening.

Rodney

---

### Post by makitso on 2012-03-25
Can't say I am a fan of the new login page greeter :-(

---

### Post by phillw on 2012-03-25
Hi guys, if you take a quick read of [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) and in particular [https://wiki.ubuntu.com/Lubuntu/Testing#Testing](https://wiki.ubuntu.com/Lubuntu/Testing#Testing) you will see that all release candidates from the 1st alpha up to and including the final release hit the iso-tracker for the valiant testers to shake down & check that they are okay to release on the public :)

During this time, the testers switch from daily builds back to iso tracking area at [http://iso.qa.ubuntu.com/qatracker](http://iso.qa.ubuntu.com/qatracker), It is here you will see that the current crop of Beta 2's are logged as 'testing'.

I hope that clears any mis understandings, I'm still new to this as well & it has taken a while for me to get my head round it all!

If there are any areas on the wiki area that you need extra clarification on, please feel more than free to ask me & I'll ensure it gets answered.

Regards,

Phill.

---

### Post by jerrylamos on 2012-03-26
Just did a clean quick successful lubuntu 20120325 Beta 2 candidate (zsync'd from daily build).

Everything working except sound.  pcmanfm hasn't even crashed yet.

Of my 4 test pc's, sound only works on one of them.  Yes there's a launchpad bug.  

Well, on lubuntu, everything else I've tried O.K. so far, except a whole lot more responsive and crisp than "ubuntu".

Jerry

---

### Post by MG&amp;TL on 2012-03-26
> **Rodney9 said:**
> I tried it as Live, can't see anything new. 

Pcfman and the software centre both crashed before even opening.

Rodney

LSC: [URL="https://bugs.launchpad.net/ubuntu/+source/lubuntu-software-center/+bug/959867"]We're working on it!
[/URL]

Julien Lavergne ("boss!") is on it.

PCManFM-works here no prob, I can't say for you. :)

---

### Post by andrewabc on 2012-03-27
> **jerrylamos said:**
> Just did a clean quick successful lubuntu 20120325 Beta 2 candidate (zsync'd from daily build).

Everything working except sound.  pcmanfm hasn't even crashed yet.

Of my 4 test pc's, sound only works on one of them.  Yes there's a launchpad bug.  

Well, on lubuntu, everything else I've tried O.K. so far, except a whole lot more responsive and crisp than "ubuntu".

Jerry

Bug link?

Is it a sound problem where volume is turned all the way down (impossible to increase), so if you crank speakers up you can hear stuff barely? Or no volume icon (or sound) at all?

I had the volume turned down all the way and can't change it bug last several releases, but beta1 showed this bug fixed. Hope it didn't come back!

---

### Post by jerrylamos on 2012-03-27
Did an update.  Sound works fine now.

Oh, yes, pcmanfm sitting in the background crashed.  Made a launchpad bug for some reason ? they couldn't process it.

Try again later.

Doing a zsynch getting ready for Thursday's beta 2, will install again then.

Jerry

---

### Post by DogMatix on 2012-03-27
I've been testing Lubuntu 12.04 since alpha. No real issues so far. pcmanfm has unexpectedly closed a few times, generally when I yank out my pendrive storage.

I generally test Ubuntu+1 on this particular partition on my Acer One netbook, but, as the netbook has got a little longer in the tooth and the Unity desktop is a a little more demanding on resources I decided on lxde. 

Generally impressed. Not a Chromium fan though. Installed Hotot to feed my Twitter habit, Hotot didn't work to start with but the issue has been resolved (there is a bug report on launchpad - somewhere!). Also, the Openbox session has been a revelation.

---

### Post by ventrical on 2012-03-27
> **jerrylamos said:**
> Just did a clean quick successful lubuntu 20120325 Beta 2 candidate (zsync'd from daily build).

Everything working except sound.  pcmanfm hasn't even crashed yet.

Of my 4 test pc's, sound only works on one of them.  Yes there's a launchpad bug.  

Well, on lubuntu, everything else I've tried O.K. so far, except a whole lot more responsive and crisp than "ubuntu".

Jerry


 I had a major crash with my older SOYO system, but I used the 'standard' ISO rather than the alternate. I thought the ISO was damaged but I just installed that into a 2.2GHz system and the  install was seamless .. 15 minutes give or take a few. I'm not sure I'll be able to test the alternate before  the night is over.  L ubuntu is working just great.

Also .. I have Ubuntu canditate running on 256MBDDR ram !!! with Unity 3D. I just love pushing this stuff to the limit.  These latest ISOs are really rocking!

---

### Post by andrewabc on 2012-03-27
forgot to mention:

When I had 10.10 on liveusb and I tried getting chromium to autostart when computer turned on, I couldn't get it to work properly. The best I could do is get two chromium windows to open, but they were very small size. I have no idea what happened or why. I tried googling all the possible solutions and edited about 10 different config files. With previous versions a simple google search would give the best answer and always worked fine, so I don't know why all of a sudden I failed at doing it.

Can anyone tell me exactly what to do for 11.04 to get chromium to autostart when computer turned on?
What config file etc. I guess what command to put into terminal, and what to insert into the config file. Thanks! This will be very important for liveusb users like me who just want a fast web browsing OS.

I'm not sure why autostart programs has not been implemented into a GUI yet. I know it does have a gui that shows what autostarts (normal ubuntu stuff), but no way to add/remove (other than uncheck).
I thought there was talk of this in past releases, but don't think it ever happened.

---

### Post by jerrylamos on 2012-03-27
> **DogMatix said:**
> Generally impressed. Not a Chromium fan though. Installed Hotot to feed my Twitter habit, Hotot didn't work to start with but the issue has been resolved (there is a bug report on launchpad - somewhere!). Also, the Openbox session has been a revelation.

About the first thing I do on a lubuntu install is sudo apt-get synaptic, straighten out the repositories, remove completely chromium so synaptic automatically installs firefox.  Synaptic install adobe-flashplugin and then I'm off and running.  Oh, yes, restore a couple hundred bookmarks....

Firefox uses less space than chromium, not an over riding factor, however chromium and I don't do well handling bookmarks and I forget how to do flashplugin on chromium but I've done it in the past.

Running lubuntu on my thinkpad (fast!) unity looking for bugs on this Compaq tower.

Jerry

---

### Post by lisati on 2012-03-27
> **jerrylamos said:**
> About the first thing I do on a lubuntu install is sudo apt-get synaptic, straighten out the repositories, [COLOR="Red"]remove completely chromium so synaptic automatically installs firefox[/COLOR].  Synaptic install adobe-flashplugin and then I'm off and running. 


Huh? Something doesn't sound right here....

---

### Post by phillw on 2012-03-27
> **jerrylamos said:**
> About the first thing I do on a lubuntu install

From that list, xubuntu would be better for you? 

The other option that lubuntu could possibly support would be to be read the wiki area.

[ Change to Lubuntu ]( https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu)

Also you may like to have a look at [ Restricted DVD / Music formats](https://help.ubuntu.com/community/RestrictedFormats)

Regards,

Phill.

---

### Post by teh603 on 2012-03-28
You sure that you're using Lubuntu? I downloaded the .iso from the 22nd, and Synaptic was part of the default loadout.

---

### Post by jerrylamos on 2012-03-28
> **teh603 said:**
> You sure that you're using Lubuntu? I downloaded the .iso from the 22nd, and Synaptic was part of the default loadout.

As I remember, on lubuntu 20120325, I did do sudo apt-get install to get synaptic, and it didn't say the current version version was the latest, it just did an install.

Now I've got Beta 2 candidate lubuntu running on a thinkpad, unity-2D running on a netbook, a tower, and a wide screen notebook so maybe my memory isn't infallible.....

Anyway they're all working with a few launchpad bugs, none showstoppers.

Two annoying ones:  pcmanfm just loves to crash, even in the background doing nothing.

My fast tower has a sata and an ide.  Meerkat, Lucid, .... on in to the past have /dev/sda as the drive that boots first.

Narwhal, Ocelot, Pangolin have the boot drive as /dev/sdb and the secondary drive as /dev/sda.  Kinda screws up grub2 and install.  

Example after install the installed Grub2 looks for a UUID on the wrong drive and never finds it, absolutely refuses to look at the other drive.  So I boot up Lucid and run grub2 update and install /dev/sda to straighten things out.

Yes there's a launchpad bug and no development is not interested.

Jerry

---

### Post by phillw on 2012-03-28
> **jerrylamos said:**
> 
Yes there's a launchpad bug and no development is not interested.

Jerry

There is a release for grub2 held in the queue because we are on feature freeze for the beta 2. It is for a problem where grub is not seeing all the OS's installed. 

Regards,

Phill.

---

### Post by nm_geo on 2012-03-28
> **teh603 said:**
> You sure that you're using Lubuntu? I downloaded the .iso from the 22nd, and Synaptic was part of the default loadout.

I think Jerry was installing a min.iso when he needed to install synaptic.  It is always installed on Desktop or Alternate installs in Lubuntu, but on a mini-iso build with the lubuntu-core it is typically the first thing we install even before lubuntu-desktop. That might have been the issue ~ If my Memory is not falling me ~

---

### Post by teh603 on 2012-03-28
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/967132](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/967132)

modemmanager wasn't part of the default loadout, so I had to manually install it for my USB cell modem to work. Here's the bug, please add yourself to it if you've had trouble getting your 3G connections working.

I'm also having issues with pcmanfm crashing.

On the issue of where to install GRUB, you used to be able to force the installer to install it on /dev/sda. Course that was back in the days of Intrepid and Jaunty, and eeePC 701s that had to boot Ubuntu off the SD card slot because the internal SSD was only 2 gigs and non- replaceable. Dunno if you still can; I haven't had the issues with GRUB going into the wrong place like I did back then.

---

### Post by ventrical on 2012-03-28
> **jerrylamos said:**
> As I remember, on lubuntu 20120325, I did do sudo apt-get install to get synaptic, and it didn't say the current version version was the latest, it just did an install.

Now I've got Beta 2 candidate lubuntu running on a thinkpad, unity-2D running on a netbook, a tower, and a wide screen notebook so maybe my memory isn't infallible.....

Anyway they're all working with a few launchpad bugs, none showstoppers.

Two annoying ones:  pcmanfm just loves to crash, even in the background doing nothing.

My fast tower has a sata and an ide.  Meerkat, Lucid, .... on in to the past have /dev/sda as the drive that boots first.

Narwhal, Ocelot, Pangolin have the boot drive as /dev/sdb and the secondary drive as /dev/sda.  Kinda screws up grub2 and install.  

Example after install the installed Grub2 looks for a UUID on the wrong drive and never finds it, absolutely refuses to look at the other drive.  So I boot up Lucid and run grub2 update and install /dev/sda to straighten things out.

Yes there's a launchpad bug and no development is not interested.

Jerry

Your right. That ISO does not have the version of synaptic that has the search dialog box and so you have to sudo apt-get install (or upgrade in ternimal I think) to get the latest version .

---

### Post by jerrylamos on 2012-03-28
> **ventrical said:**
> Your right. That ISO does not have the version of synaptic that has the search dialog box and so you have to sudo apt-get install (or upgrade in ternimal I think) to get the latest version .
Key to me, synaptic still works.

Jerry

---

### Post by phillw on 2012-03-28
> **teh603 said:**
> [https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/967132](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/967132)

modemmanager wasn't part of the default loadout, so I had to manually install it for my USB cell modem to work. Here's the bug, please add yourself to it if you've had trouble getting your 3G connections working.



It was an OOps, modemmanager has been added back, even the boss does not know how it got dropped... maybe we are working him too hard.

Regards,

Phill.

---

### Post by phillw on 2012-03-28
> **ventrical said:**
> Your right. That ISO does not have the version of synaptic that has the search dialog box and so you have to sudo apt-get install (or upgrade in ternimal I think) to get the latest version .

By default, lubuntu does NOT include that part of synaptic as it cripples low spec computers. It is NOT a bug, but a design feature.

Regards,

Phill.

---

### Post by DogMatix on 2012-03-28
After further investigation. I'd like to add that I'm not so keen on the 'Lubuntu Netbook' session. I know aesthetics need to be compromised for usability with lightweight distro's but I found the netbook interface very basic. Also, as a netbook user of Lubuntu I think I missed the point. I'm not sure if its intended for (future) touch-screen devices or for (retro) older netbooks with tiny screens? Certainly in my opinion the default Lubuntu desktop is a preferable option on a 10" Acer One 1GB RAM (circa. 2007).
 
Is 'Lubuntu netbook' still LXDE? or is it something else?

---

### Post by teh603 on 2012-03-28
> **DogMatix said:**
> After further investigation. I'd like to add that I'm not so keen on the 'Lubuntu Netbook' session. I know aesthetics need to be compromised for usability with lightweight distro's but I found the netbook interface very basic. Also, as a netbook user of Lubuntu I think I missed the point. I'm not sure if its intended for (future) touch-screen devices or for (retro) older netbooks with tiny screens? Certainly in my opinion the default Lubuntu desktop is a preferable option on a 10" Acer One 1GB RAM (circa. 2007).
 
Is 'Lubuntu netbook' still LXDE? or is it something else?I didn't know there was such a thing. A modern netbook should be able to handle KDE's Plasma Netbook or Desktop interface, though, so it might be out of Lubuntu's target audience.

---

### Post by loukingjr on 2012-03-29
I just installed Lubuntu 12.04 beta 2 in VirtualBox as a guest and everything seems okay so far except Lubuntu Software Center won't launch. The error...
```
louis@louis-VirtualBox:~$ lubuntu-software-center
Opening config file
Opening config file
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 35, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 679, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 49, in __init__
    self.ui = UI.Gui(self.on_selected_category, threadingops.get_categories())
  File "/usr/lib/python2.7/dist-packages/LSC/UI.py", line 71, in __init__
    self.pages = pages.Pages(categories_func)
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/pages.py", line 44, in __init__
    self.appsinfo = appsinfo.InfoBox()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 39, in __init__
    self.screendesc = ScreenDesc()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 97, in __init__
    self.details = Details()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 148, in __init__
    self.arrow = Gtk.Arrow()
TypeError: __init__() takes exactly 3 arguments (1 given
```

---

### Post by jerrylamos on 2012-03-29
> **ventrical said:**
> Your right. That ISO does not have the version of synaptic that has the search dialog box and so you have to sudo apt-get install (or upgrade in ternimal I think) to get the latest version .

At least as of Beta 2 20120328 lubuntu has a full synaptic.  I use it to remove completely chromium.  Synaptic automatically loads Firefox which takes up less disk space if that matters.  I find Firefox handling of a couple hundred bookmarks easier for me than with chromium.

ubuntu does not come with synaptic. I use synaptic to set repositories, install adobe-flashplugin, etc. etc. 

As I remember from months (years) ago update manager had an ability to set repositories, but I stay as far away as I can from update mangler.

A few weeks ago there was a choice on system settings to set repositories but I haven't found it lately.

I did use apt-get install adobe-flashplugin on one of my installs.

Jerry

---

### Post by compuguy1088 on 2012-03-29
> **DogMatix said:**
> After further investigation. I'd like to add that I'm not so keen on the 'Lubuntu Netbook' session. I know aesthetics need to be compromised for usability with lightweight distro's but I found the netbook interface very basic. Also, as a netbook user of Lubuntu I think I missed the point. I'm not sure if its intended for (future) touch-screen devices or for (retro) older netbooks with tiny screens? Certainly in my opinion the default Lubuntu desktop is a preferable option on a 10" Acer One 1GB RAM (circa. 2007).
 
Is 'Lubuntu netbook' still LXDE? or is it something else?

Works fine for me. Far more snappier than stock Ubuntu on my HP mini 110.

---

### Post by kansasnoob on 2012-03-30
Could we possibly merge this with:

[http://ubuntuforums.org/showthread.php?t=1888933](http://ubuntuforums.org/showthread.php?t=1888933)

Does that make sense?

I have a testing request, or more specifically Lubuntu's lead developer has a request:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21)

Remember that using packages from a PPA can break your OS, possibly requiring re-installation, but so far it's good on my end :)

---

### Post by ventrical on 2012-03-30
> **phillw said:**
> By default, lubuntu does NOT include that part of synaptic as it cripples low spec computers. It is NOT a bug, but a design feature.

Regards,

Phill.

I stand corrected.

---

### Post by ventrical on 2012-03-30
> **jerrylamos said:**
> At least as of Beta 2 20120328 lubuntu has a full synaptic.  I use it to remove completely chromium.  Synaptic automatically loads Firefox which takes up less disk space if that matters.  I find Firefox handling of a couple hundred bookmarks easier for me than with chromium.

ubuntu does not come with synaptic. I use synaptic to set repositories, install adobe-flashplugin, etc. etc. 

As I remember from months (years) ago update manager had an ability to set repositories, but I stay as far away as I can from update mangler.

A few weeks ago there was a choice on system settings to set repositories but I haven't found it lately.

I did use apt-get install adobe-flashplugin on one of my installs.

Jerry

  Yes.. I just tried that .. a very unique little  workaround with firefox replacement of Chrome.  I tried Chrome but it just doesn't work for me..

  I'll keep an eye on the 'mangler' too :)

*edit*

For the most part  the Update Manager has worked extremely well except on only a few occasions and most of those fails were due to something I did or did not do.

---

### Post by cesera on 2012-04-02
I am presuming this is thread is for reporting Lubuntu Beta 2 issues, if not, please let me know and I'll post it somewhere else.  I seem to have run into an issue with sudo. I have added the following line to sudoers (using "sudo visudo"), but I still get prompted for a sudo password when using truecrypt. ```
userid    ALL=(ALL) NOPASSWD: /usr/bin/truecrypt, /sbin/fsck -a
```I there is security implications and things with that line, but the issue is that is should allow me to run truecrypt and fsck -a without typing in my password and it doesn't seem to work.

---

### Post by kansasnoob on 2012-04-02
> **cesera said:**
> I am presuming this is thread is for reporting Lubuntu Beta 2 issues, if not, please let me know and I'll post it somewhere else.  I seem to have run into an issue with sudo. I have added the following line to sudoers (using "sudo visudo"), but I still get prompted for a sudo password when using truecrypt. ```
userid    ALL=(ALL) NOPASSWD: /usr/bin/truecrypt, /sbin/fsck -a
```I there is security implications and things with that line, but the issue is that is should allow me to run truecrypt and fsck -a without typing in my password and it doesn't seem to work.

I think you'd get better results posting here:

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)

The OP, amjjawad, has been really good about seeking out help when none of us have an answer.

Personally I'm clueless. I haven't messed with sudoers in a very long time, the last time I did was when I was still using Firestarter as a firewall front-end.

---

### Post by cariboo on 2012-04-02
> **cesera said:**
> I am presuming this is thread is for reporting Lubuntu Beta 2 issues, if not, please let me know and I'll post it somewhere else.  I seem to have run into an issue with sudo. I have added the following line to sudoers (using "sudo visudo"), but I still get prompted for a sudo password when using truecrypt. ```
userid    ALL=(ALL) NOPASSWD: /usr/bin/truecrypt, /sbin/fsck -a
```I there is security implications and things with that line, but the issue is that is should allow me to run truecrypt and fsck -a without typing in my password and it doesn't seem to work.

You may be better off posting your question in the [Security Discussion]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum, as these type of problems are dealt with there all the time.

It may be wise to add a note to the bottom of your post, that it was suggested you start a thread there, because if not, your thread may end up back here again. :)

---

### Post by loukingjr on 2012-04-03
I posted this in another Lubuntu thread without much luck so I thought I would try here. When I first installed Lubuntu 12.04 beta2 I also installed xcompmgr for a little eye candy. It was working normally until updating a few days ago and now shadows stopped working. I read xcompmgr is no longer being developed so one, I was wondering if it can be fixed, or two, is there some other comp manager that will work with Lubuntu 12.04?

thanks.

---

### Post by andrewabc on 2012-04-03
> **jerrylamos said:**
> Just did a clean quick successful lubuntu 20120325 Beta 2 candidate (zsync'd from daily build).

Everything working except sound.  pcmanfm hasn't even crashed yet.

Of my 4 test pc's, sound only works on one of them.  Yes there's a launchpad bug.  

Well, on lubuntu, everything else I've tried O.K. so far, except a whole lot more responsive and crisp than "ubuntu".

Jerry

Tried lubuntu beta2 on my e-350 nettop.
No sound at all. Not even icon at bottom right.
Any idea what files were needed to update to get sound working?
I don't want to install all updates since my usb stick is only 2gb and not much free space.

I tried searching for "sound" in synaptic, but no files to update.

---

