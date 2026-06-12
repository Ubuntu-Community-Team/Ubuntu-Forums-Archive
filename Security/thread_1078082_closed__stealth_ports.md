---
title: "closed / stealth ports"
date: 2009-02-22
forum: Security
---

### Post by UBUminJ on 2009-02-22
Just switched from Windows to Ubuntu, so I am not yet very knowledgable about Linux. Sorry.

On my Windows all ports are in stealth mode (using Zonealarm, checked by "Shields Up", [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)).
On Ubuntu most ports are closed but not stealth ?
Why not ?

Thank you.

Michael

---

### Post by bodhi.zazen on 2009-02-23
It is a matter of semantics.

In Linux the firewall is iptables.

iptables will do 1 of three things (basically) with a packet ..

Accept

Drop

Reject

Drop = "stealth"
Reject = "closed"

See : [http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

I have a short section which discusses "Shields up".

Both closed and stealth are secure.

---

### Post by UBUminJ on 2009-02-23
Thank you for your answer and the link to your Iptables primer.

---

### Post by bodhi.zazen on 2009-02-23
You are most welcome.

---

### Post by sahabcse on 2009-02-23
Hi 

Try UFW (Uncomplicated Firewall). It is default fire wall, easy to manage iptables.Try for more info

================================================
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
=============================================


Regards
Sahab

---

### Post by cdenley on 2009-02-23
> **UBUminJ said:**
> 
On Ubuntu most ports are closed but not stealth ?
Why not ?

Why would you want them stealthed?

---

### Post by howlingmadhowie on 2009-02-23
> **bodhi.zazen said:**
> You are most welcome.

nice tutorial, bodhi.

a few suggestions for the css cos it's hurting my eyes atm!

for div#content:
font-size:12px;
font-family:sans-serif;
padding-left:200px;
padding-right:120px;

p.code 
font-family:monospace;

h2 
margin-left:-50px;

---

### Post by bodhi.zazen on 2009-02-23
> **howlingmadhowie said:**
> nice tutorial, bodhi.

a few suggestions for the css cos it's hurting my eyes atm!

for div#content:
font-size:12px;
font-family:sans-serif;
padding-left:200px;
padding-right:120px;

p.code 
font-family:monospace;

h2 
margin-left:-50px;

Thank you for the suggestions with css, greatly appreciated as I am more comfortable with the back end.

---

