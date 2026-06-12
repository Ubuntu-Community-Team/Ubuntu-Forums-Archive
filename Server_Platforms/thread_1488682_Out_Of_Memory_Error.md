---
title: "Out Of Memory Error"
date: 2010-05-20
forum: Server Platforms
---

### Post by PyrexKidd on 2010-05-20
I am running an FTP server using Ubuntu Server 10.04 LTS and vsftpd.  After about two hours the computer gives an 

```

"Out of Memory Error"  attempt to kill process PID
Killed PID

```

when this happens it runs very slow and I can't connect remotely via ssh or run any commands locally on the server.  Any suggestions on what might be causing this?  how do I go about trouble shooting this?  is there a way to encourage the system to write operations to swap or to keep them in memory?

Thanks in advance.

---

### Post by dudumomo on 2010-05-20
How much memory do you have ?
check your available memory with the command: free -m

It may be interesting to check which software is using a high amount of mem.

Your system was very slow because, I guess, it was swapping.

---

### Post by SlugSlug on 2010-05-20
```
df -h 
```
may also be useful

---

### Post by PyrexKidd on 2010-05-20
I have 4GB of ram on this server.  

here is the Kernel log from boot to reboot.  It started happening right about 8:13 today.

---

### Post by PyrexKidd on 2010-05-20
vsftpd is what is eating up all the memory.

---

