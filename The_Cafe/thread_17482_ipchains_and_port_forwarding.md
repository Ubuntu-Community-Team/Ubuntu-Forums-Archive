---
title: "ipchains and port forwarding?"
date: 2005-02-28
forum: The Cafe
---

### Post by t.rei on 2005-02-28
Hi,

just ran into a Problem today. 

For running amule on my ubuntu powerbook properly I need to find out ho to forward ports with ipchains (I know, I know...)

I have my ubuntu on my client (192.168.0.2) and am running debian stable on a router (192.168.0.1). It's still on ipchains. I wouldn't like to change it - cause... well you know "never change a running system" and that router has endured years now. ;)

so - to keep it brief: Is anyone here so familiar with ipchains (been googleing a while now :/ ) to just give me the**** lines required to do the forwarding of:
4662 (TCP) and 4672 (UDP)?

I would be really gratefull!

thx

---

### Post by p!=f on 2005-02-28
Ipchains does not support forwarding ports, use ipmasqadm and portfw.
I recommend you to upgrade your machine to use iptables instead.

---

### Post by jdong on 2005-02-28
Ugh, not to mention **known attacks** against old versions of IPChains -- everything from buffer overflows to stalling the box.

---

### Post by t.rei on 2005-03-01
yes yes ... i know... since I figure help will be lacking on ipchains... I will attempt to install iptables... narf... wish me luck!

but thanx for reading anyways... :)

---

### Post by t.rei on 2005-03-01
Ok ok - iptables...

I upgraded my router from debian woody to ubuntu warty,  set up iptables and wrote this howto :P
[http://www.ubuntuforums.org/showthread.php?t=17594](http://www.ubuntuforums.org/showthread.php?t=17594)

---

