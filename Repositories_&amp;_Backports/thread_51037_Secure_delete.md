---
title: "Secure delete?"
date: 2005-07-22
forum: Repositories &amp; Backports
---

### Post by H_Roark on 2005-07-22
Does anyone know of a repository that has an srm type tool?  If so, how do I get there, and what name do I use for the package?

Thanks in advance.

---

### Post by dataw0lf on 2005-07-22
Check out the `shred` command.

---

### Post by matthew on 2005-07-22
I didn't know that was there...thanks for the heads up. Is there a way to do something similar on free space? For example, I have an old computer that used to have sensitive database info on the hard drive. I have deleted the data (not knowing about the shred command) but I know it could easily be recovered by someone with just a little knowledge. Is there a way to overwrite all the free space with either a random string of 1's and 0's or just a recurring pattern of some sort while keeping it shown as free space? Kind of like what governments require to be done with their equipment before it is tossed out/auctioned off.

---

### Post by H_Roark on 2005-07-22
What's the syntax for that?  Just shred -filename in a terminal?

---

### Post by damonw5 on 2005-07-22
[QUOTE=H_Roark]What's the syntax for that?  Just shred -filename in a terminal?[/QUOTE]
 [http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/shred](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/shred)

---

### Post by H_Roark on 2005-07-22
[QUOTE=damonw5][http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/shred](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/shred)[/QUOTE]

Perfect.  Thank you.

---

### Post by ArBaDaCarBa on 2005-07-22
Just looking at the man page: shred doesn't work every time.

> 
 CAUTION:  Note  that  shred relies on a very important assumption: that the filesystem overwrites data in place.  This is the  traditional  way to  do  things,  but many modern filesystem designs do not satisfy this assumption.  The following are examples of filesystems on  which  shred is not effective:

       * log-structured or journaled filesystems, such as those supplied with

              AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       *  filesystems  that  write  redundant  data  and carry on even if some writes fail, such as RAID-based filesystems

       * filesystems that make snapshots,  such  as  Network  Appliance’s  NFS server

       * filesystems that cache in temporary locations, such as NFS version 3 clients

       * compressed filesystems

       In  addition, file system backups and remote mirrors may contain copies of the file that cannot be removed, and that will allow a shredded file to be recovered later.


[QUOTE=matthew]Kind of like what governments require to be done with their equipment before it is tossed out/auctioned off.[/QUOTE]
Isn't physical destruction of the hard drive the requirement BTW?

---

### Post by matthew on 2005-07-22
[QUOTE=ArBaDaCarBa]Isn't physical destruction of the hard drive the requirement BTW?[/QUOTE]

One would think so, but in "not so secret" but still potentially sensitive situations I kind of doubt it. Case in point, I have a friend who was given a lot of 40 old computers (PII's and early PIII's I think) to set up a small internet cafe. They were donated by a government agency and still had hard drives in them.

---

### Post by matthew on 2005-07-31
[QUOTE=ArBaDaCarBa]Isn't physical destruction of the hard drive the requirement BTW?[/QUOTE]
Just saw this and thought it fit in with the discussion...

[http://yro.slashdot.org/article.pl?sid=05/07/31/0618205&amp](http://yro.slashdot.org/article.pl?sid=05/07/31/0618205&amp)

I would like to *bump* my question:

> I didn't know that was there...thanks for the heads up. Is there a way to do something similar on free space? For example, I have an old computer that used to have sensitive database info on the hard drive. I have deleted the data (not knowing about the shred command) but I know it could easily be recovered by someone with just a little knowledge. Is there a way to overwrite all the free space with either a random string of 1's and 0's or just a recurring pattern of some sort while keeping it shown as free space? Kind of like what governments require to be done with their equipment before it is tossed out/auctioned off.
07-22-2005 07:40 AM

Edit: I want to add that the Slashdot article led me to several good ideas for wiping a hard drive completely, but I am still looking for a way to wipe free space while keeping undeleted data intact. I have seen Windows programs that do this, both in ntfs and fat32 such as this one among many: [http://www.heidi.ie/eraser/features.php](http://www.heidi.ie/eraser/features.php)

---

### Post by larry_steiner on 2005-09-15
Hello,
I'm interested in a multi pass delete too.  Wipe free space and cache as well.  Have you had any luck?  Remember IBM OS/2?  It had an option for secure delete built in as it was intended for DOD use.

Thanks

---

### Post by matthew on 2005-09-15
Hi, Larry,

I still haven't found anything specificly designed for wiping free space. For deleting a file I learned you can use the shred command. I haven't really used it yet so the best I can do is point you to what I have found--in a terminal type "man shred" for the manual page on the command.

I am following this with interest, however, as I used in for years under windows along with its predecessor E4M. [http://www.truecrypt.org/future.php](http://www.truecrypt.org/future.php) They say a linux version is in the plan, but not target date is listed...it's not the same thing as a secure delete for free space, but since it goes with the idea of keeping data secure I thought you might find it interesting.

This guy wrote an article a few years ago with some scripts for free space wiping, but I haven't tried them, so I can't recommend them specifically. [http://www.theregister.co.uk/2002/11/21/data_security_for_linux_power/](http://www.theregister.co.uk/2002/11/21/data_security_for_linux_power/)

Finally, from these very forums, comes a discussion of a utility that someone wanted to use to try to do this. In the thread a specific command was discussed that would write either zeros or pseudorandom data to create a nonsense file to overwrite all the free space on a hard drive, effectively doing what we are looking for. [http://ubuntuforums.org/showthread.php?t=61862](http://ubuntuforums.org/showthread.php?t=61862) Here are the notes I made to myself based on the discussion. I'm looking for some free time to test it out. 
```
Command to erase (overwrite) a hard disk...use with caution, it will be unrecoverable!!

Note: use the second command after using the first if paranoid. If really paranoid, use a few times and then get a big hammer!

dd if=/dev/zero of=/dev/hda

dd if=/dev/urandom of=/dev/hdc bs=102400

man dd for more
```

---

### Post by Deacon Nikolai on 2005-09-15
[QUOTE=larry_steiner]Hello,
I'm interested in a multi pass delete too.  Wipe free space and cache as well.  Have you had any luck?  Remember IBM OS/2?  It had an option for secure delete built in as it was intended for DOD use.

Thanks[/QUOTE]

Mac OS X does too since it is used by the government, It is nice to have.

---

### Post by yama108 on 2007-10-01
Gutmann's Eraser program for Windows is probably the best data removal tool I've come across, (it's Open Source too).

Unfortunately that doesn't help us linux users since it only works on Windows.  I'm still looking for a decent data removal tool for linux.  Will post if I find one.

BTW multi-pass erasing is the only way to go.  DoD recommends 3-7 overwrites.  Guttmann pushes it as far as 32 overwrites.  Talk about secure.

---

### Post by Lysander10 on 2007-12-28
I have the same problem, I'm in need of an application that can securely wipe files and free space. I ran a search with Synaptic and found a program called "secure-delete". From the description, it looks like it fits the bill. Problem now is, I'm not sure how to use it. If anybody on here does, please let me know.

---

### Post by Lysander10 on 2007-12-28
I answered my own question. To wipe free space, you type this at the command prompt: 

Syntax: sfill [-fiIlvz] directory

Options:
        -f  fast (and insecure mode): no /dev/urandom, no synchronize mode.
        -i  wipe only inodes in the directory specified
        -I  just wipe space, not inodes
        -l  lessens the security (use twice for total insecure mode).
        -v  is verbose mode.
        -z  last wipe writes zeros, not random data.

---

### Post by Mud.Knee.Havoc on 2008-02-07
There's quite a bit more information on sfill and related programs here: [http://www.techthrob.com/tech/securedelete.php]("http://www.techthrob.com/tech/securedelete.php")

---

### Post by grikdog on 2008-09-16
> **ArBaDaCarBa said:**
> Just looking at the man page: shred doesn't work every time.




Isn't physical destruction of the hard drive the requirement BTW?

Reading further in man shred, you discover that shred does indeed work as expected when Ext3 runs in default (i.e., ordered data) mode.  You can verify that your Ext3 fs's are indeed running in default ordered data mode by examining the System log.

In addition, shred works by overwriting a file N times with random bytes from /dev/urandom.  If you want srm in particular, i.e., secure remove, which uses Peter Guttman's algorithm, you need the "secure-delete" package available via Synaptic.  Do a man srm after installing for details.

Both srm and shred have an optional zero fill pass.

So, if you have an additional, nonboot, nonsystem partition, plus TrueCrypt for Linux, plus the secure-delete package from Synaptic, you have the basic tools required to get your laptop impounded by any American airport security drama team.

---

### Post by rpglover64 on 2008-11-27
> **matthew said:**
> Edit: I want to add that the Slashdot article led me to several good ideas for wiping a hard drive completely, but I am still looking for a way to wipe free space while keeping undeleted data intact. I have seen Windows programs that do this, both in ntfs and fat32 such as this one among many: [http://www.heidi.ie/eraser/features.php](http://www.heidi.ie/eraser/features.php)

As far as I know, the simplest way to overwrite free space is to fill it, so maybe something like this would work:
```

for i in `seq 25` # write random data 25 times
do
  dd if=/dev/urandom of=file #make sure the file is on the partition
  # whose free space you want to fill
  # dd should exit when you run out of free space
  rm -f file
done
dd if=/dev/zeros of=file # now overwrite with zeros
rm -f file

```
Note: this will take a *while*.
Alternatively, you could use partimage to back up the partition (to some other hard drive) and then wipe where it was and restore it.

---

### Post by mahmater on 2008-12-10
well friends,I installed the secure-delete package and I want to add it to nautilus action so I have only to right click a file and overwrite it...but I don't know how!  I instaled nautilus action ?I clicked "add" but I don't know what to write in the parameter tab. wil you please help?

---

### Post by benny bronx on 2008-12-10
You can add the built-in shred function to the context menu using this:
[http://gnome-look.org/content/show.php/shred_file?content=66603]("http://gnome-look.org/content/show.php/shred_file?content=66603").  Also, if you search for bcwipe in this forum, you will find a thread that explains how to install this secure delete program from jetico.

---

### Post by mahmater on 2008-12-10
thanks. I've already found a lot of howtos about adding the built-in wipe.however,I'm told that secure delete is more developed and more efficient.I will follow your suggestions and look at the bcwipe ...

---

