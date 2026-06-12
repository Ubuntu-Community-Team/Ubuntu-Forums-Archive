---
title: "LAMP is Broken"
date: 2014-01-25
forum: Server Platforms
---

### Post by cessanfrancisco on 2014-01-25
Hi,

I have LAMP set up on my Ubuntu 13.10 computer.  All was working fine; I was able to open PHP files, etc.  Then I decided to start messing around with Ruby on Rails.  I "activated" (for lack of a better term) the rails server and was able to access the app framework on my local server using:

localhost:3000

Now I can't seem to access my PHP files anymore.

Any ideas how I can make things go back to where I could just type "localhost" into my browser and my PHP directories would show up?

Thanks.

---

### Post by tfrue on 2014-01-25
I would bet that the apache config file is using port 80, so when you connect to your localhost, your are connecting to port 3000 rather than 80. I would try and type this in the URL:

[http://localhost:80](http://localhost:80)

See if that will bring your stuff back

If not, then I would go back and change local host to its default, which I think is 80.

---

### Post by cessanfrancisco on 2014-01-25
Thanks.

How to I change the local host default back to 80?  I looked in the apache2.conf file and didn't see anything to change.

---

### Post by tfrue on 2014-01-27
Post the output of:
```
cat /etc/hosts
```
That will be the file you will probably chage, but let's look at that file first and make sure we're going to do what we really want to do.

---

