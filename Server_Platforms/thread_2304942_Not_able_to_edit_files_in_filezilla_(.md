---
title: "Not able to edit files in filezilla :("
date: 2015-12-01
forum: Server Platforms
---

### Post by soamz on 2015-12-01
I need to edit my index.html as I have installed LAMP. 

So, /var/www/index.html

Logged in as user in filezilla and tried to edit and it did not let me in. 
The file permissions are fine, 644. 


> [FONT=Helvetica]Last login: Mon Nov 30 23:53:39 2015 from 103.194.232.228[/FONT]
[FONT=Helvetica]jetplex@ubuntu:~$ cd /var/www[/FONT]
[FONT=Helvetica]jetplex@ubuntu:/var/www$ cd html[/FONT]
[FONT=Helvetica]jetplex@ubuntu:/var/www/html$ ls[/FONT]
[FONT=Helvetica]index.html  index.html.save[/FONT]
[FONT=Helvetica]jetplex@ubuntu:/var/www/html$ find -maxdepth 15 -type f -exec chmod 777 {} \; [/FONT]
[FONT=Helvetica]chmod: changing permissions of './index.html.save': Operation not permitted[/FONT]
[FONT=Helvetica]chmod: changing permissions of './index.html': Operation not permitted[/FONT]
[FONT=Helvetica]jetplex@ubuntu:/var/www/html$ sudo -i[/FONT]
[FONT=Helvetica][sudo] password for jetplex: [/FONT]
[FONT=Helvetica]root@ubuntu:~# find -maxdepth 15 -type f -exec chmod 777 {} \; [/FONT]
[FONT=Helvetica]root@ubuntu:~#[/FONT]



But filezilla says permission denied.

---

### Post by soamz on 2015-12-01
Solved it with chown.

---

### Post by Habitual on 2015-12-01
Hate to be the bearer of bad news, but
```
[FONT=Helvetica]find -maxdepth 15 -type f -exec chmod 777 {} \;  [/FONT]
```[FONT=Helvetica]
[B][COLOR=#ff0000]IS NOT A 'FIX'.
[/COLOR][/B]You just opened every file for editing to anyone from the 'net that knows the file location.

It's gonna byte you on the backside.

Files should be 644 and directories 755
Add yourself to the www-data group and 
```
[FONT=Helvetica]find -maxdepth 15 -type d -exec chmod 775 {} \;[/FONT]

```[/FONT] if anything.

---

### Post by mastablasta on 2015-12-02
actually files can be 777 as long as the folders are not. 

[http://www.simplemachines.org/community/index.php?topic=2987.0](http://www.simplemachines.org/community/index.php?topic=2987.0)

[COLOR=#FF0000][SIZE=3]**However this is still a much better option!: **[/SIZE][/COLOR]
[COLOR=#FF0000]**> [FONT=Helvetica]Files should be 644 and directories 755[/FONT]**[/COLOR]

---

### Post by boudia on 2015-12-04
i have problem with my ubunut server I m new user and my server give me message permission denied when I tranfser file to /var
and message of ssh transfer error 7
i need help

---

### Post by darkod on 2015-12-04
Did you try reading about linux/ubuntu permissions?

Many system folders are limited for "ordinary" users. To copy into /var you would need to use sudo in front of the command. But even after you copy the file you need to adjust permissions if needed because sudo will copy it as root and in most cases the file will need to be accessed by some application and can not be allowed only for root.

If transferring files from remote location, you could tranfer it to your /home folder first (or another location where you have write rights), and then log in using ssh session and do the sudo copy.

---

