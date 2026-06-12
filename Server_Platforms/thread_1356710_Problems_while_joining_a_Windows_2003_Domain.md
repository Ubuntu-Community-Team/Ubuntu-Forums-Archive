---
title: "Problems while joining a Windows 2003 Domain"
date: 2009-12-16
forum: Server Platforms
---

### Post by woehler on 2009-12-16
Hi there,

I used this tutorial to set up my ubuntu server into a windows 2003 domain. ([http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510))

When I make:
net ads join -U [email]myuser@MYDOMAIN.LOCAL[/email]

I get:
Failed to join domain: failed to lookup DC info for domain 'MYDOMAIN"' over rpc: Undetermined error

When I try kinit and klist it works. How can I resolve this problem?

Thank you in advanced. 
woehler

---

### Post by craigp84 on 2009-12-16
Here's 2 stabs in the dark -->

In your /etc/resolv.conf, does the (only) nameserver entry point to your windows DNS server?

On your active directory side, where is your global catalogue located? In a small network its going to be on the same host as the DC, but just in case its somewhere else (microsoft recommend you put it somewhere else from what i remember).

---

### Post by woehler on 2009-12-17
My resolve.conf look like this:

search DOMAIN.LOCAL
nameserver 192.168.206.1
nameserver 192.168.206.2
nameserver 192.168.206.3

Every IP above is a DC with global catalogue.

The server is located in our DMZ. Is this the problem?

---

### Post by craigp84 on 2009-12-17
Sounds a distinct possibility. Samba is saying it can't query the ms dns for SRV records. Do name lookups work from the dmz? What is your firewall policy on port 53 UDP and TCP which will also be required.

---

### Post by woehler on 2009-12-17
Port 53 was free.

Now I opened all ports between the KDC and the ubuntu server and now I get the following message:

Failed to join domain: failed to lookup DC info for domain 'domain_name' over rpc: Logon failure

kinit and klist works still fine.

---

### Post by craigp84 on 2009-12-17
> Logon failure

I think that's likely to be an accurate message, something about the authentication credentials are not suitable.

How are you specifying the username? DOMAIN\LinuxBridgeUser

As for the ports thing, you can do a packet sniff (install tcpdump or even wireshark on the linux host) to see what traffic is going between the boxes then cross reference against your firewall policy to see what you've missed. That will allow you to lock down the firewall policy again.

Sorry to keep harping on about DNS, but it's a relatively common error that firewall gui's make by labeling a convenience rule "DNS Access" and really it only opens UDP port 53 and the TCP port 53 is blocked.

Here's what MS say on the matter --> [http://support.microsoft.com/kb/832017](http://support.microsoft.com/kb/832017)

> 
DNS Server
The DNS Server service enables DNS name resolution by answering queries and update requests for DNS names. DNS servers are required to locate devices and services that are identified by using DNS names and to locate domain controllers in Active Directory.

```

System service name: DNS
Application protocol	Protocol	Ports
DNS	                  UDP	         53
DNS	                  TCP	         53

```



---

### Post by woehler on 2009-12-17
Ok, here is my solution:

I installed the VMWare client again with ubuntu server. I started the tutorial again. 

When I made "net ads join -U [email]Administrator@DOMAIN.LOCAL[/email]", I get the same error.

I tried "net ads join -U Administrator" and it works... 

Unusual.... but it works... :)

Thanks for your Help!

---

### Post by craigp84 on 2009-12-17
Nice :)

---

