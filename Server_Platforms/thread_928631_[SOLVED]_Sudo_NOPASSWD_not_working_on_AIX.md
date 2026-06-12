---
title: "[SOLVED] Sudo NOPASSWD not working on AIX"
date: 2008-09-24
forum: Server Platforms
---

### Post by satyendra on 2008-09-24
Hello,

I want to run a sudo command without entering the password using script on AIX server. I tried the following settings in /etc/sudoers 
<username>      ALL=(ALL)NOPASSWD:ALL -- This works fine

but below setting doesn't work 
<username>      ALL=(ALL)NOPASSWD:/tmp/<ScriptName>

I tried above stting with and without spaces but had no luck.

Can anyone please help me out with this...........

Thanks

---

### Post by cdenley on 2008-09-24
Are you adding that setting to the bottom of your sudoers file?

---

### Post by satyendra on 2008-09-24
Yes this setting is added to the end of the sudoers file.

---

### Post by cdenley on 2008-09-24
It seems to work fine for me.
```
cdenley ALL = (ALL) NOPASSWD:/usr/bin/whoami
```
```

cdenley@ubuntu:~$ sudo -K
cdenley@ubuntu:~$ sudo whoami
root

```
I don't know what else to suggest.

---

### Post by satyendra on 2008-09-24
I got it now . 
I was executng the script by using command 
#sudo su - "-c <scriptname>" 

Thanks a lot for your quick reply.

---

