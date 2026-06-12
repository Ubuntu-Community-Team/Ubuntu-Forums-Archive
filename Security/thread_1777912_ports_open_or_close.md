---
title: "ports open or close?"
date: 2011-06-08
forum: Security
---

### Post by luofeiyu on 2011-06-08
sudo ufw status
Status: active

To Action From
-- ------ ----
Anywhere DENY 220.182.50.30
Anywhere DENY 183.28.249.110
Anywhere DENY 60.173.9.73
9415 DENY Anywhere
11705 DENY Anywhere
Anywhere DENY 60.173.10.172
Anywhere DENY 60.173.12.114
Anywhere DENY 60.173.26.35
Anywhere DENY 60.173.12.115
Anywhere DENY 222.186.26.202
Anywhere DENY 222.186.23.153
10000 DENY Anywhere
45368 DENY Anywhere
51577 DENY Anywhere
25/tcp DENY Anywhere
139 DENY Anywhere
445 DENY Anywhere
631 DENY Anywhere
8888 DENY Anywhere
9415 DENY Anywhere (v6)
11705 DENY Anywhere (v6)
10000 DENY Anywhere (v6)
45368 DENY Anywhere (v6)
51577 DENY Anywhere (v6)
25/tcp DENY Anywhere (v6)
139 DENY Anywhere (v6)
445 DENY Anywhere (v6)
631 DENY Anywhere (v6)
8888 DENY Anywhere (v6)

~$ nmap 127.0.0.1

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-06-08 17:32 CST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00062s latency).
Not shown: 994 closed ports
PORT STATE SERVICE
25/tcp open smtp
139/tcp open netbios-ssn
445/tcp open microsoft-ds
631/tcp open ipp
8888/tcp open sun-answerbook
10000/tcp open snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.33 seconds

i have closed ports : 25 \139\445\631\8888\10000,why in the nmap ,these ports are open?

---

### Post by spynappels on 2011-06-08
UFW/GUFW doesn't firewall the lo (loopback) interface as far as I know.

You are better running nmap from another computer on the same network to see what is happening to external connection attempt.

---

### Post by psusi on 2011-06-08
Blocking ports with a firewall is like unplugging the telephone from the line.  If you don't want to answer, then why did you pay for the line in the first place?

In other words, if you don't want to accept connections on port 25, then don't install an smtp server.

---

### Post by bodhi.zazen on 2011-06-08
> **psusi said:**
> Blocking ports with a firewall is like unplugging the telephone from the line.  If you don't want to answer, then why did you pay for the line in the first place?

In other words, if you don't want to accept connections on port 25, then don't install an smtp server.

I would disagree with that.

It depends on the server, some servers are intended to be public, apache or a public FTP server.

Other servers are intended to be private, VNC and SSH.

You would configure your firewall in various ways depending on the needs of your server.

I would agree that this is not windows and I would discourage installing a Firewall on Linux because that is the way it is done on windows , feeling that you are somehow more secure with a firewall just because you activated it, etc, etc.

Security is an active process and requires a willingness on the part of users to learn, and more experienced users to explain.

By default, there are no significant open ports on a default Ubuntu installation, so there is nothing to firewall.

The OP needs to explain what services they plan to run and what firewall needs they have .

---

### Post by bodhi.zazen on 2011-06-08
> **luofeiyu said:**
> i have closed ports : 25 \139\445\631\8888\10000,why in the nmap ,these ports are open?

You need to understand what nmap is telling you and what the lo interface is.

If you scan localhost, you are scanning the lo interface.

You can use a different tool from localhost to see what services are listening and on what address/interface.

```
netstat -an | grep LISTEN | grep -v ^unix
```

```
netstat -ntulp
```

```
lsof -i -n -P 
```

I believe the mistake you are making it to run a tool (nmap) without reading the documentation.

As to what those services are, what did you install ? I know some of those ports off the top of my head, 631 is CUPS (printing) for example.

25 is for mail. [http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)

139 and 445 for samba (file sharing)

The nmap is telling you the default service that runs on those ports and the commands I gave you will tell you more.

I have not idea about the other 2 ports.

Hopefully my post has clarified

---

### Post by The Cog on 2011-06-09
> **psusi said:**
> Blocking ports with a firewall is like unplugging the telephone from the line.  If you don't want to answer, then why did you pay for the line in the first place?

In other words, if you don't want to accept connections on port 25, then don't install an smtp server.
I like that analogy, and in general, I agree. 

There may be times where you want to allow connections from some IP addresses and not others, and in that situation, a firewall is one way to achieve it. Specific application settings might occasionally do instead, but I like the fact that the firewall can be a single place to control all network access. 

But often your services are intended to be publicly reachable. In which case installing a firewall that blocks connections to them, and then reconfiguring that firewall to allow connections through again, is a bit of a waste of time.

---

