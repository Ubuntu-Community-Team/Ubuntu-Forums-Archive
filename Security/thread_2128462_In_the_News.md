---
title: "In the News"
date: 2013-03-23
forum: Security
---

### Post by PsyclonJohn on 2013-03-23
Hello All,

So I was just reading the news and noticed there is a piece of malware going around in S. Korea called 'Jokra' which erases Linux partitions. I was wondering would it be possible for Ubuntu users to get this malware without running Root.

Thanks,

John

---

### Post by The Cog on 2013-03-23
According to this:
[http://www.symantec.com/connect/blogs/remote-linux-wiper-found-south-korean-cyber-attack](http://www.symantec.com/connect/blogs/remote-linux-wiper-found-south-korean-cyber-attack)
the malware resides on a windows box, and watches for anyone making ssh connections from the windows box to a linux box. Then if it can (if the ssh connection logged in as root) then it wipes the /kernel, /usr, /etc, and /home directories. 

Conclusion - don't ssh from windows boxes into linux boxes as root, especially not using mRemote. It's the windows box that you can't trust. Actually, I thought I read somewhere else that it also forwards the ssh login credentials to a server somewhere on the internet (presumably for later use by the baddies). So even using non-root ssh from a windows box is not safe.

Edit:
Two afterthoughts:
Firstly, this malware is remarkably dumb. If it can hijack root ssh connections like that, it would be much smarter to drop proper malware such as a backdoor than to simply wipe the target machine.
Secondly, Ubuntu is more vulnerable than most other linux's in that even if the user doesn't log in as root, the same password that's used in the ssh credentials can probably be used again with sudo to gain root. Most other linux distros would require a different password to gain root, although the malware could still do keyboard logging to find it.

---

### Post by PsyclonJohn on 2013-03-23
Ah, thank you for clearing that up for me!

---

### Post by Stonecold1995 on 2013-03-23
> **The Cog said:**
> According to this:
[http://www.symantec.com/connect/blogs/remote-linux-wiper-found-south-korean-cyber-attack](http://www.symantec.com/connect/blogs/remote-linux-wiper-found-south-korean-cyber-attack)
the malware resides on a windows box, and watches for anyone making ssh connections from the windows box to a linux box. Then if it can (if the ssh connection logged in as root) then it wipes the /kernel, /usr, /etc, and /home directories. 

Conclusion - don't ssh from windows boxes into linux boxes as root, especially not using mRemote. It's the windows box that you can't trust. Actually, I thought I read somewhere else that it also forwards the ssh login credentials to a server somewhere on the internet (presumably for later use by the baddies). So even using non-root ssh from a windows box is not safe.

Edit:
Two afterthoughts:
Firstly, this malware is remarkably dumb. If it can hijack root ssh connections like that, it would be much smarter to drop proper malware such as a backdoor than to simply wipe the target machine.
Secondly, Ubuntu is more vulnerable than most other linux's in that even if the user doesn't log in as root, the same password that's used in the ssh credentials can probably be used again with sudo to gain root. Most other linux distros would require a different password to gain root, although the malware could still do keyboard logging to find it.
The malware wasn't dumb.  It's purpose was to disable the SK broadcasting (or something like that), not to set a backdoor.

---

### Post by maglinu on 2013-03-24
It also appears from one of the avast blogs that for the Windows host exploit to succeed DEP had to be disabled on the target machines.

---

