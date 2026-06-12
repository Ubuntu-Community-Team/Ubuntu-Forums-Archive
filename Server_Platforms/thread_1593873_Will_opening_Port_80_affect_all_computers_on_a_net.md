---
title: "Will opening Port 80 affect all computers on a network"
date: 2010-10-11
forum: Server Platforms
---

### Post by Nix1794 on 2010-10-11
I'm thinking about making a web server but, I have an issue:will opening Port 80 affect all computers on a network?
please help :D

---

### Post by Barriehie on 2010-10-11
> **Nix1794 said:**
> I'm thinking about making a web server but, I have an issue:will opening Port 80 affect all computers on a network?
please help :D

Port 80 is typically the port that the server listens to for http requests.  You'll be needing a good IP tables setup.  My machine gets a ssh attack about once every 42 minutes and I'm using a nonstandard port.

HTH

---

### Post by CharlesA on 2010-10-11
> **Nix1794 said:**
> I'm thinking about making a web server but, I have an issue:will opening Port 80 affect all computers on a network?
please help :D

The way port forwarding works, is that it forwards that port to a single ip address.

---

### Post by HighCommander540 on 2010-10-11
> **Barriehie said:**
> Port 80 is typically the port that the server listens to for http requests.  You'll be needing a good IP tables setup.  My machine gets a ssh attack about once every 42 minutes and I'm using a nonstandard port.

HTH

Hey, I get that too. What weird people. Spend all day doing that crap. IDK, how they even got my IP address. My is dynamic and private only for me.

Anyway, can you give me link(s) to any good tutorials on IP tables or what I can do to help stop and prevent this?

---

### Post by Barriehie on 2010-10-12
> **HighCommander540 said:**
> Hey, I get that too. What weird people. Spend all day doing that crap. IDK, how they even got my IP address. My is dynamic and private only for me.

Anyway, can you give me link(s) to any good tutorials on IP tables or what I can do to help stop and prevent this?

I use denyhosts and don't worry about it.  I'm guessing they just have a script that runs a gamut of IP's.  Mines dynamic too.  Here's a link I've found helpful.  What I've done for my server is use a nonstandard port and then no-ip redirects to my machine when there's a request for the url.  Can't stop the attacks but you don't have to open the door!

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by CharlesA on 2010-10-12
The SSH attacks are just scripts that scan blocks of ip addresses for open ports. I've been using only iptables and key-based auth and my logs seem to be realitively clean.

---

### Post by Barriehie on 2010-10-12
> **CharlesA said:**
> The SSH attacks are just scripts that scan blocks of ip addresses for open ports. I've been using only iptables and key-based auth and my logs seem to be realitively clean.

Here's a good link for getting scanned.  I ended up backing off on my denyhosts logging and it's settled down.  I just wanted to see if it was working, and it is, like a dog!

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

My machine:

---

