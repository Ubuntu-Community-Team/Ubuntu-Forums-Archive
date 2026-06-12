---
title: "Webmin on Ubuntu"
date: 2011-01-15
forum: Server Platforms
---

### Post by haydenh on 2011-01-15
I've installed Webmin before on Ubuntu with no problems. However, I started from scratch and now I am getting errors.

I've got Ubuntu 10.04 LTS install along with LAMP + phpMyAdmin

I downloaded Webmin fine to my server. Trying to install it I get dependency errors. I install each dependency with apt-get install and the rerun the install of Webmin. It then lists the exact same dependencies that I just installed! It's a never ending loop it seems and I can't get Webmin installed. Can anyone please help me with this?

---

### Post by haydenh on 2011-01-15
I seem to have solved this issue. I had to run the following commands:

```
apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl
```

then for dependencies

```
 apt-get install libnet-ssleay-perl libauthen-pam-perl libio-pty-perl apt-show-versions
```

---

### Post by RobbanC on 2011-01-16
Good you solved it! Webmin is a great thing.

Just for the record... I installed webmin like this.

First download the installation file, of course, then install it with:
```

sudo dpkg -i webmin-current.deb

```
This will kind off install webmin, but set the needed dependencies. So now you can simply install the needed/waiting dependencies with:
```

sudo apt-get -f install

```

That's it. Webmin is up and running. :)
(Should work also for 10.04)

---

### Post by SwellJoe on 2011-01-16
You could also enable the Webmin.com apt repository, and then use apt-get to install Webmin which would allow apt to satisfy all dependencies for you. Setting up the apt repo is documented on the Webmin site.

---

