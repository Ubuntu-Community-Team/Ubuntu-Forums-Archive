---
title: "OpenSSH Jail Issues"
date: 2010-05-01
forum: Server Platforms
---

### Post by SectorNine50 on 2010-05-01
Alrighty...  So I'm at the end of my rope here, and am extremely frustrated.

I have a web server running on Ubuntu Server and am using OpenSSH for all my SSH and sftp needs.  However, I have the strangest of all situations that I cannot for the life of me figure out.

I have a user chrooted to /var/www/username in /etc/ssh/sshd_config and in /etc/passwd.
When the user is chrooted to that folder, whenever I try to log in through SFTP using any client, I get an error saying "Network error: Software caused connection abort."

The kicker is, when I chroot the user to /var/www that user can log in just fine.  I've tried changing every chmod and chown setting I can think of, and I have NO idea why it matters by one folder.

I had the jail working perfectly for about 2 hours, when it seemingly just decided to stop...  What's really getting to me is why the two folders, which have the exact same settings, are not operating the same way...

Help... Please... lol

---

### Post by SectorNine50 on 2010-05-01
A bit of an update:

It seems my chroot jail is now completely broken.  No matter what I set ChrootDirectory to in the sshd_conf file, I can't log-in to the SFTP.  However, if I comment it away, then I can log in and the default folder is the home folder.  This wouldn't be a problem except that because it's not jailed, they can search through the entire computer and access folders I'd rather them not.

Any ideas?  I'm even open to starting from scratch at this point... :(

---

### Post by JPorter on 2010-06-11
Did you follow this guide?  [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

The sshd_config section given as an example in the guide works really well for group-level management with chrooted home directories named the same as the users, it uses "/home/%u" as the declaration for the group ChrootDirectory.


Double check that:
[LIST]
[*]root (user and group) owns the directory that you are chrooting (the user owns the subdirectories)
[*]in sshd_config, make sure the right sftp server is running...
[FONT="Courier New"]   Subsystem sftp internal-sftp[/FONT]
[*]restart sshd just to be sure?
[/LIST]

---

### Post by inphektion on 2010-06-12
> **SectorNine50 said:**
> A bit of an update:

It seems my chroot jail is now completely broken.  No matter what I set ChrootDirectory to in the sshd_conf file, I can't log-in to the SFTP.  However, if I comment it away, then I can log in and the default folder is the home folder.  This wouldn't be a problem except that because it's not jailed, they can search through the entire computer and access folders I'd rather them not.

Any ideas?  I'm even open to starting from scratch at this point... :(

one thing to check... you haven't said what ubuntu server you are on.  I know my hardy servers don't have the version of openssh that enable using chrootdirectory.  So i had to implement sftp chroots with scponly.  
So what ubuntu server is this and what version of openssh do you have?

---

### Post by JPorter on 2010-06-13
^^ What he said... I didn't even consider that you might be using an older version.

---

