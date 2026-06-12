---
title: "What does this ufw log mean?"
date: 2012-10-30
forum: Security
---

### Post by arroy_0209 on 2012-10-30
I have enabled ufw (sudo ufw enable) but not yet set any rules. However there are many (hundreds of such) UFW block messages in the ufw log, one example being:

```
[UFW BLOCK] IN=ppp0 OUT= MAC= SRC=210.4.15.236 DST=101.221.01.2 LEN=52 TOS=0x00 PREC=0x20 TTL=116 ID=4214 DF PROTO=TCP SPT=32581 DPT=1080 WINDOW=65535 RES=0x00 SYN URGP=0 
```What is meant by this? I am unable to find what port number 32581 signifies. some of such ports are stated to be unassigned by IANA. In general, when I notice such  ufw block message, should I be concerned? Do I need to do anything extra?

---

### Post by jerrrys on 2012-10-30
[http://ubuntuforums.org/showthread.php?t=1724144](http://ubuntuforums.org/showthread.php?t=1724144)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ufw+log&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ufw+log&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by OpSecShellshock on 2012-10-31
My guess: an external computer is attempting to use yours as a proxy, but since you aren't running a proxy server, the connection is being refused.

---

### Post by arroy_0209 on 2012-11-01
If that is true, I guess refusal for working as proxy has nothing to do with enabling ufw by me. In fact I have enabled ufw only recently and till that time there was no firewall. Is it possible that somebody might have accessed my computer while connected to internet? I have never got any positive response for "crontab -l" and no PID/Program name with "bin" from output of netstat -anlp. Are there other things to check in case of suspicion?

---

### Post by OpSecShellshock on 2012-11-01
Even without it enabled you still won't accept incoming connections unless you happen to be running a service like an ssh server or a web server or anything meant to accept incoming connections from the internet. A default installation won't have any of those things running. That's not really the whole picture, but it's good enough in most cases. There are ways of getting services opened and running without you knowing about it and then those services getting connected to, but those things don't happen often for desktop Linux users. I hope that makes sense. It's not safe, but it's not recklessly dangerous either.

Either way, it's certainly better that you're using it now. If you are using netstat to check for things, make sure you use sudo, and for clarity have browsers closed while checking.

---

### Post by Ms. Daisy on 2012-11-02
> **OpSecShellshock said:**
> Even without it enabled you still won't accept incoming connections unless you happen to be running a service like an ssh server or a web server or anything meant to accept incoming connections from the internet. A default installation won't have any of those things running. That's not really the whole picture, but it's good enough in most cases. There are ways of getting services opened and running without you knowing about it and then those services getting connected to, but those things don't happen often for desktop Linux users. I hope that makes sense. It's not safe, but it's not recklessly dangerous either.

Either way, it's certainly better that you're using it now. If you are using netstat to check for things, make sure you use sudo, and for clarity have browsers closed while checking.+1
When you see an incoming connection blocked, then you know your firewall is doing what it's supposed to. 

If you see an outgoing connection that you did not initiate, that's when you should do some more research.

To explain the port number you saw a little... you'll see a source port and a destination port. One of them will probably be higher than 1023 and one will probably be below that. Without going into technical details, that's just how connections work.  The ports below 1024 are registered, so those are the ones that will tell you what service is likely being used.  OpSecShellshock knew it was probably a proxy connection attempt because port 1080 is registered for socks proxy.
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

