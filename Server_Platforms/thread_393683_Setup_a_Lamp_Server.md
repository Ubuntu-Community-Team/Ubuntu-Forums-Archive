---
title: "Setup a Lamp Server"
date: 2007-03-26
forum: Server Platforms
---

### Post by mprusek on 2007-03-26
Hey guys,

Ok, absolute Linux NEWB here. I am attempting to start using an Ubuntu 6.10 Linux Server for web hosting etc.

My uses will include file backup and testing my web pages on it. Now I have about 30 tabs open in firefox trying to find out how to do this but I can't figure it out. 

Could somebody please help me or point me in the direction of a start to finish guide on this?

I installed the server with the LAMP option and I know Apache is running because if I go to 192.168.1.100 it shows the apache screen. I don't know how to get files on there (tried FTP) so that I can upload my web pages to it. 

I found this site:
[http://blog.saturnlaboratories.co.za/2007/01/01/howto-ubuntu-home-lan-server.html](http://blog.saturnlaboratories.co.za/2007/01/01/howto-ubuntu-home-lan-server.html)

But couldn't get past the adding the info to the apache2.conf file (I don't know how to get out of the file :S after I add the info in). 

Thanks guys!

Mita

---

### Post by GumbyNoTalent on 2007-03-26
[www.howtoforge.com](www.howtoforge.com)

Do a quick search and there is a guide how to add all the extra bits.

---

### Post by huygens on 2007-03-26
Hello Mita,

If you have a default Ubuntu 6.10 Server Edition installation, the file for Apache to be published on internet are all under /var/www/

So let say you want to install a blog, CMS or wiki. Just download the file to your Ubuntu server and extract them from the archive under /var/www/ then simply follow the installation instruction of the blog/CMS/wiki.
Take care of one thing. A normal user does not have write access to /var/www/ so you will need 'sudo' to copy/extract files there. Further more, the Apache server runs as www-data user and www-data group. Make sure the file are readable by this user or group, and even writable if necessary.

If you need further assistance, do not hesitate to post back. :-)

---

### Post by huygens on 2007-03-26
I forgot to add 2 interesting resources to set-up a LAMP configuration with Ubuntu.
First, there is the [official Ubuntu documentation]("https://help.ubuntu.com/"): [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html)
If you look for the chapters about HTTPd, PHP5, Databases and/or OpenSSH you should find most of the resources needed for a web server.

Second is the [Ubuntu Documentation Storage Facility]("http://doc.gwos.org/index.php/Main_Page") which has a nice article on Ubuntu Server: [http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

---

### Post by mprusek on 2007-03-26
Gumby - Thanks, looks like a good site! Will check it out :)

Huygens - So how do I upload stuff to my web server? Do I have to use my server to do it or do I setup FTP access? I installed Webmin, hopefully I can find some stuff in there :S.

Thanks!

Mita

---

### Post by huygens on 2007-03-26
Do you have your web server locally and do you own the box?
Or is it a host were you have chosen to install Ubuntu Server?

In the first case? How do you access your box? Do you have a keyboard and screen plug to it?
If it is the case, then I would recommend that you install SSH (the package name is openssh-server) So by typing, you should have it:
```
sudo apt-get install openssh-server
```
Then to upload from your "desktop" Ubuntu to your "server" Ubuntu. I would propose the following solution, but there are other possibilities:
on your server type the following commands, they will give "write" permission to the group www-data in /var/www and will make your user part of this group:
```
cd /var
sudo chgrp www-data www
sudo chmod g+w www
sudo adduser <server-username> www-data
```You have to replace <server-username> with the user name you use to login on your server.

Now from your desktop, you can upload data to your server. There are two ways via the command line or the graphical user interface (GUI). I will start with the command line:
from your desktop: ```
scp <my-file-to-upload> <server-username>@<server-hostname>:/var/www/
```Replace the following elements:[LIST]
[*]<my-file-to-upload> by the filename you want to upload (or use "-R directory_name" for a directory)
[*]<server-username> by the user name you use to login on your server
[*]<server-hostname> by the IP address or the hostname (network name) of your server[/LIST]The file are now under /var/www on your server.

If you want to use the GUI. In Gnome, you go in the menu "Places" and then click on "Connect to server". A new window appears. You need to enter the following information:[LIST]
[*]"Service type" select SSH
[*]"Server" enter the IP address or the hostname (network name) of your server
[*]"Port" you can leave it blank
[*]"Folder" you can set it to /var/www
[*]"User Name" enter the user name you use to login on your server
[*]"Name to use for the connection", enter what you want to call it. You could say "Web Server Repository"[/LIST]Now, you should have a new "disk" displayed on the Gnome desktop and in the "Places" menu. When opening it, it may ask you for the password of the user on the server, after this you will see the content of the /var/www directory. Simply drag and drop files or directories there.

After, you should read the information about SSH, MySQL (database), Apache (HTTPd) and PHP in the 2 documentation repository that I mention to you. This is perhaps not needed to start using your web server, but it is recommended if you plan to make your server accessible to other persons (e.g. via internet), because you might need to tighten the security and understand the impact of your configuration changes.

---

### Post by djearwig on 2007-03-26
I use WinSCP to upload my webpages to my server.  Maybe this only works if you develop in a windows environment...
Anyway, I used this link to set up my server in about 45 minutes:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by mprusek on 2007-03-27
Hey guys,

I need some help still

I feel pretty stupid right now :S, I can't figure out how to edit a file with sudo vi.

I make the changes (where the blue ~ are right?) but how do I save?

Also, why is it sometimes when I try to type it won't type, but then when I hit certain keys (not even sure what the keys are) it starts working. For example:

(Using the last posted link for perfect server setup)
Setting up the Network: 

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

but when I try to change DHCP to Static it won't type part of the time then when I try to type it makes capital "C" and "$" symbols. Then if I messup trying to type in the address etc. and try to go back and type anything etc.?

Mainly, how do I get out of the file when I am done editing it? 

Thanks

Mita

---

### Post by huygens on 2007-03-27
No worries, vi is really hard to learn, but I enjoy it a lot now. However, there are easier alternatives.
You can use nano. Simply replace vi by nano in all your command. It will behave as you expect. As for saving, exiting, etc. in nano, it is indicated at the bottom of the screen once launched. For example to save it is written: "^O Writeout" so you have to press the keys Ctrl+O. So the '^' symbol stands for Ctrl (the keyboard key).

As for vi and if you are interested to understand what happen to you, there is two mode in vi. The default after launching vi is called the command mode. You cannot modify directly the content of the text in this mode, but you can use commands that will let you do it. The second mode is the editing mode. So usually, you use command to go quickly at the point where you want to modify the text, and type some more commands (either i, I, a, A, r, R, etc.) to enter into edit mode. In edit mode, you can only edit, no other fancy thing. So to come back to command mode, you need to type the escape key (Esc). To save a file, you need to be in command mode and type :w and then press Enter. To exit, you can type :q and then Enter.

It is a bit complicate at the beginning, but it is really handy after :-) you can find [more information on vi here]("http://www.eng.hawaii.edu/Tutor/vi.html").

---

### Post by huygens on 2007-03-27
> **djearwig said:**
> Anyway, I used this link to set up my server in about 45 minutes:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

I'm reading quickly this how-to, and it is creating a server that does everything... I'm not sure it is the "perfect" set-up. But if you understand what each service is for, then you have an overview about how to configure each of them.

However, _I would strongly suggest **not** to enable the root account_. Using sudo is fine, and in the event that you cannot stand typing all the time sudo before each command, you could use sudo -s. A server with 'root' account enable cannot be "perfect" because an attacker would always know at least this account user name. So he could try brute force attack against this account to gain administrative privileges. Whereas if you use a user name, the attacker would have to figure it out first. This might only delay a really attacker, however, the ones going for quantity will just move to another target.

Furthermore, if your aim is to configure a little home server that will not be accessible to the Internet or through a residential gateway, then the server can stay in DHCP. No need for static IP address. For businesses, a static IP address would be more suitable.

Section 7, is IMHO not necessary. First, I'm not sure of the interest of this ISPConfig script. Second, if ISPConfig uses bash extensions, it should use bash and not sh. So I would recommend not to perform the steps in section 7. If you still want to use ISPConfig, it is easy to modify the file using nano or vi and replace /bin/sh by /bin/bash in the first line of the file.

Section 8, should not be done! Installing development tool on a web server!! That's crasy ;-)

In section 11, it is recommended to make MySQL listen to all interfaces!! If your web server is on the same machine as the MySQL engine, then there is no need to do that, and it is even dangerous, because all external system could access the MySQL database!! It is safer to let it as it is configured in Ubuntu.
Also when creating the root password, one should think of deleting the entries in his history, or anyone managing to access the account can view the mysql root password. To delete the history entirely type 'history -c', or to delete just the required entry, type 'history' then you can view the history offset on the left side. For each entry where the password is visible type 'history -d offset'.

Section 14, there is no need to install the autoconf, automake and autotools for using PHP5!

So I think this how to is far from perfect ;-) but it is a good base if you know what you want to do with your server. Not all advice should be followed.

---

### Post by didijeeeke on 2007-03-27
> **huygens said:**
> '
However, _I would strongly suggest **not** to enable the root account_ 
I am a debian admin for 6 years always used root to log in.
 I know it's a security risk but if you need to manage over 10 servers sudo can be a pain. 
The risk of using root is only big when you use root for graphical sessions i don't need to explain you why (we all know windows:) ) 

Also i configured my servers for 3 password mistakes i don't think the risk is that big unless you give me a better reason to not use root .

---

### Post by mprusek on 2007-03-27
Thanks Huygens,

I will work with nano now, as it seems easier :)

What you said about section 11; what if I'm going to just throw my server in a closet and upload to it from my windows computer? Still not use it?

Thanks for your help,

You've been great!

Mita

---

### Post by mprusek on 2007-03-27
Got the server up and running! :)

Thanks for everybody's help!

Mita

---

### Post by mprusek on 2007-03-28
Ok, thought I had the server up and running. . . 

It was working before, but now when I try to connect with my FTP the directory is empty (/, if I try to go to /var/ it says directory doesn't exist) and ANY folder I try to open it says that the directory doesn't exist :S. . . 

Help?

Thanks,

Mita

EDIT: I found out where I am logging in to:

/home/username/

before I was logging into / which is where I need to log into.

Thanks

EDIT2: NVM Figured it out

Mita

---

### Post by huygens on 2007-03-28
> **didijeeeke said:**
> I am a debian admin for 6 years always used root to log in.
 I know it's a security risk but if you need to manage over 10 servers sudo can be a pain. 

You can always do 'sudo -s' and you're root :-) but at least no one locally who does not have sudo permissions or remotely can use the 'root' account.
The advantage of it? Well for simple commands, administrative privileges is used at a strict minimum. You can still connect as root with sudo.
If someone tries to get administrative privileges but should not be authorised to do so, he would have to guess two things: the login and the password. He might be able to guess both by social engineering, but in the blind it would be a pain for him.

On the other side having the root account enable might get you lazy ;-) and you might be unnecessary using this privilege (this increase the risks to do something bad for the system, even if slightly), an unauthorised person already know the login, he just have to guess the password!

---

### Post by huygens on 2007-03-28
> **mprusek said:**
> What you said about section 11; what if I'm going to just throw my server in a closet and upload to it from my windows computer? Still not use it?

So let's be clearer on that part. Imagine you want to make a web server with PHP and MySQL to install a blogging or wiki platform. The software is written in PHP, requires Apache and a MySQL back-end.
If you put MySQL, Apache and PHP on the same server, then when your PHP application will access the MySQL server, it will be locally. So having the 127.0.0.1 IP for the bind-address is enough.
However, if you plan to have a server with MySQL only, and another physical server with Apache&PHP, then you would need to give access from remote to MySQL.

So as you seem to have one server, do not follow advice in section 11!

I would suggest that you read one of the new [comment on this how-to about MySQL Security]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4#comment-3137").

---

### Post by huygens on 2007-03-29
To increase security, you could also have a look at the following articles in the Ubuntu Documentation:
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://doc.gwos.org/index.php/SecureSSH](http://doc.gwos.org/index.php/SecureSSH) (non official doc)

---

