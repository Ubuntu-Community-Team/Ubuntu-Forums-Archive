---
title: "virtual ubuntu server - network problem"
date: 2008-12-02
forum: Virtualisation
---

### Post by Gungy on 2008-12-02
Hello, i m currently trying to setup an ubuntu server ( hardy heron, some image that was already configured vor the virtual box) in my virtualbox, it is starting fine and i also configured my eth1 with ```
ifconfig eth1 192.168.2.39
```. 
my problem now is, that i cant get access from my ubuntu server to the internet nor to my host system, a ```
ping 192.168.2.39
``` in ubuntu is working fine, a ```
ping 192.168.2.1
``` (router adress) is giving an DESTINATION HOST UNREACHABLE to me. A ping to some external ip is giving me a NETWORK UNREACHABLE.

Any ideas how to get my ubuntu server to connect to the internet?

setup: windows xp as host ( 192.168.2.34 with dhcp)
       router (192.168.2.1)
       ubuntu as guest ( 192.168.2.39 no dhcp i guess)

thx in advance

---

### Post by Dedoimedo on 2008-12-02
You will have to bridge your host network interface with a virtual network device (tap).
Dedoimedo

---

### Post by Gungy on 2008-12-02
you have any link with a tutorial?

---

### Post by Dedoimedo on 2008-12-03
I didn't write any, I'll look for some and then post. I think there's a nice one here ... gimme some time to find it.
Dedoimedo

---

### Post by bodhi.zazen on 2008-12-03
There is a tutorial on how to do this in the Virualization Megathread at the top of these forums.

*That thread was made a stick for a reason*

If you still have questions let up know.

---

