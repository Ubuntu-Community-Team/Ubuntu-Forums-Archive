---
title: "Multiple SSH/SFTP Users with SSH Key Pairing Setup"
date: 2016-10-19
forum: Server Platforms
---

### Post by thomo2710 on 2016-10-19
Hi,

Fairly new to Linux, been a Windows sheep for what seems forever! :)

Im setting up a 16.04 Ubuntu webserver to host a few websites.

I have setup SSH key Pairing and disabled password login for SSH/SFTP connections for my main server user account that i use to admin the server.

1 of the website owners likes to manage his own site and needs SSH/SFTP access to it.

Do i just create a new user account on the server and configure SSH key Pairing for that particualr user account so they can connect as that user and no the main server admin account? Creating a new public/private key pair for that user thats completely different to the main server admin keypair?

And then lock down access to just their home directory and their website directory?

Thanks

---

### Post by SeijiSensei on 2016-10-19
Yes, you can give each user a keypair.

As for locking down their access, that's a bit trickier.  You might look into creating "[chroot jails]("http://allanfeid.com/content/creating-chroot-jail-ssh-access")" for them.  Basically you create a little sandbox with copies of the necessary files from places like /lib and /usr.  When they log in, they can see only the files in the jail and cannot navigate out to the actual filesystem.

---

### Post by Habitual on 2016-10-19
> **SeijiSensei said:**
> Yes, you can give each user a keypair.

As for locking down their access, that's a bit trickier.  You might look into creating "[chroot jails]("http://allanfeid.com/content/creating-chroot-jail-ssh-access")" for them.  Basically you create a little sandbox with copies of the necessary files from places like /lib and /usr.  When they log in, they can see only the files in the jail and cannot navigate out to the actual filesystem.
(Remote) user wants to edit /var/www/html/ ?

I make keys and stick them in place.
If the "user" has more knowledge on Linux than yourself, you may very well have to allow him.
But it doesn't have to be scary.
As a rule in my shop, I don't allow "users" to edit DocumentRoot.
But either case, I'd create the key and stick it in place, then test it in place.
Then deliver to the "user".

Strong keys:
```
ssh-keygen -f /path/to/file_rsa -t rsa -N '' -b 4096 -q
```
and contents of /path/to/file_rsa.pub go on the target server.

---

### Post by SeijiSensei on 2016-10-19
Why would the user need to edit /var/www/html?  I put all my virtual hosts in directories under /home and point the DocumentRoot accordingly.  I rarely if ever put anything in /var/www/html and just leave the default Ubuntu page there.  As long as the DocumentRoot directory is visible from both within the jail and from the actual filesystem, I don't see a problem.  

I run BIND in a chroot jail which is pretty simple to do with RHEL/CentOS systems.  The named process is bound to /var/named/chroot and cannot see anything above that.  I, of course, can see all the files below /var/named/chroot when logged in as the root user.

---

