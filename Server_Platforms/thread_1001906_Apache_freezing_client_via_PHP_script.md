---
title: "Apache freezing client via PHP script"
date: 2008-12-04
forum: Server Platforms
---

### Post by ofosho on 2008-12-04
Hello everyone,

I have a page that I am creating that is essentially a terminal over the web. It is actually working fine on my ubuntu 8.04 laptop running apache2.2.8 and PHP5.2.4, however when I run the code on my 8.10 desktop running apache2.2.9 and PHP5.2.6 firefox keeps locking up. 

The way the PHP code works is that when called to do a read it continually checks the serial port until it finds data. Then it echos the data and closes. I am using prototype.js to execute an ajax command that waits until it receives data to continue (onComplete). 

The only thing I can think of is that the new apache is not sending something that prototype needs in order not to crash during a long wait?

Any suggestions? 

I have attached the dumps from phpinfo from both my laptop and desktop.

---

### Post by Dr Small on 2008-12-04
Sounds like an error in your script, and the loop is never ending.

---

### Post by ofosho on 2008-12-04
No, the code runs fine on my laptop. The issue is coming from some difference between server/php versions. 

The PHP script is supposed to be never ending, but will always timeout based on the php timeout variable.

The javascript is also ends indefinitley based on the PHP, however, when the PHP ends, so will the javascript, as the javascript just waits for a reply. 

The issue I think, must come while the javascript is waiting for something from the PHP. During that time, something is different between apache versions, but I don't know what.

Also the page isn't completley frozen. It goes grey, but comes back every now and again, probably once the PHP times out. and before the next loop starts.

---

