---
title: "[SOLVED] How to allow an existing user to edit any file on the server via FTP"
date: 2008-04-11
forum: Server Platforms
---

### Post by max.goedjen on 2008-04-11
Hi guys,
OK, so I've gone and set up an FTP server(vsftpd specifically), and I've already got an existing user in the system. What I'd like to do is set that user to be able to edit the ENTIRE filesystem via ftp, as an alternative to CLI. How would I do that? Would it be best to mess around with file permissions via chmod, or mess with user settings(setting home directory to /)?

Thanks,
Max

---

### Post by mrsteveman1 on 2008-04-11
By default an FTP user can see the entire filesystem anyway unless you have that user chroot'd, which isnt the case unless you go way out of your way to set that up.

As long as the user is part of the admin group they should be able to edit whatever they want.

---

### Post by songshu on 2008-04-11
uhm,

interesting idea, the entire file system?

you could let vsftpd itself run as root and allow for anonymous log in, but i would have to say 
WARNING WARNING WARNING SECURITY RISK <DISASTER HAPPENING SOON>

but since you are root i will leave that choice to you and assume you know what you are doing.

---

### Post by netlogic on 2008-04-11
> **mrsteveman1 said:**
> By default an FTP user can see the entire filesystem anyway unless you have that user chroot'd, which isnt the case unless you go way out of your way to set that up.

As long as the user is part of the admin group they should be able to edit whatever they want.

I don't recommend it. It can be easily hacked if someone has enough knowledge to knock down your DNS server. If this has to be done, add root user, allow root login through FTP, FORCE SSL for ftp and ftp data, use pamd, chroot local users (chroot_local_user=YES) and add root to vsftpd.chroot_list. Also, add chroot_list_file=/etc/vsftpd.chroot_list to vsftpd.conf file.

---

### Post by mrsteveman1 on 2008-04-11
You know, it might be better to just allow the user to login with sftp or scp, since neither of those require running an FTP server of any kind, and openssh can handle them both out of the box.

That way, any user who has permissions locally has permissions remotely. There are a number of good sftp clients, on windows winscp is a good one.

---

### Post by max.goedjen on 2008-04-11
I AM using sftp currently(Transmit on OSX as the client). However, currently I can only edit my home directory. I'd like to use this as an alternative to using the shell to edit my directory structure. How would I edit an existing user to allow this? Should I basically just log in as root(I know enough to not mess things up too much, and this server is isolated enough to not constitute a security risk.

---

### Post by mrsteveman1 on 2008-04-11
I believe on OS X you can just add the user to the admin group

---

### Post by netlogic on 2008-04-11
> **mrsteveman1 said:**
> I believe on OS X you can just add the user to the admin group

I don't want to be rude, but OSX's security is only a bit better than XP. I would never in my life will run OSX based server. That is like running apache on xp. Yes, I have used OS 7 to 10 in the past.

---

### Post by songshu on 2008-04-11
> **netlogic said:**
> I don't want to be rude, but OSX's security is only a bit better than XP. I would never in my life will run OSX based server. That is like running apache on xp. Yes, I have used OS 7 to 10 in the past.

there is nothing wrong with xp running apache if its in a "safe" location.

and lets be rude ;)
how many ubuntu server admins on this forum who load up a full desktop with the restricted extras actually know what to do with ip tables?

not that i'm running XP anywhere cause i find it to hard to configure but i actually know people who do

---

### Post by max.goedjen on 2008-04-11
Think you're misunderstanding me. I'm logging into a Ubuntu server, using Transmit(and thus, OSX) as my ftp CLIENT. I'm trying to set up the server part. What I'm trying to do is set it up so that I can administrate the filesystem on the Ubuntu box from OSX, over SFTP.

---

### Post by mrsteveman1 on 2008-04-11
Yea i misread the OS X part.

So its an ubuntu local user you want to have access to the entire filesystem. You can just add that user to the root group by putting the users name at the very end of the root line it in /etc/group like this:

> root : x : 0 : user

I put spaces between the characters because the forum turns them into smily faces. This is slightly insecure but only if someone manages to log in as this user.

btw, XP security is a joke (botnets....), and no one uses it to host websites, ever. Comparing it to OS X though is funny, OS X is much more secure.

---

### Post by max.goedjen on 2008-04-11
I've used linux for years hosting websites, though never directly administrating those servers. I'm setting up this server for internal development(SVN, trac, code testing, etc), so I'm still learning my way around. 
Adding my name to the end of the root line didn't really seem to work. I've restarted the box, and just as before, when I sftp into it, and try to make a file/directory outside of my home folder, I get a permissions error. Thoughts?

---

### Post by mrsteveman1 on 2008-04-11
If that didn't work I'm not sure what the problem is, perhaps you need to also add this user to the admin group?

---

### Post by max.goedjen on 2008-04-11
It was the account I set up Ubuntu with, so wouldn't it already be?

---

### Post by mrsteveman1 on 2008-04-11
It should be, yes. If thats the case, that this user is part of both the admin and root groups, it should have access to every file on the system. 

I seem to remember i used to login as root with sftp anyway, its not insecure as long as the password is strong.

---

### Post by netlogic on 2008-04-11
look into /etc/pam.d/vsftpd and /etc/ftpusers

---

### Post by max.goedjen on 2008-04-11
> **mrsteveman1 said:**
> It should be, yes. If thats the case, that this user is part of both the admin and root groups, it should have access to every file on the system. 

I seem to remember i used to login as root with sftp anyway, its not insecure as long as the password is strong.

Yeah, I've got a good password, that's probably what I'll do. I'm able to do what I want with this, I tried it.

Thanks for your help everyone!

---

### Post by mrsteveman1 on 2008-04-11
> look into /etc/pam.d/vsftpd and /etc/ftpusers

those only apply if you are using actual ftp, sftp runs through openssh entirely, so posix permissions already apply.

---

### Post by netlogic on 2008-04-11
> **mrsteveman1 said:**
> those only apply if you are using actual ftp, sftp runs through openssh entirely, so posix permissions already apply.

No kidding. He said he wanted run FTPs, not SFTP.

---

### Post by max.goedjen on 2008-04-11
This was in error. I, for some reason or another, was getting SFTP and FTP with SSL mixed up.

---

### Post by netlogic on 2008-04-11
> **max.goedjen said:**
> This was in error. I, for some reason or another, was getting SFTP and FTP with SSL mixed up.


Ah... They are totally different thing. It is easy to get confused.

---

