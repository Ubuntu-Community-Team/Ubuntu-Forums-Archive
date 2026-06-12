---
title: "Synaptics touchpad problems"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by creosote on 2012-02-15
After an update yesterday of xserver-xorg-input-synaptic to Version: 1.5.0+git20120210-0ubuntu2, a double-click in the title bar no longer toggles maximize, a triple click no longer highlights a line, and drag-lock is on.

I see from here:
[http://www.ubuntuupdates.org/package/core/precise/main/base/xserver-xorg-input-synaptics](http://www.ubuntuupdates.org/package/core/precise/main/base/xserver-xorg-input-synaptics)
that the last two issues seem to be by design and i'm assumming so is the first.

Anyone have a line on how i can get back the previous behavior? I don't have a clickpad, just a regular old touchpad thingee and this is using gnome-shell.

Appreciate your help.

---

### Post by mc4man on 2012-02-15
> **creosote said:**
> After an update yesterday of xserver-xorg-input-synaptic to Version: 1.5.0+git20120210-0ubuntu2, a double-click in the title bar no longer toggles maximize, a triple click no longer highlights a line, and drag-lock is on.

Don't think the d. click to max & un-max has anything to do with the upgrade, could just be a breakdown, try a log out/in

As far as the other 2 the upgrade made no difference here, 3 click still highlights, drag-lock isn't enabled.

You may be able to disable the drag-lock thru synclient, the 3 click may be have to be done in source

If need be you can build the package in about 2 min.'s, with the 2 new patches not applied

---

### Post by creosote on 2012-02-16
Thanks for the response.

Did the compile without the patches and everything worked as usual.

Just for kicks i upgraded to the version with the patches fully expecting it to break and it didn't. Still fine through reboots.

Apparently a ghost peculiar to my setup.

Thanks again.

---

### Post by _oOMOo_ on 2012-02-18
Yah boo sucks another change in Precise that adversely affects me and no preference added to easily allow a return to 11.10 behaviour:

xserver-xorg-input-synaptics (1.5.0+git20120210-0ubuntu2) precise; urgency=low

  * Enable tap-and-drag locked drags by default
  * Disable three-click action by default so three touch gestures work

 -- Chase Douglas <chase.douglas@ubuntu.com>  Mon, 13 Feb 2012 20:51:56 -0800

tap-and-drag by default is a joke. Try programming in Geany with it enabled Mr. Chase Douglas.

---

### Post by balduin on 2012-02-20
> **_oOMOo_ said:**
> tap-and-drag by default is a joke. Try programming in Geany with it enabled Mr. Chase Douglas.

Yes, I don't understand this change either. I had to install [FONT="Courier New"]gpointing-device-settings[/FONT] in order to get the normal behaviour back.

---

### Post by jfernyhough on 2012-02-20
Is this why my touchpad is being crappy? Gah.

---

### Post by mc4man on 2012-02-20
Maybe there is some diff. depending on touchpad hardware?, but don't see that 3 **tap** has been prevented here on a run of the mill synaptics touchpad (dell

1,2 & 3 tap still work though 2 & 3 tap now can cause issues here so I've disabled 2 & 3 taps for the moment
3 **click** still works though not sure that was involved in the 'change' anyway.
if you're not getting 3 click I'd file a bug & see what happens

---

### Post by calanor on 2012-02-21
Yup, something is wrong with my touchpad too. Keeps on dragging and selecting stuff when I just want to move my cursor. Please remove this abomination of a default Ubuntu !!! Also guys would you please tell me how you disabled it ?

---

### Post by mc4man on 2012-02-21
> **calanor said:**
> Yup, something is wrong with my touchpad too. Keeps on dragging and selecting stuff when I just want to move my cursor. Please remove this abomination of a default Ubuntu !!! Also guys would you please tell me how you disabled it ?
see this thread
[http://ubuntuforums.org/showthread.php?t=1926751](http://ubuntuforums.org/showthread.php?t=1926751)
I've 'fixed' here for the moment as in post's 12 & 14

bug report
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770)

---

### Post by calanor on 2012-02-21
Thank you so much. Its working fine now.

---

### Post by tista on 2012-02-21
Guys...

Here seems a nice thread...
Yeah I also have some issues on touchpad driven by "synaptics" driver.

Mine?
In past, we could deal with "3 fingers tap" as "center button" of 3-button mouse, oh it's really hard to explain for ... :P For example, I often used "3 fingers tap" in web browser to open link as "new tab" and/or something like that...

But today I couldn't do that. What's happening in synaptics driver?? :(

So sorry for disturbing your discussions,
Regards,
Tista

---

### Post by mc4man on 2012-02-21
> **tista said:**
> Guys...

Here seems a nice thread...
Yeah I also have some issues on touchpad driven by "synaptics" driver.

Mine?
In past, we could deal with "3 fingers tap" as "center button" of 3-button mouse, oh it's really hard to explain for ... :P For example, I often used "3 fingers tap" in web browser to open link as "new tab" and/or something like that...

But today I couldn't do that. What's happening in synaptics driver?? :(

So sorry for disturbing your discussions,
Regards,
Tista
I'm  not really sure, something to do with touch gestures? From perspective here my touchpad only uses 1 finger so a 2 or 3 tap means 2 or 3 single  finger taps. 
In this case the change(s) have created very poor behavior if a 2 or 3 tap also involves cursor movement.
( which hopefully won't be considered user error as in - don't move the cursor 

So the fix here, while likely not 'proper' as implemented,  is effective, ie, disabling 2 & 3 single finger taps thru one of the synclient parameters
(users with single finger touchpads should not be precluded from 2 or 3 tap, intended or not

In your case maybe take a look at the diff's on launchpad for the last several package  upgrades, maybe something pops out, the changelogs are not all  that helpful by themselves.(though it may extend beyound just the xserver synaptics package?

I guess you could also look at synclient -l & see if any of the various parameters, if adjusted make any diff. to your hardware/use case

---

### Post by tista on 2012-02-21
> **mc4man said:**
> I'm  not really sure, something to do with touch gestures? From perspective here my touchpad only uses 1 finger so a 2 or 3 tap means 2 or 3 single  finger taps. 
In this case the change(s) have created very poor behavior if a 2 or 3 tap also involves cursor movement.
( which hopefully won't be considered user error as in - don't move the cursor 

So the fix here, while likely not 'proper' as implemented,  is effective, ie, disabling 2 & 3 single finger taps thru one of the synclient parameters
(users with single finger touchpads should not be precluded from 2 or 3 tap, intended or not

In your case maybe take a look at the diff's on launchpad for the last several package  upgrades, maybe something pops out, the changelogs are not all  that helpful by themselves.(though it may extend beyound just the xserver synaptics package?

I guess you could also look at synclient -l & see if any of the various parameters, if adjusted make any diff. to your hardware/use case

@mc4man,

What a nice!

"synclient TapButton3=2" did a trick for me !! :)
Really thanks for your advance...

Best Regards,
Tista

---

### Post by mc4man on 2012-02-21
> **tista said:**
> @mc4man,

What a nice!

"synclient TapButton3=2" did a trick for me !! :)
Really thanks for your advance...

Best Regards,
Tista
So just to mention though i'm sure you'd know, you can add that to a start up  so it applies each time you boot up , either gobally or locally
(I'm a single user only other than creating some test accounts at times so I add such to Startup Applications, usually with a small delay

Edit: at some point I'll probably fool around with the various parameters to see what happens, in the case of my recent 'fix', just choose the 1st. one that got the job done, albeit partially

---

### Post by ventrical on 2012-02-21
On my Acer Aspire 3620 the touchpad mouse scroller will only work one click at a time for scroll (won't scroll). have to use down-arrow key or usb mouse.

 Is this the same as bug in other thread ?

---

### Post by dummyxl on 2012-02-21
I made a bug report of this locked drag behavior.

I you affected by this, please vote for this bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934184](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934184)

thanks.

---

### Post by mc4man on 2012-02-21
> **dummyxl said:**
> I made a bug report of this locked drag behavior.

I you affected by this, please vote for this bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934184](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934184)

thanks.If you run this does it improve?

```
synclient LockedDrags=0
```

---

### Post by dummyxl on 2012-02-21
> **mc4man said:**
> If you run this does it improve?

```
synclient LockedDrags=0
```


This works, how can i make this permanent on login?
ps. there is a new bug report this one is for collating feedback.
So vote for this one instead.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770)

---

### Post by mc4man on 2012-02-21
> **dummyxl said:**
> This works, how can i make this permanent on login?
ps. there is a new bug report this one is for collating feedback.
So vote for this one instead.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770)
```

gedit ~/.config/autostart/synclient.desktop
```


```
[Desktop Entry]
Type=Application
Exec=synclient LockedDrags=0
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=5
Name=No locked drag
```
Then it'll run on every login

As far as the other bug - I filed it & am trying to make a case against the current implementation (right or wrong ? I don't like it

---

### Post by mc4man on 2012-02-21
This bug will act as feedback for a bit. If you don't like the new behavior then clicking on the 'This affects me' link will act as a vote against as currently implemented.
**Comments aren't particularly needed** & could be counterproductive unless you have a solution other than the obvious ones
. Odds are it's going to be kept unless a fair number vote against, so if it's a concern the take the opportunity

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770)

Edit: just to note: there are at least 3 issues here, maybe more depending on hardware/use case. It's not just about LockedDrags, at least from my perspective..

---

### Post by dummyxl on 2012-02-21
thank you for the fast reply;

It's fine when this new behavior can be enabled in the mouse settings but not by default I think.
I don't understand why they change this behavior and not provide a user option to revert the change. That makes absolutely no sens to me. 

On new users it can be confusing also that it "sticks" My mom for instants, she uses my laptop to see if the new Ubuntu is something for her in the near future (she don't likes windows that much) and she was troubling with moving windows and didn't understand that she has to tab again. At the time i sad that it was a bug.
 
So it confuse new people and i don't like it also. 

I think you are right, I don't like the new behavior, ](*,)
And i wonder why so few people are complaining at this time.


> As far as the other bug - I filed it & am trying to make a case against the current implementation  small world ;)

---

### Post by mc4man on 2012-02-21
When I filed that bug the stuck cursor & dead left click were happening here out of the blue. Then I saw I could do it at will though I thought a left click was also involved. 
After that it became clear it was from a simple double tap with cursor move, intended or not.

And what's also clear is this & a dead left click are unintended consequences of that particular change & maybe something else. 
Even though getting out of the stuck cursor is simple, a new double tap will do that, don't think that's the point.

May will get this without intentionally doing a 2 tap in the 1st place so the idea they'll think to then intentionally do a 2 tap makes no sense. The more likely is they'll stop moving till the time out takes affect, this is not a logical solution to this.

If they want to help out 'clickable touchpads' or whatever it is then create an option for that, not the default is there is only one way or the other.

Time will tell...

---

### Post by kaldor on 2012-02-21
I love this feature. I don't want to see it go :)

---

### Post by mc4man on 2012-02-21
> **kaldor said:**
> I love this feature. I don't want to see it go :)
It doesn't really matter one way or the other if an option is provided. So for instance here I've returned to pretty much the previous with this
```
synclient LockedDrags=0 TapButton1=1 TapButton2=3 TapButton3=2
```

Conversely if the above or thereabouts was the default you could get what is now with an appropriate similar command
If in fact it is that simple/straightforward I'd put the new behavior in a Startup App that was visible & default disabled, though the opposite would be ok

---

### Post by kaldor on 2012-02-21
On OS X you can enable or disable this feature from the Trackpad section in the preferences application. There's a checkbox called "Tap to drag" or something like that. I'd be very happy about something like that in Ubuntu.

Edit with screenshot:

[IMG]http://www.blogography.com/photos55/DragLock.jpg[/IMG]

---

### Post by Irihapeti on 2012-02-21
I don't know if it's connected with other synaptics bugs, but I've been finding that when I am moving the cursor - not dragging anything - the cursor keeps going unless I take my finger off the touchpad. Makes it very hard to click on a close box or similar small area. To me, the touchpad is almost unusable. (If I had a short temper, I think the netbook would have been thrown at something by now. :( )

I've reported it at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/937307](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/937307) So far, I appear to be the only one affected. Please add your name to "this bug affects me" if it does.

---

### Post by effenberg0x0 on 2012-02-21
@mods
We've got at least 4 Touchpad-Related open threads in the top 20 (last 6 hours). I think it's safe and more productive to merge then under the currently opened thread named[ Synaptics touchpad problems]("http://ubuntuforums.org/showthread.php?t=1925872"). It has a more generic title. 

@op
Synaptics is in fact a mess right now. Mc4man posts in the recent touchpad-related threads provide working fixes for the reported issues. Until more information, new software and/or workarounds arise I think there's not much we can do now but to use the workarounds he suggested. 

Regards,
Effenberg

---

### Post by Irihapeti on 2012-02-21
I wasn't sure whether or not to post to one of the existing threads. In some forums, that's frowned on. But if merging works best here, I'm happy with it.

My bug has been marked a duplicate, so presumably it affects at least one other person.

---

### Post by cariboo on 2012-02-21
Merged 4 similar threads.

---

### Post by dummyxl on 2012-02-22
> **mc4man said:**
> It doesn't really matter one way or the other if an option is provided. 

yes that is right. They change the behavior and not provide a descend option box inside mouse setting of Ubuntu to revert the change and i do not understand that decision.

there is however a settings box on the option program available trough the software center "Gpointing Device Settings" there is a Locked Drags option box there.
The problem with this program under Ubuntu 12.04 is that it works only one session after reboot the settings are gone .

---

### Post by dummyxl on 2012-02-24
fix released :popcorn:

---

