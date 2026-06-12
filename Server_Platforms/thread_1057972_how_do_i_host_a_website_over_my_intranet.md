---
title: "how do i host a website over my intranet?"
date: 2009-02-02
forum: Server Platforms
---

### Post by Meow27 on 2009-02-02
im trying to make a homepage server over my network. im having trouble with this because i dont know how to either apache php or sql. i have a website ready, bu i dont know what to do with it in order to get it hosted

additionally, im trying to do this on ubuntu intrepid desktop as i want to run nagios on the same PC (im not sure if i should be running Virtual machines for these separately or in the same environment simotaniously) (sorry for my bad spelling)

if im not clear enough id be glad to elaborate

thanks in advance
-meow

---

### Post by lykwydchykyn on 2009-02-02
Does your web site even use PHP or a database?  Or is it just plain HTML files?

You should be able to run nagios and a web server on the same machine just fine, virtualizing will just slow everything down needlessly.

---

### Post by Meow27 on 2009-02-02
no. its just a bunch of html files (with images if that helps :S)

---

### Post by tomwerner470 on 2009-02-02
If it is just HTML pages, install Apache 2 by running in a terminal:
```
sudo apt-get install apache2
```

Once that is installed you can copy your files in to /var/www and point your browser to [http://127.0.0.1](http://127.0.0.1). 

If you want to edit the location where these files are stored, you will need to change the Document root in the file:
```
/etc/apache2/sites-enabled/000-default
```

Hopefully it is as quick and simple as that...

**EDIT:** Depending on how you are installing Nagios, apache2 may be installed as a dependancy automatically, in that case all you may need to find out is where the DocumentRoot for / has been changed to (if at all).

Regards,

Tom

---

### Post by Meow27 on 2009-02-02
thanks, but this method only works for the computer that is hosting this. im trying to get EVERY computer over my network to be able to view my webpage

---

### Post by f37u5g0d on 2009-02-02
When you are on another computer put in the ip address of the computer with the website on it into the browser.

[http://192.168.x.x](http://192.168.x.x) 

Or whatever your ip scheme is.

---

### Post by Meow27 on 2009-02-03
i havent tried this on another computer yet, but in the case where im using another computer on the same ip address (including the computer which i am hosting from) 

is it supposed to work?

---

### Post by Meow27 on 2009-02-03
ok i tried it and i think it working!

thanks for everyone who commented ^^

(will mark as solved once im done with it completely)

---

### Post by Iowan on 2009-02-03
> **Meow27 said:**
> (will mark as solved once im done with it completely)
Not until "they" re-enable the [SOLVED] feature. ;)

---

