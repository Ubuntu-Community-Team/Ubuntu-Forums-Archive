---
title: "Run command from http"
date: 2008-12-08
forum: Security
---

### Post by phillips321 on 2008-12-08
Hi guys,

I have a script that I would like to be able to run remotely.

My phone will only allow me to use http so i cannot ssh into the box.

What i need to do is to be able to remotely run a sript using the http service presented by apache.

First of all how do i get apache to run a command on the box? What sort of http command would i use, i guess something along the lines of php etc..

Secondly i dont wish anyone else to be able to execute this so im thinking .htaccess is a good route, i was also considering restricting access to a range of IP address but my mobile phones IP always changes.

If you need to be able to securely execute a single script stored on the server using http how would you do it?

Cheers in advance

---

### Post by hyper_ch on 2008-12-09
the php exec() function is probably what you look for.

---

### Post by cdenley on 2008-12-09
I would be very cautious when doing this. Creating a php script would be easiest. However, a programming mistake may allow users to run ANY command, which would be very bad. Even if you require authentication, it's still a risk. Make sure you use encryption and a strong password.

---

### Post by smetj on 2009-02-15
Hi phillips321,

I think [http://www.smetj.net/wiki/Teleporter](http://www.smetj.net/wiki/Teleporter) is exactly what you're looking for.

Cheers,

Jelle

---

### Post by kevdog on 2009-02-15
Sorry misunderstood the question.

---

