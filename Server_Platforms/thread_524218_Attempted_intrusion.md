---
title: "Attempted intrusion"
date: 2007-08-12
forum: Server Platforms
---

### Post by p_quarles on 2007-08-12
I run Apache on one of my boxes, and sometimes open the firewall on my DSL modem to allow access to my site. I forgot to close it up last night, and inadvertently left it open all night. When I realized this, I checked the access log, and saw this:
```
68.xx.xx.xx - - [11/Aug/2007:23:10:05 -0500] "GET / HTTP/1.0" 200 64
68.xx.xx.xx - - [11/Aug/2007:23:10:05 -0500] "POST /_vti_bin/_vti_aut/fp30reg.dll HTTP/1.1" 404 227
```Now, I know that there's not much that a LAMP server can do with .dll files, so I wasn't too worried (besides, it returned a 404), but I did look into it.

First, I googled fp30reg.dll, which turns out to be an MS Frontpage remote administration tool that can also be used to start buffer overrun attacks on IIS servers. 

Then, I nmapped the intruding IP address. The box on the other end had multiple open ports, including 80. I paid a visit with Firefox, which revealed a running IIS server and a default "site under construction" page. 

So, what do you think happened here? And are there any tools I'm not thinking of that might help me find out? 

In my thinking, these are the possibilities:
1) This was a deliberate attack
2) This was an insecure machine that has already been hijacked and is running scripts that attempt to hijack further machines.
3) Someone was trying to log in remotely and got the wrong address (entirely possible: the remote IP is very similar, we're in the same city with the same ISP, and we both have dynamic IPs)

This is more an academic question than anything else, I guess, but I'm very new to operating a server, and am just curious to know how and how much I should react to an event like this. No harm was done, here, but I imagine there are ways to perform similar attacks on Apache servers. Any thoughts or suggestions are welcome.

---

### Post by PilotJLR on 2007-08-12
I'm not familiar with this attack, but my guess is either your idea #1 or #2 is right. I can't imagine why innocent traffic would try to post this file. Since the "attack" was against IIS, maybe this was a script kiddie??

It's amazing how much port scanning and script attacks are out there. For example, I left port 22 forwarded to one of my machines for a few days once, and I got a brute force attack. Literally, some bot in Hong Kong (where the source IP was) kept trying to login as "bob", "john", etc. Never got in, but still surprising they found the open port so fast.

After that attack, I remember to install denyhosts.  :-)

---

### Post by p_quarles on 2007-08-12
> I can't imagine why innocent traffic would try to post this file.Yeah, you're probably right. The .dll *is *apparently a legitimate remote admin application, but the time (11:10pm local) seems kind of an odd one to be updating a home web site remotely.:)

I'm off to look into denyhosts. Thanks for the tip.
EDIT: I see that denyhosts is for SSH. It's now installed and running, but I'd still appreciate any advice on programs that help prevent attacks on Apache.

---

### Post by dscherry on 2007-08-13
Hi,
Two things to mention.  Apache has very good security built in to it.  You could add mod-ssl, and use https to access your web pages and theoretically that would tighten things up a bit.  With Apache, often the weak links are the apps themselves, such as php or cgi scripts, where the door gets left open through poor design or bad programming practices.  Just because somebody bangs on the door, doesn't mean Apache will let them in.  By all means, continue with deny/allow hosts if you know who your visitors *should* be.

Second, most of the script kiddies and bots hit the 'normal' ports.  You can always shift to different port numbers.  This makes sense, only if you want specific people to access your server, and can let them know what the 'changed' ports are.  I used to get about a dozen to 20 attempts per day (to my knowledge, none got in).  After shifting ports, now it's more like 1 a month (hopefully still not getting in).

hth,
Dan

---

### Post by p_quarles on 2007-08-13
> **dscherry said:**
> Second, most of the script kiddies and bots hit the 'normal' ports.  You can always shift to different port numbers.  This makes sense, only if you want specific people to access your server, and can let them know what the 'changed' ports are.  I used to get about a dozen to 20 attempts per day (to my knowledge, none got in).  After shifting ports, now it's more like 1 a month (hopefully still not getting in).
I'd given that some thought before, and it's beginning to seem like a very good solution. That way, at least, I'll be able to leave a port open and still be able to pay attention to every attack. It's certainly easier to look for damage once a month than twenty times a day :)

Thanks.

---

