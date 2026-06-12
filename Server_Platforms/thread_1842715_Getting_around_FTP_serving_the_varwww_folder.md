---
title: "Getting around FTP serving the /var/www folder"
date: 2011-09-12
forum: Server Platforms
---

### Post by Heeter on 2011-09-12
Hi all,

I have been trying to upload files directly to the /var/www folder on my webserver via proftpd.

I am the only user. I am able to upload to the /home folder, but not the /var/www folder. I can download from the /var/www via the FTP, but cannot upload, delete, rename, and create via FTP.

I know it's a permissions thing blocking me, but cannot get around it.

Could it be that Ubuntu 11.04 absolutely protects the /var/www folder?

If so, how can I get around it?

Presently, I upload my webfiles into the /home folder, then log into the server, and move them to the /var/www folder.

Thanks

Heeter

---

### Post by louis vitton on 2011-09-12
Hey mate,

This might help. [https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)

This is not using proFTP though but possibly might point you to the right area.

Cheers Louis

---

### Post by cj13579 on 2011-09-12
You could add your user to the www-data group (or group which owns your /var/www folder and set the perms on /var/www to be 775.

Probably not a kosha method but a work around none the less...

---

### Post by Heeter on 2011-09-12
I have already tried to chmod the /var/www to 755 a couple of times, but still no go.

How do I add the user to the group?

If you can give me the proper command lines for it, that would be great.

Thanks


Heeter

---

### Post by cj13579 on 2011-09-12
```
sudo useradd -G www-data {username}
```

You will need to check that the group is actually "www-data".

```
sudo chmod 775 /var/www 
```

NOTE: This will only change the permissions for the /var/www folder but nothing below!

---

### Post by Heeter on 2011-09-12
> **cj13579 said:**
> ```
sudo useradd -G www-data {username}
```

You will need to check that the group is actually "www-data".

```
sudo chmod 775 /var/www 
```

NOTE: This will only change the permissions for the /var/www folder but nothing below!

Thanks for this,

Still getting errors, though.

How do I check the name of the group?

Thanks

Heeter

---

### Post by CharlesA on 2011-09-12
You can check the permissions via ls -l

Also: I recommend using sftp/scp instead of regular ftp. More secure since it's encrypted.

---

### Post by dudumomo on 2011-09-12
I strongly agree, SFTP will be a better solution than just FTP.
You could also use MySecureShell software to help you deal with that. (With a GUI or simple command line)
I'm using it and are quite satified with it. 
I just create a user without SSH account but with available space where I want.

But in your case, if you just want one user, yours. Well, just add your username to the www-data (after checking if it is the correct group with ls -l /var/ and check www) and after adding your user, set the correct permission to the folder (sudo chmod -R 775 /var/www for www and everything in it)
Note that you will need to logout and in after having added your username to the www-data group.

---

