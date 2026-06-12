---
title: "help setting up iptables-p2p limiting"
date: 2006-01-13
forum: Server Platforms
---

### Post by NiN on 2006-01-13
Hello!

I`m on a small lan sharing the internet connection through a router.

Since some people are aggressivly violating our p2p policy, I&#180;d like to set up a resource limit.
Since our admin is not that skilled, I&#180;d like to help out with some firewalling rules, but I&#180;m relativly new to iptables and would appreciate any help regarding this topic.

P.S. sorry for my bad english :)

[EDIT]
O.K.
I don't want to block ports, I want to filter packets.
I&#180;ve read, that it is possible to mark certain packets (depending on it&#180;s type) and drop them (or other things), but I don&#180;t know how to do something like that.
I already found a project (iptables-p2p), but there is only a very limited documentation with it and the last update was some time ago.
[/EDIT]

---

### Post by Koybe on 2006-01-13
You're not telling exactly what you want, it's not so simple to answer ;)
A firewall at this time should have all his policy to drop an opening only the needed ports. 
This is a good start. Then it depends on your networks... on your needs.
And I'm not sure youre asking to stop the p2p (and which one) or to let it pass with a controlled amount of data ;)

---

### Post by palerider on 2006-03-21
i've found a posible solution for p2p downloads.

[http://www.ipp2p.org/](http://www.ipp2p.org/)

but i dont know if it will work will ubuntu.

can anyone here confirm if it will? i'd like to try it with ubuntu but i dont know how.

---

### Post by dafyre on 2007-06-06
I'm currently working with IPP2P, although I haven't been successful at all at getting it installed on Ubuntu with kernel v2.6.21.3 -- I haven't tried any other versions.  It's confirmed to work with 2.6.16.8.  I've got a security appliance running around here somewhere with it running.

I do however, have some examples using the linux TC command to filter a couple of different things...  The attached text file is a copy of the script I use [it runs with Shorewall], but can also be run by sh  if you like...

If you have any questions about the commands I used, feel free to contact me!  I'd also recommend checking [http://www.lartc.org](http://www.lartc.org) -- it has some in depth documentation on how to do traffic classifying and a little filtering with just the tc commands.

---

