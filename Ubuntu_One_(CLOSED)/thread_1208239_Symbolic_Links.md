---
title: "Symbolic Links"
date: 2009-07-09
forum: Ubuntu One (CLOSED)
---

### Post by RealG187 on 2009-07-09
Does anyone know how the Ubuntu client handles symbolic links? Will it upload the symbolic link or the file it links to?

Because if it uploads the actual file then I could use symbolic links to upload files outside the folder I cannot move (like my knotes folder)

---

### Post by jpeddicord on 2009-07-11
Doesn't look like it does. Symlinked an outside folder and Ubuntu One just ignores it completely.

---

### Post by RealG187 on 2009-07-13
> **jacobmp92 said:**
> Doesn't look like it does. Symlinked an outside folder and Ubuntu One just ignores it completely.That sucks, I love symlinks.

But I found a way around that.

For my Knotes (/home/dope/.kde/share/apps/knotes) instead of making "/home/dope/Ubuntu One/My Files/knotes" a symlink to "/home/dope/.kde/share/apps/knotes" I made "/home/dope/.kde/share/apps/knotes" a symlink to "/home/dope/Ubuntu One/My Files/knotes"

---

### Post by renkinjutsu on 2009-07-17
you can probably use hardlinks .. although pretty useless since it doesn't work for directories

---

### Post by lodp on 2009-07-17
I just received my invitation, and after installing I was a bit disappointed about the symlink thing. Dropbox does work with symlinks.

Is there a reason why ubuntu one doesn't support that? Is it planned to be supported? 

It seems eminently useful for backing up / syncing application data (knotes is a good example, but I'd also like to use it for thunderbird, firefox, korganizer and such)

---

### Post by zekopeko on 2009-07-17
> **lodp said:**
> I just received my invitation, and after installing I was a bit disappointed about the symlink thing. Dropbox does work with symlinks.

Is there a reason why ubuntu one doesn't support that? Is it planned to be supported? 

It seems eminently useful for backing up / syncing application data (knotes is a good example, but I'd also like to use it for thunderbird, firefox, korganizer and such)

i think they will implement symlinking at some point. but the whole point of u1 is so that you don't need to symlink application data yourself. it will do it for you. 
i know that they are working on contact sync with evolution contacts (it's probably going to be expanded to empathy/pidgin contacts also) and desktop screen sharing. 
at a latter date they could easily implement application settings sync for all of the major desktop app. 
and not to mention that the client is open source so they could also simply provide an API for applications to plugin to so that they don't have to wait for the u1 team to do it for them.

---

### Post by lodp on 2009-07-17
wouldn't it take ages for all the applications to support that?

also, it's not just application data that many people like to backup and sync - it's also documents and other stuff that resides somewhere in a folder structure outside the ubuntu one folder, and symlinks would be great for that.

I'm planning to do this with dropbox for the time being -- does anybody know whether there's an inherent problem with symlinking application data into a synced folder (and if so, is that why ubuntu one doesn't support it)?

---

### Post by Primefalcon on 2009-07-18
hard links do work (of course) but sym links no

---

### Post by nortexoid on 2009-10-30
Can you hard link a folder? Or can you symlink it and hard link that to get it to work?

---

### Post by krippa on 2010-05-04
This seems like it should be a top priority but the new Ubuntu one client in Lucid still doesn't support this! 

I have my docs, pictures etc. on a partition separate from my home folder so it seems I am completely out of luck.. And I was even thinking of getting 50GB subscription for my photos. For now I am stuck with Dropbox..

Symlinks ASAP please!

Does anyone know if symlink support is planned?

---

### Post by joshuahoover on 2010-05-05
> **krippa said:**
> This seems like it should be a top priority but the new Ubuntu one client in Lucid still doesn't support this! 

I have my docs, pictures etc. on a partition separate from my home folder so it seems I am completely out of luck.. And I was even thinking of getting 50GB subscription for my photos. For now I am stuck with Dropbox..

Symlinks ASAP please!

Does anyone know if symlink support is planned?

We don't currently have plans to add symlink support. We do provide a way to right-click on a folder in your home folder and synchronize that folder, but don't support symlinks.

Thank you,

Joshua

---

### Post by RealG187 on 2010-05-07
> **krippa said:**
> This seems like it should be a top priority but the new Ubuntu one client in Lucid still doesn't support this! 

I have my docs, pictures etc. on a partition separate from my home folder so it seems I am completely out of luck.. And I was even thinking of getting 50GB subscription for my photos. For now I am stuck with Dropbox..

Symlinks ASAP please!

Does anyone know if symlink support is planned?For me "/home/mpg/Ubuntu One" is a symlink and I think that works, but symlinks inside the Ubuntu One folder don't work...

---

### Post by krippa on 2010-05-08
> **RealG187 said:**
> For me "/home/mpg/Ubuntu One" is a symlink and I think that works, but symlinks inside the Ubuntu One folder don't work...

With this solution can you still only add folders within your home directory to be synced or any folder on the partition that is symlinked?

Thanks

---

### Post by krippa on 2010-05-08
I found out another way to synchronize any folder on *any* partition (I only have ext partitions so I dont know if it will work with ntfs etc.).

For various reasons I dont want to mount my "file store"-partition in my home folder directly, I want it at /media/hd. What I then did was edit my fstab file to create a "binding" (similiar to mount) of some of these folders to my home directory which Ubuntu One then lets me synchronize by right-clicking in Nautilus.

Here's what I did for my pictures folder:
Edit my /etc/fstab:
```
sudo gedit /etc/fstab
```

After the existing mount, I added a bind entry:
```
UUID=49af66cc-3eab-4d0a-b5a6-e1e18b926b47 /media/hd       ext3    defaults        0       2
/media/hd/Pictures /home/kristofer/Pictures       none    bind        0       0
```

Then you have to create /home/kristofer/Pictures and remount drives with: ```
sudo mount -a
```

---

### Post by mynameisflorian on 2010-08-26
I've been waiting for this feature since the inital launch. I guess I shouldn't hold my breath. Does anyone know of a similar service that can handle symlinks?

---

### Post by krippa on 2010-08-28
Yeah, dropbox does support symlinks and also sync between OS:es, public sharing etc. It does not directly support syncing settings of apps but if you know symlinking you can probably manage that too.

---

### Post by onecsguy on 2012-01-24
> **lodp said:**
> wouldn't it take ages for all the applications to support that?

also, it's not just application data that many people like to backup and sync - it's also documents and other stuff that resides somewhere in a folder structure outside the ubuntu one folder, and symlinks would be great for that.

I'm planning to do this with dropbox for the time being -- does anybody know whether there's an inherent problem with symlinking application data into a synced folder (and if so, is that why ubuntu one doesn't support it)?

Ubuntu One doesn't support Symbolic Links because people would backup their mysql folders and possibly root =P, I imagine they are worried about data traffic and have probably specifically excluded symbolic links (they would have had to as to an application unless attributes are checked, a symlink appears as a regular folder / files)

---

### Post by dunnerz on 2012-01-31
> **onecsguy said:**
> Ubuntu One doesn't support Symbolic Links because people would backup their mysql folders and possibly root =P, I imagine they are worried about data traffic and have probably specifically excluded symbolic links (they would have had to as to an application unless attributes are checked, a symlink appears as a regular folder / files)

If I really wanted to do that, I could very easily save mysql root dir to the ubuntu directory.

It's a shame they are not doing sym links though - losing a customer here.

---

### Post by kevinfishburne on 2012-12-12
Well it's nearly 2013 and I just got hit in the head with a brick: Ubuntu One *still* doesn't let you sync anything outside your home directory or support symlinks. It's effectively useless unless you're the least common denominator type user who doesn't even know what a symlink or partition is. I can barely believe it, but there it is. *facepalm*

---

### Post by Redsandro on 2013-03-05
4 years have passed, and the Ubuntu One team still does not understand why Dropbox is more successful.
It is SO EASY in Dropbox to make a link to some data/settings and have it backed up. You don't have to think.

Also I like to have a little ecryptfs on there, and I need a link to a directory outside my home, not to the folder in Ubuntu One (which is a popular workaround) because you cannot mount ecryptfs (custom) from within ecryptfs (default encrypted home).

Of course, a typical developer would argue *"you can work around this, you can share additional folders, you can specify the location on other computers, etc"*

But: [LIST]
[*]You have to sit down and think how to tackle your specific problem.
[*]You cannot easily specify the location of a new synced directory on a machine without the control panel (deamon only)
[*]You would have to remove the existing local target application folder and store the U1 folder in the new location.
[*]This folder will first sync completely (new computer), and then you have to move it out of home and you have to wait again (e.g. encrypted home -> non-encrypted share)
[*]*"Please choose a folder inside your "/home/redsandro" directory, and not overlapping with any existing cloud folder."*
[/LIST]

Ubuntu One is giving me acid reflux.

Why waste time postponing ways to handle this (i.e. ignore symlinks) when there is a perfectly fine POSIX equivalent of symbolic links developed in the '60s?

> **lodp said:**
> It seems eminently useful for backing up / syncing application data (knotes is a good example, but I'd also like to use it for thunderbird, firefox, korganizer and such)

---

