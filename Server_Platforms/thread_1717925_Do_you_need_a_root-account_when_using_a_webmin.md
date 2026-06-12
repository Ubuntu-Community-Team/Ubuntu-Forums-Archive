---
title: "Do you need a root-account when using a webmin?"
date: 2011-03-30
forum: Server Platforms
---

### Post by Dry Lips on 2011-03-30
Hi y'all!  
 
 I've got an old computer around that I've put Ubuntu server 8.04 on.
 At the moment, this is only a little hobby of mine purely for educational
 purposes. (Great for learning Linux!) After using this tutorial:
[http://www.the-web-book.com/build-your-own-webserver.html](http://www.the-web-book.com/build-your-own-webserver.html)
for setting up a LAMP-server, I'm trying to figure out is whether
 or not setting up a root-password is necessary or not. I think the tutorial
 is really great for a newbie, but it consistently uses su instead of sudo... 
I'm aware of the fact that setting a root-password isn't recommended 
in the documentation, but don't you need a root-account to be able to run
tools such as webmin? 
[https://help.ubuntu.com/10.04/serverguide/C/user-management.html](https://help.ubuntu.com/10.04/serverguide/C/user-management.html)

---

### Post by lykwydchykyn on 2011-03-30
Once upon a long long time ago you did... but webmin has since been fixed so that you don't require access to root.  When you install it on Ubuntu, it lets you log in with any sudo-enabled account.

BTW, there is a repository for installing webmin now, see here:

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

EDIT: I should add that there is no practical reason to ever enable root on Ubuntu.  If you need a root shell you can just type "sudo -i" or "sudo bash".  The only time I've ever actually *needed* to enable the root account was when using some very badly designed 3rd party software (*cough*VMware p2v tool *cough*).

---

### Post by Dry Lips on 2011-03-30
Well, the funny thing is that I cannot log into webmin (v. 1.380) 
using my ordinary sudo-enabled account. Using root is the only 
thing that works. Could this be because I use 8.04?
 
 (I agree that one should ideally use sudo and not su, but I was
 copying and pasting instructions, and some were written in a way
 where you would have to phrase the commands in another way if 
you used ordinary sudo.)  
 For instance:
 ```
cd /var/www
mkdir webuser1
useradd webuser1 &#8211;p xxxx &#8211;d /var/www/webuser1 &#8211;s /bin/false
chown webuser1 webuser1

``` xxxx being the root-password.

---

### Post by lykwydchykyn on 2011-03-30
> **Dry Lips said:**
> Well, the funny thing is that I cannot log into webmin (v. 1.380) 
using my ordinary sudo-enabled account. Using root is the only 
thing that works. Could this be because I use 8.04?
 

I would suspect the problem is the ancient version of webmin; webmin is at version 1.530, see the repository instructions I linked above to install the most recent version.  It should run on 8.04 just fine.
> 
 (I agree that one should ideally use sudo and not su, but I was
 copying and pasting instructions, and some were written in a way
 where you would have to phrase the commands in another way if 
you used ordinary sudo.)  
 For instance:
 ```
cd /var/www
mkdir webuser1
useradd webuser1 &#8211;p xxxx &#8211;d /var/www/webuser1 &#8211;s /bin/false
chown webuser1 webuser1

``` xxxx being the root-password.
Why would you need webuser1's password to be the same as root's?

You could just do "sudo -i" like I mentioned, get a root prompt, and run the same code; "sudo -i" gets you a root shell, just like "su", but simply uses sudo for privilege elevation.  You wouldn't have to change the commands at all.

Not that it matters to me which one you do, but just making the point.

---

### Post by Dry Lips on 2011-03-30
> I would suspect the problem is the ancient version of webmin; webmin is  at version 1.530, see the repository instructions I linked above to  install the most recent version.  It should run on 8.04 just fine.I suspect your right. Actually I used an old version of the tutorial, 
if I'd used the newest one, I would have installed the newest version
of webmin. The old tutorial has:
```
apt-get install openssl libnet-ssleay-perl libauthen-pam-perl libio-pty-perl libmd5-perl

Then type:

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.380_all.deb 
```Whereas the new tutorial has:
```
wget http://www.webmin.com/download/deb/webmin-current.deb
sudo dpkg -i webmin-current.deb
sudo apt-get -f install
```> Why would you need webuser1's password to be the same as root's?From the tutorial:

[I]Let’s make an account for a user called webuser1 with a password of flintstone.  These are the steps that you need to do for each web user account you want to create:

cd /var/www
mkdir webuser1
useradd webuser1 –p xxxx –d /var/www/webuser1 –s /bin/false
chown webuser1 webuser1
passwd webuser1 and, when asked, choose flintstone as the password.

Note that xxxx above is your root password, not the one that you want to assign for the webuser1 account.[/I]

So, if I understand this right, webuser gets a new password. 
(I didn't bother to include all the code in the quote above, sorry!)

---

### Post by Dry Lips on 2011-03-30
[FONT=Verdana][SIZE=2]I've just removed the old version of webmin, and installed the new,[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]but alas, I still cannot log into any other account but root!

[/SIZE][/FONT][FONT=Verdana][SIZE=2]But webmin shouldn't be the problem here, as the installer[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]specifically stated:[/SIZE][/FONT]
> [FONT=Verdana][SIZE=2]Webmin install complete. You can now login to [https://xx.xx.xx.xx:10000/](https://xx.xx.xx.xx:10000/) [/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]as root with your root password, or as any user who can use sudo [/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]to run commands as root. [/SIZE][/FONT]
 

---

### Post by Dry Lips on 2011-03-30
[FONT=Verdana][SIZE=2]Eureka![/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]I've figured out what the problem was. My normal user had a password that used special characters, which was no problem as long as you used the terminal. But webmin apparently didn't like my password. Changing the password fixed it. [/SIZE][/FONT]

---

### Post by lykwydchykyn on 2011-03-31
> **Dry Lips said:**
> I suspect your right. Actually I used an old version of the tutorial, 
if I'd used the newest one, I would have installed the newest version
of webmin. The old tutorial has:
```
apt-get install openssl libnet-ssleay-perl libauthen-pam-perl libio-pty-perl libmd5-perl

Then type:

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.380_all.deb 
```Whereas the new tutorial has:
```
wget http://www.webmin.com/download/deb/webmin-current.deb
sudo dpkg -i webmin-current.deb
sudo apt-get -f install
```

I would recommend using their APT repository.  That way you get the most recent version whenever you update.
> 
From the tutorial:

[I]Let’s make an account for a user called webuser1 with a password of flintstone.  These are the steps that you need to do for each web user account you want to create:

cd /var/www
mkdir webuser1
useradd webuser1 –p xxxx –d /var/www/webuser1 –s /bin/false
chown webuser1 webuser1
passwd webuser1 and, when asked, choose flintstone as the password.

Note that xxxx above is your root password, not the one that you want to assign for the webuser1 account.[/I]

So, if I understand this right, webuser gets a new password. 
(I didn't bother to include all the code in the quote above, sorry!)

I can't blame you for being confused, but whoever wrote that tutorial needs to reread the man page for useradd.  The "-p" switch is for specifying a password for the user being created.

---

### Post by Dry Lips on 2011-03-31
> **lykwydchykyn said:**
> I would recommend using their APT repository.  That way you get the most recent version whenever you update.
Yes, that would be a very good idea. *done*
> 
I can't blame you for being confused, but whoever wrote that tutorial needs to reread the man page for useradd.  The "-p" switch is for specifying a password for the user being created.I see... I found other stuff in the tutorial that perhaps also
is a bit... inaccurate. For example he uses some sudo in the
new version of his tutorial, but only after logging in as su! 
At least I've learned not to trust every tutorial I find on the
net unconditionally...

Thank you so much for your help; the only thing that now 
remains is to:
```
sudo passwd -l root
```

---

