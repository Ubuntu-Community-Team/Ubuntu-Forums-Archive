---
title: "Securing the OpenSSH server"
date: 2006-11-03
forum: Server Platforms
---

### Post by nadamsieee on 2006-11-03
Here is what I changed in **/etc/ssh/sshd_config**:

```
# Only use protocal 2 (more secure)
Protocol 2

#Disable root login. Users have to su to root
PermitRootLogin no

#Turn on Public key authentication
PubkeyAuthentication yes

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

# Don't allow graphic applications
X11Forwarding no

```

Comments? Suggestions?

I also had to enable the ChallengeResponseAuthentication option, in order to log-in:

```
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes
```

---

### Post by Chayak on 2006-11-05
Change it to a nonstandard port.  That will help you a lot in avoiding bots on the net trying random bruteforce attempts on your server.
[http://www.runyourownserver.org/]("http://www.runyourownserver.org/") has some good tips on locking down services.

---

### Post by adrianhensler on 2006-11-05
> **Chayak said:**
> Change it to a nonstandard port.  That will help you a lot in avoiding bots on the net trying random bruteforce attempts on your server.


Just a quick post to second that suggestion.  I went from hundreds of attempts per day to practically none when I changed to a nonstandard port.  Security through obscurity might be a bad model in general; but it certainly can reduce the bulk attempts.

---

### Post by Randomskk on 2006-11-05
I use the standard port, but I restrict it to my local network IP - the port isn't forwarded to the public anyway, or even to the top step of my network, and even then it's only allowed to my ip, which is given to me based on the MAC address from the DHCP server.
Look into /etc/hosts.allow to set this kinda stuff up.
802.1x authentication would make this setup even better.

---

