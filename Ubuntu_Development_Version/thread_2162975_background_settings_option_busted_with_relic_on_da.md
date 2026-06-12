---
title: "background settings option busted with relic on daily-live-i386"
date: 2013-07-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-07-16
Zsyncing the daily-live saucy-desktop-i386.iso then booting into live session and desktop backgrounds from right click will not work.   Will show screen from <system settings> pulldown menu but will not give any other options , plus, there is a widget relic on the screen.

---

### Post by ventrical on 2013-07-16
No difference with todays <live-daily> -1/2 hour ago-  zsync.

Choosing 'appearance' option from the <system settings> produced from the <system settings> icon on the Unity Panel will work.

---

### Post by ventrical on 2013-07-16
This problem not apparent after full install on hdd.

---

### Post by jbicha on 2013-07-16
Yeah, I do see that the Background panel in System Settings is acting a bit weird here too in GNOME, although the problems I see are a  bit different on my computer.

Please file a bug against gnome-control-center.

---

### Post by mc4man on 2013-07-17
From what you've posted it sounds like nautilus is doing so, (you can r. click on Desktop, 2 default Desktops icons are visible), though I'm not exactly clear if you actually  are?

Only asking because  when created with S-d-c & doing a normal boot up to the menu > Try, ect., nautilus won't be handling the Desktop & the appearances panel will be the gnome one. ( the one you show in screen is gnome's, ie - Background

Sdc > normal boot > nautilus not handling the Desktop is an ongoing bug for some time [lpbug]1170483[/lpbug]

( A non normal boot that would not see the above would be to go to the alt. menu, -  as soon as boot starts hit any key, ect.

---

### Post by ventrical on 2013-07-17
> **mc4man said:**
> From what you've posted it sounds like nautilus is doing so, (you can r. click on Desktop, 2 default Desktops icons are visible), though I'm not exactly clear if you actually  are?

Only asking because  when created with S-d-c & doing a normal boot up to the menu > .

Yes , I am right clicking desktop after choosing <Try Ubuntu> from yesterdays (daily-live) saucy-desktop-i38.iso and no options at all. The previous saucy zsyncs all gave me the <right-click> (Desktop backgrounds) in working order.

 It is probably only temporary.  I just thought I would mention it.

---

### Post by mc4man on 2013-07-17
> **ventrical said:**
> Yes , I am right clicking desktop after choosing <Try Ubuntu> from yesterdays (daily-live) saucy-desktop-i38.iso and no options at all. The previous saucy zsyncs all gave me the <right-click> (Desktop backgrounds) in working order.

 It is probably only temporary.  I just thought I would mention it.
If when you get to the live session Desktop & a right click produces 'nothing', (no context menu), then nautilus isn't handling the Desktop
(and you also see no icons on the Desktop
This is the defacto default for 13.04 & 13.10 & there is no indication they've gotten any where fixing in 3+ months

If you see the 2 icons & a r. click produces a menu but the appearances panel is the no nothing gnome one, (Background, not Appearances),  Then that is something new..

---

### Post by ventrical on 2013-07-17
> **mc4man said:**
> If when you get to the live session Desktop & a right click produces 'nothing', (no context menu), then nautilus isn't handling the Desktop
(and you also see no icons on the Desktop
This is the defacto default for 13.04 & 13.10 & there is no indication they've gotten any where fixing in 3+ months


 I double checked and you are correct. This check with an .iso from a week and 1/2 ago. My mistake. My apologies for misunderstanding.


> 
If you see the 2 icons & a r. click produces a menu but the appearances panel is the no nothing gnome one, (Background, not Appearances),  Then that is something new..

 Yes .. this is what I got with yesterdays daily-live saucy-desktop-i386 in the <Try Ubuntu> session. But , as I noted, it installed apparently seamlessly.

 Again .. the first part of my declaration is an erroneous assumption on my part.  I must have been doing some other experiment on a full install (USB).

Regards..

---

### Post by mc4man on 2013-07-17
I'll have to try a new iso last was a couple of days old & only was as I described.
To note: - the issue with booting to a live session without nautilus handling the Desktop is only with S-d-c created disks & only if taking the typical boot up path (boot up & wait for the menu that has Try or Install options

Doesn't occur with unetbootin or dd disks or if using a S-d-c created disk going to the alt. menu right as boot up starts.

Overall the state of live sessions has deteriorated over the past year - one really curious change/break is the ability to log out/in in a live session.
The removal of the session option dates back quite some time, a dev (mpt) thought it unnecessary. It re-showed for one release (maybe 12.10? or 11.10, forget.
In any event doesn't matter if it's in the session indicator or not, I've found any attempt to log out in a live session to fail 
(ctrl+alt+delete 
If Ubuntu dev's can't see the value of a log out/in from the live session then I don't see any point in trying to show them why...

---

### Post by ventrical on 2013-07-18
> **mc4man said:**
> 
Overall the state of live sessions has deteriorated over the past year - one really curious change/break is the ability to log out/in in a live session.
The removal of the session option dates back quite some time, a dev (mpt) thought it unnecessary. It re-showed for one release (maybe 12.10? or 11.10, forget.
In any event doesn't matter if it's in the session indicator or not, I've found any attempt to log out in a live session to fail 
(ctrl+alt+delete 
If Ubuntu dev's can't see the value of a log out/in from the live session then I don't see any point in trying to show them why...


  I would think it would be important if one was trying to do demo for a new client, especially with 'mir' on deck and then having all those fails with the live sessions.

Your input - much appreciated.

Thanks and ,
Regards..

---

