---
title: "nftables in Trusty?"
date: 2014-02-20
forum: Ubuntu Development Version
---

### Post by The Cog on 2014-02-20
I read that kernel 3.13 incorporates nftables, the successor to iptables. I'm keen to try this out.
Trusty is now using the 3.13 kernel, but I can't find any sign of the nft or nftables userspace tools. Neither can I find any mention of whether or not nft will actually be included. 

Is anyone here in a position to actually state whether nftables user tools will be included in Trusty?

---

### Post by QDR06VV9 on 2014-02-20
Here is all I know for now>
```
[COLOR=#363636][FONT=Arial]"[/FONT][/COLOR][NFTables]("http://netfilter.org/projects/nftables/")[COLOR=#363636][FONT=Arial] is [/FONT][/COLOR][queued up for merging into the Linux 3.13 kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ5MDU")[COLOR=#363636][FONT=Arial]. NFTables is a four-year-old project by the creators of Netfilter to write a new packet filtering / firewall engine for the 
Linux kernel to deprecate iptables (though it now offers an iptables compatibility layer too). NFTables promises to be more powerful, simpler, reduce code complication, improve error reporting, and 
provide more efficient handling of packet filter rules. The code was merged into net-next for the Linux 3.13 kernel. Iptables will still be present until NFTables is finished, but it is possible to
 [/FONT][/COLOR][try it out now]("https://home.regit.org/netfilter-en/nftables-quick-howto/")[COLOR=#363636][FONT=Arial]. LWN also has a writeup on [/FONT][/COLOR][NFTables]("http://lwn.net/Articles/324989/")[COLOR=#363636][FONT=Arial]."[/FONT][/COLOR]
```

The try it now link is a how to.

---

### Post by The Cog on 2014-02-20
Thanks for the reference. 
By my understanding, the[COLOR="#aa0000"] try it out now[/COLOR] link is describing how to compile a custom kernel with nftables in it, which suggests that the normal 3.13 kernel will not support nftables after all. I'm guessing that the net-next branch for 3.13 will become default in 3.14?

---

### Post by QDR06VV9 on 2014-02-20
I was also reading the NTFTables
Found this quite funny
"[COLOR=#000000][FONT=Times New Roman]This could be a disruptive and expensive transition; the kernel development community will want to see some very good reasons for inflicting this pain on its users."[/FONT][/COLOR]

---

### Post by The Cog on 2014-02-20
Yes, but I got the impression that comment was made before the iptables compatibility tools were made. I gather that with teh compatibility tools, it will be possible to issue iptables commands and that nftables in the kernel will then do what is reqired (though I doubt you could mix and match iptables with nft commands).

---

### Post by QDR06VV9 on 2014-02-20
> **The Cog said:**
> Yes, but I got the impression that comment was made before the iptables compatibility tools were made.  
I should have clarified that> Just sometimes People have a Knee Jerk reaction!;) To Change.
But I Think I'm going to play with it tonite some, Looks Interesting.
Regards

---

### Post by Thiago Camargo on 2014-02-24
Hi!

I'm wondering about NFTables on Trusty too! Trusty already have NFTables modules compiled!
 
Take a look on what I'm trying to achieve:

Feature Request: add support for NFTables in Ubuntu 14.04:

[https://bugs.launchpad.net/ubuntu/+bug/1273337](https://bugs.launchpad.net/ubuntu/+bug/1273337)
[https://answers.launchpad.net/ubuntu/+question/242817](https://answers.launchpad.net/ubuntu/+question/242817)

But, as far as I know, no one is working on that for Trusty, maybe Debian guys are doing it?!


On Debian (I think):

[http://mentors.debian.net/package/nftables](http://mentors.debian.net/package/nftables)

[https://github.com/aborrero/pkg-nftables](https://github.com/aborrero/pkg-nftables) <- ???

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=736973](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=736973)


Anyway, if you want to play with it, I have a much easier NFTables install procedure, give it a shot!

--
Install Procedure, NFTables on Trusty:



1- Install Ubuntu Server 14.04 daily builds;


2- Prepare the env: "aptitude install build-essential git libgmp-dev libreadline-dev libmnl-dev libmnl0"


3- git clone git://git.netfilter.org/libnftnl


3.1 - cd libnftnl ; ./autogen.sh ; ./configure ; make ; make install ; ldconfig


4-


git clone git://git.netfilter.org/nftables
cd nftables
./autogen.sh
ac_cv_func_malloc_0_nonnull=yes ac_cv_func_realloc_0_nonnull=yes  ./configure
make
make install


5- nft -h




Well done!   :-P


Source: [https://home.regit.org/netfilter-en/nftables-quick-howto/](https://home.regit.org/netfilter-en/nftables-quick-howto/)
---

Cheers!
Thiago

---

### Post by Thiago Camargo on 2014-03-07
NFTables on PPA!

[https://launchpad.net/~xuzhen666/+archive/nftables](https://launchpad.net/~xuzhen666/+archive/nftables)

Cheers!
Thiago

---

