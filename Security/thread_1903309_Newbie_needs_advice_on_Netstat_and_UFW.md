---
title: "Newbie needs advice on Netstat and UFW"
date: 2012-01-02
forum: Security
---

### Post by Mr Mercury on 2012-01-02
Hi Everybody
I would like to introduce myself as it is my first post on this forum and i am new to linux. I have installed Ubuntu 11.10 which i quite like, however......i would like to ask some questions about Netstat and UFW. 
First of all i have set up UFW as recommended by links from this forum i.e. incoming deny and strict out going policies. After using grc.com Shields Up it would respond to a ping.....how do i permanently solve the ping issue? Also If i run Netstat there seems to be an awful lot of listening and connected sockets.....is this ok?. Is it possible for updates to change UFW settings without my knowledge?

Many Thanks:p

---

### Post by Dangertux on 2012-01-02
> **Mr Mercury said:**
> Hi Everybody
I would like to introduce myself as it is my first post on this forum and i am new to linux. I have installed Ubuntu 11.10 which i quite like, however......i would like to ask some questions about Netstat and UFW. 
First of all i have set up UFW as recommended by links from this forum i.e. incoming deny and strict out going policies. After using grc.com Shields Up it would respond to a ping.....how do i permanently solve the ping issue? Also If i run Netstat there seems to be an awful lot of listening and connected sockets.....is this ok?. Is it possible for updates to change UFW settings without my knowledge?

Many Thanks:p

Yes it is possible for updates to change UFW settings, however if you're updating only from Ubuntu repositories they shouldn't. On that same coin though, you should always be reading change notes and not just blindly updating.

As far as disabling ICMP echo responses with UFW here is how you do it, as far as I know you need to edit your rules manually, I could be wrong but this is the most straightforward way I know to do it.

You need to edit /etc/ufw/before.rules so you would.

```

gksudo gedit /etc/ufw/before.rules

```

OR 

```

sudo nano /etc/ufw/before.rules

```

Then you need to change the following line

```

-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

to 

```

-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

```

Afterwards save the file and restart ufw

```

sudo ufw disable && sudo ufw enable

```

Hope this helps.

---

### Post by Jive Turkey on 2012-01-02
It might interest you to know that dropping ICMP doesn't really make you significantly safer than allowing it.  Also if your computer is behind a router it is likely your router that is acknowledging the ping packets.  It might make more sense to rate limit the ping requests.

---

### Post by Mr Mercury on 2012-01-03
Originally i tried ubuntu (hard wired to modem) with 'firestarter' only to find that it didnt work on shields up(poor results, although i do have access to a router,it was not connected at the time)....i immediately enabled UFW and all the ports became stealth except for ICMP ping. Shields up actually says that ICMP ping is one of the oldest forms of exploit...or words to that affect.....or have things moved on in modern times? I just dont feel that i know enough about IP tables or Netstat to feel confident with security. Can someone point me in the right direction and explain the ICMP ping thing.

Thanks

---

### Post by Soul-Sing on 2012-01-04
please take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1574981&highlight=disable+icmp+ping](http://ubuntuforums.org/showthread.php?t=1574981&highlight=disable+icmp+ping)

---

