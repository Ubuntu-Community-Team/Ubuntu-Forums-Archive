---
title: "Inertia now working on external touchpad (on Desktop)"
date: 2012-07-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-07-24
Inertia started working for me after today's updates. It's very noticeable when trying two-finger slide up and down on chromium using an external Logitech wireless touchpad on a desktop.

It's good news. However, it is still impossible to adjust a touchpad acceleration/sensitivity or configure gestures (2/3/4 fingers slides, actions for clicks on specific touchpad-areas, etc) via GUI since the "Touchpad" tab is disabled on on g-c-c/"Mouse and Touchpad" on Desktops. But even if it was enabled, it is designed for 90's touchpads. 

If anyone uses (or plans to try) a Touchpad on Desktops (like Apple Magic Trackpad, Logitech Wireless Touchpad, new keyboards with embedded touchpads, etc) and is interested in this issue, I have posted a request on Ubuntu Brainstorm to enable g-c-c/"Mouse and Touchpad/"Touchpad" tab on Desktops if a touchpad is detected (thus dropping /usr/sbin/laptop-detect logic in this case). IMO, the idea that only Laptops have touchpads will die for good in-between QQ/RR cycles. I think we should make sure QQ keeps up with the trends.

Regards,
Effenberg

---

### Post by jbicha on 2012-07-24
effenberg, I agree that if you have a touchpad attached to your computer that the Touchpad Settings should be available. Please open a bug for that.

I'm not sure where's the right place to file the bug, maybe gnome-control-center?

---

### Post by effenberg0x0 on 2012-07-25
> **jbicha said:**
> effenberg, I agree that if you have a touchpad attached to your computer that the Touchpad Settings should be available. Please open a bug for that.

I'm not sure where's the right place to file the bug, maybe gnome-control-center?

Hi jbicha, 

I'm not sure, I though about g-c-c too. The thing is, last times I opened this kind of stuff as bugs, I was advised to move to Brainstorm (the rationale would be "the lack of a functionality is not a broken feature" - more or less. Maybe it makes sense). So this time I just went directly to it: [http://brainstorm.ubuntu.com/idea/29977/](http://brainstorm.ubuntu.com/idea/29977/)

Anyway, I'll try to open a bug report for g-c-c and post a link here.

Thanks!
Effenberg

---

### Post by effenberg0x0 on 2012-07-25
LOL, just saw this at Brainstorm:

>  Darwin Survivor (Brainstorm moderator) wrote on the 22 Jul 12 at 09:27	
This sounds like a no-brainer. As such, I recommend filling a bug report. If the developers tell you that they need more community demand for such a feature, please let us know and we will re-activate this idea. 

Closing since this appears to be a bug.

A bug it is then.

Regards,
Effenberg

**EDIT:** Bug report here: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1028754](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1028754)

---

### Post by Mr. Picklesworth on 2012-07-25
Hope you don't mind, Effenberg: I just cleaned up your bug report by snipping out that "moreover" bit. I agree it would be nice to have some buttons to control scroll inertia, but sneaking a wishlist item into another bug report just results in a big bug report, which slows down progress on the real bug *and* the wishlist item ;)
It always works better when they can be tracked separately.

The touchpad panel is due for a redesign. There is a whiteboard over on the GNOME design team's wiki:
[https://live.gnome.org/Design/SystemSettings/Mouse](https://live.gnome.org/Design/SystemSettings/Mouse)
You might want to join them on IRC to chat about it.

Oh, and please try to be specific with that one. "Add more options" is not a particularly effective feature request. It's very difficult to argue that broad a position. (Especially when you're talking with people who design things to have as few loose bits as possible). "Add X option" is a better place to start.

---

### Post by effenberg0x0 on 2012-07-25
> **Mr. Picklesworth said:**
> Hope you don't mind, Effenberg: I just cleaned up your bug report by snipping out that "moreover" bit. I agree it would be nice to have some buttons to control scroll inertia, but sneaking a wishlist item into another bug report just results in a big bug report, which slows down progress on the real bug *and* the wishlist item ;)
It always works better when they can be tracked separately.

The touchpad panel is due for a redesign. There is a whiteboard over on the GNOME design team's wiki:
[https://live.gnome.org/Design/SystemSettings/Mouse](https://live.gnome.org/Design/SystemSettings/Mouse)
You might want to join them on IRC to chat about it.

Oh, and please try to be specific with that one. "Add more options" is almost universally ignored as a feature request. It's very difficult to argue that broad a position. (Especially when you're talking to people who design things to have as few loose bits as possible). "Add X option" is a better place to start.


Thanks for your help Mr. Picklesworth :) It's really appreciated. 

Unfortunately, I wont be able to join the developers on IRC or be any more specific about which features should be available. I am on a bad phase this cycle, totally burned out, not so happy about the community dynamics and I do not have the patience for FOSS politics right now. As I probably wouldn't contribute to it positively, I try to stay away as much as possible. 

I am confident that the reasonable people in development will look to the market and code something to keep Gnome (and the OSs that depend on it) competitive. They can just copy MacOS more or less and it's fine, it's no quantum physics anyway: Just a GUI for settings that are already doable (and being done by users) via xorg.conf and keymaps. I'm sure devs have a precise idea of whats needed, better than I could ever express.

I hope others answer to this call, I'm sure people will :)

Thanks!
Effenberg

---

