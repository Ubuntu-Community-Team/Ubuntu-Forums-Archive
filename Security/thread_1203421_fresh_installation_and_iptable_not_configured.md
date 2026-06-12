---
title: "fresh installation and iptable not configured?"
date: 2009-07-03
forum: Security
---

### Post by sandrocchio_0.1 on 2009-07-03
I am not sure about my disappointment, but is it true that Ubuntu come with IPTABLE not configured, actually configured to allow all?

---

### Post by bodhi.zazen on 2009-07-03
Yes.

It is also true that a default installation has no listening services, so with a default installation all ports are closed.

Most people are behind routers and,thus, for the average desktop user, a permissive firewall is sufficient.

What makes you think you need a firewall if all your ports are closed ?

If you wish, Ubuntu comes with ufw. If you want a graphical front end simply install gufw.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

```
sudo ufw enable

sudo iptables -L -v
```

---

### Post by sandrocchio_0.1 on 2009-07-03
Well it is true that it comes with no listening services, but it also doesn't mention that the default FW is set to allow all incoming traffic.
Soon or later the new user who has moved to Ubuntu will start to play with server applications and then it'd be wiser have the ports shut. 
(Personally I'd prefer to spend time installing a FW frontend instead than fix an hacker attack.)

---

### Post by bodhi.zazen on 2009-07-03
Sounds as if UFW is perfect for you.

Firewalls have been an issuse of recurring discussion on these forms and opinions vary.

Rather then debate how it should be, understand how it is and, if you wish, turn you firewall on and off.

I do not like the default settings inf Fedora and change them, so go figure. It takes all for 10 seconds

```
su -
iptables-restore < iptables.conf
service iptables save
```

---

