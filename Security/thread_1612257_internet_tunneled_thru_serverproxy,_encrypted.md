---
title: "internet tunneled thru server/proxy, encrypted???"
date: 2010-11-02
forum: Security
---

### Post by krack3rz on 2010-11-02
I'm still a bit green to Linux, and not really even sure if this is possible and if it belongs in securities area but here it goes:

Is it possible for me to establish an encrypted connection to my home-comp (on 24/7) so that I surf the web? If yes, help find some direction or solution :KS

what I mean is, I want to make sure the place where the internet connection is monitored and throttled or denied completely is bypassed and doesn't know what I'm browsing exactly but instead just passing as it will see gibberish data to my home-comp and back of data my home computer accesses via a different route???
maybe 1k rsa encryption? or better? like ssh server I run 2048-bits? (not very good at using cmd line to do advanced things)

I guess its like a "zombie" machine which acts as a host to relay data...

This is to be done like this:
Laptop(with unknown/untrusted wifi connection) --encrypted--> home-comp. --not encrypted--> some site.
then:
some site --> home-comp. --encrypted--> my laptop :)
it would be awesome :guitar:
Addition:Most it must be automatic...so that it isn't necessary to type in cmd line for every web page.

---

### Post by HermanAB on 2010-11-03
Yes,

That is how I always work.  

You need to rent a server in a friendly country, then use SSH and set up a Socks proxy connection and tunnel all your traffic over that.  Not difficult, just a one liner, but it does require familiarity with SSH and of course it will cost you $50 to $100 per month for the server.

---

### Post by krack3rz on 2010-11-03
> **HermanAB said:**
> Yes,

That is how I always work.  

You need to rent a server in a friendly country, then use SSH and set up a Socks proxy connection and tunnel all your traffic over that.  Not difficult, just a one liner, but it does require familiarity with SSH and of course it will cost you $50 to $100 per month for the server.

thats awesome, but 2 things:
1. i wanna use my home comp. so it wont cost me anything (i already have auth keys on ssh online and working great!)
2. how do I do this? i can, like always, log into my home-comp. via ssh via terminal but I wanna use laptop normally, but firefox automatically sends requests to wifi --> "some wifi" --encrypted-> home server/comp --> internet, then back retracing steps.

so the most important thing is I need it to do this by itself so I will see firefox as if I am normally using it.

any HowTo's out there? I mean, i don't even know what I'm lookin for...

---

### Post by HermanAB on 2010-11-03
Go to [http://google.com/linux](http://google.com/linux) and search for "SSH Sock Proxy Firefox".

---

### Post by krack3rz on 2010-11-04
thanx mate!

This is the first time i've seen the google/linux search! Its pretty nifty :)

thanx again

---

