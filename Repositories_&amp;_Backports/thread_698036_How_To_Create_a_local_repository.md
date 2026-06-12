---
title: "How To: Create a local repository"
date: 2008-02-15
forum: Repositories &amp; Backports
---

### Post by jman12321 on 2008-02-15
The objective of this tutorial is to explain how to create a local mirror of the ubuntu repositories. Depending on how many repositories you mirror, you will need 10-50GB of free space.

[LIST=1]
[*]Log in as root.
```
sudo su
```
[*]Install apt-mirror. This will allow you to mirror the Ubuntu repositories.
```
apt-get install apt-mirror
```
[*]Select which repositories you would like to mirror.
```
vim /etc/apt/mirror.list
```
[*]Install apache2
```
apt-get install apache2
```
[*]Create a link between your repository and apache
```
ln -s /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/ /var/www/
```
[*]Run apt-mirror. This will take a long time to finish, as you are downloading gigabytes of information.
```
apt-mirror
```
[*][Optional] If you would like your mirror to update daily, uncomment the line in cron
```
vim /etc/cron.d/apt-mirror
```
[*]Edit source.list to use your new mirror
```
vim /etc/apt/sources.list
```
Entries will look similar to:
```
deb http://<hostname or IP>/ubuntu/ gutsy-updates main restricted
```
[/LIST]

---

### Post by K.Mandla on 2008-02-19
Moved to Repositories and Backports.

---

### Post by Gourgi on 2008-06-08
hi 
thanks for the tutorial worked out of the box

but i have a problem with all the packages, when i update the replace sources.list to my clients with those from my local repository a warning is displayed saying that the packages are from an unsigned source

is there any way, packages, or script to sign the packages i mirror?
or is there an other solution to this ?

---

