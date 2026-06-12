---
title: "Iptables configuration"
date: 2005-07-23
forum: Server Platforms
---

### Post by gallagher_niall on 2005-07-23
Hi All,

I am relatively new to Ubuntu, I have been using Redhat for a long time. However, I am finding that the iptables command is not working as it did for Redhat and other such distributions. I am using the following command:

/sbin/iptables -t nat -A PREROUTING -i eth+ -i lo -p tcp --dport 80 -j REDIRECT --to-port 8080

My goal is to map port 80 to port 8080 so that I can start an application server (Resin) as a non root user. I am getting no error messages or warnings when I use this command, however when I do an "iptables -L" it comes up empty, as if had not done anything. I have been trying now for a few hours and can get nowhere. Can anyone help, or point me twards some relevant documentation? An help on this issue would be greatly appreciated!

Niall

---

### Post by LordHunter317 on 2005-07-23
The issue is your rule is invalid.  You can't specify two incoming interfaces in the same rule.

---

### Post by hippyjim on 2005-07-26
[QUOTE=gallagher_niall]
My goal is to map port 80 to port 8080 
[/QUOTE]

I'd like to do the same, so I can make my proxy transparent. Did you figure it out at all?

---

### Post by gruepig on 2005-07-26
iptables -L only displays the rules for the standard chains (input, forward, output).  Try 'iptables -t nat -L'.  I don't know if you can specify two interfaces in one iptables rule, but otherwise the rest of your syntax is definitely correct (I have something similar working).

---

