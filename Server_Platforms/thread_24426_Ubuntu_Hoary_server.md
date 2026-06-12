---
title: "Ubuntu Hoary server"
date: 2005-04-06
forum: Server Platforms
---

### Post by somuchfortheafter on 2005-04-06
Ok well I have Hoary installed with the following
Apache2
Proftpd
and ssh for remote access
also i have an external hard drive "/dev/sda1" which is set to be the director /storage.  In the storage directory I would like it that all of my ftp traffic would enter there and then if lets say i created the somuchfortheafter directory there and put in an index.html file via ftp, i could then go to http://so.muc.h's.ip/somuchfortheafter/ then when i hit enter I would see the site. Alas I have never ran a server and have no idea how to configure what I am asking. I have been reading the  man pages and the .conf that each program has and I still seem to be lost. So can anyone help please lol. Also I already have my router setup to accept incomming traffic to that pc for http and ftp requests.

---

### Post by somuchfortheafter on 2005-04-06
ok well i semi fixed it by running 
```

ln -s /storage/thanatosys /var/www/apache2-default/thanatosys

```
incase everyone is wondering yes I do want the site to be in the thanatosys directory.
however getting ftp access to it is still a bother.... any ideas?

---

### Post by dataw0lf on 2005-04-06
Take a look at this [site.](http://www.proftpd.org/docs/directives/linked/by-name.html)   This defines various .conf directives. Although I haven't setup a Proftpd server before, you're probably going to have to set your DefaultChdir .  As for accessing said directory from the web, off the top of my head I'd suggest a ln to the 
ftp directory, located inside your DocumentRoot.

---

### Post by HungSquirrel on 2005-04-06
Glad you figured out the solution.  Alternatively, if you aren't worried about tildes (~) being in URLs and you don't absolutely need this stuff on /storage, Apache is set up by default to load the contents of /home/whoever/public_html at [http://you.com/~whoever/](http://you.com/~whoever/) .

---

### Post by somuchfortheafter on 2005-04-07
no i wanted it on /storage because that is my storage section lol, see it only has a 6bg hard drive and the /storage is a 20gb external drive. I still am trying to get ftp to work but ehh ill get it sometime

---

