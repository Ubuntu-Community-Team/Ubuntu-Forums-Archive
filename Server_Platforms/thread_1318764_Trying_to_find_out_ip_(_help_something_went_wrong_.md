---
title: "Trying to find out ip ( help something went wrong )"
date: 2009-11-07
forum: Server Platforms
---

### Post by cf329rn on 2009-11-07
ok guys so i typed in ifconfig to check my ip on my ubuntu server and through all the jargon i dont know which one is the ip. i need it to acess webmin which ofcourse the server isnt broadcasting outside yet only locally in my house. so yesh what is my ip? anyone know


[IMG]http://techzone.sitefrost.com/u1.jpg[/IMG]

---

### Post by redmk2 on 2009-11-08
> **cf329rn said:**
> ok guys so i typed in ifconfig to check my ip on my ubuntu server and through all the jargon i dont know which one is the ip. i need it to acess webmin which ofcourse the server isnt broadcasting outside yet only locally in my house. so yesh what is my ip? anyone know


[IMG]http://techzone.sitefrost.com/u1.jpg[/IMG]

The IP address for this host is 10.0.2.15. The interface is eth0.  See the line that starts with: *inet addr*.

It looks like this is a VM.  You might have other connectivity issues in getting this host to talk to others in you LAN or to the outside internet.

---

### Post by DGortze380 on 2009-11-08
> **redmk2 said:**
> 
It looks like this is a VM.  You might have other connectivity issues in getting this host to talk to others in you LAN or to the outside internet.

Simply ensure you're using a bridged interface.

You'll also likely want a static IP on that machine.
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by cf329rn on 2009-11-08
> **DGortze380 said:**
> Simply ensure you're using a bridged interface.

You'll also likely want a static IP on that machine.
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)


how do i bridge the network on ubuntu server. i know how to do it in windows.

---

### Post by redmk2 on 2009-11-08
> **cf329rn said:**
> how do i bridge the network on ubuntu server. i know how to do it in windows.

[_https://help.ubuntu.com/community/VirtualBox/Networking_]("https://help.ubuntu.com/community/VirtualBox/Networking")

---

### Post by DGortze380 on 2009-11-08
> **cf329rn said:**
> how do i bridge the network on ubuntu server. i know how to do it in windows.

It's nothing to do with the server, it's a function of VirtualBox

---

