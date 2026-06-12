---
title: "Parellel Processing"
date: 2008-04-26
forum: Virtualisation
---

### Post by secondstage on 2008-04-26
I have two nearly identical computers and only use one for my website(not currently available from outside my home). Is there any easy way to have them both running and have them act as one computer?

Edit: Did some more googling and...
1. What is Zen?
2. Would Zen do a good job of this?

**Specs**
[list]
_Computer A_
[*]Pentium 3
[*]256 MB of ram
[*]20 GB Hard Drive

_Computer B_
[*]Pentium 3
[*]512 MB ram
[*]40 GB Hard Drive
[/list]
Both are running Gutsy, but if there is a distro that can do what I want better, then I could always switch.

---

### Post by tamoneya on 2008-04-26
it depends on exactly what you are trying to do in parallel but it is typically not the best thing.  Take a look at [http://www.beowulf.org/](http://www.beowulf.org/).  It may meet your needs.

---

### Post by secondstage on 2008-04-26
Seems to be way over my head. Is there no way to just install a program on both computers and have them connected via ethernet cable? Or am I asking for too much too early?

---

### Post by tamoneya on 2008-04-26
no it is not a plug and play sort of thing.

---

### Post by secondstage on 2008-04-26
I'll probably go and post this question in a web server forum anyway, but what would be a good way to spread the work of hosting out onto the second computer?

---

### Post by gary vollink on 2008-04-27
> **secondstage said:**
> I'll probably go and post this question in a web server forum anyway, but what would be a good way to spread the work of hosting out onto the second computer?

What you are trying to do is typically done by load balancing.  There are a few ways of doing this... the simplest is to set up a single DNS name with both of the IP addresses of each computer, and keep the same web-software running on both computers.  Each inbound, new request will get a "random" of one of these IPs, and will end up hitting one instead of the other.

The right way to do the above is to use a piece of hardware called a load-balancer (some of which can also do fail-over monitoring, and utilization monitoring to keep the systems running evenly).

Some web setups will run specific sub-directories on one server, and not the other (you can use Apache proxy and proxy reverse statements to have processing for sub-directories serve from one server, but pass through the front server).  This can be useful if, say, you are running a large static site on one server, but an interactive site in one sub-directory.  The static server can be the front-end, but then it will have the hard processing done on the other server (say, the one with the bigger hard drive).

---

### Post by Dan Patch on 2008-05-19
You could throw those away and buy a pc made this century for $50 and not bother with DNS RR.  Which--as it turns out--happens to not be random.

A hardware load balancer would tend to be more expensive than this setup combined by around 50x, so may not be your best choice either.

Instead, you should look at using them for separate tasks, perhaps one a db server and the other web.  Or, one a php server and one web, if you don't have need for a db.

---

