---
title: "Ubuntu Desktop Next 14.10 (Utopic Unicorn) Daily Build"
date: 2014-06-10
forum: Ubuntu Development Version
---

### Post by novatillasku2 on 2014-06-10
[h=1]Ubuntu Desktop Next 14.10 (Utopic Unicorn) Daily Build[/h]We have now Unity 8 daily, but don't work for me.
I try to install via usb an have an error "This image is not COM32R"
Press tab and write live and start.
User is ubuntu-desktop-next and ok, but when press enter on password says: the password is incorrect.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

---

### Post by thotz on 2014-06-11
I got a different message telling me that the desktop couldn't be loaded.

---

### Post by novatillasku2 on 2014-06-11
Don't work.I install it on my hard drive and don't start after login.

---

### Post by ventrical on 2014-06-11
[s]Total waste of bandwidth..[/s]

Not a COM32R image:

 Ok .. you have to hit the Tab key to get the menu and then type in "live" or "live-install"

  I am installing now.

  The username and password method does not work on live-usb.

---

### Post by ventrical on 2014-06-11
Ok.. I got it to work ! :)

 I hard installed it using :

```


boot: live install <enter>


```

 I ran Ubiquity and partitioned a disk and used my usual username and password.

 Then I Ctrl+Alt+F1 and was able to log on with my username and password. I then installed:

```

sudo apt-get install fvwm-crystal


```

then

```


sudo apt-get update
sudo apt-get dist-upgrade


```

Then 

```

sudo service lightdm restart


```

 and I got this huge arrow/cursor (which is probably mir working) and then my screen turned into a giant phone tablet:)bwwahahahahahah:)lol

 And is it ever fast !!

Regards...

btw .. lots of bugs..

:)

---

### Post by craig10x on 2014-06-11
Does it also work on live session? And if so, does it boot right into it or do you have to do some trick to get there?

---

### Post by ventrical on 2014-06-11
> **craig10x said:**
> Does it also work on live session? And if so, does it boot right into it or do you have to do some trick to get there?



 I can't get it to work in live session. I get lightdm/unity greeter but it will not log on (session error) when entering password (which is just the Enter key).

 Hard install works but the Browser is not working and a lot of apps are not working (like gnome-screenshot for example). Firefox too will not gome up in the apps display but a lot fo the other features work (or appear to be working on the hard install). Basically it is like a framework or backbone version of a phone tablet or ipad. Looks pretty kewl on the desktop. I would say there is a lot of work to be done to  get to a point to call it even a minimal of an example of convergence.

---

### Post by ventrical on 2014-06-11
> **novatillasku2 said:**
> **Ubuntu Desktop Next 14.10 (Utopic Unicorn) Daily Build**

We have now Unity 8 daily, but don't work for me.
I try to install via usb an have an error "This image is not COM32R"
Press tab and write live and start.
User is ubuntu-desktop-next and ok, but when press enter on password says: the password is incorrect.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)


 I did hard install and have it working after updates. It will come up in the Unity Greeter. Live session no work here either.

---

### Post by Mateusz Stachowski on 2014-06-12
> **ventrical said:**
> I can't get it to work in live session. I get lightdm/unity greeter but it will not log on (session error) when entering password (which is just the Enter key).

 Hard install works but the Browser is not working and a lot of apps are not working (like gnome-screenshot for example). Firefox too will not gome up in the apps display but a lot fo the other features work (or appear to be working on the hard install). Basically it is like a framework or backbone version of a phone tablet or ipad. Looks pretty kewl on the desktop. I would say there is a lot of work to be done to  get to a point to call it even a minimal of an example of convergence.

Currently the programs that don't have native Mir support will not run in Unity 8 Mir session because there is no support for "rootles" X under Mir. 

[https://blueprints.launchpad.net/ubuntu/+spec/client-1410-mir-rootlessx](https://blueprints.launchpad.net/ubuntu/+spec/client-1410-mir-rootlessx)

Also the Ubuntu browser will not work until [Oxide 1.1]("https://launchpad.net/oxide/+milestone/branch-1.1") is released and this is targeted for 20th June.

[#1307709]("https://bugs.launchpad.net/ubuntu/+source/unity8-desktop-session/+bug/1307709") webbrowser-app does not start in Unity 8 preview session

---

### Post by ventrical on 2014-06-12
> **Mateusz Stachowski said:**
> Currently the programs that don't have native Mir support will not run in Unity 8 Mir session because there is no support for "rootles" X under Mir. 

[https://blueprints.launchpad.net/ubuntu/+spec/client-1410-mir-rootlessx](https://blueprints.launchpad.net/ubuntu/+spec/client-1410-mir-rootlessx)

Also the Ubuntu browser will not work until [Oxide 1.1]("https://launchpad.net/oxide/+milestone/branch-1.1") is released and this is targeted for 20th June.

[#1307709]("https://bugs.launchpad.net/ubuntu/+source/unity8-desktop-session/+bug/1307709") webbrowser-app does not start in Unity 8 preview session


  Just in retrospect ,unity8 worked just fine during  Saucy and Trusty testing. The browser worked fine and so did a few other apps .

 Also .. downloading and installing the next.iso was not a complete loss as I was able to put gnome-flashback in there and get a fairly decent working desktop so as I can be able to keep on getting updates for unit8 and see how it progresses. A funny thing I noticed was that during my gnome flashback session, some of the Unity8 icons came up in the pulldown menus :)

---

### Post by Mateusz Stachowski on 2014-06-12
> **ventrical said:**
> Just in retrospect ,unity8 worked just fine during  Saucy and Trusty testing. The browser worked fine and so did a few other apps .

 Also .. downloading and installing the next.iso was not a complete loss as I was able to put gnome-flashback in there and get a fairly decent working desktop so as I can be able to keep on getting updates for unit8 and see how it progresses. A funny thing I noticed was that during my gnome flashback session, some of the Unity8 icons came up in the pulldown menus :)

You are talking about Unity 8 launched in window under Unity 7 and X. While the bug with browser not working is in Unity 8 desktop session running on Mir.

---

### Post by ventrical on 2014-06-12
> **Mateusz Stachowski said:**
> You are talking about Unity 8 launched in window under Unity 7 and X. While the bug with browser not working is in Unity 8 desktop session running on Mir.

Yes . That is exactly it. I shouldn't bring that into this discussion. I just thought it might have been helpful.

 ATM I am in a holding pattern with my current install and will wait to see how the updates go and keep an eye out here in this thread for news and fixes and other experiments, while also checking out the daily builds.

Regards..

---

### Post by Hazzabin on 2014-06-12
trying out this new Ubuntu Next
I noticed a few post back I think it was ventrical mentioned "[FONT=Ubuntu Mono, monospace][COLOR=#000000]install fvwm-crystal" can I ask why, I'm not familiar with it[/COLOR][/FONT]

---

### Post by ventrical on 2014-06-13
> **Hazzabin said:**
> trying out this new Ubuntu Next
I noticed a few post back I think it was ventrical mentioned "[FONT=Ubuntu Mono][COLOR=#000000]install fvwm-crystal" can I ask why, I'm not familiar with it[/COLOR][/FONT]

It allows you to log into another minimal desktop if unity8 is broken, so that you can update.. etc.. and run synaptic. Unity8.iso does not include a lot of what we are used to with the other flavours. I do it just as a matter of habit so that I do not have to use vim or nano.

regards..

---

### Post by Lodmot on 2014-06-13
I was able to get the live usb session to load into a desktop.
In my case, I used a 32GB flash drive as my ubuntu-desktop-next boot disk.

To get a ubuntu-desktop-next boot disk to make it to a desktop, follow these steps:


1)  When you first boot up to the login screen (LightDM), go to the  top-right where your networking icon is in the panel, and connect to  your WiFi/Ethernet connection that way.


2) Once the networking icon signifies that you're connected successfully, press CTRL+ALT+F4 to get to a terminal.


3) At the terminal, we're going to install the gnome desktop environment with this command:


sudo apt-get install gnome


This  will download and install Gnome, not onto your hard-drive, but into a  temporary storage area created from the USB/DVD boot disk (whichever one  you have). This process usually takes about 10 minutes with a decent  internet connection.


4) When gnome finally finishes installing, you're going to want to install compiz, so type this into the terminal prompt next:


sudo apt-get install compiz


Compiz is nice and small, so this usually takes like 20 seconds.


5)  After this I usually install xinit. Not entirely sure what xinit is  really for (LOL!) but every time I did this trick, xinit never screwed  things up for me. So we'll type:


sudo apt-get install xinit


6)  Finally, we're now ready to refresh LightDM so it notices the new  desktop environments. We'll do it by typing in this command:


sudo killall lightdm


This command will end the process of LightDM that's running.


7)  Now wait a second or two after the "killall" command in step 6, and the  screen will suddenly change and bring you to the LightDM login screen.  Whenever you kill the lightdm process, it seems to restart itself  automatically.


8) Finally, select a desktop environment in the  sub-menu, and login with the mentioned credentials,  "ubuntu-desktop-next" for the user name, and leave the password blank. I  know for a fact that the Gnome 3, Gnome Flashback (Compiz) and Unity 8  environments work from this procedure. In fact, this entire post was  written using the ubuntu-desktop-next boot disk. :3


A few notes:


Unity  8 in this version appears to be the same as the regular 14.04 version  of Unity, but the biggest change is that theres now a neat little  tutorial that shows you how to use Unity 8's swiping gestures. I also  noticed that the unlock screen never appeared this time around, and I  could only access the Apps scopes. When I tried to click on the web  browser icon, it gave me 3 orange rotating dots in the center of the  screen, which I never saw happen in the Unity 8 for 14.04 (though that  COULD be that I may have to update mine). But other than those few  little things, Unity 8 in ubuntu-desktop-next as of now, is the same as  the current version/tablet version.

---

### Post by grahammechanical on 2014-06-13
I must be missing something and I do not mean in the ISO image. I am prepared to test, off and on, over the next 12 months the ubuntu-desktop-next (UDN) ISO image both as a live session and an installed distribution. I do not see the point of installing this and that to make it a usable system as then it would cease to be the ubuntu-desktop-next at its present state of development.

I do not have exotic hardware but at the moment the UDN ISO image is like a motor vehicle where you can turn on the interior light but cannot start the vehicle because the ignition key is not connected to the vehicle's electrical system. But hey, it is only the second daily image. I got another 363 daily images to go. ;)

Regards.

---

### Post by Lodmot on 2014-06-13
> **grahammechanical said:**
> I must be missing something and I do not mean in the ISO image. I am prepared to test, off and on, over the next 12 months the ubuntu-desktop-next (UDN) ISO image both as a live session and an installed distribution. I do not see the point of installing this and that to make it a usable system as then it would cease to be the ubuntu-desktop-next at its present state of development.

I do not have exotic hardware but at the moment the UDN ISO image is like a motor vehicle where you can turn on the interior light but cannot start the vehicle because the ignition key is not connected to the vehicle's electrical system. But hey, it is only the second daily image. I got another 363 daily images to go. ;)

Regards.

The idea is to be able to see what Unity 8 looks like in this build. Even after just two/three days of development, there are already differences in Unity 8 in this distribution of Ubuntu that are quite interesting.

---

### Post by philinux on 2014-06-13
[http://www.omgubuntu.co.uk/2014/06/unity-8-daily-build-images-go-live?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/06/unity-8-daily-build-images-go-live?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

More info.

---

### Post by Hazzabin on 2014-06-13
Thanks mate, understand now

---

### Post by mc4man on 2014-06-13
I see that iso has 2 added sessions "unity8-x11" & "unity8-mir"
When one first tries to log in the user .dmrc is set to "Session=ubuntu", which doesn't work
But then again editing to one of the 2 new ones doesn't work either so from my perspective iso is worthless till it can log in to the expected session without any user intervention or adding additional fm's & or sessions

---

### Post by Mateusz Stachowski on 2014-06-14
> **mc4man said:**
> I see that iso has 2 added sessions "unity8-x11" & "unity8-mir"
When one first tries to log in the user .dmrc is set to "Session=ubuntu", which doesn't work
But then again editing to one of the 2 new ones doesn't work either so from my perspective iso is worthless till it can log in to the expected session without any user intervention or adding additional fm's & or sessions

The image from today (14th June) contains updated unity8-desktop-session package with fix for failing to start session.

[https://launchpad.net/ubuntu/utopic/+source/unity8-desktop-session/1.0.10+14.10.20140613-0ubuntu1](https://launchpad.net/ubuntu/utopic/+source/unity8-desktop-session/1.0.10+14.10.20140613-0ubuntu1)

> unity8-desktop-session (1.0.10+14.10.20140613-0ubuntu1) utopic; urgency=low

  [ Iain Lane ]
  * Make the sessions the default if they are installed, so that
    automatic logging in in the iso works. Use the Upstart idiomatic --
    no-wait instead of & in pre-start.

This makes it so that Unity 8 is started automatically in live mode (no login screen). You end up on Unity 8 greeter right from the start. I still can't use Unity 8 on Mir because it freezes, crashes.

---

### Post by bregma2 on 2014-06-14
> **Mateusz Stachowski said:**
> I still can't use Unity 8 on Mir because it freezes, crashes.

(1) Does Unity 8 come up at all and run for a while, then freeze/crash?

(2) Is it the shell that freezes or crashes, or apps?

(3) What video driver are you using?

(4) The logs are in $HOME/.cache/upstart if you want to poke around to try to glean more information.

---

### Post by Mateusz Stachowski on 2014-06-14
Hi Stephen nice that you took a look at forums.

Yes the Unity 8 comes up but freezes right at the greeter. I'm using Nouveau and when I tested unity8-desktop-session previously in Trusty I opened a bug report. But one of the devs commented that he is not sure if it is meant to work on Nouveau.

[https://bugs.launchpad.net/bugs/1298914](https://bugs.launchpad.net/bugs/1298914)

Anyway I tried this new image from today in VMware and it worked quite well. I didn't install it just used iso booted in live mode but eventually it become unresponsive. That happened when I was trying to install an app (2048 Native).

[Unity 8]("http://imgur.com/o6ezsdZ") running in VMware Player

---

### Post by Mateusz Stachowski on 2014-06-14
I tried running it again on real hardware but I just can't get further than the greeter.

I'm attaching logs from:

~/.cache/upstart
/var/log/lightdm

There was also unity8 crash report in /var/crash.

Looking at the unity8-mir.log it seems that it is the same problem I had in Trusty (the one from bug report). I'm thinking so because there is this:

> nouveau: kernel rejected pushbuf: Invalid argument

---

### Post by bregma2 on 2014-06-14
> **Mateusz Stachowski said:**
> 
Looking at the unity8-mir.log it seems that it is the same problem I had in Trusty (the one from bug report). I'm thinking so because there is this:

I'm going to hazard a guess an say that looks like a bug in the nouveau driver that gets revealed by the Mir compositor.  I'd suggest contacting the Mir devs (try #ubuntu-mir on freenode) about where to file a bug, they'll know more.

---

### Post by grahammechanical on 2014-06-14
In one of the UOS sessions (convergence progress I think) It was said that autologin is failing due to a bug. And when I think about it we should not be getting a login in a live session. So, the reason given makes sense to me.

---

