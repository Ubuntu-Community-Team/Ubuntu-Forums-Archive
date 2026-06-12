---
title: "SSH error: Bad packet length"
date: 2012-02-15
forum: Server Platforms
---

### Post by octopus22 on 2012-02-15
ssh [email]user@example.com[/email]
Bad packet length 1885434739.
Disconnecting: Packet corrupt

Server is up and running, web sites working ok, i can even chroot it using resque system.
All users got same error.

---

### Post by Grenage on 2012-02-15
OpenSSH is installed on the server (which is where I assume the problem lies).

What happens when you try and connect using:

```
ssh -1 *host*
```

---

### Post by octopus22 on 2012-02-15
Same story: Disconnecting: Bad packet length 1885434739

---

### Post by Grenage on 2012-02-15
Are you using openssh on the server?

---

### Post by octopus22 on 2012-02-15
Yes. 
Ubuntu server x64, ISP manager 4.4, LAMP, openssh, memcached, mongodb.

SSH stop working without any updates or installations from my side.
Have no idea what to check.

---

### Post by Grenage on 2012-02-15
While I've never seen this, reading suggests that data corruption is a possibility, so let's rule things out.  If you plug the server directly into a client PC (crossover cable), does it still happen?  If you don't have a crossover cable, do you have another switch or router that you can use?

---

### Post by octopus22 on 2012-02-15
This server is placed in data center, no router problems. Other connections with server is ok, just corrupted ssh.

I can chroot to get and look into any config, but don't know where to start from. Google doesn't help with that.

Tech support advice to make full reinstall and data migration, but this is last thing i want to deal with.

---

### Post by Grenage on 2012-02-15
Unfortunately I don't know what to suggest; the little information I found suggested routers/cables/etc as the faulty candidates.  Hopefully someone who has soon it will come by this post.

---

### Post by octopus22 on 2012-02-15
thank you for helping anyway. at least we know this is not ssl2 issue.

---

### Post by octopus22 on 2012-02-15
I can dig and publish any config or whatever on this machine.

---

### Post by Grenage on 2012-02-15
Are you able to SSH *from* the server to another machine?

---

### Post by octopus22 on 2012-02-17
Yes, server can make ssh connection to another machine without problems!

---

### Post by octopus22 on 2012-02-29
Finally, it was a rootkit with advanced shields and security. Config was OK, SSH was blocked in some other way.
Moving data to other server, clean install.

---

