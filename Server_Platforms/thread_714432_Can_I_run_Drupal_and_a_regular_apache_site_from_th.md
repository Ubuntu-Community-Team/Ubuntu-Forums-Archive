---
title: "Can I run Drupal and a regular apache site from the same box?"
date: 2008-03-03
forum: Server Platforms
---

### Post by uberlinux on 2008-03-03
Like the subject says, I'm trying to figure out if I can keep my regular http website up while installing and serving a Drupal site.  Is anyone else doing this?  I'd really like to be able to do both on the same box.  The goal is to host a slew of sites both regular Apache and Drupal.  

Thanks everyone!

---

### Post by dmizer on 2008-03-04
i'm not sure exactly what you mean, but i think i have a pretty good idea.  you want to point several website addresses to your apache server.

mainsite.com
drupalsite.com
someothersite.com

for this, you need to configure apache for virtual hosts.  here is a good howto for enabling virtual hosting: [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

you can configure as many sites as you like this way.  however, the more traffic your server handles, the more beefy it will have to be both in cpu clock cycles as well as with memory.  also, for drupal, you will need to install and configure both mysql and php.

as a final note, i'm not positive but the way your question is written, you seem to be confused as to the actual function of drupal.  drupal is a cms (content managment system).  it's purpose is to allow the creation and editing of a website content and layout without having to manually manipulate the html and php code.  it does not perform the same function as apache.  apache is the actual html server software on which both non-drupal and drupal websites depend for rendering a website.

if i've made this judgment in error, i apologize.

---

### Post by ctyc on 2008-03-04
yes

---

### Post by uberlinux on 2008-03-04
I just wanted to make sure that if I installed Drupal onto a server already running Apache2, that it wouldn't stomp all over my existing Apache settings and my existing HTML content being served.  I'll try the install again, but it was threatening to redo some Apache configs and restart the Apache2 service, so I just wanted to be sure my existing site would remain intact.  I'll be using another virtual host for this Drupal powered site.  Hopefully my server is up to the extra load.  It was built to be as lean on energy consumption as possible since apache doesn't need much, so we'll see.

---

### Post by vpsville on 2008-03-04
Yes you can. Drupal shouldn't interfere with virtual host settings.

---

### Post by uberlinux on 2008-03-04
Cool, thanks much, guys.  Now I just have to figure out what to set up on the virtual hosts config file.

---

