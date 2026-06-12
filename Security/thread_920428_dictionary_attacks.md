---
title: "dictionary attacks"
date: 2008-09-15
forum: Security
---

### Post by cdenley on 2008-09-15
Is it illegal in the US to perform a dictionary attack on an SSH server? I have a sort of SSH honeypot running, logging the IP's,usernames, and passwords of authentication attempts. I was thinking of writing a script to perform dictionary attacks on the attackers with the passwords the attackers are using (assuming they are also running an SSH server). My assumption is that many of the hosts attacking me have themselves been compromised with a dictionary attack because of a weak password. I guess if I got root, I can find some way to contact the server admin, or even fix their system myself. Seems like a fun idea, but I don't want to get into any trouble. Even if it were illegal, I can't see why anyone would care since they attacked first and I'm not doing anything malicious.

---

### Post by The Cog on 2008-09-15
I imagine such activity would be illegal. Also, you really don't want to be caught and then accused of being the one who first compromised the machine.

---

### Post by Oldsoldier2003 on 2008-09-15
> **cdenley said:**
>  I guess if I got root, I can find some way to contact the server admin, or even fix their system myself. Seems like a fun idea, but I don't want to get into any trouble. Even if it were illegal, I can't see why anyone would care since they attacked first and I'm not doing anything malicious.

It doesn't matter- if the machine is hosted by a ISP/hosting service they will attempt to prosecute anyone and everyone involved. Illegal access is illegal access.

---

### Post by HermanAB on 2008-09-15
You can reverse the attack back onto the attacker and have some fun, but it probably not legal: 
[http://aeronetworks.ca/ssh-kiddies.html](http://aeronetworks.ca/ssh-kiddies.html)

---

### Post by cdenley on 2008-09-15
I guess I will have to settle for e-mailing their ISP's, although most e-mails to addresses obtained from whois queries seem to bounce back. I improved my web interface to retrieve whois results automatically, and organize the data well.
[http://cdenley.yi.org/ssh_honey/](http://cdenley.yi.org/ssh_honey/)
I wrote the script to attack the attackers and determine their root password, but I don't think I will be using over the net.

---

