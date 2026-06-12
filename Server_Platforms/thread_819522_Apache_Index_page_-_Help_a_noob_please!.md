---
title: "Apache Index page - Help a noob please!"
date: 2008-06-05
forum: Server Platforms
---

### Post by rustic on 2008-06-05
I am running the typical LAMP build on my server.

I have installed and configured a delightfully useful CMS and all is well there.  

My question is how can I make my CMS show up on the root of my webserver in a browser?

Ex:  Currently when I go to http://<mydomain>> I get the apache page, however, my CMS populates to http://<mydomain>/<CMS>/

I want http://<mydomain>/<CMS>/ to = http://<mydomain>

I realize that I can do this with DNS (right?) but don't know how else to accomplish this.

Thanks,
rustic

---

### Post by Kolipoki on 2008-06-05
I would also like to know what rustic is asking, as I'll need to do that very soon. Thanks in advance for the help.

---

### Post by rustic on 2008-06-05
I am currently using an http redirect
```

<meta http-equiv="Refresh" content="0; URL="http://mydomain/subfolder/">

```

While it's NOT what I was aiming for, it does fall under the "just works" category of computing.  If you know of the more "professional" manner of pulling this off, please don't hesitate to let us know!

rustic

---

### Post by lsmobrian on 2008-06-05
I think thats an option in httpd.conf


There should be a variable docroot or serverroot or something similar.  it should probably be set to "var/www"

so then just change it to "var/www/CMS" and restart apache, hopefully that works

---

### Post by matthewboh on 2008-06-05
It's in /etc/apache2/sites-available/default 

It is the line labeled DocumentRoot

Also, I love Webmin for managing the server - makes life a little easier sometimes.  You can get it by typing

```
sudo apt-get update
sudo apt-get install webmin
```

and then you can get to it at [https://(yourdomain):10000](https://(yourdomain):10000)

and then you just select Servers | Apache Server | Virtual Address on * and at the bottom of the page is the Document Root folder.  Just change it there and save it and apply the changes

---

### Post by rustic on 2008-06-05
> **matthewboh said:**
> It's in /etc/apache2/sites-available/default 

It is the line labeled DocumentRoot

First off, thank you!  This is the thing I thought I knew was out there but was a bit confused about.  Duly noted in my "book of tricks".  Kudos!
> **matthewboh said:**
> 
Also, I love Webmin for managing the server - makes life a little easier sometimes.  You can get it by typing

```
sudo apt-get update
sudo apt-get install webmin
```

and then you can get to it at [https://(yourdomain):10000](https://(yourdomain):10000)

and then you just select Servers | Apache Server | Virtual Address on * and at the bottom of the page is the Document Root folder.  Just change it there and save it and apply the changes

I attempted to pull webmin and got the following:
```

Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

I will assume I don't have a required repository in my list at this point, but have also put this on my list of things to look into.

Thanks a lot.  I'll give one last reply once I have my DocumentRoot adjusted to suit my needs to report my success(!).

~rustic

---

### Post by rustic on 2008-06-05
Update:  edited /etc/apache2/sites-available/default 

all is well now.

Again, thank you SO much matthewboh.

---

