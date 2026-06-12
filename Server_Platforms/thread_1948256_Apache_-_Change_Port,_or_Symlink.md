---
title: "Apache - Change Port, or Symlink?"
date: 2012-03-28
forum: Server Platforms
---

### Post by Roasted on 2012-03-28
I have a unique situation here that will likely make some people wonder why I'm doing this, but there's always a method to the madness.

I have a spare desktop. Pentium Dual Core, 2 GB ram, nothing to write home about. It has two SATA ports. I decided to re-utilize it as a sort of backup server, as it's very low powered versus my desktop (which runs its own RAID array, but is quite a hog on the wattage meter vs this spare desktop).

Of course, I wanted to utilize RAID in this desktop, so I'm running a pair of 500 GB drives in software RAID. Err, wait. Two SATA ports, two drives, where's the OS? The OS is installed neatly on a little flash drive... Considering Apache defaults to /var/www, that of course limits me to the space I can host.

Is there a way I can change the default path of Apache? My array is mounted at /media/NAS, and inside are folders to the users in the house hold, followed by the type of computer/OS they are.

/media/NAS/jason/DesktopUbuntu
/media/NAS/jason/LaptopUbuntu
etc...

But I'd like to have a /media/NAS/public to serve the same purpose as the typical /var/www...

Is there a way to re-route the path? Or is that too involved to really change?

The other idea somebody suggested was to do some sort of symlink. That's great but in my practice, it didn't work. If I symlink /media/NAS/public to /var/www (or vice versa) and drop a file in /media/NAS/public, it also copies that file to /var/www/folder, which of course negates the whole idea since I'm severely limited on space there.

SO... having the whole story out on the table and you folks knowing my plan of action, what say you? 

Thanks much!

---

### Post by volkswagner on 2012-03-28
Changing the default directory for Apache2 is simple.

```
sudo nano /etc/apache2/sites-available/default

```

You will want to change a couple settings here:

```
DocumentRoot /var/www
```
and
```
<Directory /var/www/>
```

Change to:

```
DocumentRoot /media/NAS/public
```
and
```
<Directory /media/NAS/public/>

```

You will also need to make sure apache has permission to serve those files.  Apache2 runs as www-data.

Or you will need to make sure files are world readable.

Then restart apache

```
sudo service apache2 restart
```

---

