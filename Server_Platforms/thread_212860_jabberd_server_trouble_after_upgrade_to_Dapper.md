---
title: "jabberd server trouble after upgrade to Dapper"
date: 2006-07-10
forum: Server Platforms
---

### Post by ivomans on 2006-07-10
I'm running jabberd, including jabber-msn/icq/jit. Used to be running fine until I upgraded to Dapper a few days ago. 

When I login with psi/gajim/etc on a just started deamon everything works fine. When I then logout and wish to login again I cann't connect anymore, not shortly after, but also not next day.

When I then give a 'sudo /etc/init.d/jabber stop' the process does not stop. I need to do a 'sudo killall jabberd jabberd-jit' to stop the processes. If I then start a new 'sudo /etc/init.d/jabber start' I can login again.

Very annoying, especially since this happens to every user trying to use my server.

Hope somebody could suggest where to find a solution for this.

Kind regards,
Ivo Mans.

From /var/log/jabber/error.log:
> 20060710T17:16:51: [notice] (-internal): initializing server
20060710T17:16:56: [notice] (-internal): initializing server
20060710T17:16:56: [notice] (aim.mans-manik.com): AIM-Transport starting up for
instance aim.xxx.xxx...
20060710T17:16:57: [alert] (-internal): Jabberd started.
20060710T17:16:57: [notice] (-internal): initializing server
20060710T17:16:58: [warn] (jit/wp_client.cpp:659): Buffer pointer not at end aft
er parsing FLAP was: 0x86 should be: 0xfc on channel 0x2

But these messages don't prevent my initial login.

From /var/log/jabber/record.log:
> 20060710T17:16:54 [email]xxx@xxx.xxx[/email] login ok 10.1.2.1 Psi
20060710T17:16:58 sessionstart   ;xxx@xxx.xxx;

---

### Post by lamego on 2006-07-10
If you are using jabberd1 you should be looking into upgrade to jabberd2 it is more reliable.

---

### Post by ivomans on 2006-07-10
> **lamego said:**
> If you are using jabberd1 you should be looking into upgrade to jabberd2 it is more reliable.

I'm using the jabber 1.4.3-3ubuntu1 so far.
Does this jabberd2 also work with the jabber-msn (etc.) packages? I don't see a 'jabberd2-msn' in the package list.

---

### Post by mazirian on 2006-07-10
I run a jabberd2 server under Debian and I am quite happy with it.     The transports for legacy IM networks you are using are available in the form of Python scripts (search for pyAIMt and pyICQt).  They seem to be pretty reliable.  I haven't yet had the need or opportunity to install transports for Yahoo or MSN.

---

### Post by ivomans on 2006-07-18
Been considering to switch to jabberd2 or ejabberd. But so far I still like the simple configuration-file system  of jabberd most.

Found out my problem was already filed as a bug: [https://launchpad.net/distros/ubuntu/+source/jabber/+bug/35953](https://launchpad.net/distros/ubuntu/+source/jabber/+bug/35953)

The mentioned workaroud in the bug-comments (forcing a downgrade to 1.4.3-3) solved my issue.

---

