---
title: "Apache2 and public_html"
date: 2005-09-09
forum: Server Platforms
---

### Post by PoZZyX on 2005-09-09
Hello,

I've activated in apache2 configuration the "public_html" option.

PHP and Mysql are ok on /var/www/ but on ~/public_html/index.php (<?php echo "blub"; ?> ) I get :
Warning: Unknown(/home/pozzyx/public_html/index.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)(): Failed opening '/home/pozzyx/public_html/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0.

After I do : chmod 644 index.php , the page is ok.

But when I create a file with gnome (right clic => new blank document), it creates the file with no permission to read to "others".

Is there the possibility to create files with gnome automatically with 644 permissions ? Or a method for Apache2 to read files with permissions only to users ?

Thx

PS : Sorry for my english, that's not my first language. I hope you understand me :S ;)

---

### Post by lao_V on 2005-09-09
Sorry, did you restart apache after modifying the conf file?

---

### Post by Spudgun on 2005-09-09
[QUOTE=lao_V]Sorry, did you restart apache after modifying the conf file?[/QUOTE]

I think the problem is that he can't create new files with a 644 permission as default.

---

### Post by PoZZyX on 2005-09-09
[QUOTE=Spudgun]I think the problem is that he can't create new files with a 644 permission as default.[/QUOTE]

Yes that's exactly my problem, is there a solution ?

---

### Post by LordHunter317 on 2005-09-09
[QUOTE=PoZZyX]Yes that's exactly my problem, is there a solution ?[/QUOTE]
 Change your default umask in /etc/profile.  Set it to 022.

---

### Post by PoZZyX on 2005-09-10
[QUOTE=LordHunter317]Change your default umask in /etc/profile.  Set it to 022.[/QUOTE]

The umask in /etc/profile is already 022 :S

I want if possible to create automatically files with permission 644 only in public_html, if possible...

---

### Post by LordHunter317 on 2005-09-10
Well, clearly, something isn't following that then; if your run 'umask' on the command is 0022 spit out?

If not, I can think of a way to forcibly override in that directory with ACLs.

---

### Post by PoZZyX on 2005-09-10
[QUOTE=LordHunter317]Well, clearly, something isn't following that then; if your run 'umask' on the command is 0022 spit out?

If not, I can think of a way to forcibly override in that directory with ACLs.[/QUOTE]

pozzyx@sony:~/public_html$ umask
0022
pozzyx@sony:~/public_html$

---

### Post by LordHunter317 on 2005-09-10
What are the permissions on ~/public_html proper (ls -ld ~/public_html)?

And you're using gedit to create these files?

---

### Post by PoZZyX on 2005-09-11
[QUOTE=LordHunter317]What are the permissions on ~/public_html proper (ls -ld ~/public_html)?

And you're using gedit to create these files?[/QUOTE]

pozzyx@sony:~$ ls -ld public_html/
drwsr-sr-x  3 pozzyx pozzyx 200 2005-09-08 21:49 public_html/


and to create the files I do right clic => create new document => blank document :
pozzyx@sony:~$ ls -l public_html/
-rw-------  1 pozzyx pozzyx     0 2005-09-11 12:42 new document

and I need -rw-r--r--

---

### Post by LordHunter317 on 2005-09-11
I'd look in the nautilus preferences to see if it has a default, different umask setting.  Or, stop creating files that way, I suppose.  Either way, it makes no sense as to why those permissions are being set like that.

---

### Post by PoZZyX on 2005-09-13
How can I simply create php files with good permissions ?

---

### Post by LordHunter317 on 2005-09-13
Try creating the file with gedit directly?  Or use a command-line editor?

---

### Post by Ride Jib on 2005-09-13
Sorry to interrupt, but on a similar note, can you cause a user to have a different default group when creating files in a certain directory?

For instance, i am user x, and user y wants to work on our web files. is there a way for him to not have to chgrp to "webgrp" when in /var/www ?

---

### Post by LordHunter317 on 2005-09-13
Yes, make the directory be group-owned by webgrp, then add the setgid bit:```
chgrp webgrp /var/www
chmod 2775 /var/ww
```It'll probably be worthwhile to add him to webgrp as well (I assume he if, if he can chgrp).  Also, that only applies to new files and directories in /var/www, you'll need to do it recursively to effect other existing directories.

---

### Post by Ride Jib on 2005-09-13
[QUOTE=LordHunter317]Yes, make the directory be group-owned by webgrp, then add the setgid bit:```
chgrp webgrp /var/www
chmod 2775 /var/ww
```It'll probably be worthwhile to add him to webgrp as well (I assume he if, if he can chgrp).  Also, that only applies to new files and directories in /var/www, you'll need to do it recursively to effect other existing directories.[/QUOTE]


sweet. thank you very much. I will relinquish my thread-jacking now  [-X

---

### Post by loon on 2005-09-14
nm....

---

### Post by CYHPT.net on 2005-09-15
Hi,

I have a problem with a start of my IP address. Im not sure, but I cant find DocumentRoot in the apache2.conf file. What I want to do is to do [http://192.168.0.1](http://192.168.0.1) and the index.html page should show up. But for some reason it doesnt, it only shows the indexes which has the folder of apache default. But when you click on the folder, it shows the page.

I really need to go straight to the index.html page where I only have to enter [http://192.168.0.1](http://192.168.0.1) instead of [http://192.168.0.1/apache2-default](http://192.168.0.1/apache2-default)

I hope you guys know wat Im tryin to say here.

Thanks

---

### Post by Ride Jib on 2005-09-16
[QUOTE=CYHPT.net]Hi,

I have a problem with a start of my IP address. Im not sure, but I cant find DocumentRoot in the apache2.conf file. What I want to do is to do [http://192.168.0.1](http://192.168.0.1) and the index.html page should show up. But for some reason it doesnt, it only shows the indexes which has the folder of apache default. But when you click on the folder, it shows the page.

I really need to go straight to the index.html page where I only have to enter [http://192.168.0.1](http://192.168.0.1) instead of [http://192.168.0.1/apache2-default](http://192.168.0.1/apache2-default)

I hope you guys know wat Im tryin to say here.

Thanks[/QUOTE]

If memory serves me right, I just deleted the apache2-default directory, and had my index.html in /var/www and it recognized that page as default therein.

---

### Post by CYHPT.net on 2005-09-17
[QUOTE=Ride Jib]If memory serves me right, I just deleted the apache2-default directory, and had my index.html in /var/www and it recognized that page as default therein.[/QUOTE]
 Hmm.. so I cant create an extra folder under www?

---

