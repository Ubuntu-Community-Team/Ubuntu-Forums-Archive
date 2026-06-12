---
title: "samba recycle bin"
date: 2006-04-05
forum: Server Platforms
---

### Post by gaspedalo on 2006-04-05
Hi, I've a samba domaincontroller with a lot of shares. A big mistake that eventually happens is accidental deletion. I understand that the recycle option in Samba ist keeping deleted files as hidden. That's fine, but useless when files are kept forever and diskspace decreases fast. So a good way of handling that would be deletion after time. I fear that Samba won't do that, I think there might be a way of doin' that with a daily cron job. Something like checking certain folders (.recycle folders of samba shares) for files that are older than X and then deleting them. Would be nice, wouldn't it.
Unfortunately I'vo no idea how to do that or how a script or shellscript like that would look like, and how it would be integrated inro cron.

---

### Post by gaspedalo on 2006-04-06
doesn't anybody use a timefunction with the samba recycle bin...or neither the recycle bin itself?

---

### Post by jetpeach on 2006-05-17
I'm interested in this as well and am trying to implement it.  I'm starting to read about VFS and recycle.so now, but just searched these forums now and found your thread and that's all.  If I figure it out, I'll post what I've discovered.  I haven't yet set up the recycle option at all yet and am looking for info on that first.

As for writing a script to check for the age of deleted files, I don't think it would be very hard.  I am very amatuer with my python abilities, but I think in a few hours I could figure it out.  After I set up the recycle in samba, I'll look for a script written already, but if I can't find one I'll try writing one myself.

---

### Post by gaspedalo on 2006-05-18
Hi Jetpeach. I'm sorry that I didn't post before, but I've found a pretty conveniant solution to delete files that are older than 7 days on a daily basis. I use a cron job. I've put a file into /etc/cron.d/ that I called "cronjobs". That's where I define all the jobs I need. "Cron.d" is for jobs where you define when they should take place inside the cron-command. My command is as the following:

35 6 * * * root find /xxx/xxx/xxx/.Papierkorb -atime +7 -print -exec rm -rf {} \;

That means that everyday at 6:35 am root performs a find command on the recycle folder. It looks for files with -atime more than 7 (be sure to activate 'touch' in the samba recycle options). If a file or a folder is older it executes 'rm' and writes a mail to root with a list of the deleted file.

That's it.
Hope that helps.

---

### Post by gaspedalo on 2006-05-18
I forgot:
Search for howtos on cronjobs, I got some definition added to my cronjob file, like:

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/USER/bin
MAILTO=root
HOME=/home/USER

---

### Post by jetpeach on 2006-05-19
Great, thank you for the information.  I just got the recycle vfs working yesterday (easier than I thought actually), and will add this shortly.

---

### Post by FredSambo on 2006-07-13
How To Create a Samba Recycle Bin

ok, first you need to create the /etc/samba/recycle.conf file.  

```
sudo vi /etc/samba/recycle.conf
```

You must create this from scratch so don't be frightened by the blank page.  Mine looks like this:

```
##Recycle Bin Configuration File##
name = Recycle Bin
mode = KEEP_DIRECTORIES|VERSIONS|TOUCH
maxsize = 0
exclude = *.tmp|*.temp|*.o|*.obj|~$*|*.~??|*.log|*.trace
excludedir = /tmp|/temp|/cache
noversions = *.doc|*.ppt|*.dat|*.ini

```

and then edit your /etc/samba/samb.conf file...

```
sudo vi /etc/samba/smb.conf
```

add the following lines to the directory within which you'd like the recycle bin to live (i have recycle bins in [homes] and [www] on my server):

```

   vfs object = recycle
   config-file = /etc/samba/recycle.conf
   recycle:repository = Recycle Bin
   recycle:keeptree = Yes
   recycle:versions = Yes

```

then restart your samba daemons and the recycle bin should show up after a few momnents (but most likely after you delete your first file).

```
sudo /etc/init.d/samba restart
```

i worked on this all day and had trouble finding solid documentation.  this was the only thread on the subject here, so hopefully this will help someone else out!

---

### Post by FredSambo on 2006-08-08
> 35 6 * * * root find /xxx/xxx/xxx/.Papierkorb -atime +7 -print -exec rm -rf {} \;

here is my crontab entry for emptying the recycle bin, like the one above, it also empties files that are 7 days old every morning.

i put this in root's crontab file (crontab -e):

```
56 06 * * * find /home/shares/'Recycle Bin'/ -mtime +7 -type f -exec rm "{}" ";"
```

---

### Post by icpeanuts on 2007-06-14
Is it possible to create the recycle bin folder with a permission so users can not just delete the whole folder by mistake? Thanks

---

### Post by irkengir on 2007-10-05
> **FredSambo said:**
> i worked on this all day and had trouble finding solid documentation.  this was the only thread on the subject here, so hopefully this will help someone else out!

Thanks very much for posting that!

I found after I followed those instructions samba would:
[LIST][*]place deleted files in a dir called .recycle on the share path
[*]If you delete a file create another with the same name and delete that you'd end up with 'filename' and 'Copy #1 of filename' in .recycle
[*]Files would be placed in directories appropriately so if you delete /smbshare/foo/bar/file it will be placed in /smbshare/.trash/foo/bar/file
[*]Things are recycled immediately
[/LIST]

Could you post a link to any documentation you did find or perhaps summarize what those directives are doing. Some of them could be a bit ambigious.

---

### Post by coremesh on 2008-03-20
Thanks for the post FredSambo, works great for me.

---

### Post by njparton on 2008-04-10
Is it possible to set this up with one central recycle bin for all shares? I have 10 shares and would prefer to have a single recycle bin if possible.

---

### Post by BassKozz on 2008-05-28
> **FredSambo said:**
> How To Create a Samba Recycle Bin

ok, first you need to create the /etc/samba/recycle.conf file.  

```
sudo vi /etc/samba/recycle.conf
```

You must create this from scratch so don't be frightened by the blank page.  Mine looks like this:

```
##Recycle Bin Configuration File##
name = Recycle Bin
mode = KEEP_DIRECTORIES|VERSIONS|TOUCH
maxsize = 0
exclude = *.tmp|*.temp|*.o|*.obj|~$*|*.~??|*.log|*.trace
excludedir = /tmp|/temp|/cache
noversions = *.doc|*.ppt|*.dat|*.ini

```

and then edit your /etc/samba/samb.conf file...

```
sudo vi /etc/samba/smb.conf
```

add the following lines to the directory within which you'd like the recycle bin to live (i have recycle bins in [homes] and [www] on my server):

```

   vfs object = recycle
   config-file = /etc/samba/recycle.conf
   recycle:repository = Recycle Bin
   recycle:keeptree = Yes
   recycle:versions = Yes

```

then restart your samba daemons and the recycle bin should show up after a few momnents (but most likely after you delete your first file).

```
sudo /etc/init.d/samba restart
```

i worked on this all day and had trouble finding solid documentation.  this was the only thread on the subject here, so hopefully this will help someone else out!
THANKS FredSambo :D
Question for you,
What if your share has multiple sub-directories but you only want to "protect" (recycle) some of the subdirectories?
For Example: my ***smb.conf*** lists */media/extra_storage/Windows_Share/* as one of my shares, but within */Windows_Share/* I have 3 directories, lets call them */work/*, */play/*, and */other/*... now what if I only want the recycling bin to recycle files/folders from the ***/work/*** directory and not the */play/* and */other/* folders?

> **njparton said:**
> Is it possible to set this up with one central recycle bin for all shares? I have 10 shares and would prefer to have a single recycle bin if possible.

/\ I would also like to know this? /\

---

### Post by BassKozz on 2008-05-29
This is weird, *.tmp files are showing up in my new SAMBA recycling bin, as well as versions of *.doc and *.pdf's even thou I have **/etc/samba/recycle.conf** set to:```
##Recycle Bin Configuration File##
##Ref - http://ubuntuforums.org/showthread.php?p=1252880#post1252880
name = Recycle Bin
mode = KEEP_DIRECTORIES|VERSIONS|TOUCH
maxsize = 0
exclude = *.tmp|*.temp|*.o|*.obj|~$*|*.~??|*.log|*.trace|*.pst
excludedir = /tmp|/temp|/cache
noversions = *.doc|*.ppt|*.dat|*.ini|*.pdf
```:confused:

---

### Post by BassKozz on 2008-07-13
> **FredSambo said:**
> here is my crontab entry for emptying the recycle bin, like the one above, it also empties files that are 7 days old every morning.

i put this in root's crontab file (crontab -e):

```
56 06 * * * find /home/shares/'Recycle Bin'/ -mtime +7 -type f -exec rm "{}" ";"
```

that doesn't work for me:
```
~$ crontab -e
no crontab for user - using an empty one
crontab: installing new crontab
"/tmp/crontab.3Ute3g/crontab":2: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit? 
```
:confused:

**_EDIT:_** I forgot to use 'sudo' :doh: ](*,)
```
~$ sudo crontab -e
```

---

### Post by misace on 2008-07-21
..therefore you have configure recycle bin this way:

[myshare]
path = /var/samba/myshare
valid users = myuser1, myuser2
read only = No
vfs objects = recycle
recycle:repository = .recycle           *# hidden folder on top every share, or*
# recycle:repository = recycle          *# visible folder on top every share,*
# recycle:repository = /tmp/samba_trash *# or with full path it will create only 1 recycler for whole machine*
recycle:keeptree = Yes
recycle:touch = Yes
recycle:versions = No
recycle:maxsize = 0
recycle:exclude = *.tmp *.temp ~$* *.~??

other option are already mentioned in this thread above.

*one important hint: if u have read only share, you don´t need to create recycle bin :)*

---

