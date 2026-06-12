---
title: "packet priority"
date: 2006-04-20
forum: Server Platforms
---

### Post by dixon on 2006-04-20
Hi, I've just installed ipp2p, so I can mark the p2p packets. 
Now I need to do something like packet priority chart.
for example:
1. http
2. ftp
3. ports for counter strike
.....
last position. p2p :)

How can I do that? :) I've heard something about HTB, but I can't find any HOWTO anywhere(for packet priorization). ](*,) 

thx for help :wink:

---

### Post by nagilum on 2006-04-20
What you need can be done with the iproute2 utility, look for some advanced routing howtos, like [this one](http://www.lartc.org/howto).

---

### Post by dixon on 2006-07-16
OK - so I've read "a bit" about HTB and I have few questions :)

I've got Ubuntu server with 2 interfaces - eth0(internet), br0(LAN). My connection to the internet is DSL 1536 / 256 kbits. I share this connection with 10 people.

When I want to shape download and also upload - How can it be done? Can it be done by tc class add dev **eth0** - makes cell for **download** and tc class add dev **br0** for **upload**?

What about input for HTB - I've read, that I should give smaller input than my connection really is for HTB, but what is smaller? Can it be 1230 / 230 (That's 80%)? 
What happends to the bandwith, which is not given as input for HTB(1536 - 1230 = 306kbit).
What happends if HTB didn't get amount of bandwith as It's expected?

What's the meaning for setting up burst? I've read that it's only  offset from rate... What's the default value?

How can I mark normal HTTP traffic and HTTP downloading?

I want to mark packets through iptables ... --set-mark, but I'm also using ipac-ng and I think it's based on iptables marknig. Do you know about some replacement for ipac-ng?

I'm going to "design" the cells like this
VoIp prio 0
Games prio 0
SSH prio 1
HTTP browsing + DNS prio 2
other traffic prio 3
p2p prio 4

If you have any suggestions about "design", please write :)

What rate(up/down) would you give to the cells?
VoIp - using average 1 person and max 3
     - traffic = 10kBs/10kBs
Games - using average 2 persons and max 4
      - traffic for CS = 4kBs/4kBs
      - Call of Duty 2 is played very often on our network - if you now the traffic of this game - please let me know ;)
SSH - using max 1 person
    - traffic = 2kBs/2kBs

THX for the help and patience :-k

---

### Post by dafyre on 2007-06-06
Hey Dixon:

Have you got a How To that you went through to get it installed?  I've been unsuccessful at getting ipp2p installed with Kernel 2.6.21.3...  What kernel version are you using?

I have some TC examples for you ...  At first, the script will seem quite lengthy, but once you read through it a few times, I think you could understand it... 

If you don't, ask me, and I'll answer your questions if I can....  Otherwise, check out [http://www.lartc.org](http://www.lartc.org) -- they have some awesome docs on how to do the traffic filtering...  Check out Chapter 9 and read it closely...  

You'll notice that my scripts use the HTB and SFQ for a lot of stuff and filters for the rest... 

Like I said, if you have any questions after reading the script & LARTC, let me know.

See Ya!
~Brant

---

### Post by Flotter on 2007-11-19
> **dafyre said:**
> Hey Dixon:

Have you got a How To that you went through to get it installed?  I've been unsuccessful at getting ipp2p installed with Kernel 2.6.21.3...  What kernel version are you using?

I have some TC examples for you ...  At first, the script will seem quite lengthy, but once you read through it a few times, I think you could understand it... 

If you don't, ask me, and I'll answer your questions if I can....  Otherwise, check out [http://www.lartc.org](http://www.lartc.org) -- they have some awesome docs on how to do the traffic filtering...  Check out Chapter 9 and read it closely...  

You'll notice that my scripts use the HTB and SFQ for a lot of stuff and filters for the rest... 

Like I said, if you have any questions after reading the script & LARTC, let me know.

See Ya!
~Brant

I'd love to know the secret of installing ipp2p as well.  I've tried for about a week to install it with the 2.6.22-server kernel & iptables 1.3.6.  **ANYBODY** make this thing work yet????????????

---

### Post by dixon on 2007-12-04
Did you follow the instructions in README file? I didn't have any problems, but that was a year ago. Next week I should be installing new server, so I'll try the ipp2p and let you know...

---

