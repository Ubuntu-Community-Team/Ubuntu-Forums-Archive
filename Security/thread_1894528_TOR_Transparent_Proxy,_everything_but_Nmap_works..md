---
title: "TOR Transparent Proxy, everything but Nmap works."
date: 2011-12-12
forum: Security
---

### Post by RyanRahl on 2011-12-12
So, I am fiddling with TOR as a transparent proxy because it is my wish to redirect ALL traffic through tor on the local interface. I have been successful for the most part until I use Nmap, at which point my real IP address is revealed to the remote host instead of a TOR exit point. All software from the CLI like NetCat, Nikto, SSH and Lynx work but Nmap does not. I followed the instructions on this page to get it going:

[https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy)

Here are some sample input/outputs to show what I am talking about

My local address will be 209.189.*.*
My remote address is 74.94.*.*
Un-sanitized IPs are obviously TOR exit devices

Local Mahine NetCat to port 9000 on remote host:
```
root@localhost:/#nc -vv 74.94.*.* 9000
Connection to 74.94.*.* 9000 port [tcp/*] succeeded!
```

Remote machine syslog from NetCat port 9000:
```
Dec 12 16:09:19 hero kernel: [2513112.171118] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=77.247.181.162 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=49 ID=45922 DF PROTO=TCP SPT=31608 DPT=9000 WINDOW=5840 RES=0x00 SYN URGP=0 
Dec 12 16:09:22 hero kernel: [2513115.173868] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=77.247.181.162 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=49 ID=45923 DF PROTO=TCP SPT=31608 DPT=9000 WINDOW=5840 RES=0x00 SYN URGP=0 
```

SSH attempt on standard port (my listening SSH port is non-standard)
```
root@localhost:/#ssh ryan@74.94.*.*
```

Remote syslog from SSH attempt:
```
Dec 12 16:12:10 hero kernel: [2513283.096891] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=80.237.226.74 DST=74.94.*.* LEN=60 TOS=0x00 PREC=0x20 TTL=49 ID=62361 DF PROTO=TCP SPT=60777 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 
Dec 12 16:12:11 hero kernel: [2513283.833134] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=199.48.147.38 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=55 ID=42759 DF PROTO=TCP SPT=35096 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 
Dec 12 16:12:14 hero kernel: [2513286.838401] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=199.48.147.38 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=55 ID=42760 DF PROTO=TCP SPT=35096 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 

```

Nikto Scan from localhost:
```
root@localhost:/#nikto -host 74.94.*.*
```
Access Log of remote host Nikto scan:
```
80.237.226.74 - - [12/Dec/2011:16:03:35 -0800] "GET / HTTP/1.1" 301 645 "-" "Mozilla/4.75 (Nikto/2.1.1) (Evasions:None) (Test:headers: base)"
80.237.226.74 - - [12/Dec/2011:16:03:37 -0800] "GET /index.html HTTP/1.1" 301 664 "-" "Mozilla/4.75 (Nikto/2.1.1) (Evasions:None) (Test:headers: etag)"
80.237.226.74 - - [12/Dec/2011:16:03:39 -0800] "GET /index.htm HTTP/1.1" 301 662 "-" "Mozilla/4.75 (Nikto/2.1.1) (Evasions:None) (Test:headers: etag)"
80.237.226.74 - - [12/Dec/2011:16:03:41 -0800] "GET /robots.txt HTTP/1.1" 301 664 "-" "Mozilla/4.75 (Nikto/2.1.1) (Evasions:None) (Test:headers: etag)"

```

If I open Lynx and go to check.torproject.org it says I am using TOR but unless I specify in the "system wide" proxy setting or the individual browser proxy settings to use TOR browsers like Chrome and Firefox do not use TOR. So at this point I know TOR is working and the transparent proxy connection to it is working until I do this:

Nmap from localhost:
```
root@localhost:/#nmap -sX 74.94.*.*
```

Syslog from Nmap on remote host:
```
Dec 12 16:21:05 hero kernel: [2513817.853877] Shorewall:logflags:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=40 ID=35897 PROTO=TCP SPT=41110 DPT=9535 WINDOW=3072 RES=0x00 URG PSH FIN URGP=0 
Dec 12 16:21:05 hero kernel: [2513817.854706] Shorewall:logflags:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=41 ID=63338 PROTO=TCP SPT=41110 DPT=5730 WINDOW=4096 RES=0x00 URG PSH FIN URGP=0 
Dec 12 16:21:05 hero kernel: [2513817.855567] Shorewall:logflags:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=43 ID=59086 PROTO=TCP SPT=41110 DPT=9290 WINDOW=2048 RES=0x00 URG PSH FIN URGP=0 
```
Obviously this just a sample of the pretty large output from the scan but the point is made with the source IP address.

Just as FYI all browser plugins like WebSecurify work fine with TOR as well.

So I guess my questions are: Is this normal? Am I missing something? Is there a better/easier way to proxy ALL traffic through TOR?

---

### Post by Dangertux on 2011-12-13
Probably because you're doing an Xmas scan...

Connect scan should work fine through tor. Read RFC 793 if you'd like to know why.

---

### Post by RyanRahl on 2011-12-13
It does it with any kind of scan from Nmap, I just chose -sX scan because I was testing and I was looking to be as noisy as possible.

here are the other scans:

local:
```
nmap -sS 74.94.*.*
```
remote
```
Dec 13 08:55:48 hero kernel: [2573500.805068] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=39 ID=26248 PROTO=ICMP TYPE=13 CODE=0
```

local:
```
nmap -sN 74.94.*.*
```
remote:
```
Dec 13 08:56:11 hero kernel: [2573523.810235] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=27 ID=50009 PROTO=ICMP TYPE=13 CODE=0
```

local:
```
nmap -sU 74.94.*.*
```
remote:
```
Dec 13 08:57:50 hero kernel: [2573622.966480] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=27 ID=46341 PROTO=ICMP TYPE=13 CODE=0
```

I haven't had time to read through the rfc so I'd like to ask, is there something particular about a xmas packet that would cause a machine to behave differently upon reception aside from a RST or just outright ignoring it because it doesn't make sense to receive an unsolicited packet like that?

---

### Post by Dangertux on 2011-12-13
> **RyanRahl said:**
> It does it with any kind of scan from Nmap, I just chose -sX scan because I was testing and I was looking to be as noisy as possible.

here are the other scans:

local:
```
nmap -sS 74.94.*.*
```remote
```
Dec 13 08:55:48 hero kernel: [2573500.805068] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=39 ID=26248 PROTO=ICMP TYPE=13 CODE=0
```local:
```
nmap -sN 74.94.*.*
```remote:
```
Dec 13 08:56:11 hero kernel: [2573523.810235] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=27 ID=50009 PROTO=ICMP TYPE=13 CODE=0
```local:
```
nmap -sU 74.94.*.*
```remote:
```
Dec 13 08:57:50 hero kernel: [2573622.966480] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=209.189.*.* DST=74.94.*.* LEN=40 TOS=0x00 PREC=0x20 TTL=27 ID=46341 PROTO=ICMP TYPE=13 CODE=0
```I haven't had time to read through the rfc so I'd like to ask, is there something particular about a xmas packet that would cause a machine to behave differently upon reception aside from a RST or just outright ignoring it because it doesn't make sense to receive an unsolicited packet like that?


The reason XMAS is different is because not all OS's respond to URG / PSH the same, so the response is different depending on the OS. Usually only nix's respond properly. Windows AIX and a handful of others will botch it up.

Did you try -sT?

---

### Post by RyanRahl on 2011-12-13
Well that seemed to work.
local:
```
nmap -sT 74.94.*.*
```
remote:
```
Dec 13 14:55:20 hero kernel: [2595072.211648] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=217.115.137.222 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=46 ID=58062 DF PROTO=TCP SPT=21778 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Dec 13 14:55:20 hero kernel: [2595072.271878] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=137.56.163.46 DST=74.94.*.* LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=56451 DF PROTO=TCP SPT=34106 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0 
```

Is it because of this info that I found in the manpage:
> Instead of writing raw packets as most other scan types do, Nmap asks the underlying operating system to
           establish a connection with the target machine and port by issuing the connect system call. This is the same high-level system call that web
           browsers, P2P clients, and most other network-enabled applications use to establish a connection.

I guess my next question is how do I transparently proxy ALL traffic, even the low level raw traffic that nmap produces?

the -sA, -sY, -sW, all give my real IP.

Something strange happened next. I went back to test the -sT again and now it reveals my true IP! I'm totally confused now because just to be sure I sent another NetCat connection and it logged a TOR router as the source.

---

### Post by Dangertux on 2011-12-13
> **RyanRahl said:**
> Well that seemed to work.
local:
```
nmap -sT 74.94.*.*
```remote:
```
Dec 13 14:55:20 hero kernel: [2595072.211648] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=217.115.137.222 DST=74.94.*.* LEN=52 TOS=0x00 PREC=0x20 TTL=46 ID=58062 DF PROTO=TCP SPT=21778 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Dec 13 14:55:20 hero kernel: [2595072.271878] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:30:18:a0:4c:c9:00:22:2d:c9:d4:fb:08:00 SRC=137.56.163.46 DST=74.94.*.* LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=56451 DF PROTO=TCP SPT=34106 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0 
```Is it because of this info that I found in the manpage:


I guess my next question is how do I transparently proxy ALL traffic, even the low level raw traffic that nmap produces?

the -sA, -sY, -sW, all give my real IP.

Something strange happened next. I went back to test the -sT again and now it reveals my true IP! I'm totally confused now because just to be sure I sent another NetCat connection and it logged a TOR router as the source.

Honestly, tor is a fickle beast with this type of thing, I might waiger it has something to do with the configuration of the exit router.

Out of curiousity why are you trying to make this type of traffic anonymous (also just consider using an FTP bounce scan). It generally doesn't mean you're up to a whole lot of good when you're trying to vuln scan anonymously ;-)

---

### Post by OpSecShellshock on 2011-12-13
> **Dangertux said:**
> Out of curiousity why are you trying to make this type of traffic anonymous (also just consider using an FTP bounce scan). It generally doesn't mean you're up to a whole lot of good when you're trying to vuln scan anonymously ;-)

Have to say I'm curious about that myself. In my experience from having external tests run from behind Tor nodes, I was still able to find ways of figuring out who they were and that they were testing. These are not exactly subtle tools in many hands.

---

### Post by RyanRahl on 2011-12-13
>  It generally doesn't mean you're up to a whole lot of good when you're trying to vuln scan anonymously
:lolflag:

This is very true and I am realizing how my posts may appear. Full disclosure: this is purely an educational curiosity thing. I have 2 offices and I am conducting these tests from one location to another. I recently read the Syngress book "Basics of Hacking and Penetration Testing" and I am experimenting with what I have read and trying different tools with different network configurations. I have 2 internet facing firewalls in my organization so as you may know I am pretty well constantly being scanned from all corners of the earth and this exercise was to gain a better understanding of how it all goes down from the other end. Most scans come from China, Russia and South America and I found it odd that there was little effort to conceal the source of the attacks. I'd bet that the machines scanning me are hijacked machines themselves. After reading that book I have become a lot more paranoid about the security of my systems and it has led me down a path that I never have gone down before. I will say I am totally fascinated by security research and I can see myself becoming a lot better versed in these technologies as time goes on.

---

### Post by Dangertux on 2011-12-13
> **RyanRahl said:**
> :lolflag:

This is very true and I am realizing how my posts may appear. Full disclosure: this is purely an educational curiosity thing. I have 2 offices and I am conducting these tests from one location to another. I recently read the Syngress book "Basics of Hacking and Penetration Testing" and I am experimenting with what I have read and trying different tools with different network configurations. I have 2 internet facing firewalls in my organization so as you may know I am pretty well constantly being scanned from all corners of the earth and this exercise was to gain a better understanding of how it all goes down from the other end. Most scans come from China, Russia and South America and I found it odd that there was little effort to conceal the source of the attacks. I'd bet that the machines scanning me are hijacked machines themselves. After reading that book I have become a lot more paranoid about the security of my systems and it has led me down a path that I never have gone down before. I will say I am totally fascinated by security research and I can see myself becoming a lot better versed in these technologies as time goes on.


Well you're correct in saying it's mostly compromised machines. While many of the utilities you are testing can utilize Tor most are just proxied through already compromised systems (in an actual attack). Honestly since you are in charge of either end point I wouldn't worry about anonymizing the traffic what are you going to do -- report yourself to the DOJ? ;-)

---

### Post by Dangertux on 2011-12-13
Just...nevermind...

---

### Post by RyanRahl on 2011-12-13
Jeez, that's a little over the top don't you think? I had a Fawkes mask as a profile pic leading up to Bank Transfer Day as a symbol and that was it. Who I follow on Twitter is my own business thanks, I follow movement politics and like it or not Anonymous is part f that.  This whole thing is a misunderstanding, I do own physically both the machines I'm working with, one is my home the other my office. I don't have any interest in hacking anything that isn't mine and I don't have any interest going to jail. I have a family and a home and I intend to keep it that way. This thread was a question about TCP/IP and how it works on a low level, why it behaves the way it does, that's all.I could have used any proxy, Tor was nust convienent. And the book was a free ebook. I don't make isany attempt to conceal who I am, if I wanted to use my computers illegally the last thing I would do is ask how to do it in a public forum with an email address I use for a bunch of other stuff. The reason I picked that book was because I first read the NetCat Power Tools and I liked the writing so I looked into the publisher. I'm reading the one about Xen virtualization now. The tweet about netcat is just something I read and thought it was amusing so I put it out there. I do know how to use netcat btw, that was a pretty harsh thing to say. I became interested in netcat while searching for a way to intercept traffic without having to turn my netbook into a router and place the machine I need to capture from on a seperate subnet.I have a copier /scanner that automatically adds slashes to SMB addresses (the host and sharename are seperate feilds)and I kept getting addressing errors. So I used netcat to forward traffic and capture the stream without a ton of network reconfiguration. I don't even know why I feel like I need to defend myself, I assure you my intentions are innocent. 


Btw netbus was just an example, the book wasn't focused on rootkits, it was an introduction to penetration testing in a professional environment. It has a whole chapter about good reporting, the book even said it wasn't going to go in depth about rootkits because they aren't something you use in a professional environment. They were covered to demonstrate the power of such things and why you want to protect from them.

---

### Post by Dangertux on 2011-12-13
> **RyanRahl said:**
> Jeez, that's a little over the top don't you think? I had a Fawkes mask as a profile pic leading up to Bank Transfer Day as a symbol and that was it. Who I follow on Twitter is my own business thanks, I follow movement politics and like it or not Anonymous is part f that.  This whole thing is a misunderstanding, I do own physically both the machines I'm working with, one is my home the other my office. I don't have any interest in hacking anything that isn't mine and I don't have any interest going to jail. I have a family and a home and I intend to keep it that way. This thread was a question about TCP/IP and how it works on a low level, why it behaves the way it does, that's all.I could have used any proxy, Tor was nust convienent. And the book was a free ebook. I don't make isany attempt to conceal who I am, if I wanted to use my computers illegally the last thing I would do is ask how to do it in a public forum with an email address I use for a bunch of other stuff. The reason I picked that book was because I first read the NetCat Power Tools and I liked the writing so I looked into the publisher. I'm reading the one about Xen virtualization now. The tweet about netcat is just something I read and thought it was amusing so I put it out there. I do know how to use netcat btw, that was a pretty harsh thing to say. I became interested in netcat while searching for a way to intercept traffic without having to turn my netbook into a router and place the machine I need to capture from on a seperate subnet.I have a copier /scanner that automatically adds slashes to SMB addresses (the host and sharename are seperate feilds)and I kept getting addressing errors. So I used netcat to forward traffic and capture the stream without a ton of network reconfiguration. I don't even know why I feel like I need to defend myself, I assure you my intentions are innocent. 


Btw netbus was just an example, the book wasn't focused on rootkits, it was an introduction to penetration testing in a professional environment. It has a whole chapter about good reporting, the book even said it wasn't going to go in depth about rootkits because they aren't something you use in a professional environment. They were covered to demonstrate the power of such things and why you want to protect from them.

Fair enough... I apologize if I over-reacted. However you should certainly understand how your line of questioning in conjunction with what I saw on your Twitter might have made me feel a little...Cautious.

In any case -- Tor isn't the best example for understanding how TCP/IP works at a low level, or how proxy services work. It uses something of a convoluted methodology. Start with a simple SOCKS proxy if that's what you're trying to learn then move on to Tor. Tor overcomplicates the entire situation.

As I said earlier, your issues may be due to the exit router's configuration. Tor is not an exact science.

Also Netbus is a RAT, not really a rootkit. But that's another discussion. 

Good luck with your issue. Again if my assumption was wrong I'm sorry. If not...Well...Yeah what I said earlier. Suffice it to say on the Internet, you can say your intentions are whatever you want them to be. Not that I don't trust you, but I don't have any real reason to trust you either... It's kind of a double edged sword like that, and you'd be surprised how many people ask for information on a public forum like that lol.

P.S : I wasn't saying YOU don't know how to use netcat, I just noticed the article lol.

---

### Post by RyanRahl on 2011-12-14
> you should certainly understand how your line of questioning in conjunction with what I saw on your Twitter might have made me feel a little...Cautious.

Yes I totally get that, that's why I said this was all a misunderstanding. Looking back on the posts I can totally see that and I apologize for sounding like a 'cracker' it's just that my curiosity sometimes leads me to to weird experiments. I also apologize for getting so defensive it's just that my morals are very important to me and being called a liar is very hurtful. 

>  Start with a simple SOCKS proxy if that's what you're trying to learn then move on to Tor
Will do... because that's really what the core of it is. I just want to understand why some things register as coming from the proxy and why some things(nmap) don't.
> As I said earlier, your issues may be due to the exit router's configuration. Tor is not an exact science....
...Good luck with your issue. 

Thanks for your support.:D It's not issue that is important in any real way, it was just bizarre behavior in my eyes so i brought it to the forums. Curiosity again.

---

### Post by nothingspecial on 2011-12-14
I think it would be better for all concerned if we just leave this one here.

Closed.

---

