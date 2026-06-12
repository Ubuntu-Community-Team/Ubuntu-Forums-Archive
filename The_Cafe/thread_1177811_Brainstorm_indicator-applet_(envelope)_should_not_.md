---
title: "Brainstorm: indicator-applet (envelope) should not be only option for notifications"
date: 2009-06-03
forum: The Cafe
---

### Post by vegetarianshrimp on 2009-06-03
[[IMG]http://brainstorm.ubuntu.com/idea/20098/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/20098/)

**Rationale:**
In Ubuntu 9.04, the Pidgin icon in the notification area was replaced by the Gnome indidcator-applet, and is the only option for Pidgin notifications. I think it's a great idea, putting all notifications together, but some people (like me), only use it for one thing, for example, Pidgin. It's really annoying, because it requires two clicks, one on the envelope, and one on the program, instead of just the icon of the program. 
[B]
Solution #1: automatic switch to regular icons with removal of indicator-applet    [/B] 
Its fairly simple. Someone removes the indicator-applet from their Gnome panel, and the original icons for things like Pidgin reappear in the Notification Area.

---

### Post by Viva on 2009-06-03
Install guitifications

---

### Post by vegetarianshrimp on 2009-06-03
> **Viva said:**
> Install guitifications
I already have notifications of people logging in and such from the new notification system in 9.04. thanks though :)

---

### Post by Tibuda on 2009-06-03
> **vegetarianshrimp said:**
>  
[B]
Solution #1: automatic switch to regular icons with removal of indicator-applet    [/B] 
Its fairly simple. Someone removes the indicator-applet from their Gnome panel, and the original icons for things like Pidgin reappear in the Notification Area.

Are you sure it does not already works? I don't have the indicator applet, and I have a Pidgin icon in the notification area. Maybe there's a setting somewhere, I had imported from Intrepid.

---

### Post by zekopeko on 2009-06-03
better and simpler way would be to make the indicator applet open on mouse over not on click.

---

### Post by bruce89 on 2009-06-03
The only way I can see is to abandon libindicate entirely. Clearly Canonical can't be bothered submitting it as a GNOME depenency, so they have hopefully lost interest.

---

### Post by mcduck on 2009-06-04
Good idea, although I'm much more annoyed by the fact that the applet doesn't have a handle. If you don't have Pidgin, Evolution or some other program running that uses the applet it will be completely invisible, unclickable and unmovable but still on the way of your other panel applets.

---

### Post by mcduck on 2009-06-04
> **danielrmt said:**
> Are you sure it does not already works? I don't have the indicator applet, and I have a Pidgin icon in the notification area. Maybe there's a setting somewhere, I had imported from Intrepid.

Pidgin icon can still be enabled from Pidgin's settings.

Although if you do that and still have the Indicator applet on your panel you end with 4 different applets/icons reacting to Pidgin status. Indicator applet, Pidgin's notification icon, User Switcher-applet and on top of everything it even shows in the Window List on all workspaces..

Pretty bad result considering the purpose was to *reduce* clutter in panels..

---

### Post by zekopeko on 2009-06-04
> **bruce89 said:**
> The only way I can see is to abandon libindicate entirely. Clearly Canonical can't be bothered submitting it as a GNOME depenency, so they have hopefully lost interest.

isn't the whole point of notify-osd and libindicate to test waters?
why submit it as a dependency when it's not stable nor at a level worthy of gnome inclusion?

---

### Post by vegetarianshrimp on 2009-06-05
> **danielrmt said:**
> Are you sure it does not already works? I don't have the indicator applet, and I have a Pidgin icon in the notification area. Maybe there's a setting somewhere, I had imported from Intrepid.
Yes, you can enable the pidgin icon in the preferences of pidgin, but I was thinking that if you removed the indicator-applet, all the default icons and such of the applications using it would appear.

---

