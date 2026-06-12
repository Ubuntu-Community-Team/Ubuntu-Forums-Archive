---
title: "A Question on localhost (127.0.0.1)"
date: 2006-09-16
forum: Server Platforms
---

### Post by Sagotis on 2006-09-16
Hi All

I did an nmap on localhost (127.0.0.1) and I get this:

[I]Interesting ports on localhost (127.0.0.1):
Not shown: 65530 closed ports
PORT      STATE SERVICE
631/tcp   open  ipp
8118/tcp  open  unknown
9050/tcp  open  unknown
44074/tcp open  unknown
48218/tcp open  unknown[/I]

I know that ports 8118 and 9050 have to do with Tor, however, is port 631 something to do with Internet Printing Protocol (ipp) and if so how can i disable it, and if I do will it break something on my system (such as pringing)?

Also I have no clue as to what ports 44074 and 48218 deal with thus is there a way to see which progs are trying to access these ports?

Thanks

Sagotis

---

### Post by Sagotis on 2006-09-16
Sorry All

It seems after looking into the nmap commands a bit further I can have it spit this out:

[I]PORT      STATE SERVICE     VERSION
631/tcp   open  ipp         CUPS 1.2
8118/tcp  open  http-proxy  Junkbuster/Privoxy webproxy
9050/tcp  open  tor-socks   Tor SOCKS Proxy
44074/tcp open  hpssd       HP Services and Status Daemon
48218/tcp open  hpiod       HP Linux Imaging and Printing System[/I]

One thing is for sure, I love nmap!

The command for that, if anyone wanted to know is: sudo nmap -sS -sR -sV -p- -PI -PT -vv 127.0.0.1 :D.

Yep, I am still a nub :roll:

Sagotis

---

