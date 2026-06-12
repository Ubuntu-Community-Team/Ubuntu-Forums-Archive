---
title: "Ports Open"
date: 2009-04-24
forum: Security
---

### Post by riskyayush on 2009-04-24
Hi, 
I recently installed Firestarter. I ran through the setup wizard and did exactly as I was told to. 
Now when I try and check the status of my computers ports through Shields Up, it shows that my following ports are opened:
SSH
HTTPS
HTTP.

I am assuming these ports, if open, are very dangerous. So please suggest how to close these ports.
Thank you

---

### Post by brian_p on 2009-04-24
> **riskyayush said:**
> Hi, 

I am assuming these ports, if open, are very dangerous.

Not so.

> So please suggest how to close these ports.

Configure firestarter correctly.

---

### Post by dburnett77 on 2009-04-24
> **riskyayush said:**
> Hi, 
I recently installed Firestarter. I ran through the setup wizard and did exactly as I was told to. 
Now when I try and check the status of my computers ports through Shields Up, it shows that my following ports are opened:
SSH
HTTPS
HTTP.

I am assuming these ports, if open, are very dangerous. So please suggest how to close these ports.
Thank you

Open the Firestarter GUI, select the last tab on the right..."Policy".
Then in the drop-down menu, select "Outbound Policy..."
"Restrictive" allows only the ports you want, "Permissive" will deny the ports you specify.
There's a drop down menu there with some of the ports that can access the most resources.  Try that.

---

### Post by JK3mp on 2009-04-24
> **brian_p said:**
> not so.



Configure firestarter correctly.

1+

---

### Post by bodhi.zazen on 2009-04-24
> **riskyayush said:**
> Hi, 
I recently installed Firestarter. I ran through the setup wizard and did exactly as I was told to. 
Now when I try and check the status of my computers ports through Shields Up, it shows that my following ports are opened:
SSH
HTTPS
HTTP.

I am assuming these ports, if open, are very dangerous. So please suggest how to close these ports.
Thank you

There is no way of answering your questions without knowing a lot more information.

first, do you use a router ? Of so, ShieldsUp is scanning your router and not your box.

second, what services are you running ? If you are running apache, it is normal for port 80 to be open. If you are not running a web server port 80 should not be open. Same for you other ports.

last, what is you are expecting a fire wall to do for your ? show closed ports on Shields up ? Or something else like limit connections in some way ? How ?

Also although Firestarter is often advised, it is quite out dated. Ubuntu now uses ufw, gufw if you want a gui tool.

---

### Post by riskyayush on 2009-04-24
Well, if I use my machine to connect to the internet through my university I have those ports open, but if I use my home connection those ports go into stealth mode. I am guessing that at home, my router masks my IP address and hence all the ports show up in stealth mode.

All I am worried about is with these ports open can be dangerous or not.

> 
Originally posted by **dburnett77**

Open the Firestarter GUI, select the last tab on the right..."Policy".
Then in the drop-down menu, select "Outbound Policy..."
"Restrictive" allows only the ports you want, "Permissive" will deny the ports you specify.
There's a drop down menu there with some of the ports that can access the most resources.  Try that. 

once I add those ports firestarter prevents me from opening any website.

---

### Post by Stupendoussteve on 2009-04-24
> **riskyayush said:**
> Well, if I use my machine to connect to the internet through my university I have those ports open, but if I use my home connection those ports go into stealth mode. I am guessing that at home, my router masks my IP address and hence all the ports show up in stealth mode.

All I am worried about is with these ports open can be dangerous or not.

once I add those ports firestarter prevents me from opening any website.

If you only see the ports open at the university, they are probably running SSH and HTTP/HTTPS. It is scanning their router/nat/forwarded machine, not yours.

At home if you run a router, point a DMZ at your Ubuntu box, then you can scan it instead of the router.

---

### Post by riskyayush on 2009-04-24
> 
Originally posted by Stupendoussteve

If you only see the ports open at the university, they are probably running SSH and HTTP/HTTPS. It is scanning their router/nat/forwarded machine, not yours.

At home if you run a router, point a DMZ at your Ubuntu box, then you can scan it instead of the router.     
I am sorry if it sounds amateurish, but how do I point a DMZ to my machine?

---

### Post by cariboo on 2009-04-24
You have to go into the management interface of your router, to enable a DMZ. Depending on what make of router you have, you can try:

[list]
[*]192.168.1.1
[*]192.168.0.1
[*]192.168.2.0
[/list]

---

