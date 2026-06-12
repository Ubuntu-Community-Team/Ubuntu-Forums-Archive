---
title: "Tomcat Autostart (init.d?)"
date: 2006-06-11
forum: Server Platforms
---

### Post by boomerzz on 2006-06-11
I'm running 6.06 Desktop (64 bit) with a Pentium D.

It installed with no problems.  I set up tomcat 5.5 and the 1.5.0 jdk (07) with no problems they both work.  (in the /opt directory)

I can't seem to get tomcat to startup when the box boots.  I have tried a couple different scripts in the /etc/init.d directory, both worked fine if I ran them via shell and started tomcat.  (as root)

These required a start / stop argument etc...

What else do I have to do to make it run those?  Is there somewhere it would dump to a log if it ran those and failed?  Does is automatically pass the start / stop argument to these scripts?

---

### Post by boomerzz on 2006-06-11
I solved this by running this as root.

update-rc.d tomcat start 91 2 3 4 5  . stop 20 0 1 6 .

Thanks!

---

