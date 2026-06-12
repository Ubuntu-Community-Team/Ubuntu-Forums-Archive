---
title: "SSH to server hangs after a while..."
date: 2009-07-17
forum: Server Platforms
---

### Post by afowler on 2009-07-17
Hello,

I set up a new Ubuntu server install using the defaults.  (plus Apache2 & SSH server)

However when I SSH in to the machine from my laptop (Ubuntu Desktop), if I don't type for a while, weird stuff happens...

1) Sometimes the connection becomes "laggy" and takes a few seconds to respond. But after a few moments, it wakes up and works fine.

2) Other times the session hangs entirely, and I have to force quite the gnome terminal.

Notes:

- In all cases, I can start a new SSH session with out any trouble.
- I can SSH just fine to my web host's machine. No problems.
- The machines are connected via a gigabit switch, and the server is not overloaded at all.

Any ideas?

Thank you,
:)

---

### Post by dragos2 on 2009-07-17
> **afowler said:**
> Hello,

I set up a new Ubuntu server install using the defaults.  (plus Apache2 & SSH server)

However when I SSH in to the machine from my laptop (Ubuntu Desktop), if I don't type for a while, weird stuff happens...

1) Sometimes the connection becomes "laggy" and takes a few seconds to respond. But after a few moments, it wakes up and works fine.

2) Other times the session hangs entirely, and I have to force quite the gnome terminal.

Notes:

- In all cases, I can start a new SSH session with out any trouble.
- I can SSH just fine to my web host's machine. No problems.
- The machines are connected via a gigabit switch, and the server is not overloaded at all.

Any ideas?

Thank you,
:)

cat /var/log/messages
tcpdump
ntop
iptraf
htop

Post some logs :D

---

### Post by afowler on 2009-07-20
> **dragos2 said:**
> cat /var/log/messages
tcpdump
ntop
iptraf
htop

Post some logs :D


Thank you for the help...

Can you be more specific as what I should look for / post?

The /var/log/messages file just shows a bunch of lines like:

Jul 20 07:46:30 UbuntuSvr -- MARK --
Jul 20 08:06:30 UbuntuSvr -- MARK --
Jul 20 08:26:30 UbuntuSvr -- MARK --
Jul 20 08:46:30 UbuntuSvr -- MARK --
Jul 20 09:06:30 UbuntuSvr -- MARK --
Jul 20 09:26:30 UbuntuSvr -- MARK --
Jul 20 09:46:30 UbuntuSvr -- MARK --


Thank you,
:)

---

### Post by afowler on 2009-07-24
anybody?

---

### Post by FakeOutdoorsman on 2009-07-24
Log into your server and then run:
```
tail -f /var/log/auth.log
```
This will show you auth.log as it gets updated.  Keep that window open and log in and see if you find anything interesting.

---

### Post by dragos2 on 2009-07-24
> **afowler said:**
> anybody?

Do verbose ssh and post the results.

---

