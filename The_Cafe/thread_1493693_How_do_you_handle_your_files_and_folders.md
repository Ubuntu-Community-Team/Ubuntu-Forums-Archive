---
title: "How do you handle your files and folders?"
date: 2010-05-26
forum: The Cafe
---

### Post by Capta!nCrude on 2010-05-26
How do you handle your files and folders? Personally, I've been waiting for the semantic desktop for a long time, and as it seems today, there is still a long way to go. Recently I've been starting to play around with Latex, thus the reason for me to make this thread. I've always stored my documents in the Document folder, which seems quite reasonable and natural, however I feel that it's cumbersome to properly navigate and find my desired files through Nautilus. At the beginning when the folder is practically empty, it's no problem at all, but when the files start to pile up, the problems commence. 

I now have a dedicated PDF folder where I, obviously, store my PDF files. All other files are stored directly under the default Documents folder. This folder tends to grow rapidly, and I've encountered numerous times, accidentally deleting the wrong files, no more shift+delete for me, just because I find it hard to extinguish files with the same name, but different format.

I've tried various tools like Tracker and Beagle, but they haven't been completely satisfying, with some minor glitches and nuisances. The Gnome Activity Journal seems nice, did a brief testing on my previously Debian computer, now Ubuntu, but it's still not the best way to interact with files.  The way I do it now is a very tedious and inefficient way, a name every file after what it represents, my wallpaper folder is now named after what the picture displays instead of 172jfsp9odfigasg.jpg. This however takes a lot of time and effort, and I'm wondering if someone has found a solution to this problem. 

So before this thread gets out of hand I will state the question again;  How do you handle you files and folders?  Cheers!

---

### Post by Drenriza on 2010-05-26
Personally i make a folder on the Desktop. And store driffent files in driffent folders on the desktop. This way i can always quickly find what i want.
 
I rarely use the native folders to store any files in both windows, ubuntu.

---

### Post by Barrucadu on 2010-05-26
Here's a slightly trimmed down version of my home folder, as you can see I have fairly general-purpose directories in ~, which then break down into more specific ones. If I showed this to a greater depth, you'd see that this breaking down continues.

```
.
&#9500;&#9472;&#9472; backup -> /media/M2HDb
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; code
&#9474;   &#9500;&#9472;&#9472; c
&#9474;   &#9500;&#9472;&#9472; commonlisp
&#9474;   &#9500;&#9472;&#9472; elisp
&#9474;   &#9500;&#9472;&#9472; java
&#9474;   &#9500;&#9472;&#9472; pascal
&#9474;   &#9500;&#9472;&#9472; python
&#9474;   &#9492;&#9472;&#9472; scheme
&#9500;&#9472;&#9472; docs
&#9474;   &#9500;&#9472;&#9472; derivations
&#9474;   &#9500;&#9472;&#9472; essays
&#9474;   &#9500;&#9472;&#9472; org
&#9474;   &#9492;&#9472;&#9472; osdev
&#9500;&#9472;&#9472; graphics
&#9474;   &#9500;&#9472;&#9472; avatars
&#9474;   &#9500;&#9472;&#9472; misc
&#9474;   &#9500;&#9472;&#9472; photo
&#9474;   &#9492;&#9472;&#9472; wallpapers -> /usr/share/wallpapers/
&#9500;&#9472;&#9472; hurd
&#9474;   &#9500;&#9472;&#9472; git
&#9474;   &#9492;&#9472;&#9472; livecd
&#9500;&#9472;&#9472; music -> /share/eihort/music
&#9474;   &#9500;&#9472;&#9472; Music
&#9474;   &#9500;&#9472;&#9472; Musicals
&#9474;   &#9500;&#9472;&#9472; Podcasts
&#9474;   &#9492;&#9472;&#9472; Soundtracks
&#9500;&#9472;&#9472; projects
&#9474;   &#9500;&#9472;&#9472; erasmus
&#9474;   &#9500;&#9472;&#9472; fractalgen
&#9474;   &#9500;&#9472;&#9472; gnu
&#9474;   &#9500;&#9472;&#9472; mpd-utils
&#9474;   &#9500;&#9472;&#9472; uzbl
&#9474;   &#9492;&#9472;&#9472; wiipen
&#9500;&#9472;&#9472; tmp
&#9474;   &#9500;&#9472;&#9472; misc
&#9474;   &#9492;&#9472;&#9472; working
&#9500;&#9472;&#9472; video
&#9474;   &#9500;&#9472;&#9472; anime -> /media/M2HD/anime
&#9474;   &#9500;&#9472;&#9472; movies
&#9474;   &#9492;&#9472;&#9472; tv -> /media/M2HD/tv
&#9492;&#9472;&#9472; websites -> /media/M2HD/websites
    &#9500;&#9472;&#9472; barrucadu.co.uk
    &#9500;&#9472;&#9472; mawalker.me.uk
    &#9492;&#9472;&#9472; uzbl.org

```

For example, my wallpaper directory (to use your example) is broken down by where I got the wallpaper, along with a 'rotation' directory that my random wallpaper script uses:
```
/usr/share/wallpapers/
&#9500;&#9472;&#9472; Desktopography
&#9474;   &#9500;&#9472;&#9472; 2005
&#9474;   &#9500;&#9472;&#9472; 2006
&#9474;   &#9500;&#9472;&#9472; 2007
&#9474;   &#9500;&#9472;&#9472; 2008
&#9474;   &#9492;&#9472;&#9472; 2009
&#9500;&#9472;&#9472; Fractals
&#9500;&#9472;&#9472; Gaia
&#9474;   &#9500;&#9472;&#9472; 2007
&#9474;   &#9500;&#9472;&#9472; 2008
&#9474;   &#9492;&#9472;&#9472; 2009
&#9500;&#9472;&#9472; Interfacelift
&#9492;&#9472;&#9472; rotation

```

So I use a very structured and hierarchal method of sorting my files, and I find it works very well.

---

### Post by Capta!nCrude on 2010-05-26
@Drenriza

Seems like a good solution for projects you are currently working on, but what about Music, Wallpapers and Videos etc.


@Barrucadu


You have a very detailed and organized setup there, how well do you follow your hierarchy, when I try to set up such a scheme, it usually deteriorates because I find it anoying to browse through myriad of folders just to acquire a single file, and maybe I later need another file, that is deep into another folder subsystem. But I will definitely try it again.

---

### Post by Barrucadu on 2010-05-26
I follow it quite well; using it properly is second-nature now, though it probably helps that the system evolved from a disorganised mess rather than me suddenly thinking one day "I'm going to be organised!"

The process was more like: "I need a place to store my code", followed by a week or so later, "Hmm, it'd be convenient if I broke my code up by language", and so on.

---

### Post by ajgreeny on 2010-05-26
I also do more or less what Barrucadu does, and have done since I started using Windows 3.1, a long time ago.  Everything is to hand this way, but if I had not done it from the beginning it would now be almost impossible to sort things out.

As an example, all my photographs are in a main folder called "Pictures" and in this I have many subfolders, eg family, holidays, etc, some of which also have subfolders.  I find this hierarchical folder system so much easier than using tags on the photos when I download then from the camera's photo card.

Similarly, I have main folders for other Pics, ie not photos, for PDFs, for Audio recordings I've made, for music, for videos, a separate doc folder for Abiword, etc etc.  It may seem complicated, and as I say it would be almost impossible to set up now from scratch, with a home partition with 69GB used out of the 130GB total, but it works extremely well for me, and with that setup and using tracker occasionally, I can always find anything I want.

---

### Post by Phrea on 2010-05-26
> **Barrucadu said:**
> Here's a slightly trimmed down version of my home folder, as you can see I have fairly general-purpose directories in ~, which then break down into more specific ones. If I showed this to a greater depth, you'd see that this breaking down continues.

[...]

So I use a very structured and hierarchal method of sorting my files, and I find it works very well.

My respects, sir. I'd **love** to be able to do this.
Unfortunately I'm a a *very* chaotic person by nature. I've tried systems like this time and time again, but never been able to stick to it for very long.

---

### Post by lovinglinux on 2010-05-26
I use a mix of project folders and file type folders.

Documents that are not tied to a specific project are stored by file type. For example, downloaded PDF files are stored under the pdf folder, but pdf manuals I create for software I design are stored under each software project folder.

Sometimes I also save project files under the file type folders. For example in my pictures folder there is a *websites* sub-folder with several sub-folders for each site. Then I have symlinks from each web site sub-folder under the site project folder. So while I can browse each project images from their project folders, the images are actually saved in the pictures folder.

---

### Post by BrokenKingpin on 2010-05-26
I have a folder hierarchy similar to Barrucadu, which makes it pretty easy to find things. Sometimes I find the hierarchy getting quite deep and it is just annoying to get to the document I want. I have been using Microsoft OneNote at work, and I find it absolutely awesome for managing notes in one view, but unfortunately I haven't found anything nearly as good on Linux yet.

---

### Post by Capta!nCrude on 2010-05-27
What I find the most difficult, is to find a proper name for a folder or a sub-folder. For instance take the music folder as an example. It's hard to sort artists after genre, mostly because they a very vaguely defined. A band that fits in Rock might also fit in another category depending on album. Currently I have a Classical folder and a Soundtrack folder, the rest is just the artists and their corresponding albums in sub-folders.

I will install Gnome Activity Journal on this machine and simultaneously try to set-up a proper file-hierarchy.

---

### Post by Drenriza on 2010-05-27
> **Capta!nCrude said:**
> @Drenriza

Seems like a good solution for projects you are currently working on, but what about Music, Wallpapers and Videos etc.



All work related stuff goes in the left side of the screen, in their appropriate folders. Private stuff goes in the right side of the screen, in their folders.

I do have cairo duck installed. And iam trying to get used to use folders such as.

Documents,
Cristian (my normal user).
downloaded files.
music.
video.
pictures.

to use for private stuff. And then all work related stuff still goes on the desktop in the left side of the screen.

---

### Post by cguy on 2010-05-27
Is it possible that the tags I assign to files to be stored inside the files themselves?

Particularly the photos: I may tag them with the location, date, persons who were there, etc., but if these tags are stored in a local database, what's the point?
Photos are moved around or shared and I'd lose all the work.

I remember than in Windows XP you could right click on the photo, select Properties and add keywords of your own.
Were those stored inside the tagged files (EXIF data or smth)?

---

### Post by YuiDaoren on 2010-05-27
Here's how I organize:

+Yui
| random files, configs, quick code snippets
+ Documents
| | Random files
| + Accidentally created folder
| + Accidentally created folder 2
+ Music
| | Variety of music in folders essentially at random.
| + Accidentally created folder
+ Pictures
| | Images, files accidentally dropped here, soft links to files long deleted.
+ Accidentally created folder
+ Accidentally created folder 2
| | Files accidentally dropped in here, considered MIA unless I use a search.
+ Accidentally created folder
+ Desktop
| | Everything I'm currently working on, and everything I was working on but lost interest in. Dead soft links to old folders from an aborted attempt to organize.
| + Accidentally created folder
| + Recent downloads
| + Accidentally created folder 2
| + Accidentally created folder 3
| + OOo Docs
| | A pile of half-written stories and essays that belong in the Docs folder
| + Accidentally created folder 4

Hope this helps!

---

### Post by ajgreeny on 2010-05-29
I'm fascinated to know;  how do you "accidentally" make a folder?

---

