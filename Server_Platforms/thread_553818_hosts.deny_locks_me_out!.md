---
title: "hosts.deny locks me out!"
date: 2007-09-18
forum: Server Platforms
---

### Post by isecore on 2007-09-18
This is actually for a Debian Etch server, but since there are a lot of similarities between Ubuntu and Debian (and also since I run Ubuntu on my desktop) as well as having good experience with knowledgeable answers is why I'm posting here.

Here's the low-down: Me and my girlfriend are almost completely 100% Linux. We run Ubuntu on both her and my desktop-systems. I run a Debian Etch server where we do Samba-shares as well as run FTPd and Apache for our websites.

The only problem is that every time I fire up CUPSd on my Ubuntu box it triggers Portsentry on the Debian box which adds my IP to hosts.deny and locks me out of it. This is rather annoying, and I'm wondering why CUPS triggers it, since I don't have the most paranoid settings on Portsentry.

Secondly, it's not difficult to SSH from a different machine into and delete the entry from hosts.deny, but for my life I cannot figure out how to reload the deny-list without rebooting the server - which as you can understand is something that we really try to avoid unless absolutely necessary.

So, my questions: Why does CUPS trigger Portsentry? It only does it from my machine for some reason, my girlfriend does not get locked out when she does the same thing. And secondly, how do I reload/refresh/whatever the hosts.deny so that Debian reloads the list of blocked hosts?

Any input is greatly appreciated, since I've ripped out most of my hair already and would like to keep whatever is left.

---

### Post by HermanAB on 2007-09-18
Hmm, I would not use Portsentry.  There is a script called f*kportsentry that adds the whole world to it...

Cheers,

H.

---

### Post by Wim Sturkenboom on 2007-09-18
hosts.deny and hosts.allow are consulted by the application and not by the operating system. So restarting the applications that consult those files should do the trick.

Services are often started through (x)inetd. This means that a new instance of the application (e.g. ftp) is started when a request arrives and in that case it works 'automagically'.

---

### Post by isecore on 2007-09-18
Dang.

Yeah, that's pretty much the result of my research as well. That kinda sucks, having to reboot for that change to take effect.

Also I found the recommendations to not use Portsentry, so I apt-get purged it. I've just been running it for several years and it's worked for me, but no more.

Thanks for your input anyway!

---

### Post by Wim Sturkenboom on 2007-09-19
As I said, you don't have to reboot. You need to restart the application / service. Or am I missing something?
Annoying yes.

---

### Post by isecore on 2007-09-19
> **Wim Sturkenboom said:**
> As I said, you don't have to reboot. You need to restart the application / service. Or am I missing something?
Annoying yes.

No, you're not missing anything. I'm just being more stupid than usual. Thanks for the input!

---

