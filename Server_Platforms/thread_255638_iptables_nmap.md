---
title: "iptables nmap"
date: 2006-09-11
forum: Server Platforms
---

### Post by distroman on 2006-09-11
First of, what I **don't** know about iptables, is a lot. I know I should go read some. 
Maybe someone could pass me some, easy to understand links. 
As I understand it, ubuntu comes with “out of the box” iptables. 

I got a question though. 

I ran a nmap and I am a bit confused about the output.
```
Starting Nmap 4.11 ( http://www.insecure.org/nmap ) at 2006-09-11 21:56
Interesting ports on
Not shown: 65532 filtered ports
PORT    STATE SERVICE
21/tcp  open  ftp
25/tcp  open  smtp
110/tcp open  pop3
```
I can't figure out if the ftp service, is open or not, or if it's just bound to localhost. 
I had a look here [http://ldrolez.free.fr/secu/](http://ldrolez.free.fr/secu/) but didn't make it, to clear at all.
I am really guessing, that this is not an issue at all, but I would like to know, a bit more about it.

Thanks

---

### Post by Klaidas on 2006-09-12
Well, if are nmap yourself (that is, nmap localhost or just nmap a computer which your are at now) it's ok.

---

### Post by distroman on 2006-09-12
Run with 
```
nmap -T Aggressive -P0 -sT -r -p 1-65535
```
on LAN

What if per say I was on a LAN, with about 300 other boxes, would it be a problem then?
If so, how would I close these ports/services?

---

### Post by steve.horsley on 2006-09-15
I think when nmap says they're open that means they are listening for incoming connections, and they accepted the connection from nmap. 

None of those ports are open on a default Ubuntu install, so I guess you have been installing servers.

---

