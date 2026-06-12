---
title: "install simultaneously php4 and php5 ??"
date: 2005-11-01
forum: Server Platforms
---

### Post by CHUCKYCHUCK on 2005-11-01
hi ! i'm using breezy, i plan to install the server packages soon, and i'd like to know how i can have php4 and 5 running simultaneously ?  ( php4 as a module and php5 as a cgi )
.php would be run by php4
.php5 by php5

to install php4, i just have to install libapachemodphp4 and the dependencies of course, but for php5, i have to install php5-cgi, but then how do i configure apache2 so that it uses php5 for .php5 files ???

thx

---

### Post by Glut on 2005-11-01
>  how do i configure apache2 so that it uses php5 for .php5 files ???

Rather than rewrite the wheel: [http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)
replace .pl or .cgi with .php5
This, of course assumes that you've got your php5 enviornment down pat.

---

