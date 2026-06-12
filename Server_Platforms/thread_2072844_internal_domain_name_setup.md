---
title: "internal domain name setup"
date: 2012-10-18
forum: Server Platforms
---

### Post by spillage2 on 2012-10-18
Hi All,

Before I ask I will just let you know I am new to server setups for please forgive my possible daft question.

I have set up a server running on Vbox on my ubuntu desktop.

apache, php,msql and ssh are all up and running.

What I would like to do and I'm not sure if its possible is set up a running website but only on my network and not open to the www.

Am I able to set this up with any web address rather than the ip address so it can be accessed via the web browser.

i.e could I set it up [www.mywebsite.co.uk](www.mywebsite.co.uk) rather than 192.xxx.x.xx

I have spent hours looking for a simple answer but have come up with zilth.

cheers,

Spill.

---

### Post by Cheesemill on 2012-10-18
Yes you can.

The easiest way is to just add a line to the /etc/hosts file on the machine you wish to connect from, for example:
```
192.168.1.200   www.example.com    www
```
Obviously use the correct IP and name for your setup.

---

### Post by spillage2 on 2012-10-18
Thanks Cheesemill,

I have added this (ip address changed) but cannot access this via ff on my main comp. 

sure I'm missing something simple but can't see the trees for the wood.

do i need to setup my router for this or am I missing something on the server?

would using [www.example.host](www.example.host) work?

Spill.

---

### Post by Cheesemill on 2012-10-18
You did edit the file on your main computer and not the server didn't you?

Also you can use whatever name you want as long as you put it in the hosts file.

---

### Post by spillage2 on 2012-10-18
Doh

Thanks ever so much...see told you I was daft.

Spill.

---

