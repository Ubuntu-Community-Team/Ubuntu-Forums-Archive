---
title: "Comcast Domain Helper hijacks address bar search"
date: 2009-10-10
forum: The Cafe
---

### Post by brookie on 2009-10-10
Hi all, 

I just had a weird experience where I logged into my comcast.net account to check on some email filters that were not working, then logged out. Listened to some tunes, and farted around, then hopped on my pc and typed in my FF address bar something about "playing movies on samba share hang", and...voila...

I got a comcast.net search page instead of my usual google search page. :confused: So, I did some googling and found that Comcast has implemented a domain helper. To opt out you have to log in to your account and turn it off! 

[https://dns-opt-out.comcast.net/](https://dns-opt-out.comcast.net/) 

A similar thing happened when I was using Charter in Oregon. Dang hijackers! 

[http://ww11.charter.net/options](http://ww11.charter.net/options) 

So now they want to drive my browser. Hope this helps some of you who's address bar search got hijacked. 

Cheers, 
Brookie

---

### Post by jrothwell97 on 2009-10-10
Gah. Virgin Media have started doing this too of late, but IIRC it doesn't affect Firefox's built-in search and it can be turned off without logging in.

---

### Post by madhi19 on 2009-10-11
Change your DNS server to Open DNS that should prevent comcrap from ever messing with you that way. 
208.67.222.222
208.67.220.220

---

### Post by JillSwift on 2009-10-11
> **madhi19 said:**
> Change your DNS server to Open DNS that should prevent comcrap from ever messing with you that way. 
208.67.222.222
208.67.220.220
I recommend this route. OpenDNS is not only less stupid about "helping" you, it's noticeably faster than Comcast's DNS.

---

### Post by Dr. C on 2009-10-11
Or install Bind9 from the repositories and run your own DNS. The best part is when one finds out a week later that your ISP had a day long DNS outage.

---

### Post by brookie on 2009-10-11
Thanks madhi19 and JillSwift,

I set up open dns ip's on my machines and routers. We'll see how it works. FineE, I'll check out that Bind9 as soon as I research it. 

The only thing that still bugs me is that when for instance, I type 'youtube' in the address bar I want the browser to go to 'youtube.com' automatically like it used to. 

Now with open dns, I get the open dns guide page asking me if I meant youtube.com? Of course I did. ;) 

I'll give it a shot for a spell anyhoot. 

Cheers,
Brookie

btw, sites really do seem to load faster using open dns. or am i placeboing? :P

---

### Post by brookie on 2009-10-11
madhi19 and JillSwift, 

I changed the ips to the open dns ips. everything is working but I have a question. I watched the tutorial on open dns website and they recommend creating an account with them and setting it up. Is this necessary? 

Also, their site will grab my Comcast ip address but when I go work in Oregon, I'll be using a different modem and using Charter so would I have to set up that network also? 

It seems like I'm using their DNS servers just by adding the ips to my router and machines so what are the pros or cons of creating an opendns acocunt and setting it up? 

Cheers

---

### Post by madhi19 on 2009-10-11
No I never did and you don't need to either. Open dns is so great it the very first thing I setup after any clean install. They filter a lot of crap and it the best protection against dns spoofing.

---

### Post by CarpKing on 2009-10-11
I tried OpenDNS, but the redirects bothered me.  If they bother you, check out [this site](http://www.tech-faq.com/public-dns-servers.shtml).  It has a list of free public DNS servers, at least some of which don't have redirects.  Set them up the same way you did OpenDNS (which is one of the entries on the list).

---

### Post by LookTJ on 2009-10-11
> **madhi19 said:**
> change your dns server to open dns that should prevent comcrap from ever messing with you that way. 
208.67.222.222
208.67.220.220+1

---

### Post by brookie on 2009-10-11
Great info all around. :) 

I did some googling and found some info on dslreports about a dns benchmark tool. I went to [this]("http://www.grc.com/dns/benchmark.htm") site and downloaded their free dns benchmark utility tool and ran it in winxp in my virtualbox. 


He also has an online spoofability test [here]("https://www.grc.com/dns/dns.htm") 

Pretty interesting results and cool tool if any of you have access to windows for the utility. 

Enjoy, 
Brook

---

### Post by Joe Munster on 2009-12-07
[B][SIZE=3]http://code.google.com/speed/public-dns/[/SIZE]
[/B]

**Google Public DNS**

  **What is Google Public DNS?**

 Google Public DNS is a free, global [Domain Name System]("http://en.wikipedia.org/wiki/Domain_name_system") (DNS) resolution service, that you can use as an alternative to your current DNS provider.  
To try it out: 

[LIST]
[*]Configure your network settings to use the IP addresses 8.8.8.8  	and 8.8.4.4 as your DNS servers or
[*]Read our [configuration instructions]("http://code.google.com/speed/public-dns/docs/using.html").
[/LIST]
 If you decide to try Google Public DNS, your client programs will perform all DNS lookups using Google Public DNS. 

+++++++++++++++

make the change on your router. :p

---

### Post by macmike on 2010-05-26
How do you setup open DNS instead of comcast?

---

### Post by libssd on 2010-05-26
If you use Chrome, this won't happen. It's also about 4X faster than FF.

---

