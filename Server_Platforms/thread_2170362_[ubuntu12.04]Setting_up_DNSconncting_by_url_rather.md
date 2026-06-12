---
title: "[ubuntu12.04]Setting up DNS/conncting by url rather than IP address"
date: 2013-08-25
forum: Server Platforms
---

### Post by JfWPzYy on 2013-08-25
Alright, well I thought I had this figured out but now I'm all kinds of lost and confused.

My operating system:
Ubuntu Server 12.04 (Precise) Server 32-bit

My end goal:
To get my server set up so that when I'm running game server software (e.g. running a minecraft/terraria server) players connect to a url type thing (e.g. example.net) instead of my IP address.

What I've tried:
[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

I'm not too confident that I did that right though. I can still connect to the internet on that machine though so there's that...
I tried going to the desired web address in my internet browser (on another computer) and nothing came up (I would expect it to at least give me a "connection refused" or something similar if it worked right?).

So my question to you is:
What on earth do I even need to do?

I tried to keep it short so if I accidentally withheld any important information or wasn't specific enough please tell me. Which I'm sure you will.
Thanks for any help in advance!

---

### Post by Kevin_Arnold on 2013-08-26
You don't need to set up a dns server, you need to buy a domain.  I use hover.com but you can go any where that sells domain names.  Once you have that, there will be a spot on the registrars website for you to enter the ip address of your server.  That's it, you'll be up and running.

---

### Post by CharlesA on 2013-08-26
> **Kevin_Arnold said:**
> You don't need to set up a dns server, you need to buy a domain.  I use hover.com but you can go any where that sells domain names.  Once you have that, there will be a spot on the registrars website for you to enter the ip address of your server.  That's it, you'll be up and running.

Just to add to that, if your registrar provides hosting, they usually have a DNS control panel you can use, so you don't have to run a DNS server yourself. That's how I have my site set up.

---

### Post by Kevin_Arnold on 2013-08-26
> **CharlesA said:**
> Just to add to that, if your registrar provides hosting, they usually have a DNS control panel you can use, so you don't have to run a DNS server yourself. That's how I have my site set up.

Right, the registrar will have a spot to put in name servers or you can just use theirs and just put in your ip address. In this case, you don't want to change the name servers, just enter your external ip address.

---

