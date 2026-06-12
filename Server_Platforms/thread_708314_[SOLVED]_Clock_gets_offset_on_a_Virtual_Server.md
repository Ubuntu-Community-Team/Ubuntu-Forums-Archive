---
title: "[SOLVED] Clock gets offset on a Virtual Server"
date: 2008-02-26
forum: Server Platforms
---

### Post by trymbill on 2008-02-26
I've got a problem ...

I've got Ubuntu 6.06 Server running on Virtual Server 2005 R2 SP1 from M$ and my clock on Ubuntu gets offset from normal time quite a lot.  I've tried running cron jobs for ntpdate ntp.ubuntu.com and that fixes it, but it's not enough.  I really need my clock to work 100%, like it should if I was running it on a normal computer.

I've already added "clock=pit" (or something like that .. don't remember :P) and that fixed it a lot, but not enough.

Can some one here explain to me why this is happening and how I can fix it?

---

### Post by faulkes on 2008-02-26
Consider using the ntp package instead of ntpdate.

ntpd (the daemon) runs constantly and adjusts the time as frequently as needed in
order to keep the clock sync'd.

```

sudo apt-get install ntp

```

Faulkes

---

### Post by trymbill on 2008-02-26
Ok, I will ... thank you! :)

---

