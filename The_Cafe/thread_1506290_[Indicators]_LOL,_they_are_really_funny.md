---
title: "[Indicators] LOL, they are really funny"
date: 2010-06-10
forum: The Cafe
---

### Post by vkontakte on 2010-06-10
Not indicators. The devs/designers are really funny. They failed to do indicator for network-manager (it creates a kind of mess together with Tomboy they are talking about notification area). So what we have now:
1) Really usefull messaging indicator
2) Relatively usable me-menu. But it's ugly as hell. It's designer really should discover what colors are. I've just uninstalled it with tons of useless stuff like gwibber.
3) Unusable applet for shutdown/reboot/etc. It's designer should also be taught what both colors and icons is. Before the education this ugly should be dropped to old good gnome-panel applet.
4) Indicator for nautilus file copying. It's the LOL: menu with the only item to open a window :mrgreen:
5) Indicators for Rhythmbox and Transmission. They just drop a possibility to raise applications windows with right click. Gave no common way to open them instead (items to perform this task are placed in different positions and named differently).
6) Network manager and Tomboy -- they make the "messy mess" ayatana guys are talking about. Because another items consistently raise on the left click, show menu on the right. They promised to make the behaviour unified. So, where is "The unified behaviour"? I only see they've reduced some very useful functionality (raise on the left click), but the "mess" is still here since they failed to do something usable with both Tomboy and Network Manager.
Oh, today they are making **very consistent** time applet, without weather report feature. :mregreen:
BTW, I like part of the things they've done. But I absolutely hate what they've done with RB, Transmission and Nautilus File Copying. I've never used right click menu, it's absolutely featureless.

The confirmation they've failed with network-manager applet is the indicator network developers ppa: they use connman instead of network manager :mrgreen:

So, the summary is they acts like an ostrich. They failed with Tomboy, failed with Network Manager. These are the only two apps from Notification Area what makes the mess, since their behavior is differs from others. But what indicator team do: they reduced functionality of apps that acts consistently and could do nothing with apps that acts inconsistently. :mrgreen:

P.S. I'm not against indicators. I'm against indicators for apps that raises main program window on left click and show menu on the right one. I like how messaging menu works, how new sound menu works. I don't care about me menu and "shutdown-reboot-etc" indicator since the first thing I do is to drop both. But I hate indicators for Rhythmbox and Tranmission, they are absolutely awful and unusable. I hope they won't touch weather/time applet, it's a way better than their time indicator.

---

### Post by zekopeko on 2010-06-10
> **vkontakte said:**
> Not indicators. The devs/designers are really funny. They failed to do indicator for network-manager (it creates a kind of mess together with Tomboy they are talking about notification area). So what we have now:
1) Really usefull messaging indicator
2) Relatively usable me-menu. But it's ugly as hell. It's designer really should discover what colors are. I've just uninstalled it with tons of useless stuff like gwibber.
3) Unusable applet for shutdown/reboot/etc. It's designer should also be taught what both colors and icons is. Before the education this ugly should be dropped to old good gnome-panel applet.

You basically didn't say anything constructive. What does "designer should also be taught what both colors and icons" mean? You do understand the icons in the menus (for most things) have been dropped? And indicators are designed to behave as close as possible to menus.

> 4) Indicator for nautilus file copying. It's the LOL: menu with the only item to open a window :mrgreen:

That was a small patch and in the future it will most likely expand to show active transfers. That indicator also behaves as it should, as a menu.

> 5) Indicators for Rhythmbox and Transmission. They just drop a possibility to raise applications windows with right click. Gave no common way to open them instead (items to perform this task are placed in different positions and named differently).

They both show an indicator and both have a "Show XYZ" option, so yes, there is a common way to access that functionality.

> 6) Network manager and Tomboy -- they make the "messy mess" ayatana guys are talking about. Because another items consistently raise on the left click, show menu on the right. They promised to make the behaviour unified. So, where is "The unified behaviour"? I only see they've reduced some very useful functionality (raise on the left click), but the "mess" is still here since they failed to do something usable with both Tomboy and Network Manager.
Oh, today they are making **very consistent** time applet, without weather report feature. :mregreen:

Both would have been a huge time investment to port them to the indicator menu. If there were more people working on it it could have probably been done. Another reason Tomboy didn't get ported was because the indicator spec doesn't currently have support for pins (on the right in the current Tomboy applet).

The explanation I heard about the time indicator not having weather was that weather has very little to do with time.

> BTW, I like part of the things they've done. But I absolutely hate what they've done with RB, Transmission and Nautilus File Copying. I've never used right click menu, it's absolutely featureless.

You are still missing the point of indicator. To have a consistent way  of accessing that information. The fact that left-clicking shows the menu and right-clicking doesn't is a testament to that.

> The confirmation they've failed with network-manager applet is the indicator network developers ppa: they use connman instead of network manager :mrgreen:

Conman is targeted to replace network-manager in the Netbook Edition. The reason for that is most likely purely technical. Meego is using it to great effect. So no there is no confirmation of failure as you claim.

> So, the summary is they acts like an ostrich. They failed with Tomboy, failed with Network Manager. These are the only two apps from Notification Area what makes the mess, since their behavior is differs from others. But what indicator team do: they reduced functionality of apps that acts consistently and could do nothing with apps that acts inconsistently. :mrgreen:

The spec wasn't implemented for all applications. Ubuntu has limited amount of time and developers for each cycle. It's unrealistic to expect them to fix every single app. What can be debated if the indicator work should have been postponed until it was fully compatible with all the applications in Main repo.

> P.S. I'm not against indicators. I'm against indicators for apps that raises main program window on left click and show menu on the right one. I like how messaging menu works, how new sound menu works. I don't care about me menu and "shutdown-reboot-etc" indicator since the first thing I do is to drop both. But I hate indicators for Rhythmbox and Tranmission, they are absolutely awful and unusable. I hope they won't touch weather/time applet, it's a way better than their time indicator.

They created a consistent way to access that functionality. Left-click and that's that. You are also confusing that area for a window list. If you are accessing RB and Transmission so much why do you minimize them to the indicator applet at all? I can understand if you check Transmission every few hours and then it isn't so hard to left-click and click on "Show Transmission". If you are doing it every few minutes then you shouldn't minimize them to the indicator applet.

All in all you should really read about what indicators do and why are they designed like that.

---

### Post by vkontakte on 2010-06-10
> **zekopeko said:**
> You basically didn't say anything constructive. What does "designer should also be taught what both colors and icons" mean? You do understand the icons in the menus (for most things) have been dropped? And indicators are designed to behave as close as possible to menus.
They must be intuitive. Today they looks like ....
> They both show an indicator and both have a "Show XYZ" option, so yes, there is a common way to access that functionality.
It's a lie:
[IMG]http://www.hostanypic.com/out.php/i9883_screenshot-2.png[/IMG]
[IMG]http://www.hostanypic.com/out.php/i9884_screenshot-3.png[/IMG]
> Both would have been a huge time investment to port them to the indicator menu. If there were more people working on it it could have probably been done. Another reason Tomboy didn't get ported was because the indicator spec doesn't currently have support for pins (on the right in the current Tomboy applet).
And how it will look like after being indicatorized? Or they will reduce functionality again?
> The explanation I heard about the time indicator not having weather was that weather has very little to do with time.
Another team, much more successful -- GNOME foundation once add this functionality to their applet. I have much more faith to them but not to canonical. In addition, I feel it's good, I like using it and it doesn't feel any overcomplicated.
> You are still missing the point of indicator. To have a consistent way  of accessing that information. The fact that left-clicking shows the menu and right-clicking doesn't is a testament to that.
LOL, that's the point! What "information" does RB or Transmission applet grant? They are both about the actions. Of course, I know they suggest to use menu to basic actions, but I always find this way inconvenient.
> Conman is targeted to replace network-manager in the Netbook Edition. The reason for that is most likely purely technical. Meego is using it to great effect. So no there is no confirmation of failure as you claim.
The confirmation is clean. Where the Network Manager indicator? They didn't manage to do a good replacement so far. There were no "indication" they will be successful in it.
> The spec wasn't implemented for all applications. Ubuntu has limited amount of time and developers for each cycle. It's unrealistic to expect them to fix every single app. What can be debated if the indicator work should have been postponed until it was fully compatible with all the applications in Main repo.
And it won't. Most linux desktop development are doing by Novell and RedHat employees. I'm sure they won't do anything with appindicators.
> They created a consistent way to access that functionality. Left-click and that's that. You are also confusing that area for a window list. If you are accessing RB and Transmission so much why do you minimize them to the indicator applet at all? I can understand if you check Transmission every few hours and then it isn't so hard to left-click and click on "Show Transmission". If you are doing it every few minutes then you shouldn't minimize them to the indicator applet.
I don't need the real mess at my Alt+Tab and Taskbar. It hurts me much more than imaginary mess in the notification area. I do basic actions with RB by keyboard, not with its menu. But I often change filtering there, so I need its window.
> All in all you should really read about what indicators do and why are they designed like that.
LOL
Another indicator message: it can't be unusable, but it should be consistent :mrgreen:

Your "explanation" only proved the indicator idea is another impracticable scheme with idea "make everything acts like a menu" without any real research.4ndC4gTW9zdCBsaW51eCBkZXNrdG9wIGRldmVsb3BtZW

---

### Post by Merk42 on 2010-06-10
> **vkontakte said:**
> [QUOTE=zekopeko;9439720]They both show an indicator and both have a "Show XYZ" option, so yes, there is a common way to access that functionality.It's a lie:
[IMG]http://www.hostanypic.com/out.php/i9883_screenshot-2.png[/IMG]
[IMG]http://www.hostanypic.com/out.php/i9884_screenshot-3.png[/IMG]
[/QUOTE]

Well I don't know about you, but I certainly see "Show Transmission" and "Show Rhythmbox" in those screenshots.  You can maybe file a bug that "Show Transmission" is first and "Show Rhythmbox" is second to last, but the functionality is there.

---

### Post by hugmenot on 2010-06-10
> **vkontakte said:**
> And how it will look like after being indicatorized? Or they will reduce functionality again?

There is a tomboy indicator. And yes, they didn’t implement pinning.

---

### Post by vkontakte on 2010-06-10
> **Merk42 said:**
> Well I don't know about you, but I certainly see "Show Transmission" and "Show Rhythmbox" in those screenshots.  You can maybe file a bug that "Show Transmission" is first and "Show Rhythmbox" is second to last, but the functionality is there.
Of course I'm talking about the functionality: it should be performed automatically. BTW it was "Open app" before in Transmission (I don't use that crap since 10.04 switch to this awful stuff, Deluge is way better, and it still use Left click -- Right click approach).

---

### Post by vkontakte on 2010-06-10
> **Merk42 said:**
> Well I don't know about you, but I certainly see "Show Transmission" and "Show Rhythmbox" in those screenshots.  You can maybe file a bug that "Show Transmission" is first and "Show Rhythmbox" is second to last, but the functionality is there.
Oh, yes. I filled the bug in time of 4th or 5th alpha.

---

### Post by zekopeko on 2010-06-10
> **vkontakte said:**
> They must be intuitive. Today they looks like ....

It's a lie:
[IMG]http://www.hostanypic.com/out.php/i9883_screenshot-2.png[/IMG]
[IMG]http://www.hostanypic.com/out.php/i9884_screenshot-3.png[/IMG]

Oh look, "Show Rhythmbox" and Show Transmission".

> And how it will look like after being indicatorized? Or they will reduce functionality again?

You really need to do some research before asking rather inane questions.

> Another team, much more successful -- GNOME foundation once add this functionality to their applet. I have much more faith to them but not to canonical. In addition, I feel it's good, I like using it and it doesn't feel any overcomplicated.

FYI Gnome removed the icons in menus. If you like vanilla Gnome then use the stracciatella session.

> LOL, that's the point! What "information" does RB or Transmission applet grant? They are both about the actions. Of course, I know they suggest to use menu to basic actions, but I always find this way inconvenient.

So what is the point of the old **notification** area? It had actions as well which aren't notifications. Semantic nitpicking won't bring you anywhere.

> The confirmation is clean. Where the Network Manager indicator? They didn't manage to do a good replacement so far. There were no "indication" they will be successful in it.

LOL. Let me repeat again: do research into the current blueprint for the new network indicator before making assumptions. Every time Ubuntu changes something they have a backup plan if they don't make it in time. If they don't make the indicator in time they will simply fall back on the old Network-Manager applet.

> And it won't. Most linux desktop development are doing by Novell and RedHat employees. I'm sure they won't do anything with appindicators.

Here you go again. Making baseless assumptions. A number of applications are already supporting them and more are on the way.
RedHat and Novell are free to do what they want with their own distros. For instance Novell has the SLAB menu and YaST which Gnome doesn't use.

> I don't need the real mess at my Alt+Tab and Taskbar. It hurts me much more than imaginary mess in the notification area. I do basic actions with RB by keyboard, not with its menu. But I often change filtering there, so I need its window.

The mess ins't imaginary. It's real but nobody cared before to clean it up.
BTW you will be pleased to know that Gnome is adopting some part of the indicators in Gnome-Shell.

> LOL
Another indicator message: it can't be unusable, but it should be consistent :mrgreen:

This is your personal opinion. I for one find it doesn't have any merit and is basically ranting because you won't learn the new way of doing things.

> Your "explanation" only proved the indicator idea is another impracticable scheme with idea "make everything acts like a menu" without any real research.4ndC4gTW9zdCBsaW51eCBkZXNrdG9wIGRldmVsb3BtZW

Just because you can't understand my explanation and haven't done your research on the subject doesn't prove that "indicator idea is another impracticable scheme". I would say it is quite the opposite.

---

### Post by cariboo on 2010-06-10
Moved to the Cafe, as it really not a support thread.

---

