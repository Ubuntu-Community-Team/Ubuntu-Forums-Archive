---
title: "php not getting permission to create files"
date: 2011-10-24
forum: Server Platforms
---

### Post by shubham1 on 2011-10-24
my php sever is not getting permission to acces files nether to create ahow to set the permissions

---

### Post by SeijiSensei on 2011-10-24
PHP has the same permissions as the Apache server which runs as user www-data.  To write files, the target directory must be writable by user www-data.

---

### Post by linuxwin2 on 2011-10-25
Change permission or owner of files
```
$sudo chown www-data.www-data -r Yourdirectory

```

---

### Post by shubham1 on 2011-10-25
i have change the owner from root to shubham
i want to change the permission of /var/www/
hole but changing the user will give me permission to accaess files

---

### Post by shubham1 on 2011-10-26
done still not geting permission

---

### Post by PsyclonJohn on 2011-10-26
The best and easiest way (to me) is to access them using this command: 

[PHP]gksudo nautilus[/PHP]

Then going to the /var/www folder

---

### Post by shubham1 on 2011-10-26
> **PsyclonJohn said:**
> The best and easiest way (to me) is to access them using this command: 

[PHP]gksudo nautilus[/PHP]

Then going to the /var/www folder
i can create php file
but my php web server is not getting
means using php scripts

---

### Post by shubham1 on 2011-10-26
> **PsyclonJohn said:**
> The best and easiest way (to me) is to access them using this command: 

[PHP]gksudo nautilus[/PHP]

Then going to the /var/www folder
if you want to change the permissions use
sudo chmod -R 777 /var/ww/
if it says permission deneied
then change the owner user
sudo chown username /var/www/

---

