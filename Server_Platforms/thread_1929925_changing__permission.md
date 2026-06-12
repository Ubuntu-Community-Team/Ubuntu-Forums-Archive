---
title: "changing  permission"
date: 2012-02-22
forum: Server Platforms
---

### Post by magpie03 on 2012-02-22
Hello all.
I have setup a Ubuntu 11.0 server at home. I get the default "It Works" web page. Using Webmin I can edit the page. Now I want to rename the default index.html to index.bak. Using Ubuntu 10.10, from the menu-places-connect to server, I select SSH. Put in user name and password and I get a nice GUI showing my files. When I go to rename I get "You do not have the permissions to rename."

So far I have tried this:

sudo addgroup webmasters
sudo gpasswd --add mikiee webmasters
sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

My /var/www/ permissions are as follows:

drwxrwsr-x  2 root root  4096 2012-02-22 14:16 www

What am I doing wrong?

Thanks all....
magpie

---

### Post by hawkmage on 2012-02-22
It looks like the directory /var/www is still owned by the user root and the group root  and not webmasters so with the directory having owner and group write you will either have to do the rename as the root user or be in the root group.

---

### Post by magpie03 on 2012-02-22
Thanks hawkmage. Can I add/should I ad me to root? Or can I ssh in as root just to update files?
Thanks again...
magpie

---

### Post by hawkmage on 2012-02-22
Since you created the group webmasters I would think that you may want to set the group ownership of the directory to webmasters.

---

### Post by magpie03 on 2012-02-24
Got it. Thanks hawkmage. Guess I had to reboot after running the change group command. Thanks again...
magpie

---

