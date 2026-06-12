---
title: "White Darter 7.10 (gutsy) install"
date: 2007-10-21
forum: System76 Support
---

### Post by riseringseeker on 2007-10-21
OK, since I had my darter I've tweaked and modified, so when it came to installing 7.10 I decided to do a clean install rather than an upgrade.

Things went fast, though honestly I wish the install had a few more options - maybe an "Advanced User" button to click to allow a little more customization - but that's beside the point.

Make a long story short, I run ubuntu and have KDE installed on top.  I much prefer the configuration methods in KDE, as well as a few of the other features - the ability to quickly change displayed time zones, and konqueror is not only the best little ftp tool around, but is the only browser other than IE that can tackle the crappy web pages my employer has.

OK, so overall I am impressed with 7.10, Skype worked better than ever - even automagically using the front mike or the headset without making any changes.  (Though now it doesn't, but will work with whichever mike I manually choose)

The problems I am having are only three (so far), but two I feel are more than minor annoyances.

First, from time to time, with no apparent reason an application will "freeze", and "go grey" - much like the entire screen does when you start an administrative task and it asks for your password, only in this case it is only the one app that does so.  I have the clock showing seconds, and it never stops, and I can choose and use other apps while the greyed out one sits and thinks.  

I have noticed this most with pidgin, kopete and skype, though firefox has done it as well.  I'll try leaving the IM programs off for a bit, as I have noticed it worst with them.  I have had the system monitor up to watch the CPU usage, and honestly 7.10 seems to eat a little more than 7.06 did.  Right now firefox, the only running app just greyed out on me.  I kept typing, and when it came back, all the text I had type flowed in, but it still is at least annoying as hell!

Tom, Carl, or anyone, if you can help me out with this, would much appreciate it.  Been making Linux converts regularly with this, but the greying out would be a show stopper for most if not all folks/

The other problem I am having, and since you don't install it, not sure you can help.  Under KDE it will not automount a USB device.  I googled around and it looks like it may indeed be a bug.  I also looked at udev.conf and found only one uncommented line - which I strongly suspect to be the problem.  The uncommented line is:

```
udev_log="err"
```

Lastly, I have one other thing.  When I boot, there is about a 15 second delay from the time the startup music (desktop startup) and the desktop itself actually loading.  In the meantime I am looking at just a tan screen - though it does blink twice, or perhaps three times during that.  Once it never did come out of  a tan screen and ended up shutting it down with the power button, but so far only the once.

If there is any more information I can give that will help solve this, please just ask!

---

### Post by perce on 2007-10-22
I installed Gutsy on Friday on a white Darter. I can confirm about the gray applications. To me also some application (usually Realplayer and Network manager) sometime start eating a lot of the CPU and make the computer going to almost 60C.

I don't confirm the problem with USB devices: I've just plugged my MP3  
player and it was automounted correctly. Maybe is it a KDE issue? I'm using Gnome.

---

### Post by riseringseeker on 2007-10-22
> **perce said:**
> I installed Gutsy on Friday on a white Darter. I can confirm about the gray applications. To me also some application (usually Realplayer and Network manager) sometime start eating a lot of the CPU and make the computer going to almost 60C.

I don't confirm the problem with USB devices: I've just plugged my MP3  
player and it was automounted correctly. Maybe is it a KDE issue? I'm using Gnome.

Automount works fine under gnome.  I do believe **that** problem is KDE related, but the greying out of apps and the long delay after the Desktop should come up before it does concerns me.

---

### Post by thomasaaron on 2007-10-22
Before digging too deeply into the graying problem, have both of you done the firmware update for the cd drive?

If not, that caused little freezing spells. They were not exactly like what you guys are describing, but they are close enough to make me wonder if the problem doesn't manifest itself a little differently under Gutsy.

I've also heard that the graying might be a side-effect of running compiz. Try turning off your Desktop effects and seeing if it still happens.

---

### Post by riseringseeker on 2007-10-22
> **thomasaaron said:**
> Before digging too deeply into the graying problem, have both of you done the firmware update for the cd drive?

What firmware update?  I have the latest system76 drivers installed, something else I need to do?

> If not, that caused little freezing spells. They were not exactly like what you guys are describing, but they are close enough to make me wonder if the problem doesn't manifest itself a little differently under Gutsy.

I've also heard that the graying might be a side-effect of running compiz. Try turning off your Desktop effects and seeing if it still happens.

Will give that a shot.

---

### Post by greg_g on 2007-10-22
The graying is a part of compiz, it is basically saying "HEY! don't click on this app, it is working dang hard right now just to catch up"  I get that sometimes with Synaptic when I do a search.  And FF is some script on the pages doesn't want to stop.

---

### Post by riseringseeker on 2007-10-22
> **greg_g said:**
> The graying is a part of compiz, it is basically saying "HEY! don't click on this app, it is working dang hard right now just to catch up"  I get that sometimes with Synaptic when I do a search.  And FF is some script on the pages doesn't want to stop.

Well, that pretty much sucks, but have turned off visual effects, we'll see what happens.  Whenever Tom slips back in here, I'll find out about the firmware update.

I'll also try to boot to KDE and see if any of the updates I just installed help at all.

---

### Post by thomasaaron on 2007-10-22
This is the firmware update I was talking about. If you've not done it you probably should.

[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

NOTE TO DARU2 USERS: This was from the Daru1 only (the white one).

---

### Post by riseringseeker on 2007-10-22
> **thomasaaron said:**
> This is the firmware update I was talking about. If you've not done it you probably should.

[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

NOTE TO DARU2 USERS: This was from the Daru1 only (the white one).

TWO(!) pen drives??  I guess I was going to get another one anyway - want to have ubuntu on a stick.

---

### Post by perce on 2007-10-22
> **thomasaaron said:**
> Before digging too deeply into the graying problem, have both of you done the firmware update for the cd drive?


Yes I have. 

Also the symptoms here are very different from what happens before the firmware upgrade: it is just the grayed application that becomes irresponsive, while before the firmware upgrade it was the whole system, and I had no other choice but reboot.

---

### Post by riseringseeker on 2007-10-22
> **thomasaaron said:**
> This is the firmware update I was talking about. If you've not done it you probably should.

[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

NOTE TO DARU2 USERS: This was from the Daru1 only (the white one).

After our phone conversation, I finally got ["Ultimate Bootable CD]("http://ubcd.sourceforge.net/download.html")" and went from there.  The update looked familiar, and I **think** I had done it before, though I don't recall having to use 2 jump drives, but could have been.

I assume that installing it again won't hurt anything...

I still think I am going to reinstall, as like I said on the phone, I wonder if a couple of the problems were installing kubuntu-desktop, uninstalling that then putting in KDE.  A reinstall will tell me I suppose.

---

### Post by thomasaaron on 2007-10-23
Re-flashing the firmware (if indeed you did) won't hurt anything.

---

### Post by Rotarychainsaw on 2007-10-23
I dont have any pen drives :( Is there a way to turn all that into a bootable CD or something? I bet there is, I just don't want to do the legwork haha.

edity - after a quick search, it looks really easy if I can find a way to add the 2 files to one of the dos bootdisk ISOs out there.

edit - uh oh, Making the disk worked, it booted into dr-dos and I ran the program. It said it completed and I should reboot. Now the cd drive doesnt do anything. I can't even make it eject when I push the button. Does the 305 bios need to be used with this firmware?

---

### Post by thomasaaron on 2007-10-23
No, the 305 bios has nothing to do with it. Use a paperclip to open your drive. Hopefully that didn't hose the firmware for the drive.

The best bet, if it doesn't work is to (pray and) try to re-flash the firmware again with two usb sticks. Or one bootable cd containing freedos and one pen drive containing the files.
I'm not sure how to add the firmware files to the cd.

---

### Post by Rotarychainsaw on 2007-10-23
Figure a new post will get some views too. 

The cd drive is in the HAL. Hmmm, Now I cant use the CD drive to update the bios either (put them both on the same cd). I see there is a bios flashing utility built into the darter. I guess A: is only a floppy that we don't have?

edit - I posted before I saw your post. I'll have to do the usb way since the drive doesn't read bootable cd's anymore. Investigating. . . 
edit - well 2 usb drives are in the mail. I'll have to try it properly in a week I guess. I was really hoping the BootCD way would work since its so much easier lol.

---

### Post by thomasaaron on 2007-10-23
I'm not trying to mince words, here. I just want to add this for clarification.
I'm not sure where flashing the bios came into play. The bios resides on the motherboard, and it is not a good idea to flash it unless you are certain that you actually need to do so.

We are talking here about flashing the firmware for the cd drive, which resides on the cd drive. This is the problem that is causing the freezing.

---

### Post by Rotarychainsaw on 2007-10-23
Oh I know, I was just planning to update the bios to fix the brightness keys. I was thinking maybe the new firmware reports something different that the older bios can't handle, but that's obviously not the case. It shows up in the bios and all that, it just doesn't do anything.

---

### Post by riseringseeker on 2007-10-23
> **thomasaaron said:**
> Re-flashing the firmware (if indeed you did) won't hurt anything.

Good, as I am pretty sure I did.  Seems to me I have done two low level upgrades to the Darter - the BIOS, and the firmware.

Well, as I mentioned on the phone, I also re-reinstalled ubuntu.  The greying reappeared almost at once, but turning off compiz seemed to get rid of it - we'll see as I keep using this now.  I guess compiz-fusion isn't quite ready for prime time yet - too bad, it looks good, but I can't have the apps slowing/freezing like that.

The booting seems a little faster now, no long long wait from the end of the music to a usable desktop.

I am still trying to find info on the lack of automounting when I run a KDE session.  I have **got** to think it's related to the lack of any meaningful entries in udev.conf.  The total extent of udev.conf is:

```
# udev.conf

# The initial syslog(3) priority: "err", "info", "debug" or its
# numerical equivalent. For runtime debugging, the daemons internal
# state can be changed with: "udevcontrol log_priority=<value>".
udev_log="err"

```

---

### Post by greg_g on 2007-10-23
> **riseringseeker said:**
> The greying reappeared almost at once, but turning off compiz seemed to get rid of it - we'll see as I keep using this now.  I guess compiz-fusion isn't quite ready for prime time yet - too bad, it looks good, but I can't have the apps slowing/freezing like that.


Just curious about that; From my experience with the greying of applications, it is basically that this app is unresponsive because IT is doing something.  Like when firefox gets hung up on a script or whatever.  

Are you replicating the cause in both compiz-enabled and compiz-disabled?  When not using compiz is the application unresponsive, or partially unresponsive?  

What I am getting at is I don't think compiz is the "cause" of the greying, it is just greying to show unresponsiveness.

I could be wrong though, that is just what I assumed when it happened to me when firefox greyed out.  Then it happened in Synaptic (searching for a keyword) but it popped right back up when the search was done

In fact, I just tested Synaptic.  I searched for "test" and it was searching (I saw the harddrive access applet on my panel spike) and then greyed out after ~5 seconds, but it was only grey for ~1 second as the search finished then.

----
EDIT:
Also, Deluge just did greyed, and it was Deluge's "fault."  I had it remove a torrent and delete the downloaded files, there were 1.2 gigs worth, so as it was deleting those, it was unresponsive, and it greyed (I even got the "Deluge is not responding, do you want to wait or force quit" for a second.

So, the greying, not a fault of Compiz.  In fact, I see it as a plus.  It is letting you know not to mess with the app, it is busy doing something else.

---

### Post by riseringseeker on 2007-10-24
> **greg_g said:**
> Just curious about that; From my experience with the greying of applications, it is basically that this app is unresponsive because IT is doing something.  Like when firefox gets hung up on a script or whatever.  

Are you replicating the cause in both compiz-enabled and compiz-disabled?  When not using compiz is the application unresponsive, or partially unresponsive?  

Not that I can tell, but then again, how can I tell.  There are times when FF takes quite some time to open a particular page, sometimes even ones that shouldn't.  With CF enabled I get greying **sometimes** when this happens, but not others.

Also running pidgin it will sometimes dim/grey when I am not doing anything with it with CF enabled - IOW it's just sitting behind another app.  It may very well be it's polling the server or something, but if it's unresponsive I wouldn't know it if CF was turned off and be able to try to have it do anything.

> What I am getting at is I don't think compiz is the "cause" of the greying, it is just greying to show unresponsiveness.

I see what you are trying to say here, though it's a matter of semantics.  CF **causes** the greying, but perhaps for a valid reason.

> I could be wrong though, that is just what I assumed when it happened to me when firefox greyed out.  Then it happened in Synaptic (searching for a keyword) but it popped right back up when the search was done

In fact, I just tested Synaptic.  I searched for "test" and it was searching (I saw the harddrive access applet on my panel spike) and then greyed out after ~5 seconds, but it was only grey for ~1 second as the search finished then.

----
EDIT:
Also, Deluge just did greyed, and it was Deluge's "fault."  I had it remove a torrent and delete the downloaded files, there were 1.2 gigs worth, so as it was deleting those, it was unresponsive, and it greyed (I even got the "Deluge is not responding, do you want to wait or force quit" for a second.

So, the greying, not a fault of Compiz.  In fact, I see it as a plus.  It is letting you know not to mess with the app, it is busy doing something else.

Another problem popped up this morning.  I used it off of AC power for the first time, and it dimmed down after about a minute to where it was difficult to see.  Tried setting the power management to not dim at all on DC power, but it didn't seem to take until after a reboot.  Seems to be working properly OK after a reboot though.

---

### Post by riseringseeker on 2007-11-01
Wanted to update this thread.  I have compiz running with lots of bells and whistles now, and the greying seems to have abated quite a bit.  

Also, I was able to get usb drives to automount under KDE.  All I had to do was put a stick in, then pull it out and put it back in.  I used a stick with nothing on it, so didn't risk loosing any data.  This mounted the stick and put the icon on my desktop.  I went to "Properties", and unclicked mount as user.  I can now plug in any USB device and it automounts now.

---

### Post by perce on 2007-11-01
> **riseringseeker said:**
>   I used a stick with nothing on it, so didn't risk loosing any data. 

You probably don't risk loosing any data removing the stick, if it wasn't mounted.

---

### Post by Rotarychainsaw on 2007-11-03
I'd also like to update my separate subthread lol. I got my usb sticks and did it right, now my cd drive works again. I guess following directions pays off sometimes.

---

### Post by riseringseeker on 2007-11-04
> **perce said:**
> You probably don't risk loosing any data removing the stick, if it wasn't mounted.

The way it worked wasn't 100% sure it was not mounted (System saw it when I plugged it in, just didn't display it).  Why take the chance?

---

