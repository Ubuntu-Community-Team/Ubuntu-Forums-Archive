---
title: "[SOLVED] I need some basic help with Elive, I am having an Odd problem"
date: 2007-09-03
forum: The Cafe
---

### Post by RAV TUX on 2007-09-03
So I like Elive alot but here is the problem:

I can not access my website via Elive with any browser, specifically IceWeasel, Opera and Konqueror

[http://cafelinux.org/](http://cafelinux.org/)

I am not sure whats up?

I can access the website with any other OS except Elive.

Anybody have a clue what may be happening?

---

### Post by blithen on 2007-09-03
This SHOULD be in the general help section. :P But no worries.

Did you make your site with java/flash?

---

### Post by RAV TUX on 2007-09-03
> **blithen said:**
> This SHOULD be in the general help section. :P But no worries.

Did you make your site with java/flash?
It's not about the site, the site works in every other OS and every other browser.

look at this webpage:

[http://CafeLinux.org/](http://CafeLinux.org/)

no java and no flash!

Again please do not focus on the Website, I can use any other Distro and it works fine

There has to be something that I need to change in Elive.

I am stomped on this one.

Probably something basic I am over looking.

---

### Post by RAV TUX on 2007-09-03
Initially, I thought was a problem with IceWeasel but no matter what Web Browser I use I get the same result.

When I use those same web Browsers in any other OS it works fine.

Test it your browser, in your OS

[http://cafelinux.org/](http://cafelinux.org/)
[http://distropedia.com/](http://distropedia.com/)

---

### Post by ThrobbingBrain66 on 2007-09-03
Can you ping [www.cafelinux.org](www.cafelinux.org)?

---

### Post by RAV TUX on 2007-09-03
> **ThrobbingBrain66 said:**
> Can you ping [www.cafelinux.org](www.cafelinux.org)?


I can access the website from every other OS, even on the same computer.

Again this is not a website issue

---

### Post by RAV TUX on 2007-09-03
I will try reinstalling Elive.

I was just in the IRC room for Elive and confirmed that the page loads for other Elive users.

There must be something wrong with my install.

---

### Post by ThrobbingBrain66 on 2007-09-03
Just asking because it took me a couple tries to ping cafelinux.org

---

### Post by RAV TUX on 2007-09-03
> **ThrobbingBrain66 said:**
> Just asking because it took me a couple tries to ping cafelinux.org
Hey Thanks for helping, I know it isn't a server or website issue or a problem with my internet connection.

I have three computers and every computer connects fine.

1. PC-BSD connects instantly
2. XP Tablet Edition Connects instantly
3. Dual boot computer XP & Elive
   a. XP Media Center Edition connects instantly
   b. Elive doesn't connect

---

### Post by Onyros on 2007-09-03
RAV, I tried the site and it's not working for me. I can't ping it, either.

I've tried on an Ubuntu laptop, an Arch Linux laptop, my wife's Ubuntu laptop, tried on ZenWalk, on my desktop's Arch install... nothing, nada, zippo.

It's not working for me, so don't scrap your Elive install just yet.

Probably something to do with DNS propagation?

---

### Post by mips on 2007-09-03
RAV,

Those sites arent working, I tried from Sabayon with Konqueror and my laptop with Ubuntu & Firefox.

The error i get on all of them is:
```
[code=DNS_TIMEOUT] A DNS lookup error occurred because the request timed out during the lookup.

```
Your issue are site related. Your other pc's probably have the website cached.

---

### Post by init1 on 2007-09-03
I can connect in Antix.

---

### Post by kelvin spratt on 2007-09-03
I'm on Elive works perfect for me 3secs to load

---

### Post by init1 on 2007-09-03
> **mips said:**
> RAV,

Those sites arent working, I tried from Sabayon with Konqueror and my laptop with Ubuntu & Firefox.

The error i get on all of them is:
```
[code=DNS_TIMEOUT] A DNS lookup error occurred because the request timed out during the lookup.

```
Your issue are site related. Your other pc's probably have the website cached.
Mine isn't cached. I've never been to any of those sites in Antix.

---

### Post by RAV TUX on 2007-09-03
> **Onyros said:**
> RAV, I tried the site and it's not working for me. I can't ping it, either.

I've tried on an Ubuntu laptop, an Arch Linux laptop, my wife's Ubuntu laptop, tried on ZenWalk, on my desktop's Arch install... nothing, nada, zippo.

It's not working for me, so don't scrap your Elive install just yet.

Probably something to do with DNS propagation?

> **mips said:**
> RAV,

Those sites arent working, I tried from Sabayon with Konqueror and my laptop with Ubuntu & Firefox.

The error i get on all of them is:
```
[code=DNS_TIMEOUT] A DNS lookup error occurred because the request timed out during the lookup.

```Your issue are site related. Your other pc's probably have the website cached.

> **init1 said:**
> I can connect in Antix.

Wierd, I'm on the Wolvix Live CD and it connects instantly....

This concerns me that many people can't connect I may need to change my host....

I may or may not keep elive, I am experimenting now with Wolvix.

Thanks for the 411 about elive and my website

Does anybody know of an inexpensive reliable host?

---

### Post by popch on 2007-09-03
I can ping the site. http and nslookup work as well. Traceroute does not work, presumably because of disabled ports along the way.

Are you using the same DNS server for all systems you have mentioned?

BTW, you did not state in what way [http://cafelinux.org/](http://cafelinux.org/) was inaccessible. Does name resolution work? Does the server answer anything at all?

It should not matter (in theory), but in several posts there were different cases of the URL (CafeLinux vs cafelinux).

---

### Post by RAV TUX on 2007-09-03
> **popch said:**
> I can ping the site. http and nslookup work as well. Traceroute does not work, presumably because of disabled ports along the way.

Are you using the same DNS server for all systems you have mentioned?

BTW, you did not state in what way [http://cafelinux.org/](http://cafelinux.org/) was inaccessible. Does name resolution work? Does the server answer anything at all?

It should not matter (in theory), but in several posts there were different cases of the URL (CafeLinux vs cafelinux).

No worries, I have changed my Linux OS to Foresight, I figured I should stay with what I know the best a GNOME and rPath based distro.

---

### Post by mips on 2007-09-03
Seeing that it works for some and not others I'm beginning to suspect a DNS change somewhere. Give it some time to propegate through the network and all should be able to access it.

---

### Post by RAV TUX on 2007-09-03
> **mips said:**
> Seeing that it works for some and not others I'm beginning to suspect a DNS change somewhere. Give it some time to propegate through the network and all should be able to access it.

Thanks Mips I appreciate it.

---

### Post by FuturePilot on 2007-09-03
Hi RAV!
It worked for me. I'm stumped too.:(

---

### Post by RAV TUX on 2007-09-12
> **RAV TUX said:**
> So I like Elive alot but here is the problem:

I can not access my website via Elive with any browser, specifically IceWeasel, Opera and Konqueror

[http://cafelinux.org/](http://cafelinux.org/)

I am not sure whats up?

I can access the website with any other OS except Elive.

Anybody have a clue what may be happening?

I solved the problem by doing a fresh install of Elive Gem 1.0, all my webpages render correctly. All is good again.

---

### Post by ComplexNumber on 2007-09-12
closed at OP's request.

---

