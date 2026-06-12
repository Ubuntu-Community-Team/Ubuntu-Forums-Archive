---
title: "snort logs"
date: 2005-11-08
forum: Server Platforms
---

### Post by HJThis on 2005-11-08
Hi,To all

Anyone know of a GUI or a prog i can use to look at the
snort logs,better yet is there something i can use so just
the output of the logfile will show.

what i am asking is so there is no need to look at
a 1000 logfiles all day need something that would
popup on the screen.

Thank you :???:

---

### Post by Jussi Kukkonen on 2005-11-09
Well, once you have the rules you want to use ready, you have several output options from snort: 
* write to log file or database
* send output to a unix socket
* send a winpopup message through SMB
* probably others...

The reason they're all so primitive is speed -- you don't want to do anything resource intensive on every snort logging event...

What you should probably do is log to a file, and set up another program to periodically do stuff with that file. Maybe this helps: [http://www.snort.org/docs/faq/1Q05/node94.html](http://www.snort.org/docs/faq/1Q05/node94.html) .

---

### Post by ubernoob on 2005-11-18
You are probably looking for BASE or ACID. ACID hasn't been updated in years.  BASE is based on the code from ACID. 

[http://secureideas.sourceforge.net/]("http://secureideas.sourceforge.net/")

I'm not sure how you should install it on ubuntu, but tell me if you find a good howto.

This guide from gentoo might give you some hints if you want to do it by yourself.
[http://gentoo-wiki.com/HOWTO_Setup_BASE_with_Apache,_Snort,_and_PostgreSQL]("http://gentoo-wiki.com/HOWTO_Setup_BASE_with_Apache,_Snort,_and_PostgreSQL")

---

### Post by HJThis on 2005-11-18
Hi,ubernoob

I thank you for the time & help this maybe just what i
was looking for.

BOL ;)

---

