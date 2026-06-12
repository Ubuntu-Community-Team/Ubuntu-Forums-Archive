---
title: "Jabber server stopped working after reboot"
date: 2005-07-26
forum: Server Platforms
---

### Post by sugna on 2005-07-26
Hi.

I recently setup a jabber server for my home LAN by following the wiki [https://wiki.ubuntu.com/SettingUpJabberServer?highlight=%28jabber%29%7C%28server%29](https://wiki.ubuntu.com/SettingUpJabberServer?highlight=%28jabber%29%7C%28server%29).

It worked fine until the server had to be rebooted after an unexpected power cut.  The jabberd daemon is running, the right ports are open and listening, and the config files are exaclty as they were before (unless they have somehow changed without my input).  But now I can no longer log onto the jabber server from the other computers on my LAN.  The network connection is healthy, since I can still connect to the server with VNC, etc.

Can anyone give me some hints about what might have gone wrong?  I was so glad to get it working but am now very frustrated that it has inexplicably stopped.

Thanks.

---

### Post by sugna on 2005-07-26
OK, I've got it working again.

I noticed that I couldn't access the shared folders on the server from my Windows cpus, so I decided to do a samba restart.  That got the shares working again and, mysteriously, got the Jabber server working again, too.

So my question is now this:  What the #@%! does Samba have to do with Jabber?

(And why did I have to restart samba anyway -- isn't that initialised by default when you boot up??)

---

