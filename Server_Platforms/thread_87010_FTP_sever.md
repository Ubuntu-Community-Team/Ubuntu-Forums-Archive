---
title: "FTP sever"
date: 2005-11-07
forum: Server Platforms
---

### Post by amalby on 2005-11-07
Hello! I want to setup my own FTP sever so i can go to my friends house and download some files when ever i want. I am using ubuntu 5.10. I am not sure if there is an easy way or not but i am willing to learn.

Thanks a bunch!

---

### Post by adwait on 2005-11-07
Install the ftp server with
```
sudo apt-get install vsftpd
```
Now start the ftp server with
```
sudo /etc/init.d/vsftpd start
```

You are done. You can connect from any computer to your computer using its IP address and a ftp client

PS: To start the server everytime you switch your computer on
```
sudo rcconf
```
Check the box against vsftp (or whatever). If you get a command not found error,
```
sudo apt-get install rcconf
```

---

### Post by frodon on 2005-11-07
[QUOTE=amalby]Hello! I want to setup my own FTP sever so i can go to my friends house and download some files when ever i want. I am using ubuntu 5.10. I am not sure if there is an easy way or not but i am willing to learn.

Thanks a bunch![/QUOTE]I wrote a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=79588") for beginners about that, you should have a look :)

---

### Post by Rollo Tamasi on 2005-11-07
[QUOTE=adwait]
You are done. You can connect from any computer to your computer using its IP address and a ftp client
[/QUOTE]

i presume you connect by ftp.myipaddress is it?

---

### Post by adwait on 2005-11-07
no just your ip.
eg: if there's a box asking you to enter the address of the server, enter only your Ip address (eg: 202.567.341.2)

---

### Post by herrpoon on 2005-11-07
Hi, I am confused, for my ftp needs I just use sftp, other than sftp being encrypted what are the differences?

---

### Post by simon w on 2005-11-07
nowt

---

### Post by amalby on 2005-11-07
when i try to log in it gives me an error

after i enter my user name and password!

is my user name my user name on my computer?


ERROR when i enter a username and password:    500 opps child dead

ERROR with out username and password:  500 Opps: vsftpd: refursing to run with writtble annoymous boot

---

### Post by adwait on 2005-11-08
Username and password are same as those on the computer.

---

### Post by amalby on 2005-11-09
then why do i get the error

---

### Post by grendelkhan on 2005-11-10
In vsftd.conf did you enable local users?  I think they're disabled by default.

---

### Post by chusome on 2005-11-10
by default vsftpd is set to only handle anonymouse connections
open a terminal and type:


sudo gedit /etc/vsftpd.conf

and edit these lines to appear as follows:

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=no

# Uncomment this to allow local users to log in.
local_enable=YES

---

### Post by tonym on 2005-11-13
[QUOTE=herrpoon]Hi, I am confused, for my ftp needs I just use sftp, other than sftp being encrypted what are the differences?[/QUOTE]

I agree,  install Open SSH and use sftp.  Easier to set up and more secure.  You can even set up certificates so you don't need to enter passwords each time.

---

### Post by Arvin on 2005-11-15
openssh+[mysecureshell]("http://translate.google.com/translate?u=http%3A%2F%2Fmysecureshell.sourceforge.net%2Ffr%2Fframe.html&langpair=fr%7Cen&hl=fr&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") is a very good choice ;) 
[http://forum.ubuntu-fr.org/viewtopic.php?pid=65524#p65524](http://forum.ubuntu-fr.org/viewtopic.php?pid=65524#p65524)

---

### Post by grendelkhan on 2005-11-15
If you're using Windows clients and just want to do quick downloads, sftp is more of a pain in the butt because then you need something like Putty to make it work.

I've used vsftpd for years and had no issues with it.

---

### Post by herrpoon on 2005-11-15
[QUOTE=grendelkhan]If you're using Windows clients and just want to do quick downloads, sftp is more of a pain in the butt because then you need something like Putty to make it work.

I've used vsftpd for years and had no issues with it.[/QUOTE]

I use filezilla which has sftp and it works a treat!

---

