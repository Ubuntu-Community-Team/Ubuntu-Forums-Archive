---
title: "Apache: AllowOverride All in one public_html directory"
date: 2009-10-27
forum: Server Platforms
---

### Post by ola on 2009-10-27
Hi,

Is it possible to set Apache to *AllowOverride All* for one of my users *public_html* directory but not the others?

Thanks in advance!

---

### Post by Lars Noodén on 2009-10-28
Have you tried using <Location> or <Directory> further down in the vhost configuration file to set something different for just that directory?

---

### Post by ola on 2009-10-29
I tried to install CakePHP to my public_html directory but I couldn't get it to work so I set up a virtual domain instead...

---

