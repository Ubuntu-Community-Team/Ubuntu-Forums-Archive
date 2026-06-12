---
title: "apache2/php/mysql ok. change file through sftp not ok"
date: 2008-10-23
forum: Server Platforms
---

### Post by goksu on 2008-10-23
hello,

I am a somewhat new user to linux. made the transition from winXP a couple of months ago.

I have a laptop (MSI m670 AMD x64 x2 1.5GB RAM) running ubuntu 8.04 hardy. My intention is to use it as a web/DB server for my projects. I have some demos running on WinXP but want to get everything transferred to opensource in the following months. In the near future, this will become harder and harder to do as the work progresses.

I installed apache2, php5, mysql through synaptic. everything worked like a charm! I was surprised. got the "It Works!" web page through the LAN. 

I installed ssh. and managed to sftp to by box from WinXP. I don't want to sit on the laptop while working on the webapps. I want to do the work some other place and upload the contents through sftp. 

problem is this: default sftp directory is /home/username. I crawl to the /var/www directory. can read the index.php. but can NOT edit/change it.

I understand it is an issue with permissions. I did not want to do a dumb chmod everything. I want to do it the right way. Hense my posting here.

I have been reading man pages and tutorials the last couple of months on and off. but I need a quick proper fix to get going with my webapp building effort. 

what is the proper thing to do to update the webapp? How do I do it? 

I have found a couple of threads on the issue. they all seem to go around the ideal solution. some have been hijacked. So here I post anew. The help I get I'll consolidate into a tutorial. 

Thank you.
Goksu

---

### Post by goksu on 2008-10-25
bump, sorry, this is something I really need to have solved. please help.

thank you.

---

### Post by cariboo on 2008-10-25
The quick and improper fix to your problem is to change the permissions on /var/www to world read/writeable this way you can get your work done.

The reason it is improper is that if the site ever goes live on your laptop everybody will be able to change files.

To change the permissions, ssh into the laptop then type:

```
sudo chmod -R 777 /var/www
```

Enter your password when asked. You should now be able to use sftp to drop files directly in /var/www

Jim

---

### Post by zitcon on 2008-10-25
OR, you can log in on sftp as _root_ .

**Quote from my terminal:**
```

lsr@slap:~$ sudo passwd root
[sudo] password for lsr: YOURdefaultPW
Enter new UNIX password: NEWrootPW
Retype new UNIX password: RetypeRootPW
passwd: password updated successfully
lsr@slap:~$ 

```
- Remember to do it in SSH

Now you can log in trough SFTP with root and the password you just made.

- Lasse

---

### Post by goksu on 2008-10-26
ok, can I somehow login as www-data? that user is locked for local login only? it is not in my home directory (/home/www-data does ot exist).

sorry. I am somewhat new to linux.

or other than root and having everything open, no other way? is it possible to have a dedicated user only for updating the apache2 web files?

---

### Post by zitcon on 2008-10-27
Well, cariboo907 have already told you how to do this .

sudo chmod -R 777 /var/www is the command you are looking for ..

To this over SSH or directly on the servers terminal .

---

