---
title: "Apache Default nice"
date: 2011-03-27
forum: Server Platforms
---

### Post by mmxbass on 2011-03-27
Is there a quick and easy way to make sure apache always starts with a certain nice value?

---

### Post by kihjin on 2011-03-27
The easiest way that I've found is editing /usr/sbin/apache2ctl directly

Find the line (line #100 here)

$HTTPD ${APACHE_ARGUMENTS} -k $ARGV

add nice to beginning

nice -n 5 $HTTPD ${APACHE_ARGUMENTS} -k $ARGV

You could probably make it flexible by adding a parameter to envvars, but it gets more complicated that way.

---

