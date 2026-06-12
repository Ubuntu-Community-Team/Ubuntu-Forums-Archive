---
title: "What can you say about the new indicator-applet in Jaunty?"
date: 2009-04-25
forum: The Cafe
---

### Post by wersdaluv on 2009-04-25
When I upgraded to Jaunty, I did not preserve some GNOME configuration files to see how the default desktop would look like. It appears that the panel has a new configuration. The volume applet isn't present by default (I don't understand why) and there's a new indicator-applet. I don't really get what it is for. The only apps I use that it works with are Pidgin and Gwibber. The only thing that it has done for me so far is to change its icon when one of my Pidgin contacts goes online, which is not very useful because there's already a notification daemon.

Also, does it have something to do with Pidgin's Buddy List's being in window lists of all workspaces?

What can you say about the indicator-applet?

---

### Post by joey-elijah on 2009-04-25
In one word: WTF?!

Im not sure what it does other than take up room on my panel... only Gwibber ever sits in it and it just confuses me .. why do i need to instances of an application in my taskbar? I normally notice when Gwibber updates itself because of this new feature called Notifications... i don't spend hours looking at the applet waiting for it to change colour...

---

### Post by wersdaluv on 2009-04-25
> **joey-elijah said:**
> In one word: WTF?!

Im not sure what it does other than take up room on my panel... only Gwibber ever sits in it and it just confuses me .. why do i need to instances of an application in my taskbar? I normally notice when Gwibber updates itself because of this new feature called Notifications... i don't spend hours looking at the applet waiting for it to change colour...
I feel the same way. I'm just curious why they made the applet. I hope, there's a useful feature that is yet for me to discover.

---

### Post by SunnyRabbiera on 2009-04-25
The volume applet is no more, its been replaced by pulse entirely and you cant max out volumes unless you have a booster like I do...
I cant hear my sound unless I put my speakers on full blast

---

### Post by wersdaluv on 2009-04-26
> **SunnyRabbiera said:**
> The volume applet is no more, its been replaced by pulse entirely and you cant max out volumes unless you have a booster like I do...
I cant hear my sound unless I put my speakers on full blast
What booster?

---

### Post by bryncoles on 2009-04-26
i have a volume applet, and my sound is same as it ever was...

is it because i upgraded instead of reinstalling?

---

### Post by wersdaluv on 2009-04-26
> **bryncoles said:**
> i have a volume applet, and my sound is same as it ever was...

is it because i upgraded instead of reinstalling?
Yep. Your old configuration files are preserved.

---

### Post by swoll1980 on 2009-04-26
> **SunnyRabbiera said:**
> The volume applet is no more, its been replaced by pulse entirely and you cant max out volumes unless you have a booster like I do...
I cant hear my sound unless I put my speakers on full blast

Did you try changing your master?

---

### Post by billgoldberg on 2009-04-26
> **wersdaluv said:**
> Yep. Your old configuration files are preserved.

Bullsh*t.

I did a fresh install, and the volume applet is sitting there as usual, on both machines.

---

### Post by Sealbhach on 2009-04-26
Maybe it's still in development, so sort of experimental.


.

---

### Post by wersdaluv on 2009-04-26
> **billgoldberg said:**
> Bullsh*t.

I did a fresh install, and the volume applet is sitting there as usual, on both machines.
lol. Chill. You might get a heart attack.

Thanks anyway. It seems that the issue's just with my desktop judging by the Jaunty screenshots on Lifehacker.

---

### Post by Seaco on 2009-04-26
my volume is in the same place like it was on hardy, and i am using jaunty since beta release

---

### Post by defreng on 2009-04-26
well, if you use GMail you can place a great notifier in this applet ;)

[http://ubuntuforums.org/showthread.php?t=1136699](http://ubuntuforums.org/showthread.php?t=1136699)

---

### Post by Giant Speck on 2009-04-26
Does the indicator-applet have anything to do with the supposed new notification system?  Because I haven't seen it do a thing since I installed 9.04.

---

### Post by 23meg on 2009-04-26
> **joey-elijah said:**
> In one word: WTF?!

Im not sure what it does other than take up room on my panel... only Gwibber ever sits in it and it just confuses me .. why do i need to instances of an application in my taskbar? I normally notice when Gwibber updates itself because of this new feature called Notifications... i don't spend hours looking at the applet waiting for it to change colour...

> **wersdaluv said:**
> I feel the same way. I'm just curious why they made the applet. I hope, there's a useful feature that is yet for me to discover.

Reading the specification may help you understand the rationale.

[https://wiki.ubuntu.com/MessagingMenu/](https://wiki.ubuntu.com/MessagingMenu/)

---

### Post by Polygon on 2009-04-26
from that wiki article:

> 
In the &#8220;Interface&#8221; tab of Pidgin&#8217;s Preferences, the &#8220;System Tray Icon&#8221; section should be removed, with the &#8220;Show system tray icon&#8221; setting being hard-coded to &#8220;Never&#8221;. 


if that happens i will be very upset. Why? because right clicking on the pidgin entry in indicator applet does NOTHING, it just raises the buddy list. the tray icon is useful cause i can right click > exit, right click > set status, right click > plugins.....its so much easier. 

some things deserve a spot in the tray. The pidgin tray icon is one of them.

---

### Post by Tibuda on 2009-04-26
I don't use it, because I already got the notification area or system tray.

---

### Post by Kareeser on 2009-04-26
Mmhm... I find the indicator applet useless as well. I believe it was included in an attempt to limit the amount of icons in the notification area.

It's just still in develoment, unfortunately... it looks like applications like Pidgin and such haven't crossed over yet.

---

### Post by mc4100 on 2009-04-26
I gather from the wiki that the indicator applet is a menu for consolidating messages gathered by various applications, but does it really need to *be* an applet. It doesn't degrade very well when:
[list][*]You haven't opened any of those specific apps yet.
[*]There aren't any new messages yet[/list]
In both cases, it's useless and shouldn't be stealing space in the panel. 
This reminds me of the volume applet and how *it* didn't do well either if there were no sound cards. It too would be completely useless and waste space.
The solution was to have it magically appear in the notification area when it was needed (read: output device detected) ... should the messaging menu, ie., the indicator applet, do the same: appear in the notification area only when there are messages to be indicated?

Edit: Forgot to say, this new volume applet-thing (what do I call it) isn't in Jaunty, it caused regressions so the change was reverted. It'll be in Fedora though.

---

### Post by Namtabmai on 2009-04-26
> **Polygon said:**
> from that wiki article:



if that happens i will be very upset. Why? because right clicking on the pidgin entry in indicator applet does NOTHING, it just raises the buddy list. the tray icon is useful cause i can right click > exit, right click > set status, right click > plugins.....its so much easier. 

some things deserve a spot in the tray. The pidgin tray icon is one of them.

I thought exactly the same thing as you when I read this, but then I remembered that they no longer refer to it as a systray but as a "Notification area". With this change in mind it makes sense.

Then again I don't agree with that which is why I've jumped off the Gnome ship, but I'd be very annoyed if they make these changes to Pidgin so it effects all users regardless of the DE they are running.

---

### Post by hanzomon4 on 2009-04-26
I don't see whats wrong with it besides the icon. It functions like the usual applets for pidgin and evolution. Takes up less space and you can remove it, so....

---

### Post by Orlsend on 2009-04-26
I like it, I wish my applications would use it more often. but for now only Wireless changes are the only updates I get.

---

### Post by drawkcab on 2009-04-26
Yeah, not a big deal for me.  I prefer a clean and tidy desktop and I think it's fine.

---

### Post by 5nak3 on 2009-04-26
Personally, I am neutral on the whole situation i had it sitting there it looked nice, I noticed it did nothing, so I removed it. No big issue.

My bigger issue is the actual notifications that pop up now, especially when using Pidgin, the reason is when I had libnotify, i could click the notification and the chat window would pop up for the contact that signed in. The new system seems to fade away when I mouse over. This is good as I can reach the max,min and close buttons regardless of who is signing in. But it also means I have to open the contact list and then double click the contact of choice when I want to chat to someone who has just logged in!

---

### Post by wersdaluv on 2009-04-26
> **Polygon said:**
> from that wiki article:



if that happens i will be very upset. Why? because right clicking on the pidgin entry in indicator applet does NOTHING, it just raises the buddy list. the tray icon is useful cause i can right click > exit, right click > set status, right click > plugins.....its so much easier. 

some things deserve a spot in the tray. The pidgin tray icon is one of them.
That's the important part. I kept my Pidgin config files so I still have the Pidgin icon. Hence, I found the indicator-applet useless. And yes, I agree with your stand.

---

### Post by Kareeser on 2009-04-27
Experimenting with the indicator applet further, I can see why it was implemented.

Evolution also uses it, and the applet itself is just a general indicator of new activity, such as a new email or new message.

Granted, there are notifications for new instant messages, and that's the behaviour that everyone is used to (the nicknamed "toaster popup"), but I find that it works superbly for Evolution as a mail client.

*cough*

The point being that with Pidgin and Evolution **both** using the indicator applet, we get less space used on the notification area. Is this a step in the right direction? I personally think so, but there will be some things that we have to get used to (e.g. clicking on the indicator applet does nothing except open up a drop down menu for you to open the application in question).

So it works to consolidate many different apps' notifications, *as least obtrusively as possible*.

---

### Post by wersdaluv on 2009-04-27
> **Kareeser said:**
> Experimenting with the indicator applet further, I can see why it was implemented.

Evolution also uses it, and the applet itself is just a general indicator of new activity, such as a new email or new message.

Granted, there are notifications for new instant messages, and that's the behaviour that everyone is used to (the nicknamed "toaster popup"), but I find that it works superbly for Evolution as a mail client.

*cough*

The point being that with Pidgin and Evolution **both** using the indicator applet, we get less space used on the notification area. Is this a step in the right direction? I personally think so, but there will be some things that we have to get used to (e.g. clicking on the indicator applet does nothing except open up a drop down menu for you to open the application in question).

So it works to consolidate many different apps' notifications, *as least obtrusively as possible*.
Makes sense. It's just that, the right clicking of an icon is significant. Something like the drawer applet's concept would be nice so they can be right clicked and they have icons.

---

