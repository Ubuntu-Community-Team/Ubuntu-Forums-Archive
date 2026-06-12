---
title: "How to live without system tray"
date: 2010-05-15
forum: The Cafe
---

### Post by rumca.js on 2010-05-15
Hi all you linux lovers,

For six months I've been using Ubuntu (Jaunty, Karmic, now lucid). Still, I am very much used to windows way about things in system. I am very glad that every system issue is in file (that can be editable with proper knowledge and sudo rights).

I can understand also that some people may think that system tray is confusing in behavior. However if not using system tray, then what?  (I am referring to the fact that system tray is about to be dropped).

How am I supposed to live without system tray?

If transmission is not there how am I supposed to open it, or view the download progress?
If pidgin is not there how am I supposed to view messages?

I do not know how well pidgin is integrated in lucid with os, because I threw the indicator applets. But I think pidgin is not even integrated so good and I can't use evolution because it does not support well IM protocol used in Poland (argh!! importing contacts in gadu-gadu is impossible).

That is why I am using system tray again and made transmission / pidgin tray icons visible.

I can't see also any good ubuntu tutorial about how to live without system notification area. Even google doesn't say anything about it (or it's just that I can't find any useful hint).

What else is out there for us used to windows?
Will Ubuntu drop panel support, or will throw out windows and use something different, hard, which would involve unnecessary change.

---

### Post by Calash on 2010-05-15
I believe the intent is to use other methods of window control that will make the system tray (Notification Area as it is known in Ubuntu) obsolete

If you look at Gnome-Shell, a key part of Gnome3, and how it functions you can see the logic that the Devs are using.  There is a notification popup, but but for the most part Windows are managed in the Overlay, where even closed windows are shown and can quickly be inspected even without activating them.

---

### Post by ibuclaw on 2010-05-15
It's called the **notification area**, not the system tray. And that is the pinnacle of the confusion. ;)

As this not a support question, moving to Cafe.

---

### Post by cguy on 2010-05-15
You could use multiple virtual workspaces and have non-closeable windows binded to those workspaces.
eg: You have Pidgin always open on the "Internet" workspace, Transmission on "Others" etc.


There are some good ideas about the future of the system tray, but I fail to see why everybody wants to nuke it.



@ibuclaw: it's called a freaking System Tray, not a notification area!!! It may have started as a notification area, but its current purpose is far beyond notifing.

---

### Post by Mr. Picklesworth on 2010-05-15
The system tray isn't being *removed*; it's being replaced. Its replacement is with the StatusNotifier specification, which has been adopted by KDE and Ubuntu (and is aiming to become a Freedesktop specification, which should be easier when the Gnome Shell guys realize that their approach isn't going to work, or that the rest of the world has chosen for them).

Ubuntu's implementation of that specification is the Indicator Applet and libindicate. It also has some extra gadgets such as the messaging menu, which is being referred to as a &#8220;category indicator.&#8221; Many apps feed into the one indicator to achieve magical stuff.

For developers, like libnotify, the system provides order; a single way to do a single specific task.

The old system tray specification + notification area literally gives an application a tiny window and tells it to do whatever it wants with it (&#8220;but please only use it for notifications!&#8221;). It doesn't take into account that different applications think differently. It does NOT work well for a number of reasons. System tray applets are used to extend the surrounding desktop interface, but *extensions* just plain shouldn't be implemented that way. Consider browser toolbars (see Internet Explorer in any off the shelf Windows machine; the manufacturer usually adds Google, Norton or Yahoo toolbar, or all of them, to torment you), compared to Firefox extensions. Firefox extensions integrate with the surrounding UI; they are not written with arbitrary programming languages or UI toolkits. Browser toolbars are uniquely horrible things because they get stamped on top of the UI and do things however they want. (Usually creating intense breakage).

For users, the StatusNotifier + Indicator system provides consistency. Every indicator becomes a menu, so you can click any one of those icons at the top right of your screen confidently knowing what will happen; it'll open a menu and you will see a bunch of clearly labelled options. Being a menu, all the usual menu tricks apply; you can hold the button down, drag to the option you want and release, etc.
If you happen to be using KDE (or, some day, a text-based environment), all of those menus will follow your environment's respective rules because the menus are generated by a single specifically tuned application of your choosing, based on requests made by the applications you are running.

Not all of the applets are moved over yet. The Sound, Power, Bluetooth, Messages, Session, Universal Access and Transmission applets all use the indicator system in Lucid. (Version 0.8 of Dropbox does, too). The Network applet doesn't yet, but should for 10.10.

It may take some getting used to over the old approach, and there are some kinks to work out, but in a year this shall be grand :)

---

### Post by 23meg on 2010-05-15
The notification area (also commonly known as the "system tray") is being gradually replaced with [application indicators]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators"). The plan is to remove it from the panel *by default* by Ubuntu 10.10; you'll still be able to add it to your panel if absolutely needed.

---

### Post by MichealH on 2010-05-15
I agree with 23meg because Everything like Transmission has it oven Indicator which can be added to the panel.In the Indicator Applet you have 3 Items labelled Chat, Mail and Broadcast which informs you of anything going on in the program itself. The Chat,Mail and Broadcast are not Indicators but they are part of the indicator. Hope to of cleared things up

---

### Post by nothingspecial on 2010-05-15
I live without the panel.

Never mind the "system tray".

---

