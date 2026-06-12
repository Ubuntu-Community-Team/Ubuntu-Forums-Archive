---
title: "problems with samba4"
date: 2010-04-24
forum: Server Platforms
---

### Post by tenmoi on 2010-04-24
Hi everyone,

I was following instructions on this site: [http://wiki.samba.org/index.php/Samba4/HOWTO#Report_your_success.2Ffailure.21](http://wiki.samba.org/index.php/Samba4/HOWTO#Report_your_success.2Ffailure.21)

And I am stuck at step #8

Background info:
1.I already have a basic DNS server up and running. DNS domain name is nubuntu.local
2. The samba4 sever is running on the same machine as the DNS server.

The problem is if I provision with the domain name nubuntu.local, I cannot start bind9 after including "/usr/local/samba/private/named.conf"; as per the wiki instruction.

The solution: re-provision with a subdomain like this abc.nubuntu.local and you can start bind9.

The new problem is the command (and the next two commands): 
```
$ host -t SRV _ldap._tcp.samdom.example.com.
```
fails, returning:
```
Host _ldap._tcp.sambaad.nubuntu.local not found: 2(SERVFAIL)
```

I'd really appreciate your help.

P.S.
I do not know much about Bind. I do have one book but I haven't read it completely. I just read the first few chapters to set up a basic server.


FYI:
My bind9 files:

---

### Post by HermanAB on 2010-04-24
Hmm, do one thing at a time.

Read the BIND manual and a few howtos and *test* your DNS with 'dig' (read the dig man page).

Once that works, try the next thing, else you are just running around like a headless chicken...

---

### Post by tenmoi on 2010-04-24
> **HermanAB said:**
> Hmm, do one thing at a time.

Read the BIND manual and a few howtos and *test* your DNS with 'dig' (read the dig man page).

Once that works, try the next thing, else you are just running around like a headless chicken...

Thanks,

I have managed to set up this samba4 server successfully, anyway. I mean I am now able to join a Windows client to it :guitar:. 

Been trying to join Ubuntu with SMDS.:).

---

