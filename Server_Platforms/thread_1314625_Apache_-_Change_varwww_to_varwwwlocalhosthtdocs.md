---
title: "Apache - Change /var/www to /var/www/localhost/htdocs"
date: 2009-11-04
forum: Server Platforms
---

### Post by roundhay on 2009-11-04
I read this article in Linux Format earlier this year and as I am about to set up a new server install I would like to hear opinions on whether or not it is worth changing the default file structure as detailed in the article?

I'm not an expert in this area but like the idea of making my server as secure as I can.

Edit: It would help if I posted a link to the article!

[http://www.tuxradar.com/content/how-set-web-server-apache](http://www.tuxradar.com/content/how-set-web-server-apache)

---

### Post by Iowan on 2009-11-04
My standard (favorite?) [link]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") has a section on Virtual Hosts - which includes using a different default site.

---

### Post by GCoffee on 2009-11-06
I cannot see any benefits to changing the directory that much.

I know I have used symbolic links for subdirectories occassionally so I can lock a user to their home directory in FTP and still let them acces via web (didnt want them to get into other files in the web root.)

---

### Post by Lars Noodén on 2009-11-07
> **roundhay said:**
> I read this article in Linux Format earlier this year and as I am about to set up a new server install I would like to hear opinions on whether or not it is worth changing the default file structure as detailed in the article?

I'm not an expert in this area but like the idea of making my server as secure as I can.

Edit: It would help if I posted a link to the article!

[http://www.tuxradar.com/content/how-set-web-server-apache](http://www.tuxradar.com/content/how-set-web-server-apache)

If you have several virtual hosts and want to chroot SFTP access to them, yet allow the chrooted users to have some access to logs and such, then that is a way to go.  SFTP clients include the built-in sftp, the GUI Filezilla, PuTTy's PSFTP and Pageant, or Fugu, etc.  

  
```

# from /etc/ssh/sshd_config

# vhost A
Match Group vhost1devel
  ChrootDirectory /var/www/vhost1
  ForceCommand internal-sftp

Match Group vhost1authors
  ChrootDirectory /var/www/vhost1/htdocs
  ForceCommand internal-sftp

# vhost B, require key authentication for this vhost
Match Group vhost2devel
  ChrootDirectory /var/www/vhost2
  ForceCommand internal-sftp
  PasswordAuthentication no

Match Group vhost2authors
  ChrootDirectory /var/www/vhost2/htdocs
  ForceCommand internal-sftp
  PasswordAuthentication no

# everyone else
Match Group !admin, Group !ejanitors
   ChrootDirectory /var/www
   ForceCommand internal-sftp


```

With the above, you could have those in the developers' group access documents, logs, scripts, while the authors only access the documents.

Something missing from the article is the practice of using a separate directory for images and icons.  Doing that allows you to turn of scanning for Server-Side Includes (SSI) or PHP if you are using PHP or [HTML::Mason](http://www.masonhq.com/) if you are using Perl.  There's no point in the server rummaging through a 1MB jpeg looking for scripts and includes that aren't there.

Another thing missing from the article is the use of ACLs for that file system.  If you put /var/www/ in a separate partition, then you can adjust mount options, such as ACLs, to suit www work.  ACLs give you better control and more flexibility over group permissions.  A second advantage to having /var/www in its own partition is that it won't compete with /tmp, /var/tmp and /var/log for space.  If all 4 are on the same partition, then someone could create a denial of service attack accidentally or on purpose by filling /var/www up so that there is no space on the others.  If /var/www is separate then it does not matter, as far as the operating system is concerned, if it is full.

---

