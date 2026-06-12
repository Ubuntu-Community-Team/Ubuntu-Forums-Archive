---
title: "removing 'trusted' keys ssh.."
date: 2010-02-19
forum: Security
---

### Post by mahela007 on 2010-02-19
Hi.. I've installed the ssh server on my Ubuntu desktop and the very first time I accessed the server from my laptop, it got a message asking me whether to permanently add the key of the server. After I added this, it gave me a message saying that the key had been permanently added. My question is how do I remove this key? I just want to know how to do this because I'm going to disable password based logins and I want to start anew.

---

### Post by giammy on 2010-02-19
> **mahela007 said:**
> Hi.. I've installed the ssh server on my Ubuntu desktop and the very first time I accessed the server from my laptop, it got a message asking me whether to permanently add the key of the server. After I added this, it gave me a message saying that the key had been permanently added. My question is how do I remove this key? I just want to know how to do this because I'm going to disable password based logins and I want to start anew.

Hi,

just remove file ~/.ssh/known_hosts

bye
giammy

---

### Post by CharlesA on 2010-02-19
> **giammy said:**
> Hi,

just remove file ~/.ssh/known_hosts

bye
giammy

That would remove all hosts with known keys. You can just edit that file and take out the line with the host you want to remove. Simpler to do tbh.

---

### Post by Kareeser on 2010-02-19
Now, on the other hand, the entries in known_hosts are hashed, so you can't make heads or tails of it - but you can figure out which entry is which by logging into the remote host (if it has changed). The error message will tell you which line.

Note that identical hosts with different hostnames will have different entries (i.e. "bob-1" and "192.168.0.101")

---

### Post by mahela007 on 2010-02-19
Sorry.. I didn't quite get that.

---

### Post by bodhi.zazen on 2010-02-19
If you do not want to delete all the hosts in ~/.ssh/known_hosts, then simply:

```
ssh-keygen -R hostname
```

Where hostname is the one you wish to remove.

Beware of the warning :

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle  attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f2:92:1d:da:81:2a:d7:16:0a:48:f0:43:20:1c:f4:b5.
Please contact your system administrator.
Add correct host key in /home/novak/.ssh/known_hosts to get rid of this  message.
Offending key in /home/novak/.ssh/known_hosts:1

If you see this, confirm the server host key has changed before you simply delete the key from known_hosts, otherwise you may not be connecting to the server you think you are ;)

---

### Post by joberly on 2010-02-19
Editing the known_hosts file does not change or remove the actual SSH key that is used for authentication. If you want to remove the key that is being used for that user, you need to take it out of ~/.ssh/authorized_keys on the host.

---

