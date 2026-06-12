---
title: "SSH Proxies ? Tunneling? SOCKS?"
date: 2008-10-22
forum: Security
---

### Post by user9015 on 2008-10-22
I'm trying to learn about how to make my internet travels secure, and anonymous. There is a TON of info out there on the subject, but I'm having some confusion with regards to what I should be doing/using.  I tried installing TOR and such through firefox, I did an anonymous PC Audit Check, and it appeared as though using TOR was successful.  However, it seemed to decrease the usability of the internet drastically in that it was deathly slow, and there was a lot of things I couldn't do/links I couldn't click on/content I couldn't access. 

I then found a thread on some forum saying to open an ssh proxy account and that will consequently create a SOCKS Proxy to tunnel into the ssh account and encrypt all my internet stuff. I found a website that offers this kind of service for a reasonable charge [www.sh3lls.net](www.sh3lls.net).  But I don't know if this is what I actually want..  and I don't want to pay for something if it's the wrong thing.  Any insight would be highly appreciated.

Linux Newbie

fyi I'm running Ubuntu 8.04

---

### Post by jerome1232 on 2008-10-22
You better check that they allow ssh tunneling, allot of ssh servers disable it.

Creating a ssh tunnel and using it as a socks proxy will encrypt all of your traffic between your computer and the other computer, it still goes out over the web as normal, and as I understand it dns requests will still get sent unencrypted (meaning someone sniffing the traffic on the LAN could tell what sites you visited, but they couldn't get any of the traffic that was actually exchanged) there is a workaround to get the dns requests sent encrypted. (can't find it at the moment)

Really this is just something to prevent people from sniffing your wifi traffic and/or to protect your traffic from someone connected to the lan who is sniffing packets trying to glean useful info.

---

### Post by user9015 on 2008-10-22
So ...  hmm.. Say I was at work, and logged onto the server with my personal laptop.  could I was doing this ssh tunneling and SOCKS proxy stuff, would the IT people be able to still track everything I was doing?

---

### Post by jerome1232 on 2008-10-22
Assuming the dns requests are encrypted, all they can tell is that you opened an encrypted connection to whatever host your ssh'ing to, and that data is being sent to/from those two computers, and what port your using to send the encrypted data.

The rest of the world would see all your traffic as coming from the computer that your ssh'd to.

If your work was really interested in your suspicious activity they could figure out who that ip belongs to that your ssh'ing to, and if the company that you bought the account from is willing to give away what traffic the computer that your ssh'd to is sending/receiving then I guess they could figure it out. 

edit: It seems they have a service explicitly for proxies/ssh tunneling. 
[http://www.sh3lls.net/proxy/index.html](http://www.sh3lls.net/proxy/index.html)

---

### Post by user9015 on 2008-10-22
interesting...  Not that I'm up to anything crazy..  ebay and craigslist just arn't typically deemed workplace suitable...  lol  and I have a lot of down time in my job.  Better to surf the web then fall asleep working 3rd shift if you know what I'm saying

---

### Post by user9015 on 2008-10-22
That website that I posted [www.sh3lls.net](www.sh3lls.net)  it says it has 2 different services each for $5 a month.  one is ssh tunnel proxy, and the other is socks proxy...  Which do I need?  or do I need both?

---

### Post by jerome1232 on 2008-10-22
A little  bit of reading ;) I would say ssh tunnel but only because I'm familiar with exactly what it's doing.

[http://en.wikipedia.org/wiki/Tunneling_protocol#SSH_tunneling](http://en.wikipedia.org/wiki/Tunneling_protocol#SSH_tunneling)

[http://en.wikipedia.org/wiki/SOCKS](http://en.wikipedia.org/wiki/SOCKS)

edit: As Dr. Small has pointed out, an ssh tunnel is in fact creating a socks proxy so I would say they are the same. They have the ability to encrypt all data over one port, bypassing restrictive firewalls and preventing any sniffing of the traffic between the two connection points.

---

### Post by user9015 on 2008-10-22
I don't have any restrictive firewalls with the exception of filters on work oriented email.  which I think is through outlook, but that's on work computers, not on my personal Linux system obviously.  I just want to avoid any potential hassles at work by staying under the radar with my personal machine.

---

### Post by kevdog on 2008-10-22
Dont you have another computer at home for example that could act as the ssh server?  Yes you could pay someone to do this, but in many cases all you need is another computer somewhere that could run an ssh server.  This could even be a windows computer that could run an ssh server courtesy of the cygwin installation.  Its not a linux thing.

Your employer would only be able to detect network traffic, however the packets would all be encrypted.  Tunneling DNS queries provides more security, however in some cases this has detrimental consequences in terms of performance issues.

---

### Post by Dr Small on 2008-10-22
> **jerome1232 said:**
> Alot of the time people will call using a ssh tunnel to encrypt your traffic 'using it as a socks proxy'. I *think* socks is  more of a way to get out of restrictive firewalls. SSH accomplishes this (getting past restrictive firewalls) and encrypts the data.


I thought when you connected to the SSH server with the -D option, you are creating a SOCKS proxy to the server. Because after I connect with something like this:
```
ssh -N -D 1991 user@host
```

I go into Firefox Network Settings, and use the SOCKS5 proxy settings to connect to localhost 1991


**Edit**
From the SSH manual:
```

       -D [bind_address:] port
              Specifies a local ``dynamic'' application-level port forwarding.
              This works by allocating a socket to listen to port on the local
              side,  optionally bound to the specified bind_address.  Whenever
              a connection is made to this port, the connection  is  forwarded
              over  the  secure  channel, and the application protocol is then
              used to determine where to connect to from the  remote  machine.
              Currently the **SOCKS4** and **SOCKS5** protocols **are supported**, and _ssh_
              _will act as a SOCKS server_.  Only root  can  forward  privileged
              ports.   Dynamic  port  forwardings can also be specified in the
              configuration file.

```

---

### Post by jerome1232 on 2008-10-22
Yeah, my last post was pretty much part retarded. The ssh tunnel *is* creating a socks proxy on localhost.

---

