---
title: "How to remain 'hidden' on a network"
date: 2010-10-26
forum: Security
---

### Post by Alexander D. Gray on 2010-10-26
Hello everyone,

I have a netbook with a copy of Kubuntu 10.04 installed, with full disk encryption as done with the alternative install CD.

I know about proxies and how they can allow you to remain anonymous when you're accessing the Internet, but what I'm curious about is how to remain anonymous/hidden when accessing a particular network.

For example, say I go to a local cafe and access their wireless network, how could I make it so that no other computer on that network (ie, others in the cafe) can see my computer on the network? If it isn't possible to completely remove one's footprint, what are some ways to make it as small as possible?

I've searched around google and these forums but I haven't found anything, perhaps because I'm not searching for the correct stuff. Unfortunately I'm not entirely sure where to start, as I'm not entirely sure what options are available to make this happen.

Could someone please provide me with some general advice, or perhaps a website or other resource that would help me out in learning how to do this?

Thank you.

---

### Post by CharlesA on 2010-10-26
They'll be able to see yer hostname, but if you are on a public network, it's usually a good idea to tunnel your traffic, so no one is able to sniff it and grab stuff like passwords and usernames.

---

### Post by anomie on 2010-10-26
[QUOTE=Alexander D. Gray]... say I go to a local cafe and access their wireless network, how could I make it so that no other computer on that network (ie, others in the cafe) can see my computer on the network? If it isn't possible to completely remove one's footprint, what are some ways to make it as small as possible?[/QUOTE]

I'm not an 802.11 expert, but I find it very unlikely that you're going to be able to hide your interface's layer 2 traffic (as that would logically interfere with normal communication). 

Two simple things for substantially mitigating risks: 
[list=1]
[*] Do not have any tcp/udp services listening for external connections. 
[*] Only communicate over trusted (i.e. pay attention to those cert warnings), encrypted channels. 
[/list]

As alluded to in the previous post, if you're sending anything clear text (including email, file transfers, web form submissions, etc.) you can assume that it will be intercepted and read.

---

### Post by Chayak on 2010-10-27
It depends a lot on who you're trying to hide it from.

A simple proxy, noscript, and disabling cookies will keep websites from tracking you.  A VPN tunnel will protect your traffic over wifi to keep people from sniffing your traffic.

If you're trying to hide your activities from ISPs... VPN

If you're trying to hide from law enforcement... ask elsewhere

---

### Post by karthick87 on 2010-10-27
> **Chayak said:**
> It depends a lot on who you're trying to hide it from.

A simple proxy, noscript, and disabling cookies will keep websites from tracking you.  A VPN tunnel will protect your traffic over wifi to keep people from sniffing your traffic.

If you're trying to hide your activities from ISPs... VPN

If you're trying to hide from law enforcement... ask elsewhere


Interesting :)

---

### Post by uRock on 2010-10-27
> **Alexander D. Gray said:**
> Hello everyone,

I have a netbook with a copy of Kubuntu 10.04 installed, with full disk encryption as done with the alternative install CD.

I know about proxies and how they can allow you to remain anonymous when you're accessing the Internet, but what I'm curious about is how to remain anonymous/hidden when accessing a particular network.

For example, say I go to a local cafe and access their wireless network, how could I make it so that no other computer on that network (ie, others in the cafe) can see my computer on the network? If it isn't possible to completely remove one's footprint, what are some ways to make it as small as possible?

I've searched around google and these forums but I haven't found anything, perhaps because I'm not searching for the correct stuff. Unfortunately I'm not entirely sure where to start, as I'm not entirely sure what options are available to make this happen.

Could someone please provide me with some general advice, or perhaps a website or other resource that would help me out in learning how to do this?

Thank you.
When you have GUFW enabled to deny all incoming, then nobody should be able to see your PC. If you are on a network that doesn't use WPA, then it is possible for someone to intercept the wireless packets.

---

### Post by karthick87 on 2010-10-27
I have allowed the incoming port 21 alone for my ftp server..So am i secure..?

```
karthick@Ubuntu-desktop:~/Desktop$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
21                         ALLOW       Anywhere
```

---

### Post by uRock on 2010-10-27
> **getyourkarthick said:**
> I have allowed the incoming port 21 alone for my frp server..So am i secure..?

```
karthick@Ubuntu-desktop:~/Desktop$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
21                         ALLOW       Anywhere
```
Maybe this link will be helpful. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by emarkay on 2010-10-27
If you have one of those wire thingies connected to your PC, and it goes to one of those telephone jack type things, or even worse, you just pick yer signal from the Ether, then there is a chance, not slim to none, but a real chance that someone can monitor that data.

That is a fact.  

It depends on who wants to do so and how much time, money or water they want to spend to get to that data, and then, again, to transcribe it.  Remember, it doesn't have to be read  in "real time" to offer one the unfortunate option of "real time"...

---

### Post by Alexander D. Gray on 2010-12-22
Hello everyone,

Sorry for the delay in my response. School kept me really busy so I wasn't able to work on this side project very much.

To Emarkay - your comment is a truism of the internet and I'm well aware that being a complete ghost is essentially impossible. I was once told that there's three things  to pay attention to with computer security: time, price, and complexity. Typically you pick two to focus on because all three simply isn't feasible. What I was mostly curious about is some beyond basic methods to avoid being an easy target on a public network.

To uRock - forgive me for being naive, but if you are denying all incoming data, wouldn't that significantly limit what you're able to do online? Say, if you're sending an email, wouldn't that require some level of incoming data to be permitted? I'll need to read more into this certainly, but I am familiar with the WPA standard and how it trumps something like WEP.

To Chayak - Thanks for the pointers, I had started to think the VPN was the way to go. You can rest assured that I am not attempting to hide from law enforcement. My intent is to avoid the bad guys, not to be one. As an aside, why would someone use public internet while committing some sort of crime? Wouldn't it be 'safer' to use a private network, or perhaps hijack onto someone else's private network, rather than use a public medium like a cafe's connection?

And finally, to CharlesA - When you say they'll be able to see my hostname, that's the reference name for my computer correct? Is that inevitable? 

As an example, think of a home network with 3 computers. When you're on any one computer you can 'see' the others on the network, access certain files, etc. I'm curious as to whether or not it's possible to access said network and not show up so easily to these other computers. It sounds like once you're online something like a VPN is an effective way to conceal your traffic, but what about your basic presence on the network?

As a related example, I have a buddy who lives in residence at his university. Going over to his dorm room I can access the university's network. Looking at the network settings I can 'see' the computers of a whole bunch of people in the dorm. Some of them seem to have everything open such that I can see their shared docs, music, movies, what have you. That's the kind of thing I'm looking to avoid. Being so open just doesn't seem like a great idea on a public network.

Thanks for all your help so far!

Cheers.

---

### Post by uRock on 2010-12-22
> **Alexander D. Gray said:**
> To uRock - forgive me for being naive, but if you are denying all incoming data, wouldn't that significantly limit what you're able to do online? Say, if you're sending an email, wouldn't that require some level of incoming data to be permitted? I'll need to read more into this certainly, but I am familiar with the WPA standard and how it trumps something like WEP.
Blocking incoming does not block incoming packets from connections you have made, such as your email client. In other words, your applications will not be effected by blocking incoming connections.

---

### Post by CharlesA on 2010-12-22
> **Alexander D. Gray said:**
> 
To uRock - forgive me for being naive, but if you are denying all incoming data, wouldn't that significantly limit what you're able to do online? Say, if you're sending an email, wouldn't that require some level of incoming data to be permitted? I'll need to read more into this certainly, but I am familiar with the WPA standard and how it trumps something like WEP.

The way uRock has it set up, is that new incomming connections are blocked, but connections are are already established and related to existing connections are allowed. That means no one can connect to your machine from the outside, but you are still able to do stuff like browse the internet and whatnot.

> To Chayak - Thanks for the pointers, I had started to think the VPN was the way to go. You can rest assured that I am not attempting to hide from law enforcement. My intent is to avoid the bad guys, not to be one. As an aside, why would someone use public internet while committing some sort of crime? Wouldn't it be 'safer' to use a private network, or perhaps hijack onto someone else's private network, rather than use a public medium like a cafe's connection?

Well I guess they use public connections, since any activity they do will be logged there and it's not "their network" so they don't get in trouble.

> And finally, to CharlesA - When you say they'll be able to see my hostname, that's the reference name for my computer correct? Is that inevitable? 

As far as I know you cannot hide your hostname.

> As a related example, I have a buddy who lives in residence at his university. Going over to his dorm room I can access the university's network. Looking at the network settings I can 'see' the computers of a whole bunch of people in the dorm. Some of them seem to have everything open such that I can see their shared docs, music, movies, what have you. That's the kind of thing I'm looking to avoid. Being so open just doesn't seem like a great idea on a public network.

That's why you configure your firewall to block all incoming connections if you are on a public network. :)

---

### Post by bodhi.zazen on 2010-12-22
When I log onto a public wireless (WAP) I personally:

1. Activate the firewall

```
sudo ufw enable
```

Does not add much, but I feel better =)

2. Use encryption for all sensitive traffic, with web browsing this means https or tunnel over ssh.

3. If truly paranoid VPN.

4. Disable [Avahi](http://avahi.org/) and CUPS (no, I almost never print on such networks). 

5. I think the confusion comes from the working of your request:

> How to remain 'hidden' on a network

There is no such thing as being invisible or hidden if you are connected to the network.

---

