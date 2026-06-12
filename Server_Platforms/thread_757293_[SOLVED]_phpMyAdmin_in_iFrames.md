---
title: "[SOLVED] phpMyAdmin in iFrames???"
date: 2008-04-16
forum: Server Platforms
---

### Post by lambono on 2008-04-16
Hi,
I would like to include phpMyAdmin in and iFrame in my site....

<iframe 
src ="http://localhost/phpmyadmin"
width="100%"
height="600px"
frameborder="0">
</iframe>

however when I open the page containing this frame I am automatically redirected to the full phpmyadmin page and asked for the database username details. 
Once logged in to phpmyadmin it will work fine in the iframe but as I said it jumps out of it if you were not previously logged in.

Any ideas how to stop this???

Thanks in advance for your help!!

---

### Post by maya75 on 2008-04-17
Hi lambono,

I had the same problem and took a look at the code. I changed some lines and it seems to work.
My version : phpmyadmin 2.9.1.1 (path :  /usr/share/phpmyadmin/ )

Open /usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php :

1) comment out the lines 94,95,96 :

[PHP]//if (top != self) {
//    window.top.location.href=location;
//}[/PHP]

2) In the line 160, change in the <form> tag :
[PHP]target="_top" by target="_self"[/PHP]

I just made the changes so maybe there'll be some glitches but so far it seems to work.

---

### Post by lambono on 2008-04-17
Great!
Thanks! That works a treat :)

---

