---
title: "Ten second delay between username and password on SSH"
date: 2006-09-21
forum: Server Platforms
---

### Post by timelord726 on 2006-09-21
A strange problem has recently appeared on my server.  I have configured a new Ubuntu 6.06 web server with SSH, and the server runs well.  However, there is a strange problem when I attempt to log in to the server via SSH.  After connecting, it asks me for my username, which I enter.  Once I enter the username, it seems to pause for around 10 to 15 seconds, and then presents the password prompt as normal and allows me in.  It's not slow once I've logged in, and it makes the connection quickly.  This happens every time I connect.  Any idea what could be causing this?  Thanks!

---

### Post by paul.maddox on 2006-09-21
Sounds like a DNS problem to me.

It may be trying to perform a reverse dns lookup on your machine and failing.

Try ssh'ing the box with a few extra levels of verbosity:

ssh -v user@box

or even

ssh -vv user@box


See what extra information you can get

---

### Post by MJN on 2006-09-21
I agree, and if you try putting the IP (and name) of your client machine in the server's /etc/hosts file then you may well find the delay disappears.

Mathew

---

### Post by timelord726 on 2006-09-22
> **MJN said:**
> ...if you try putting the IP (and name) of your client machine in the server's /etc/hosts file then you may well find the delay disappears.
Excellent suggestion!  Cleared it right up.  Thank you very much!  :D

---

### Post by MJN on 2006-09-22
Paul ought to take the credit... he highlighted the potential problem and I did the easy bit of suggesting the workaround! ;-)
 
I wonder why it does the reverse lookup anyway? To increase the level of detail in the log perhaps? (I'm not at my machine right now so can't check what is/isn't logged)
 
Mathew

---

### Post by jinacio on 2006-12-12
quick tip for server:

echo "UseDNS no" >> /etc/ssh/sshd_config
/etc/init.d/ssh restart

---

