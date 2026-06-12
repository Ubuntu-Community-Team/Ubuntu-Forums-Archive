---
title: "Installation of MYSQL/phpMyAdmin"
date: 2006-01-07
forum: Server Platforms
---

### Post by hen3rz on 2006-01-07
Hello,

Im looking for a tutorial showing me how to install phpMyAdmin and MYSQL on Ubuntu. 

Im sorry if this is a common question.

Thank you.

---

### Post by Corvillus on 2006-01-08
Getting a LAMP stack on Ubuntu is fairly straightforward
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```
After doing that phpMyAdmin should be installed at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by hen3rz on 2006-01-08
hahah sweet. thank you.

---

### Post by hen3rz on 2006-01-08
you wouldnt happen to know what the default username and password is??? and how i would go about changing them?
[B]
Fixed[/B]

Relised you can do it through phpmyadmin (Default username is root)

---

### Post by pieboy314 on 2006-01-08
[QUOTE=hen3rz]you wouldnt happen to know what the default username and password is??? and how i would go about changing them?
[B]
Fixed[/B]

Relised you can do it through phpmyadmin (Default username is root)[/QUOTE]

I am sorry, I can't figure out how to log in to phpmyadmin
... 

tried username "root" and password blank....and everything else I could think of. ??

** got it, thanks !! **

---

### Post by Copernicus on 2006-09-23
I installed Ubuntu 6.06 and it doesn't have the phpMyAdmin package...any ideas?

---

### Post by nix4me on 2006-09-23
The wiki has step by step instructions for getting mysql/apache/php and phpmyadmin working.  Tells you how to set up mysql user too.

Here is a link:
[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29)


nix4me

---

### Post by jthomp86 on 2006-10-11
ive gotten LAMP installed just fine, but for some reason phpmyadmin is not in my /var/www/ directory. it tells me phpmyadmin is installed, so how do i get to it?

---

### Post by pppetter on 2006-10-12
> **jthomp86 said:**
> ive gotten LAMP installed just fine, but for some reason phpmyadmin is not in my /var/www/ directory. it tells me phpmyadmin is installed, so how do i get to it?

There should be a symlink in /var/www. Try going to the actual site, if you haven't tried that yet: [http://serverIP/phpmyadmin](http://serverIP/phpmyadmin)

IF you have a desktop on your server, you can also do: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by naerae on 2007-03-11
> **Corvillus said:**
> Getting a LAMP stack on Ubuntu is fairly straightforward
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```
After doing that phpMyAdmin should be installed at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Hello. Is it still the same solution method for server based programs? Asking for Ubuntu Edgy.

---

### Post by ztirffritz on 2007-03-11
> **Corvillus said:**
> Getting a LAMP stack on Ubuntu is fairly straightforward
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```
After doing that phpMyAdmin should be installed at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

When I try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it just tries to download a file. It acts as if it has not finished installing.  The file that it tries to download is
1n0nhifs.phtml

**EDIT**
I got in by going to [http://localhost/phpmyadmin/index](http://localhost/phpmyadmin/index)

---

### Post by Nikron on 2007-03-11
> **ztirffritz said:**
> When I try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it just tries to download a file. It acts as if it has not finished installing.  The file that it tries to download is
1n0nhifs.phtml

Make sure your apache server is loading the php5 module...  If you have apache2 and php5, there is an apache command to enable it, but I can't think of it.  If you want to do what I did.. do this

sudo mv /etc/apache2/mods-available/php5 .load /etc/apache2/mods-enabled && sudo mv /etc/apache2/mods-available/php5 .conf /etc/apache2/mods-enabled && sudo /etc/init.d/apache2 reload

---

### Post by kg1 on 2007-03-11
Rather than moving the files as Nikron suggests, I think the preferred method is to make symbolic links from the mods-enabled directory.
```
cd /etc/apache/mods-enabled
sudo ln -s /etc/apache2/mods-available/php5.conf php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load php5.load
```
for whatever mods you need enabled.

And don't forget to restart apache2

---

### Post by Nikron on 2007-03-11
> **kg1 said:**
> Rather than moving the files as Nikron suggests, I think the preferred method is to make symbolic links from the mods-enabled directory.
```
cd /etc/apache/mods-enabled
sudo ln -s /etc/apache2/mods-available/php5.conf php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load php5.load
```
for whatever mods you need enabled.

And don't forget to restart apache2

Actually, wouldn't it just be easier to

```

a2enmod php5

```

My bad for not remembering the command earlier..

---

### Post by neerolyte on 2007-03-28
Any suggestions for what to do if the php5 module is not installing correctly?

```
# apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

# a2enmod php5
This module does not exist!

# ls /etc/apache2/mods-available/ | grep php | wc -l
0
```

I found the fix:
```
# apt-get install libapache2-mod-php5
```

---

### Post by szj on 2007-03-28
Hello,

I was looking for a tutorial showing me how to install phpMyAdmin and MYSQL on Ubuntu and stumbled on your forum (which i'm glad i did!) i followed the instructions and had no problem installing

mysql-server
apache2
php5
php5-mysql

but when i came to install phpmyadmin i got the following problem...

$ sudo apt-get install phpmyadmin

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin

and now i'm a bit stuck!! :confused:  i would appreciate any help you can give me on this subject and many thanks in advance

Thank you.

---

### Post by neerolyte on 2007-03-28
> **szj said:**
> 
$ sudo apt-get install phpmyadmin

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin


I think that's because you don't have the universe apt source enabled... try something like this:
```
$ sudo nano -w /etc/apt/sources.list
*uncomment* this line: deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
*save file*
$ sudo apt-get update
$ sudo apt-get install phpmyadmin 
```

You need the apt-get update in there to make sure it downloads the new headers.

Give that a go.

If I haven't given you the right source it has to be in one of these (because they are all I have enabled):
```
deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
```
Make sure you run apt-get update after **every** source that you change.

Post back which one works so that I can correct this post :)

---

### Post by szj on 2007-03-28
> **neerolyte said:**
> I think that's because you don't have the universe apt source enabled... try something like this:
```
$ sudo nano -w /etc/apt/sources.list
*uncomment* this line: deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
*save file*
$ sudo apt-get update
$ sudo apt-get install phpmyadmin 
```

You need the apt-get update in there to make sure it downloads the new headers.

Give that a go.

If I haven't given you the right source it has to be in one of these (because they are all I have enabled):
```
deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
```
Make sure you run apt-get update after **every** source that you change.

Post back which one works so that I can correct this post :)


FANTASTIC!! :guitar: 

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

was the one that did it!

Thats very much for all your help fantastic forum :)

---

### Post by jvisaac on 2007-05-10
First things first.  These forums have been extremely helpful.

I have an IMac running ubuntu.
I have Apache, mysql, VNC, putty and everything else running on it and it is great.

I had phpmyadmin on it and I messed something up and now it is gone.  
I tried installing it again and it appears like it worked but when I go to /var/www there is no directory phpmyadmin.

Any suggestions???

Thanks in advance for any recommendations.

---

### Post by robbekema on 2007-07-27
## ALLREADY GOT THE SOLUTION!!
My source.list was not correct.
Thnx anyway, this forum is a great help!

I have done all the things on this page.
I have php5 running because I can see my localhost.
But why can't I get phpmyadmin running!
My list of services says that PHP5 and phpmyadmin are running.
But I can't see [http://localhost/phpmyadmin](http://localhost/phpmyadmin).

Does somebody has an solution for my problem?

---

### Post by cmaxter on 2007-07-27
Like said the	
Corvillus dude nn

many say if you can't apt-get it it ain't worth having..

sudo apt-get install php5-mcrypt woe! 

root nn blank will get you inside on a feisty fawn nn feisty fawn is righ't On

 :guitar:

---

### Post by jayjaygibbs on 2008-03-08
> **jvisaac said:**
> 
I tried installing it again and it appears like it worked but when I go to /var/www there is no directory phpmyadmin.

Any suggestions???

Thanks in advance for any recommendations.

if you go to [pluckypigeon]("http://www.pluckypigeon.com/phpmyadmin.html") it has an easy step by step guide that you can follow. You will need mySQL and Apache installed first though! :)

---

### Post by needhelpplease on 2008-03-13
> **Corvillus said:**
> Getting a LAMP stack on Ubuntu is fairly straightforward

After doing that phpMyAdmin should be installed at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Cool, thanks, that worked easily with no hassle.

---

### Post by rubneo on 2008-06-27
Done all the things on this page.
But why can't I get phpmyadmin running!
But I can't see [http://localhost/phpmyadmin](http://localhost/phpmyadmin).
I get :
'Not Found
The requested URL /phpmyadmin was not found on this server.'

HELP! PLEASE!

---

### Post by Kilarin on 2008-06-27
[quote="rubneo"]why can't I get phpmyadmin running![/quote]
adredz just solved this for me in [<this thread>](http://ubuntuforums.org/showthread.php?p=5273812)

All you have to do is create a symbolic link to phpmyadmin in your apache localhost folder.

---

### Post by yantaq on 2008-07-08
> **Kilarin said:**
> adredz just solved this for me in [<this thread>](http://ubuntuforums.org/showthread.php?p=5273812)

All you have to do is create a symbolic link to phpmyadmin in your apache localhost folder.

action speaks louder

 sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin

solved :)

---

### Post by Subabooba on 2008-07-20
> **yantaq said:**
> action speaks louder

 sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin

solved :)

Legend, thank you :)

---

