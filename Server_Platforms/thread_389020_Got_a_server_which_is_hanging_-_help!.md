---
title: "Got a server which is hanging - help!"
date: 2007-03-20
forum: Server Platforms
---

### Post by jpdrawneek on 2007-03-20
I got a box running ubuntu server (not sure which one 10/06 or 06/06)

Every so often it just stops, its still powered on but has locked up.

Theres nothing in the general logs so i am confused on whats causing it.

Are there any more detail ways of grabbing whats going on?

---

### Post by gepatino on 2007-03-20
It could be some hardware related issue. Try runing memtest86 and check if it shows some errors, it could take several hours.

Other reason could be that your server ir really busy. Once I had a similar problem in a mail server, and the problem was a user sending a 200Mb attach to some 100 different adrresses... the server was almost dead but responding (if you had patience).

---

### Post by jpdrawneek on 2007-03-20
Is there any way to test things like memory across the net, as the box is a long long away from us :( 

I don't think its load - how long was your box down for? a day?

Ours has been for a day at a time, takes while for it to get reset.

In that time there is nothing written to the logs, no process seen to happen - the box stops working!

---

### Post by gepatino on 2007-03-20
I don't know of any remote memory check tool.

In the case of our mail server, it took several hours, maybe all night, since the big mail was send at night and i only realized the following morning. In this case the logs didn't show anything special since the server was doing what it's supposed to do: send mails. 

Maybe you have some resource hungry process that runs periodically. Check what you have in your crontabs, are you runing any admin scripts on some big database, etc

---

### Post by jpdrawneek on 2007-03-20
The box is not doing alot

Its running vmware server with 3 virtual machines in it.
Its got enough stick to not make that a problem.

The virtual zones are only doing light work - games servers - web

Theres nothing huge going on.

Things like mail you would notice that theres a lot of web traffics going on, our box does nothing when its down.

Theres nothing in crontab - theres no huge db - theres nothing really running

Thats why we confused, it seems to be dieing for no reason :confused: 

Are there any monitoring tools we can put on the box to get a better idea on whats going on?

---

### Post by gepatino on 2007-03-20
> **jpdrawneek said:**
> The box is not doing alot

Its running vmware server with 3 virtual machines in it.
Its got enough stick to not make that a problem.

The virtual zones are only doing light work - games servers - web

Theres nothing huge going on.


try disabling one of those virtual zones at a time, maybe some of them is turning your server down

> 
Thats why we confused, it seems to be dieing for no reason :confused: 


well... if you are **sure** there is no hw problems, it must be doing something.

> 
Are there any monitoring tools we can put on the box to get a better idea on whats going on?

you can use top and free from the console. for something more elaborated, you could use mrtg to monitor the system, generate graphs, etc. I never used mrtg but you should be able to find a lot of info in the web.

---

### Post by jpdrawneek on 2007-03-20
> **gepatino said:**
> try disabling one of those virtual zones at a time, maybe some of them is turning your server down

Not a chance, the amount of time between these hangs is months, so to try this method would take a year.

> **gepatino said:**
> 
well... if you are **sure** there is no hw problems, it must be doing something.

Never said i was sure - just asked how to test the hardware when its on the other end of the country from you :) 

> **gepatino said:**
> 
you can use top and free from the console.

Sounds pointless - you can't see top result when it cashes

> **gepatino said:**
> 
 for something more elaborated, you could use mrtg to monitor the system, generate graphs, etc. I never used mrtg but you should be able to find a lot of info in the web.

Will look into this

---

