---
title: "test Server"
date: 2005-11-27
forum: Server Platforms
---

### Post by Insane on 2005-11-27
I want to use Ubuntu as a desktop OS, however, there are things like php scripts etc which I would like to test and run on localhost.

So, I was wondering, assuming i have installed the Apach 2 package from the Synaptic thing, and it is running, and I know where my ww directory is....but how do I access my www directory through my web browser. on XP i used a thing called WAMP server, and in my web browser i could type Localhost, but not on ubuntu...so, cna someone please tell me?

I dont want to use it as a hosting server, just to test my own php and MySQL aplications.

---

### Post by Joey French on 2005-11-27
So, you're saying you can't type "localhost" in a browser and see your server? How about 127.0.0.1? If you can't see your server with these, it might not be running. Try this:
```
sudo apache2ctl start
```
This should start the server, but if you just installed it via Synaptic, it should be running and showing the default Apache "install successful" page. To stop the server:
```
sudo apache2ctl stop
```
Hoep that helps!

---

### Post by Insane on 2005-11-27
No.....still can't...

But I can access it like this...file:///var/www/apache2-default/index.html.en

not exactly what I need.

---

### Post by simon.schmidt on 2005-11-27
[QUOTE=Insane]No.....still can't...

But I can access it like this...file:///var/www/apache2-default/index.html.en

not exactly what I need.[/QUOTE]
when you acces like that you bypass apache...

do you get any error messeges when starting apache?
have you looked in /var/log/apache2/error.log? show us the output of:
tail /var/log/apache2/error.log

---

### Post by Insane on 2005-11-27
ok, nevermind. I just restarted my computer...now it works! YAY!

Now i only have to figure out how to get phpmyadmin installed so i can access it through the browser aswell...

---

### Post by Joey French on 2005-11-27
Cool. Good luck!

---

### Post by Spudgun on 2005-11-27
[QUOTE=Insane]ok, nevermind. I just restarted my computer...now it works! YAY!

Now i only have to figure out how to get phpmyadmin installed so i can access it through the browser aswell...[/QUOTE]

I just installed it through apt-get, worked for me.

---

