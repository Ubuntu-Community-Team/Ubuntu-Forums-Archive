---
title: "Honeypot with Rootkit"
date: 2008-01-25
forum: Server Platforms
---

### Post by hoffmannick on 2008-01-25
Hello, I'm currently setting up a honeypot on a vmware virtual disk.  I want to install a rootkit into the honeypot so I can guarantee my own access to the box at all times.  I would also like to have keylogging ability among other things.  

Is there any good rootkits for linux that will install into ubuntu?  I've tried setting up Adore and SucKIT but none of which are compiling correctly.  Sebek doesn't seem to make friends with the kernel.  ( I should also put in a side note, that the compile errors aren't due to not having build-essential, libc6-dev, etc, etc, installed)

Does anyone have suggestions or even better, a tutorial :)

Thanks!
-Nick

---

### Post by HermanAB on 2008-01-25
No, install OpenSSL using Synaptic and run sshd on port 22.

Cheers,

Herman

---

### Post by hoffmannick on 2008-01-26
Thanks, but I'm not sure that has a solution that I'd be looking for.  The purpose of the honeypot is to remain vulnerable, while locking down or making a secret account into the box, I don't think that ssh and ssl will provide the control that I would like over it.  Making a local account on the box will give them access to passwd and shadow, there would be nothing from them manually editing, or running john on it.  Not to mention that ssh connections would show up in ps or who, so someone could potentially (with some privilege escalation) get into the box and kill my connection.  I would need something (like a rootkit, or kernel based trojan) that could hide all my connections to the box and show anything.  

It is my understanding that tools like sebek can be discovered by lsmod, but even so, they cannot be removed by rmmod.  This is something that I'd be more interested in.  With a tool like this, I don't even have to log into the box, It can just phone home to me on some udp connection.  Sounds much nicer than trying to worry about all the above mention processes.

---

### Post by nfox on 2008-06-07
Tutorial or it didn't happen. I'd like to see what you did with that/

---

### Post by hoffmannick on 2008-06-07
What do you mean?  Tutorial or it didn't happen?

---

