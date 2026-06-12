---
title: "are proxy server programs safe"
date: 2009-11-13
forum: Security
---

### Post by kiridude on 2009-11-13
Hi, I was wondering if programs such as the ones offered by freedur and hidemyass were safe. In other words, are those programs doing anything they shouldn't be once installed on my machine?

Also, if anyone can suggest a better alternative, it would be much appreciated.

Thanks

---

### Post by ld.4lpha on 2009-11-13
I haven't used either of those, so cannot vouch for them.

There are free options though.  Depending on what level of anonymity you need, you could use something like libertybell.biz or Tor. 

If you're wanting more anonymity and don't want your ISP to see your activity, you'll need an end-to-end tunnel.  At first glance, it looks like hidemyass does this.

To simply prevent analytics software from recording your IP and geolocation, you could get by with libertybell or Tor.  Keep in mind that any of these options will decrease browsing performance.

With a better idea of what you're trying to do, specifically, perhaps I can provide more detailed information.

---

### Post by kiridude on 2009-11-14
Thanks for your feedback ld.4lpha.

Libertybell didn't work very well and the popups were a pain in the ***. Tor works well but is REALLY slow.

I basically want to access tv sites like Hulu that are only available to residents of the US. My thinking is that a program I pay for will be of higher quality than the free stuff. I have no problem paying programmers for their hard work. My only qualm is that I don't really know what closed source programs are doing behind the scenes.

---

### Post by unspawn on 2009-11-14
> **kiridude said:**
> I basically want to access tv sites like Hulu that are only available to residents of the US. 
If you posted that reason in your OP then nobody would have needed to waste time with suggesting anonymizing services. (It also means it really is not a security forum issue but a networking one.) What you want is just to subvert access restrictions. TOR was never made for that kind of stuff and using it for your own high-bandwidth purposes only helps saturate circuits and we're not even talking about the overhead TOR requires for anonymizing which you obviously don't need. 

I do not know if bypassing access restrictions is against the forum rules but what you need is just access to an(y) open proxy that falls within their acceptable ranges. Lots of sites list open proxy addresses, you just have to test them yourself and be aware that routing traffic through servers you have no access to exposes you to whatever the proxy owner does.

---

### Post by kiridude on 2009-11-14
> **unspawn said:**
> If you posted that reason in your OP then nobody would have needed to waste time with suggesting anonymizing services. (It also means it really is not a security forum issue but a networking one.) What you want is just to subvert access restrictions. TOR was never made for that kind of stuff and using it for your own high-bandwidth purposes only helps saturate circuits and we're not even talking about the overhead TOR requires for anonymizing which you obviously don't need. 

I do not know if bypassing access restrictions is against the forum rules but what you need is just access to an(y) open proxy that falls within their acceptable ranges. Lots of sites list open proxy addresses, you just have to test them yourself and be aware that routing traffic through servers you have no access to exposes you to whatever the proxy owner does.


Please re-read my OP. 

When you do, you will notice that I was asking if hidemyass and similar programs are safe to install - meaning, do they keep logs, compromise my machine, etc. This question seemed like a security question to me.

From there, the conversation took a turn to _one_ of the reasons I wanted to use such programs, and I thank ld.4lpha for taking the time to try and help. He was the only one. My knowledge of proxy servers and VPNs is limited and I am trying to learn more. This is usually the reason people post and discuss on this forum.

You sound irritated that I don't know exactly what I'm doing, and you accuse me of "wasting" people's time when you didn't read the OP carefully. And what's the point of suggesting I use an open proxy when you point out the obvious security problems with that?

---

### Post by unspawn on 2009-11-14
> **kiridude said:**
> you will notice that I was asking if hidemyass and similar programs are safe to install (..). This question seemed like a security question to me.
Yes, you're right about that.

---

### Post by ld.4lpha on 2009-11-16
> **kiridude said:**
> Libertybell didn't work very well and the popups were a pain in the ***. Tor works well but is REALLY slow.

I basically want to access tv sites like Hulu that are only available to residents of the US. My thinking is that a program I pay for will be of higher quality than the free stuff. I have no problem paying programmers for their hard work. My only qualm is that I don't really know what closed source programs are doing behind the scenes.

Since you need good performance (and you're right that LB and Tor are really slow), your best bet may be to go with a paid service. 

I understand your concern with closed source; if you're really concerned about it, you could install the software in a VM to keep it off of your production OS.

Sorry for the tardy reply.

LD

---

### Post by BelzeBob on 2009-11-17
Hi

My first post here. Yes, newbie myself. I've tried various things like Tor, but without much success. And on Windows I've tried "Hide my IP". Reduced browsing speed (or no browsing at all) is a problem. It can also be that I haven't managed to install Tor like I'm supposed to. Installation isn't that straightforward. Maybe I'm not skilled enough.

Anyways: you can always use (without installing/configuring anything) hidemyass.com or some online service like that- for when you really feel the need to be anonymous. Or - when f.ex your school or workplace blocks access to the site you want to go to.

If anyone has a simple to follow (step-by-step, *exact* instructions) instruction for how to set up Tor on Linux/Ubuntu 9.10, then it'd be wonderful. I tried yesterday, but I couldn't get it right.

---

### Post by kiridude on 2009-11-17
For Tor, if you follow the directions on this [link]("http://www.torproject.org/docs/tor-doc-unix.html.en"), you should be good. If you get stuck somewhere, post back.

---

