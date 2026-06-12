---
title: "DoS Attack help!"
date: 2011-02-01
forum: Server Platforms
---

### Post by guessswh0 on 2011-02-01
Hi there people,

I am in need of some assistance.  My website has been under DoS attack.  After looking at the logs, it appears that the attacker is just sending tons of empty http requests, and just DoSing Apache (I am using apache as my web server).

When I notice this, I am able to block his IP address and the attack will stop.  However, the attacker switches IP, and then continues his attack.  I am in need of some good advice.

Obviously this is not a sophisticated attack.  This is not a botnet.  it is just someone from a single IP.  First, any suggestions?   Second, do you know of any apache configurations where I can limit the number of requests per IP address (not for the server, but per IP address)?  I could definitely just use some good advice, so hopefully you guys can help me out.

Thanks for the assistance.

---

### Post by lisati on 2011-02-01
You might want to check out options like fail2ban, mod_defensible and mod_security. These won't prevent all your problems, but might help alleviate some of the hassle.

---

### Post by cariboo on 2011-02-01
You can stop ddos attacks using iptables, have a look at [this]("http://bipinkdas.blogspot.com/2008/09/prevent-dos-attack-in-linux.html") page. Iptables is installed by default, so you just need to edit the rules.

Have a look at [bodhi.zazens's ptables primer]("http://bodhizazen.net/Tutorials/iptables").

---

### Post by slooksterpsv on 2011-02-01
> **cariboo907 said:**
> You can stop ddos attacks using iptables, have a look at [this]("http://bipinkdas.blogspot.com/2008/09/prevent-dos-attack-in-linux.html") page. Iptables is installed by default, so you just need to edit the rules.

Have a look at [bodhi.zazens's ptables primer]("http://bodhizazen.net/Tutorials/iptables").

Thank you, I'm not the OP but I still find that information useful. I didn't know bodhi.zazen had a site.

---

### Post by guessswh0 on 2011-02-02
I know I can use IP Tables, and install some software, however I do not have root access to the box as it is on a shared hosting server.  However, if I can find an apache configuration line in the config file, then I can talk to the hosting company to get it added.

Any ideas?  Any apache specific configs that allow you to limit the number of connections per IP?

---

### Post by James78 on 2011-02-02
Someone mentioned fail2ban, mod_security (and OWASP, which now has some DoS attack rules!), and mod_defensible. There's also mod_evasive. :) (Thanks for the tip on mod_defensible! I only used fail2ban, mod_security, and mod_evasive. Now I get to add another good one to the mix. :))

---

### Post by guessswh0 on 2011-02-02
I saw that, but fail2ban does not prevent against someone making tons of empty http requests.  Mod_defensible is more spam oriented, which is not the problem at the moment.  Mod-Security looks interesting, but it seems like it needs root access to the box, not something you get on shared hosting.

mod-evasive looks interesting though.  I haven't seen that.  I'll talk to the company and see if they can install that.

---

### Post by weedeater64 on 2011-02-02
Nothing you can do on your end. You need to seek assistance from your ISP, and possibly the police.

---

