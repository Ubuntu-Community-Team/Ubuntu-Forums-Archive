---
title: "tcp wrapper on a dekstop/ no server situation?"
date: 2011-03-30
forum: Security
---

### Post by Soul-Sing on 2011-03-30
Hi, I did a NMAP on a 10.4 desktop system.
Found tcp wrapper on my system with an open port. Again I do not run a server. etc/host-deny and etc/host-allow contain no active elements. I know tcp wrapper as a great tool to secure a server.
Closing the port with ufw gives no result, tcp wrapper still show up.
Anyone with some advice on this?

---

### Post by bodhi.zazen on 2011-03-30
what is the exact output and where are you running nmap from ? localhost or from a remote host ?

---

### Post by Soul-Sing on 2011-03-30
[COLOR="Magenta"]23/tcp open  tcpwrapped[/COLOR]: outcome
nmap running from [COLOR="Red"]localhost[/COLOR]

i add some nice colors, need some attention...:)

---

### Post by bodhi.zazen on 2011-03-30
First, running nmap on localhost is a bit misleading as it will services listening only on localhost will show as open.

If you are wanting information on open ports on localhost IMO you have severa much better options:

```
netstat -an | grep LISTEN | grep -v ^unix
netstat -ntulp
lsof -i -n -P
```

Second, port 23 is typically telnet and I would assume you know if you installed telnet for some reason ?

As far as the "tcpwrapped" in the output, that does not directly refer to tcpwrapper, or imply that tcpwrapper is "listening" on that port, it refers to behavior on the server.

I could not find a detailed discussion, see:

[http://seclists.org/nmap-dev/2007/q4/599](http://seclists.org/nmap-dev/2007/q4/599)

If you wanted to know the details, use tcpdump or wireshark to capture the packets and compair an open port to a tcpwrapped port.

It seems this information is somewhat unreliable as you can see from that discussion and nmpa lists port 80 as tcpwrapped. Unless one compiles apache from source, apache does not use tcpwrapper :)

HTH

---

### Post by Soul-Sing on 2011-03-31
> netstat -an | grep LISTEN | grep -v ^unix
netstat -ntulp
lsof -i -n -P

these give "no noise", no information.
running tcpdump gives "no noise".

the thing that really puzzled me is why I can't close the relevant port via ufw. 
(And why it is related, or seems to be realted, to a server like tool)

---

### Post by bodhi.zazen on 2011-03-31
My guess is that you can not "close" that port as you are scanning from localhost, and ufw will not restrict connections on localhost (127.0.0.1).

You need to either scan from another box (which is what I would advise), or use an alternate tool.

If you need further assistance, please post the raw output from the relevant commands. Would be nice to see the contents of /etc/hosts./deny and /etc/hosts.allow as well.

When you post nonsensical information such as "no nose" I can not really help you interpret the situation / data.

---

### Post by Soul-Sing on 2011-04-27
sudo lsof -i -n -P
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient  799 root    5w  IPv4   4332      0t0  UDP *:68 

no telnet based programs installed here.

in /etc/hosts(deny/allow) all is "outcommented" with a #

running tcpdump gives no noise/information.

---

