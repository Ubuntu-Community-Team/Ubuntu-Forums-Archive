---
title: "Moving Files from Win to LAMP"
date: 2006-07-19
forum: Server Platforms
---

### Post by uncleclinto on 2006-07-19
Okay Peeps,

Thanks to Azz, Fred, and several others, I set up Ubuntu on my new (used) P3 box last night.  I also used aptitude install "apache2 php5-mysql libapache2-mod-php5 mysql-server" on my desktop installation. I can see my VAR/www folder.  Now I need to make the big move.  My website is currently sitting on a WAMP box and needs to be moved.  I also use Macromedia Studio on a Win2k box for design and development.  

Am I better to set up an ftp program for this or use something like Samba for windows networking?  Does Samba have a GUI, or is it simply command line?

I am in the process of reconciling several manuals and tutorials on this stuff, and am simply confused.

I also keep getting stuff about EtherApe.  Does it even network with Windows?  

so confused....  ](*,)

---

### Post by Kurt` on 2006-07-19
I recommend Samba.

[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

That guide is pretty simple and relatively straightforward, but read it carefully!

Create a user, and set a password for him. Then create a share to your /var/www directory.

Then from your Windows machine, go to My Network Places (from the start menu, or My Computer), and you will be able to login to the share. Then just drag and drop all your files over.

The share will need to be writable however.

With this method, you can edit the files on your Ubuntu machine using a text editor/development program on your Windows machine. ;) No more copying files over, just create them in your editor and save across the network.

---

### Post by uncleclinto on 2006-07-19
Cool...  I also have a backup of a MySQL database that will need to be moved to the new server.  Where do I put that??

:-k

---

### Post by Kurt` on 2006-07-19
> **uncleclinto said:**
> Cool...  I also have a backup of a MySQL database that will need to be moved to the new server.  Where do I put that??

:-k

Put it anywhere on the server, then run the following command:

# mysql -p -h DBSERVER dbname < dbname.sql

Where dbname is the desired database name. and dbname.sql is the path to your backup file. (You'll be promped for the root mysql password).

---

### Post by uncleclinto on 2006-07-19
rock!  That's pretty logical...  Thanks!

Helluvalot easier than DOS!

---

### Post by foxylad on 2006-07-20
If you are only doing this once, just install ssh and use winscp - it is a Windows secure ftp client, and will allow you to transfer files to and fro easily.

---

