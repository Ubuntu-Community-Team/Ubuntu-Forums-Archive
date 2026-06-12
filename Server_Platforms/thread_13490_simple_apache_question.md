---
title: "simple apache question"
date: 2005-01-31
forum: Server Platforms
---

### Post by Ampsonic on 2005-01-31
This is my first day on linux, so you'll have to excuse me. I really did try to find the answer myself, and I'm sure theres a very obvious place to find it, but for some reason it eludes me. Here's my problem:

I installed apache 2 on my new ubantu box. (A speedy pII 400mhz). It took me forever to find that you put your "web files" in /var/www  but when i try to put something there, I don't have write access, and I don't know how/if I should change the permissions. (right clicking on the folder and going to permissions won't let me change anything). I also was looking to see if I could just change the "web folder" to something I create, but I can't find that in the config files either. All of my searching through the apache documentation didn't tell me any of this, though I bet I just can't find the correct place to look.

Wow, that's a long winded post. Sorry.

---

### Post by DJ_Max on 2005-01-31
You have to have root privileges to write to anything outside your /home directory. In actuality, you don't have to put them there.
Make a directory called public_html in your home directoy. For example, my username is daejuanj, so it looks like.
/home/daejuanj/public_html
I put my files in that folder. I access the folder in your browser by [http://localhost/~daejuanj](http://localhost/~daejuanj)

This is of course the default settings Apache has in it's config file whenever you compile it manually. It's looks like you installed it via a .deb packages, and it's config is a bit different, but not too different. So it should work either way.

---

### Post by Ampsonic on 2005-01-31
How would I set it up so that the files are accessed only via [http://localhost](http://localhost) ?

Is there any GUI for config?

---

### Post by benjamin on 2005-02-01
You have to change the apache config file httpd.conf and change it.
After ..... restart Apache.

Bye

---

### Post by az on 2005-02-01
No, you do not need root permissions to write anywhere outside your home drive.  That is too simplistic and insecure.  
The /war/www folder belongs to www-data.  Add your user to that group and you should be able to write there.

To use public_html directories, you need to enable user directories in the apache2 configuration.  Read the manual.

No, there is no GUI.


"How would I set it up so that the files are accessed only via http://localhost"

You need to change the redirect in the configuration.

---

### Post by DJ_Max on 2005-02-01
When I meant root privileges, I mean a normal user  would need special privilges and by default, won't be able to write to anything outside your home directory......

Anyway, you need to restart apache for the changes to take effect.

---

### Post by BillDrew on 2005-02-03
[QUOTE=DJ_Max]You have to have root privileges to write to anything outside your /home directory. In actuality, you don't have to put them there.
Make a directory called public_html in your home directoy. For example, my username is daejuanj, so it looks like.
/home/daejuanj/public_html
I put my files in that folder. I access the folder in your browser by [http://localhost/~daejuanj](http://localhost/~daejuanj)

This is of course the default settings Apache has in it's config file whenever you compile it manually. It's looks like you installed it via a .deb packages, and it's config is a bit different, but not too different. So it should work either way.[/QUOTE]
 But what if I want it  to go to a specific page without the ~username?  That is my problem.  I don't want to use the url in the style of [http://www.servername.edu/~username](http://www.servername.edu/~username) I want [http://www.servername.edu](http://www.servername.edu) to take me to the proper page.

---

### Post by az on 2005-02-03
"But what if I want it to go to a specific page without the ~username? That is my problem. I don't want to use the url in the style of [http://www.servername.edu/~username](http://www.servername.edu/~username) I want [http://www.servername.edu](http://www.servername.edu) to take me to the proper page."

You need to change the redirect in the configuration. 

look in /etc/apache2/sites-enabled/default

---

### Post by cpinto on 2005-02-03
[QUOTE=BillDrew]But what if I want it  to go to a specific page without the ~username?  That is my problem.  I don't want to use the url in the style of [http://www.servername.edu/~username](http://www.servername.edu/~username) I want [http://www.servername.edu](http://www.servername.edu) to take me to the proper page.[/QUOTE]
 In, like azz said, the default configuration, change these settings:

DocumentRoot /home/username

Hope you're only configuring a /home/apache directory structure though.

---

