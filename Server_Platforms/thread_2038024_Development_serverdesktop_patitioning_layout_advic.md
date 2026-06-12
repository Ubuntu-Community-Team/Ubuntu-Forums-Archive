---
title: "Development server/desktop patitioning layout advice"
date: 2012-08-05
forum: Server Platforms
---

### Post by Kivech on 2012-08-05
Hi all,

I need to set up a Ubuntu server/desktop that will serve as a development platform. For this purpose I will initially have to run at least the following services, but potentially more later on:
Apache
MySQL
OpenJDK

The machine will mostly be used to develop Cloud software. So this means lots of web site development, lots of JAVA, PHP, some C# and C++. However, other development will be there as well.

There will be multiple distributions installed, but the Ubuntu environment will be the production environment.
I will also be using VirtualBox extensively, and of course remote server management will be part of the deal.

I have a fairly recent system with 2x1Tb disk space and 8Gb RAM.

I want to use one disk for the system, and one disk for all the data. Ideally I would like to set things up in such a fashion that backing up should be easily done. I know that technically that would be easily solved by using the second harddisk for my /home directory and put all development data in there. I'm just wondering if there might be better ways of doing this.

So what would be a solid partitioning layout for a machine like this? It needs to be easy to administer, and set up professionally that takes future expansion into account. I don't want to have to go through hell if one day I decide to change distribution for whatever reason, and my data needs to be safe (of course). Also keep in mind that lots of users should be using this machine remotely when things have to be (load) tested.

What would you recommend? I know the default more advanced layouts, but it is hard to find a recommendation for my particular situation. The part I know is that a simple start would be like this:
/boot
/swap
/
/usr
/var
/tmp
/home

But I take it that when you go the server route as well, with development as the main purpose of the environment, that things might need some more detail than just this. Most of all, I would like to have ideas on how much space I should assign to which partition (also additional ones to the ones I mentioned) for my particular purpose.

I'm looking forward to your suggestions.

---

### Post by Kivech on 2012-08-06
Is there really no one who can even give a hint as to what would be a decent partition layout for the purpose I want to use my server/desktop for?

---

### Post by LHammonds on 2012-08-06
If you are not sure how it needs to be setup and what will grow, then design it so it can be expanded as needed.  LVM would be great for doing this.

The way I setup my servers is to initially give them just enough space to install and keep everything separated into their own volumes.  I then expand the volumes that need more space later and then increment the file systems (but not consume the entire volume).  I then setup an automated script that will keep an eye on disk space for each volume and automatically increase as needed (along with sending me an FYI email).

I then use LVM and FSArchiver to perform full system-level backups that I can use to restore if the hardware fails.  For incremental or more granular file-level backups, I use rsync and have it keep a mirror copy to a backup location.  I also compress the backup location on a regular basis and store offsite as snapshot-in-time archives.

You can see how I did this in my sig for setting up an Ubuntu server.

LHammonds

---

