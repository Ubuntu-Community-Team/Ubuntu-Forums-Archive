---
title: "Free server with root access for remote X?"
date: 2009-10-12
forum: Security
---

### Post by Ulysses_ on 2009-10-12
It is possible to run a linux executable on one computer and show the X output on another computer. I would like to run firefox like this. The executable would run on a free server, and the X output would appear on my linux pc.

1. Where do I find a free hosting server that offers this sort of root access?

2. What packages do I need to run the X session over a secure link to the server?

3. How do I save a disk image of the server's system partition and restore it at every boot time?

I understand a virtual private server can do all that.  But where do I get one for free, or a server with root access for free?

---

### Post by Ulysses_ on 2009-10-12
Actually, maybe root access is not required, just firefox to be preinstalled and remote usage of X to be enabled.

---

### Post by Penguin Guy on 2009-10-12
Why on earth would you want to do that? :confused:
Anyway, perhaps [this]("http://www.xs4all.nl/~zweije/xauth.html") might help - good luck.

---

### Post by movieman on 2009-10-12
X was designed for LANs, and doesn't work well over the Internet due to high latency. You can install FreeNX, which is a much more efficient X proxy and should greatly reduce the number of round-trip messages; I'm not sure whether it's available in Ubunutu repositories.

---

### Post by Agent ME on 2009-10-12
> **Ulysses_ said:**
> It is possible to run a linux executable on one computer and show the X output on another computer. I would like to run firefox like this. The executable would run on a free server, and the X output would appear on my linux pc.[/code]
Why would you want to run firefox like this? It would act very slow. Perhaps you want to use the server like a proxy? This is easy. Connect to the server as you would via SSH, but add the argument for a dynamic proxy: "ssh somehost.com -D7070". Now set Firefox to use localhost:7070 as a socks 5 proxy.

If you're curious though, it is possible to run programs remotely and have their display forwarded to you. Connect in like this: "ssh somehost.com -X". Then type "firefox &" or "xterm &", and the program will start up just as if you did it on a local command terminal (but it's really running on the server - try File -> Open in Firefox and you'll see the server's files). But this is pretty slow over the internet.

[QUOTE=Ulysses_;8093397]1. Where do I find a free hosting server that offers this sort of root access?
You don't need root access to do this. Every user account is able to run programs and SSH in (or else the account would be useless as a shell account).

> **Ulysses_ said:**
> 2. What packages do I need to run the X session over a secure link to the server?
On the client computer, you do not need anything extra. Everything needed is already installed.
But most servers don't have the right software installed to run a program like Firefox.

> **Ulysses_ said:**
> 3. How do I save a disk image of the server's system partition and restore it at every boot time?
Ugh, why would you want to do that? The data in the system partition/folders isn't write-able by normal users, so you don't need to worry about that area getting a virus (like with windows).

> **Ulysses_ said:**
> I understand a virtual private server can do all that.  But where do I get one for free, or a server with root access for free?
I don't think you'll find one for free that can run Firefox, but you might be able to find one that can act as a proxy (with the "-D7070" parameter). No root access required.

---

### Post by Ulysses_ on 2009-10-13
Thanks, I am familiar with some of the information above except freenx is new to me and seems to be the way to go - thanks a lot.  

But the main problem is:   Where do I get a free server?  

Also, if firefox is not preinstalled, are you sure I can install firefox without root access? I remember installing it from the debian repositories, and that required root access.

By the way, please do not ask why I want to do this because the answer is not trivial and it will distract us from the question in the title.

---

### Post by Agent ME on 2009-10-14
Programs can be installed without root access to your own user account. It's easiest if you install the programs from source.

However, many servers don't even have X running, so you could run into some issues. I think a user install of X or compatible program could be possible, but is likely more trouble than it's worth.

> **Ulysses_ said:**
> By the way, please do not ask why I want to do this because the answer is not trivial and it will distract us from the question in the title.
The reason I do this is because I cannot imagine any scenario this is needed, and I believe that there may be a more direct approach to whatever you're trying to do. I also do not believe you will find a free shell server that will let you do what you want.

Why do you need to run firefox remotely? I can think of three possible reasons (and counter-reasons):[list]
[*]You want to use the server as a secure proxy.
You don't actually need to run firefox on the server; it's much easier just to proxy your internet connection through the server. The connection gets encrypted, and the browser itself runs locally so it's still responsive.
[*]You think running Firefox remotely will be more secure to prevent attacks on your own computer.
If you really think you'll manage to stumble onto a 0-day exploit while browsing with firefox, there are many more straightforward (and cheaper...free) ways to lock down firefox than run it on a remote server. Install NoScript, run Firefox on its own user account (like the built-in guest account), or run Firefox in a VM (like Virtual Box).
[*]You want to run multiple instances of Firefox with their own settings.
This can also be done much more straight-forwardly. Press alt-f2, and enter in:
```
firefox -ProfileManager -no-remote
```
Make a new profile. You can use this profile concurrently and separately than other profiles. To start Firefox with the non-default profile, simply enter the same command and pick the same profile. (You can even set a shortcut to do this.)
[/list]

---

### Post by Ulysses_ on 2009-10-14
> **Agent ME said:**
> 
[LIST]
[*]```
firefox -ProfileManager -no-remote
```
[/LIST]


This is cool, assuming a site visited by one instance cannot see the cookies of the other instance, right?

If you really want to know why this setup is being considered, here are some clues, I hope you guess the rest. Scripts and flash java etc can be used to retrieve ip's. Some sites do not work if scripts or flash etc are disabled. Tor exit nodes can be used to steal passwords or eavesdrop.  So for real anonymity and privacy, chains like this are being considered: 

pc - tor network - hostile tor exit node - free server - hostile site

Some meat goes around this skeleton or similar, I hope you do not want to go deeper into the... anatomy of it.

---

### Post by Ulysses_ on 2009-10-14
Where should I ask for a free server that can run X and firefox?

---

### Post by Agent ME on 2009-10-14
> **Ulysses_ said:**
> This is cool, assuming a site visited by one instance cannot see the cookies of the other instance, right?

If you really want to know why this setup is being considered, here are some clues, I hope you guess the rest. Scripts and flash java etc can be used to retrieve ip's. Some sites do not work if scripts or flash etc are disabled. Tor exit nodes can be used to steal passwords or eavesdrop.  So for real anonymity and privacy, chains like this are being considered: 

pc - tor network - hostile tor exit node - free server - hostile site

Some meat goes around this skeleton or similar, I hope you do not want to go deeper into the... anatomy of it.
Forwarding an X connection through all of that would be hell. Trust me, not usable.

Flash and Java work fine for me under Tor. I've loaded so-called exploits to find your IP with those, and I guess I had the right updated version (which was installed by Ubuntu already) and none could find my real IP.
If you're paranoid someone trying a 0day exploit on you, you can set up a VM or even a specific user account that has *all* traffic forwarded through Tor or dropped ([https://wiki.torproject.org/noreply/TheOnionRouter/TransparentProxy](https://wiki.torproject.org/noreply/TheOnionRouter/TransparentProxy)).

---

### Post by Ulysses_ on 2009-10-14
> **Agent ME said:**
> Forwarding an X connection through all of that would be hell. Trust me, not usable.

You've tried freenx over tor? Freenx is designed specifically for high latency and low bandwidth connections.  Eg it caches menus so the second time you open a menu it opens immediately.  Should be tried over tor to see what happens.  Maybe I can try it if I manage to connect two computers over a tor route, you know how to do that if all you have is an adsl router?

> Flash and Java work fine for me under Tor. I've loaded so-called exploits to find your IP with those, and I guess I had the right updated version (which was installed by Ubuntu already) and none could find my real IP.They will continue to work fine then, until someone comes up with another exploit.  It's an endless cycle, that's why I'm hoping to come up with smarter solutions.

> someone trying a 0day exploit on you, you can set up a VMHere's an exploit for a VM, an executable in the VM can launch itself in the host.

[http://www.immunityinc.com/documentation/cloudburst-vista.html](http://www.immunityinc.com/documentation/cloudburst-vista.html)

> or even a specific user account that has *all* traffic forwarded through Tor or dropped ([https://wiki.torproject.org/noreply/TheOnionRouter/TransparentProxy](https://wiki.torproject.org/noreply/TheOnionRouter/TransparentProxy)).Could you explain why this helps against any 0day exploits trying to work out your ip?  Surely the external IP is what they're after, right?  You've got a script that can tell a site your external ip when you're visiting through tor but which fails when you do the transparent proxy thing?

---

### Post by Agent ME on 2009-10-15
> **Ulysses_ said:**
> You've tried freenx over tor? Freenx is designed specifically for high latency and low bandwidth connections.  Eg it caches menus so the second time you open a menu it opens immediately.  Should be tried over tor to see what happens.  Maybe I can try it if I manage to connect two computers over a tor route, you know how to do that if all you have is an adsl router?
*SSH terminal connections* often border on unusable. Anyway, to do what you want, if Freenx is a drop-in replacement for X it should work very easily with "ssh -X hostname". (To proxy ssh through, [look here](http://blog.kurthbemis.com/2008/08/25/tools-ssh-over-tor-for-secure-and-anonymous-sessions/). Get connect-proxy from ubuntu reps.)

> **Ulysses_ said:**
> They will continue to work fine then, until someone comes up with another exploit.  It's an endless cycle, that's why I'm hoping to come up with smarter solutions.
Most places that try to find your IP don't have the absolute latest detection methods, unless you're wandering into some sort of FBI stings. If you worry about that, try the VM or account-with-all-traffic-through-proxy methods.

> **Ulysses_ said:**
> Here's an exploit for a VM, an executable in the VM can launch itself in the host.

[http://www.immunityinc.com/documentation/cloudburst-vista.html](http://www.immunityinc.com/documentation/cloudburst-vista.html)
That's an exploit dealing with the consumer-oriented vmware's shared folder system in case I recall correctly. Try using something more barebones like KVM (which is completely functional for running desktop OS's, besides no accelerated video or shared folder support).

> **Ulysses_ said:**
> Could you explain why this helps against any 0day exploits trying to work out your ip?  Surely the external IP is what they're after, right?  You've got a script that can tell a site your external ip when you're visiting through tor but which fails when you do the transparent proxy thing?
If you're running in a VM, then the VM has no way of knowing your real IP if all of its traffic is forwarded through a proxy. Same with a user account that's restricted to a proxy.

---

