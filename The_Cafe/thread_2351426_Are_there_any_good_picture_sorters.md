---
title: "Are there any good picture sorters?"
date: 2017-02-03
forum: The Cafe
---

### Post by zer010 on 2017-02-03
I'm sure many people have the same issue of having tons of pictures and not everyone is great at sorting them in the most organized way. 
A lot of these pictures probably don't have the most descriptive names other than maybe timestamps. Most people probably sort them into folders, but 
not every person does this with every single picture every single time, me being one of them.  In the end, you have a single directory with 100's even 1000's of 
photos in a jumbled mess.  

I was just wondering if anyone here has a good solution to sorting through the clutter and organizing it into something more manageable.
I had made a rough mock-up of something I'd like to see.  It borrows from the (infamous) file-picker.  Where as the fp has files/folders on one side and a preview on the right,
this shows pictures of a directory in either slideshow or manual next mode and all the user has to do is drag and drop the picture into one of the pre-chosen directories on right. 

Thoughts?

Picture is just something made in Gimp.

---

### Post by TheFu on 2017-02-03
Having 1,000s of files in any directory is asking for them to be lost should the directory "file" become corrupted.  File processing also slows down when there are that many files in a single location.

I organize my 130,000 photos by YYYY/MM/DD-event.
I learned that any program/DB that does these virtual organizations, not really on the file system, will eventually leave me with a data migration issue.  They write any extra info into their DB, not somewhere I can use it in 10 yrs. OTOH, with my system, a file system manages the most important metadata for me - date and location.  I don't spent much time on the filenames, except for the very best photos maybe 5 per day. I do keep the photos in order by using sequential names - **geeqie** has a powerful renaming capability.  I also might tag photos using exiftool with specific locations, keywords, etc. This is all done through scripts.

Any data that isn't kept either inside the image file itself or in the file system is useless as far as I'm concerned.

For slide shows, I tend to use either plex media server or nextcloud "gallery."

And don't forget backups: [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)

---

### Post by zer010 on 2017-02-03
Decent organization from the start, DB or not.  WHat I'm looking for is a way to sort that 100,000 in a jumbled mess into distinct directories.  Virtual organizations do no good if they don't invoke the mv command.

---

### Post by TheFu on 2017-02-03
I agree about the "move" aspect.
Steps:
[LIST=1]
[*]Sort by Create Date (any file manager can do this, but so can geeqie)
[*]Split files by year.
[*]Split files inside each year by month
[*]Split each set inside each month, by events
[/LIST]
The first two should take under 2 hrs.  Then it is time to eat the elephant ... perhaps 1 hr a day?  I've done this with lots and lots of huge projects.

BTW, I have about 4K photos from recent trips that still need to be organized beyond those 3 levels. My cameras create a new directory for each day. Created a few scripts that help me out, but they aren't safe for public consumption.  Basically a file renaming script to remove the useless parts of the filenames the cameras create and force everything to lowercase.

---

### Post by ajgreeny on 2017-02-04
I'm with TheFu here and I don't believe there is any application that can do what you want in a simple manner.
Or if there is such an application it has escaped me for many years.

I think you will simply have to "bite the bullet" and settle down with a few hours available and sort them; I think the "by-year" sort for a start is a good idea, then it will be up to you.

I have always sorted my photos manually into meaningfully named sub-folders of Pictures, eg Family, Holidays, etc etc, and also always download photos using the card reader and file-manager rather than allowing an application such as shotwell to do it for me.  I also avoid using tags as I have found in the past, much to my dismay, that any tags added by one application are possible (probably?) not usable by another application, and I do not wish to be tied to the same application all the time.

Enjoy your sorting; I expect you will come across a huge number of photos that you have totally forgotten about, if you're anything like me!

---

### Post by HermanAB on 2017-02-04
Have a look at Phatch.  It may help with some aspects of your problem.

---

### Post by The Cog on 2017-02-04
Why not just open two file manager windows side by side. In the left hand one show a large icon view into the unsorted pictures folder. In the right hand one, show a view into the folder containing all your sub-folders. Then drag/drop from images view on the left and  onto the appropriate folder on the right.

---

### Post by yoshii on 2017-02-21
If you have 32-bit Wine running, LupasRename is pretty useful for automated file renaming and automatic numbering of filenames and changing filetype extensions.  It's Windows freeware.  
Similarly, IrfanView has some menu commands for with keyboard shortcuts I think for copying or moving to a variety of preset directories.  It's also Windows freeware.  Both run OK on 32-bit Ubuntu Linux.  
I have used them.  They also work well in most versions of Windows.

---

### Post by mastablasta on 2017-02-22
> **The Cog said:**
> Why not just open two file manager windows side by side. In the left hand one show a large icon view into the unsorted pictures folder. In the right hand one, show a view into the folder containing all your sub-folders. Then drag/drop from images view on the left and  onto the appropriate folder on the right.

proabbly a split will also work (like dolphin has).

what abotu DigiKam?

Google can sort and make albums. not sure how good they actually are.

---

### Post by Wadim_Korneev on 2017-03-07
Linux may not have a ton of super advanced photo managers, but it has a few solid programs, the best of which is easily the near professional-grade digiKam.

---

### Post by TheFu on 2017-03-07
Last year at Southeast Linuxfest, there was a session about linux-based tools used by professional photographers.
"An Overview of Doing Professional Photography on Linux"
by  JT Pennington

The video should be on youtube by now.  For photo "ingestion" he listed a few tools, 
** Rapid Photo Downloader (can also thumbnail, etc as part of this)
** File Manager
** Incron - inode monitoring
** systemd.path
These were just to get the files into the locations he wanted to start working.

For library management, my notes have this:

Library Management
 ** Xnview-MP (like ACDSee)
 ** Aftershot Pro
 ** DigiKam
 ** Shotwell
 ** F-spot
 ** Picasa
 ** kphotoalbum
 * Other Utils
 ** exiftool
 ** imagemagick
 ** Luminance HDR
 ** CHDK Canon Hack Dev Kit
 ** Hugin ???

He was also very concerned about file corruption with bitrot.  I have a note to use ZFS for stuff like that since it is the only file system that actually validates what was sent to disk was actually written there. Data migration every few years helps too - anything that forces a complete read then write gives the disks internal protection method opportunities to correct and/or relocate blocks that are having issues.

---

### Post by Paddy Landau on 2017-03-09
> **zer010 said:**
> Thoughts?
This probably isn't quite what you're after, but it is a bit of lateral thinking.

Upload all your photos to Google Photos. If you choose the so-called "high quality", it gives you free unlimited space (it compresses images, but in my experience with no noticeable loss of quality). If you use "original quality", you'll have to pay for more than 15Gb space.

Google applies artificial image recognition, allowing you to search by all sorts of terms: beach, cat, people, etc. It will be of help if your images have the date and location in their meta-data. It's jolly clever. You can also manually create albums and move images into them, although the interface for doing this is still a little clunky.

Of course, you can also access your images through your Google account from any device with an Internet connection.

It's a thought.

---

