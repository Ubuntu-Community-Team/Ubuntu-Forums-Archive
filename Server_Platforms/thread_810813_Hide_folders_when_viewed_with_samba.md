---
title: "Hide folders when viewed with samba?"
date: 2008-05-28
forum: Server Platforms
---

### Post by krelkor on 2008-05-28
Hi guys, im doing some clean up and a little thing has been bugging me enough to finally figure out how to fix it

I have a raid 5 mounted using linux software raid. 

I access the ubuntu box using samba

I have a Lost+Found folder right in the middle of my root access and i would like to figure out how to get rid of it. Is there a way i can make it hidden on the ubuntu box so i never have to see it through samba again? Can i just get rid of it all together?

I searched and found that i can make a file /.hidden and add it lost+found to it, but doesn't that only work with nautilus?

Thanks!

---

### Post by NateMan on 2008-05-28
Mount a folder above it in samba so you don't see it. Seems like a good way to fix it. I normally have a separate folder for samba and symlink everything I want to be accessible. It makes for a nice easy to follow scheme, and its easy to add and remove parts of your system for view.

---

### Post by krelkor on 2008-05-28
> **NateMan said:**
> Mount a folder above it in samba so you don't see it. Seems like a good way to fix it. I normally have a separate folder for samba and symlink everything I want to be accessible. It makes for a nice easy to follow scheme, and its easy to add and remove parts of your system for view.



Sorry, I may have not been entirely clear. 

I have a raid array mounted as /data
I have my samba set up so that when i access //192.168.1.128 or //server across the network i see a share called "storage" and that dumps me to /data

inside /data there is:

/data/applications
/data/documents
/data/lost+found
/data/movies
/data/music/


Im looking to get rid of the lost+found by any means necessary. If that means not actually getting rid of it and just hiding it through some obscure samba setting than thats ok, but if i could just get rid of it on the actual hard data level that would be even better.

---

### Post by NateMan on 2008-05-28
well you need to leave that file, so why don't you make another directory and place symlinks to your applications, documents, movies, and music in there, then share the directory with the symlinks over samba? that's a very very easy solution to your problem that does not involve any obscure samba or linux tricks.

---

### Post by ephur on 2008-09-29
If you want to share the root of the file system and don't want the extra overhead of worrying about links, and such, then you can put the following in /etc/samba/smb.conf 

hide files = /lost+found/ 

Put that in the section for each share, restart samba, and you'll be set.

-- Richard

---

### Post by koenn on 2008-09-29
that, or set "hide unreadable files = yes" in samba config (global or per share, I'm not sure, maybe both are possible). 
More about samba access control : [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2605646](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2605646)

---

### Post by cybertron on 2009-11-25
I know this thread is really old, but I wanted to update it with some useful information. 

I was also trying to hide lost+found on my samba share. And here are the two options I know about... 

under your share in smb.conf, you can add either: 

```
   hide files = /lost+found/

or

   hide unreadable = yes
```

The first option does hide the folder but if you have "Show hidden files, folders, and drives" enabled on your windows PC, it will still show up, just as a transparent icon. The second option though will totally make it disappear from your share, even when "Show protected system files" is enabled. 

Hope that's helpful.

---

### Post by DezSP on 2011-08-14
Bump. This thread is even older now but it's the top Google result, and I figured this would be useful.

As well as "hide files", samba has an option called "veto files", which will make the folders inaccessible, rather than just hidden. So you can use a line like this:

veto files = /Network Trash Folder/Temporary Items/

This lets you remove folders that are considered readable, but aren't relevant to SMB - my example above being the folders created when using AFP (OS X file sharing).

Some more stuff available here: [http://www.samba.org/samba/docs/using_samba/ch08.html](http://www.samba.org/samba/docs/using_samba/ch08.html)

---

