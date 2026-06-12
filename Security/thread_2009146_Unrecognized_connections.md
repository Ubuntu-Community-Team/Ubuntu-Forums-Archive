---
title: "Unrecognized connections"
date: 2012-06-24
forum: Security
---

### Post by aligator12 on 2012-06-24
Hi, I ran the netstat -netp command and I see connections I don't recognize. Is it safe to post them here?

---

### Post by aligator12 on 2012-06-24
The reason I decided to look is because I was browsing the web and got jacked to the website jobs.retailjobsweb.com. So did this site infect me?

---

### Post by aligator12 on 2012-06-24
Anyone? And please take a look at this:
[http://sitecheck.sucuri.net/results/jobs.retailjobsweb.com](http://sitecheck.sucuri.net/results/jobs.retailjobsweb.com)

---

### Post by OpSecShellshock on 2012-06-24
It should be perfectly fine to post the netstat output here. You can obscure your own IP address if it's not NATted.

What were the circumstances around getting linked to the blacklisted site? The Sucuri scan doesn't appear to have found any malware on the page, but it does bear some similarities to search result hijacks and/or click fraud.

---

### Post by aligator12 on 2012-06-24
Should I have censored anything above? Thanks.

---

### Post by aligator12 on 2012-06-24
And should I have run that root?

---

### Post by Soul-Sing on 2012-06-25
> **aligator12 said:**
> And should I have run that root?

please run a
```
netstat --all --programs
```
please post the outcome?

and a
```
sudo netstat --all --programs | grep '*:'
```

---

### Post by aligator12 on 2012-06-25
> **leoquant said:**
> please run a
```
netstat --all --programs
```
please post the outcome?

and a
```
sudo netstat --all --programs | grep '*:'
```
Hi, after running the 
```
netstat --all --programs
```
it got to long and cut off the text.

How can I stop it from cutting off so I can post the whole log?

Also, I decided to try to randomly lookup some ip addresses and one of them I looked up was registered to "Road Runner" (107.14.43.169), and I have been receiving spam from road runner, even to email accounts I only registered here at ubuntu forums, see this thread here:
[http://ubuntuforums.org/showthread.php?t=1978593&page=2](http://ubuntuforums.org/showthread.php?t=1978593&page=2)

What do you make of this?

---

### Post by aligator12 on 2012-06-25
Anyone?

---

### Post by Soul-Sing on 2012-06-25
91.189.89.22(:80) is ubuntu/canonical
geo-ip = ubuntu/canonical
i don't see any strange things.
74.125.45.99= google inc.

---

### Post by aligator12 on 2012-06-25
> **leoquant said:**
> 91.189.89.22(:80) is ubuntu/canonical
geo-ip = ubuntu/canonical
i don't see any strange things.
74.125.45.99= google inc.
What about 107.14.43.169?

---

### Post by Soul-Sing on 2012-06-25
> **aligator12 said:**
> What about 107.14.43.169?

a US Internet service provider (ISP) (Road Runner HoldCo LLC)

---

### Post by aligator12 on 2012-06-25
> **leoquant said:**
> a US Internet service provider (ISP) (Road Runner HoldCo LLC)
I know, but I don't use Road Runner, I use a different isp. But the thing is, is that I have received a good bit of spam in 3 separate email accounts from rr.com and now I notice that connection.

---

### Post by Soul-Sing on 2012-06-25
> **aligator12 said:**
> I know, but I don't use Road Runner, I use a different isp. But the thing is, is that I have received a good bit of spam in 3 separate email accounts from rr.com and now I notice that connection.

but you did start this thread with
> I was browsing the web and got jacked to the website jobs.retailjobsweb.com. 

why did you think your jacked? other than the information you gave us?

your additional information:
> But the thing is, is that I have received a good bit of spam in 3 separate email accounts from rr.com and now I notice that connection

How serious is this spam? I mean who doesn't receive spam from time to time......

---

### Post by aligator12 on 2012-06-25
> why did you think your jacked? other than the information you gave us?
Because I was browsing a seedy site with lots of ads.

> How serious is this spam? I mean who doesn't receive spam from to time......
Well, I created 3 separate yahoo email accounts (one I only used to register to this site) and everyone of them began receiving spam from rr.com.

And how do I see every outgoing connection? Because every command I have run so far creates a log so large it cuts off.

---

### Post by Soul-Sing on 2012-06-25
> Well, I created 3 separate yahoo email accounts (one I only used to register to this site) and everyone of them began receiving spam from rr.com.

you could block the ip address via ufw/gufw.
you think you'r "infected" but netstat, ```
netstat -netp
```
or ```
watch netstat -netp
``` gives no information you'r in danger. [COLOR="Red"]Not every ip adress showing up is a "danger"[/COLOR].

if you want to harden your system please read this wiki:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
learn about ufw/gufw,netfilter, and inbound/outbound rules.

take your time to get fam. with this stuff. and relax.

just because i am curious, what gives: ```
netstat -taupen
```

---

### Post by aligator12 on 2012-06-25
> gives no information you'r in danger. Not every ip adress showing up is a "danger".
Well if you think I am fine, then I will take your word for it. But I have one more question out of curiosity, why do I have so many connections to google?

---

### Post by CharlesA on 2012-06-25
They are in the TIME_WAIT status, it's normal.

That netstat looks fine to me.

---

### Post by emiller12345 on 2012-06-27
> **aligator12 said:**
> why do I have so many connections to google?
Google is massively integrated.  Just about every website you go to has been integrated with google. Even your firefox browser has default built in links to [http://safebrowsing.clients.google.com](http://safebrowsing.clients.google.com) (in the about:config section). It is very hard to not connect to google.

---

