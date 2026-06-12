---
title: "Installing MySQL without the internet ?"
date: 2008-11-12
forum: Server Platforms
---

### Post by ndnd on 2008-11-12
Hello,

My apologies if this comes as a repeat (Had a problem with web and  my entire page went away :)). 

I am new to Linux environment. I needed to install the server edition to run a specific application. I have proceeded to install the latest server edition on my laptop and it went fine. 

I haven't configured my network yet. I would like to install MySQL package and I tried 

sudo apt-get install mysql-server

at the command prompt. However, I got a message that...
 package not found. 

I have the Server Installation CD- can I use that to install the package ? 

If not how can I install SQL without the net ?

Any help would be appreciated. 

Once again I am new to linux (very limited experience as a user) so details would be very much appreciated. I have tried to run searches for my specific problem however, most of SQL installations come up related to different versions etc. 

Thanks in Advance.

---

### Post by Wayne_V on 2008-11-12
If mysql server is on the CD, then yes, you can install it:

$ sudo -s
# cd /etc/apt
# mv sources.list sources.list.save
# apt-cdrom add
# apt-get update
# apt-get install mysql-server

I don't have the Ubuntu server CD tho so I can't guarantee that package is there ...

Once you are attached to the network:

# cd /etc/apt
# mv sources.list.save sources.list
# apt-get update
# apt-get dist-upgrade

---

### Post by cariboo on 2008-11-12
The package you are looking for is mysql-server-5.0, and it should be on the server cd.

Jim

---

### Post by ndnd on 2008-11-13
Hello Wayne_V and cariboo907,
Thank you for your detailed reply. I tried using the above mentioned commands in sequence

When I tried to use the 
#apt -cdrom add
could not open file '/etc/apt/source.list'
The program 'apt' can be found in the following packages:
*sun-java5-jdk (You will have to enable component called 'multiverse')
*openjdk-6-jdk (You will have to enable component called 'main')
*cacao-oj6-jdk (You will have to enable componenet called 'universe')
*sun-java6-jdk  (You will have to enable component called 'multiverse')
Try: apt-get install <selected package>
bash:apt:command not found
root@..:/etc/apt#

---

### Post by Wayne_V on 2008-11-13
apt-cdrom --- no spaces

---

### Post by ndnd on 2008-11-13
Thanks.
It seems I have installed MySQL. However as per the documentation on MYSQL 

Given by:
[https://help.ubuntu.com/8.04/serverguide/C/mysql.html]("https://help.ubuntu.com/8.04/serverguide/C/mysql.html")


Says: 
If I do 
> sudo netstat -tap | grep mysql

I should get something like:
> tcp        0      0 localhost.localdomain:mysql           *:* LISTEN -

However for me I am simply sent to the command prompt without doing anything.

I also tried restarting the database and it did work fine

I still have configured the network if that is the problem. Is there some other way to test if this is okay ?

---

### Post by Wayne_V on 2008-11-13
If the network is not up you probably won't see anything listening.

What does 'sudo ifconfig -a' tell you?

Can you bring eth0 up with a dummy IP just to test?  ('sudo ifconfig eth0 192.168.1.1 up' or something similiar)

---

