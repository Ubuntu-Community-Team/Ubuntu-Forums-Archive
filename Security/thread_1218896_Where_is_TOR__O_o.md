---
title: "Where is TOR ? O_o"
date: 2009-07-21
forum: Security
---

### Post by asbesto on 2009-07-21
> root@gemini:~# apt-get install tor privoxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate
root@gemini:~# 


Am I missing something? :confused:

Where is the tor package?

---

### Post by kerry_s on 2009-07-21
[http://www.torproject.org/](http://www.torproject.org/)

a lot of sites, will ban tor users, so make sure you really want to use it.

---

### Post by bodhi.zazen on 2009-07-21
> **kerry_s said:**
> [http://www.torproject.org/](http://www.torproject.org/)

a lot of sites, will ban tor users, so make sure you really want to use it.

I wonder why :twisted:

---

### Post by kerry_s on 2009-07-21
> **bodhi.zazen said:**
> I wonder why :twisted:

:lolflag:
does the forum ban tor to or is it just the rss?

---

### Post by NoctisCaelum on 2009-07-23
I was wondering something.. first of all, TOR hides only inside the browser, or even our connections when we're connected to some server.. like some gameserver or something like that, can't they really see our ip ? I'm afraid that the answer will be no, so, how could I possibly hide my ip from every server that I connect ? I want my privacy at max. Sorry if i'm asking it in the wrong side.

---

### Post by doas777 on 2009-07-23
since no one felt like answering the question, you have to install another repo for tor:
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by doas777 on 2009-07-23
> **NoctisCaelum said:**
> I was wondering something.. first of all, TOR hides only inside the browser, or even our connections when we're connected to some server.. like some gameserver or something like that, can't they really see our ip ? I'm afraid that the answer will be no, so, how could I possibly hide my ip from every server that I connect ? I want my privacy at max. Sorry if i'm asking it in the wrong side.


um, thats what privoxy is for. and no, tor is a network level proxy, not application level. you have to configure your other apps to use it, but it is not tied to your browser. some apps will leak DNS queries whether you like it or not, but you can usually do somthing about it.

---

### Post by bodhi.zazen on 2009-07-23
I think it is a fallacy to think you are anonymous on the internet. If you were truly anonymous how could traffic find it's way from the server back to your client ? 

As a client, you can not hide from the server. You can encrypt the traffic (https) and you can make it difficult for a packet sniffer, but you can not hide from those who would find you.

If it makes you feel better, I have no problem with that, but don't go that extra step and fool yourself that you are anonymous.

---

### Post by 2e0spf on 2009-07-23
> **bodhi.zazen said:**
> 
As a client, you can not hide from the server. You can encrypt the traffic (https) and you can make it difficult for a packet sniffer, but you can not hide from those who would find you.


I would check your facts before you make yourself look stupid.

---

### Post by doas777 on 2009-07-23
> **2e0spf said:**
> I would check your facts before you make yourself look stupid.

meddle not in the affairs of dragons, for you are crunchy and taste great with ketchup.

---

### Post by bodhi.zazen on 2009-07-23
[http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)

---

### Post by 2e0spf on 2009-07-23
> **bodhi.zazen said:**
> [http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)
Hmm i should probably check that a poster isnt the admin of the forum before i start challenging them... now who feels stupid...

Anyway, i still disagree with your post as you stated that as a client you cannot hide yourself from the server. The tor network will only reveal to the server the exit point ip from the tor network, and each server in the network your traffic has hopped through only knows the previous hop and the next hop. the only server which knows your ip is the entry server.

Please please tell me if ive got it wrong, but if i havnt then doesnt that prove your statement false?

Steve

---

### Post by bodhi.zazen on 2009-07-23
> **2e0spf said:**
> Hmm i should probably check that a poster isnt the admin of the forum before i start challenging them... now who feels stupid...

Anyway, i still disagree with your post as you stated that as a client you cannot hide yourself from the server. The tor network will only reveal to the server the exit point ip from the tor network, and each server in the network your traffic has hopped through only knows the previous hop and the next hop. the only server which knows your ip is the entry server.

Please please tell me if ive got it wrong, but if i havnt then doesnt that prove your statement false?

Steve

If you say so :)

You are welcome to your opinion and I wish you luck with that.

Please treat **all** members of the community with respect. Keep in mind your message is less effective when you use an antagonistic or confrontational tone. Even if you are correct, I think you will find evoking a negative emotional response in people does very little to win them over to your point of view.

I do not think (although I am not sure) doas777 was referring to "challenging an admin" in the cautionary post.

---

### Post by NoctisCaelum on 2009-07-23
thanks for the answers to both of you, but now I want to make another question, how I can encrypt my connection, to a point that no one could find where I entered, it is possible ? if it is... even the ISP could not pick the places where I have been ? (like using some kind of 'tunneled' conecction, like VNC protocol)

---

### Post by doas777 on 2009-07-23
you could look into vpn'ing into a leased server somewhere else in the world, but performance would be poor. you will have to be very careful with your privoxy configuration though, and probably block all outbound traffic, except that which passes through the tunnel.

to be honest, there is no good legal way to completely obscure your origins, unless protocols like I2P take off. try to support privacy conscious protocols when possible, and study networking if you have the interest. Privacy and paranoia were actually some of my first impetus' to start seriusly studing computing. after a while, i realized that it was easiest and most effective to hide in the crowd, rather than skulk in the shadows behind it.

seriously, beware the darkside. when you peel back the shiny veneer of the internet, thar really be dragons thar, and when they bite you, you feel the pinch in the real world.     

best regards,
franklin

---

### Post by AndyCinDallas on 2009-07-26
> **doas777 said:**
> since no one felt like answering the question, you have to install another repo for tor:
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)
That worked like a charm - thank you, doas, I have been battling with Tor for weeks now :D

---

