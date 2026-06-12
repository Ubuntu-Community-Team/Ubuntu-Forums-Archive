---
title: "ssh/sftp subsystem question"
date: 2008-02-13
forum: Server Platforms
---

### Post by BaseRunner on 2008-02-13
Hello,

I was trying to use the sftp subsystem by invoking the ssh client like this: "ssh -s <target> sftp"
Of course I could use the sftp client, I know;-)
Anyway, the sftp-server is started as expected but I am not able to talk to it using the sftp commands (ls, put, get etc.).
strace shows that the commands arrive in clear text there; contrary to a normal sftp sessions where the read() shows binary data.
Can anyone tell me why this is? Or am I completely wrong and overlooked something in the man pages?

Many thanks!
keep running

---

### Post by crouton on 2008-02-13
What exactly are you trying to do by using the remote invocation flag?

---

### Post by BaseRunner on 2008-02-14
Oh, yes. I recognized that the sftp client always returns 0 in batch mode  even if the transfer fails so I cannot use the return code for error checking. The plan was now to use the stderr output to check if something goes wrong. Unfortunately the motd of the server is written there as well. Now some older sftp clients cannot be started in quiet mode so I wanted to use the ssh client in quiet mode starting the sftp subsystem on the server side and perform the commands with a here script.
Quite a mess, I know. If you have any suggestions pls. let me know!
Thanks a lot.

---

### Post by crouton on 2008-02-14
It sounds like you are trying to automate the sftp process such a local script is run, and that any errors are reported and parsed on the local side.  This sound correct?

---

### Post by BaseRunner on 2008-02-15
Yes, that hits the bull's eye! Do you have any recommendations?
Many thanks,
Batta

---

### Post by faulkes on 2008-02-15
> **BaseRunner said:**
> Yes, that hits the bull's eye! Do you have any recommendations?
Many thanks,
Batta

You may want to consider using scp with keys as an alternative.

Faulkes

---

### Post by BaseRunner on 2008-02-15
Ah, that helps a lot! :lolflag:

---

