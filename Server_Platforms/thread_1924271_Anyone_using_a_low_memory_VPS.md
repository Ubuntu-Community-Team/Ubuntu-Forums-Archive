---
title: "Anyone using a low memory VPS?"
date: 2012-02-12
forum: Server Platforms
---

### Post by d4m1r on 2012-02-12
Hey guys, I just purchased a linux VPS to play around with and it has 250mb ram. Anyway, although CentOS seems to be a more popular option, I went with Ubuntu 11.04. Obviously it does not have enough memory to run a UI so I just access the root user over SSH.

Yesterday I tried setting up LAMP (Apache, PHP, and mysql) and I managed to get them all running but 256mb is just not enough, even when I turned all their settings down...Apache and PHP don't use a lot of resources but mysql was using 130mb while idle....

Does anyone have any recommendations? Is anyone else running stuff off a 256mb VPS?

---

### Post by 2F4U on 2012-02-12
Since you don't seem to be needing a GUI, why not try the Ubuntu Server Edition. It comes without a GUI by default and installs just what is necessary to run a server.

---

### Post by d4m1r on 2012-02-12
> **2F4U said:**
> Since you don't seem to be needing a GUI, why not try the Ubuntu Server Edition. It comes without a GUI by default and installs just what is necessary to run a server.

That's what the server is already running, 11.04 Server (no UI by default).

---

### Post by SeijiSensei on 2012-02-12
Can you upgrade to 512M?  While I've run versions of Linux in as little as 64M, I'd consider 256M a bit tight by modern standards.

Do you have a swap area or swap file?  Run "top" and see how much swap there is.  It should be at least another 256M, and you might consider allocating 512M to swap as well.  You can add swap yourself independent of the VM provider by create a swap file in the local filesystem.  See [this howto](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/) for details.

---

### Post by d4m1r on 2012-02-12
Thought I would update this. After 3 OS reinstalls I finally have it  setup the way I like it....Apache, PHP, and a FTP server are using  20-25mbs when I am not logged into the server which is crazy low I think  [IMG]http://www.webhostingtalk.com/images/smilies/biggrin.gif[/IMG] I know ngix or lightppd would have been better as Apache isn't very efficient but its what I am used to...

It **is** possible to run several services off a 128mb linux VPS,  some semi-popular websites like 96mb.com and lowendbox.com run off  similar VPS's...

Anyway, I did give up on Mysql however....No matter how I configured it, it would still take 100-150mb of ram even when idle [IMG]http://www.webhostingtalk.com/images/smilies/wallbash.gif[/IMG] I realized I don't have any plans to run any DB's off this box anyway so I don't need it.

Help me stress-test my new VPS by visiting my site @ [**www.d4m1r.tk**]("http://www.d4m1r.tk/")

---

### Post by robgr85 on 2012-02-13
For static files/pages it should work fine - you can disable most of apache modules to decrease apache resources usage. 

But such a low amounts of RAM sounds extreme for any dynamic websites and traffic a above few users at a time. Apache will probably eat most of Your free memory fast when running dynamic pages under decent load.

---

### Post by d4m1r on 2012-02-13
Actually, it seems like some semi-popular websites run off of similar spec VPS' if not lower spec (96mb ram). Namely 96mb.com and lowendbox.com

Some run apache set to use very low resources and many modules disabled (that I would have disabled anyway) while others use ngix or lighttp, but it is possible :)

---

### Post by Cookieh on 2012-02-13
My friend had the same problem, but then he decided to run it at 512 mb and later went back to 256 mb as he just fiddled about with Ubuntu Server Edition. Suggest you to try it out and play around with it..

---

### Post by d4m1r on 2012-02-28
[SIZE=2][COLOR=Red]UPDATE:[/COLOR][/SIZE] I bought a higher end  package so I no longer need my 128MB system. The account still has 11  months paid for so PM me if you want it.

---

