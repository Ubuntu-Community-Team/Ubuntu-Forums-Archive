---
title: "Problem with UFW"
date: 2010-08-29
forum: Security
---

### Post by grimm08 on 2010-08-29
I have just set up a ubuntu server to serve as my central file storage.  I also added a streaming media client, I have yet to get the uShare client to work correctly with my xbox but my gf's PS3 works with no problem.

The problem I keep having is that UFW is blocking the needed ushare port for my xbox, if some one could give me some help I would be greatfull.  Since I do not want to use iptables unless there is no other option.

---

### Post by an0dos on 2010-09-02
bodhi.zazen has a guide to setting up firewall rules using UFW here:
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

You just need to allow communication over the port that the xbox uses.

BTW, UFW is a front-end for iptables.

---

### Post by wojox on 2010-09-02
If your using a router it can act as your firewall and just use port forwarding. ;)

---

### Post by an0dos on 2010-09-02
> **wojox said:**
> If your using a router it can act as your firewall and just use port forwarding. ;)

This too.

---

### Post by bodhi.zazen on 2010-09-02
> **grimm08 said:**
> I have just set up a ubuntu server to serve as my central file storage.  I also added a streaming media client, I have yet to get the uShare client to work correctly with my xbox but my gf's PS3 works with no problem.

The problem I keep having is that UFW is blocking the needed ushare port for my xbox, if some one could give me some help I would be greatfull.  Since I do not want to use iptables unless there is no other option.

What port do you need to allow ?

The basic syntax is 

```
sudo ufw allow port#
```

Although you can also limit that by ip address as well.

---

### Post by dirtrider1 on 2011-07-23
I also have this problem even after allowing the port in ufw the Xbox360 says cannot connect Firewall blocking but with Ufw disabled it work's perfectly?

---

### Post by bodhi.zazen on 2011-07-23
> **dirtrider1 said:**
> I also have this problem even after allowing the port in ufw the Xbox360 says cannot connect Firewall blocking but with Ufw disabled it work's perfectly?

The order of your rules makes a difference.

Start a new thread, as opposed to hijacking an old one, and post your rules.

---

