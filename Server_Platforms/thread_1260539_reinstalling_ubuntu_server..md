---
title: "reinstalling ubuntu server."
date: 2009-09-07
forum: Server Platforms
---

### Post by hockey97 on 2009-09-07
Hi, I am going to reinstall ubuntu since I messed up the permissions of all files so I have no bootable system.

I am currently making backups. 

I want to know what backups I need for apache,mysql,bind, and webmin. I use webmin to admin my servers threw webmin. 

Also how can I backup datatables already created by mysql?

I also want to backup postfix. 

do I just need to backup the configs that's in /etc/ ?

---

### Post by windependence on 2009-09-07
Why not just boot a live disc and fix your perms? Mount your filesystem under /mnt, and then chmod them to 755 to get going, then reboot. Once you are in you can fix the perms to the correct permissions.

If you can't do this, then you need to do an SQL dump, back up your apache root directory, and your bind configuration. You probably don't even need to run a DNS server unless you have tons of machines on your local network. This is a good expample of where command line knowlege would come in real handy.

-Tim

---

### Post by LepeKaname on 2009-09-07
Apache:

1. Backup your web files (usually in /var/www)
2. Backup /etc/apache2/*
3. Backup /etc/php5/apache2/php.ini

MySQL:

1. Dump to sql:  mysqldump -u root -p --all-databases -r alldata.sql (check mysqldump documentation)
2. Shutdown mysql and backup: /var/lib/mysql/* . You can restore them only copying them to the new location.

Postfix:

1. Backup /etc/postfix/*
2. Depending on your configuration backup other config files as well (like Dovecot, Spamassassin, ClamAV, etc...)

If you have a second drive/partition I recommend you to install the new Ubuntu server to that drive. That way, you can mount your old drive and be able to retrieve all your data without having to go with a full backup and you would not loose important information/setups. Start copying the files you need in your new drive and once you have all working, you can delete the old drive.

Good luck

---

