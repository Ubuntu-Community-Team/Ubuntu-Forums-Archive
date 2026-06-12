---
title: "file server for class room"
date: 2007-03-25
forum: Server Platforms
---

### Post by jdm2 on 2007-03-25
I'm helping a teacher at my school to get a server up for she can use in her classroom.  We are trying windows 98 right now.  She had xp running as one but she wants to be able to set up passwords for the folders.  Here is what she wants to do:  

She is an art teacher so she teaches a graphic arts class that uses adobe photoshop.  She wants to be able to set up a password for only that person can get into his/her files.  She wants access to the files.  She wants a server that is closed down tight.  She wants to have it so that the kids can access and upload their files on the network.  Can you help me out?  Thanks for the help.

---

### Post by elst on 2007-03-26
The "Samba" suite of software enables a Linux system to act as a Windows server, and it's extremely well documented - see [www.samba.org](www.samba.org). If it has a failing, it's that the number of options leads people to overthink things. You can do what you've described just by creating a user account for each pupil and switching on the home directory share option. "SWAT" provides a Web interface for managing Samba.

The standard server edition of Ubuntu doesn't install any services by default, so the only network access is that which you explicitly configure. The classroom server edition of Edubuntu provides a thin client system in addition to Samba, so may do more than you need.

---

### Post by Aberrix on 2007-03-26
ftp sounds like it would work as well.

---

### Post by jdm2 on 2007-03-26
The teacher doesn't want to have to teach the students how to do it really.  Let me see if I got this right.  With samba I can set it up and have 20 folders with a password that is different for each one?  Thaks for thel help

---

### Post by Mr. C. on 2007-03-27
Yes, you can have either user-level permissions, or the less secure, but easier to manage share-level permissions.  Each folder can have its own sets of permissions.

MrC

---

### Post by jdm2 on 2007-03-29
So can I have a main folder in some directory then indivual folders, the main folder everybody can access but the indivudial folders that person needs to have permission.  How would I go around doing this:  the people going to use this will be using xp and they need to be able to access it and upload to it from the network.  Also the teacher will need to be able to access all the folders from a xp machine to.  

NOTE:  These students are graphic art students so they willl need to be able to open them up with adobe photoshop and then be able to save their project from adobe photoshop in xp to their own folder.  

Thanks for the help.

---

### Post by Mr. C. on 2007-03-29
I'm not sure which solution you are considered, nor which OS for the server.

Share-level gives you the ability to provide a password for a folder.  If that folder is in a parent folder that has a different share-level password, you cannot use both.  Basically, share-level provides the ability to see "from this point down the folder tree".  So you get :

```

  - Main Folder
       - Student Folder 1
       - Student Folder 2
       - Community Folder
       - File 1
       - File 2

```

If you share Student Folder 1 to a student, then that student can only see files and folders at or below Student Folder 1.  If the student has any access to Main Folder, they see all files and folders below, which includes Student Folder 1 and Student Folder 2.   In addition, Share-level is read, or read/write only, with nothing in between.  This clearly is not what you want.  There are also limits on how many folders can be shared in the older Windows OS's.

To accomplish what you want, you need User-Level sharing, which allows you to specifically set which users (and groups) can access which files and folders.  In the above example, you can set permissions such that each student can access their own Student folder (read, write, delete), but cannot access any other student folders.  You can allow students to create or move files into Community folder, but not delete or see them.  You can allows students to see File1 but not File2.

All of this comes with a price - its a little complex if you don't understand Windows User, Groups and Permissions.  You cannot use Windows 98 to accomplish what you need in this case.

Your choice of OS' for this really is Linux/Unix, or Windows NT, 2000, or XP Pro.

Without knowing your level of skills, I can't recommend or direct more than this.  Perhaps you can help us understand what you can handle.

MrC

---

### Post by elst on 2007-03-31
It may be much simpler to use the built-in home directory share feature to automatically share the home directory for each user, and set up a separate public share. IIRC, the supplied Samba configuration file includes the necessary settings, with comments.

The only tweaks needed would be to set home directory creation make home directories private by default, and ensure that the built-in staff group has permissions over the /home/ directory. Something like these terminal commands:

sudo dpkg-reconfigure adduser
(select "no" when prompted)
sudo chmod -R 2771 /home
sudo chgrp -R staff /home

After that, every time that a user account is created, accounts that are members of the staff group should automatically have access to each home directory.

Share-level security exists to emulate obsolete versions of Windows, and if the server is going to support a number of users then it's probably best to set it up as a domain controller anyway, so that login scripts can be used to automatically attach shared folders as network drives.

jdm2: If you haven't already, you will need to spend about 20 minutes with your choice of Samba or Windows networking document/book to understand the concepts of "groups", "shares", "mapped drives" etc. It's not complicated, but most tutorials and sets of instructions won't make sense until you know the terms.

---

