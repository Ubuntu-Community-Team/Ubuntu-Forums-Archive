---
title: "lubuntu 18.10 slow shutdown"
date: 2018-08-01
forum: Ubuntu Development Version
---

### Post by VMC on 2018-08-01
It takes a minute or two to shutdown. Not always, but most of the time now.
ps status doesn't show any abandon process.
journalctl didn't reveal anything. I didn't look at kernel output yet.

Here's what I know. googling revealed cups-browsed.service, may cause this.
I "masked" it out.
Actually I "masked" out several unneeded services.

Another item is to change /etc/systemd/system.conf:
[I]DefaultTimeoutStartSec=10s
DefaultTimeoutStopSec=10s[/I]
 That fixed it 90% of the time.

Checking processes when there is immediate shutdown vs slow shutdown, are the same.

I'll wait a week or so before bug reporting to make sure. I reinstall every weekend.

If anyone has come across this in the past, let me know. I've searched and applied most of the fixes. Maybe I missed something.
You won't see the message output unless splash quiet is removed.

---

