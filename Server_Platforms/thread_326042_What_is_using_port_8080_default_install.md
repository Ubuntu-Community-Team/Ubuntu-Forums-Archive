---
title: "What is using port 8080 default install?"
date: 2006-12-26
forum: Server Platforms
---

### Post by emocan on 2006-12-26
[B]What is using port 8080? default server install ( Ubuntu 6.10 )

I' am trying to install a chat software that uses port 8080, no success.
Can't see port 8080 at listen ports with netstat or lsof.


thx[/B]

---

### Post by tturrisi on 2006-12-27
Nothing should be using port 8080 on a default install.
If you have iptables (firewall) installed then it may be blocking port 8080.
Did you config the chat software to use 8080?  Is router port-forwarding 8080?

---

### Post by MadMan2k on 2006-12-27
apache?

---

### Post by MrHorus on 2006-12-27
> **emocan said:**
> 
I' am trying to install a chat software that uses port 8080, no success.


Unfortunatly that doesn't really tell us much.

In what way do you get "no success"?
Will it install but not run?
Do you get any error messages during the install process?
If so, what are they?

As stated before nothing should be using port 8080 out of the box although in production environments the convention is that it's the standard port for encrypted web connections (SSL).

---

### Post by MJN on 2006-12-29
> **MrHorus said:**
> As stated before nothing should be using port 8080 out of the box although in production environments the convention is that it's the standard port for encrypted web connections (SSL).
 
You're thinking of port 443.
 
That aside, I agree that we need more info as to what the actual symptoms are before being able to help much further...
 
Mathew

---

### Post by MrHorus on 2006-12-29
> **MJN said:**
> You're thinking of port 443.

Indeed, my mistake.

---

