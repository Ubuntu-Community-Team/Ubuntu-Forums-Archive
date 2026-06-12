---
title: "SSH Access from anywhere"
date: 2013-09-03
forum: Server Platforms
---

### Post by Vilsol on 2013-09-03
So I have just installed the ubuntu server 13.04 and when I was installing it I checked that I want SSH to be installed with it.
Now when I want to test it, I can't access SSH from anywhere, not even from lan, it just simply says Incorrect Password no matter what.
But when I use ssh localhost on the actual server, then it allows me to connect and the password is just fine.
I have checked the ssh_config and it has: "Hosts *" and in the sshd_config there is  "PermitRoot yes" (or something like that), which means I should be able to access it...

---

### Post by Vilsol on 2013-09-03
Oh my god, this was the stupidest mistake I have ever made.
On my console, when i press SHIFT + 2 it makes "
But in my computer it is @
I am so ashamed of myself

Please lock this topic.

---

### Post by Habitual on 2013-09-03
Chalk it up to "Experience".

---

### Post by kpothi on 2013-09-04
Hi Vilsol,

You can mark this thread as solved, using the thread tools (please just search for the term "thread tools" in this page, you'd see a dropdown menu).

---

### Post by markbl on 2013-09-05
I don't understand why anybody would set "PermitRootLogin" to yes, particularly on a Ubuntu box where root account login is disabled by default anyhow. Users should ssh in using their own account (so you can see in the log files who it is at the very least!), and then use sudo. If you want to run root scripts remotely then set "PermitRootLogin without-password".

---

### Post by CharlesA on 2013-09-05
> **markbl said:**
> I don't understand why anybody would set "PermitRootLogin" to yes, particularly on a Ubuntu box where root account login is disabled by default anyhow. Users should ssh in using their own account (so you can see in the log files who it is at the very least!), and then use sudo. If you want to run root scripts remotely then set "PermitRootLogin without-password".

It is set to yes by default.

---

