---
title: "From Webmin to LAMP"
date: 2008-12-29
forum: Server Platforms
---

### Post by Stumbler on 2008-12-29
Please be gentle, I'm new. ;)

I have a basically configured 8.04.1LTS server in a remote data center with Webmin correctly installed. Essecntially, you can say that I have SSH and Webmin access.

How would I be best advised to go about installing [L]AMP from here with a view to all future configuration being conducted in webmin. Should I work through webmin or work from apt until the platform is fully installed?

Can anyone recommend a procedure?

I hope someone sees where I'm coming from and can help.):P

---

### Post by volkswagner on 2008-12-29
There are too many how-to's to list.

Check out [howtoforge]("http://www.howtoforge.com/trip_search") for many great ones.  Read the list and use the one that best meets your needs.

Best of luck.

Oh, use ssh and aptitude to do the entire setup.

---

### Post by Iowan on 2008-12-29
Consider PHPMyAdmin for working with MySQL.

---

### Post by cariboo on 2008-12-29
Seeing as you have already setup your server, ssh in and at the propmt type:

```
sudo tasksel
```

Select LAMP from the list and install. You should be able to configure the rest from webmin.

JIm

---

### Post by Stumbler on 2008-12-30
Thanks for the advice.

I shall venture forth and see where I get.

---

