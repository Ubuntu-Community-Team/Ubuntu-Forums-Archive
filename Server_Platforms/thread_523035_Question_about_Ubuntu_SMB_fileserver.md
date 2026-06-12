---
title: "Question about Ubuntu SMB fileserver"
date: 2007-08-11
forum: Server Platforms
---

### Post by donaldvr on 2007-08-11
I work for a school with a lab full of PCs running windows XP.  I have set up an ubuntu machine with Samba, Apache, and SWAT.  It works nicely, but I cannot figure out how to get the configuration that I would like.

Here is what I want:
  I would like each student at the school to have his/her own folder on the ubuntu machine that is shared via the SMB protocol so that it can be accessed using a Windows machine.
  On the Ubuntu side all the student folders could be owned by a single user named "student" but each folder would have a unique password when accessed via SMB.  Is this possible? Or do I have to create a Linux user for every student folder that is to be shared?

Any ideas would be appreciated. I am comfortable using SWAT or directly editing the smb.conf file.

Thanks.

---

### Post by elst on 2007-08-11
> **donaldvr said:**
> 
  On the Ubuntu side all the student folders could be owned by a single user named "student" but each folder would have a unique password when accessed via SMB.  Is this possible? Or do I have to create a Linux user for every student folder that is to be shared?


They should use separate accounts, but you don't need to create the accounts and home directories by hand! The best approach depends on whether this will be the main server, or will instead reuse accounts from a Windows server (domain controller).

---

### Post by donaldvr on 2007-08-11
This will be the main server.  All I really want is for each student to have his/her own folder with a unique password.  I would also like to have one public readonly folder.

Thanks again.

---

### Post by koenn on 2007-08-11
> **donaldvr said:**
> 
  On the Ubuntu side all the student folders could be owned by a single user named "student" but each folder would have a unique password when accessed via SMB.  Is this possible? .
What you want to do is either
1- have one user account with mulltiple, valid passwords. to my knowledge, this is impossible
2- have several user accounts, but all with the same user name. I'm not sure that is possible, but it's easy to check : create an acount "user", than try create another one with the same username. 

I'd say you need to create seperate accounts for each student, if you want them to have separate passwords. 
It should be quite simple to write a script that loops from 1 to number_of_students and for each student does
*add user, or useradd 
*smbpasswd
*create a home folder and set permissions if this hasn't been handled by useradd or adduser

or something along those lines. I think it's even possible to have smb passwords and unix passwords synced automatically. 

for a publicly accessible share, I think there's aan example in smb.conf

---

### Post by donaldvr on 2007-08-11
Yes, I think that will work.  But just to make sure that someone else can't think of another way, I'll restate what I want in a different way:

Last school year I purchased a network hard drive.  The hard drive's interface allowed me to create individual folders, each with it's own password.  It was perfect for assigning each student his/her own network folder. (I wrote a log-in script that mapped the folder to a drive letter when the student logged in.)  The problem was that the drive (although this was not listed anywhere in the manual or packaging) had a 30-something folder limit.  The drive was also unreliable when several computers connected to it at once.

To replace the network drive with a solution that will be more reliable and work for a larger number of students, I have set up an Ubuntu machine(Feisty Fawn) with Samba.  I'd like to be able to create folders on the machine in the same way as I did with the network drive.  I'd also like to create a public folder that is read-only and doesn't require a log-in password.

If someone can explain the easiest way to do this (please don't just tell me that it's easy) I would be very grateful.

Thanks.

---

### Post by koenn on 2007-08-12
OK, here's an idea :
create user accounts without passwords, but make the usernames as if they were passwords. So you'd have a user Xm_18Q, a user aaD$r8, and so on. 

You can't have home folders named after the username then, because you don't want your "passwords" to be visible in the form of folder names.So you'd have to create the home folders separately, and assign them to the users. You can then share the homes via samba (and assign drive letters etc)

You must realise that this weakens your security. You'd have to make sure that those accounts were very limited (no shell, no login, only access to samba ...). It's rather an onorthodox way of doing things so it will be easy to overlook something. 


An other approach could be to create folders that are read- and writeable for anyone at the filesystem-level, but you limit samba-access to 1 specifiek user per folder.
This is how Windows 98 shares worked, because the FAT filesystem  didn't have any security, so only the share permissions would apply. 
I'm not sure that this will work but you can give it a try. Again, this weakens security : a logged-on user would have unlimited access to all the folders that you've set up this way. That also applies for remote log-in s.a. ssh and possibly other protocols should you run them. The limitations will only apply to samba users. 

I suggest you experiment with this with 1 or 2 accounts untilll you have a configuration / procedure that is satisfactory, including security issues I mentioned,  and then look for a way to automate it. How many students are we talking about ?

---

### Post by donaldvr on 2007-08-12
Thanks for all the help.  What I think I'm going to do is just create a script for quickly adding users to linux and Samba.  You are right that I should get things working with a few users before I set it up for all the students.

Security is not a serious issue as the samba server will not be acessable to students and will not be exposed to the internet.  I just want to make sure it won't be easy for one student to gain access to another's files as I had some problems with that last year.

I know this is probably a dumb question, but a tried creating a user with useradd: 
> sudo useradd --create-home --password paswd --shell /bin/bash randomStudent
I must have done something wrong because this user does not work in Samba.  Incidently I could not log this user into gnome either, not that, that would be necessary.  Am I giving this user too much power?  All I need the user to be able to do is share his/her home folder in samba.  Do I have to modify a Samba users file?

Oh and one more thing: Once I get this working, I'm planning on creating a simple PHP page that allows the students to change their password.  What kind of permissions to I have to add to the PHP user so that it can do this?  

Thanks a ton!

---

### Post by koenn on 2007-08-13
You do know that samba uses seperate useraccounts, so you'd hafe to  create a samba account for each user as well? smbpasswd does that, if you run it as root, with a username as argument
```
sudo smbpasswd RandomStudent
```
There may be other ways to handle user accounts for Samba, but I've never had to look in to that, so ...


Also, consider giving a fake (logon-)shell to your users. That prevents them from loging in. It doesn't prevent them from running shell commands in a GUI terminal, if they'd have the chance. 
> sudo useradd  ... ....   --shell /bin/true   .. 
/bin/false is also possible.

Check that the user you created has indeed a home folder, and if so, that he owns it / has write access to it. If not, this may be the reason of the gdm login to fail. 

> Security is not a serious issue as the samba server will not be acessable to students 
This, I don't understand. You do want to make Samba shares for your students, right ? You don't consider accessing a share and the directories/files therin as "access to the server" ?

---

### Post by donaldvr on 2007-08-13
> This, I don't understand. You do want to make Samba shares for your students, right ? You don't consider accessing a share and the directories/files therin as "access to the server" ?
What I meant was that students won't be able to physically access the server machine.  As long as the SAMBA accounts have different usernames and passwords there isn't a serious threat.  I was just trying to state that high levels of security aren't necessary.  About 60 students will be using the system.  Most of them are very young and will always be monitored when using the computers.  I'm not particularly worried about any serious hacking attempts.  In fact, I'd be quite impressed if there was one.
I very much appreciate your help.

Thanks.

---

