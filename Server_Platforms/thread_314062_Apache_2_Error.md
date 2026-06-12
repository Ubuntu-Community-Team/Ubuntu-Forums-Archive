---
title: "Apache 2 Error"
date: 2006-12-07
forum: Server Platforms
---

### Post by RMorris78 on 2006-12-07
I have already posted this in the beginner forum, but got no respose.  If you have noticed the double post, please excuse me.

Ok, i just downloaded apache2 through synaptic, i am using Xubuntu 6.06 LTS.

I just made a little sample HTML File to figure out how this whole thing works, because I am new to apache and i wanted to see how it would work.

I keep getting an error with apache. After trying to restart apache, it fails. So after reading another thread i found that i should run "sudo apache2 -X". I have the error from that and it is
Code:

Syntax error on line 25 of /etc/apache2/sites-enabled/index.html: Expected </br> but saw </h2>

so i thought i had my HTML wrong, but i checked it, changed it around, tried everything i know of, but i keep getting that error.

any ideas?

thanks alot, im new to this sorry!
if you want to see the HTML code im willing to paste it if it helps you

---

### Post by houstonbofh on 2006-12-07
Where did you put the html file?  It should be in /var/www/ but it looks like you have it in /etc/sites-enabled ?
Here is a roadmap.  Some places they hide stuff is non-intuitive.

[http://wiki.apache.org/httpd/Info/DistrosDefaultLayout](http://wiki.apache.org/httpd/Info/DistrosDefaultLayout)

---

### Post by RMorris78 on 2006-12-07
thats what i thought as well, but then i read something that said to put it in sites-enabled, so i put a copy in each.

thanks for the link though! i will take a look at it and get this all figured out

---

