---
title: "Permission denied (publickey). error"
date: 2017-02-24
forum: Server Platforms
---

### Post by recharde on 2017-02-24
When i run #ssh root@my _ip i got this error, "Permission denied (publickey)" can anyone help me, its urgent.:(

---

### Post by QIII on 2017-02-24
First -- never allow root login to your server over SSH.  Don't.  Do.  It.

Second -- don't be root on your client and SSH to your server.  Don't. Do. It.

In fact, Ubuntu comes with root disabled by default for a reason.

So.  Tell us how you set up SSH on the server.  Have you taken a look at [this wiki entry]("https://help.ubuntu.com/community/SSH")?  There are some good links there.

My first guess would be that you generated your keys while logged in as your normal user, but you are trying to log in from your client as root into the root account on your server.

---

### Post by wildmanne39 on 2017-02-24
*Thread moved to **Server Platforms**.*

---

### Post by recharde on 2017-02-24
i know that never give root access, but i face this type of problem please tell me solution. 
i just install OpenSSH and configure some in etc/ssh/sshd_config or i cant do nothing. But i really cant understand what is public key and how i setup it.

---

### Post by DuckHook on 2017-02-24
I suspect that English is not your native language. No problem with that at all. However, we are not mind-readers. It is impossible to make out what your "problem" is. Pleading for help without any information is useless.

QIII has asked you a question that must be answered before any further help can be given. Please answer him.> **QIII said:**
> &#8230;Tell us how you set up SSH on the server.

---

### Post by recharde on 2017-02-24
I just Install SSH on server like
1. # apt-get install openssh-server
2.# nano /etc/ssh/sshd_config then i change MaxAuthTries 3 and AllowUsers my_username RSAAuthentication yes PubkeyAuthentication yes
3.# service ssh restart

or nothing then i got this error

---

### Post by cariboo on 2017-02-24
You missed one of the must important parts. Generate the keys on the system you want to use when you ssh into another system:

```
ssh-keygen -t rsa
```

Once the keys have been generated copy them to the target system using the following command:

```
ssh-copy-id user@target
```

where target is the system you want to ssh into and user is your normal user, follow the prompts, as it will tell you what to do from there.

---

### Post by recharde on 2017-02-24
Hello, [URL="https://ubuntuforums.org/member.php?u=77104"][B][COLOR=#990303][B]cariboo 
[/B][/COLOR][/B][/URL]when i run #ssh-copy-id user@target i got below error. 
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
Permission denied (publickey).
one thing i can explain that i have use, user as my_local_machine and target as server ip, is it ok or not

---

### Post by howefield on 2017-02-24
Did you also disable password logins on the machine being ssh'ed into ?

---

### Post by recharde on 2017-02-24
yes, i make it disable.

---

### Post by howefield on 2017-02-24
So you have disabled password authentication and then setup key authentication except that you have no key on the machine being ssh'ed into ?

Sounds like you have locked yourself out of the machine and will have to find an alternative way to get the keys copied over.

---

### Post by DuckHook on 2017-02-24
A further note:

From your posts, it seems that you continue to do everything using root. This is bad practice and may be one of the reasons you are running into problems. You should be SSH-ing into you server (and creating keys for it) using your normal unprivileged account. If you are doing so as root, then you are creating your keys under the wrong account and trying to log in under the wrong account.

---

