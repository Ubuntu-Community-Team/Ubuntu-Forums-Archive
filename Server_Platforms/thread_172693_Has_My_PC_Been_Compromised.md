---
title: "Has My PC Been Compromised?"
date: 2006-05-09
forum: Server Platforms
---

### Post by GordSellar on 2006-05-09
I connect to the University network where I work because I live on campus. Today, around noon, my internet connection was shut off because the sysadmins suspected my computer had been compromised and was being used for a DOS attack. Now, the school runs on a Windows server, and the admin guys seemed to be surprised anyone was using Linux at all, but the strange thing was, they said they thought my PC had been compromised, and I ought to reinstall my OS. I don't necessarily mind doing it, but I want to make sure they just didn't misinterpret something that was not a DOS attack.

The reason I doubt their interpretation is because it seems very strange to me for a couple of reasons: for one, another of my computers was taken offline for a similar reason, but it's running Windows. The only thing the two systems have in common is that Azureus was running on both, so it's possible, I suppose, that a worm was attacking via that route. However, there was something else strange. 

The sysadmin showed me a list of the supposed "attacks" and later, while trawling about my logs for information, I found a matching record of them online in my user.log, and it looks like anon-proxy was just screwing up:

May  7 07:37:27 localhost AnonMix: [2006/05/07-07:37:27, info    ] Try connecting to next Mix... 
May  7 07:37:27 localhost AnonMix: [2006/05/07-07:37:27, critical] Cannot connect to next Mix! 
May  7 07:38:27 localhost AnonMix: [2006/05/07-07:38:27, info    ] Try connecting to next Mix... 
May  7 07:38:28 localhost AnonMix: [2006/05/07-07:38:28, critical] Cannot connect to next Mix! 
May  7 07:39:28 localhost AnonMix: [2006/05/07-07:39:28, info    ] Try connecting to next Mix... 

There are hours and hours of that in the log. Now, I left the PC on all night, and from about midnight last night to sometime around noon today, I got this kind of thing happening. It tried to connect, and a minute later it tried again. 

So I'm thinking that my PC wasn't actually compromised... that it was just Anon-Proxy ganking out on me. Does that sound about right?

It does, however, seem weird to me since my Windows PC seems to have provoked a similar reaction on the same night. This is what makes me wonder if maybe someone did do something via Azureus. 

The sysdamn also gave me a target address for this ostensible DOS attack -- it was 202.98.116.66 ... does that mean anything to anyone? He couldn't track it because it was outside Korea, or so was the implication I got. We were communicating across a language barrier. 

Also, since the Anon Proxy failure was so easily trackable to my IP, does it make any sense to even bother to reinstall it? And what kind of security measures do you recommend for a newbie who's just using some P2P, surfing, maintaining websites, and that sort of thing?

Thanks for any help you can offer!

---

### Post by Azrael on 2006-05-09
Unable to say, so far.

> The sysadmin showed me a list of the supposed "attacks"
Can you elaborate this?

Also, can you list all the services you were running (that are accessible from a remote location)?

---

### Post by Sef on 2006-05-09
> The sysdamn also gave me a target address for this ostensible DOS attack -- it was 202.98.116.66

That address is in China.

---

### Post by GordSellar on 2006-05-09
[quote=Azrael]Unable to say, so far.


Can you elaborate this?

Also, can you list all the services you were running (that are accessible from a remote location)?[/quote]

I don't know how to find out. Where would I look for such a list? I haven't enabled or disabled anything. (I'm listed as having been a member of the forums since September but only really started using Ubuntu since March, so I am a pathetic newbie. 

Thanks!

---

### Post by Azrael on 2006-05-09
A default Ubuntu install doen't have any network services running (you can use a portscanner to check this), so unless someone had physical access to your computer or you installed software from an untrusted source, the chances of being compromised are quite small.

But what list of supposed attacks did the sysadmin show you? 

>  The sysdamn also gave me a target address for this ostensible DOS attack -- it was 202.98.116.66
I found this page with Google: [http://greatinca.net/blog/emule-ip-blocker-hits-04022006/]("http://greatinca.net/blog/emule-ip-blocker-hits-04022006/") Have a look at the very first IP address on this page. I think this supports your suggestion that this may be bittorrent/Azureus related. I don't know what kind of abnormal (bittorrent?) traffic took place between that IP address and your computer but it's definitely worth looking into.

---

### Post by GordSellar on 2006-05-09
[quote=Azrael]A default Ubuntu install doen't have any network services running (you can use a portscanner to check this), so unless someone had physical access to your computer or you installed software from an untrusted source, the chances of being compromised are quite small.

But what list of supposed attacks did the sysadmin show you? 

 I'd try to find out if your proxy software was trying to connect to that address, if possible. Btw, I found this page with Google: [http://greatinca.net/blog/emule-ip-blocker-hits-04022006/]("http://greatinca.net/blog/emule-ip-blocker-hits-04022006/") Have a look at the very first IP address on this page. I don't know how these pieces fit together, but I doubt it's coincedence...[/quote]

The sysadmin plugged my cable into his PC, checked the network records, and then showed me a bunch of attempts to connect to the address I mentioned. He characterised them as "attacks", probably because, according to the server logs (I think it would be) my computer was logged as having attempted to connect to that IP once per minute for something like 12 hours straight.

I was running Amule, so it's possible Amule was trying to download from a bogus peer or something. Actually, I was running Azureus, too, and that IP seems to be listed as a Bittorrent Corrupt Data Sender on several sites. It would also help the situation with my other (Winbox) machine make sense, because it, too, was running Emule or Azureus (I'm not sure which, maybe both) at the time. 

So I guess I should install some kind of virus scanner? And look for logs to see what program was trying to do what? But I scoured the logs and this was the only clear reference I got. Hmmmmm. Any ideas where I could look for any of the info? And also just to make sure nothing's remotely accessible?

---

### Post by GordSellar on 2006-05-09
[quote=GordSellar]The sysadmin plugged my cable into his PC, checked the network records, and then showed me a bunch of attempts to connect to the address I mentioned. He characterised them as "attacks", probably because, according to the server logs (I think it would be) my computer was logged as having attempted to connect to that IP once per minute for something like 12 hours straight.[/quote]

Scratch that, it was having this error for several days straight. I didn't look in the logs, so I had no idea. I think I must have configured anon-proxy wrong or something. 

Of course, that doesn't mean nothing bad happened last night, but it makes me suspect it was anon-proxy that caused the problem. A repeated failure to connect by an anomalous looking agent - AnonMix - is probably what worried the sysadmin guy. 

If I haven't set anything to be accessible remotely, I should also feel secure that it's very unlikely a bat chunk of data infested my system via Emule or Azuerus, right? Should I install a virus scanner or something? Is there any security anyone recommends to me? (I tried installing a few things and they ganked out on me, I'm going to go try again I think.) 

](*,) Thank you for all this help. I do appreciate it.

---

### Post by zac_zhou on 2006-05-23
I can tell you that your computer is not compromised. Add that IP to your ipfilter.dat. I have tracked that ip for some times. Its purpose is just sabotaging the Kademlia network used in emule/amule in my observation.

---

### Post by GordSellar on 2006-05-23
Zac_Zhou, 

Thanks. I pretty much came to that conclusion. Is there a collected list of bad IPs that can be added to the ipfilter list? It cannot be dynamically updated from a trusted source, can it?

---

