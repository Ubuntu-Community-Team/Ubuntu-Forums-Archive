---
title: "Apache2 + ownCloud not working..."
date: 2015-03-30
forum: Server Platforms
---

### Post by Josh22799 on 2015-03-30
I have been working on this for over 12 hours and I am now getting quite tired of it.

I have been getting a 403 Forbidden page whenever I go to http://<IP Address>/owncloud

I have tried almost everything but it keeps coming up with the same thing!

I am still getting used to using my Ubuntu 14.04 LTS server as I have not used it in a while due to a graphics card fault. So that means I will probibaly not understand anything complicated very well for now.

I have run out of options and if you know a simple way to fix this or even better a even simple alternative to ownCloud and with the same (Or simmilar) result, Please let me know, I have grown tired of all this confusion.

Thanks in advance for any replies!

P.S: I appologise for any poor spelling or anything not making sense, I have been at this for a while and it is now almost midnight.

---

### Post by volkswagner on 2015-03-30
You really haven't given any information.

Post your Apache host file and permissions of web directory.
Also post links to any tutorial you followed.

---

### Post by Josh22799 on 2015-03-30
Hi,

Thanks for the reply.
Could you please inform me where I could find the files you would like to see, As I said in my previous post. I have kind of lost my way with my Ubuntu machine after not using it for awhile...

Also, I have read so many tutorials that I have not thought to keep track of them...

---

### Post by volkswagner on 2015-03-30
Can you post the output of the following commands?

```
cat /etc/issue
ls -al /var/www
ls -al /etc/apache2/sites-available
```

---

### Post by Josh22799 on 2015-03-30
Hello,

Got the results for the commands you told me to do.

```
josh@josh-Ubuntu-Server:~$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l


-----------------------------------------------------------------------------------------


josh@josh-Ubuntu-Server:~$ ls -al /var/www
total 12
drwxr-xr-x  3 root root 4096 Mar 30 21:59 .
drwxr-xr-x 14 root root 4096 Mar 30 21:30 ..
drwx------ 11 root root 4096 Mar 30 17:39 owncloud


-----------------------------------------------------------------------------------------


josh@josh-Ubuntu-Server:~$ ls -al /etc/apache2/sites-available
total 32
drwxr-xr-x 2 root root 4096 Mar 30 22:17 .
drwxr-xr-x 8 root root 4096 Mar 30 22:23 ..
-rw-r--r-- 1 root root 1329 Mar 30 22:14 000-default.conf
-rw-r--r-- 1 root root 1336 Mar 30 22:08 000-default.conf~
-rw-r--r-- 1 root root 6441 Mar 30 22:17 default-ssl.conf
-rw-r--r-- 1 root root 6437 Jan  8  2014 default-ssl.conf~



```

Thanks.

---

### Post by Josh22799 on 2015-03-31
I have managed to get the server to work on my Windows machine, But for some odd reason it wont work on my Ubuntu Server...

---

### Post by nerdtron on 2015-03-31
This is wrong:

drwx------ 11 root root 4096 Mar 30 17:39 owncloud

Owncloud should be readble to all. This is basic for web pages. Which guide did you follow?

To fix:

chmod a+r /var/www/owncloud

---

### Post by Josh22799 on 2015-04-01
Hi,

Thanks for the command, I will try it out in the terminal later when I can get the machine to run.

I didn't really follow many guides and installed the Server files according to my own knowlege and this is the only problem I have run into so far (Appart from the fact that I cant get a CSR code from Apache on any platform, Working or not.)

Anyway, Thanks for your help and I will get back to you when I have the machine running and have tried the code.

---

### Post by Henrik_Iivonen on 2015-04-02
I think owncloud needs write permissions too.
So my guess is that you need: 
chown -R www-data.www-data /var/www
chmod -R u+wr /var/www

---

