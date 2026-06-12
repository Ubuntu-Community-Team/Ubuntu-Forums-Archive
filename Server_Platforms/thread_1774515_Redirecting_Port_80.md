---
title: "Redirecting Port 80"
date: 2011-06-03
forum: Server Platforms
---

### Post by poker158149 on 2011-06-03
Hi everyone.

My ISP blocks port 80, so I had to change the port my site is on. How can I make it so that when someone visits my site, it automatically redirects them to the new port? I know they can manually type it in, but that's just a pain. Is this possible to do without any third-party sites or third-party applications, or are those required?

---

### Post by lykwydchykyn on 2011-06-03
There's no way to do this without a third-party workaround of some sort.  When you put a URL into a web browser, there's an implied :80 on the end -- in other words, it's always going to hit port 80 first.  If that's blocked, nothing you try to do on your server is going to get through.

---

### Post by HermanAB on 2011-06-03
There is a very simple fix actually.  Upgrade your account to a small business server account.  It will cost about $10 a month more than your current home user account.

---

### Post by poker158149 on 2011-06-03
That's what I figured. Well, using third-party applications, what would be the easiest way to do it?

---

### Post by lykwydchykyn on 2011-06-03
> **poker158149 said:**
> That's what I figured. Well, using third-party applications, what would be the easiest way to do it?

 - Find a free webhost
 - put a page there with a redirect to your server at whatever port

Better make sure you aren't violating your ISP's TOS, though.  You can get web hosting dirt cheap these days, I pay about $50/yr for a deluxe package from my webhost.

---

### Post by poker158149 on 2011-06-03
I don't want to have to go to another webhost, especially not one that gives me some cheesy subdomain just to get to my site. I saw someone saying something about iptables?

---

### Post by ruffEdgz on 2011-06-03
I have another question:
---
What port are you using now and which port do you want them to go to?
---

iptables can be used but will need to know what you are thinking to see if its doable. 

The main concern I see in this is you want people to get to you site (i.e. mysite.com) without using a port to get to it (mysite.com:8080) and iptables can not fix that if your ISP is blocking port 80.

---

### Post by poker158149 on 2011-06-03
It's still going to port 80 as of right now, and I'm trying to get it to go to port 81 without having to actually type in mysite.com:81. Port 81 has my active site on it.

---

### Post by CharlesA on 2011-06-03
They have a port redirector thing at [no-ip]("http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html"). Not sure how well it works.

---

### Post by poker158149 on 2011-06-03
I've tried no-ip, and it works quite well, but they make you use one of their subdomains.

---

### Post by CharlesA on 2011-06-03
> **poker158149 said:**
> I've tried no-ip, and it works quite well, but they make you use one of their subdomains.
Ah thanks. I didn't know that.

---

### Post by lykwydchykyn on 2011-06-03
> **poker158149 said:**
> I don't want to have to go to another webhost, especially not one that gives me some cheesy subdomain just to get to my site. I saw someone saying something about iptables?

If iptables can help, I can't imagine how.  Like I said before, if someone types your URL into their browser, the browser resolves the URL to an IP, then contacts that IP **on port 80**. 

If your ISP is blocking port 80, then they aren't even going to be able to reach your server to begin with (without manually specifying another port), so any trickery on the server is moot.

---

