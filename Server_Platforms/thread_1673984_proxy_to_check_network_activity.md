---
title: "proxy to check network activity"
date: 2011-01-23
forum: Server Platforms
---

### Post by amsterdamharu on 2011-01-23
Hello and thank you for reading my post.

I would like Windows laptops to use a proxy to connect to the network so I can check network activity and see if any malware is trying to connect and where it is trying to connect to.

So on my Ubuntu desktop I would like to install something as simple as possible to be used as a proxy, I've seen squid but does that only handle http requests? Does that handle streaming requests and such as well? This so I can see the source of some media that's being played in flash or pps.tv

It only needs to forward requests and log it so I can see what the laptop is doing.

---

### Post by HereIam on 2011-01-23
Maybe, you can find a tool here: 
[http://www.linuxjournal.com/content/hacking-old-school](http://www.linuxjournal.com/content/hacking-old-school)

---

### Post by amsterdamharu on 2011-01-23
It looks like tpcdump is a good one to use for Linux and winpcap is good to use on Windows.
[http://www.winpcap.org/](http://www.winpcap.org/)

These are not proxy's but when run it dumps the activity of a network card so good for my purpose.

Thank you very much for your reply

---

### Post by amsterdamharu on 2011-01-24
I seem to have spoken too early, I can't make anything of the output of tcpdump.
There is just way too much output.

The first thing I wish to do is see what messages QQ messenger is sending to where, hoping to find something that has been changed since the pidgin plugin is not compatible with current qq service.
Tried squid but that doesn't show the messages sent just the requests made. 

tcpdump is giving me a lot of stuff but doesn't seem to be giving me the messages that are sent and received between the programs.

---

