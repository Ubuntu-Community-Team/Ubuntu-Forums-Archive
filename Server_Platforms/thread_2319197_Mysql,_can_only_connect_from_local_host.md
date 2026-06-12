---
title: "Mysql, can only connect from local host?"
date: 2016-04-01
forum: Server Platforms
---

### Post by Higgins909 on 2016-04-01
So, I've got a VM running ubuntu server, then I've got a laptop running ubuntu desktop, that is being a server/desktop for a week or so. (Gunna run testing game servers on it)
The server has phpmyadmin on in and I can use that fine, but I can't seem to get me laptop's game server to use Mysql.
I tried to telnet from both my server and laptop.  The server will connect to itself though local host, but this.
```

admin-ben@LangweilerG:/etc/mysql$ telnet localhost 3306
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
[
5.6.28-0ubuntu0.15.04.1
                       'jb.YY&#9618;,3YKImhBQOy6mysql_native_passwordConnection closed by foreign host.
admin-ben@LangweilerG:/etc/mysql$

```
The laptop won't connect to it at all.
```

admin-ben@Dellio:~$ sudo telnet 192.168.0.102 3306
Trying 192.168.0.102...
telnet: Unable to connect to remote host: Connection refused
admin-ben@Dellio:~$

```
How can I setup my Mysql server to allow connections from my lan?  Do note I allowed 3306 though ufw on laptop and the VM don't seem to have a firewall?
My router is not port forwarded on this port as I don't want anyone connecting to it, from outside my local network.
I went to my /etc/mysql/ and I checked every config file in there and nothing looked like I could put a IP in it, as I found a forum here, but it was from 2010.
[HTML]http://ubuntuforums.org/showthread.php?t=1625679[/HTML]  I tried the first line of code, with the grep.  There was about 5 lines and 1 was very long.

Thanks,
Higgins909

---

### Post by darkod on 2016-04-01
If I'm not mistaken, in the main mysql config file my.cnf you have a bind-address parameter. By default it is 127.0.0.1 (localhost) to protect from "outside" entry. You can change that bind address to the server private IP but note in this case that you can't use localhost any more. And there can be only one bind address.

If you set it to 0.0.0.0 it will listen on all IPs it has (if there are more) and localhost too.

Don't forget to restart the service after doing the modifications.

And if the laptop is the client you don't need to allow 3306 on it unless you are filtering outgoing traffic too. Only on the server but you said it has no firewall.

---

### Post by Higgins909 on 2016-04-01
That's that thread I didn't exactly link in said.  But I looked in it and this is all it has.
```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

```
I once tried to mod this file because I thought I needed to turn of strict mode... which I guess doesn't exist or maybe just for linux.
It would cause Mysql to not start.
Through phpmyadmin, I setup a user with everything, to be connectable from anywhere (any host %)

Edit, here is a grep thing.
```

admin-ben@LangweilerG:/etc/mysql$ netstat -l --numeric-ports | grep 3306
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
admin-ben@LangweilerG:/etc/mysql$

```

---

### Post by darkod on 2016-04-02
Is that your whole /etc/mysql/my.cnf or you didn't copy the full content? Because it should have much more options in it. This one is basically empty.

The netstat clearly shows that mysql is binded only on 127.0.0.1 which is the default behavior. You should change that with bind-address in /etc/mysql/my.cnf.

---

### Post by Higgins909 on 2016-04-02
> **darkod said:**
> Is that your whole /etc/mysql/my.cnf or you didn't copy the full content? Because it should have much more options in it. This one is basically empty.

The netstat clearly shows that mysql is binded only on 127.0.0.1 which is the default behavior. You should change that with bind-address in /etc/mysql/my.cnf.

Yep, that's the full my.cnf in that file path.
I've tried to sudo mysql -u root -p
then enter bind-address = 0.0.0.0;   but it says there is something wrong with my syntax on line one.
```

admin-ben@LangweilerG:~$ mysql -V
mysql  Ver 14.14 Distrib 5.6.28, for debian-linux-gnu (x86_64) using  EditLine wrapper
admin-ben@LangweilerG:~$

```
Maybe I installed the wrong version or something?

Edit: forgot to mention that every time that I try to modify it, it won't let mysql restart.

---

### Post by darkod on 2016-04-03
I don't think you can issue bind-address on the mysql prompt. It should be in the config file. You are saying that modifying the my.cnf is not letting mysql restart restart correctly?

If you don't have important data in the DBs yet, I think it might be a good time to consider reinstalling mysql.

Did you install it using standard ssh session and command line? Or maybe using some GUI tools? I am asking because often various GUI tools do not correctly edit some config files and can create issues that way.

Your situation is very weird because the default my.cnf after installation has much more data in it.

---

### Post by nerdtron on 2016-04-03
Did you use sudo to edit the /etc/mysql/my.cnf file?


This is a system file and cannot be edited by the normal user. You need the sudo or root access to modify this file. Same goes for restarting mysql service. Can you post your screenshot on how you edit the file and the error you receives when you restart mysql.

---

### Post by Higgins909 on 2016-04-03
Yes I've used sudo nano /etc/mysql/my.cnf to edit the my.cnf.  I've scrolled down to check and even used vi.
I  want to say I used the ssh/command line to install mysql, but then  after that I installed phpmyadmin and that added apache2 which was done  though a semi graphic menu.
The error logs seems to be empty.  Yes, mysql hangs on startup/restart of mysql when I modify my.cnf
How  would I go about, reinstalling mysql? apt-get remove, purge? other?   Also since I've got phpmyadmin and apache2 working with it?

---

### Post by cariboo on 2016-04-03
I guess someone should mention here that if you allow access to mysql from systems other than the one it is installed on, you may be leaving yourself open to others accessing it. I'd suggest if you want to use mysql from the command line, you do it via ssh without a password.

---

### Post by Higgins909 on 2016-04-04
Its only going to be on a LAN, the modem/router thing will not be port  forwarded for mysql.  But what do you mean "without a password" Like do I  log into server by ssh, then sudo mysql -u root -p or ?
I installed  mysql-server on my debian machine but did not install phpmyadmin or  apache2 as I was just testing and the my.cnf was way more filled out.
On  a security note, I noticed in phpmyadmin, you could setup so users  could only connect to the mysql server from a certain ip. (have yet to  test for sure)

---

### Post by darkod on 2016-04-04
I would say try reinstalling mysql on the server. It shouldn't matter that you added phpmyadmin later.

To make sure you get rid of all config (and if there is nothing you with to keep!!!):
```
sudo apt-get purge mysql-server
sudo apt-get install mysql-server
```

Then check if the default my.cnf has more data, make a copy before beginning to edit it (so you always have the default original) and try to change the bind-address. I think just commenting out the 'bind-address=127.0.0.1' should be enough in fact. In case it comes uncommented (active).

---

### Post by Higgins909 on 2016-04-04
I did "sudo apt-get --purge remove mysql-server" then "sudo apt-get install mysql-server" and I think it installed the same version.
Ubuntu sever
```

admin-ben@LangweilerG:~$ mysql -V
mysql  Ver 14.14 Distrib 5.6.28, for debian-linux-gnu (x86_64) using  EditLine wrapper
admin-ben@LangweilerG:~$ 

```
Ubuntu Desktop laptop and Debian server. (not sure why my laptop has mysql server on it)
```

admin-ben@Dellio:~$ mysql -V
mysql  Ver 14.14 Distrib 5.5.47, for debian-linux-gnu (x86_64) using readline 6.3
admin-ben@Dellio:~$

```
Hmm I guess it didn't ask me to make a password for root, but on my debian build it uses ReadLine wrapper?  What is the wrapper?
Just noticed darkod's post.  Tired it and the same thing.
Maybe its installing a broken version of it?  This wouldn't be the first time ubuntu server has done this to me. (samba feature broken or totaled for os reinstall)

---

### Post by cariboo on 2016-04-04
> **Higgins909 said:**
> Its only going to be on a LAN, the modem/router thing will not be port  forwarded for mysql.  But what do you mean "without a password" Like do I  log into server by ssh, then sudo mysql -u root -p or ?
I installed  mysql-server on my debian machine but did not install phpmyadmin or  apache2 as I was just testing and the my.cnf was way more filled out.
On  a security note, I noticed in phpmyadmin, you could setup so users  could only connect to the mysql server from a certain ip. (have yet to  test for sure)

What I meant is to use ssh with public and private keys, instead of using a password. You also don't need to use sudo to work with mysql.

---

### Post by darkod on 2016-04-04
Mysql can be different version between ubuntu and debian, depending which version of mysql is in the current repositories. Between ubuntu desktop and server it should be the same if they are same version and if mysql was installed with apt-get (not manually from source).

So even reinstalling mysql ended up with the same empty my.cnf, is that what you are saying?

---

### Post by Higgins909 on 2016-04-05
> **darkod said:**
> Mysql can be different version between ubuntu and debian, depending which version of mysql is in the current repositories. Between ubuntu desktop and server it should be the same if they are same version and if mysql was installed with apt-get (not manually from source).

So even reinstalling mysql ended up with the same empty my.cnf, is that what you are saying?

Yep, that's what I'm saying.


Laptop
```

admin-ben@Dellio:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty
admin-ben@Dellio:~$

```
Server, which I think I also failed to mention that My debian and ubuntu server installs are on a VM server.
The ubuntu server VM is also a VM install. (one of the install options)
```

admin-ben@LangweilerG:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid
admin-ben@LangweilerG:~$

```

---

### Post by Higgins909 on 2016-04-05
I found it... this is a bit embarrassing...
I did notice in the  my.cnf of etc/mysql that at the bottom of the included dir's, but I  thought the "mysql.conf.d" was a file...  I did nano it but failed to  notice nano saying it was a dir.
Same for the other one.  Probably  would have spotted this sooner if I knew the ssh color code when I  "ls".  But in the end, googling the troubled mysql version with keyword  my.cnf did it.

---

### Post by darkod on 2016-04-06
Great, I was suspecting if the included paths contain the file but failed to mention it.

By the way, did you notice that you are running the non-LTS 15.04 on your server? And also by the way, it is out of support already. It was released April 2015 and it has only 9 months of support.

Because of that people rarely use non-LTS for servers, even for home servers. Also, your laptop has desktop 14.04 LTS and your server 15.04, hence the difference in the mysql version between the two.

---

