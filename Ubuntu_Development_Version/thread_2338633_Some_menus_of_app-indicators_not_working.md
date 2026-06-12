---
title: "Some menus of app-indicators not working"
date: 2016-09-30
forum: Ubuntu Development Version
---

### Post by wgarcia on 2016-09-30
Anybody seeing this for the menus of app-indicators in 16.10? I see it for the menus of the Dropbox and HP (hplip) app-indicators. The video of the problem is here:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1629251/+attachment/4751623/+files/out.ogv](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1629251/+attachment/4751623/+files/out.ogv)

and here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1629251](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1629251)

---

### Post by P-I H on 2016-09-30
In my case it's not working for Dropbox.
Working for Psensors, System Load Indicator, Keybord, Sound, Calendar and System Settings.

I added myself to the bug report.

---

### Post by mc4man on 2016-09-30
Why wouldn't this be the affected app's issue(s) vs unity's? 
i would think app indicator support is province of the app. (& most work fine.

---

### Post by P-I H on 2016-10-01
Perhaps that's the case.
The Dropbox icon behaves different on 16.10 compared to 14.04. On 16.10 there is a graphic notification in the icon, that shows if the Dropbox archive is updating or updated.

---

### Post by oldos2er on 2016-10-01
I'm on Xubuntu, and the Dropbox icon is messed up on xfce4-panel. Added myself to the bug too.

---

### Post by mc4man on 2016-10-01
dropbox icon appears to work correctly here if it's forced to use it as a systray icon rather than an app indicator. 
Seems a bit hard to troubleshoot as it's proprietary software, maybe try the latest beta version.. ( I don't really use dp, google drive for me.
[https://www.dropboxforum.com/hc/en-us/community/posts/213303026-Beta-Build-12-3-19](https://www.dropboxforum.com/hc/en-us/community/posts/213303026-Beta-Build-12-3-19)

---

### Post by P-I H on 2016-10-02
There is a thread about this on the Dropbox forum.
[https://www.dropboxforum.com/hc/en-us/community/posts/210328003-Dropbox-menu-disappeared-on-Ubuntu-16-10?page=1#community_comment_211649386](https://www.dropboxforum.com/hc/en-us/community/posts/210328003-Dropbox-menu-disappeared-on-Ubuntu-16-10?page=1#community_comment_211649386)

---

### Post by wgarcia on 2016-10-03
I see it also for the hplip app-indicator. Since it started hapenning after the upgrade to yakkety, it looks to me as something related to both the applicacions and some library, probably not specific of unity as it is also seen in other desktops.

---

### Post by mc4man on 2016-10-03
hplip does seem to account for LP bugs & add support for new releases  (which 16.10 is not yet)
Maybe file a bug there on hplip. 
(the current version is 2 behind - [http://hplipopensource.com/hplip-web/release_notes.html](http://hplipopensource.com/hplip-web/release_notes.html)

---

### Post by crs2k on 2016-12-03
That worked for me for Dropbox:

dropbox stop && dbus-launch dropbox start

---

