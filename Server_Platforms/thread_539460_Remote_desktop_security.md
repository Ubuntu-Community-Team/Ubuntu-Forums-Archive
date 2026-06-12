---
title: "Remote desktop security"
date: 2007-08-31
forum: Server Platforms
---

### Post by nvteighen on 2007-08-31
Isn't it a security risk that any user could activate GNOME's Remote Desktop without any admin privilege? Wouldn't it be better to make it available for all users  only if someone with admin privileges gives permission to do that? Yes, I may sound a bit restrictive, but consider this scenario: a family computer where a 10-years child that has his own limited user account so he cannot do any mess activates the remote desktop... and the machine gets compromised. It sounds to be really possible... or just someone makes a mistake?

Just curious. (I don't use remote desktop, so this is just a question to learn a bit more)

---

### Post by bodhi.zazen on 2007-08-31
Well, the only way to protect users from themselves is with education (even then ...)

Any type of remote desktop is potentially a security hazard, but, in the example you site, access is only given to the 10-year-old's desktop.

IMO the best solution may be for you to install firestarter and configure you firewall to disallow external connections.

Of a secure connection I like ssh or tunneling a vnc connection over ssh.

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by nvteighen on 2007-09-02
If I understood well, you mean that in such scenario, a potential attacker wouldn't have admin privileges and he'd be have to beat that barrier in order to compromise the whole system.

Of course, you could use Firestarter too... but is it really secure to have that running with admin privileges the whole time? And also, you'll have to set Firestarter that way that 1) it starts automatically 2) without admin privileges, so anyone can use it.

---

### Post by bodhi.zazen on 2007-09-02
> **nvteighen said:**
> If I understood well, you mean that in such scenario, a potential attacker wouldn't have admin privileges and he'd be have to beat that barrier in order to compromise the whole system.

As long as the 10-year old is not a member of the admin group :)

> Of course, you could use Firestarter too... but is it really secure to have that running with admin privileges the whole time? And also, you'll have to set Firestarter that way that 1) it starts automatically 2) without admin privileges, so anyone can use it.

Well, firestarter is a gui front end to iptables. 

Once you configure iptables with firestarter your firewall remains set until you change them again.

So, firestarter is not active at boot, but your changes to iptables sure are ...

So, 

1. The firewall is active at boot automatically, firestarter just configures it. The configuration changes you make survive re-booting.

2. Well, actually the only one who needs access to firestarter is the admin user ...

3. If you *really feel* other users need access, you can grant access via sudo (see man sudoers).

HTH :)

---

### Post by nvteighen on 2007-09-03
> **bodhi.zazen said:**
> As long as the 10-year old is not a member of the admin group :)
Actually, that's something very common... in Windows :)



> **bodhi.zazen said:**
> Well, firestarter is a gui front end to iptables. 

Once you configure iptables with firestarter your firewall remains set until you change them again.

So, firestarter is not active at boot, but your changes to iptables sure are ...

So, 

1. The firewall is active at boot automatically, firestarter just configures it. The configuration changes you make survive re-booting.

I've tried Firestarter before and that has never worked for me! I've installed now again and, after rebooting, when I do "sudo iptables -nL", everything is lost. Maybe I configure Firestarter in a bad way... and so, I removed it then because I felt it was useless... anyway, I don't use any server (I don't like online games in general, so I'm a bit "safer").

EDIT: I figured out that my Firestarter problem was a common conflict with Network Manager. I've solved it using [this guide]("http://ubuntuforums.org/showthread.php?p=3071503")

---

