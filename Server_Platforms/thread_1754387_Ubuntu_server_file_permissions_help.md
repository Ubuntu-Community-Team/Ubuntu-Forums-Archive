---
title: "Ubuntu server file permissions help"
date: 2011-05-10
forum: Server Platforms
---

### Post by falven on 2011-05-10
Hello,
I have Ubuntu server 11.04 (LAMP, SAMBA) installed with the ubuntu-desktop interface (I am not yet experienced enough to run without it).
My problem is I am trying to share the www directory through samba so I can edit the site, but no matter what I do I get errors when I try and access the directory form the other machine.
I did add it to the smb.conf file, and it does show up fine on teh network, however, when I try and open or change the contents of the directory it says I am unauthorized.
I tried:
```
 sudo chown <sambausername> /var/www 
```
even tried
```
chmod 777 /var/www
```

Thanks,
-Falven

---

### Post by koszta on 2011-05-10
check that samba is running 
```
service samba status
```

Test it like this: 

- add a new user (```
useradd dan
```)
- give him a unix password => sudo passwd dan
- NOW the important part is you have to add him as a user of SAMBA (this is crucial and is probably causing your problem)
- ```
smbpasswd -a dan
```
=> give him a samba password (preferably the same as unix password)
=> make sure that your www directory is defined as a share in ```
/etc/smb.conf
```

=> RESTART SAMBA (```
service samba restart
```)

connect from any windows machine :) (I recomend using netshell directly instead of GUI since that was laggy for me)

---

### Post by falven on 2011-05-10
Hello,
Samba is running. I do not create Ubuntu user accounts for my file shares (To my knowledge they are not needed if just accessing files and are wasteful in such case)I just made samba ones (smbpasswd), and they seem to be working fine for my other shares. It's just the www directory that must have some weird permissions and as such I cannot replace it. See [http://71.227.171.13/](http://71.227.171.13/)
Thanks for your help so far,

---

### Post by volkswagner on 2011-05-10
> **falven said:**
> Hello,
I have Ubuntu server 11.04 (LAMP, SAMBA) installed with the ubuntu-desktop interface (I am not yet experienced enough to run without it).
My problem is I am trying to share the www directory through samba so I can edit the site, but no matter what I do I get errors when I try and access the directory form the other machine.
I did add it to the smb.conf file, and it does show up fine on teh network, however, when I try and open or change the contents of the directory it says I am unauthorized.
I tried:
```
 sudo chown <sambausername> /var/www 
```
even tried
```
chmod 777 /var/www
```

Thanks,
-Falven



```
 sudo chown <sambausername> /var/www 
```
and
```
chmod 777 /var/www
```

Are only modifying the folder not the folder contents.

You can verify by listing the files and permissions.

```
ls -alt /var/www
```

You would need to add the recursive switch, if you want the contents to have the same permissions you are assigning.
```
chmod 777 -R /var/www
```

However I do not recommend such permissions on a website.  Is this site going to be LAN only, or are you opening it to the world?

With your setup you will most likely constantly have permission issues.

For the webserver (Apache2), files need to be readable by the Apache user 'www-data'.  You can try and add www-data to your smbgroup, or vice versa.

---

### Post by falven on 2011-05-10
This website will be open to "the whole world" I would just like to be able to edit it/change it over my LAN (samba network) instead of setting up an FTP service since whenever I edit it I will be in the same network...

---

### Post by volkswagner on 2011-05-11
If you are using Ubuntu to administer the Server, you can use ssh to edit/upload files.

From Ubuntu Desktop goto >Place  >Connect To Server  >Choose Server Type 'SSH', insert ipaddress of server, and enter user name >Hit 'Connect' and you will be prompted for your server password.  This approach will give you a graphical file manager window so you can drag and drop or cut and paste.

---

### Post by falven on 2011-05-18
> **volkswagner said:**
> If you are using Ubuntu to administer the Server, you can use ssh to edit/upload files.
 
From Ubuntu Desktop goto >Place >Connect To Server >Choose Server Type 'SSH', insert ipaddress of server, and enter user name >Hit 'Connect' and you will be prompted for your server password. This approach will give you a graphical file manager window so you can drag and drop or cut and paste.
 
This is what I ended up doing, I forgot I could just SSH throught the local network...
thanks! :)

---

