---
title: "lock the CD/DVD when absent"
date: 2010-05-07
forum: Security
---

### Post by rnerwein on 2010-05-07
hello
i tried to make a  [recommendation ( ups that link ain't comes from me - i only looked for a word in a dictionary )]("http://dict.leo.org/ende?lp=ende&p=CjpDXDPoAA&search=recommendation&trestr=0x8001") about traveling around with a laptop.
i talking about my own experinace ( sitting in a train go to dinner - chain my laptop but - DVD-drive ?? )
for GUI user i think it will be a nice option in the screensaver setup to lock the CD/DVD drive and thus
should be very easy to implement by the "eject" command. just have another buttom "lock/unlock" the drive in the menue.
think it's usefull and easy to implement.
--> ecject -i 1 / 0.
i use this on my sony - works.
i know it possible to bypass this - but this will take some much more time.

ciao     ;)

---

### Post by Agent ME on 2010-05-07
That sounds like a cool feature idea. However, if it doesn't get implemented, there's a few ways you can do that:

You can set a script in your crontab that checks every minute if the screensaver is active, and if it is, locks the drive; if it isn't, unlock the drive. There might be permissions problems about this but I think it could work. Though it would have the side-effect that if another user of the computer hit the "Switch User..." button and logged on, the drive would still stay locked while they were logged on because your screensaver and crontab script were still running in the background.

Alternatively, you can make a shortcut on your application bar (near the firefox, email, and help icons) that runs that command by right-clicking in an open space and creating a custom application launcher/shortcut.

---

### Post by EloiseJoseph on 2010-05-07
very nice information thanks for sharing this useful information with us. I m enjoying my presence here well done guys keep it up .

---

### Post by rnerwein on 2010-05-08
> **Agent ME said:**
> That sounds like a cool feature idea. However, if it doesn't get implemented, there's a few ways you can do that:

You can set a script in your crontab that checks every minute if the screensaver is active, and if it is, locks the drive; if it isn't, unlock the drive. There might be permissions problems about this but I think it could work. Though it would have the side-effect that if another user of the computer hit the "Switch User..." button and logged on, the drive would still stay locked while they were logged on because your screensaver and crontab script were still running in the background.

Alternatively, you can make a shortcut on your application bar (near the firefox, email, and help icons) that runs that command by right-clicking in an open space and creating a custom application launcher/shortcut.

hi
i ain't use a crontab script. i only use it for my laptop and i have already made a shortcut on my panel.
there i call my script in my ~/scripts/pause.sh with following contents
#!/bin/sh
#
# /dev/sr0 is my device - your's may be different 
eject -i on /dev/sr0
/usr/bin/xdg-screensaver activate
#eject -i off /dev/sr0 # this don't work - i must call it by myself after login. the screensaver app only 
# send a message to the gnome-screensaver app wich is already running and returns immediately.
# that's it
exit 0

have fun
ciao

---

