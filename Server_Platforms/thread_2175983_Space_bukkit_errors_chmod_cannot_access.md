---
title: "Space bukkit errors chmod: cannot access"
date: 2013-09-22
forum: Server Platforms
---

### Post by EpicMinerBackup on 2013-09-22
```

root@TerraElysio:/home/jeff# cd /var/
root@TerraElysio:/var# clear
root@TerraElysio:/var# cd www
root@TerraElysio:/var/www# sudo sh install.sh
Checking dependencies...

unzip...                        OK
webserver...                    Apache2
sql...                          MySQL
php...                          OK
php-curl...ls: cannot access /usr/lib*/*curl*: No such file or directory
                        ERROR
You don't have Curl installed. Spacebukkit will need it. Do you want to install Curl now? [Y]/n y
Installing Curl...              OK

Dependencies are OK!

Are you SURE the current directory you are in (/var/www) is the directoy the script is in and also the directory where you want to install Spacebukkit? [y/N]
y
Downloading Spacebukkit now...  OK
Unzipping...chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/tmp’: No such file or directory
chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/webroot’: No such file or directory
chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/Config/database*’: No such file or directory
chown: cannot access ‘SpaceDev-SpaceBukkitPanel-*/*’: No such file or directory
cp: cannot stat ‘SpaceDev-SpaceBukkitPanel-*/*’: No such file or directory
cp: cannot stat ‘SpaceDev-SpaceBukkitPanel-*/.htaccess’: No such file or directory
rm: cannot remove ‘SpaceDev-SpaceBukkitPanel-*’: No such file or directory
                        OK

Everything has been unzipped, modded and owned correctly!
You now have a perfect copy of the awesome Spacebukkit Panel! \o/ *!party!* \o/

```

---

### Post by Simon_WM on 2013-09-24
> **EpicMinerBackup said:**
> ```

root@TerraElysio:/home/jeff# cd /var/
root@TerraElysio:/var# clear
root@TerraElysio:/var# cd www
root@TerraElysio:/var/www# sudo sh install.sh
Checking dependencies...

unzip...                        OK
webserver...                    Apache2
sql...                          MySQL
php...                          OK
php-curl...ls: cannot access /usr/lib*/*curl*: No such file or directory
                        ERROR
You don't have Curl installed. Spacebukkit will need it. Do you want to install Curl now? [Y]/n y
Installing Curl...              OK

Dependencies are OK!

Are you SURE the current directory you are in (/var/www) is the directoy the script is in and also the directory where you want to install Spacebukkit? [y/N]
y
Downloading Spacebukkit now...  OK
Unzipping...chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/tmp’: No such file or directory
chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/webroot’: No such file or directory
chmod: cannot access ‘SpaceDev-SpaceBukkitPanel-*/app/Config/database*’: No such file or directory
chown: cannot access ‘SpaceDev-SpaceBukkitPanel-*/*’: No such file or directory
cp: cannot stat ‘SpaceDev-SpaceBukkitPanel-*/*’: No such file or directory
cp: cannot stat ‘SpaceDev-SpaceBukkitPanel-*/.htaccess’: No such file or directory
rm: cannot remove ‘SpaceDev-SpaceBukkitPanel-*’: No such file or directory
                        OK

Everything has been unzipped, modded and owned correctly!
You now have a perfect copy of the awesome Spacebukkit Panel! \o/ *!party!* \o/

```

you need to do chmod 777 /var/www or install Spacebukkit to a different location

---

