---
title: "Jabber server"
date: 2005-07-08
forum: Server Platforms
---

### Post by opi on 2005-07-08
Hi guys! I'm running a Ubuntu server and I would like to know if someone here has some experience with setting Jabber server? Server I use normally gets down to often nowdays, so I decited to bring this thing home. 

Any general tips on daemons, useful tools and administration?

---

### Post by sugna on 2005-07-26
Hi there.

recently I managed to set up a local Jabber server on my home LAN by following the Wiki guide at [https://wiki.ubuntu.com/SettingUpJabberServer?highlight=%28jabber%29%7C%28server%29](https://wiki.ubuntu.com/SettingUpJabberServer?highlight=%28jabber%29%7C%28server%29)

It was very easy and worked just fine . . . until I had to reboot the server.  Now I can't get any Jabber clients to connect to the server, even though jabberd appears to be running properly and the config files are just as they were when it was working.  I'm completely stumped as to what might be wrong.  Oh well, it was great while it lasted . . . .

---

### Post by circlecast on 2005-08-05
Well dont feel bad I am having problems with Jabber also
 ](*,)

---

### Post by sugna on 2005-08-05
Oh, I forgot to report that I got it working after all.  I must have said it in another thread.

Basically, I realised that Samba also wasn't working properly, as I could not access shared drives from my Windows computers.  So I restarted Samba, which fixed the shared drive problem . . . and, for some reason fixed the jabber problem too.

So I'm happy that it is working again, but am left with two questions:

1) Why did I have to restart samba?  Shouldn't it have initialised properly at boot?

2) More importantly, what on earth does samba have to do with Jabber???

---

