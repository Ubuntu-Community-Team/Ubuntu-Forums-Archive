---
title: "DoS Protection"
date: 2010-08-26
forum: Security
---

### Post by ash369 on 2010-08-26
I've just recently created some game servers, they are all set-up and running perfectly. But, just recently the servers have started to lag for no reason at all. I'm pretty sure some kid is dosing the servers. IPTables is installed and i've blocked pretty much all the ports i don't use.

But, what i would like to know is. Is there anything else i can do to protect the server? Is there something i can use to monitor DoS attacks or find out the IP of who is doing it so i can block them on the firewall?

---

### Post by pytheas22 on 2010-08-26
[OSSEC]("http://www.ossec.net/") is useful for detecting different kinds of attacks.  [This thread]("http://ubuntuforums.org/showthread.php?t=213445") explains installing in on Ubuntu.

[snort]("http://www.snort.org/") is also very good for detecting network-based attacks.

And of course if you just want to monitor traffic to see if someone appears to be doing something nasty from a remote location, there's tcpdump (or Wireshark if you want a graphical interface).

---

### Post by cariboo on 2010-08-26
Have a look [here]("http://bipinkdas.blogspot.com/2008/09/prevent-dos-attack-in-linux.html"), the author has some example iptables rules that should help.

---

### Post by ash369 on 2010-09-01
Thanks for these links, i'll check them out.

---

