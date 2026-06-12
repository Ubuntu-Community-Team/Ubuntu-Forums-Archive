---
title: "How to replace Notify OSD"
date: 2011-01-10
forum: The Cafe
---

### Post by robi_sabocanec on 2011-01-10
To all of you that don't like notify OSD, here is how you can get good old notifications that one can click on.

Motivation:
After reading about Notify OSD, I've found out that it has been done according to some standard, and, most likely, the standard was done towards OS X notifications system. Everything look nice IMHO, but using it is frustrating.
Many applications rely on notification system, take Gwibber, for example, you get notification of new tweet which contain a link, but to open the link, you have to go to the actual app (gwibber) and then open a link. What's the use of notification in that case? And if you want to keep the notification displayed a bit longer, you instinctively move your mouse pointer over it, but than the notification gets blurred and you no longer see what's on it. Totally counter-intuitively. 
Also, I'm using Dropbox for sharing, so when someone add a content to our shared folder, I get notification which says something like "... click to open a folder...". But, again no use of click, I have to manually open nautilus etc.

In rational, designers say they want to protect user from accidental clicks. This is a bad argument IMHO, users aren't stupid, there is a plenty of other ways to make harm to your computer. 

One more thing that bothers people is that you can't change the notification's position on the screen without patching notify-osd. Notification position can become real issue when you have two monitors for example.

So, I decided to disable notify OSD and give a chance to notification-deamon, which does what I expect it to do, although it's not an eye candy.

Firstly, I tried to uninstall notify-osd, but that's impossible since ubuntu-desktop package depends on it!!!

Here is another way to do it:

1. Install notification-deamon (sudo apt-get install notification-deamon)
2. Open /usr/share/dbus-1/services/org.freedesktop.Notifications.service (You can backup this file if you plan to return to notify-osd later)
3. Change the 'Exec' line to 
   Exec = /usr/lib/notification-daemon/notification-daemon
4. Save the file and restart computer

I also want to say that for an average user this may look complicated and it is one of the design decision which makes harm to linux popularity.

Regards

---

### Post by Paqman on 2011-01-10
> **robi_sabocanec said:**
> most likely, the standard was done towards OS X notifications system.

OS X doesn't have a notification system. There's Growl, but that's a 3rd party app and is available for Windows, too.

I like notify-osd myself. Having it pre-installed and integrated is one of the things that genuinely puts Ubuntu ahead of Windows or OS X. Fair enough if you want to remove it though, it's your system.

---

