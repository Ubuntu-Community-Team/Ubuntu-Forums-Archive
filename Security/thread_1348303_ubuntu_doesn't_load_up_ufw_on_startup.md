---
title: "ubuntu doesn't load up ufw on startup"
date: 2009-12-07
forum: Security
---

### Post by karian021 on 2009-12-07
higuys i have  this problem my ubuntu 9.10  64-bit  wont  load up ufw on startup,i always have to do it manually,can someone help me out,please and can also  someone tell me if  the creative fatality usb gaming  headset work completely on ubuntu specially the mic because  i got it  as a present and i can't get the mic to work.

---

### Post by cdenley on 2009-12-07
Post any commands and related output or explain how you determined that UFW wasn't "loaded".

---

### Post by bodhi.zazen on 2009-12-07
> **karian021 said:**
> higuys i have  this problem my ubuntu 9.10  64-bit  wont  load up ufw on startup,i always have to do it manually,can someone help me out,please and can also  someone tell me if  the creative fatality usb gaming  headset work completely on ubuntu specially the mic because  i got it  as a present and i can't get the mic to work.

Those are two completely separate issues and I suggest you ask for assistance with your usb device on GH ;)

for ufw one typically types, in a terminal,

```
sudo ufw enable
```

The only times I have seen UFW fail is when one has another tool for configuring your firewall, most common on these forums, Firestarter. In that case remove (with the purge option) firestarter.

```
sudo apt-get purge firestarter
```

---

### Post by karian021 on 2009-12-07
> **bodhi.zazen said:**
> Those are two completely separate issues and I suggest you ask for assistance with your usb device on GH ;)

for ufw one typically types, in a terminal,

```
sudo ufw enable
```The only times I have seen UFW fail is when one has another tool for configuring your firewall, most common on these forums, Firestarter. In that case remove (with the purge option) firestarter.

```
sudo apt-get purge firestarter
```



thanks bodhi.zazen removing firestarter fixed my problem

---

### Post by Scholar-code on 2009-12-09
Yes, I was facing the same issue, and bodhi zazen has helped me with that and it was "Firestarter".
/me just wondering why/what causing the ufw to disable, when firestarter is active. Is that mean, firestarter is disabling ufw when the system shut downs? I always like to learn why thing works instead of it works kind of thing!

And, I honestly admit this, bodhi zazen, I appreciate and thank you very much for all your efforts and work regarding ubuntu. I simply love & enjoy and makes me more interested in ubuntu by reading :]

[http://blog.bodhizazen.net](http://blog.bodhizazen.net) &
[http://bodhizazen.net](http://bodhizazen.net)

---

### Post by bodhi.zazen on 2009-12-09
Thank you for your kind words.

In a nutshell, both ufw/gufw and firestarter are front ends to configure your firewall, which is iptables, which in turn is a front end to netfilter, LOL

So what happens is that, if both ufw and firestarter are installed, they both try to configure iptables at the same time, and thus conflict. It would be as if there were 2 steering wheels in an automobile and two drivers trying to turn the car in different directions at the same time.

Keep on reading and learning =)

---

