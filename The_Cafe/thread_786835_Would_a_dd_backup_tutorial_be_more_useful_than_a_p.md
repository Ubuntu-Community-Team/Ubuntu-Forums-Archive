---
title: "Would a dd backup tutorial be more useful than a partimage one?"
date: 2008-05-08
forum: The Cafe
---

### Post by aysiu on 2008-05-08
A while ago (a *long* while ago), I did [a backup tutorial on PartImage](http://www.psychocats.net/ubuntu/partimage) (the screenshots are from Hoary, so you can see just how old it is).

Recently, though, I've been using the *dd* command to back up things (my Sansa Clip before making it a bootable USB live Ubuntu "CD"; and my Eee PC before installing Ubuntu on it or removing unionfs from Xandros on it), and I find that process a lot simpler. Is it just me?

And, if it's not just me, do you think, for newcomers looking for a simple way to back up a drive or partition, a *dd* backup tutorial would be more useful than an updated PartImage tutorial?

If you click the PartImage tutorial link above, you'll see there are a lot of steps involved. For *dd*, I just did this off the live "CD": ```
sudo dd if=/dev/sda of=/media/disk/eeeoriginal.img
``` and to restore it ```
sudo dd if=/media/disk/eeeoriginal.img of=/dev/sda
``` No additional software to install. No complicated ncurses dialogues.

What do you think?

---

### Post by sefs on 2008-05-08
What i have wanted to see is a tutorial for dd or dd_rescue where it compresses the image to gz and then breaks it into suitably sized pieces, can you give us a tutorial on that?  Only using cmds that are available in ubuntu/linux, so that when push comes to shove there is something native to fall back on thats already in the system.

---

### Post by aysiu on 2008-05-08
> **sefs said:**
> What i have wanted to see is a tutorial for dd or dd_rescue where it compresses the image to gz and then breaks it into suitably sized pieces, can you give us a tutorial on that?  Only using cmds that are available in ubuntu/linux, so that when push comes to shove there is something native to fall back on thats already in the system.
I'd have to do some research and experimentation to write that tutorial. Frankly, I'm not that adept at options for command-line programs. I can usually do the basic command, but I don't know how to do neat tricks with all those hyphenated letters.

If I can figure it out, though, I might make such a tutorial.

---

### Post by aaaantoine on 2008-05-08
I strongly encourage such a tutorial, because for the past few months, I've been thinking that would probably be the simplest way to back up a disk drive (without actually knowing anything about DD, and being too scared to try it for myself).

I also encourage such a tutorial because I have a few concerns about the process.

1. Does it copy a literal disk image?  If I dd a non-full 120GB disk drive, should I expect the output file to be 120GB?
2. Can I use this method to copy the contents of my /home partition, rather than the entire device?
3. Can I use this method to copy the contents of a folder and its subfolders?

Also, I like sefs' idea.

---

### Post by aysiu on 2008-05-08
*dd* is quite flexible and can do at least #1 and #2, but I wouldn't want such a tutorial to overwhelm new users with options (to be overwhelmed, read the *man* page for *dd*).

---

### Post by FuturePilot on 2008-05-08
The thing about using dd is that it copies the empty blocks too. So if you have a large partition, you're going to have a huge image to store somewhere. But Partimage doesn't copy empty blocks so you end up with a much reduced in size image.

I would vote for Partimage.

---

### Post by agim on 2008-05-08
Yes, a dd backup tutorial would be incredibly useful.

---

### Post by pjkoczan on 2008-05-08
Doesn't dd copy absolutely everything, including magic numbers, metadata, superblock data, and UUIDs?

That might be what you want when doing a full partition backup, but it never hurts to consider the implications of doing so.

One thing you'd want to strongly advise would be to put the backup image on a different physical disk (not just another partition). That way if a disk goes bad, you wouldn't also lose the backup.

---

### Post by aaaantoine on 2008-05-08
Thank you, FuturePilot, that answers question #1 for me.

Also, thank you, aysiu, for your answer.  I'd probably do something along the lines of #2 rather than #1 or #3, though that's still a 72 GiB image according to my system monitor.  Gzipping the image would help tremendously...

[color=red]DISCLAIMER: Do not try any of these!  They are speculation only.[/color]

So my backup command would probably look like...
```
sudo dd if=/dev/sda3 of=/[backup-media]/backup.img
```

Can you pipe dd's output to the tar command?
```
sudo dd if=/dev/sda3 | tar -czf /[backup-media]/backup.tar.gz -
```

Or do you have to make it into a file first?
```
sudo dd if=/dev/sda3 of=/[backup-media]/backup.img
tar -czf /[backup-media]/backup.tar.gz /[backup-media]/backup.img
```

---

### Post by Daveski on 2008-05-08
> **FuturePilot said:**
> The thing about using dd is that it copies the empty blocks too. So if you have a large partition, you're going to have a huge image to store somewhere. But Partimage doesn't copy empty blocks so you end up with a much reduced in size image.

I would vote for Partimage.

I like Partimage too. Would compression on a dd file effectively remove the empty blocks and give you a filesize similar to a compressed Partimage image?

---

### Post by Atomic Dog on 2008-05-08
There is a reason people call dd "data destroy."  One slip of the finger and you can ruin your day.

OTOH, it does work well in certain instances -like backing up a thumb drive (for me anyway).

Also, isn't there a way to pipe it into a tar file? (as asked above)  I have never done it, but I understand it can be done.  Having a working example of the command would be nice of somebody for sure knows how to do it.

---

### Post by aysiu on 2008-05-08
Well, frankly, any kind of disk utility (GParted, PartImage, *dd*) poses a major risk to someone who is careless or ignorant. We've all had those "Doh! I should have done that..." moments in computing. I don't think it's specific to *dd*.

Based on some of the remarks I've read in this thread, I guess it's not an either/or. PartImage does have the advantage I'd forgotten about of not copying the empty blocks. So *dd* really is ideal for smaller drives (I've been using it for backups for 2 GB and 4 GB drives - I'd probably never use it for a 160 GB drive with only 30 GB in actual use).

---

### Post by Biochem on 2008-05-08
I recently converted to dd and find it more usefull than partimage.

to reduce the file size I first zeroed all empty block. The ratioanl is that having as many continuous 0 just make compression algorithm more efficient
dd if=/dev/zero of=/somewhere/in/my/home/folderzero.img

then
dd if=/dev/sda | bzip2 > /output/file.imj.bz2

or for encrypted backup:
dd if=/dev/sda | bzip2 | gpg --encrypt --recipient=myself --output=/media/backup/image.imj.bzip.gpg

I the output of the last one was a 32GB file from a 100GB hard drive. On a brand new computer 160GB HD (Windows not yet activated) the output file was a tremendous 3.3GB. so it not that bad. And yes I was able to restore the data.

It would be nice though if tar accepted input from pipe. I would gladly have split it to put on dvd. Maybe 7zip can do it.

---

### Post by flick152 on 2010-03-15
I use this page for dd reference:
[URL="http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"]
http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/[/URL]

---

### Post by handy on 2010-03-15
I think a Clonezilla tutorial is a better idea, as it does (from my experience) the job in an uncomplicated fashion that is more reliable over multiple file system types in combination.

Due to its simplicity, Clonezilla makes for a much more secure option, than using the dd command line.

Clonezilla uses dd on certain file systems itself.

---

### Post by Conu on 2010-03-16
> **flick152 said:**
> I use this page for dd reference:
[URL="http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"]
http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/[/URL]

Thanks for the link :) i have been looking for a good place to learn dd. And OP a dd tutorial is a fantastic idea.

---

### Post by Skip Da Shu on 2010-07-01
> **handy said:**
> I think a Clonezilla tutorial is a better idea, as it does (from my experience) the job in an uncomplicated fashion that is more reliable over multiple file system types in combination.

Due to its simplicity, Clonezilla makes for a much more secure option, than using the dd command line.

Clonezilla uses dd on certain file systems itself.

I'm leaning this way myself.  Which I've used once before to make an image... have forgotten how I did it.  I thought CZilla also used partimage but could be wrong.  I  know that my 74GB /dev/sda image was only about 14GB last time.

I am off to boot my Clonezilla CD and make a image of /dev/sda (swap, root, home partitions on it).

---

### Post by Paqman on 2010-07-01
Doing backups with dd might make sense if you had a really full drive, but it seems a bit ridiculous to copy all the blank space otherwise. I never really have drives more than about half full, so why use a method that takes twice as long as it needs to?

---

### Post by The Real Dave on 2010-07-01
Personally, I reckon a Clonezilla tutorial would be even more useful, considering how versatile Clonezilla is. 

As far as I know, Clonezilla uses both partimage and dd, depending on the circumstances. 

I use it whenever I need to backup my systems, or just to have a copy of a drive or partition. The latest version has some nice features, including making a lshw report when you make a backup :)

---

### Post by seshomaru samma on 2010-07-01
+1 
for clonezilla

---

### Post by capink on 2010-07-01
Since I moved to linux I don't need cloning anymore. I back up every thing using tar.

I only used cloning in the past for backing up the windows partitions since traditional back up did not work because some windows files need to be on spcefic sectors. But I can backup my linux partition using a simple tar command:

```
tar cvzpf /path/to/the/bakcup/file --one-file-system --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/* /
```

---

