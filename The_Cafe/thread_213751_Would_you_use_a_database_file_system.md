---
title: "Would you use a database file system?"
date: 2006-07-11
forum: The Cafe
---

### Post by dyssident on 2006-07-11
Whould you use a database file system? People seem to be very divided on wether these are the future of the filesystem or just an annoyance. 

To clarify, a dbfs is a filesystem based around searches instead of heirarchy. A concrete example: Gmail uses searches exclusively to find and organize emails. It uses labels instead of folders to organize emails so that an email can have an unlimited number of labels instead of existing in only one folder. Similarly, you use the search function to find what you want instead of remembering the location that you archived it or looking through an extremely long list of old emails. 

In the same way, a dbfs throws away the idea of a heirarchy of directories in favor of searching on keywords in the file or metadata about the file. This of course very similar to the way that Google handles doc and pdf files. The equivalent of folders would be created by defining search terms or attaching something akin to labels.

Here are some examples:
[http://www.apple.com/macosx/features/spotlight/](http://www.apple.com/macosx/features/spotlight/)
[http://ozy.student.utwente.nl/projects/dbfs/](http://ozy.student.utwente.nl/projects/dbfs/)
[http://en.wikipedia.org/wiki/WinFS](http://en.wikipedia.org/wiki/WinFS)
[http://desktop.google.com/](http://desktop.google.com/) (not really a file system)

---

### Post by prizrak on 2006-07-11
I as most others likely care very little about my file system. As long as it doesn't lose my files and doesn't consume resources it makes very little difference what is under the hood. The only time you really care about a filesystem is when you need to add another drive or make sure you can read/write to one.

---

### Post by banjobacon on 2006-07-11
Honest question: How would I hide my porn in a dbfs?

---

### Post by Engnome on 2006-07-11
> **banjobacon said:**
> Honest question: How would I hide my porn in a dbfs?

You tag it as "NOT PORN! DONT LOOK NOTTIN* INTERESTING...GO AWAY" :twisted:

---

### Post by maagimies on 2006-07-11
No, I like my files organized the way I want them, I don't need the  functionality of dbfs.
> **banjobacon said:**
> Honest question: How would I hide my porn in a dbfs?
Quite simple, as with normal filesystems, you create a file of certain size, cryptsetup it with some password, create a filesystem of your choice and mount it.
To members of your family, you can just say that you keep the "system backup binaries" in the file :)

---

### Post by Engnome on 2006-07-11
> **maagimies said:**
> No, I like my files organized the way I want them, I don't need the  functionality of dbfs.

Quite simple, as with normal filesystems, you create a file of certain size, cryptsetup it with some password, create a filesystem of your choice and mount it.
To members of your family, you can just say that you keep the "system backup binaries" in the file :)

Encrypting stuff to hide it is to bothersome, put it on a thumb drive and guard it with you life instead (or hide it) but maybe your XXX folder is to big for a thumb drive banjobacon? =P

BTW shouldn't this be a poll?

---

### Post by banjobacon on 2006-07-11
Besides the porn thing (:)), I'd like a database file system if it worked. Like prizrak said, I don't care about the fs, as long as my files don't get lost somehow. I'm quite disorganized, so maybe I'd like a dsfs.

---

### Post by dyssident on 2006-07-11
> **prizrak]I as most others likely care very little about my file system.[/QUOTE]

I think not caring about the filesystem is the best argument for a dbfs. Everyone loves to Google for what they need and have it automagically appear said:**
> 
put it on a thumb drive and guard it with you life instead


Ill move all of mine as soon as the 2TB thumb drives come out.

[QUOTE=Engnome]
BTW shouldn't this be a poll?
[/QUOTE]

Yes it should. And I should also think about such things before posting a thread.

---

### Post by Engnome on 2006-07-11
> **dyssident said:**
> 
Ill move all of mine as soon as the 2TB thumb drives come out.


THAT much XXX:p ?  (couldn't resist;) )

Anyway +1 one for dbfs here, tagging my files into virtual folder is a feature I would use.

There was some guy (darkmatter_ I think) on #ubuntuforums who was going to add virtual folder to GNOME somehow, think it was called tinz. They have #tinz at freenode anyway. Gonna go check it out. Would be great if this would be integrated into GNOME. Once people get used to it they'd love it think.

---

### Post by dyssident on 2006-07-11
> **Engnome said:**
> 
There was some guy (darkmatter_ I think) on #ubuntuforums who was going to add virtual folder to GNOME somehow, think it was called tinz. 


I wrote a google desktop clone in java (based on lucene) a while back, and it was wicked easy. From my point of view, the hard part is integrating into the os as a real file system, not just a search app. 

I suppose that something like GnomeVFS makes it much simpler, but to get all of the potential advantage, you would have to do things like replace the standard gtk file open dialogs with your own custom search and tag oriented version. Seems like alot of work.

---

### Post by sagarhshah on 2006-07-11
I wouldnt use a DBFS.

Although I would probably use Google Desktop if they released it for linux.
I hear google have a few people working on "Goobuntu" linux so hopefully they might come out with one.

Lets see

---

### Post by Engnome on 2006-07-11
> **dyssident said:**
> 
I suppose that something like GnomeVFS makes it much simpler, but to get all of the potential advantage, you would have to do things like replace the standard gtk file open dialogs with your own custom search and tag oriented version. Seems like alot of work.


Yeah alot of work, he had some real bad things to say about GNOME dev's to, so it probably won't happen as he described it.

Anyway I think his solution was neat, it wasn't a total abandoning of traditional fs just a way to make virtual folders that contained files with the same tag, one file could exist in many folder (sounds confusing) sounds kinda like those vista "stored searches" function we've been hearing so much about. Ah well as long as i quickly can find the file i'm looking for I'm happy. It feels like file managing is one of the most boring things to do with a computer and there is no real solution. I bet even in dapper+50 you still have to shuffle around files alot like we do to day. Maybe not move around manually but somehow keep track of them. 

"computer open the last .php file i was working with"

---

### Post by fluffington on 2006-07-11
I wouldn't use a database filesystem. I happen to like hierarchical organization of stuff. I like having exactly one place for something and knowing exactly how to get to it. For those rare instances where having a separate access path is handy (like having all my wallpaper-sized images in one place, or not wanting to have to remember the exact version number of whatever source code I'm working on), a symbolic link or two does the job nicely.

---

### Post by prizrak on 2006-07-12
> **sagarhshah said:**
> I wouldnt use a DBFS.

Although I would probably use Google Desktop if they released it for linux.
I hear google have a few people working on "Goobuntu" linux so hopefully they might come out with one.

Lets see

Goobuntu is a version of Linux that Google uses in-house it will never be released (nor is it needed).

> I wouldn't use a database filesystem. I happen to like hierarchical organization of stuff. I like having exactly one place for something and knowing exactly how to get to it. For those rare instances where having a separate access path is handy (like having all my wallpaper-sized images in one place, or not wanting to have to remember the exact version number of whatever source code I'm working on), a symbolic link or two does the job nicely.
I would assume that dbfs would accomodate that as well as having all the fun stuff that a db driven fs could provide. So for those who are like you and I who like to organize stuff it would allow us to do that  and those who don't organize anything could find things easily.

---

### Post by grusifix on 2007-09-22
Could it still make into Gutsy Gibbon? ;D
I bumped into this site [http://tech.inhelsinki.nl/dbfs/](http://tech.inhelsinki.nl/dbfs/) while googling for DBFS. I think that linux will always use "normal" fs under the hood, but why not give to the user a more convenient way to find the files.

Me needs DBFS!

---

### Post by hessiess on 2007-09-22
would be 100% imposoble to orgnise my files without the hirarcy

---

### Post by Npl on 2007-09-22
I dont have much interest in searching, keep the file-system simple & efficient - dbfs are neither.

Need searching for songs by artist, album, whatever: use a Player that uses a database. I dont need a filesystem that tries to accomplish everything.

---

### Post by happy-and-lost on 2007-09-22
My view on this subject...

There's no place like /home

---

### Post by Nonno Bassotto on 2007-09-22
I like having a hierarchical file system, but with the possibility to use virtual folders, which show every file with a certain tag.

---

### Post by Polygon on 2007-09-22
> **Nonno Bassotto said:**
> I like having a hierarchical file system, but with the possibility to use virtual folders, which show every file with a certain tag.

virtural folders could be useful, but i still like my standard hierarchical file system

---

### Post by starcraft.man on 2007-09-22
I don't see a need for a database file system. I keep all the folders I use often on my desktop/in places and none are more than 3 clicks away from me. I believe some people just need to be a bit better organized.

---

### Post by happysmileman on 2007-09-22
> **Npl said:**
> Need searching for songs by artist, album, whatever: use a Player that uses a database. I dont need a filesystem that tries to accomplish everything.

Agreed, Amarok creates database of my music, that's all I need... If I want to look at a PDF file or anything I know exactly where they are in /home/paul/

---

### Post by dyssident on 2007-09-22
i think we can all agree that the way apps like amarok use metadata is elegant and generally cool. just imagine if such functionality was built into standard libraries so that all apps could take advantage of it seamlessly, instead of each building their own indexing/metadata reading stuff like amarok has.

imagine telling gedit to open all files that mention walruses or telling gimp to open all images containing walruses. for that matter, imagine telling an command line app to do the same thing. unless you already had your filesystem organized this way, it would be time consuming to do, likely requiring some advanced 'find' knowledge.

im not a fan of tagging. its really a substitute for effective artificial intelligence. plus, metadata like tags doesnt travel well. few file formats, most notably many commonly used image types, dont have an equivalent of an ID3 tag.

files already tell you alot about themselves with their content. my hope is that one fine day well be able to use machine learning and image recognition to identify the main ideas of text, music and images so that tagging wont be necessary.

---

### Post by thisllub on 2007-09-22
None of this discussion focuses on the issue of efficiency.

Consider a system that requires storage of > 1 million documents. Databases handle this easily through B-Tree indexes that exponentially reduce filesystem accesses. File systems aren't anywhere near as efficient.

Have you ever tried "mv thesefiles/* thosefiles/." with thousands of files? How about files within a date range?
You can do it with find and xargs but it is clumsy.

A command "move thesefiles/* where dateaccessed between last monday and today to thosefiles" would be a HUGE improvement. 

A database file system that had efficient large binary file storage combined with SQL access and compatibility with the current hierarchical  structure and commands would be a huge leap forward.

---

### Post by Npl on 2007-09-23
> **thisllub said:**
> None of this discussion focuses on the issue of efficiency.I already said its inefficient :p
> **thisllub said:**
> 
Consider a system that requires storage of > 1 million documents. Databases handle this easily through B-Tree indexes that exponentially reduce filesystem accesses. File systems aren't anywhere near as efficient.You conviniently forgot to tell that those structures only contain a single property - be it filename, date, accessrights, etc..
you need 1 tree for EACH property. (Add another index for full-textsearch if you consider it part of a DBFS)
> **thisllub said:**
> Have you ever tried "mv thesefiles/* thosefiles/." with thousands of files? How about files within a date range?
You can do it with find and xargs but it is clumsy.

A command "move thesefiles/* where dateaccessed between last monday and today to thosefiles" would be a HUGE improvement. Dont forget you have a DB for the WHOLE partition, so you dont have to search 1000s of files which dates match, but all files on the partition (10000s? 100000s?). Then you also have to do a second search which path begins with "*currentdir*/thesefiles/" . And then take those files which were found in both searches.

> **thisllub said:**
> A database file system that had efficient large binary file storage combined with SQL access and compatibility with the current hierarchical  structure and commands would be a huge leap forward.There are ALOT of operations that will be way slower.
Browsing directors wil require DB-Search instead just grabbing a few lists, writing files will need updating alot of your B-Trees (not just one), those Btrees also need to be stored somewhere too (both on HDD and - if you want any useable performance - cached in Memory)...

Why would you want to force a damn-clumsy-in-many-respects DB upon everything? Im not arguing that there are also many cases where a DB is valuable, but in those cases, just teach the program to use a DB-library. Or in your case it would be thinkable to bind a DB to a directory you regulary need to do complex searching (but then you could just store/load directly into a Database as well).

In short - replacing filesystem is bad, augmenting where needed good.

---

### Post by thisllub on 2007-09-23
> **Npl said:**
> 
Dont forget you have a DB for the WHOLE partition, so you dont have to search 1000s of files which dates match, but all files on the partition (10000s? 100000s?). Then you also have to do a second search which path begins with "*currentdir*/thesefiles/" . And then take those files which were found in both searches.

That is not how an indexed search works. 

> **Npl said:**
> 
There are ALOT of operations that will be way slower.
Browsing directors wil require DB-Search instead just grabbing a few lists, writing files will need updating alot of your B-Trees (not just one), those Btrees also need to be stored somewhere too (both on HDD and - if you want any useable performance - cached in Memory)...

Some of that is true but compared to a journaling filesystem the difference in writes would not be that great. For individual document retrieval the performance would be greater  where there are large numbers of files.

> **Npl said:**
> 

Why would you want to force a damn-clumsy-in-many-respects DB upon everything? Im not arguing that there are also many cases where a DB is valuable, but in those cases, just teach the program to use a DB-library. Or in your case it would be thinkable to bind a DB to a directory you regulary need to do complex searching (but then you could just store/load directly into a Database as well).

In short - replacing filesystem is bad, augmenting where needed good.

I have to disagree.
I see no need to replace filesystems on partitions that are used for what the average user does i.e. a standard install, but once the numbers of files gets into the  thousands, the standard file management tools struggle to cope.

Applications like complex websites would be far easier to build, maintain and backup.

---

### Post by happysmileman on 2007-09-23
> **dyssident said:**
> i think we can all agree that the way apps like amarok use metadata is elegant and generally cool. just imagine if such functionality was built into standard libraries so that all apps could take advantage of it seamlessly, instead of each building their own indexing/metadata reading stuff like amarok has.

Agreed... Amarok should index our music... Kaffeine should index all your video... KWord should index all your ODF's etc... (Yes I'm just looking through KMenu for examples)

Having entire FS databased is stupid... No-one wants to database all the crap in /bin and /libs that they'll never directly use (well they'll use some stuff in /bin)

---

### Post by Npl on 2007-09-24
> **thisllub said:**
> That is not how an indexed search works. I worded it wrong, you are searching through file-**descriptors**, is that what you mean?. But tell me how you intend to search for a **range** of dates with one global index.
> **thisllub said:**
> Some of that is true but compared to a journaling filesystem the difference in writes would not be that great. For individual document retrieval the performance would be greater  where there are large numbers of files.and why would you think so? In an hierarchical filesystem you can arrange the filedescriptors in an sorted list or BTree aswell, giving it an edge if all required files are only in a couple directories.

> **thisllub said:**
> I have to disagree.
I see no need to replace filesystems on partitions that are used for what the average user does i.e. a standard install, but once the numbers of files gets into the  thousands, the standard file management tools struggle to cope.Depends **highly** on what you want to do with it. Other than having complex searches on a big number of files I dont see the point of it.

---

### Post by Sluipvoet on 2007-09-24
I keep my /home folder tidy and organised with hierarchial folders and subfolders. I know exactly where to look for something.
I just can't image doing the same with a DBFS.

PS. This labels vs. folders thing kinda reminds me of the epiphany bookmarking system. And that Epiphany bookmarking system made me switch from GNOME to KDE.

---

