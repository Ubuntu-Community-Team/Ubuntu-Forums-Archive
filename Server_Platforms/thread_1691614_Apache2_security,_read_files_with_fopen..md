---
title: "Apache2 security, read files with fopen."
date: 2011-02-20
forum: Server Platforms
---

### Post by artheus on 2011-02-20
Hey!

I've been searching the forums for this matter, but can't seem to find anyone that has been posting for this.. Might be because I don't know the name of the security hole.

I was thinking about starting a web hosting service. But the thing is that if I start that using apache2 and php, the clients using my webhosting service might be able to browse my server with php script and fopen files, and read stuff like my passwords or other clients passwords and stuff.

How can I prevent them from being able to do this?

Is it possible to chroot the apache2-php scripts to the virtual host directory?

Cheers,
Artheus

---

### Post by rudelgurke on 2011-02-20
Suexec + FastCGI offers what you're looking for. Seperated PHP users for each Vhost + PHP settings allow some nice seperation that one Vhost can't access the file of another one and vise versa.

---

### Post by James78 on 2011-02-21
To add to what rudel said, since his solution would allow you to use a php.ini (or PHP configuration) per virtualhost, you could use that advantage to set PHP open_basedir restrictions for the virtualhost. An example would be..
```
open_basedir = /home/user/:/home/user/public_html/:/home/user/tmp/:/tmp/:/usr/lib/php5/:/usr/share/php/:/usr/bin/
```(If you're worried security wise about me including /usr/bin/ in here, you should realize that disable_functions should already be set to disallow all/most PHP execute functions, that way there's no security hole in the first place. It's not like I can't build my own binary virus, upload it to my public_html folder, and call it from a PHP script right?; so security would already have been compromised unless you disabled the functions in the first place. /usr/bin/ is in there in the first place to allow things like imagemagick to be used by PHP scripts, for example, to allow image thumbnails, as in phpBB)

---

