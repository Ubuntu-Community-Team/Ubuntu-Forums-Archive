---
title: "samba &amp; folder permissions"
date: 2006-03-21
forum: Server Platforms
---

### Post by evanc on 2006-03-21
Kind of a weird request -

I've got an Ubuntu 5.10 / Samba box running a simple file server at my job, which about 15 people have access to over the LAN. When I set it up I didn't pay too much attention to file permissions, and just set everything to read, write, execute across the board. We're not really concerned about security, the data's not very sensitive, and we run a backup every night.

The problem I'm having is people often accidentally move project folders into one another, just by sloppy mousework I guess, but it becomes a problem when you look for a project folder and it's just "gone" - moved into an adjacent folder.

The setup is like this:

2005-Projects/Project-Name/

people need full access to project files under "Project-Name" and need to be able to create folders / whatever / inside that directory. People need to be able to read the directory list under 2005-Projects, but should not be able to move subdirectories or create new files. One administrator needs access to create new project folders as needed. I guess we can do this with sudo if we have to.

I've run a few quick tests - and the problem i'm running into now is that if the top level is set to read only, but the subfolders are full access, if you drag and drop a project folder into another, it will move all the files, just won't delete the directory from the top level. how frustrating.

any suggestions?

---

### Post by rennen on 2006-03-21
I run Gentoo Linux generally, but am starting to use Ubuntu a bit. Just as a server, not a desktop. I still love Gentoo.  

I use Samba as a PDC in my domain. Every user has a home dir they have r/w [755] access too, but then I map a drive to their local Windows machines as the P:\ drive from the /home/public on the Samba server. They have only Read access [655] to this directory. They are part of the users group and so is the /home/public directory. I own the directory so I have r/w. It works out fairly well. If they need something I manage it from shell.

Here is a great link on how to set up Samba as a PDC. Generally just good info. You don't have to follow the Gentoo specific advise. ;)
[CENTER][How-To Samba as a PDC]("http://gentoo-wiki.com/HOWTO_Implement_Samba_as_your_PDC")[/CENTER]

I see that you have everything set as you like, but you might want to think about another group of permissions.

---

### Post by derelict on 2006-03-21
[QUOTE=evanc]People need to be able to read the directory list under 2005-Projects, but should not be able to move subdirectories or create new files. [/QUOTE]

For the share that maps 2005-Projects use the option:
directory mode = 0755

---

