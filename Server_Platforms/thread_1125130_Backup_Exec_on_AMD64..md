---
title: "Backup Exec on AMD64."
date: 2009-04-14
forum: Server Platforms
---

### Post by Grenage0 on 2009-04-14
Greetings all!

I've been attempting to get backup exec remote agent working on an Ubuntu x64 install here, with some limited success.  After some initial problems, I read through the [[COLOR="Blue"]following information[/COLOR]]("http://ubuntuforums.org/showthread.php?t=186128&page=2").


I'm at the final hurdle, but installing the agent returns one error message:

> /bin/rpm: Permission denied

This is obviously due to the package's RH roots, but I figured that creating the folder /bin/rpm and ensuring permissions would get round it.  Alas, I was clearly mistaken.

Has anyone else come across this issue, or might be able to suggest a course of action to take?

Russell.

---

### Post by Innom on 2009-04-14
Sounds like it's trying to execute a script called '/bin/rpm'.

It's probably trying to determine what packages are installed on the system, which is found by running /bin/rpm -qa on a RPM based server.

---

### Post by Grenage0 on 2009-04-14
That didn't occur to me, but it would explain the problem; thank you for that.  I find it surprising that the individuals in the other thread did not encounter this problem, but I guess I shall have to see what I can do to circumvent it.

Cheers again for your help.

Russell.

---

### Post by Grenage0 on 2009-04-14
Thank you, your observation was exactly what I needed :)

ln -s /user/bin/rpm /bin/rpm

Problem solved!

---

