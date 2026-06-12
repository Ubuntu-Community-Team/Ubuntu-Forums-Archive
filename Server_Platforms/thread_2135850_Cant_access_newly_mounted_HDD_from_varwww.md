---
title: "Cant access newly mounted HDD from /var/www"
date: 2013-04-15
forum: Server Platforms
---

### Post by apatheticrory on 2013-04-15
Hi,

i'll start with a quick rundown of what i'm running. i set up Ubuntu Server 12.10 and have been using it as a web server. I created a simple website and have been throwing some media on there to stream around the house. it's been working great but i ran out of space on the only hdd installed. 

i've since mounted a new drive, named data1 in the /media - worked fine; i can upload/delete etc - but when i try to create a link on the website it's telling me that it can't find the directory /media/data1/example.mp4

could someone help? it's driving me crazy.

also read somewhere that i shouldn't be hosting data in the var/www directory at all, which would't be a problem if i could access the /media folder from the website. 

sorry if this makes no sense

Thanks, Guys

---

### Post by darkod on 2013-04-15
Did you make an entry in fstab so that it mounts /media/data1 on every boot?

What do you mean by link on the website, is it literary some form on a webpage or what? I don't think a website would know what /media/data1 is. The filesystem knows that, but a webpage doesn't.

You probably should have used LVM when you installed the server so that you can add more physical disks but use the new space in the existing mount points (LVs). There is no problem using /var/www as long as you have enough space in it.

Alternatively, I guess you need to modify the website configuration in apache to change the document root/folder.

---

### Post by apatheticrory on 2013-04-15
Thanks for replying! 

I quite like the idea of having a separate hard drive for all the data I'm storing, so if anything was to go wrong with the system I could easy save the data. 

Sorry not to have made the website thing clear. I've put a very simple HTML webpage in var/WWW and put simple links to the files so I can access them from loads of different devices while at home. Saves throwing hard drive from machine to machine. 

So when I added the new one, I expected it to work the same but the link would be different. I.e /media/disk1/example.mp4 instead of /var/WWW/example.mp4

How would I make an entry on fstab?

---

### Post by darkod on 2013-04-15
Assuming the partition on the second disk is /dev/sdb1 for example, and that the filesystem you used is ext4, you would need to add a new line in /etc/fstab saying:
```
/dev/sdb1   /media/data1   ext4   defaults   0   2
```

Note that while you can use /media it is usually better to use another mount point. You can create it yourself, as you want. For example, you can create a folder /data1 and use it as mount point in fstab:
```
sudo mkdir /data1
```

You will also need to set correct permissions depending how you plan to use the folder.

---

### Post by apatheticrory on 2013-04-15
Thank you, that worked and the drive is mounted and i have full permissions...i think. i can add to the folder, delete etc but i just can't seem to access it at all using my browser. 

currently using the internal ip 192.168.0.2 which gives me access to everything within the /var/www (which is on the system disk) but i assumed that typing 192.168.0.2/data1 would take me to that directory. sadly not :(

thanks for your help, Darkod

---

### Post by steeldriver on 2013-04-15
I'm not a webserver guy but if you're trying to serve pages from somewhere other than the default 'DocumentRoot' (i.e. /var/www) then afaik you need to do one of the following things:

1. actually mount your external partition at the default DocumentRoot location /var/www instead of /media/data

2. bind-mount or symlink your /media/data to /var/www

3. modify your /etc/apache2/sites-available/default file to point to your alternative location

4. add a new /etc/apache2/sites-available/whatever and run a2ensite to enable it

I don't know which approach is considered 'best practice' or if there are security implications of one versus the others. Option (1) is kind of old school. Option (4) is more appropriate for multiple 'virtual servers' where you have different domains or subdomains, I think. I just tried (3) on my little play server i.e.

```
 sudo mkdir -p /data/mysite

sudo mv /var/www/* /data/mysite/

sudo nano /etc/apache2/sites-available/default
```

changing both occurrences of /var/www to /data/mysite 

```
$ cat /etc/apache2/sites-available/default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        [COLOR=#ff0000]**DocumentRoot /data/mysite**[/COLOR]
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        [COLOR=#ff0000]**<Directory /data/mysite>**[/COLOR]
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

and then restarting apache2

```
sudo service apache2 restart
```

This seems to work. FWIW I wouldn't use /media/whatever since /media is kind of 'reserved' for the system to automount stuff - I'd suggest /data or /storage or somesuch.

---

### Post by darkod on 2013-04-16
Like steeldriver I'm not a webserver guy myself. What he said is what I think too. The location /media/data1 (or which ever mount point you chose) is not used automatically. And web pages can't use anything outside the document root in my opinion too.

As for the availability of 192.168.0.2/sharename that is more like a samba share, than web share. But if you go with samba it would be accessible only from the local LAN. On the other hand, 192.168.0.2 is also accessible only from the local LAN unless you have port forwarding on your internet router.

It depends what you want to do with this. If this is only for LAN sharing, samba is probably the best option.

If you want to access it from the internet too, from outside your network, then i guess the web page is a better choice but you have to make the necessary adjustments so that it uses the location. Another separate web page with the document root poiting to your new mount point, or something similar.

---

### Post by apatheticrory on 2013-04-16
Thanks, guys. will try it out today and let you know....

---

