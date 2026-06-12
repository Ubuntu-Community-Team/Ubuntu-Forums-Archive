---
title: "Lynis 1.5.9 install"
date: 2014-08-06
forum: Security
---

### Post by dunbrokin on 2014-08-06
[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ lynis
The program 'lynis' is currently not installed. You can install it by typing:[/I]

OK, so I have to do something to the downloaded lynis script in this folder.....otherwise it is telling me that lynis from the repositories needs to be installed...but that is 1.3.7 or something like that. The instructioins say to install I should enter sh lynis or ./lynis to install. So I try that.


[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ sh lynis
Security check failed: Permissions for consts or functions file should be 600 with owner root.
Please change ownership and permissions of the extracted files and start Lynis again.
pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ sudo sh lynis
[sudo] password for pj: 
Security check failed: Permissions for consts or functions file should be 600 with owner root.
Please change ownership and permissions of the extracted files and start Lynis again.[/I]

OK, that failed...lets see about the ./

[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ ./lynis
Security check failed: Permissions for consts or functions file should be 600 with owner root.
Please change ownership and permissions of the extracted files and start Lynis again.[/I]

OK, lets check permissions

[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ ls -l
total 180
-rw-r----- 1 pj pj 55092 Jul 31 20:55 CHANGELOG
-rw-r----- 1 pj pj   768 Jul 30 03:36 CONTRIBUTORS
drwxr-x--- 2 pj pj  4096 Jul 25 20:29 db
-rw-r----- 1 pj pj 10380 Jul 25 20:29 default.prf
drwxr-x--- 3 pj pj  4096 Jul 25 20:29 dev
-rw-r----- 1 pj pj  4138 Jul 25 20:29 FAQ
drwxr-x--- 2 pj pj  4096 Jul 31 20:57 include
-rw-r----- 1 pj pj  1389 Jul 25 20:29 INSTALL
-rw-r----- 1 pj pj 35147 Jul 25 20:29 LICENSE
-rwxr-x--- 1 pj pj 32125 Jul 31 20:55 lynis
-rw-r----- 1 pj pj  3054 Jul 25 20:29 lynis.8
drwxr-x--- 2 pj pj  4096 Jul 25 20:29 plugins
-rw-r----- 1 pj pj  4397 Jul 25 20:29 README
pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ [/I]

So lets change permissions

[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ sudo chmod 600 lynis
[sudo] password for pj: 
pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ ls -l
total 180
-rw-r----- 1 pj pj 55092 Jul 31 20:55 CHANGELOG
-rw-r----- 1 pj pj   768 Jul 30 03:36 CONTRIBUTORS
drwxr-x--- 2 pj pj  4096 Jul 25 20:29 db
-rw-r----- 1 pj pj 10380 Jul 25 20:29 default.prf
drwxr-x--- 3 pj pj  4096 Jul 25 20:29 dev
-rw-r----- 1 pj pj  4138 Jul 25 20:29 FAQ
drwxr-x--- 2 pj pj  4096 Jul 31 20:57 include
-rw-r----- 1 pj pj  1389 Jul 25 20:29 INSTALL
-rw-r----- 1 pj pj 35147 Jul 25 20:29 LICENSE
-rw------- 1 pj pj 32125 Jul 31 20:55 lynis
-rw-r----- 1 pj pj  3054 Jul 25 20:29 lynis.8
drwxr-x--- 2 pj pj  4096 Jul 25 20:29 plugins
-rw-r----- 1 pj pj  4397 Jul 25 20:29 README[/I]

OK, that should do it...lets try now...

[I]pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ sudo lynis
sudo: lynis: command not found
pj@pj-Latitude-E6420:/usr/local/lynis/lynis-1.5.9$ lynis
The program 'lynis' is currently not installed. You can install it by typing:
sudo apt-get install lynis
[/I]

Arrgh!....so what is so obvious that I am missing???!

---

### Post by dunbrokin on 2014-08-09
bump!

---

### Post by harold-de-bruijn on 2014-08-11
Hi,

You should have unpacked lynis-1.5.9.tar.gz as root. (sudo -i) after that you can run in the same sudo shell the lynis binary as standalone application. ( # ./lynis -c )
To have it installed as the someone would have to create a package, i did not find a ppa for it in a quick search..

---

### Post by dunbrokin on 2014-08-13
Thanks for that, I will give it a try.

---

### Post by dunbrokin on 2014-08-28
OK, that did not work as well as I had hoped!

pj@pj-Latitude-E6420:~$ cd /usr/local/lynis
pj@pj-Latitude-E6420:/usr/local/lynis$ ls
pj@pj-Latitude-E6420:/usr/local/lynis$ sudo -i
[sudo] password for pj: 
root@pj-Latitude-E6420:~# wget [http://cisofy.com/files/lynis-1.6.0.tar.gz--2014-08-28](http://cisofy.com/files/lynis-1.6.0.tar.gz--2014-08-28) 20:56:44--  [http://cisofy.com/files/lynis-1.6.0.tar.gz](http://cisofy.com/files/lynis-1.6.0.tar.gz)
Resolving cisofy.com (cisofy.com)... 149.210.134.182
Connecting to cisofy.com (cisofy.com)|149.210.134.182|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 155004 (151K) [application/octet-stream]
Saving to: &#8216;lynis-1.6.0.tar.gz&#8217;

100%[======================================>] 155,004     67.4KB/s   in 2.2s   

2014-08-28 20:56:46 (67.4 KB/s) - &#8216;lynis-1.6.0.tar.gz&#8217; saved [155004/155004]

root@pj-Latitude-E6420:~# tar xfvz lynis-1.6.0.tar.gz
lynis/CHANGELOG
lynis/CONTRIBUTORS
lynis/FAQ
etc
etc

So, now

root@pj-Latitude-E6420:~# ./lynis
-bash: ./lynis: Is a directory
root@pj-Latitude-E6420:~# sh lynis
root@pj-Latitude-E6420:~# ,/lynis -c
-bash: ,/lynis: No such file or directory
root@pj-Latitude-E6420:~# sh lynis -c
root@pj-Latitude-E6420:~# lynis
The program 'lynis' is currently not installed. You can install it by typing:
apt-get install lynis
root@pj-Latitude-E6420:~# ls
lynis  lynis-1.6.0.tar.gz
root@pj-Latitude-E6420:~# exit
logout
pj@pj-Latitude-E6420:/usr/local/lynis$ ls
pj@pj-Latitude-E6420:/usr/local/lynis$ sudo lynis -c
sudo: lynis: command not found
pj@pj-Latitude-E6420:/usr/local/lynis$ ./lynis -c
bash: ./lynis: No such file or directory
pj@pj-Latitude-E6420:/usr/local/lynis$ sudo lynis -c
sudo: lynis: command not found
pj@pj-Latitude-E6420:/usr/local/lynis$ lynis
The program 'lynis' is currently not installed. You can install it by typing:
sudo apt-get install lynis
pj@pj-Latitude-E6420:/usr/local/lynis$ ls
pj@pj-Latitude-E6420:/usr/local/lynis$ sudo ls
pj@pj-Latitude-E6420:/usr/local/lynis$ sudo -i
root@pj-Latitude-E6420:~# ls
lynis  lynis-1.6.0.tar.gz
root@pj-Latitude-E6420:~# lynis -c
The program 'lynis' is currently not installed. You can install it by typing:
apt-get install lynis
root@pj-Latitude-E6420:~# ./lynis -c
-bash: ./lynis: Is a directory
root@pj-Latitude-E6420:~# sh lynis
root@pj-Latitude-E6420:~# sh lynis -c
root@pj-Latitude-E6420:~# ./configure
-bash: ./configure: No such file or directory
root@pj-Latitude-E6420:~# exit
logout
pj@pj-Latitude-E6420:/usr/local/lynis$ ./configure
bash: ./configure: No such file or directory

What am I doing wrong please...or not understanding?

---

### Post by cariboo on 2014-08-28
You have to expand the file, as it is a tar archive.

```
tar -zxvf *gz
```

In the lynis directory should get you going.

**edit** you need to use sudo when running the above command

---

### Post by fugu2 on 2014-08-30
> **dunbrokin said:**
> root@pj-Latitude-E6420:~# wget [http://cisofy.com/files/lynis-1.6.0.tar.gz--2014-08-28](http://cisofy.com/files/lynis-1.6.0.tar.gz--2014-08-28) 20:56:44--  [http://cisofy.com/files/lynis-1.6.0.tar.gz](http://cisofy.com/files/lynis-1.6.0.tar.gz)


I cringed when you ran this command.

---

### Post by Habitual on 2014-08-30
Try this [http://bournetoraiseshell.com:3030/8699d5a71c07eff4055d7](http://bournetoraiseshell.com:3030/8699d5a71c07eff4055d7)
and let us know if you have any further questions.

---

