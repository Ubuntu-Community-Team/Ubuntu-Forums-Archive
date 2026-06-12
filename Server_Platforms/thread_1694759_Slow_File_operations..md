---
title: "Slow File operations."
date: 2011-02-24
forum: Server Platforms
---

### Post by hkphooey on 2011-02-24
I've got a file server running with the following specs:
[LIST]
[*]Ubuntu 10.04 server. No GDM
[*]Disk partitioned into three segments. /, /boot and /home
[*]Disk is Raid 1 for /boot partition, and Raid 5 for the other two partitions, using mdadm, but not LVM
[*]ext4 filesystem on all partitions.
[*]2Gb RAM
[/LIST]

The file server is now starting to accumulate a lot of files, and as its being used by a lot of software developers they seem to get a lot of small files. One of the guys has 2 million files in his directory. I have a backup rotation scheme that makes 7 snapshot copies of this, with hardlinks, so his total is around 16 million files, with most of those being hardlinks. That's about 60Gb of files in total. 

So, I've noticed that file operations have now become very slow. Deleting one of these subdirectories with 2 million files takes around half an hour. ( rm -rf /subdir ). Doing a chmod on it takes around one hours (chmod -R user:user /subdir). Doing a hardlink copy takes around two hours (cp -al /subdir1/* /subdir2 )

So my question. Is this normal? If so, what is the cause? Is it the software RAID, ext4 journalling? Or a combination? 

I'll have access to the server again on Tuesday, so I'm trying to get a series of 'things to try' on it arranged before then.

---

### Post by elico on 2011-02-25
if it's small files you will might want to consider using
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

---

### Post by rubylaser on 2011-02-25
There are a couple decent ideas on this page.
[http://antmeetspenguin.blogspot.com/2010/12/linux-do-large-folder-sizes-slow-down.html]("http://antmeetspenguin.blogspot.com/2010/12/linux-do-large-folder-sizes-slow-down.html")

---

### Post by JRV on 2011-02-25
Run "top" from the command line.

If "gvfsd-metadata" is hogging your processor do this:

```

rm -rf /home/USERNAME/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

---

### Post by hkphooey on 2011-02-27
Thanks for the ideas. I'll try them out and let you know how it goes. Probably won't be migrating to ReiserFS though ... if it takes a couple of hours to do a directory listing, it might take a few years to copy all the files onto new disks! :-)

---

### Post by hkphooey on 2011-03-01
OK, trying these out now ... 

ReiserFS - migrating isn't an option, although I might try it out on a future install. Evidence for it being much faster seems somewhat contradictory. 

gvfs-metadata - doesn't really seem to be the case here. The system is a bare bones server, with no gui installed, and gvfs is installed with GNOME as I understand. When running top, the main CPU hog is whatever process is being used (eg ls, or chown) followed by the process controlling raid, so that seems to bear out my hypothesis. 

I was excited about the tune2fs dir_index option. However that was already enabled on the Raid container, as listed in the features section of ```
tune2fs -l /dev/md2
```

The noatime thing seemed to bear some fruit. I tried it on a single directory, noting the time a command took to run before and after. ie.
```
time du -h --max-depth /home/joe
chattr -R -A /home/joe
time du -h --max-depth /home/joe
```

The second run through this took around half the time, so there seems to be some saving there. I need to research this a little  more before I mount the whole raid partition with noatime. For reference its already mounted with relatime, which is 'halfway between' noatime and atime. 

More to come when I have it ...

---

