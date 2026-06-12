---
title: "Parent Network Controls"
date: 2006-08-19
forum: Server Platforms
---

### Post by nicholaspaul on 2006-08-19
I'm planning on setting up a Ubuntu machine that the kids can use on the network, but I need some restrictions put on it. 
Firstly, I have a wired/wireless network going through a router, so I understand that there are some restrictions I can put in place at the router. However, these would have to be machine-specific. There is only potentially one computer that needs extra security. 
Is there a way to limit useage of certain programs (messenger, in particular) and also to restrict website access to, say, certain websites? Are there any parents around that have secure machines set up? Is it possible to limit port access on one machine?

Any and all advice/anecdotes appreciated!

---

### Post by Klaidas on 2006-08-20
Well, using Firestarter, which is ubuntu's reposities, you could block outgoing ports/connections to websites. 
It need admin password to run, so your kids won't change anything :)

By the way, how old are they?

---

### Post by btdown on 2006-08-20
Search the forms for parental controls. There are a couple of options in there...
heres one in the howto section:

[http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)

---

### Post by nicholaspaul on 2006-08-20
> **Klaidas said:**
> Well, using Firestarter, which is ubuntu's reposities, you could block outgoing ports/connections to websites. 
It need admin password to run, so your kids won't change anything :)

By the way, how old are they?
Thanks, i'll look into it. 
They little ones range from 8 to 15, increasing with age and curiosity.

---

### Post by Gonesville on 2007-10-17
Although you may already know, a very easy way to block specific sites on your comp is to simply block them using Firestarter. Simply bring up the gui, go to policy, select editing outbound traffic policy, right click in deny connection to host, enter site name (ex. [www.abc.com](www.abc.com)) Viola. A very simple process. Hope this helps.

---

### Post by koenn on 2007-10-17
Ubuntu CE has web content filtering (a combination of DansGuardian, TinyProxy, and a GUI). You can install it seperately, eg [http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

and I think you can deny access to programs by modifying the permessions on their executables, but there may be better ways I don't know of.

---

### Post by xpod on 2007-10-17
With 5 kids and as many machines around the house what they can ...or cant accidently access in is a must for us too.

My own machine here *is* the router/firewall/gatway for all the kids pc`s and while i can easily restrict access to msn etc with firestarter i generally use [http://www.opendns.com/](http://www.opendns.com/) for the porn filtering.

Of course you can also restrict everything and only allow the sites you want to allow access to but my older 2 have proven responsible enough so far with the access they do get.
My youngest girls use a desktop that sits right next to mine though so their constantly being helped & monitored.

I can monitor all their machines from here though, and they all know it:)
I think just teaching your kids what they should and should`nt be doing goes a long way too.If you catch them young enough anyway:)
My only reason for ever sitting down at a pc last year was to hopefully keep our kids safe and with the help of Ubuntu & Co that jobs just been all the easier....imo

Edit:The Social Networking Sites are where the real problems can be so thats also something you should know about

---

