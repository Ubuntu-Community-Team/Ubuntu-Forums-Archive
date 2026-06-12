---
title: "Externally accessible proxy server"
date: 2010-08-31
forum: Server Platforms
---

### Post by mpgarate on 2010-08-31
I am trying to make a proxy server that is accessible externally. (Not on my home network) I would like to be able to browse the web as my home ip address from a machine at Starbucks, for example. Can this be accomplished with Squid? I managed to set up a home proxy server which worked internally. (1 local machine using the ip address of the other)

Can anyone point me in the right direction?

thanks,
m

---

### Post by oomar on 2010-08-31
I don't know how well squid works.

The most effective and secure (and fairly easy) way to do this is to set up SSH and use a tunnel to tunnel your traffic home.

1. Set up SSH (public-key authentication is nice... :) you can use putty on windows, and even use putty-gen for the key. )
2. set up firewall and router for port forwarding
3. double check SSH settings (wouldn't want to let some script kiddie hack the pentagon from your computer would you?)
4. run "ssh -D 9999 serveraddress" (use 9999. you can use any port you want but if its below a certain value (i dont remember which port) you require root. 9999 works fine for your purposes)
5. go to your internet browser settings and configure it to use a SOCKS host (v2) at 127.0.0.1 on port 9999.

ummm i didn't forget anything, did I?

---

### Post by BkkBonanza on 2010-08-31
oomar has it right - that's the easiest way since on Ubuntu **ssh** is installed already.

only a few notes to add,

If you start ssh with the -D option then you must keep that terminal open to keep ssh running. Another way is to use -fND options which starts it as a background process. But then you'll want to kill it after.

It's "SOCKS5" you want in browser settings. You can use this method with any program that supports SOCKS5 proxy including email, torrents, skype etc. 

You only need to config port forwarding on your router if you intend to access into your home network from outside. For browsing out from your home/router it's not needed.

This method is ideal for when wanting security at cafes or any place you don't trust that eavesdropping may occur, such as apartment and school networks.

You need to have access to SOME server running sshd to do this. Often people will setup their home for this but that can be slow as well. If you have a web server somewhere that is ideal. There are shell accounts out there for free/almost free but it's always questionable how safe they are. 

Another method I've setup and used that is cheap (but not free) is to sign up for an Amazon EC2 account. With just a few commands you can use this to start an on-demand server when you need and only pay for hours used (about 3 cents/hr). If anyone wants to know how to do that just ask and I'll write up a brief how-to. There are some tutorials out there but they are roundabout and cumbersome. It's pretty easy from Ubuntu.

When using Firefox and Thunderbird be sure to set the about:config options to use remote DNS otherwise DNS lookups are local and hence, leak out. This isn't so much a security threat as privacy when you don't want local ISP or govt listeners recording sites you visit.

Finally, there is a gSTM package in the repos that allows GUI desktop management of ssh tunnels and with that you don't even need to open a terminal. It makes this even easier.

---

### Post by bodhi.zazen on 2010-08-31
> **BkkBonaza said:**
> oomar has it right - that's the easiest way since on Ubuntu **ssh** is installed already.

Just to clarify, the ssh client is installed, but not the server.

---

### Post by DiagonalArg on 2011-01-19
> **BkkBonanza said:**
>  [...]
Another method I've setup and used that is cheap (but not free) is to sign up for an Amazon EC2 account. With just a few commands you can use this to start an on-demand server when you need and only pay for hours used (about 3 cents/hr). If anyone wants to know how to do that just ask and I'll write up a brief how-to. There are some tutorials out there but they are roundabout and cumbersome. It's pretty easy from Ubuntu.


BkkBonanza.  I'd like to take you up on your offer.  If you want to write up a short how-to, I would be much appreciative!  Thanks for the offer (and thanks in advance).

DR

---

### Post by BkkBonanza on 2011-01-20
I sort of already wrote this out. Not exactly though. I wrote up a tutorial on using EC2 as a intermediate tunnel. The same info applies except a proxy is easier since you don't need to bother with starting a tunnel. Once the EC2 instance is running you can just use ssh to proxy through it.

I'd suggest reading my other tutorial, but skip over any details about the tunnel. Getting an EC2 account and setting up an instance is pretty easy and without the tunnel you don't even need to customize it. It's been a while and I didn't go re-read my previous posts but I think a lot of it was about customizing the instance to run a specific tunnel on startup.

[http://ubuntuforums.org/showthread.php?t=1576257](http://ubuntuforums.org/showthread.php?t=1576257)

In that thread the original question is different but further down [noparse](post #8)[/noparse] I have several tutorial posts that lay out the EC2 details and more.

Edit - just checked the thread and the two tutorial posts are #12 (about setting up account) and #22 (about using cmd line tools).

---

