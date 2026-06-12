---
title: "How to join domain in Ubuntu desktop?"
date: 2010-11-04
forum: Server Platforms
---

### Post by raymondxmak on 2010-11-04
I use Samba on Ubuntu 10.04 LTS server as domain controller and sucessfully let a Windows 7 machine join the domain.
Then I tried to let a Ubuntu 10.04 Desktop machine join the domain but fail.
Here is my join command and error message:
sudo domainjoin-cli join TEST root@TEST
Joining to AD Domain: TEST
With Computer DNS Name: raymond-ubuntu.test
root@TEST's password: 
Error: Lsass Error [code 0x00080047]
9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially the requested address does not exist.
And I tried another command and failed also:
sudo net dom join -S ubuntu-server -U ubuntu-server\\root%12345678 domain=TEST account=TEST\\root password=12345678
Failed to join domain: Access is denied
Please help.
Raymond

---

### Post by HermanAB on 2010-11-05
Howdy,

Test your DNS with 'dig'.  Read the dig man page, it is quite trivial, then fix the problem in your DNS server, before you try to continue.

---

### Post by raymondxmak on 2010-11-05
Hi HermanAB,
Thank you for your reply.
 
My understanding about DNS is:
It is retrieved from ISP automatically when make connection. Wherever the OS need DNS I enter 192.168.2.1, it is my router's IP address,
I don't know what DNS related to a domain controller.
Would you please explain more?
 
I tried dig and here is the result:
; <<>> DiG 9.7.0-P1 <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29087
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;.    IN NS
;; ANSWER SECTION:
.   192712 IN NS l.root-servers.net.
.   192712 IN NS m.root-servers.net.
.   192712 IN NS a.root-servers.net.
.   192712 IN NS i.root-servers.net.
.   192712 IN NS d.root-servers.net.
.   192712 IN NS e.root-servers.net.
.   192712 IN NS j.root-servers.net.
.   192712 IN NS c.root-servers.net.
.   192712 IN NS f.root-servers.net.
.   192712 IN NS b.root-servers.net.
.   192712 IN NS g.root-servers.net.
.   192712 IN NS h.root-servers.net.
.   192712 IN NS k.root-servers.net.
;; Query time: 7 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Sat Nov  6 00:30:46 2010
;; MSG SIZE  rcvd: 228
 
Thanks
Raymond

---

### Post by HermanAB on 2010-11-05
Well, I don't know your setup, but it looks like you are trying to access a machine with two different names TEST and test (DNS is case sensitive if the name is defined in anything other than lower case. 

These two things are probably not the same thing:
root@TEST
raymond-ubuntu.test

That is why I think that your DNS setup is probably bad.

So you got to resolve this error message:
9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially the requested address does not exist.

---

