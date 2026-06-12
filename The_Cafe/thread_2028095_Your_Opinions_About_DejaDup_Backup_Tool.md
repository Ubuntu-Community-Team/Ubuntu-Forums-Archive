---
title: "Your Opinions About DejaDup Backup Tool"
date: 2012-07-17
forum: The Cafe
---

### Post by robtygart on 2012-07-17
I was going to install DejaDup on Kubuntu, but most of the current reviews are really bad? What are your experiences? 

What do you use of backing up your system, and does it backup all your home folder, Personal files, programs, and settings?  

Thanks 
Rob

---

### Post by MG&amp;TL on 2012-07-17
Deja Dup works really well for me. I backup to my own network drive, so I might be biased (I guess most people backup to U1?)

It is a Gtk tool though, I do wonder if there's a KDE tool for you Kubuntu lot.

---

### Post by robtygart on 2012-07-17
Kubuntu runs Gtk widget themes so I am guessing it would be the same for DejaDup right?

---

### Post by MG&amp;TL on 2012-07-17
> **robtygart said:**
> Kubuntu runs Gtk widget themes so I am guessing it would be the same for DejaDup right?

No doubt. I can't honestly say I've ever run Kubuntu, but if it has a Gtk+ 3 theme, DD should look fine.

---

### Post by alefa on 2012-07-17
Well, I've always used BackInTime as a backup tool. Works really well, and has a few more configuration options than Deja Dup, I believe. Apart from the GTK-Gui, there is also a KDE version. Just install the package "backintime-kde".

---

### Post by blackbird34 on 2012-07-18
Yeah, me too.

---

### Post by mastablasta on 2012-07-18
redo backup is a nice backup ubuntu based CD utility for manual bare metal backup
 
mintbackup tool is also very simple and easy to use...

---

### Post by forrestcupp on 2012-07-18
It's good at what it does, but I prefer mirrored, rsync type backups. With DejaDup, you don't have access to your individual files, and you *have* to use DejaDup to restore your backup. It compresses your backup in such a way that you can't get to it unless you restore everything. If you're only wanting to restore a few files without changing any other progress you've made, you're just screwed. If I'm wrong about that, someone please correct me.

But with an rsync type backup, it mirrors your files to an external hard drive, so you can access whatever you want, and it only backs up the files that have changed. LuckyBackup is one good GUI frontend for rsync.

---

### Post by robtygart on 2012-07-18
> **forrestcupp said:**
> It's good at what it does, but I prefer mirrored, rsync type backups. With DejaDup, you don't have access to your individual files, and you *have* to use DejaDup to restore your backup. It compresses your backup in such a way that you can't get to it unless you restore everything. If you're only wanting to restore a few files without changing any other progress you've made, you're just screwed. If I'm wrong about that, someone please correct me.

But with an rsync type backup, it mirrors your files to an external hard drive, so you can access whatever you want, and it only backs up the files that have changed. LuckyBackup is one good GUI frontend for rsync.

This one sound good, I have hard the same about DejaDup. I do like the fact you can encrypt your files, I would only do this if I was uploading to ubuntu one. 

I will look at the ones you guys posted.  

Thanks Rob

---

### Post by yeehi on 2012-07-18
I talked about a good way to back up files in a thread [here]("http://ubuntuforums.org/showthread.php?t=2008397").

If you like the idea and want to install it, I hope you use the links I provided as they are referral links and I will get some more online storage space! :)

---

### Post by mechanismnine on 2012-07-18
one all around mirror of your entire hard drive then burned to cd or dvd or even to hdd would be awesome. dejadup just isn't that though

---

### Post by robtygart on 2012-07-18
> **yeehi said:**
> I talked about a good way to back up files in a thread [here]("http://ubuntuforums.org/showthread.php?t=2008397").

If you like the idea and want to install it, I hope you use the links I provided as they are referral links and I will get some more online storage space! :)

No! I am doing good with Ubuntu one 5gb and skydrive 25gb there.. I am just asking about programs. (Applicatings) or what ever you call them now. lol


Don't get my thread locked :P 

[URL="http://ubuntuforums.org/showpost.php?p=12047788&postcount=5"][QUOTE=elfy];Don't attempt to disguise referral links.




Closed.[/quote][/URL]

---

### Post by robtygart on 2012-07-18
> **mechanismnine said:**
> one all around mirror of your entire hard drive then burned to cd or dvd or even to hdd would be awesome. dejadup just isn't that though

A mirror of my hard drive might be fun, that could run into a lot of space.

---

### Post by juanbuntu on 2012-07-26
I installed DejaDup and configured the tool for automatic backups.

Manual backups seem to work OK but after several days I see no trace of automatic backups. Backups are created only when I made the request manually, so that is a problem which I am reporting as a separate thread.

---

### Post by Mr. Picklesworth on 2012-07-26
> **forrestcupp said:**
> It's good at what it does, but I prefer mirrored, rsync type backups. With DejaDup, you don't have access to your individual files, and you *have* to use DejaDup to restore your backup. It compresses your backup in such a way that you can't get to it unless you restore everything. If you're only wanting to restore a few files without changing any other progress you've made, you're just screwed. If I'm wrong about that, someone please correct me.

You're half right ;)

It isn't fast at restoring files (I believe this is a todo item in the bug tracker somewhere), but you can restore individual files or folders. Just right click the file in Nautilus and choose "Revert to Previous Version&#8230;".

While it is definitely slower than rsync, and it needs a little more machinery, it also has some benefits: backups are smaller, and individual increments are stored (and abstracted behind said machinery) instead of only the latest version. This way you can get at a version of a file from six months ago, instead of just the file from your last backup.

---

### Post by forrestcupp on 2012-07-26
> **Mr. Picklesworth said:**
> You're half right ;)

It isn't fast at restoring files (I believe this is a todo item in the bug tracker somewhere), but you can restore individual files or folders. Just right click the file in Nautilus and choose "Revert to Previous Version…".

While it is definitely slower than rsync, and it needs a little more machinery, it also has some benefits: backups are smaller, and individual increments are stored (and abstracted behind said machinery) instead of only the latest version. This way you can get at a version of a file from six months ago, instead of just the file from your last backup.

That's good to know. Thanks for correcting me. I guess the only problem would be if you need to access your files on your hard drive, but don't have access to Ubuntu.

---

### Post by Old_Grey_Wolf on 2012-07-26
I tried DejaDup but didn't like it. Sure, it compresses the files to take up less disk space; however, if you have to do a reinstall of the OS that can make some things cumbersome.

I prefer the "kiss" (keep it simple stupid) method. I use rsync for servers and grsync form desktops,

---

### Post by Roasted on 2012-07-27
> **forrestcupp said:**
> It's good at what it does, but I prefer mirrored, rsync type backups. With DejaDup, you don't have access to your individual files, and you *have* to use DejaDup to restore your backup. It compresses your backup in such a way that you can't get to it unless you restore everything. If you're only wanting to restore a few files without changing any other progress you've made, you're just screwed. If I'm wrong about that, someone please correct me.

But with an rsync type backup, it mirrors your files to an external hard drive, so you can access whatever you want, and it only backs up the files that have changed. LuckyBackup is one good GUI frontend for rsync.

I was in the same pickle as well. I really liked deja dup's simplicity but I like having some extra functionality with my backups. I ended up just creating an ssh key pair with my server and run an rsync script through crontab about 3 times a day. It goes something like:

rsync -az --delete --exclude=.gvfs /home/jason jason@192.168.1.150:/media/nas/jason

Works great... No complaints.

---

### Post by robtygart on 2012-07-27
Does anyone else Deja-Dup back up your Ubuntu-One folder? I set it to ignore, that should be set to ignore by default. :-k

---

### Post by BrokenKingpin on 2012-07-27
> **forrestcupp said:**
> It's good at what it does, but I prefer mirrored, rsync type backups. With DejaDup, you don't have access to your individual files, and you *have* to use DejaDup to restore your backup. It compresses your backup in such a way that you can't get to it unless you restore everything. If you're only wanting to restore a few files without changing any other progress you've made, you're just screwed. If I'm wrong about that, someone please correct me.

But with an rsync type backup, it mirrors your files to an external hard drive, so you can access whatever you want, and it only backs up the files that have changed. LuckyBackup is one good GUI frontend for rsync.
This was the issue I had with it as well. I just setup my own rsync scripts for backups... which gives me a lot more control.

---

### Post by ratcheer on 2012-07-27
I also like using Deja Dup. It is simple and effective. You can set it to back up or exclude whatever you want. And it can backup to almost any common storage, including the cloud.

It is simple to use, but it is not a toy. It is just a simplified front-end to Duplicity, which itself is a simplified front-end for rsync and other standard OS tools.

It is not a disk imaging tool, but it is not intended to be. It backs up your files and folders and it does it well. What more do you need?

Tim

---

### Post by tomdkat on 2012-11-30
Thanks for having this discussion. I'm thinking of using DejaDup for backups but this thread is causing me to have second thoughts.

Has much changed or improved with DejaDup since this thread was last active?

Thanks!

Peace...

---

### Post by Erik1984 on 2012-11-30
It can be a good tool, but I'm a bit hesitant with solutions like Deja Dup. The #1 reason why I am currently not using it is that it stores the back-upped data in a format that you can't easily access without having the software. I'm affraid that when I need my data it can't restore the backup. With my current setup (just rsync) I can view the backup location manually to see if it's all stored correctly and accessible.  With Deja Dup there's just a bunch of archive files. On the other hand Deja Dup gives some neat version control for all files which my current setup doesn't provide.

---

### Post by DukeOfMixture on 2012-11-30
I've used Deja Dup before and found it quite useful.

Today I just 'tar'.

---

### Post by Paqman on 2012-11-30
Tried it once, but I already had a backup scheme that was simply an rsync job in anacron. Deja Dup didn't seem to offer an advantages over this, and merely added a layer of obfuscation between me and the backups.

---

### Post by mjjones on 2012-12-07
redo backup is decent, also check out ElephantDrive.com to create backups off your own infrastructure. (full disclosure I'm affiliated with ElephantDrive)

[http://home.elephantdrive.com/linux/](http://home.elephantdrive.com/linux/)

---

### Post by CJ_Hudson on 2012-12-21
DejaDup works fine for me.

---

### Post by orange2k on 2012-12-21
Normally I backup my "important" files like movies and music to DVDs and USB sticks, but more than being interested in backup tools, I'm interested in appropriate storage media, since DVDs have limited life span...

What whould you recommend as a suitable storage media for usage with DejaDup or similair backup tools and what does it cost, approximately? I'm thinking of something like tape drives (large capacity and long lifespan) and removable hard drives - what is better?

---

### Post by rrnbtter on 2012-12-21
Greetings,
Tried them all and it has to be Lucky Backup for me.

---

