---
title: "Putty SSH &quot;Server refused our key&quot; cannot connect with keys"
date: 2012-01-23
forum: Server Platforms
---

### Post by xioSlayer on 2012-01-23
[http://www.howtoforge.com/ssh_key_based_logins_putty]("http://www.howtoforge.com/ssh_key_based_logins_putty")
I have been following this guide mostly (with slight changes, like authorized_keys instead of authorized_keys2, etc)

However, I cannot SSH to my ubuntu server with key pairs generated from putty.  I used RSA 4096bit and a non-default SSH port (32000).

I'm getting "Server refused our key"  even though the public key was pasted into ~/.ssh/authorized_keys and my sshd_config is set to allow keys.

Any idea why I can only connect with my password still?

---

### Post by papibe on 2012-01-23
Take a look at this [video]("http://www.youtube.com/watch?v=ioGYnsxzL94") tutorial on how create keys in Putty, set them on the server, and connect to a server using them.

Hope it helps,
Regards.

---

### Post by pctx on 2012-01-23
Everything but this looks off:
```

PasswordAuthentication yes

**should read if using SSH key files:**
PasswordAuthentication no

```Since I have to use Windows (primary support @ work) you basically need to make sure that the copy and paste from your machine to the server has no spaces or extra characters from the putty-keygen file that gets created.

Easiest way to edit the pub or pri key files is to open them up with a text editor (in this case, I use Notepad++ but you can use notepad) and make sure you just copy the correct string.

If everything else is looking right, then the next step is to look at the actual .ssh permissions on if you have access to it.

Example:
```

user@foo~$ls -al
drwx------ user user 4096 2012-1-23 20:11 .ssh

```The user you are connecting as needs to have read permission to that file, otherwise you will get the key refused because it can't read the key file.  I remember running into that when I was first messing with SSH in my earlier life.

To make sure that user owns or controls that directory, you'll need to do a sudo chmod for read, write or execute permissions (usually 700 is the prefered default) and also sudo chown user:user on .ssh in order for that to reflect the updated ownership.

Also-- now that I see it, take off AllowRootLogin unless you want a headache. ;)  Always makes me squirm when I see that. :)

Hope that helps.
-A

---

### Post by xioSlayer on 2012-01-24
YES :]  thank you for that link Pabibe.  Apparently you are supposed to omit the public key comment at the end, I was copying it all.  Thank you :)


pctx I will take off AllowRootLogin... what sort of headache though?  i'll check the man page to see more about it.

---

### Post by pctx on 2012-01-24
Basically if your host gets compromised and you haven't hardened your server, you give them su access which allows them to control everything.

Best always to take that out. :)

---

### Post by xioSlayer on 2012-01-24
> **pctx said:**
> Basically if your host gets compromised and you haven't hardened your server, you give them su access which allows them to control everything.

Best always to take that out. :)

Ah ok thanks :]   The extent of my hardening is just iptables with some source IP specific rules...  I probably have much to learn XD

EDIT:  thanks for the help pctx.  I'm reading a Red Hat hardening tutorial now that a friend provided.  I'll try to find a more ubuntu oriented guide after i'm done with this.

---

### Post by pctx on 2012-01-24
A firewall (iptables, shorewall, ufw) is just part of the hardening.  It took me damn near a year to finish my Linux hardening script that I have now deployed on our production servers at the College I work at.

Read up and get used to reading.... and reading.... and reading.... and reading. :)

However, copying and pasting will become your new friend. ;)

---

### Post by plasmafusion on 2012-01-24
> **pctx said:**
> A firewall (iptables, shorewall, ufw) is just part of the hardening.  It took me damn near a year to finish my Linux hardening script that I have now deployed on our production servers at the College I work at.

Read up and get used to reading.... and reading.... and reading.... and reading. :)

However, copying and pasting will become your new friend. ;)
care to share? ;)

---

### Post by pctx on 2012-01-24
I can yes.  What's funny is that the document is only for the server hardening and I'm just beginning work on locking down the LAMP stack now.  What's funny is that you can seriously spend all your time worrying about 100% of the security but eventually you have to go with the 80/20 rule of getting most while still staying sane. :)

I'll see if my document (since it is internal) needs to be scrubbed any and then I'll post it in the server forum.  Hopefully we can get a discussion going (if there hasn't been one already) on good hardening practices.

---

### Post by xioSlayer on 2012-01-24
> **pctx said:**
> I can yes.  What's funny is that the document is only for the server hardening and I'm just beginning work on locking down the LAMP stack now.  What's funny is that you can seriously spend all your time worrying about 100% of the security but eventually you have to go with the 80/20 rule of getting most while still staying sane. :)

I'll see if my document (since it is internal) needs to be scrubbed any and then I'll post it in the server forum.  Hopefully we can get a discussion going (if there hasn't been one already) on good hardening practices.

oh awesome I would be interested in that as well :]

---

