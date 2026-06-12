---
title: "can't get sshd to work..."
date: 2006-02-23
forum: Server Platforms
---

### Post by KevlarGurra on 2006-02-23
Hi!

I can't ssh to my Ubuntu comp from the local network (it says network connection timed out). It is possible to ssh to it from itself which means sshd is running (I suppose?). It is also possible to ping the Ubuntu computer and I am currently using it as a router which works perfectly.
Why doesn't it work.....?

---

### Post by Iowan on 2006-02-23
Verify that you have the SSH server installed.  IIRC, I had the same issue.

OOPS... if you can connect to it from itself, it must have both halves...

---

### Post by uopjohnson on 2006-02-23
How did you set up the router?  It is possible that you did not allow connections to the router from machines on the network, or you set the wrong interface as internal so it is blocking connections from your local system.  What hapend if you run ssh -v user@host this will give you verbose error output.

---

### Post by btdown on 2006-02-23
I believe you need to edit an option in one of the config files to allow remote logins. Try looking in /etc/ssh<something> and I think the option is allow remote logins or something else thats obvious...
 
I would be able to tell you the exact filename but Im currently locked out remotely right now... ;(

---

### Post by Kurt` on 2006-02-23
Hi,

I just did a clean install of Kubuntu today, and apt-get install'ed sshd.

With the default configuration, I was able to ssh into my other machine, and ssh back into this one just fine.

Perhaps you have Firestarter or some other firewall disallowing traffic? Are the 2 machines on the same subnet? ;)

---

### Post by KevlarGurra on 2006-02-23
Thanks for your answers!
I was using dhcp but I switched to static ip's instead...and now I can ssh into the Ubuntu comp! I don't know why, apparantly there's some problem with sshd and dhcp...

---

### Post by uopjohnson on 2006-02-23
No.  There is no problem with dhcp and ssh.  The only thing I can thin of here is that you were trying to ssh into the wrong IP and now that it is static you were able to get it running.  Either that or you changed somehting else in the process of changing to static IP....
As long as it works and you are happy that is great, I just wanted to add this for anyone looking at this thread later.

---

