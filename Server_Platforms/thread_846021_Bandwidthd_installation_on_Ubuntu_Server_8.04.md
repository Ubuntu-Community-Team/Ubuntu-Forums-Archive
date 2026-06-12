---
title: "Bandwidthd installation on Ubuntu Server 8.04"
date: 2008-07-01
forum: Server Platforms
---

### Post by computermann24 on 2008-07-01
Heya, I'm just having a weee problem.

The thing is, It doesn't seem that I can get Bandwidthd working on my ubuntu server setup... I am wanting a solution where I can monitor the internet / network traffic running through the network;

My network config goes like this, my router / modem is connected to a Ethernet cable (duh) running downstairs, which is connected to a 5 port switch (goes off to server and wireless access point, as well as the xbox360 and my main PC) but also the router / modem is connected to a 5 port switch upstairs, which is connected to several devices.. Seeing the server is downstairs and is not directly hooked up to the internet (and can't be because the modem/router is in my flatmates room) I have a slight problem. (hopefully this sentence made sence, since it's quite late at night :))

Basically, seeing i'm in a flat situation, and or ADSL plan is "Pay $11.95NZL per 10gb + $42.95NZL for the base plan - Trusty New Zealand, Telecom hasn't unbundled the lines YET (anyone want to kill them for me?!)" I would like to know what flatmate is using on the internet, so I can charge them accordingly.. 

I thought Bandwidthd would work, but it seems that the package on Apt is not too good, causes errors, then you have the "Classic" situation with it not purging (aka, can't remove the package) even -f doesn't work... But after some fiddling I got it all removed - now it's time to compile from source, and I get the same common problem, it doesn't configure;

```
michaelmu@server:~/bandwith$ sudo ./configure
[sudo] password for michaelmu:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for bison... no
checking for byacc... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix...
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for /sw/lib... no
checking for /sw/include... no
checking for /usr/pkg/lib... no
checking for /usr/pkg/include... no
checking for connect in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for inet_aton in -lresolv... yes
checking for pow in -lm... yes
checking for libiconv_open in -liconv... no
checking for png_read_info in -lpng... no
configure: error: Bandwidthd requires but cannot libpng
michaelmu@server:~/bandwith$

```

I have compiled Libpng from source, with success - so have no real idea why it can't find it.

Can you recommend a solution for me? I thought of installing "IP Cop" on a old PC, but it's a pitty that I don't have a old PC..

I also had a WRT-54G back in the day, wish I kept it as it would have come in perfect right about.. now.

Thankyou :D

---

### Post by windependence on 2008-07-01
I would suggest one of these tools:

MRTG

 [http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)

CACTI

 [http://cacti.net/](http://cacti.net/)

Here are some articles of interest for you also:

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

[http://www.ubuntugeek.com/networkserver-statistics-graphing-using-cacti-in-ubuntu-server.html](http://www.ubuntugeek.com/networkserver-statistics-graphing-using-cacti-in-ubuntu-server.html)

My personal preference is MRTG

[http://www.debianhelp.co.uk/mrtg.htm](http://www.debianhelp.co.uk/mrtg.htm)

Hope this helps.

-Tim

---

### Post by mrtg.saitove.info on 2008-11-03
some really working examples you can view [Mrtg graphs]("http://mrtg.saitove.info/mrtg") and config files and examples here -> [MRTG config files and manuals]("http://mrtg.saitove.info/index.php")


if you have questions ... ask me :)

---

