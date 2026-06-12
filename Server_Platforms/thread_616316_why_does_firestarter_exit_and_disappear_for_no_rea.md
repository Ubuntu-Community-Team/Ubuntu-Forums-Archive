---
title: "why does firestarter exit and disappear for no reason?"
date: 2007-11-18
forum: Server Platforms
---

### Post by LinuxSoundMan on 2007-11-18
can someone give me some info on this. firestarter always disappears for no reason. i even have the tray icon enabled with no luck. thanks

---

### Post by ddrichardson on 2007-11-18
Run it from a terminal and see if there is any error message.

---

### Post by LinuxSoundMan on 2007-11-18
ok i ran it from terminal and when it disappeared this was all it said...> Segmentation fault (core dumped)
 any ideas on this. thanks

---

### Post by ddrichardson on 2007-11-18
If its segfaulting your best bet is to make sure you have a version from the repositories that's been checked for your architecture, if so then contact the devs/report a bug.

---

### Post by HermanAB on 2007-11-18
In any case, whatever the reason, it doesn't matter, and that is why no-one bothers with fixing it...

Firestarter consists of two parts: The one part configures the firewall through iptables.  The other part watches the logs.  It is the useless log watching utility that exits.  You don't need that part and can just as well quit it.

Cheers,

Herman

---

### Post by ddrichardson on 2007-11-18
> **HermanAB said:**
> In any case, whatever the reason, it doesn't matter, and that is why no-one bothers with fixing it...

Firestarter consists of two parts: The one part configures the firewall through iptables.  The other part watches the logs.  It is the useless log watching utility that exits.  You don't need that part and can just as well quit it.

Cheers,

Herman
I couldn't agree more.

---

### Post by LinuxSoundMan on 2007-11-18
ok i see what youre saying. basically i configure it with the GUI and once i close it my configuration remains in tact? thanks for the info.

---

### Post by HermanAB on 2007-11-18
You can list the netfilter rules created by firestarter like this:
$ sudo iptables -L

If you read the iptables man page about 5 times, those rules may eventually make some sense.

Cheers,

Herman

---

### Post by ddrichardson on 2007-11-19
There's a few handy pointers [here]("http://www.openpages.info/iptables/").

---

### Post by infoseeker on 2007-11-19
I am having the same problem. I get this> ~$ sudo firestarter
Firewall started

***MEMORY-ERROR***: firestarter[7150]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

Just for your interest.

---

### Post by eric.dylan on 2007-11-20
Just for anyone who happens across this thread (as I had). There's a bug about this issue at:

[https://bugs.launchpad.net/firestarter/+bug/120445]("https://bugs.launchpad.net/firestarter/+bug/120445")

Upon visiting the Firestarter site at [http://www.fs-security.com/news.php](http://www.fs-security.com/news.php) it looks like it's no longer maintained by the original developers, the last news item is from July 2005. I checked the sourceforge mailing lists and there's a thread about this for November. 

According to the bug thread, some folks have had success by using the following at the command line:

> user@host:~$ G_SLICE=always-malloc sudo firestarter

---

