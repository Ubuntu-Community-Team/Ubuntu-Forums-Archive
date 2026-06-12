---
title: "unable to connect to mysql (to remote server), maybe a firewall problem?"
date: 2008-09-26
forum: Security
---

### Post by adhg on 2008-09-26
Hi all,

I am SO confused. here's the scenario: 

I wish to provide access to some users from a remote-location to my mysql on my server. For this I edited the my.conf file and placed:

bind-address =   66.666.66.66 

I gave userA permission to access all databases 
I restarted and it looks good. 

When I do this (from a different computer, not the server)
mysql -u userA -h 66.666.66.66 -p 
I can access with no problems!!!

BUT.... when I try to access with userA from my application (java) I get an exception error: SimpleDataSource: Could not get a good connection to the database.

maybe a fire-wall problem?
I tried: 

$ nmap -P0 -p 3306 66.666.66.66

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-26 17:00 EDT
Interesting ports on h-66.666.66.66.nycmny83.covad.net (66.666.66.66):
PORT     STATE SERVICE
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.075 seconds

it says that it's OPEN.

WHAT'S WRONG?!?!!  
Anyone?! 

* mysql version:  5.0.51a-3ubuntu5.1 
* ubuntu version: Ubuntu 8.04.1 \n \l

---

### Post by cariboo on 2008-09-26
Give this a try in the mysql console:

```
grant all privileges on *.* to userA@'%'
identified by 'password' with grant option;
```


You may want to change the privileges, but that should work.

Jim

---

### Post by adhg on 2008-09-26
No, I get the same error message.

userA is able to connect the server via the command line of a different machine (this is why I suspect it's a fire-wall, but don't know what is the problem).

??:confused:

---

### Post by cariboo on 2008-09-27
In a terminal type:

```
sudo iptables -L
```

Post the output in you next post.

Jim

---

### Post by adhg on 2008-09-27
adhg@tropper:~$ sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by jheaton5 on 2008-09-27
I have some MySql experience and a lot of MS SQL exp.  I have some programing experience.  But I am no expert and am a novice to linux.  Having said all of that, it seems to me if the user can access the database in the terminal but not in the java application then the problem is in the application not MySql or the network.

---

### Post by adhg on 2008-09-27
that was my first assumption, so I check the same code aginst a loclhost db - and it works fine. 

If changing the database location casuse the error - I assume it's a firewall issue. but was is it?!?!?!

---

### Post by cariboo on 2008-09-27
You don't have any firewall rules set, so it can't be a firewall problem:


> Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination 

The above is the output of iptables list and it shows no rules at all.

Jim

---

### Post by adhg on 2008-09-27
Thanks Jim
mmm....so if it's not the fire-wall....what is it?
what else can cause this problem?

on a localserver it works great but not on a remote-server? this is odd.

:confused::confused::confused::confused::confused::confused:

---

### Post by cariboo on 2008-09-28
The only thing I can suggest, is that if you can access the database remotely from a terminal, but not with your application. There must be something in the application that is keeping it from connecting to the database correctly.

Jim

---

### Post by awclemen on 2009-10-14
I know its a little late, but in case anyone is looking at this, there are two things you might need to do:

(1)edit your /etc/mysql/my.cnf and comment out this line:
```
bind-address           = 127.0.0.1
```
also comment out 'skip-networking' if it happens to be in there.


(2) Update the privleges on the database to allow outside hosts to access it.  So in mysql run the command:

```
GRANT ALL PRIVILEGES ON databasename.* TO 'username'@'%' identified by 'password';
``` 

Hopefully that does the trick.

--Andy

---

