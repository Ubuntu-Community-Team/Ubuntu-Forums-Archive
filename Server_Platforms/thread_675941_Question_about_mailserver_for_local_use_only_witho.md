---
title: "Question about mailserver for local use only without internet domain"
date: 2008-01-23
forum: Server Platforms
---

### Post by yanny on 2008-01-23
Hi folks,

Well, I'm wondering, my goal is to set up a mailserver in vmware and use it for local only, so it doesn't need to be accessed outside (internet).

Do I need to buy an internet domain?

I also want to make the website (webmail) to use with the mailserver in PHP.

Is it possible what I'm doing? 

I've already installed Postfix, Courier and some security software (like anti-spam, firewall, virus-scanner etc..) 

On the internet I saw a lot of tuts about this, but I got crazy when it says $mydomain = example.com or $myhost = example.com. I don't have a domain and I don't want to purchase as I use it intern. What value do I have to complete there?
 
Do you guys knows a good tutorial voor local mailserver on LAN network? 

Thanks!!

---

### Post by HermanAB on 2008-01-23
You can make up a domain name for your own use, but it is generally better to use your ISP domain name if you don't have one, since then you won't eget errors from reverse DNS querries.

---

### Post by yanny on 2008-01-24
If I make up a domain name then I don't need to register it, right?

Can I use virtual domain (localhost) as well?

---

### Post by HermanAB on 2008-01-24
Ferinstance:
My ISP is Telus with domain name telus.net

So I give my server the hostname myserver.telus.net 

Then define the address in /etc/hosts:
w.x.y.z myserver.telus.net

and ensure that when I type 
$ hostname
that whole long name pops up.

Now if you install a mail server, it will think that you have a real domain name, since the hosts file makes the address resolve properly and a reverse lookup will resolve to your ISP.  So although the name actually only exists locally, the mail server software will be purrrfectly OK with it.

Cheers,

Herman

---

### Post by yanny on 2008-01-24
I have telfort as internet provider, I can use telfort right?

But then it's somehow strange, I mean I have installed a mailserver on Ubuntu (linux) in vmware (virtual machine) so when I take it too school I install vmware and then use that image as you know school has another ISP... by the way do I have to open up ports etc..?

I don't get it at all, yeah I'm a noob.. I have no experience with this at all.. I use it for local so why use an ISP.. :( I don't want to buy a domain...

---

### Post by HermanAB on 2008-01-24
Yes, you have to open the mail ports in your firewall.  Once you have the domain names sorted out, just leave it alone - it'll keep working.  The reverse DNS lookup is done by most mail servers as a spammer test.  As long as it resolves somehow, then you are OK.

---

