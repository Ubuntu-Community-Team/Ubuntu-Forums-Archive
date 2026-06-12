---
title: "Server has been hacked"
date: 2010-12-12
forum: Server Platforms
---

### Post by fergz on 2010-12-12
Hi on my linux server i think somebody has gained access and now a few sites on it is trying to point to the address below can anyone advise me on how to fix it?

[noparse]http://iritirlast0.co.cc/bl/show.php?key=92e93d0553cdb3c89d7d397457811f6d&u=parazit/[/noparse]

Just now thankfully google blocks it with a red box saying its a bad page or else it would install stuff on computer.


Thanks

---

### Post by restorator on 2010-12-12
Restore from your last known clean backup. You do have backups right?

---

### Post by CharlesA on 2010-12-12
> **restorator said:**
> Restore from your last known clean backup. You do have backups right?

Either that or backup yer stuff and reinstall.

---

### Post by HermanAB on 2010-12-12
Howdy,

There is only one sure solution:
[INDENT]Backup your data and re-install.[/INDENT]

Then, to ensure that it doesn't happen again:
[LIST]
[*]Use proper passwords for ALL acounts - at least 9 characters with complexity or at least 12 characters without.
[*]Do not use FTP.
[*]Do not use VNC.
[*]Set SSH to accept keys only - no password logins.
[/LIST]

---

### Post by fergz on 2010-12-15
Thanks guys just wondered if there was a easier option to it to save me installing linex and everything again

---

### Post by dtfinch on 2010-12-15
If you can determine that they probably got in through a website exploit (like an outdated bulletin board), and ran as a limited user (like www-data) rather than root, it might be enough to take it offline, fix the exploits, and clean up the mess. Even with a clean install you'd still have to fix any website vulnerabilities or they'd just exploit it again.

You might look at /root/.bash_history for signs of whether they actually got a root shell, though it'd be trivial for them to erase the history.

---

### Post by mr clark25 on 2010-12-15
> **HermanAB said:**
> Howdy,

There is only one sure solution:[INDENT]Backup your data and re-install.[/INDENT]Then, to ensure that it doesn't happen again:
[LIST]
[*]Use proper passwords for ALL acounts - at least 9 characters with complexity or at least 12 characters without.
[*]Do not use FTP.
[*]Do not use VNC.
[*]Set SSH to accept keys only - no password logins.
[/LIST]


+1

also, make sure you move ssh to a different port. the higher the (port) number the better.

---

### Post by CharlesA on 2010-12-15
> **mr clark25 said:**
> +1

also, make sure you move ssh to a different port. the higher the (port) number the better.

It's security thru obscurity, at best.

The only real thing moving SSH to a different port does, it cut down on data in the logs. If someone really wanted to get in, they'd scan the host and see what post SSH was running on.

I've been running SSH on port 22 using keys only and haven't had any problems. The only way I would run SSH as password auth is with an account with a password of 15-30 characters.

---

