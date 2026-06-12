---
title: "[SOLVED] Simple Web Server on PC"
date: 2008-12-07
forum: Server Platforms
---

### Post by unckybob on 2008-12-07
I'd like to make a simple web server to run on an older PC. I've looked around for how to do this and it seems somewhat involved. I'd like to just have something that I can copy some HTML into, give people a URL and they can access my website over the internet. Help!

---

### Post by hictio on 2008-12-07
How old is that box?
Have you tried installing Ubuntu Server on it?
Perhaps this thread has to/ will be moved to the [Server Platform forum](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=339)?

---

### Post by unckybob on 2008-12-07
It's an HP Pavilion 4550Z bought in 2000. I've got Ubuntu running on it fine. 

I was hoping it would be possible to use as a PC and a web server. 

I thought I'd try the thread on this forum first. I'm thinking that the Server Platform forum is just for people using Ubuntu server.

---

### Post by unckybob on 2008-12-07
?

---

### Post by sloggerkhan on 2008-12-07
Just install apache, and put a document in you var/www folder. You can then access it at your computer's IP, if you change the apache config to use a particular port, then ip:port, and if you want webaccess with a non-ip address, [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/) .

It's really not all that hard.

---

### Post by unckybob on 2008-12-07
I assume I can just put a index.html file in the directory you mentioned. So the URL would be something like: 

[www.(myipaddress)/index.html](www.(myipaddress)/index.html) 

or 

[www.(myipaddress).com](www.(myipaddress).com) 

?

---

### Post by hictio on 2008-12-07
> **unckybob said:**
> It's an HP Pavilion 4550Z bought in 2000. I've got Ubuntu running on it fine. 

I was hoping it would be possible to use as a PC and a web server. 

I thought I'd try the thread on this forum first. I'm thinking that the Server Platform forum is just for people using Ubuntu server.

Oh, I didn't understood on your post that it was for the same box. Then, if Apache alone, type this on a Terminal (on a box already connected to internet :D )

```

sudo aptitude install apache2 (ENTER)

```

Take a look at this page, for more options: [Apache MySQL PHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


> 
I assume I can just put a index.html file in the directory you mentioned. So the URL would be something like: 

[www.(myipaddress)/index.html](www.(myipaddress)/index.html) 

or 

[www.(myipaddress).com](www.(myipaddress).com) 


Yes, as long as you are forwarding the port 80 from your router (if any) to the IP of your Ubuntu box; and the port 80 is open by your ISP.
You can also register a domain with [www.dyndns.com](www.dyndns.com), it's free, so you don't have to keep track of your IP address, if itsn't static and it changes, and also, you can give a URL instead of an IP address to access your site.

---

### Post by brandon90c on 2008-12-07
> **unckybob said:**
> I assume I can just put a index.html file in the directory you mentioned. So the URL would be something like: 

[www.(myipaddress)/index.html](www.(myipaddress)/index.html) 

or 

[www.(myipaddress).com](www.(myipaddress).com) 

?

It would actually just be [<youripaddress>/index.html](<youripaddress>/index.html).

[www.<youripaddress>/index.html](www.<youripaddress>/index.html) might work. I'm not sure. It would also be [localhost/index.html](localhost/index.html) and [127.0.0.1/index.html](127.0.0.1/index.html) on the computer you have installed apache on.

---

### Post by unckybob on 2008-12-07
Thanks. After looking your website over it looks like it will be pretty easy!!

---

### Post by marshall.robert on 2008-12-07
please ignore, for some reason the system told me there where no replies...

---

### Post by Grey08 on 2009-03-10
why the /var/www/index.html says i m not the owner?? what do i do to edit or add files in this folder??

---

### Post by sloggerkhan on 2009-03-11
I like to make a web-edit group and give it permissions over a folder in varwww but you can always use sudo.

---

