---
title: "Dock icons &quot;lost&quot; after launching"
date: 2018-09-15
forum: Ubuntu Development Version
---

### Post by ScislaC on 2018-09-15
I upgraded from 18.04.1 to Cosmic via repos on 9/14/2018 and the desktop profile in question is Unity running on Xorg.

The short version is from a clean login everything in the session appears fine. Unity's dock looks as expected with all the usual pinned application icons. However, after launching applications the expected icons change to generic icons indicating it can't find them.

[ATTACH=CONFIG]281082[/ATTACH]

Has anyone run into this? Googling and searching the forums hasn't turned up anything helpful.

Yes, I know I'm probably the last of a group who hasn't shifted to Wayland yet, but proprietary nvidia support is still needed in my case (with the bonus of I also prefer to have my burning and wobbly compiz effects).

Note: Yes, all the "missing icons" are applications that are either still running or were previously run in this current session.

---

### Post by Frogs Hair on 2018-09-15
Have you tried removing the applications and putting them back ? Use the command below to reset icons to defaults . Unity on cosmic is uncharted territory for me.

```
unity --reset-icons
```

---

### Post by ScislaC on 2018-09-15
Unfortunately it didn't help, but thank you for the suggestion!

Another observation, when Unity's launcher (or dash or whatever is the proper term) is searching for Applications it just shows the "blank page" icons in place of all proper Application icons. It's like it gets things right on the initial read while loading the desktop (icons in the dock/launcher are good when initially loading the session), but at a certain point in the process it just isn't connecting the application icons to the shortcuts correctly anymore. I do make that distinction because other categories like "Files & Folders" and "Music" are showing the right icons in those categories via the dash search but the application in the search are always "blank" in that regard. I'm not sure if it relates to a new thumbnail-service/app related change made that I saw during the upgrade, but either way, I'd like to help track it down if it's not a currently known issue. I'll take one for the team. :)

---

### Post by Yahoé on 2018-09-15
I have been experiencing the problem for a couple days. I happened to install a new machine with 18.10 and Unity today and the problem was there too. As  1 Hour Ago Frogs Hair  suggested, I did run "unity --reset-icons" which closed my Unity session, and upon logging in, my Unity launcher favorites were lost. I put them back and my icon were nearly all different. I guess the new icon theme had kicked in, but it did not fix the issue of the disappearing icons.  Logging out and back in brings the icons back, but they are replaced by the? icon as soon as I launch app.  I opened [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1792758](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1792758) please report the problem there as well.

---

### Post by mc4man on 2018-09-15
You cannot use the yaru icons in a unity session. So log into a gnome-shell session, open the tweaks app > Appearance & change to something that works like ubuntu-mono dark with Ambiance..
Don't see Unity being useful at all come 20.04 so 18.04 is likely the end of the road there.

Filing a launchpad bug is probably a waste of time as unity is not supported. Better to comment here - 
[https://community.ubuntu.com/t/testing-unity-session-in-18-10/7996/4](https://community.ubuntu.com/t/testing-unity-session-in-18-10/7996/4)

---

### Post by ScislaC on 2018-09-15
You did an amazing job of summing up my same experience, so I will go contribute to that bug report... thank you!

---

### Post by Yahoé on 2018-09-16
Thank you Doug, changing the icon theme with grnome-tweak-tool worked.  Unity is still getting some kind of support since Canonical still pushes updates.  Weeks ago when they first pushed Yaru, Unity’s theme and icons all changed as they should and all worked well for a short while, until they pushed some other update and Radiance was back, and then the icon issue appeared.

---

### Post by mc4man on 2018-09-16
Probable that your issue will return after a reboot, if so better to post in thread I linked..

---

### Post by jbicha on 2018-09-16
[A few days ago,]("https://irclogs.ubuntu.com/2018/09/14/%23ubuntu-devel.html#t13:43") we had someone  complain about some Unity icon issue that turned out to be [Debian #908705]("https://bugs.debian.org/908705") The upstream glib developer is aware of  the issue and I think there is a good chance that will be fixed in time  for the GNOME 3.30.1 release in a week.


I don't know if that's your issue or not but it should help. (I don't use Unity these days.)

---

### Post by mc4man on 2018-09-16
> **jbicha said:**
> [A few days ago,]("https://irclogs.ubuntu.com/2018/09/14/%23ubuntu-devel.html#t13:43") we had someone  complain about some Unity icon issue that turned out to be [Debian #908705]("https://bugs.debian.org/908705") The upstream glib developer is aware of  the issue and I think there is a good chance that will be fixed in time  for the GNOME 3.30.1 release in a week.


I don't know if that's your issue or not but it should help. (I don't use Unity these days.)
Would seem likely, tested by replacing Icon=single word with /path/to/icon in a .desktop, icon in launcher remains when app is opened

---

### Post by ScislaC on 2018-09-19
This has since been fixed by an updated glib2 from the proposed repo yesterday.

---

### Post by David_Lau on 2018-11-26
install tweaks tool, then show desktop icons, works every time for me

---

### Post by Frogs Hair on 2018-11-26
Not applicable to current development version. Thread Closed.

---

