---
title: "Problem using stunnel to connect over SSL in pan"
date: 2006-11-11
forum: Server Platforms
---

### Post by gracamac on 2006-11-11
Hi, could someone please give me a quick rundown on how to use stunnel to connect to a news server in ubuntu.
Some guides I've read are:
[http://www.noderunner.net/~llin/old/nntp-ssl.html](http://www.noderunner.net/~llin/old/nntp-ssl.html)
[http://news.aioe.org/spip.php?article6](http://news.aioe.org/spip.php?article6)
... and others which tell me pretty much the same things.

So far:
- I've tried both stunnel and stunnel 4 packages from the repositories.
- I run the commands:
    - stunnel -v -c -d 119 -r nntps.xxx.xxxxxxxxxx.net:563 (old+new package)
    - stunnel tun (stunnel4 only, where tun is a config file)
- Both return no error messages. Also I can't find a verbose option in stunnel 4. stunnel(old) did not output anything with the -v option set. Using system monitor I can't tell if anything is running either.
- I can't connect in pan to localhost. Also I can't telnet into localhost using the method described in the second guide I have listed above.

Other details:
- I'm behind a NAT router.
- No firewall software configured.

---

### Post by saffsd on 2006-12-09
No solutions from me I'm afraid, just a post to let you know you've got a kindred spirit here trying to figure out why stunnel won't tunnel. Ssh tunneling works so much easier! and stunnel documentation is remarkably scarce. ](*,)

---

### Post by saffsd on 2006-12-10
Paydirt! the main problem with those guides is that they don't take into account the fact that you can't bind some ports in some situations. I know that sounds terribly vague, but I don't want to make assertions that aren't true. I think the problem is that in ubuntu you need to do something special to be allowed to bind to port numbers below 1024, but i'm not sure if this is actually ubuntu specific (normally a gentooer, just that right now i'm on a machine where i dont feel like spending a week compiling the OS :) ) or if the threshold is even 1024.

Anyhow, long story short, just use another port for now. I've got it working with port 2000. Here's my stunnel.conf for reference:

```

client = yes
foreground = yes
debug = 7

[nntps]
accept = localhost:2000
connect = news.giganews.com:563

```

you don't need (and probably don't want) the "foreground" and "debug" lines. That's what gives you the debug output though.

I'm using stunnel 4.20 compiled from sources, but I bet this would probably work with the stunnel in the repos (looks like 4.15). Let me know if this helps!

---

