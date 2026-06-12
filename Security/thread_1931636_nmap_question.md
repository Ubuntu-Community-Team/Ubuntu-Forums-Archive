---
title: "nmap question"
date: 2012-02-25
forum: Security
---

### Post by Diametric on 2012-02-25
Hello,

How vulnerable am I that while working my way through an nmap book and scanning my own network that I see that anyone who hits my router can see that I have ssh, vnc etc...?  Just with that info alone..no social engineering just that info - an IP and a few open ports/services.

Thank you in advance!

---

### Post by CharlesA on 2012-02-25
I wouldn't have VNC exposed to the internet.

As long as SSH is secured correctly you should be fine.

---

### Post by enjoijesus94 on 2012-02-25
So you want to find out whos on your router ?

---

### Post by Diametric on 2012-02-25
@ChalesA - thanks, I'll disable it...I've read how open it is.

Not so much to see who's on my router, but just for general info.  I mean, I'm starting to understand what kind of info is easily obtained.  But I'm still novice enough to wonder how vulnerable I am.  Check out the out-put from a:

```
nmap -A x.x.x.x
```


```
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 5.8p1 Debian 7ubuntu1 (protocol 2.0)
23/tcp   open  tcpwrapped
80/tcp   open  http       Verizon FIOS Actiontec http config
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
|_http-title: Verizon
443/tcp  open  ssl        OpenSSL (SSLv3)
|_sslv2: server still supports SSLv2
992/tcp  open  ssl        OpenSSL (SSLv3)
4567/tcp open  http       ActionTec TR-069 remote access
|_http-title: 405 Method Not Allowed
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
5800/tcp open  vnc-http?
|_http-methods: No Allow or Public header in OPTIONS response (status code 400)
5900/tcp open  vnc        VNC (protocol 3.7)
8080/tcp open  http       Verizon FIOS Actiontec http config
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
|_http-title: Verizon
8443/tcp open  ssl        OpenSSL (SSLv3
```)

Any comments on this would be greatly appreciated.

---

### Post by CharlesA on 2012-02-25
Looks fine but I'd kill VNC.

Most of those look like stuff that FIOS keeps open for remote access.

---

### Post by enjoijesus94 on 2012-02-25
> **Diametric said:**
> @ChalesA - thanks, I'll disable it...I've read how open it is.

Not so much to see who's on my router, but just for general info.  I mean, I'm starting to understand what kind of info is easily obtained.  But I'm still novice enough to wonder how vulnerable I am.  Check out the out-put from a:

```
nmap -A x.x.x.x
```
```
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 5.8p1 Debian 7ubuntu1 (protocol 2.0)
23/tcp   open  tcpwrapped
80/tcp   open  http       Verizon FIOS Actiontec http config
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
|_http-title: Verizon
443/tcp  open  ssl        OpenSSL (SSLv3)
|_sslv2: server still supports SSLv2
992/tcp  open  ssl        OpenSSL (SSLv3)
4567/tcp open  http       ActionTec TR-069 remote access
|_http-title: 405 Method Not Allowed
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
5800/tcp open  vnc-http?
|_http-methods: No Allow or Public header in OPTIONS response (status code 400)
5900/tcp open  vnc        VNC (protocol 3.7)
8080/tcp open  http       Verizon FIOS Actiontec http config
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
|_http-title: Verizon
8443/tcp open  ssl        OpenSSL (SSLv3
```)

Any comments on this would be greatly appreciated.

Yes me being at 18 years old i know about Security and pentesting.
check out port 80/tcp
Thats where most peoples problems come in.

make sure network is set good with a password that contains underscore and letters and charecters.

usally FTP can be bruteforced or dictonary attacked by attacking the router with a series of guesses that the attacker has input.

Not only that make sure you are on encryption higher than WEP.

they are automatically crackable.

clients or no clients.

hope this makes sense my friend):P

---

### Post by Diametric on 2012-02-25
Good enough - thanks for all the replies.

---

### Post by enjoijesus94 on 2012-02-25
> **Diametric said:**
> Good enough - thanks for all the replies.

No Problem Man:popcorn:

---

