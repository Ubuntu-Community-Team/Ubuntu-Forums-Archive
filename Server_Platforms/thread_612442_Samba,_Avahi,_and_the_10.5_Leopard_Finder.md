---
title: "Samba, Avahi, and the 10.5 Leopard Finder"
date: 2007-11-13
forum: Server Platforms
---

### Post by mcewen98 on 2007-11-13
How does samba (and remote desktop) on ubuntu automatically broadcast its presence without using an Avahi *.service file?

By default Leopard shows the samba share automatically in the finder with an icon of PC.  I can make it appear twice by adding the samba.service to /etc/avahi/services.  The same goes for the VNC service.  Both of these icons appear as the LCD indicating a mac server.

Can I either disable the automatic broadcasting of these services, or rename them so they appear differently in the OS X finder?  Remote desktop appears as "Remote Desktop" with no indication of the hostname, and the samba appears as just the hostname, with no indication that it's a samba file share.  I would like to change that...

Thanks!

---

### Post by frazze on 2007-12-27
I also found out this just a couple of hours ago... :) I get one (1) icon from the Samba server directly with the CRT image (PC Server). Another one (1) from the Avahi service file with the LCD Image (Mac Server). Grand total of two (2) icons for the one and same service. Strange.

This reply is partly to bump this issue as I'm also trying to get just one (1) icon for every service in Leopards Finder under Shared.

---

### Post by frazze on 2007-12-27
> **mcewen98 said:**
> How does samba (and remote desktop) on ubuntu automatically broadcast its presence without using an Avahi *.service file?Most likely from the smb/nmb combo. But I have to pass the technical explanation to someone else more experienced.> **mcewen98 said:**
> By default Leopard shows the samba share automatically in the finder with an icon of PC.  I can make it appear twice by adding the samba.service to /etc/avahi/services.  The same goes for the VNC service.  Both of these icons appear as the LCD indicating a mac server.Really odd this behaviour. I also found this out after a couple of hours fiddling around with all this. Got just one (1) icon for my Netatalk (afpd) service, but two (one from Samba and one extra from samba.service).> **mcewen98 said:**
> Can I either disable the automatic broadcasting of these services, or rename them so they appear differently in the OS X finder?  Remote desktop appears as "Remote Desktop" with no indication of the hostname, and the samba appears as just the hostname, with no indication that it's a samba file share.  I would like to change that...You can be more specific in the naming within the service file for avahi. Just read the man page.

---

### Post by smiler_jerg on 2008-04-29
I've also noticed this problem. I currently have three icons for the same server:
1) "Lilywhite Lilith", the Avahi service name for Samba **and** AFP
2) "lilywhite-lilit", the Samba NetBIOS (is it NetBIOS still?) name, announced by Samba itself to the browser server. This is a truncated form of the server's hostname (lilywhite-lilith).
3) "lilywhite-lilith", the AFP server displaying the hostname. This only appeared after manually connecting, but is now persistent.

One 'solution' I can think of is disabling NetBIOS name announcement in Samba. However, this would mean that Windows clients would not see it when browsing the network. Also, Mac OS X doesn't do this itself for the same reason.

So what does Mac OS X do? How does it know that two icons are the same server, but not when the server's Ubuntu? I suspected that the truncated hostname was causing the problem, but if others are also having the problem, perhaps not.

Maybe Avahi could/should send something else in the mDNS? I'll have a dig through the Avahi docs, but in the meantime, has anyone had success with this?

---

### Post by scragz on 2008-05-12
See this other post: [http://ubuntuforums.org/showthread.php?t=347019](http://ubuntuforums.org/showthread.php?t=347019)

Specifically add enable-dbus=no to /etc/avahi/avahi-daemon.conf

---

