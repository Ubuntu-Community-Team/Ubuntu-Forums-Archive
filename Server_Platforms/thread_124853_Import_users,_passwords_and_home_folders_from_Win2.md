---
title: "Import users, passwords and home folders from Win2000 server.."
date: 2006-02-02
forum: Server Platforms
---

### Post by bushtor on 2006-02-02
Hi,

Would it be possible to import the data mentioned in the header from a w2k server into a ubuntu distro?

If yes, where do I find some howto info or whitepapers on this issue

Thanks a lot for comments on this issue

regards

Tor

---

### Post by bjweeks on 2006-02-02
No, not at all.

---

### Post by bushtor on 2006-02-02
[QUOTE=bjweeks]No, not at all.[/QUOTE]

OK, does this mean that we cannot even import the user names (logon, real names etc) etc from AD?

I thought that I had read somewhere in a linux forumthat there are tools for migrating user data from windoze to linux, but maybe I had misunderstood.

Tor

---

### Post by dunstabulos on 2006-02-06
[QUOTE=bushtor]OK, does this mean that we cannot even import the user names (logon, real names etc) etc from AD?

I thought that I had read somewhere in a linux forumthat there are tools for migrating user data from windoze to linux, but maybe I had misunderstood.

Tor[/QUOTE]

You can do this using the net commands in samba, specifically vampire.

see [http://sambafr.idealx.org/samba/docs/man/Samba-HOWTO-Collection/NetCommand.html]("http://sambafr.idealx.org/samba/docs/man/Samba-HOWTO-Collection/NetCommand.html")

---

