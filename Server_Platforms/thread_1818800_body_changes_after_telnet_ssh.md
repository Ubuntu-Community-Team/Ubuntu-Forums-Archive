---
title: "body changes after telnet ssh"
date: 2011-08-05
forum: Server Platforms
---

### Post by redelek on 2011-08-05
Good morning,
 I compiled a new OpenSSH 5.8p2. I would like to get rid of the string that will show is how to telnet to your computer
 ```
telnet localhost 22
 Trying localhost ...
 Connected to localhost
 Escape character is'^]'.
 SSH-2.0-OpenSSH_5.3p1 << HOW TO CHANGE !!
 Connection closed by foreign host.
```

 Does anyone of you knows where this file can be found?

 I should be grateful for your help

Best regards
Redelek

---

### Post by dinu90 on 2011-08-05
The string you are referring to is builtin the sshd binary. If you still get the old string then it means you either did not install the new sshd properly, you did not restart sshd after installing the new one or you installed the new sshd in some other place.

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by redelek on 2011-08-08
Yes openssh install manually, and this is what you can where is this file kept records.
 SSH works fine, just do not know how to find this entry.

---

### Post by Wim Sturkenboom on 2011-08-08
> 
just do not know how to find this entry

```

sudo find / -name "*" -exec grep -H SSH-2.0-OpenSSH_5.3p1 {} \;

```
This will digg through all files in your system and display those containing the requested string.

It might take some time ;)

---

### Post by redelek on 2011-08-08
Thank you for your help

---

