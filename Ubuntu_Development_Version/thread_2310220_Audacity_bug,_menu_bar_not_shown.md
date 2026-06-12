---
title: "Audacity bug, menu bar not shown"
date: 2016-01-17
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-01-17
Hello,
I write here because I'm running Audacity on 16.04 but maybe the same problem occurs on other versions.
Using audacity, I can't do almost anything because the menu bar is not shown and all the menus don't apperas.

Here a small video: [https://youtu.be/iLh90YRbo7A](https://youtu.be/iLh90YRbo7A)

As you can see, menus don't appers when I move the mouse on the menu bar.
Has anyone the same problem?

---

### Post by howefield on 2016-01-17
Dont think it is an audacity bug, rather a development version issue, try updating if you aren't already.

I had this with LibreOffice, Audacity and a couple of other programs but resolved over the last day or two.

Incidentally, invoking the hud should give you menu options, assuming it is the same issue :)

---

### Post by mc4man on 2016-01-17
I see some possible menu issues in 16.04 but they're widespread & solved with a log out/in 
( or possibly limiting data on desktop with fast booting machines.

In the case of audacity it's fine, menus are & have been in the audacity window itself, not in menu bar

---

### Post by howefield on 2016-01-17
I shouldn't have said resolved, it appeared resolved last night after an install with the latest pending daily image.

LibreOffice was fine last night, but now doesn't have the menus, either in the window or the top panel. Concur with audacity menus in the window.

---

### Post by mc4man on 2016-01-17
> **howefield said:**
> I shouldn't have said resolved, it appeared resolved last night after an install with the latest pending daily image.

LibreOffice was fine last night, but now doesn't have the menus, either in the window or the top panel. Concur with audacity menus in the window.
Curious - does a log out/in return LO menus? (they are working here in an ubuntu session

---

### Post by enricobe on 2016-01-17
Thank you for your replies.
> **howefield said:**
> Dont think it is an audacity bug, rather a development version issue, try updating if you aren't already.

I had this with LibreOffice, Audacity and a couple of other programs but resolved over the last day or two.

Incidentally, invoking the hud should give you menu options, assuming it is the same issue :)
 I've updated the system and rebooted it. Nothing is changed and Audacity still doesn't work :(

> **mc4man said:**
> I see some possible menu issues in 16.04 but they're widespread & solved with a log out/in 
( or possibly limiting data on desktop with fast booting machines.

In the case of audacity it's fine, menus are & have been in the audacity window itself, not in menu bar
Is it fine? What do you mean? Menu bar appears neither in the audacity windows nor in the Unity's top bar.

---

### Post by howefield on 2016-01-17
> **mc4man said:**
> Curious - does a log out/in return LO menus? (they are working here in an ubuntu session

Interesting, the menus appear after a log out and back in, but do not survive a reboot. Need to log out and and in again after each reboot.

---

### Post by enricobe on 2016-01-17
> **howefield said:**
> Interesting, the menus appear after a log out and back in, but do not survive a reboot. Need to log out and and in again after each reboot.

I confirm. The menus appears after a login/logout but they don't appear after a reboot

---

### Post by mc4man on 2016-01-17
I've had a bug on missing menus for a while though - 
In my case it was about 30-35% of fresh boots or restarts (- at the time I filed the bug, recently it had been increasing.
On a fresh install things seemed better until I copied over all the folders I had had on the Desktop. Then it started up again. Removing most from Desktop has *seemingly* solved but that could be an anomaly rather than reason/solution.

Bug is here - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226)

---

### Post by howefield on 2016-01-17
Thanks for the bug link, added "affects me too"

---

### Post by mc4man on 2016-01-17
For those affected - on a  restart > no menus does dmesg |tail report any zeitgeist error/warning?
What one could try is deleting ~/.local/share/zeitgeist folder, then do an immediate restart, might improve situation, at least for a bit.
(could also lead to some restarts hanging though if so that will stop after a while...

Edit: actually i'd try deleting everything in ~/.local except the trash folder

---

### Post by enricobe on 2016-01-17
Should I add the "affects me", too? I can't understand if your bug is the same that I've seen on audacity and reported here.

I don't have a lot of icons on the desktop (5-6 icons) but I've restored my /home backup of 15.10 after the fresh install so this is not a "pure" fresh install.

---

### Post by howefield on 2016-01-17
No zeitgeist errors/warnings at all for me.

Of the common programs I use, 
Apps with menus : vlc, keepassx, synaptic (only in app window) audacity (only in app window).
Apps without menus : gedit, gimp, gpodder, libreoffice, terminal, calculator, inkscape, files.

Edit: and no relief following a reboot after deleting the zeitgeist folder.

---

### Post by enricobe on 2016-01-17
I have no zeitgeist related errors/warings too (dmesg |tail).

---

### Post by howefield on 2016-01-17
> **mc4man said:**
> Edit: actually i'd try deleting everything in ~/.local except the trash folder

Didn't see that edit initially but that seems to helped with the exception of audacity and synaptic menus shown in the program window, I'll try a few reboots later.

> **enricobe said:**
> Should I add the "affects me", too? I can't understand if your bug is the same that I've seen on audacity and reported here.

The bug relates to 16.04 and you stated you were using 16.04 so.. sounds like it affects you too :)

---

### Post by mc4man on 2016-01-17
At least here checking back with 14.04 both synaptic & audacity only have menus in app window. 

As far as bug - very mysterious. It seems that once it starts on an install it keeps coming back. Hopefully it just 'solves' itself as there is no logging showing an issue anywhere.
(- I have a new very small 16.04 install where it wasn't happening at all. Then copied over the zeitgeist folder from my other install & that set it off.
Deleting everything in ~/.local/share except trash 'fixed', at least for the moment.

On my main install it happened all the time until I removed the bulk of folders on the Desktop, hasn't returned in days. (net of those folders was about 125,000 files.

In other words - currently makes no sense...

Thinking back the zeitgeist error was at bottom of syslog... "WARNING **: Unable to get info on application://nautilus-autostart.desktop" which only showed in syslog when logging into a session with missing menus. Could be more of a result of rather than cause of missing menus.

---

