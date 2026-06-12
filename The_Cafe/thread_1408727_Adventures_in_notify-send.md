---
title: "Adventures in notify-send"
date: 2010-02-16
forum: The Cafe
---

### Post by Aphoxema on 2010-02-16
As a not-terribly-adept-but-still-well-experienced user, I've been fooling around with some scripts involving the lib-notify executable, notify-send.

Here's my first success...

```
#!/bin/sh
user=`whoami`
pids=`pgrep -u $user gnome-session`
title="The time is now"
text="`date +"%R on %d, %A %B %Y"`"
timeout=60000
image="/usr/share/pixmaps/gnome-set-time.png"

for pid in $pids; do
        # find DBUS session bus for this session
        DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
        # use it
        DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
        notify-send -u low -t $timeout "$title" "$text" -i "$image"
done
```

as a file in /home/user/bin and

```
*/5 * * * * /home/user/bin/announcetime
```

In my per-user crontab.

What this does is every 5 minutes a short message telling me (well, any DBUS session) the time and date it currently is. This is useful to me because I'm playing with a minimal desktop and I'm very bad at keeping track of time between classes but any little movement catches my attention.

What's nice about this script (lifted from [http://gnome-hacks.org/hacks.html?id=82](http://gnome-hacks.org/hacks.html?id=82) ) is you can change $title and $text to any command or string you want.

What else does anyone thing notify-send would be useful for?

---

### Post by tgalati4 on 2010-02-16
I use it when waking my server.  I could modify it to detect a ping to determine when it's really up, but a simple timer works as well.

I also edited the default spacing and recompiled notify-osd so that it doesn't block buttons and scroll bars.  Hopefully this will be fixed in Lucid.  I have a deb file for Jaunty (32-bit) if anyone wants it.

#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Alive" "You can login now."
exit 0

---

### Post by Aphoxema on 2010-02-16
Good idea. I didn't like the way notify-osd in Karmic put anything besides the volume/brightness a little down so I got a .deb someone else had that reverted to the old method.

What I would *prefer* is to have everything go to the top and instead of new messages waiting to be displayed in the sole position they would position themselves below the currently displayed message... so long as it was not so many messages it would block off the entire right-hand third of my screen. This would be more like the mock-up video that was introduced before the whole thing even came out.

I *do* like the new notification system and I feel it is more sensible to have notifications be non-interactive, I just wish it were more configurable.

---

