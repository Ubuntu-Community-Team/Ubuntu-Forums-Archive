---
title: "copying through ssh from localhost to on-line linux server"
date: 2012-03-05
forum: Server Platforms
---

### Post by pavi_elex on 2012-03-05
I have .pem file of a Linux server so through .pem I can access that linux server.
I am using ubuntu operating system, localhost is installed on ubuntu.
 I am logged in already there using...
```
ssh -i that-pem-file.pem [EMAIL="username@abx-xxx-xxx-xxx-xxx-anotherword1.otherword.com"]username@abx-xxx-xxx-xxx-xxx-anotherword1.otherword.com[/EMAIL]
```
Now I have reached into that server location. I do not have username - password of root or this username from which I am accessing linux server.
I want to copy the files from my localhost to this linux server and vice-versa. I have tried this command.
As I am logged into linux server already so I have tried...
```
[username@ip-xx-xxx-xxx-xxx tmp]$ scp -r /tmp/lampp/lampp root@192.168.0.140:/root/Desktop
```
but it says
ssh: connect to host 192.168.0.140 port 22: Connection timed out
lost connection

please suggest better solution.

---

### Post by Lars Noodén on 2012-03-05
> **pavi_elex said:**
> please suggest better solution.

The directory name suggests that you are experimenting with XAMPP.  That is a good crutch for people still on Windows, but is a very awkward way of doing things in Linux.  Indeed, it is probably the second hardest way of doing things.  It introduces redundant packages, requires manual maintenance and updating, and stores things in non-standard locations, to begin with.  

So, I would reconsider using XAMPP and instead use the Apache2, MySQL, PHP, and Perl that are provided by the package manager.   By using the package manager (via the Ubuntu Software Center, Synaptic or apt-get) you gain the ability to track security and other updates automatically as well as install in standard locations and avoid duplicate, conflicting pacakages.  Perl is built-in by default, so it does not need to be installed. MySQL is split into several packages (mysql-server, mysql-client, php5-mysql, libdbd-mysql-perl, etc.) but you won't need them until you start to build your own CMS or install one that someone else has built.

Doing that may eliminate the need for the directory transfer you are attempting.

---

### Post by pavi_elex on 2012-03-05
Instead of writing this, if you would ignore the thread, it would be better. i am not doing experiments. i have taken test names. I do not want to put my working files name here.
You are in xubuntu development with uncountable posts. 
Please suggest better solution.

> **Lars Noodén said:**
> The directory name suggests that you are experimenting with XAMPP.  That is a good crutch for people still on Windows, but is a very awkward way of doing things in Linux.  Indeed, it is probably the second hardest way of doing things.  It introduces redundant packages, requires manual maintenance and updating, and stores things in non-standard locations, to begin with.  

So, I would reconsider using XAMPP and instead use the Apache2, MySQL, PHP, and Perl that are provided by the package manager.   By using the package manager (via the Ubuntu Software Center, Synaptic or apt-get) you gain the ability to track security and other updates automatically as well as install in standard locations and avoid duplicate, conflicting pacakages.  Perl is built-in by default, so it does not need to be installed. MySQL is split into several packages (mysql-server, mysql-client, php5-mysql, libdbd-mysql-perl, etc.) but you won't need them until you start to build your own CMS or install one that someone else has built.

Doing that may eliminate the need for the directory transfer you are attempting.

---

### Post by Lars Noodén on 2012-03-05
You did ask for a better way.  :)

As far as copying using certificates, you will need to set up root access to be able to copy directly to root.  There's no way around that.

---

### Post by spynappels on 2012-03-05
> **pavi_elex said:**
> 
```
[username@ip-xx-xxx-xxx-xxx tmp]$ scp -r /tmp/lampp/lampp root@192.168.0.140:/root/Desktop
```


I may be wrong, but the prompt suggests that you may already have a shell on the remote server in which case your scp command won't work.

You use the scp in the same way you use ssh, from your local desktop to a remote server.

Try
```
scp -i <identity_file> <source_directory_and_file> <target_directory_and_file>
```

---

