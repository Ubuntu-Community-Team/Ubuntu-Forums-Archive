---
title: "Wu-ftp"
date: 2012-03-16
forum: Server Platforms
---

### Post by skipgillespie on 2012-03-16
I'm having an issue setting up my FTP server.  I installed wu-ftp and I think I've got my path and permissions set up, however; if I log in, I appear to go into some other directory and I can't determine where it's at.  If I use my web browser, it just shows that I'm connected but appears to be nothing there.  If I connect with windows explorer (not internet explorer) I first appeared to have a empty directory.  I tried to copy files into it and that appeared to go okay.  If I log in again with explorer I can still see them.  When I go back to the web browser, it still doesn't see anything in the directory.  

Any help would be greatly appreciated.

---

### Post by Holdolin on 2012-03-16
pwd will tell you what directory you're in, assuming you're using a Linux box.  No files showing would tell me that either there is nothing there, or the contents don't have the proper permissions.

---

### Post by skipgillespie on 2012-03-16
> **Holdolin said:**
> pwd will tell you what directory you're in, assuming you're using a Linux box.  No files showing would tell me that either there is nothing there, or the contents don't have the proper permissions.

I'm not certain where it's going on my server.  When I access via ftp client, I don't have the ability to issue the pwd command to list the directory.

---

### Post by skipgillespie on 2012-03-17
Okay, I got home last night and looked and sure enough.  The file that I uploaded is right where it's suppose to be.  So why can't I see any of the other files that I have in that directory? :confused:

skip@ubuntu:/srv/media$ ls -l
total 1860
drwxrwxr-x  5 skip users    4096 2012-03-13 07:39 0-9
-rwxrwxr-x  1 skip users 1877183 2012-03-16 09:30 1962_storm_of_the_century.pdf
drwxrwxr-x 18 skip users    4096 2012-03-13 21:22 A
drwxrwxr-x  9 skip users    4096 2012-03-14 18:55 Animated
drwxrwxr-x 18 skip users    4096 2012-03-15 22:38 B
drwxrwxr-x 16 skip users    4096 2012-03-16 20:24 C
drwxrwxr-x 20 skip users    4096 2012-03-16 23:04 D

The six directories are what I have on the server but I can't see them when I log in under ftp.  The .pdf file is what I uploaded via ftp.  It has the same User and Group, so I am logged in as the correct User.


I have gone through all the permissions and User/Group settings that I can think of and nothing seems to work. ](*,)

---

### Post by SeijiSensei on 2012-03-18
What are the permissions on /srv and /srv/media?  At a minimum they should be 711, or 755 if you want to allow "others" to read files in /srv/media.

Does /srv/media point to a mounted device like an external drive?  What filesystem is it using?  Is it POSIX-compliant like ext4, or proprietary like FAT32 or NTFS?

---

### Post by skipgillespie on 2012-03-18
> **SeijiSensei said:**
> What are the permissions on /srv and /srv/media?  At a minimum they should be 711, or 755 if you want to allow "others" to read files in /srv/media.

Does /srv/media point to a mounted device like an external drive?  What filesystem is it using?  Is it POSIX-compliant like ext4, or proprietary like FAT32 or NTFS?

Yes, /srv is a mounted 4TB RAID5 array.  I formated it with the ext4 file system.

I guess I'm too much of a newbie to understand what the "711" and "755" are.  I thought setting up the USERS and GROUPS was all I needed.

---

### Post by Holdolin on 2012-03-18
711 and 755 are permission settings for the user, group, and everybody else.  The numbers corolate permissions for said groups.

---

### Post by skipgillespie on 2012-03-18
> **Holdolin said:**
> 711 and 755 are permission settings for the user, group, and everybody else.  The numbers corolate permissions for said groups.

Where do I find those settings at?

---

### Post by skipgillespie on 2012-03-19
Okay, I did some reading and if I understand it correctly, the files and directories that I'm trying to access have a permission of 771 as noted from this previous post:

> **skipgillespie said:**
> 

skip@ubuntu:/srv/media$ ls -l
total 1860
drwxrwxr-x  5 skip users    4096 2012-03-13 07:39 0-9
-rwxrwxr-x  1 skip users 1877183 2012-03-16 09:30 1962_storm_of_the_century.pdf
drwxrwxr-x 18 skip users    4096 2012-03-13 21:22 A
drwxrwxr-x  9 skip users    4096 2012-03-14 18:55 Animated
drwxrwxr-x 18 skip users    4096 2012-03-15 22:38 B
drwxrwxr-x 16 skip users    4096 2012-03-16 20:24 C
drwxrwxr-x 20 skip users    4096 2012-03-16 23:04 D

Owner should have - read/write/execute
Group should have - read/write/execute
Other should have - read/execute

So, I'm logging on as username:  skip which is part of usergroup:  users.  Through FTP from the outside world, I cannot see any of the directories or files that originally resided there.  However, just for grins....I tried to upload a file....the .pdf file shown.  I am able to see it from the outside but that is it, nothing else.  It has the same permissions, user, and group as the directories so why can't I see them.

---

### Post by SeijiSensei on 2012-03-19
> **skipgillespie said:**
> 
Owner should have - read/write/execute
Group should have - read/write/execute
Other should have - read/execute

That translates to 775 for directories, and 664 for files.

However I'm more concerned with /srv and /srv/media than I am about the directories under /srv/media.

What does "cd /; ls -l | grep srv" and "cd /srv; ls -l" show?

---

