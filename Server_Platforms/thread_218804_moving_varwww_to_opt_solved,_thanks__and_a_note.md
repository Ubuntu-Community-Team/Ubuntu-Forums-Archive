---
title: "moving /var/www to /opt: solved, thanks  and a note"
date: 2006-07-19
forum: Server Platforms
---

### Post by eeried on 2006-07-19
Hello,

Thanks to this thread : [ Changing /var/www to /media/hda5/www]("http://www.ubuntuforums.org/showthread.php?t=207665&page=1&highlight=www")
I was able to move my Document Root to /opt/www. Many thanks to Randomskk for this very helpful tip that I'd been searching for for quite a while. I have a separate /opt partition.

I don't use LAMP as a server really only as a **local** server to test a few CMS and a couple of websites created with them.

I just want to add this:

I changed the name of my localhost (name of my computer) to "localhost" etc/apache2/sites-available/default as explained in the mentioned thread but then Gftp wouldn't run. I removed the "ServerName" line and ran hostname my_computer_name and restarted Apache. Gftp liked the change and ran happily!

What I mean by the computer name is the name you can change when you install Ubuntu. By default the name is "ubuntu".

Still, I can access my local website by typing in Firefox URI bar : [http://localhost/dir_name/](http://localhost/dir_name/)

Of course if I reinstall Ubuntu I'll lose my mysql data bases, I suppose? Even if I save them I'll still have to create new ones again.

---

### Post by Randomskk on 2006-07-19
You can export the data in the MySQL database.
There's a tool to do it manually, but I'd advise installing backup-manager and then editing /etc/backup-manager.conf (I think that's it, might be in it's own sub folder) to configure it.
Create an account that can SELECT any data, and give that account to the backup tool. That way, the backup tool will create a backup of all your MySQL data (and the rest of your website / server if you wish), which you can easily move to another MySQL server.
Also, the backup tool can upload these backups to another FTP server, in case you want remote backups.

---

