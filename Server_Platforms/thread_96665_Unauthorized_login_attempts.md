---
title: "Unauthorized login attempts"
date: 2005-11-29
forum: Server Platforms
---

### Post by kozimodo on 2005-11-29
I noticed an inordinate amount of hard drive activity on my server this morning so I checked auth.log.  1) it was larger than usual and 2) when I looked at it, it was filled with failed login attempts.  Moreover, when I "tail -f"ed it, I could see that the attack was ongoing.  I have not changed the root password.  Is this anything to worry about?  Should I install something like DenyHosts?

Thanks,
kozimodo

---

### Post by psoleko on 2005-11-29
Are you running an SSH server with password authorization? If you are I suggest you change to Key based authetication.

---

### Post by kozimodo on 2005-11-29
That's one solution that I've thought about but I'm a little reluctant because of the logistics of exchanging keys.  I have changed the port that sshd listens to.  I guess long term I will have to do the key exchange thing...

---

### Post by invalid on 2005-11-29
You can add a line in /etc/hosts.deny file in the following format:```
ALL: xx.xx.xx.xx
```to prevent access from a given IP address. This will at least stop further attempts from that particular address.

Cb

---

### Post by wrtrdood on 2005-11-29
[QUOTE=invalid]You can add a line in /etc/hosts.deny file in the following format:```
ALL: xx.xx.xx.xx
```to prevent access from a given IP address. This will at least stop further attempts from that particular address.

Cb[/QUOTE]


That's what DenyHosts does and it works like a charm.  It's a great solution when you need your SSH.  Also, be sure you set *PermitRootLogin* to no in /etc/ssh/sshd_config.

---

### Post by LordHunter317 on 2005-11-29
If your passwords are strong, then just ignore them.  Strong meaning reasonably long (>=8 chars) and symbols and numbers.

Passwords of the form '10$coffee' tend to fufill this nicely.  Or '1_car$exp'  Or any other short phrase, realy.  Plus, they're really easy to remember.

---

### Post by thewanderer on 2005-12-01
To reinforce what has already been said:

* If you are running ssh make sure all your passwords are of sufficent length and randomness. These brute force password attacks, run through a dictionary of passwords. If its not in the dictionary they wont get in.

* Running ssh on a different port is a good idea too. Most of the brute force ssh scanning is only hitting port 22.

* You can deny the hosts as mentioned. It is also interesting to look where they are coming from... use [http://www.geektools.com/](http://www.geektools.com/) - whois. 99% of the time the attacking hosts have been compromised. I have found government systems, universities and large corporations - all knocking away at my home ssh daemon (2 - 5 attackers / day @ 100's of attempts per attacker).

[http://www.dshield.org](http://www.dshield.org) has some interesting trend data.  :cool:

---

### Post by artnay on 2005-12-02
To add a few things:

If you want to continue with passwords, maybe you could edit your /etc/hosts.allow and /etc/hosts.deny and set the preferred hosts/IPs to allow file and to deny file ALL: ALL. I don't use any random machines to enter my box, only some machines that have static IPs. So this is an easy choice.

You could always restrict the users that have a permission to enter via SSH. Add something like this
"AllowUsers account1 account2" etc. to your /etc/ssh/sshd_config file. That way an attacker should know allowed IPs, allowed accounts and passwords for those accounts. Or you could use keys and avoid those damn keyboard loggers that way. ;) Hopefully there's no remote exploit in OpenSSH :rolleyes:

---

