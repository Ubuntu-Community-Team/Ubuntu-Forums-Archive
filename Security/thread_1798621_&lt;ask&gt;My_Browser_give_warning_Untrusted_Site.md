---
title: "&lt;ask&gt;My Browser give warning Untrusted Site"
date: 2011-07-06
forum: Security
---

### Post by Matadewa on 2011-07-06
hai all i have trouble with my browser
i used 2 browser in my ubuntu 4.0 & opera 10.63. . .
  since a few days ago, i feel my firefox being hacked because when i try to login in popular site such as facebook,yahoo or gmail. . .firefox give warning if that site untrusted although i already type their url by myself 
this is the screenshot when i try login to yahoo
   [http://imageshack.us/photo/my-images/200/bug2ew.png/](http://imageshack.us/photo/my-images/200/bug2ew.png/) 
and in firefox history menu it's display old history if i want to see new history i must do it by history -> show all history -> today
my opera give warning untrusted site too, but it's more worse if my firefox just display waning message when i try to login my opera display it every time the page is load ( normal browsing, not login)  
this is screenshot opera warning
[http://imageshack.us/photo/my-images/35/bug1s.png/](http://imageshack.us/photo/my-images/35/bug1s.png/)
i wonder how to back it to normal again because i already try to uninstall it by type sudo apt-get --purge remove opera and install again but give no effect any help really appreciate ^^

---

### Post by emiller12345 on 2011-07-06
if your receiving an invalid cert warning, if you can look to see if you can determine why its invalid.  Many programs require that the computers clock be set exactly.  In the past I've run into the situation where I went to go look at the computer calender and accidentally changed the time by + or - a year and it was reading the certs as invalid when they weren't.

If that's not the case it might be a routing error or MITM attack.

---

### Post by Tactical Fart on 2011-07-06
Try logging in from another computer. 

Hey guys, would the WOT FireFox extension help the OP?

Edit: didn't think about MITM. Ugh...

---

### Post by CharlesA on 2011-07-07
Check the date/time on your PC.

---

