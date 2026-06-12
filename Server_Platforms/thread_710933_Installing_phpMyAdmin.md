---
title: "Installing phpMyAdmin"
date: 2008-02-29
forum: Server Platforms
---

### Post by iSplicer on 2008-02-29
Hey all!

I just thought Id ask for assistance for a problem I am having: 

```
isplicer@Server:~$ sudo apt-get install phpmyadmin
[sudo] password for isplicer:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mcrypt but it is not installable or
                       php4-mcrypt but it is not installable
E: Broken packages
isplicer@Server:~$

```

I am on a Fresh LAMP installation of Ubuntu Server 7.10 x86, and I am accessing the server through SSH

Apt-get install phpmyadmin wont work? Can someone kindly provide assistance?

Thanks!

---

### Post by Alekc on 2008-02-29
Try to exec 
sudo apt-get install php-mcrypt and paste here output if it go wrong please. 

Does Php working correctly?

---

### Post by acidsolution on 2008-02-29
If you have php and mysql running fine on your system why donw you download the latest release of phpMyadmin and copy it on your /var/www/apache2-default/  folder so that you can directly use it 
i have done the same and it is working fine for me 
you can download phpmyadmin from 

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

phpMyadmin is just a phpcode for accesing mysql so its basic requirement is php and mysql running fine on server .
hope it helps for you

---

