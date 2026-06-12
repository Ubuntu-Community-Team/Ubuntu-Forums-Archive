---
title: "Virtualmin on 13.04 server?"
date: 2013-08-17
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-08-17
I've already got Webmin installed successfully and in theory, Virtualmin should work with 13.04 OK, despite that version of Ubuntu not being one of the Grade A or B systems they list here - [http://www.virtualmin.com/os-susupports](http://www.virtualmin.com/os-susupports) 

Has anyone installed it successfully on 13.04, and if so, are there any particular tips you might offer?

---

### Post by Chris of Arabia on 2013-08-17
I think we can call this one closed - I followed this guide, plus a number of the comments on it to get the installation working - [http://patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524](http://patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524)

The main points I picked up along the way were:

1. Virtualmin needed an update from here: [http://www.webmin.com/updates/apache-1.640-2.wbm.gz](http://www.webmin.com/updates/apache-1.640-2.wbm.gz)

2. /etc/apache2/mods-enabled/php5.conf needed its SetHandler lines commenting out - see here: [http://www.virtualmin.com/node/20646#comment-93488](http://www.virtualmin.com/node/20646#comment-93488)

3. Webmin needed its default 'Global Theme (Grey Framed Theme)' changing to any of the other options (I went with the Blue Framed Theme)

All now looks good and I should be able to start setting things up.

---

