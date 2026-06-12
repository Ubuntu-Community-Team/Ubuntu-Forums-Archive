---
title: "LAMP set up... Now What?"
date: 2008-04-13
forum: Server Platforms
---

### Post by wormser on 2008-04-13
I just got my first LAMP server set up on Gusty server.  This is just a learning exercise and I am looking for more things to do.  What else should I set up on the server?  Please post a HowTo with the suggestions.

Thanks

---

### Post by hyper_ch on 2008-04-14
how about a WoW-Server?

---

### Post by wormser on 2008-04-14
As in World of Warcraft?  Its not my style.  Plus this is a PII with 128mb.    Any other ideas?

---

### Post by hyper_ch on 2008-04-14
yeah, as in World of Warcraft...

Well, you have setup a mailserver yet?

---

### Post by wormser on 2008-04-14
I was going to.  What are some other good programs to run on a server?   Things like fail2ban and jailkit.  I am just trying to get an idea what other programs people use.

---

### Post by hyper_ch on 2008-04-14
depending on what you want to use I also install MySecureShell on it to give others chrooted SCP access...

I prefer HostsDeny over faile2ban...

---

### Post by Iowan on 2008-04-14
Nagios? (Netsaint?) DHCP server should already be there. Samba fileserver? Music/video?

---

### Post by Deathrend on 2008-04-14
I abuse my LAMP server, I set up Jinzora (I think that's the spelling) for media inside and out.

RoundCube Mail is another fun to use/set up application, if you're willing tot ake the time.  I used it as an IMAP client for Gmail for a while.

Nessus is a nice tool to have, if you have a decent sized home network, scans for holes/out of date OS patches/Default passwords, so on.

Be sure to install phpmyadmin, you can get it from apt, worth it's weight in gold if you're new to SQL.

SSLExplorer makes a very nice, free (Enterprise is foree for up to two users!) ssl VPN that runs on very little resources, works well with linux.

Webmin, If you're new to linux, webmin will make things a lot eiser, just be careful what you change, as you are editing system settings.

---

