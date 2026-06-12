---
title: "Need a quick favour regarding SSH, literally 2 seconds"
date: 2010-04-22
forum: The Cafe
---

### Post by deanhopkins on 2010-04-22
Hi, trying to set up my server so that i can access it from college using SSH. I can access it locally (ssh user@192.x.x.x), but when i try to access it over the internet (ssh [email]user@***.dyndns.info[/email]) it says connection refused on port 22.

I think this is due to my router not allow loop backs.

So, what I need is somebody from the outside to test my connection for me, it will only take a second.

I would appreciate it if somebody could PM me, and i will message you the address. Then you will just have to type 'ssh ****.dyndns.info' into a terminal and tell me if it works.

Thank you!

---

### Post by undecim on 2010-04-22
You won't be able to access a computer inside your college network from the internet.

The only thing you could do is connect your server to another SSH server with port forwarding, then connect to that SSH server.

---

### Post by deanhopkins on 2010-04-22
Hi undecim, what I meant was that I want to be able to access my home server while I am at college over the internet. Not a college server from home.

I have confirmed that this is working, and the thread can now be closed or deleted.

---

