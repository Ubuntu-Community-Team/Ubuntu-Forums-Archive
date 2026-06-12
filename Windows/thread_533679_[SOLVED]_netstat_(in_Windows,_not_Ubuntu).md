---
title: "[SOLVED] netstat (in Windows, not Ubuntu)"
date: 2007-08-24
forum: Windows
---

### Post by nvteighen on 2007-08-24
Hi, 
I've did a "netstat -an" in a XP machine (apropos: did Microsoft steal "netstat"? It has the same arguments as in Linux!) and I got that the computer was listening from some ports at IP 0.0.0.0. For example, 0.0.0.0:7... What does that IP mean? Is it dangerous?

(In my Ubuntu, netstat won't show any listening ports at 0.0.0.0)

---

### Post by retr0virus on 2007-08-24
If you type "netstat 0.0.0.0" in google you will find this first:
[http://support.microsoft.com/?scid=kb%3Ben-us%3B175952&x=19&y=12](http://support.microsoft.com/?scid=kb%3Ben-us%3B175952&x=19&y=12)
And there you will find your answer. It is a normal behaviour of netstat in Windows.

---

### Post by nvteighen on 2007-08-24
> **retr0virus said:**
> If you type "netstat 0.0.0.0" in google you will find this first:
[http://support.microsoft.com/?scid=kb%3Ben-us%3B175952&x=19&y=12](http://support.microsoft.com/?scid=kb%3Ben-us%3B175952&x=19&y=12)
And there you will find your answer. It is a normal behaviour of netstat in Windows.
Thanks!

Apologize for the inconvenience

---

