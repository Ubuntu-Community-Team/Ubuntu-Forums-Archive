---
title: "Fail2ban questions."
date: 2010-07-08
forum: Server Platforms
---

### Post by EmanresuusernamE on 2010-07-08
I'm looking for a script to use with fail2ban that will instantly ban IPs trying to logon as root or administrator.  As well as ban IPs that send email to those addresses as well.  I'd like to do this myself, but the documentation is a bit cryptic on how to create rules.  Also, when I try to test out my rules, it tells me that it's too common or something like that.  Is there anyway to create these rules?

---

### Post by noway2 on 2010-07-08
I don't know how to help you change the fail2ban rules, which I haven't studied, but make sure that you have set permit root logins to NO.  That will at least render the attempt to login as root futile.

If you haven't already, consider using keys instead of passwords and turning off passwords.  

Out of curiosity, other than the fact that they clearly have no business being there, is there a reason why you want to turn off IPs for attempts to access root more harshly than the default 3x or 5x that fail2ban uses?  With root logins set to off, this shouldn't have any safety effects.

---

### Post by EmanresuusernamE on 2010-07-08
Two reasons I want to ban connections from root and administrator/admin on connect:

1) My root is disabled, and I'm the only one that really connects to my server via SSH, FTP and email.  Therefore I can assume that any attempts to login as root are either people logging into the wrong server, or people trying to brute force their way into my system.  I don't care if it's an accident, but I do mind if my server is used for something I didn't want it to be used for.  I'm getting my internet connection from a friend's business, and I don't want anything coming back to haunt me that might affect her, (she's a lawyer).  If they give up on trying the root account, they may start attacking other accounts, and while I'm pretty sure I've blocked everything below 500 from logging in, there's always the chance that I'm wrong.

2) There may be a flaw that we're unaware of, which allows full access to my server.  Some encryption algorithms I've heard about take a long time to key themselves.  Which is why I want to ban people using root/admin/etc.  If it takes them longer to access my system, they may either give up, or a fix for said flaw may be discovered.

When I can't connect to a server, I usually assume it's busy, or that it's going down for maintenance, and I'll try back later.  Having fail2ban ban that IP for a few days, that person may also assume the same thing.

I've pretty much gotten APNIC to stop hounding my ssh by banning all of their IP addresses from accessing port 22, so now they're spamming me.  However, I was looking at my logs and noticed attempts from the Netherlands and a few other places.

Security is the art of delaying someone from getting access to something you don't want them to, nothing is impossible to break into.  If you can only make one attempt at root access every couple of days, then it's theoretically harder to get access to the server.

Get my drift?

---

### Post by HermanAB on 2010-07-08
Howdy,

Fail2ban and the like is a Windows mindset solution.  It is high maintenance and doesn't adequately addresses the problem.

There is actually an exceedingly simple solution to SSH script kiddies: Change your SSH port to something other than 22 and they will go away.

Trying to enumerate evil is generally a big waste of time.  So, instead of trying to ban all the bad people in the world, just allow the one or two IP addresses that you use yourself in an iptables rule and drop the rest.

---

### Post by EmanresuusernamE on 2010-07-09
> **HermanAB said:**
> There is actually an exceedingly simple solution to SSH script kiddies: Change your SSH port to something other than 22 and they will go away.
That's a bit of a Windows mindset as well if you ask me.  If you've ever used the program nmap, you'd know that it can be easy to determine what ports are open, and what they are.  With enough time, and patience that a computer and script can provide, it can be done.  A simple change like that in my opinion is nice, but not near enough.

> So, instead of trying to ban all the bad people in the world, just allow the one or two IP addresses that you use yourself in an iptables rule and drop the rest.
A nice thought too, however, since I'm in the PC repair business, and tend to connect from my server from multiple locations, and I don't know which IPs I'll be connecting from, this solution doesn't really help me much.

What I also intend on doing, is stopping people from attempting to spam my server and through it.  I was looking in my mail logs, and noticed that people were slamming my SASL for awhile, ~100 connection attempts in 15 minutes. Had a whole bunch of these:
```
[12210]: connect from unknown[84.246.224.229]
[12210]: warning: unknown[84.246.224.229]: SASL login authentication failed: UGFzc3dvcmQ6
[12210]: lost connection after AUTH from unknown[84.246.224.229]
[12210]: disconnect from unknown[84.246.224.229]
```
Which leads me back to that first point, I can't change the incoming mail port that I'm using as I won't get any mail from anyone, I've tried. :)

> It is high maintenance and doesn't adequately addresses the problem
Actually, it's high maintenance because I'm making it that way.  I could just let it sit there and do what it's supposed to do, but I like to keep my eye on my server, and poke at it with various sticks.

---

