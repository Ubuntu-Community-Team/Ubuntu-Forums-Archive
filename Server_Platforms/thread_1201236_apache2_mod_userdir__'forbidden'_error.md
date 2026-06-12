---
title: "apache2 mod_userdir  'forbidden' error"
date: 2009-06-30
forum: Server Platforms
---

### Post by mogwai on 2009-06-30
I have installed apache2 on 9.04 with ```
tasksel lamp-server
```. I used ```
a2enmod userdir
``` and restarted apache. I created a public_html directory in my HOME. But I get a 403 Forbidden error when I navigate to [http://localhost/~myuser/](http://localhost/~myuser/) or anything under it. 

If I just go to [http://localhost/](http://localhost/) everything there works.

I have tried creating symlinks (/var/www/sites/ -> /home/myuser/public_html/), but i still get the same thing.

PS: I have an encrypted home directory. Is it anything to do with that? If so, any workarounds?

---

### Post by LepeKaname on 2009-07-01
> PS: I have an encrypted home directory. Is it anything to do with that? If so, any workarounds?

It sounds to me the source of your problem. Why do you need your public_html folder encrypted? try to separate them if possible.

---

### Post by mogwai on 2009-07-08
It's not that I needed public-html encrypted, It's just that's where I always had it. I have changed my methods and now store everything under /var/www/sites/

Thanks for your reply though.

---

### Post by Thirtysixway on 2009-07-08
You're getting the error because of permissions.  Set each user's home directory and public_html folder to have the group owner as www-data

/home/user/ -(user:www-data)
/home/user/public_html -(user:www-data)

---

### Post by abaden on 2009-07-09
You could also try "chmod 755" on the public_html directory. "chmod 777" may work too, but that isn't very secure, since anybody can upload files and execute them (such as php scripts that bring phishing sites), which just isn't fun.


Alex

---

### Post by wojox on 2009-07-09
Why don't you put anything in /var/www/sites/ ?

---

### Post by computerikon on 2009-07-09
I&#8217;m new to the Ubuntu game, so correct me if I&#8217;m wrong. I just switch from Windows to Ubuntu Server.
  When I made changes to the /var/www folder I had to use theses commands and it worked for me. The first command I only used it once.
   
  sudo usermod -g www-data [YOUR USERNAME]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

---

### Post by atagar on 2009-08-18
I'm having a similar issue and I think apache simply can't use symlinks to an encrypted home directory. I installed Ubuntu on two systems, one with an encrypted home and one without and did:
sudo rm /var/www/index.html ; sudo rmdir /var/www
mkdir /home/atagar/web
sudo ln -s /home/atagar/web /var/www
echo "<html><h1>yay, it's working</h1></html>" > /home/atagar/web/index.html

For the unencryped system visiting localhost works. However, from the encrypted system it produces a 403 (Forbidden) error. Firefox can still read the file (going to "file:///home/atagar/web/index.html" works), but guess apache just can't touch the encryped home for some reason. I've tried changing the groups to 'www-data' as suggested without success. The obvious workaround is just to use someplace unencrypted:
sudo mkdir /home/web
sudo chown atagar /home/web
sudo ln -s /home/web /var/www

---

### Post by marvec on 2011-06-17
Hello,

for Apache to access your public_html directory, you must allow it to read your home dir (i.e. /home/user). So make sure that others can read and access (execute) (chmod o+rx /home/user). Please note that everybody with access to this machine will be able to read your home directory then.

Martin

P.S.: You don't need to set group to www-data and it works on an encrypted disk as long as you are logged in.

---

