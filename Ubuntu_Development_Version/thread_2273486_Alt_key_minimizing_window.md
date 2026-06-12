---
title: "Alt key minimizing window"
date: 2015-04-13
forum: Ubuntu Development Version
---

### Post by Speedwagon on 2015-04-13
Testing out 15.04 beta 2. While using steam to play Dota2, hitting alt will minimize the game and put me at the desktop. This has never happened before 15.04. Bug,  feature? Very annoying behavior though.

---

### Post by mbott on 2015-04-13
Mine is working as defined.

-- 
Mike

---

### Post by Speedwagon on 2015-04-13
That's seems to be what it is doing. But 14.04 and prior(I opted not to go to 14.10) have never done this to me. I've never tried using Alt to invoke the HUD, but I play Dota2 in 14.04 without this behavior.

But now that I know what it is doing, I can change the behavior. Curious that I've never encountered this before though.

---

### Post by mbott on 2015-04-13
Interesting as the attachment above is the same for both 15.04B2 and 14.04.2 LTS ... at least on my two installations.

-- 
Mike

---

### Post by Mateusz Stachowski on 2015-04-19
> **Speedwagon said:**
> That's seems to be what it is doing. But 14.04 and prior(I opted not to go to 14.10) have never done this to me. I've never tried using Alt to invoke the HUD, but I play Dota2 in 14.04 without this behavior.

But now that I know what it is doing, I can change the behavior. Curious that I've never encountered this before though.

You didn't encountered this behavior before because there were bugs that prevented HUD and Dash from being displayed in fullscreen programs. This is now resolved in 15.04 since January 15th and it landed in 14.04 LTS as SRU (Stable Release Update) April 15th.

[https://launchpad.net/ubuntu/+source/unity/7.3.1+15.04.20150115-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/7.3.1+15.04.20150115-0ubuntu1) (15.04 package)

[https://launchpad.net/ubuntu/+source/unity/7.2.4+14.04.20150316-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/7.2.4+14.04.20150316-0ubuntu1) (14.04 LTS package published in updates 2015-04-15)

Bug #1159249 reported on 2013-03-23 - [HUD does not show up over fullscreen window]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1159249")

Bug #860970 reported on 2011-09-27 - [Dash called with super key above fullscreen app is not interactive or does not show up at all]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860970")

The HUD minimizing fullscreen games is also reported but I guess since there was that bug I linked above it wasn't on devs radar. I already checked that bug as affecting me and I suggest to you and all others affected to do the same this way it can gain higher priority.

Bug #1167453 reported byon 2013-04-10 - [Apps should have a way to disable HUD]("https://bugs.launchpad.net/hud/+bug/1167453")

---

