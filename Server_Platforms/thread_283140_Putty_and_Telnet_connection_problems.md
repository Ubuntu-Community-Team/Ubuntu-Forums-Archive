---
title: "Putty and Telnet connection problems"
date: 2006-10-23
forum: Server Platforms
---

### Post by damonc on 2006-10-23
Hello,
I'm still battling away trying to follow the HowTo Forge on perfect server setup. I have followed the guide very carfully and have run into a few problems.

When I try and connect to the server through Putty (from a seperate machine on the LAN), I can only get a connection using the IP address, not the hostname or the FQDN.
```

unable to open connection to jfdcserver. host does not exist
``` 
Also, when trying to test Postfix I get timout errors:
```
root@jfdcserver:/home/admin# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 jfdcserver.example.com ESMTP Postfix (Ubuntu)
421 jfdcserver.example.com Error: timeout exceeded
Connection closed by foreign host.
root@jfdcserver:/home/admin#
```

Any ideas? All help greatly appreciated, as always!

---

### Post by DaveBorealis on 2006-10-23
> **damonc said:**
> When I try and connect to the server through Putty (from a seperate machine on the LAN), I can only get a connection using the IP address, not the hostname or the FQDN.

If you're connecting from a Unix-like machine, then one solution is to add the IP address and hostname/FQDN to /etc/hosts on the seperate machine.

For Windows/PuTTY I believe there's some place similar to /etc/hosts, but I don't remember off hand what it is.

/etc/hosts e.g.
```
127.0.0.1 localhost tom
127.0.1.1  tom
192.168.1.1             bill.guys     bill
192.168.1.2             bob.guys      bob

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Best regards,
Dave

---

### Post by damonc on 2006-10-23
> **DaveBorealis said:**
> For Windows/PuTTY I believe there's some place similar to /etc/hosts, but I don't remember off hand what it is.

Thanks Dave,
You reminded me that I had read something about a windows hosts file some time ago. I am trying to connect from a Windows XP laptop.

[This site]("http://vlaurie.com/computers2/Articles/hosts.htm") gives a fair description. I will have a play with it soon and let you know if it helped.

I wonder if this will help with both my problems...?

---

### Post by DaveBorealis on 2006-10-23
> **damonc said:**
> I wonder if this will help with both my problems...?

I missed the second one.  (Trying to type _and_ listen to my wife's play-by-play of the local election returns.)

Have you checked with your firewall to make certain that port 25 isn't being blocked?

Dave

---

### Post by damonc on 2006-10-24
> **DaveBorealis said:**
> Have you checked with your firewall to make certain that port 25 isn't being blocked?
To be honest, I'm just following [the guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") and hoping that it will work. I'm new to linux/servers and I'm just trying to bluff my way through! I will work out how to check the firewall and have a look when i get home from work.

These little challenges are what keeps it interesting.

---

### Post by damonc on 2006-10-24
> **DaveBorealis said:**
> For Windows/PuTTY I believe there's some place similar to /etc/hosts, but I don't remember off hand what it is.
Adding the line "192.168.1.100 jfdcserver.example.com jfdcserver"  to **Windows\System32\drivers\etc\hosts** file worked a treat.

Now onto the port 25 issue...

---

### Post by damonc on 2006-10-24
Problem solved. I didn't realise that I was supposed to type:
```
ehlo localhost
```after the connection was made. I was confused because there was no prompt, just a blank line.

When I type in the above command and the output was as expected:

```
ehlo localhost
250-jfdcserver.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME
```
Then just type "quit" to return to the shell.

---

