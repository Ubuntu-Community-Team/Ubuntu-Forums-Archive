---
title: "Annoying robot hitting my server every hour"
date: 2007-02-02
forum: Server Platforms
---

### Post by PurplePenguin on 2007-02-02
Hi, I've been playing around lately with Ubuntu Server.  Everything's up and running well, using DYNDNS and everything.  Today, when I went to check the stats for one of the websites, I noticed that a robot from [www.freewebmonitoring.com](www.freewebmonitoring.com) was hitting it once an hour, every hour.  How annoying.

So, for a server newbie, what would you recommend in order to stop these robots from accessing my site?  I've got a feeling that it's not up to any good. :)  Should I bother stopping them?  I've read that there are a lot of robots that don't respect the robots.txt file.  Would it maybe be necessary to set up a firewall that will allow everybody through except for blacklisted robots?

Thanks for any suggestions!

---

### Post by kidders on 2007-02-02
Hi there,

> Would it maybe be necessary to set up a firewallA firewall is an essential utility for any computer!

I occasionally have reason to block or discourage persistent "visitors" to my web server. Sometimes, an **iptables ..... -j DROP** is the most appropriate thing to do, but you can also use server-side scripting to fake, say, 404 HTTP response codes for certain requests or user agents. It depends on the effect you're after, I suppose.

**Edit:** You mentioned robots.txt. If spiders that ignore them irritate you, you can always trap and block them, by tempting them to spider a link your robot rules explicitly disallow. A short script could monitor your apache logs and automatically tweak your firewall to drop packets from the offending IP. Low-tech, but effective!

---

### Post by PurplePenguin on 2007-02-02
I've actually got my server hiding behind a hardware router/firewall, just forwarding any port 80 requests to it (although I'm going to change this tomorrow, since I don't want my ISP to know what I'm doing with my internet access!). :)

Your suggestions are basically what I was after.  I'll do some more research this weekend and see what I can set up.  Thanks! :)

---

### Post by kebes on 2007-02-02
If you want a simple GUI way of editing firewall rules, you can install the package "firestarter". It creates a default software firewall in Linux, and makes it easy to update the rules. You can then identify the IP address of this robot, and set add it to the ban list.

You can also add addresses to the file "/etc/hosts.deny" in order to prevent them from being granted system access.

---

### Post by PurplePenguin on 2007-02-03
I actually decided to keep my server gui-free... I wanted to learn a bit more about ssh and whatnot, so I didn't even install any graphical stuff on the server.  I do use firestarter on the other computers in my network - it's a fantastic frontend!

Using hosts.deny is a good idea!  I didn't even think of it, although now you mention it, it makes a lot of sense.  

I did some searching here on the forum and found "sudo iptables -A INPUT -s XXX.XXX.XXX.XXX -j REJECT", with the Xs replaced by the ip address.  This seems to work as well.

---

### Post by Miademora on 2007-02-03
Another approach would be to just exclude the robot from the webserver logs or the stats program

If your problem is only feeling bad i would just ignore it and learn to live with them.

---

### Post by tturrisi on 2007-02-03
You can use robots.txt to control what bots can and can't do.
[http://www.robotstxt.org/wc/exclusion-admin.html](http://www.robotstxt.org/wc/exclusion-admin.html)

---

### Post by kidders on 2007-02-03
> **tturrisi said:**
> You can use robots.txt to control what bots can and can't do.Unfortunately, as the o/p mentions, the majority of bots ignore it.

---

### Post by tturrisi on 2007-02-03
then if running apache use an .htaccess file to block bots
[http://linuxreviews.org/webdesign/htaccess/](http://linuxreviews.org/webdesign/htaccess/)

---

### Post by kidders on 2007-02-03
> **PurplePenguin said:**
> I did some searching here on the forum and found "sudo iptables -A INPUT -s XXX.XXX.XXX.XXX -j REJECT", with the Xs replaced by the ip address.One minor suggestion: Change **-A** to **-I**.

People often put general operational rules at the start of an iptables chain. If, for example, your INPUT policy was DROP (which it probably should be), and you had your INPUT chain configured to accept all traffic on port 80, *appending* a host-specific REJECT rule would fail, since packets would already have been accepted.

Just something to be aware of. :-)

---

