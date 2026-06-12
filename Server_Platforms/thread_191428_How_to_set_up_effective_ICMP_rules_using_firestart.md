---
title: "How to set up effective ICMP rules using firestarter"
date: 2006-06-07
forum: Server Platforms
---

### Post by raffytaffy on 2006-06-07
I want to set up proper ICMP filter rules using firestarter:) I'm paranoid i guess... lol
Anywho..i see 9 diferent icmp allow/deny packet types. I have two questions..
I set it up like this ALLOW- echo reply , timestamping , unreachable , adress masking , source quenching  DENY - echo request , MS traceroute , traceroute , redirection...<-- is this a right set up...and second question...given i use icmp filtering rules..can this interfere with torrents or any other ftp /http functions?

---

### Post by lcg on 2006-06-07
> **raffytaffy]I want to set up proper ICMP filter rules using firestarter:) I'm paranoid i guess... lol[/QUOTE]
Yes, it definitely seems so.  said:**
> I set it up like this ALLOW- echo reply , timestamping , unreachable , adress masking , source quenching  DENY - echo request , MS traceroute , traceroute , redirection...<-- is this a right set up...
This question cannot be anwered. At least not the way you asked it, without giving any details about what you want to protect yourself from.

It's similar to asking a question like "Will a condom protect me?"
The answer to that is (most probably) yes, if we're talking about HIV. However, if someone asked that question and then ran a motorcycle head-on into a wall at 100 mph, I guess one would have to answer no. (Kids, don't try this at home! ;) )

[QUOTE=raffytaffy]and second question...given i use icmp filtering rules..can this interfere with torrents or any other ftp /http functions?[/QUOTE]
Well, judging from what you wrote, I don't think it could have any ill effect on torrents or HTTP/FTP. (BTW, where is the logic in allowing "echo replies" if you are filtering the "echo requests"?)
But then again, ICMP has been developed for a reason and ICMP messages are pretty harmless. So, unless you have a good reason to block them I recommend you don't.

HTH,
Lars

---

### Post by LordHunter317 on 2006-06-07
The only ICMP request it's definitely safe to unconditionally block is ping.

But if you're explictly blocking ***anything*** (and definitely for ICMP) , you're almost certainly writing your rules incorrectly.

If this is a desktop, you likely don't need a firewall.  If it runs no servers, it doesn't need a firewall.  If you have a home router, then it doesn't need a firewall.

---

