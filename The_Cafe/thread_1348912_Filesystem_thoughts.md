---
title: "Filesystem thoughts"
date: 2009-12-07
forum: The Cafe
---

### Post by yester64 on 2009-12-07
I like ext4 a lot. But like windows, there is something i hope to see in the future to emerge in a filesystem.
Case. You have a lot of files (a lot, >100K picture files). If you contain them in one folder, the slow down pretty good the performance just by scanning all the files in once you open the folder.
Of course you could move files into different folder to organize them, but would it not be nice to tag images so that you can store them in one place and get them displayed by tag. That would be not only applied to pictures, but to any kind of file information.
Documents, Logs etc...
I heard a while ago that the mac operating system suppose to go that way. Not really sure since i don't use a mac.
On Windows it was always a pain to have to many files in one folder since it clocked the process just by reading in the information from each file.
Haven't figures out so far, how i can improve performance under ext4 or if there are limits.
If not, would be that not be something that can come to fruits in the future?
Or how do you store your documents and how many files do you place in your folders?

---

### Post by NoaHall on 2009-12-07
100k? All my picture files are at least 2 MB.
Oh, I see what you mean now. You mean 100000 images. 
And there's always the terminal.

---

### Post by PurposeOfReason on 2009-12-07
A lot of the bottleneck you're experiencing is what your HDD is capable of.

---

### Post by yester64 on 2009-12-07
> **NoaHall said:**
> 100k? All my picture files are at least 2 MB.
And there's always the terminal.

ugh.. i meant 100.000, thats what happens if you think about cars.;)

---

### Post by NoaHall on 2009-12-07
> **yester64 said:**
> ugh.. i meant 100.000, thats what happens if you think about cars.;)

Cars? And 100.000 = 100 XD
Anyway, you could always mount /tmp/ or where ever thumbnails are stored to ram.

---

### Post by doas777 on 2009-12-07
it would at least be nice if you could stop thumbnail creation/indexing with the stop button, but alas...

I don;t like the idea of becoming dependent on metatagging. there are a lot of things about the concept that I don't like from a practical point of view.

---

### Post by skipsbro on 2009-12-07
I personally just let applications take care of organizing my files; this gets them all orderly and I don't have to think too hard about keeping them that way. Example, allowing iTunes and iPhoto to organize their documents.

---

### Post by Bölvaður on 2009-12-07
I'm not sure you are talking about filesystems but more of filemanagers (the programs that lets you brose your files).

You are much quicker getting a list of million files with ls than nautilus.
what is slowing down ls is writing the name of the file onto the screen, nautilus has much much more than that to slow it down.

btw ls is the list command which lists all the files and directories that are in the current directory you are placed in.

---

### Post by yester64 on 2009-12-07
> **Bölvaður said:**
> I'm not sure you are talking about filesystems but more of filemanagers (the programs that lets you brose your files).

You are much quicker getting a list of million files with ls than nautilus.
what is slowing down ls is writing the name of the file onto the screen, nautilus has much much more than that to slow it down.

btw ls is the list command which lists all the files and directories that are in the current directory you are placed in.

Mm.. no, yes..
I took the approach from the the desktop. Like you would open a file in a folder by selecting **Places** / **Your Folder**.
If i am not totally wrong, it does have something to do with indexing files. All the content gets read once and stored. Or it will be always re-read at the next time you open the folder.
Yes, you can of course use a different program, but this would be the bread and butter of an OS. Just like Windows if you open a folder and it reads the files and gives you the information about the files.
I selected images as an example because they mostly come with thumbnails the system may create to display them as images in your folder.

(maybe there are tricks i don't know yet how to speed up the process)

---

### Post by Sam on 2009-12-07
> **NoaHall said:**
> Anyway, you could always mount /tmp/ or where ever thumbnails are stored to ram.

Well, it will regenerate every thumbnails on every boot, which I believe will eat more resource than just listing the files.

---

### Post by Sam on 2009-12-07
> **yester64 said:**
> Mm.. no, yes..
I took the approach from the the desktop. Like you would open a file in a folder by selecting **Places** / **Your Folder**.
If i am not totally wrong, it does have something to do with indexing files. All the content gets read once and stored. Or it will be always re-read at the next time you open the folder.
Yes, you can of course use a different program, but this would be the bread and butter of an OS. Just like Windows if you open a folder and it reads the files and gives you the information about the files.
I selected images as an example because they mostly come with thumbnails the system may create to display them as images in your folder.

(maybe there are tricks i don't know yet how to speed up the process)

Is it faster if you use the list view instead of the icon view ? Or by selecting a smaller zoom ?

---

### Post by Xbehave on 2009-12-07
I don't think your talking about filesystems (ext,zfs,reiser,etc) as such here, more "semantic file-systems", it's something kde4 is heading towards, by holding databases of tagging info so you can deal with "pictures" or "music" instead of files, however it's not really going to be usable until ~4.6 at the earliest (it really depends on how long it takes to write a program that can tag your photos, because the framework will be there in 4.4)

---

### Post by gashcr on 2009-12-07
What I would like to see is a file management system with tags ONLY. No locations. It would improve data access a lot. It could work in a fairly traditional way when saving files, but will look in a structure like this:

MAIN TAG (mimetype: Image, Music, Document, Mail, etc.)
SUBCATEGORY 1... N: work, vacations, year, (This would work like folders actually )
NAMETAG: Pretty much, file name :P

All this tags would be imperative, and some of them could be autogenerated to make it easier. Of course, you could add additional tags, at creation time (while saving the file) or later. 

Then, the file manager would be completely tag oriented :P. I think this would be work awesomely at least for /home

---

### Post by yester64 on 2009-12-07
> **Xbehave said:**
> I don't think your talking about filesystems (ext,zfs,reiser,etc) as such here, more "semantic file-systems", it's something kde4 is heading towards, by holding databases of tagging info so you can deal with "pictures" or "music" instead of files, however it's not really going to be usable until ~4.6 at the earliest (it really depends on how long it takes to write a program that can tag your photos, because the framework will be there in 4.4)

On KDE? Not Gnome? :(
But i think thats it. Perhaps i might switch then to KDE.

---

### Post by yester64 on 2009-12-07
> **gashcr said:**
> What I would like to see is a file management system with tags ONLY. No locations. It would improve data access a lot. It could work in a fairly traditional way when saving files, but will look in a structure like this:

MAIN TAG (mimetype: Image, Music, Document, Mail, etc.)
SUBCATEGORY 1... N: work, vacations, year, (This would work like folders actually )
NAMETAG: Pretty much, file name :P

All this tags would be imperative, and some of them could be autogenerated to make it easier. Of course, you could add additional tags, at creation time (while saving the file) or later. 

Then, the file manager would be completely tag oriented :P. I think this would be work awesomely at least for /home

I think that was what i wanted to express. But i am not sure about speed. I think that might be still a problem. Because it has to be indexed in manner that it doesn't slow down the machine. Meaning you having to wait for ever.

---

### Post by yester64 on 2009-12-07
> **Sam said:**
> Is it faster if you use the list view instead of the icon view ? Or by selecting a smaller zoom ?

No, just the standart. I haven't tweaked anything so far on the desktop. There might be still room to improvement on my part, as far as tweaking.
But i noticed that, if i open a folder, nautilus is generating thumbs at fly. Meaning it reads a file, then generated the thumb, then goes to the next file.
What happend was that i had a large folder and new files percolated after. Like popn in after another.
I think i explain it the complicated way.

---

### Post by gashcr on 2009-12-07
> **yester64 said:**
> I think that was what i wanted to express. But i am not sure about speed. I think that might be still a problem. Because it has to be indexed in manner that it doesn't slow down the machine. Meaning you having to wait for ever.

Well, not really, once index is made, it would be a snap. And, as the index is made little by little in normal scenarios, it wouldn't be too resource hungry. Only make sure to update de index with every change. I think this would be and interesting case to test non-relational DBs like Voldemort :P

---

### Post by Xbehave on 2009-12-07
> **yester64 said:**
> On KDE? Not Gnome? :(
But i think thats it. Perhaps i might switch then to KDE.
[NEPOMUK]("http://en.wikipedia.org/wiki/NEPOMUK_%28framework%29") is KDE based, but if the tagging plugins are useful there will probably be an effort to integrate it with gnome too (the tagging isn't GUI dependent), it all depends on the quality of the plugins tbh, having to tag 100 pictures manually is no better than using folders.

> What I would like to see is a file management system with tags ONLY. No locations. It would improve data access a lot. It could work in a fairly traditional way when saving files, but will look in a structure like this:
It seams silly to throw away locations, at worst they are simply one tag, but in reality without them CLI navigation and most of existing tools would become unworkable. It would be cool to have a filesystem that actually had tagging in it (not just file metadata but actual indexes/defragmenation by tags), if the kernel guys didn't hate reiser so much reiser4 would probably offer this through its plugins, the guy was always ahead of his time.

---

### Post by gashcr on 2009-12-07
> **Xbehave said:**
> 

It seams silly to throw away locations, at worst they are simply one tag, but in reality without them CLI navigation and most of existing tools would become unworkable. It would be cool to have a filesystem that actually had tagging in it (not just file metadata but actual indexes/defragmenation by tags), if the kernel guys didn't hate reiser so much reiser4 would probably offer this through its plugins, the guy was always ahead of his time.

Agree... but would be nice to see something like this, not necessarily in linux as we know it today :P

---

### Post by Xbehave on 2009-12-08
> **gashcr said:**
> Agree... but would be nice to see something like this, not necessarily in linux as we know it today :P
[http://sourceforge.net/projects/mysqlfs/files/](http://sourceforge.net/projects/mysqlfs/files/), it's fuse but it's still an interesting project and unless you have a very fast HDD the ioboundness probably doesn't matter. I think the solution is more likely to be something like [[IMG]http://tech.inhelsinki.nl/dbfs/thumbnail_dbfs-overview.png[/IMG] From here ]("http://tech.inhelsinki.nl/dbfs/"), however long term for a "user file system" (e.g a filesystem with just user files, no system files/configuration) a real dbfs would probably be a good idea.

---

### Post by NoaHall on 2009-12-08
> **Sam said:**
> Well, it will regenerate every thumbnails on every boot, which I believe will eat more resource than just listing the files.

You can easily create a script to change the mount point to your hard drive(and so save them) on shut down, and change it again on boot up.

---

### Post by Xbehave on 2009-12-08
> **NoaHall said:**
> You can easily create a script to change the mount point to your hard drive(and so save them) on shut down, and change it again on boot up.
If it's backed by hardrive storage, why not use readahead and filesystem caching that was designed to do this? That way the kernel can free up the ram space when other programs need it?

---

### Post by doas777 on 2009-12-08
> **Sam said:**
> Is it faster if you use the list view instead of the icon view ? Or by selecting a smaller zoom ?

the problem is that icon view is default, and if you have 20000 images in a dir, it will take 8-10 minutes before you CAN change the view type (since thumbnail gen appears to be a synchronous process, and won;t obey the stop button.) by the time I can change the view, there is little to no point, and it seems like the view settings switch back next time I open the folder.

---

### Post by doas777 on 2009-12-08
> **gashcr said:**
> What I would like to see is a file management system with tags ONLY. No locations. It would improve data access a lot. It could work in a fairly traditional way when saving files, but will look in a structure like this:

MAIN TAG (mimetype: Image, Music, Document, Mail, etc.)
SUBCATEGORY 1... N: work, vacations, year, (This would work like folders actually )
NAMETAG: Pretty much, file name :P

All this tags would be imperative, and some of them could be autogenerated to make it easier. Of course, you could add additional tags, at creation time (while saving the file) or later. 

Then, the file manager would be completely tag oriented :P. I think this would be work awesomely at least for /home

hmmm. that is the exact opposite of what I want. i would much rather just take responsibility for where I put stuff, then have to manually tag the millions of files I have archived. the only time i want to classify my data, is when I am deciding where to save it.

---

### Post by gashcr on 2009-12-08
> **Xbehave said:**
> [http://sourceforge.net/projects/mysqlfs/files/](http://sourceforge.net/projects/mysqlfs/files/), it's fuse but it's still an interesting project and unless you have a very fast HDD the ioboundness probably doesn't matter. I think the solution is more likely to be something like [[IMG]http://tech.inhelsinki.nl/dbfs/thumbnail_dbfs-overview.png[/IMG] From here ]("http://tech.inhelsinki.nl/dbfs/"), however long term for a "user file system" (e.g a filesystem with just user files, no system files/configuration) a real dbfs would probably be a good idea.

Wow, indeed a very interesting implementation

---

### Post by yester64 on 2009-12-08
> **Xbehave said:**
> [http://sourceforge.net/projects/mysqlfs/files/](http://sourceforge.net/projects/mysqlfs/files/), it's fuse but it's still an interesting project and unless you have a very fast HDD the ioboundness probably doesn't matter. I think the solution is more likely to be something like [[IMG]http://tech.inhelsinki.nl/dbfs/thumbnail_dbfs-overview.png[/IMG] From here ]("http://tech.inhelsinki.nl/dbfs/"), however long term for a "user file system" (e.g a filesystem with just user files, no system files/configuration) a real dbfs would probably be a good idea.

I like the DBFS system. It kinda what i i thought a system could look like.
Have to read more about it.
Is there anyone who uses it already?

---

### Post by renkinjutsu on 2009-12-08
I think i remember this being talked about in one of the Haiku videos.. Their filesystem would support tags and could be used to index and search files based on tags.. Pretty cool

---

### Post by froggyswamp on 2009-12-08
You seem to rely too much on filesystems and underestimate the job of the software.
A file/picture browser could/should just load the preview of the pictures asynchronously in a different thread with lower priority and process first off those pictures that are visible on the screen, when the user scrolls it should update accordingly. A reasonably good "if the user doesn't see the trees falling they sbouldn't fall" implementation would be good enough for >99% users imho.
Nautilus doesn't follow this rule, in fact, it doesn't follow its own preferences, if I set in its prefs to not load previews of files smaller than say 500KB it still loads the previews of movies! Not to mention other inconsistencies and plain bad decisions in this file browser.

---

### Post by The_Pirate_King on 2009-12-08
You could change the viewing method from "thumbnails" to "list".  This would make it so you can't see the individual images but it would greatly speed up the process of loading them.

---

