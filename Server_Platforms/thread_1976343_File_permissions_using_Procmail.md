---
title: "File permissions using Procmail"
date: 2012-05-08
forum: Server Platforms
---

### Post by daj_uk on 2012-05-08
Hi,

I'm using procmail to produce a file for each email a specific user receives.  I've created the necessary file in the home folder and everything is work as expected -- it produces files in /home/<user>/Maildir/new

I actually what to read these using PHP but the file permissions default to -rw------ for each new file so I can not access them. 

How do I change the default permissions?

I did some reading on the sticky user permissions i change some settings with 'setfacl'.  When I run 'getfacl' against the 'new' folder I am told 

user:: rwx
group:: r--
other: r--

Which seems correct, but new files are still getting -rw-------

Any thoughts?

many thanks

---

