---
title: "Ubuntu - install multithreading php"
date: 2018-03-07
forum: Ubuntu Application Development
---

### Post by thevento on 2018-03-07
Hi, i try to install a packet which allows use multithreading in php.
System: Ubuntu 17.10
I do it in this way: 
```
sudo add-apt-repository ppa:ondrej/php-zts

```Everything seems correct
Then:
```
sudo apt update

```
Result:
```
Hit:1 http://pl.archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://pl.archive.ubuntu.com/ubuntu artful-updates InRelease                                                  
Get:3 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]                                         
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                        
Hit:5 http://ppa.launchpad.net/ondrej/apache2/ubuntu artful InRelease                                               
Hit:6 http://pl.archive.ubuntu.com/ubuntu artful-backports InRelease                                                
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                                                          
Ign:8 http://ppa.launchpad.net/ondrej/php-zts/ubuntu artful InRelease                                               
Err:9 http://ppa.launchpad.net/ondrej/php-zts/ubuntu artful Release                                             
  404  Not Found
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/ondrej/php-zts/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```It's looks like packet does not exist and i get 404 error, i don't know how i fix that..


Thank you in advance for your help..

---

### Post by SeijiSensei on 2018-03-07
How busy is your web server?  I highly doubt you're pushing it to levels where multi-threaded PHP might actually make an observable difference in performance.  Inefficient coding and poorly-indexed databases are the more likely culprits.

---

### Post by thevento on 2018-03-07
It's not important, I want only to run cleary (with index file only) project and test multi-threaded, nothing more... I don't think so this information is important but i use apache2...

---

