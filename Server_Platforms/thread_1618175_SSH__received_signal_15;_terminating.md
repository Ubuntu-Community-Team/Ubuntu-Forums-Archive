---
title: "SSH:  received signal 15; terminating"
date: 2010-11-10
forum: Server Platforms
---

### Post by divided on 2010-11-10
What exactly does this mean?

Thanks in advance.

---

### Post by dapperdanny77 on 2010-11-10
that means that a process sends the SIGTERM (15) signal to the ssh process.

usually this happens when killing a process. 
>kill <processid> sends signal 15 to the process.

see kill -l for a full list of possible signals

---

### Post by divided on 2010-11-10
> **dapperdanny77 said:**
> that means that a process sends the SIGTERM (15) signal to the ssh process.

usually this happens when killing a process. 
>kill <processid> sends signal 15 to the process.

see kill -l for a full list of possible signals

Thanks for the answer.  I didn't know about the kill -l command, that really helps!

---

