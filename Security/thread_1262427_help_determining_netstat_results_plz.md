---
title: "help determining netstat results plz"
date: 2009-09-09
forum: Security
---

### Post by cLos420 on 2009-09-09
hey,

anyone know anything about this netstat result i got?

active internet connections (w/o servers)
proto recv-0 send-0 local address foreign address state
tcp            0        0 :40456           yx-in-fl00.google.c:www established
does :www mean its port 80? if so, my best guess is that its an ad

i did a search online for yx-in-fl00.google.c but no dice

i had pigdin(aim, hotmail)  and ff (pandora and gnome-look.org)
no screenlets that access the internet (radio, rss, etc)

i appreciate the feedback 
- peace

---

### Post by phillw on 2009-09-10
I *think* it is the little google search bar.

Phill.

---

### Post by cdenley on 2009-09-10
It could very well be the google search bar in firefox. Those auto-complete suggestions must come from somewhere. It appears the resolved domain was cut off in the output you posted. Also, yes, netstat display "www" for the port instead of "80" by default. This is why I always use the "n" switch when using netstat. It shows IP's instead of domains, and port numbers instead of associated services.
```

netstat -tn
man netstat

```

---

### Post by cLos420 on 2009-09-10
That makes a lot of sense, you guys rock!
Phil, I think you'll find this link amusing. (I clicked on the link to your signature) 
[http://www.reuters.com/article/newsOne/idUSTRE5885PM20090909](http://www.reuters.com/article/newsOne/idUSTRE5885PM20090909)

cdenley, thanks for the tip!

Thanks guys. 

-cLos

---

### Post by grotesk on 2009-09-13
In addition to cdenley's suggestion of turning off name resolution (-n), the most surefire way to determine what a connection is is often to use tcpdump (or Wireshark if you prefer a GUI) to dump the raw packets to your screen and have a look at what's going on.

Let's say you run

```
# netstat -tnl
```

And see something like

```
tcp  0  0  <YOUR LOCAL IP>.62964    74.125.53.100.80        ESTABLISHED
```

You know that the remote host is some webserver, and if you DNS reverse resolve it is obviously Google's:

```
$ host 74.125.53.100
100.53.125.74.in-addr.arpa domain name pointer pw-in-f100.google.com.

```

Easy enough. But what's going on? You can use tcpdump to find out:

```

$ sudo tcpdump -Atnnni eth0 -s0 host 74.125.53.100 and port 80
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
IP <IP SCRUBBED>.63032 > 74.125.53.100.80: Flags [S], seq ***, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val *** ecr 0,sackOK,eol], length 0
E..@.r@.@.>3....J}5d.8.PN..........................
............
IP 74.125.53.100.80 > <IP SCRUBBED>.63032: Flags [S.], seq ***, ack ***, win 5672, options [mss 1430,sackOK,TS val 3782176849 ecr ***,nop,wscale 6], length 0
E..<....1.."J}5d.....P.8..#.N......(.K.........
.opQ........
IP <IP SCRUBBED>.63032 > 74.125.53.100.80: Flags [.], ack 1, win 65535, options [nop,nop,TS val *** ecr ***], length 0
E..4u4@.@..}....J}5d.8.PN.....#............
... .opQ
IP <IP SCRUBBED>.63032 > 74.125.53.100.80: Flags [P.], seq 1:966, ack 1, win 65535, options [nop,nop,TS val *** ecr ***], length 965
E...e!@.@.......J}5d.8.PN.....#............
... .opQGET /complete/search?output=firefox&client=firefox&hl=en-US&q=t HTTP/1.1
Host: suggestqueries.google.com
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.6; en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive

```

(I've scrubbed a bit of IP information out here but it's not relevant)

There's a fair amount of cruft here, for our purposes, but there's something key to note. Namely, the Host value in that HTTP GET request:

Host: suggestqueries.google.com

And the query itself, which is right at the end of the URL in the GET string:

GET /complete/search?output=firefox&client=firefox&hl=en-US&q=test HTTP/1.1

So it's the Firefox search bar, helpfully asking Google for search suggestions as I type in my query.

For more information I highly recommend the man pages for tcpdump and netstat, as they are both extremely useful. You may also want to investigate the -p flag to netstat which tells you which process on your system owns that TCP connection.

Good luck!

---

### Post by cLos420 on 2009-09-15
Thanks grotesk

How do I marked this as solved?

---

