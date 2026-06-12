---
title: "OpenOffice makes DNS Calls"
date: 2011-05-10
forum: Security
---

### Post by SparTacux on 2011-05-10
I'm just curious about this and would like to find out why OpenOffice makes two DNS calls every time I open a document. I can create a document in word and then save it. When I open it, my modem always logs two DNS calls going out. It does the same with the spreadsheet program. 

Does anyone know the reason for this and is there anyway of looking at the DNS packets to see what IP address they are looking up?

---

### Post by uRock on 2011-05-10
Moved to security discussions. 

I have confirmed the issue using EtherApe. Not sure why.

---

### Post by doas777 on 2011-05-10
you my freind, are looking for Wireshark. you should find it in the repos. just fire it up, start captureing, and open a document. 
otherwise if you can get the ascii of the packet, here is the DNS datagram format
[http://www.netfor2.com/dns.htm](http://www.netfor2.com/dns.htm)

---

### Post by SparTacux on 2011-05-12
Well - I'm guessing this isn't really being seen as a problem.  Nice to see someone else confirm it though and it ain't just happening on my puter.

---

### Post by Irihapeti on 2011-05-12
> **SparTacux said:**
> Well - I'm guessing this isn't really being seen as a problem.  Nice to see someone else confirm it though and it ain't just happening on my puter.

Pure guesswork here, but could it be something to do with the "improvement program"? (See Options under Tools menu in Writer.) That would be the kind of thing that might want to access remote locations.

---

### Post by pixeldigi on 2011-05-13
So I had some free time... LibreOffice (openoffice) does in fact perform a query. The query sent, that I verified, included a request for my machine name.

I compared my output and it appears to be a known issue/bug as found here (not malicious, possibly related to a function of the printing system): [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176)

Snip of packets from my testing:
```
101205	584.878173	192.168.0.212	192.168.0.1	DNS	Standard query A testbox.(none)
101254	584.961364	192.168.0.1	192.168.0.212	DNS	Standard query response, No such name
```

---

### Post by uRock on 2011-05-13
> **pixeldigi said:**
> So I had some free time... LibreOffice (openoffice) does in fact perform a query. The query sent, that I verified, included a request for my machine name.

I compared my output and it appears to be a known issue/bug as found here (not malicious, possibly related to a function of the printing system): [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176)

Snip of packets from my testing:
```
101205	584.878173	192.168.0.212	192.168.0.1	DNS	Standard query A testbox.(none)
101254	584.961364	192.168.0.1	192.168.0.212	DNS	Standard query response, No such name
```
Looks like your DNS server is on the internal network. If you can see the text in the packet, it is querying a 72.x.x.x number, at least it was on my system. The address was only listed as being owned by Cox Communications and it didn't show who they have it leased to.

---

### Post by pixeldigi on 2011-05-13
> **uRock said:**
> Looks like your DNS server is on the internal network. If you can see the text in the packet, it is querying a 72.x.x.x number, at least it was on my system. The address was only listed as being owned by Cox Communications and it didn't show who they have it leased to.

Correct. The DNS server is the target. The query is for the hostname. In my case the DNS is on the internal network (and forwards to the root servers for recursion, which I do see in my packets as <Root>: type SOA, class IN, mname a.root-servers.net in the forwarded request). 

The 72.x.x.x you are seeing is most likely the DHCP or manually assigned DNS (cat your /etc/resolv.conf to check).

I repeated the test on my work machine. The query is for the hostname I have assigned to the machine (we query DNS for names, ARP is for address/MAC combinations).

My DNS query when repeated was as such:

```

Wireshark filter: udp.port==53

Destination: Internet Protocol, Src: 192.168.0.207 (192.168.0.207), Dst: 192.168.0.1 (192.168.0.1)

iceexchange.(none): type A, class IN

```

The response in the next packet:

```

Flags: 0x8183 (Standard query response, No such name)

```

I don't see any other indication in the source or destination address, hex, or otherwise that indicates my machine is attempting to query anything other than the DHCP assigned DNS and the machine name assigned to the unit. Verify your DNS server and query. I am going to remote a machine in my colo on the internet and see if I can repeat the test with a internet addressed machine and outside DNS.

---

### Post by uRock on 2011-05-13
The 72.x.x.x is a Atlanta Cox address. I am nowhere near Atlanta.

The address is 5 hops outside of my network, but I am guessing that it is possible for Cox to have their DHCP server that far away.

I have turned off the "improvement program" feature and this DNS query still happens.

---

### Post by doas777 on 2011-05-14
seems potentially related:
[http://user.services.openoffice.org/en/forum/viewtopic.php?p=154840#p154840](http://user.services.openoffice.org/en/forum/viewtopic.php?p=154840#p154840)

the hostname query may be realted to a host of functionality from network printer enumeration, to update checking.

---

