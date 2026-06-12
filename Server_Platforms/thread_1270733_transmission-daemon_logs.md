---
title: "transmission-daemon logs?"
date: 2009-09-19
forum: Server Platforms
---

### Post by android6011 on 2009-09-19
Are there logs for transmission-daemon? I am trying to see if blocklists are working. I set them as enabled in /etc/transmission-daemon/settings.json, and I downloaded the level1 file to /etc/transmission-daemon/blocklists . I would also just like to see any other errors that appear. Any info would be great. Thanks

Edit: also, when i upload/add torrents from the webgui where are they stored on the system? I have been unable to find them

---

### Post by MechaMechanism on 2009-09-20
> **android6011 said:**
> Are there logs for transmission-daemon? I am trying to see if blocklists are working. I set them as enabled in /etc/transmission-daemon/settings.json, and I downloaded the level1 file to /etc/transmission-daemon/blocklists . I would also just like to see any other errors that appear. Any info would be great. Thanks

Edit: also, when i upload/add torrents from the webgui where are they stored on the system? I have been unable to find themDon't that suck.  You would think that Transmission-Daemon would be setup by default to log to syslog, but noooo, it does no logging at all by default.  However to be fair, there really is not very much useful information to log.  Just when torrent files were added, deleted and when downloads completed and by which user account.  What Transmission-Daemon really needs is for the web interface to email or sms you when the tracker spits out an error.  Also see this directory "/var/lib/transmission-daemon" for your torrents.

---

### Post by Charles Kerr on 2009-09-22
There's an open ticket in the Transmission bug tracker for the daemon to do proper logging to syslog.  My best guess is that it'll be in 1.80.

Until then, one workaround is to run transmission-daemon in the foreground (with the -f argument) and pipe the output to a file of your choosing.  Ugly, but better than nothing.

---

### Post by MechaMechanism on 2009-09-22
> **Charles Kerr said:**
> There's an open ticket in the Transmission bug tracker for the daemon to do proper logging to syslog.  My best guess is that it'll be in 1.80.

Until then, one workaround is to run transmission-daemon in the foreground (with the -f argument) and pipe the output to a file of your choosing.  Ugly, but better than nothing.Awesome an actual developer, thanks for the workaround, but I will wait until 1.8 or later.

---

