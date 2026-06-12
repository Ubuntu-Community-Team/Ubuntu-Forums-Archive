---
title: "drive in another folder"
date: 2010-04-28
forum: Server Platforms
---

### Post by blakep2 on 2010-04-28
I have a website and I have a upload form and I store pictures.  When the pictures are saved they go to the drive on the server.  The disk space is not very big on this server.  I was wondering if i could attach a external hard drive and figure out a way to get the files to upload and be retrieved from there.  I would like to do this through the document root of the web server file.  If this is not possible could I do a subdomain like this XXXxx.XXX.com with the document root of that being the external hard drive location.  or any other ideas you have.

---

### Post by cdenley on 2010-04-28
You can have apache serve files from your external drive by changing the default site's DocumentRoot, creating an alias in your default site, or creating a new site with a subdomain (depending on your DNS configuration). Once you decide what you want to do, maybe someone can point you in the right direction. First step, though, is to get a filesystem on your external drive mounted.

---

### Post by blakep2 on 2010-04-28
i have the drive mounted and i would like to use the subdomain method

---

### Post by cdenley on 2010-04-28
I trust you mounted it correctly so the user www-data the required permissions. First, your subdomain has to resolve to the correct IP address. You haven't told me anything about your DNS configuration, so I can't help with that. This is how you configure apache, though.
```

cd /etc/init.d/apache2/sites-available
sudo cp default subdomain
sudo nano subdomain

```
If there is a line like "NameVirtualHost *" at the top, remove it. After the "<VirtualHost *>" tag, add the line "ServerName subdomain.mydomain.com". Edit the "DocumentRoot" line and the "Directory" tag, replacing "/var/www" with your new DocumentRoot. CTRL+X to save.
```

sudo a2ensite subdomain
sudo /etc/init.d/apache2 reload

```

---

### Post by blakep2 on 2010-04-28
> **cdenley said:**
> I trust you mounted it correctly so the user www-data the required permissions. First, your subdomain has to resolve to the correct IP address. You haven't told me anything about your DNS configuration, so I can't help with that. This is how you configure apache, though.
```

cd /etc/init.d/apache2/sites-available
sudo cp default subdomain
sudo nano subdomain

```
If there is a line like "NameVirtualHost *" at the top, remove it. After the "<VirtualHost *>" tag, add the line "ServerName subdomain.mydomain.com". Edit the "DocumentRoot" line and the "Directory" tag, replacing "/var/www" with your new DocumentRoot. CTRL+X to save.
```

sudo a2ensite subdomain
sudo /etc/init.d/apache2 reload

```
the 80 port is forwarded through my router to the local ip of the machine serving the main page.  Also what are the user www-data required permissions.

---

### Post by cdenley on 2010-04-28
> **blakep2 said:**
> the 80 port is forwarded through my router to the local ip of the machine serving the main page.

I assumed as much. Port forwarding isn't related to DNS or subdomains.
> **blakep2 said:**
> 
Also what are the user www-data required permissions.
You tell me. You mentioned uploading. If you expect apache to write files to the directory, then www-data needs write permission. If you expect apache to read and serve files in that directory, then www-data needs read permission. How to set the permissions depends on the filesystem you're using.

---

### Post by blakep2 on 2010-04-28
> **cdenley said:**
> I assumed as much. Port forwarding isn't related to DNS or subdomains.

You tell me. You mentioned uploading. If you expect apache to write files to the directory, then www-data needs write permission. If you expect apache to read and serve files in that directory, then www-data needs read permission. How to set the permissions depends on the filesystem you're using.
{
Forbidden

You don't have permission to access /index.html on this server.
}
i get this when i pull up the index.html file i just created for that subdomain.
where can i learn how to set the www-data permissions

---

### Post by blakep2 on 2010-04-28
for some reason it is not letting me change the ownership

---

### Post by cdenley on 2010-04-28
You never said what type of filesystem the files are on.
> **cdenley said:**
> How to set the permissions depends on the filesystem you're using.

Since you can't change ownership, I'm guessing FAT32 or NTFS? If that is the case, you need to use mount options to set the permissions. How are you mounting the filesystem?

---

### Post by blakep2 on 2010-04-28
> **cdenley said:**
> You never said what type of filesystem the files are on.


Since you can't change ownership, I'm guessing FAT32 or NTFS? If that is the case, you need to use mount options to set the permissions. How are you mounting the filesystem?
I am using ntfs, where are the mount options, I right clicked on the folder and when i tried to change anything to www-data it either replied do not have permissions necessary or can not be done or something like that

---

### Post by cdenley on 2010-04-28
> **blakep2 said:**
> I am using ntfs, where are the mount options, I right clicked on the folder and when i tried to change anything to www-data it either replied do not have permissions necessary or can not be done or something like that

So you have gnome installed, and you're using nautilus to mount the filesystem then? I don't know how to change the mount options nautilus uses in recent versions of ubuntu. Besides, mounts for files apache is serving should be configured in /etc/fstab so they are mounted before apache is started at boot.

[https://help.ubuntu.com/community/MountingWindowsPartitions#Manual%20Configuration](https://help.ubuntu.com/community/MountingWindowsPartitions#Manual%20Configuration)
```

/path/to/filesystem /media/mountpoint ntfs-3g defaults,locale=en_US.utf8,**fmask=111,dmask=000** 0 0

```
This will give everyone read and write access, including www-data.
```

man mount.ntfs-3g

```

---

