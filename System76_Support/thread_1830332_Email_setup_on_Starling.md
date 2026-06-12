---
title: "Email setup on Starling"
date: 2011-08-21
forum: System76 Support
---

### Post by xamiam on 2011-08-21
I posted this somewhere but I can't seem to find the post.  I'm sorry.  The email setup dialog is too big and it won't let me resize the window smaller.  How can I set up the email.

Thanks,
Max

---

### Post by Dave_L on 2011-08-21
With the cursor positioned anywhere in the window, hold down the Alt key and the left side of the button below the touchpad.  Then you can drag the window around. It's clumsy, but it lets you access all the parts of the window.

---

### Post by xamiam on 2011-08-21
OK, that helped.  Thank you.  I was able to pull the dialog up to the top and it opened a whole display window.  It jumped around a bit, but I was able to fill out the Evolution ISP info.

Now my ISP requires non-standard ports inbound and outbound.  Evolution I was not able to make those changes.  Evolution just hangs up, hard!  I had to pull the battery to regain control. :-(


Is there a way to just edit the configuration?  It didn't look like I could get to the account information in Evolution.

How do I kill a hung task?

Thank you.

---

### Post by HotShotDJ on 2011-08-24
> **xamiam said:**
> How do I kill a hung task?

Thank you.I'm not sure about your questions regarding setting up Evolution, however, I may be able to help with killing a hung task.

1) Generic

There are several ways -- my favorite is "xkill."  Simply open a terminal and type "xkill" (without the quotes, of course) and then you'll be able to click on the misbehaving application to kill it.  You may be able to add an icon to your panel to accomplish the same thing by left clicking on an empty part of the panel and then adding an applet.  I can't remember the name of the applet (I use Gnome 3 with Gnome Shell which is quite different to Gnome 2). 

You can also open the system monitor, click on the "Processes" tab and then find the misbehaving application in the list and kill it from there.  This may be a bit cumbersome, but it is usually effective.

2) Evolution Only

Open a terminal and issue the following command:```
evolution --force-shutdown
```This will make sure that all components (not just the user interface) are killed. If you use the "Generic" instructions, usually several components of Evolution are left running in the background.

Good luck and (most importantly) have fun!

---

