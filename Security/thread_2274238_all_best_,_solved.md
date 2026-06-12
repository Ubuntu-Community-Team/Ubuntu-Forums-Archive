---
title: "all best , solved"
date: 2015-04-18
forum: Security
---

### Post by ron38 on 2015-04-18
solved]

Hi guys i'm Ron , last days i start play with ubuntu 14 i'm newbie with command line but i get skills every day ! my dream is to make web server in ubuntu , but a little different Encrypted ! this is what i do for now i installed LEMP and after ```
 sudo adduser --encrypt-home aes256 
``` ```
 sudo visudo aes256 ALL=(ALL:ALL) ALL 
``` i log with ssh from new user: aes256 ```
 sudo mkdir /home/aes256/www 
``` ```
 sudo nano /etc/nginx/sites-available/encryptweb and here i modified the root /usr/share/nginx/www; with root /home/aes256/www; 
``` ```
 sudo nano /home/aes256/www/index.html and i write something inside , but when i go to IP/index.html or only IP it say 403 forbidden or something like this , i think it say this because /home/aes256/ its encrypted , so my question is how can i mount the encrypted home for be writable by WebServer ? i'm sure this is problem i tried do all steps with another user with home not encrypted and it show the index.html but with encrypted it say 403 forbidden something like this 
``` and other question are ? i have to change the new directory of webfiles only in /etc/nginx/sites-available/encryptweb ? or need to change in another directory's too ? if yes Wich files need to be modified ? ```
 last question Can i create 1 encrypted folder in /home/aes256/encryptedfoldername and make save all things here ? like MySQL DB - web server files ? its possible this ? if yes wich are the best software for create encrypted folders ? 
```

---

### Post by cariboo on 2015-04-19
Why? No one would be able to view the web page if you encrypted it. My personal feeling is that you should spend the time learning how to set up a server before taking on something like you suggest. What you want to do would probably mean you need to create a custom install, as you'd need to create custom configuration files for almost anything.

---

### Post by QIII on 2015-04-19
Hello!

Echoing and also adding:

If what you are trying to do is harden/secure your web server, you should read up on securing an Ubuntu web server and securing nginx.

Study up on it before you actually put anything on the web.  You can use a Raspberry Pi ($35) or an old machine as your test bed behind your NAT router at home to do all of your learning and experimentation while asking lots of questions here before you risk disaster.  There are a lot of very knowledgeable Forum users who would be quite happy to give you pointers.  You can build a functional web server inside your home network and use all the nasty pen testing tools you can find to plumb its weaknesses.  Just don't ask here how to use them because we'll close the thread.  

I'm on the road right now with only my laptop, or I'd give you a list of sites to look at.  I know that digitalocean.com has a lot of good tutorials for their VPS customers.

You might google using terms like 

```
secure ubuntu web server
```

or 

```
secure nginx server
```

No single source will have every detail of everything you can do for security, so don't just pick a single one and think you're done.  Securing a web server is a continuous process.

You may find that what you are really looking for is SSL... but I don't know.

---

### Post by ron38 on 2015-04-19
cariboo907  are you sure ? because for example if i mount the encrypted folders , the web server will be able to read / write files on DB etc or not ?  Qlll thanks for your suggestions i already do all this things ! just i want to know if there's a way for make run website from an encrypted folder , of course this folder need to be mounted , if i don't understand wrong when folder its mount , its like its normal ,

---

