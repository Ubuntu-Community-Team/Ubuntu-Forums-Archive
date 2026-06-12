---
title: "Please could developers correct the bug with libsvga1 and Xwrapper.config"
date: 2006-12-26
forum: Repositories &amp; Backports
---

### Post by patrick295767 on 2006-12-26
Hi, 

A bug was introduced in Dapper, and remained even after bug reports. 
Please could you have a look at the libsvga1 and Xwrapper.config
(first, sudo apt-get -f -y install zgv )
 
1/ Plz go into /dev/tty1, login as normal user, then type :
```
 xinit -- :2      ## not working, the bug is still there with Dapper & Edgy
```
    
2/ Plz go into /dev/tty1, login as normal user, then type :
```
dir *.jpg ## not working, the bug is still there with Dapper & Edgy
zgv  *.jpg
```
 
3/ Plz go into /dev/tty1, login as normal user, and try to start a video with vga libs with mplayer
and this will not work either
 
  
  
Thank you for your concern & help !

Patrick

---

