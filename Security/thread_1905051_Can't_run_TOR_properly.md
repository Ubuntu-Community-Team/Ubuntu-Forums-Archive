---
title: "Can't run TOR properly"
date: 2012-01-05
forum: Security
---

### Post by tgomes95 on 2012-01-05
So... I can't run TOR from my terminal. I have tried many different  things, but I couldn't make it run. Once, it didn't stop to run when I  wanted to. At my other attempt I also ended up failing because when it  stopped to run I couldn't connect myself to the internet. I hope you can  help me here guys. To be more specific, what I mean by "can't run from terminal" is that I  can't hide my IP if I'm installing a program from terminal, for  instance. Or if I'm running another program that is making a connection  with the internet, my IP isn't being hidden. What I want is to make TOR  work for all my programs. So my IP would be hidden in any connection  with the internet.

---

### Post by /dev/random/username on 2012-01-06
> **tgomes95 said:**
> What I want is to make TOR  work for all my programs. So my IP would be hidden in any connection  with the internet.

You dont want that.. unless you dont care about your "Privacy". You see TOR provides anonymity not privacy, and tor exit nodes relay traffic unencrypted.. you dont know who's running that exit node and is it being sniffed or not, unless you only use HTTPS for browsing the net then your connection is encrypted end-to-end.

EDIT: here is a link regarding TOR privacy [http://www.wired.com/politics/security/commentary/securitymatters/2007/09/security_matters_0920?currentPage=all](http://www.wired.com/politics/security/commentary/securitymatters/2007/09/security_matters_0920?currentPage=all)

---

### Post by tgomes95 on 2012-01-06
No... I want to do that. And be able to undo it whenever I want.

---

### Post by tgomes95 on 2012-01-06
Does anybody know what to do? = /

---

### Post by 0011235813 on 2012-01-06
> **tgomes95 said:**
> Does anybody know what to do? = /

I have some experience with this irritating program. Tor automatically startsup on my computer, and I configured firefox and thunderbird to use it to hide my IP (or should I say, give them a corporate identity from Dresden, not Manchester). I used FoxyProxy to do this. I installed it, then clicked on the icon, and then right-click-tor wizard. Easy if someone had bothered to mention it on FP page *sighs*. I don't know about terminal, this is as much as I got it working, and I won't try anything else, too troublesome.

---

### Post by tgomes95 on 2012-01-06
I see... TOR is a stubborn program. You don't even wanna mess with it when you get it to work.

---

### Post by Dangertux on 2012-01-06
Add tor to your global proxy settings

```

localhost:9050

```

You will find them under system > preferences > Network Proxy

Hope this helps.

---

### Post by tgomes95 on 2012-01-07
I have already done it. That's not the problem. = /

---

### Post by Dangertux on 2012-01-07
Okay well can you verify that Tor is actually running? 

Post output from the following

```

sudo ps aux | grep tor

``````

sudo netstat -anlp | grep :9050

```Thanks.

---

### Post by 0011235813 on 2012-01-07
I can't browse with tor. My DNS service isn't compatible with it :(On the plus sde, it does block a lot of known malware sites, and it actually seems to speed up my browsing. But some sites do require the use of a proxy sometimes, which is unfortunate.

---

