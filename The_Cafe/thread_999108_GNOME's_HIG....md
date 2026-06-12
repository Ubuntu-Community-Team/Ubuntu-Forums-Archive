---
title: "GNOME's HIG..."
date: 2008-12-01
forum: The Cafe
---

### Post by xeriouxi on 2008-12-01
Hi!

I posted up an idea not long ago to Launchpad about giving users the option to put Evolution in the system tray so that it would always be running (which is immensely helpful for new emails and appointment alerts, etc.) and not be taking up the taskbar. However, this was rejected because it said it impedes the HIG of GNOME.

I can understand to an extent why this decision was made, but the fact that it wouldn't even be given as an option is a little upsetting and confusing... after all, isn't it all about choice?

Does anyone feel that the HIG for GNOME (and perhaps even KDE, maybe?) might restrict certain features that people would want? They are, after all, guidelines and not rules as far as I am aware.

Upon saying that, however, one interesting thing I did read was on Wikipedia about HIG...

> HIGs should be taken at face value; their recommendations and advice are meant to help developers create better applications, but developers are naturally free to break them if they think that the guidelines do not fit their application. The only repercussion for doing so may be that the organisation publishing the HIG does not give the application its blessing. Mozilla Firefox's user interface, for example, goes against the GNOME project's HIG, which is one of the main arguments for including Epiphany instead of Firefox in the GNOME distribution. But such departures should only be taken when there is evidence from usability testing that the interface is improved.

As Evolution is so integrated into GNOME could it be that maybe it couldn't even add it as an option because it needs the 'blessing' of the GNOME HIG?

Thanks for any input on the topic! =)

---

### Post by aaaantoine on 2008-12-01
Yes, you should be able to always see whether or not you have new mail without running the full Evolution application.  No, the icon should not always be in the taskbar.

I would elect to have the icon only show up in the notification area when it is something that needs attention, such as unread mail.  This happens already when Evolution is running, but so far as I know, there's no such option for when it isn't running.

I had a similar idea about the trash icon being visible in the notification area for the same reason.  Because what good is an empty trash bin that takes up space on your UI?  You are only really concerned about the trash when there's stuff in it.

Likewise, what good is an Evolution nofication area icon when there's no new mail?  I already have clutter in my notification area thanks to the Compiz Fusion Icon (which I will no longer need when DRI2 makes it to Ubuntu) and Gnome-RDP (which I will no longer need when VNC adds support for RDP).  The Compiz Fusion icon would better serve as a panel applet that I could position to my liking, and Gnome-RDP has no business whatsoever adding an icon to the notification area (it doesn't even match the panel background!).

---

### Post by Mr. Picklesworth on 2008-12-01
> **xeriouxi said:**
> I can understand to an extent why this decision was made, but the fact that it wouldn't even be given as an option is a little upsetting and confusing... after all, isn't it all about choice?)

Not really. The system tray does not exist. It is the notification area, and a horrifying number of applications are screwing it up by spewing themselves on it. If you want to see a running application, look for its minimized 'on all desktops' window in your window list.

In the future, hopefully we will have a second place for a running process to represent itself which is detached from toplevel windows. MacOS manages to detach windows and processes reasonably well, although it fails miserably at explaining the distinction to users.

In the mean time, I for one would leave Evolution open and bump its open window to the right-most workspace.


As for why the HIG must be defended like this, there is a perfectly good reason. Right now Evolution's New Mail icon must blink in a stupid way. Why? Because otherwise people would ignore it. As it is, all sorts of things treat the notification area as a permanent fixture for their interfaces, so people don't view something in that area as a notification at all. We can't just create a "Notification area 2", so the actual notifications must somehow coexist in their home turf. Only one way to do that: Battling for visibility.

---

### Post by xeriouxi on 2008-12-01
Thanks for your replies! =)

I think I understand more now how the whole idea is meant to work as I did think of it more as a system tray and not a notification area. It seems that I didn't read the Launchpad idea reply well enough when it referred to the notification area, hehe!

I guess what I should hope for sometime in the future is some kind of daemon perhaps that can, as aaaantoine stated, alert me when I have new mail etc. without the actual application interface running.

---

