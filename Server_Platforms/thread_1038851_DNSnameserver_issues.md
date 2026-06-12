---
title: "DNS/nameserver issues"
date: 2009-01-14
forum: Server Platforms
---

### Post by anwoke8204 on 2009-01-14
hi, I am told that my name server/dns server isn't resolving addresses, but when I do the test config in bind in webmin, it says that all configureations are fine, anyone know how I can resolve this so my webserver will be fully operational?

TIA

the name server address if it helps is:
srv1.rooksystems.com

when I do an online nameserver test, I get the following error
Error: No answer from srv1.rooksystems.com at address 65.100.249.52 

is there a specific port I need to open in my router, other then the default DNS port?


could it also be that I don't have any reverse lookup zones (can't figure out how to get them to work/virtualmin didn't create any)

---

### Post by steve8track on 2009-01-14
If you want a website, you would need to port forward your server's ports 80 (http) and likely 443 (https SSL).  If you want an ftp server, then you would need to forward port 21, ssh is 22, and there are others for other software.

I hope this helps,

Steve

---

### Post by anwoke8204 on 2009-01-14
I have those ports opened as well as port 53 (default DNS port), but when I do any external tests on the name server, it fails, it is as if the name server isn't resolving the host names/refusing the connections.
any ideas as to why it isn't resolving, and how I fix it?

TIA

---

### Post by gombadi on 2009-01-14
Is the machine actually receiving dns packets and sending replies?

One way to check is to capture packets.

> 
sudo tcpdump -tnl -c 100 udp port 53


Then get someone to do a dns lookup and see if it captures request and reply packets.

---

### Post by anwoke8204 on 2009-01-14
here is the reply I got from the tcpdump

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
-v
quit
exit

0 packets captured
0 packets received by filter
0 packets dropped by kernel

---

### Post by gombadi on 2009-01-14
Your server never received any packets.

> 
I have those ports opened as well as port 53 (default DNS port)


Is that udp/tcp or both on port 53?

---

### Post by anwoke8204 on 2009-01-14
it doesn't look like it no, but right now it is on only TPC, let me change it to both tcp/udp, and try again.

I may also be doing the test wrong, i enter the tcpdump command, and then use an online dns lookup to do the test, will that work?

---

### Post by gombadi on 2009-01-14
Needs to be udp

I see the change to udp fixed it

```

dig +short @srv1.rooksystems.com rooksystems.com mx
0 srv1.rooksystems.com.
5 rooksystems.com.rooksystems.com.

```

---

### Post by anwoke8204 on 2009-01-14
ok, so if it is fixed, why are things still not working properly, I still can't get to webmail.rooksystems.com, admin.rooksystems.com or any of teh DNS aliases?

is there an online test I can do to test on my end that it is working?

---

### Post by gombadi on 2009-01-14
The rest of the world can see them or at least I can -
```

lroger@dave:~$ dig +short @srv1.rooksystems.com webmail.rooksystems.com
192.168.1.13
lroger@dave:~$ dig +short @srv1.rooksystems.com admin.rooksystems.com
192.168.1.13

```

There should be a page somewhere you can enter a host name and dns server to ask - not sure as I just use the command line.

The addresses above are private range addresses so do you have a machine in the local network that can send requests to your local dns server?

---

### Post by anwoke8204 on 2009-01-14
any idea as to why my priority 5 MX record is showing up as rooksystems.com.rooksystems.com?

---

### Post by gombadi on 2009-01-14
> 
any idea as to why my priority 5 MX record is showing up as rooksystems.com.rooksystems.com?


The entry in your config files will need a trailing .

i.e. rooksystems.com. instead of rooksystems.com

The trailing . tells bind not to add the domain name to the end of the entry.

---

### Post by anwoke8204 on 2009-01-14
ah didn't know that, i am switching from a windows based server, this has been a real learning experience, but it has been enlightening and fun.  thanks for the info and the assistance

---

### Post by anwoke8204 on 2009-01-14
it looks like there may still be an issue with my DNS, if I put in srv1.rooksystems.com for my MX record on my domains registered through godaddy(hosted on my , I get mail, however if I change the MX record from srv1.rooksystems to mail.rooksystems.com I can't recieve email anymore I can send, but can't recieve, any idea as to how I fix this?

TIA

---

### Post by robgolding63 on 2009-01-14
It's because mail.rooksystems.com resolves to 192.168.1.13 - which is not accessible from the outside world. I'm guessing it needs to be set to 65.100.249.52 - which is what srv1.rooksystems.com resolves to - and that works.

Hope this helps,

Rob

---

### Post by anwoke8204 on 2009-01-14
I changed the mx record from 192.168.1.13 to 65.100.249.52, sent myself a test email from my gmail account to my server, and it didn't recieve it.  I have dynamic domains that are running off of mail.dynamicname.no-ip.info with 192.168.1.13 as the ip address for the mx record and they are working fine.  any other ideas?
TIA

---

### Post by anwoke8204 on 2009-01-14
ok, now I have really goofed  up, lol
while trying to get things to work, when you ping either rooksystems.com or realdealcars.org it times out because it tries to ping address 192.168.1.13 instead of my modem ip address and I can't get it changed back, how do I fix this so that when you ping those it reflects my modem ip address.

TIA

---

