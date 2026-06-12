---
title: "Are VPN as secure as claimed???"
date: 2023-03-03
forum: The Cafe
---

### Post by jpaulb on 2023-03-03
I have been using a VPN for years and never noticed this hidden feature until I tried to watch a live TV program from a European station. 
The VPN location is set Europe, CET; UTC +1. My Hardware clock set to UTC and my local time is set to my location which is UTC -5. We are looking at a 6 hour time difference.
It is 12:00 here and 18:00 in Europe. I went to a website; the live stream program that was available was one from **my** location time 12:00 not for the servers time 18:00.
To check this a little further I set my Location time to that of the servers and could watch the program that was available at the servers time.

In theory a server could still Geoblock requests if so wanted.

---

### Post by coffeecat on 2023-03-03
Not an Ubuntu support question. *Thread moved to **The Cafe**.*

---

### Post by DuckHook on 2023-03-03
The short answer glosses over so much that it is next to meaningless—but just for the heck of it: the short answer is "No".

However, the details are the real crux of the matter, so here they are:

[LIST=1]
[*]A VPN is only as good as the the VPN provider. This should be obvious. A VPN that is run by a shyster outfit can actually screw you over worse than not having one. Aside from the false sense of security, a VPN will capture everything that you send via their service. No other outfit is better positioned to slurp your data and sell it to all and sundry.
[*]For the above reason as well as others, I wish people would stop recommending VPNs as magic bullet solutions. They aren't. If you don't do the really hard work of researching VPNs and selecting the right one, you can do yourself more harm than good.
[*]This is where we again are our own worst enemies. Many fools (I'm not going to mince words) think that "free" VPNs are fine. This is beyond lunacy. Does anyone really think that a limited and expensive resource can be offered to billions of potential users for free??? Have I got a bridge I want to sell them!
[*]In the last three or four years, a number of VPNs that used to be reputable have been bought by malware authors and spam outfits. They used the vast profits from their sordid businesses to buy out more legitimate companies. They are doing this with antivirus as well, then either bundling their VPN offerings or upselling their AV customers on VPN. It's a bad, sad world out there these days on the AV/VPN front and it is the typical don't&#8209;know&#8209;don't&#8209;care Windows/Apple user that is getting screwed. Linux people *tend* to know better, but only because the majority of Linux users are geeks and more tech&#8209;literate.
[/LIST]
On the other side of things are the following:

[LIST=1]
[*]VPN technology is tried, true and solid. It is reliable. It has been stress&#8209;tested for years. It does what it claims to do.
[*]Therefore, if you use it with both eyes open, no false sense of security, with a good reputable VPN provider, you will get real security/privacy/anonymity.
[*]For example, I leverage VPN technology a lot. I've set up Wireguard on all of my mobile devices and link back to my home ISP. That way, my public WIFI connections are safely encrypted. Since I control both endpoints and the platform itself, I have 99% confidence in my setup.
[*]Banks use VPN connections over the Internet to tie in all of their branches. They too control all endpoints as well as the platform, so there is no third&#8209;party involvement. I daresay that such VPNs are safer than the steps you take to secure your personal physical safety and we all rely on it to keep our banking data safe.
[*]Corporations both large and small, as well as SOHO users, rely on VPNs to tie their IT infrastructure together securely. I VPN my data backups to a remote location and am 99% sure that it is secure and private. But I do consider myself a power user who knows how to configure VPNs properly and how to avoid the most common dangers.
[*]If you use cloudy services that are not under your complete control, on your own iron, then all bets are off. The moment you rely on other parties, all of the above is rendered inapplicable. As kernel devs would say, "the kernel has been tainted".
[*]There is no such thing as 100% safe. The easiest way to recognize an untrustworthy hypester is whether they make such claims. Even my own VPNs—in which I control both endpoints and rely on nobody by me—are at most 99%. Perfect security does not exist in any walk of life.
[*]There are still a few third party VPN providers that I trust enough to give my business to. They tend to be the ones who have been told by a court to hand over their logs and therefore have to prove that they don't keep any. Since the penalties for perjury are personal and not just corporate, I find such evidence convincing.
[/LIST]
That's the long, wordy answer, and I haven't even covered many aspects of it. As you can see, the issue is far too complex and nuanced for a short answer.

---

### Post by DuckHook on 2023-03-03
As for your query itself,

[LIST=1]
[*]If your VPN is not configured properly, it will leak DNS info. Your real location can be determined from this.
[*]If you are viewing through a web browser and have either/both location services and/or scripting turned on, this can also be used to determine both your real physical location and/or your local time zone.
[*]All streaming services have long been aware of the VPN gambit. There has always been an arms race between the VPNs switching IPs often enough to confound the streamers and the streamers blacklisting IPs that it determines to belong to VPNs. The only streamers who don't do this are organizations that don't really care all that much.
[/LIST]

---

### Post by TheFu on 2023-03-03
VPN is 10% of an anonymous way to access the internet.  The other 90% is user behavior, which is fairly unique. If you access any website using a VPN and non-VPN, then your behavior can be tracked.  A single mistake, just 1 time, is enough for a determined sleuth.   If you post any written content, the way you write is often unique and tools exist to find similar samples across the entire web.

Basically, there are many different aspects to "security". What I consider security isn't the same was what other people do, I suppose.  Friends who work in SIGINT jobs don't post anything online and never connect from their real system or without using a very secure VPN setup that they run themselves or using TOR with at least 3 intermediate nodes. Obviously, there are trade-offs. A number of these people don't have smart phones and are having trouble getting flip phones without GPS tracking for emergency needs, since GPS has been mandated for nearly 20 yrs in all cellular devices sold here.

---

### Post by jpaulb on 2023-03-04
Thanks. Wasn't sure where to put it.

---

### Post by zebra2 on 2023-03-08
**Are VPN as secure as claimed?**

VPN  are intended to provide security.  That is the claim. 
How much security varies with the application and the claim changes with the application. I will stick with my current experience here. Brave browser has a built in Tor VPN that you can use or not use. It only claims a not absolute security, but sufficient for most needs. The instructions given by Brave is that if you want a greater level of security the use the Tor Browser. At this point you shift to the Tor claims and leave tjhe Brave claims that uses built in Tor. So even the effectiveness of Tor depends on the application. If the result is good but not perfect it may still fit my needs. Hiding from someone in a cafe is different from hiding from the CIA.  If I need to hide from the CIA I just won't go there. If I want to hide from the cafe then Brave with Tor is probably sufficient. After all everything I do may not be everone's business but it can still be legal.
As with the rest of reality you have to read the small print but the small print is meaningless if it is a phoney VPN. If the phoney VPN accumulates a million dollars worth of sales and then gets caught it will simply disappear along with the million dollars. So it helps to filter the advise you are getting. For the last decade I have used the moderators on this site for the advise and have done pretty good. In a world where anyone can claim anything, be careful.

---

### Post by DuckHook on 2023-03-08
It's a crying shame that we live in a world where crooks can take over legitimate companies and corrupt them to serve their nefarious ends, but that's the way it is.

When it comes to 3rd party VPN providers, it is *caveat emptor*.

TheFu actually nails it. The vast majority of people focus too much on the technology and not enough on themselves. No VPN, no matter how honourable the company, can save you from yourself. If you visit bad sites, a VPN will not help. If you turn on geolocation and scripting, a VPN will not help. If you visit the same site with and without VPN, then your browser can be fingerprinted and you've just done an end run around your VPN. If you visit a site that hacks you, a VPN is just so much hot air.

The same applies to Tor browser. After all, it is just a fancy 3&#8209;step VPN that adds anonymity to privacy. But many people completely misuse Tor because they don't understand the most elementary aspects of what it exists for. They think of it as a magic wand. For example, they will use Tor for their banking. They don't stop to consider that Tor exists for anonymity, but the whole point of online banking is to identify yourself and ascertain your real identity. Using Tor for banking is sucking and blowing at the same time.

More of the same applies to VPN. There's no point doing your banking through a VPN unless your objective is to semi&#8209;safely tunnel out of that coffee shop WIFI. But if you are doing your banking from a coffee shop WIFI, then… words fail… you will be the author of what pain is coming to you is all I can say.

---

### Post by agentl074 on 2023-03-12
Virtual Private Networks are only as good as they are configured and maintained. This said, the best thing you can do is avoid doing sensitive transactions on public networks. Having said this, Linux is very secure -- so long as you're not opening yourself up....

---

### Post by bernard010 on 2023-03-14
Thanks for the info on VPN's. I have been curious for a long time. I will take your advice not using a VPN.

---

### Post by DuckHook on 2023-03-14
> **bernard010 said:**
> Thanks for the info on VPN's. I have been curious for a long time. I will take your advice not using a VPN.
I don't know whose advice you are referring to, but it's not mine. I am very much into using VPNs. I'm just very careful with them and do my research when it comes to 3rd party providers.

When it comes to my own VPNs, they are must&#8209;haves. I rely on them for safety and privacy. Unlike TheFU, I do use public WIFI, but I always VPN back to my home router so that I'm encrypted all the way. If you use public WIFI, you should consider doing the same.

Therefore, my advice is the opposite of your conclusion. Use VPNs, but ***learn to use them properly***.

---

### Post by bernard010 on 2023-03-14
I do not use public WiFi. Thanks for the info. I will do some research on VPN's.

---

### Post by TheFu on 2023-03-14
> **DuckHook said:**
>  
When it comes to my own VPNs, they are must&#8209;haves. I rely on them for safety and privacy. Unlike TheFU, I do use public WIFI, but I always VPN back to my home router so that I'm encrypted all the way. If you use public WIFI, you should consider doing the same.

Therefore, my advice is the opposite of your conclusion. Use VPNs, but ***learn to use them properly***.

Don't know how this was mixed up, but I use a VPN whenever I'm
a) on someone else's network
b) using wifi (even in my own home) - I don't trust wifi or any RF connections (like Bluetooth). At home, my computers don't use wifi 99.9999999999% of the time, so almost never.
c) with on a network I trust and I need to appear to be somewhere else for many, many, different reasons.

I wouldn't be able to perform some of my jobs without using a VPN.
I use a mix of VPNs that I run and VPNs run by others.  Generally, if I'm away from a trusted network, I'll use a VPN that I run.

But if I'm a home and doing home banking, then I'm not likely to be using a VPN for those connections.  I do take a number of other security steps for online banking, however.

---

