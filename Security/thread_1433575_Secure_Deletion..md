---
title: "Secure Deletion."
date: 2010-03-19
forum: Security
---

### Post by zozza on 2010-03-19
I am using srm - rm v3.1 (c) 1997-2003 by van Hauser / THC <vh@thc.org>
 - to securely delete.

I am wondering if there are other programs people prefer or any criticisms they might have with srm?

Thanks.

---

### Post by Grenage on 2010-03-19
*Shred* is another option, but it's not as secure as srm.

P.S: There are some critiques of srm - [http://ubuntuforums.org/showpost.php?p=4407671&postcount=10](http://ubuntuforums.org/showpost.php?p=4407671&postcount=10)

The post is old, they may no longer be relevant.

---

### Post by Dayofswords on 2010-03-19
i know of none for linux

but i use eraser for windows (the older version)
[http://eraser.heidi.ie/](http://eraser.heidi.ie/)
you can choose how many times pusdorandom data overwrites the file i want gone
100x = gone gone!

---

### Post by dogdo on 2010-03-19
In the default trash file browser when i click 'empty trash' it says these items will be 'permanently lost'-are these files recoverable?

---

### Post by Dayofswords on 2010-03-19
it means you cant get it back without trying, the data is still there, but waiting to be used

---

### Post by HermanAB on 2010-03-19
Howdy,

It depends on your threat level.

If you are only defending yourself against your little kid sister, then use shred.  
If you are a business owner and you are worried about losing financial information, then encrypt your disk drive (use the alternate install CD).  
If you are doing work for the government, then contact your national security establishment and they will tell you what to do, but it will also amount to encrypting the whole disk plus few other configuration changes.

---

### Post by doas777 on 2010-03-19
> **dogdo said:**
> In the default trash file browser when i click 'empty trash' it says these items will be 'permanently lost'-are these files recoverable?
yes and no. when you delete a file, it;s like ripping out the table of contents from the front of the book. the chapter you wanted to delete is still there, but you can't find what page it is on, so you need to flip through the pages until you find it.

I've had pretty good luck recovering deleted files off several platforms, but once they start getting scribbled on, you may need to repair the file a bit.
there are also tools like spinrite, that can adjust weaker magnetic bits (an overwritten block will have a stronger and a weaker signal, so just amp the weaker) which makes the job a bit easier.

earlier this year a man was conviced for having possession of a file that he had deleted more than a year ago, because the feds undelete tools were able to recover it.

here is some info about linux file wiping:
[http://www.linux.com/archive/feature/135944](http://www.linux.com/archive/feature/135944)

personally I use wipe, but I need a good free space wiper (I don't like the way sfill works).

---

### Post by rookcifer on 2010-03-19
> **Grenage said:**
> *Shred* is another option, but it's not as secure as srm.

Reference?  Shred does exactly the same thing as srm.  Both of them merely overwrite files with either random data or zeroes.  The difference is the secure-delete package can overwrite directories and free disk space.  Shred cannot.

OP, another option is bcwipe, but it's not in the repos.  You will have to get it from the BestCrypt website.  It works well, but is not open-source, which is my only complaint against it.  It's essentially the same as the secure-delete package in features and functionality.

---

### Post by Soul-Sing on 2010-03-19
Maybe the best way to get rid of super confidential stuff is to encrypt it.

---

### Post by doas777 on 2010-03-19
> **leoquant said:**
> Maybe the best way to rid of super confidential stuff is to encrypt it.
true, but you have to make sure that a plaintext version never existed on the system. many ency systems crypt existing files, so you still need to wipe the unciphered version.

---

### Post by Ijan on 2010-03-19
> **Dayofswords said:**
> 
but i use eraser for windows (the older version)
you can choose how many times pusdorandom data overwrites the file i want gone
100x = gone gone!

If the files you want to erase are stored on an NTFS and you want to erase individual files not the whole partition IMHO you better use Windows and Windows tools. - Or do other people here do have a sufficent level of confidence in the existing OS-NTFS drivers?

The additional security of using multiple passes and random data instead of zeroing out the unwanted blocks just once is BTW disputed for years.

If you're not paranoid it's probably a waste of time: [http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

I don't know if the advanced options of erasing FS metadata and freespace as provided by some Windows tools are made available by OS-tools in an equally safe and convenient way for Linux and it's commonly used file systems as well. Does sb know?

> Maybe the best way to get rid of super confidential stuff is to encrypt it.

I'd say that it's quite a difference if a file is deniably and irretrievably gone, or just one of both or even neither of both and just inaccessible as long as you don't have an existing key or password as is the case with encrypted files.

---

### Post by OpSecShellshock on 2010-03-19
Storage media comes cheap these days. You can always go with physical destruction.

---

### Post by Ijan on 2010-03-19
> **OpSecShellshock said:**
> Storage media comes cheap these days. You can always go with physical destruction.
That sure will give you all smiling faces at the security gates if you smash your notebook-hdd in the Fahd International Airport lobby before having it checked as it contains confidential business information, or even more if you are a Dissident somewhere.

---

### Post by uRock on 2010-03-19
And we wonder why the landfills are overflowing with junk....

I have used Shred, it seems good enough for me

---

### Post by ApEkV2 on 2010-03-20
> **Ijan said:**
> The additional security of using multiple passes and random data instead of zeroing out the unwanted blocks just once is BTW disputed for years.

And now with ssd's there is zero need for multiple passes, thus renders random data unneeded as well. 
Where'd the good times go?

---

### Post by HermanAB on 2010-03-20
All you need to securely delete files is LUKS and a brick.  Encrypt all your data with LUKS.  When you need to delete it, hit yourself upside the head with the brick so you forget the password.

---

### Post by Kinstonian on 2010-03-20
> **Dayofswords said:**
> i know of none for linux

but i use eraser for windows (the older version)
[http://eraser.heidi.ie/](http://eraser.heidi.ie/)
you can choose how many times pusdorandom data overwrites the file i want gone
100x = gone gone!

Just so you know...

1.  With modern hard dries you only need to overwrite data once before it's gone.  The reason why the government requires more is just in case someone figures out a way to do recover after multiple writes again.

2.  Because of [Volume Shadow Copy](http://blog.szynalski.com/2009/11/23/volume-shadow-copy-system-restore/), if you're using Windows Vista or 7, I wouldn't be so sure your data is unrecoverable... even after 100 overwrites.

---

### Post by km0r3 on 2010-03-20
I commonly use ```
shred -u [filename]
```to securely delete sensitive files.

Until now I never heard of `srm` and I was wondering which of both is more "secure". Doing a forum search spitted out something quite useful: [**Wipe VS Shred - Your opinion?**]("http://ubuntuforums.org/showthread.php?t=868747")
Though I doesn't really answer the question which of both is more secure, just popularity.

---

### Post by doas777 on 2010-03-21
> **HermanAB said:**
> All you need to securely delete files is LUKS and a brick.  Encrypt all your data with LUKS.  When you need to delete it, hit yourself upside the head with the brick so you forget the password.
I like that. I may have to use it next time I'm arguing with a user about ency.   
cheers

---

### Post by zozza on 2010-03-21
> **Grenage said:**
> *Shred* is another option, but it's not as secure as srm.

P.S: There are some critiques of srm - [http://ubuntuforums.org/showpost.php?p=4407671&postcount=10](http://ubuntuforums.org/showpost.php?p=4407671&postcount=10)

The post is old, they may no longer be relevant.

I wonder if any other posters saw this link.  The secure delete program seems to have last been updated in 2003 (according to the website) so the complaint may well be valid.

What do other people think?

> And now with ssd's there is zero need for multiple passes

SSD's???

> I don't know if the advanced options of erasing FS metadata and freespace as provided by some Windows tools are made available by OS-tools in an equally safe and convenient way for Linux and it's commonly used file systems as well. Does sb know?

Indeed with Eraser using XP slack space can it claims be deleted.  How does this work in Ubuntu?

---

### Post by doas777 on 2010-03-21
> **zozza said:**
> I wonder if any other posters saw this link.  The secure delete program seems to have last been updated in 2003 (according to the website) so the complaint may well be valid.

What do other people think?

SSD's???

Indeed with Eraser using XP slack space can it claims be deleted.  How does this work in Ubuntu?

well I won't speak to superiority specifically without the code and the wherewithall to evaluate it as an expert, but a dead project is kind of worrisome. on the other hand, it is a very simple process as I understand it, so perhaps no updates are needed.

ssd => solid state disk. the next generation of hard drives. they are flash memory rather than a magnetic medium, and have no moving parts, so they are much faster than the current spinning platter disks. in fact ssds are more like chips than disks.

in linux, it seems that the freespace wipe algoritm (at least the one sfill uses) is to write a series of psudeorandom data to a file that is the exact size of the partitions freespace. then it deletes that file, and does it all over again. if somthing goes wrong however, you may not get the file deleted correctly, so i don;t particularly like this algorithm.

bleachbit has an new option for freespace wiping that I want to check out. I think it may overwrite each block independently instead of working on all the freespace at once.

---

### Post by rookcifer on 2010-03-21
> **zozza said:**
> I wonder if any other posters saw this link.  The secure delete program seems to have last been updated in 2003 (according to the website) so the complaint may well be valid.

What do other people think?


As long as the file system is set as data=ordered, you can securely remove files.  If you still don't feel comfortable, you can merely erase all free space, which will assure its destruction.



> SSD's???

Solid State Drives.  The future, basically.



> Indeed with Eraser using XP slack space can it claims be deleted.  How does this work in Ubuntu?

You can do the same.

---

