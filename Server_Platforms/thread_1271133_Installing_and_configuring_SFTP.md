---
title: "Installing and configuring SFTP"
date: 2009-09-20
forum: Server Platforms
---

### Post by bacterozoid on 2009-09-20
Let me preface this by saying that I'm by no means an expert at this. I've had on and off Linux experience, that's all.

I've got Ubuntu Server 9.04 up and running. It works fine. I've installed openssh and can SSH from my mac without any trouble.

I'd like to get SFTP set up somehow, though. I can use filezilla and SFTP right now because I've installed openssh, but I want to have an FTP user configured so that, when they connect, they are taken to /var/www, and not the home directory.

At the moment when I use SFTP I don't have any permissions outside the home directory.

---

### Post by Bachstelze on 2009-09-20
/var/www is the home directory of the www-data user. Setting it as the home directory of an additional user could be a bad idea depending on your setup.

Using FileZilla's Site Manager, you can specify a directory to which FZ will automatically change on startup (in the "Advanced" tab, under "Default remote directory"). Just set it to /var/www for your normal account.

To set permissions on /var/www, just use chown and chmod so your account has write access to it. TYhere are plenty of guides explaining how UNIX permissions work.

---

### Post by bacterozoid on 2009-09-20
Instead of making it the home directory, I want my ftp user to ONLY have access to /var/www (and their home directory, if it's not possible to restrict that). Is it not more secure this way, should that user become compromised?

---

### Post by hessiess on 2009-09-20
> **bacterozoid said:**
> Instead of making it the home directory, I want my ftp user to ONLY have access to /var/www (and their home directory). Is it not more secure this way, should that user become compromised?

the only wat to do that is using a chroot jail, which is rather complex to configure,  its easier to just create another user with the home dir set to /var/www and use file permissions to prevent the user writing anywhere else.

Idealy you would also want to get apache running as the same user with mpm-itk and create virtual hosts for every website with there own user, blocking one user from accessing any outher sites, but this is also quite complicated to set up.

---

### Post by Bachstelze on 2009-09-20
> **bacterozoid said:**
> Instead of making it the home directory, I want my ftp user to ONLY have access to /var/www (and their home directory, if it's not possible to restrict that). Is it not more secure this way, should that user become compromised?

Then just install a FTP server with SSL encryption, restict the user in question to his home dir and bind-mount /var/www to a subdir of it, for example /home/username/www.

---

### Post by bacterozoid on 2009-09-20
I wasn't interested in messing with chroot jail and I'd rather just use what I have rather than trying to install an FTP server (I had trouble with proftpd).

Bach, I took your suggestion and used chown to get permission to the /var/www directory. It looks like the default permissions only allow me inside my home directory, anyways, so I'm good there.

Thanks for your help!

---

