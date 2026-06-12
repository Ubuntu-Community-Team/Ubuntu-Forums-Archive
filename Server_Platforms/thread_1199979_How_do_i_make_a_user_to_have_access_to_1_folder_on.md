---
title: "How do i make a user to have access to 1 folder only"
date: 2009-06-29
forum: Server Platforms
---

### Post by jargen on 2009-06-29
i'm making a few users for some of my friends to use but i want them to only have access to 1 certain folder. I tried making a normal user but it could access alot of files.

Im using Ubuntu Server 9

---

### Post by lightnb on 2009-06-29
Are they logging in to the local machine? Or accessing the folder remotely via FTP/SSH/Samba?

---

### Post by jargen on 2009-06-29
they will be accesing it via ssh

---

### Post by lightnb on 2009-06-29
I believe that read-access to many system files/folders is required to login and use the system successfully.

It would be easier if there were certain folders you wanted to hide, rather than trying to hide *everything*. Could you provide more details of what your trying to accomplish? There may be a better way to keep sensitive data safe...

If you want to prevent someone from seeing a file or folder, set the world-readable value to zero with chmod, and make sure the user is not the owner, or in the group for the given file.

example:
```

chmod 700 /home/MyUserName
chown MyUserName:MyUserName /home/MyUserName

```

...would make your home folder only accessible to you. Be carefull with this though, as preventing read access to some files may cripple your system.

---

### Post by jargen on 2009-06-29
well what i intend to do is make a folder on the apache folder /var/www/ so they have their own folder  /var/www/username but i dont want the users to be able to see other peoples folder eg /var/www/craig cant  see /var/www/jake and vise versa and it would be good if they cant see the system files either so their limited to just their own folder

so if someone named jake had a account they could only access and add files to /var/www/jake and nothing else if thats possible

---

### Post by Iowan on 2009-06-29
Another option is to set up the directory in their /home directory.  More details [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts").

---

### Post by capscrew on 2009-06-29
What you are trying to do is called "chroot jail".

See here: [**_https://help.ubuntu.com/community/BasicChroot_**]("https://help.ubuntu.com/community/BasicChroot")

Here is a Google [**_search_**]("http://www.google.com/search?hl=en&q=chroot+%2Bjail+%2Bubuntu+%2B+howto&aq=f&oq=&aqi=") on the term.

---

### Post by jargen on 2009-06-30
> **capscrew said:**
> What you are trying to do is called "chroot jail".

See here: [**_https://help.ubuntu.com/community/BasicChroot_**]("https://help.ubuntu.com/community/BasicChroot")

Here is a Google [**_search_**]("http://www.google.com/search?hl=en&q=chroot+%2Bjail+%2Bubuntu+%2B+howto&aq=f&oq=&aqi=") on the term.


yeah but how do i manage to make that work for specific users that seems to be for applications

---

### Post by jargen on 2009-06-30
anyone got any ideas? i need this pretty urgently

---

### Post by lightnb on 2009-06-30
I would use the home folder setup.

Each user has a home folder, with a sub-folder "www".

You would then create a Virtual Host for the domains, and point each domain to that user's web directory under home.

Then, "chmod 700 /home/User" their home folder, so that only that user can read it. You may want/need to make www-data the group, and give the group read access so that Apache can get to the files as well.

Example:
chmod 750 /home/User
chown UserName:www-data /home/User/www

The user can read and write to their own folder, apache can read and execute files, and no one else can see anything in that users folder.

Any files that contain passwords, SSL certs, etc can be chmoded to 000 (Root access only). (Assuming they don't need to be accessed by any other processes. OR make the file owned by the processes' user (www-data for apache, dovecot for mail server config files, etc). then chmod 400 them.

Users will still be able to browse system files, but if they are not the owner, they won't be able to make changes. If you want to hide configuration files, just make them "owned" via chown to their respective process user and set the world readable option to 0. ie. chmod 400.

---

### Post by dtoronto on 2009-06-30
If you are using vsftpd for your ftp server you need to uncomment the file that jails users to their directory (chroot=yes)  You can then create users and with a home directory that only they can access.

---

