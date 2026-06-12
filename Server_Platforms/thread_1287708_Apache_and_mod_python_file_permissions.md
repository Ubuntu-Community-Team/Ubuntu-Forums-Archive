---
title: "Apache and mod_python file permissions?"
date: 2009-10-10
forum: Server Platforms
---

### Post by UbuKunubi on 2009-10-10
Hello!

Im really hoping that someone can help, as im at my wits end.

I have run into this problem before, but my previous solution is failing!

I have apache2 installed and up on a Jaunty Desktop (because the original dedicated server is now useless due to it's NIC getting fried during a power cut).

Can anyone please tell me what is needed to allow a mod_python program to write to a file in the /var/www directory?

I have tried many combinations of chmod 777,666,etc
I have tried moving the target file to another directory, (my previous solution) and this also fails!

I know this is possible, so I'd be extremely grateful for someone to help.

Many thanks for taking the time to read this,
Ubu

---

### Post by UbuKunubi on 2009-10-11
Bump.

---

### Post by UbuKunubi on 2009-10-12
Bump

---

### Post by rnodal on 2009-10-13
Could you provide at least the results of:
```
ls -l
```

You need to find out who owns the directory and files and the permissions that are in effect so you can trouble shoot things easier.

-r

---

### Post by UbuKunubi on 2009-10-13
> **rnodal said:**
> Could you provide at least the results of:
```
ls -l
```

You need to find out who owns the directory and files and the permissions that are in effect so you can trouble shoot things easier.

-r
Thanks for your input!
Here is the output as requested - I think that you've pointed me towards the cause of the issue - apache needs to be made owner of the file I wish to have test.py modify:msgs.txt
I do not know how to change the ownership (still learning) without locking myself out - despite tring various combinations of chmod.....

abcd@abcd-desktop:~$ cd ..
abcd@abcd-desktop:/home$ cd /var/www/
abcd@abcd-desktop:/var/www$ ls -l
total 211168
-rwx------ 1 abcd abcd     57115 2009-09-21 19:37 aa1.jpg
-rwx------ 1 abcd abcd     12519 2009-09-21 19:38 AlienArena.png
-rwxr--r-- 1 abcd abcd   5922993 2009-10-13 00:42 a.mp3
drwx------ 2 abcd abcd      4096 2009-10-12 22:43 animation
-rwx---r-- 1 abcd abcd      5798 2009-09-28 19:32 Animations.html
-rwx------ 1 abcd abcd       337 2009-10-08 00:24 a.py
-rw-r--r-- 1 abcd abcd         1 2009-10-08 00:24 a.py~
-rwx------ 1 abcd abcd  52215596 2009-08-06 02:12 a.wav
-rwx---r-- 1 abcd abcd      1416 2009-09-21 15:56 BACK_btn.jpg
-rw-r--r-- 1 abcd abcd      4755 2009-09-28 19:39 bored.html
-rwxrwxrwx 1 abcd abcd  21812768 2009-09-22 18:51 mov0001_0250.avi
-rwx------ 1 abcd abcd       760 2009-10-07 23:59 c.html
-rw-r--r-- 1 abcd abcd       751 2009-10-07 23:59 c.html~
-rwx------ 1 abcd abcd      1351 2009-10-08 00:12 d.html
-rw-r--r-- 1 abcd abcd      1482 2009-10-08 00:11 d.html~
-rw-r--r-- 1 abcd abcd      1358 2009-09-24 16:39 EMAPPF.html
-rw-r--r-- 1 abcd abcd      1256 2009-09-21 19:48 GSM.html
-rw-r--r-- 1 abcd abcd      7084 2009-09-21 20:49 ImageGallery.html
drwx------ 6 abcd abcd      4096 2009-10-08 15:26 images
-rwx---r-- 1 abcd abcd      5006 2009-10-13 01:01 index.html
-rw----r-- 1 abcd abcd      5006 2009-10-13 01:00 index.html~
-rwx------ 1 abcd abcd      1675 2009-09-21 21:20 index_html_10f5c287.jpg
-rwx---r-- 1 abcd abcd     21948 2009-09-22 18:20 index_html_18584830.png
-rw-r--r-- 1 abcd abcd     27155 2009-10-13 00:48 index_html_1df4eb2d.jpg
-rwx------ 1 abcd abcd      2683 2009-09-21 21:20 index_html_287dca70.jpg
-rwx------ 1 abcd abcd      1344 2009-09-21 21:20 index_html_3cfade7c.jpg
-rw-r--r-- 1 abcd abcd     31904 2009-10-12 22:27 index_html_4152755b.jpg
-rwx------ 1 abcd abcd      2873 2009-09-21 21:20 index_html_454d3e84.jpg
-rw-r--r-- 1 abcd abcd     14995 2009-10-13 00:48 index_html_4ddb14a0.jpg
-rwx---r-- 1 abcd abcd     45524 2009-10-08 14:05 index_html_5dfa62bd.jpg
-rwx------ 1 abcd abcd     33692 2009-09-23 21:06 index_html_665655ab.png
-rwx------ 1 abcd abcd      2393 2009-09-21 21:20 index_html_9367d8d.jpg
-rwx------ 1 abcd abcd      2776 2009-09-21 21:20 index_html_m1774b2e5.jpg
-rwx---r-- 1 abcd abcd     23896 2009-09-22 18:20 index_html_m1addc6d.png
-rw-r--r-- 1 abcd abcd     13462 2009-10-13 00:48 index_html_m4dc5a2a1.jpg
-rw-r--r-- 1 abcd abcd     24485 2009-10-13 00:48 index_html_m5833cb0d.jpg
-rwx---r-- 1 abcd abcd     21102 2009-09-23 21:06 index_html_m5aca5572.png
-rw-r--r-- 1 abcd abcd     21340 2009-10-13 00:48 index_html_m5fd354f2.jpg
-rwx---r-- 1 abcd abcd      2734 2009-09-21 21:20 index_html_m641d0f52.jpg
-rwx---r-- 1 abcd abcd     33321 2009-09-29 23:58 index_html_m6e0082e2.jpg
-rwx---r-- 1 abcd abcd     96229 2009-10-08 14:05 index_html_m7735f78e.gif
-rwx---r-- 1 abcd abcd     14819 2009-09-23 21:06 index_html_m851f763.png
-rw-r--r-- 1 abcd abcd     30451 2009-10-13 00:48 index_html_ma0730af.jpg
-rwx---r-- 1 abcd abcd     64369 2009-10-08 14:05 index_html_ma4cda28.jpg
-rwxr--r-- 1 abcd abcd 115206204 2009-09-21 23:42 Robot.avi
-rwx------ 1 abcd abcd       280 2009-10-08 17:12 MB_bottom.html
-rw-r--r-- 1 abcd abcd       279 2009-10-08 17:12 MB_bottom.html~
-rwx------ 1 abcd abcd       137 2009-10-08 20:21 MBINDEX.html
-rw-r--r-- 1 abcd abcd       137 2009-10-08 20:20 MBINDEX.html~
-rwx------ 1 abcd abcd        34 2009-10-08 00:18 MB_top.html
-rw-r--r-- 1 abcd abcd         1 2009-10-08 00:17 MB_top.html~
-rwx------ 1 abcd abcd      1406 2009-09-23 23:48 Message.html
-rwxr--r-- 1 abcd abcd  19291686 2009-05-27 00:29 Monsters.mp3
-rwx------ 1 abcd abcd         0 2009-10-11 19:42 MSGS4SKYPE.html
-rwx------ 1 abcd abcd         0 2009-10-08 23:19 MSGS4SKYPE.txt
-rwx------ 1 abcd abcd     15315 2009-08-07 14:33 msgs.txt

---

### Post by rnodal on 2009-10-13
If you want mod_python to create a file under the directory then should either do:

```
chown www-data:abcd /directory
```

or 

```
chown abcd:www-data /directory
```

Try that and see if it works. For the other files with seting the permissions for "others" to be able to read should be fine.

```
chmod o+r /directory/file
```

I hope that helps a little bit.

-r

---

### Post by UbuKunubi on 2009-11-15
> **rnodal said:**
> If you want mod_python to create a file under the directory then should either do:
```
chown www-data:abcd /directory
```
or 
```
chown abcd:www-data /directory
```

Try that and see if it works. For the other files with seting the permissions for "others" to be able to read should be fine.

```
chmod o+r /directory/file
```

I hope that helps a little bit.

-r

Many thanks,
That is just the advise I needed! Thanking you,
Ubu

---

