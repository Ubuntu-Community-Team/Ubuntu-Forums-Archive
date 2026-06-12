---
title: "Feature Request- Directory descriptions on hover."
date: 2019-05-14
forum: Ubuntu, Linux and OS Chat
---

### Post by vysero on 2019-05-14
Yesterday, we had a meeting at work to discuss our CodeBase architecture/layout. One of our directory's is named BMFamily and someone asked why. The answer was something like: "well that's where we keep the Linux apps". Of course that makes no sense... unless you knew that the Blackmore product line is all Linux based utilities and apps. We then discussed naming conventions and whatnot for a bit and of course my mind began to wander and wonder about a solution that wouldn't require altering the naming conventions, I thought: "It would be nice, if I could just hover over the directory and get a short description of it.". I wonder, what do you guys think, should Ubuntu include a feature like that?

---

### Post by TheFu on 2019-05-15
No need.

You can use **user extended attributes** for this, if you like.  File systems pretty much support this already.  Making any GUI program display the extattrs shouldn't be too hard, it will slow down all file and directory access however. Probably 50%.  I have ZERO interest in that.  When I say "shouldn't be too hard", I mean for someone to modify whatever GUI they use to access and display the extended attributes.  I don't know of any GUI that does this today.

Commands are **getfattr** and **setfattr**.  These are enabled by default in EXT4, but can be disabled at mount time. XFS and other Linux file systems have them too, but might use different commands to set/get them.

Or you could use hardlinks to have both names for the same file system object. 
```
$ ln BMFamily Linux_Applications
```
A symbolic link might be better, since hardlinks aren't easy to know about without looking at the inode reference counts.```
$ ln -s BMFamily Linux_Applications
```

Of course, the manpage for each command has more details on these things.

Doing something outside the file system is a terrible idea. MSFT did this with their "Libraries" which failed.  They failed because it only worked if you used MSFT GUI file choosers and there wasn't anything on the file system.  5+ yrs later, MSFT fixed their error by adding both hard and symbolic links to NTFS - like 40 yrs after Unix file systems had them.

I've been coding for 25+ yrs.  This issue isn't anything new. In 1993, we were writing multi-platform code (12+ platforms) in C/C++ and needed ways to clearly denote any specialized code for the platforms, cough , Windows, cough ,  that needed it.  For most of the Unix platforms, only a slight tweak to a #define or #include was needed.  If you look through the Linux kernel tree, you'll find how they deal with it.  Linux runs on all sorts of different hardware from Motorola, ARM, intel, AMD, Via, Mips, and probably 20 others.  Lots of well-considered examples, if I'm understanding the question.

---

### Post by TheFu on 2019-05-15
BTW, nobody here works for Canonical.

---

### Post by mastablasta on 2019-05-16
launchpad is the place for feature requests.

also how would the system know what is in the directory (description) unless someone told him what was inside. how would it know what is in the folder "legs" that i have? how would it know that these are my queries, photos and offers for washing machine legs?

---

### Post by vysero on 2019-05-16
No, I think you guys are over thinking it a bit. You wouldn't be hovering over the directory and seeing all the contents of the directory. The idea would be to have the ability to right-click a directory and select a 'set description' option. In which you would actually write out a description yourself s/t when a user hovers over the directory it should pop up that written description. So something like:

* user hovers mouse over BMFamily
* small descriptor window pops up: "The BM in BMFamily stands for Blackmore and apps/contents within this directory run under Unix like operating systems..."

that way someone won't go sticking application code in the wrong directory or, if they are interested, they can learn a bit about the directory just for kicks.

---

### Post by QIII on 2019-05-16
Hello!

While interesting discussions are encouraged, I want to make sure you noticed two points from posts above:

> BTW, nobody here works for Canonical.

and

> launchpad is the place for feature requests.

Nobody here, including the Staff, is in a position to add/delete/change features.

I you are just looking for a sounding board before you go to Canonical with an idea, then carry on.

---

### Post by TheFu on 2019-05-16
> **vysero said:**
> No, I think you guys are over thinking it a bit. You wouldn't be hovering over the directory and seeing all the contents of the directory. The idea would be to have the ability to right-click a directory and select a 'set description' option. In which you would actually write out a description yourself s/t when a user hovers over the directory it should pop up that written description. So something like:

* user hovers mouse over BMFamily
* small descriptor window pops up: "The BM in BMFamily stands for Blackmore and apps/contents within this directory run under Unix like operating systems..."

that way someone won't go sticking application code in the wrong directory or, if they are interested, they can learn a bit about the directory just for kicks.

And *extended user attributes* are the way you can have that. [http://man7.org/linux/man-pages/man5/attr.5.html](http://man7.org/linux/man-pages/man5/attr.5.html)
You would just need to make the GUI modifications to access that existing capability which is seldom, if ever, used.

---

### Post by vysero on 2019-05-16
> **QIII said:**
> Hello!

While interesting discussions are encouraged, I want to make sure you noticed two points from posts above:



and



Nobody here, including the Staff, is in a position to add/delete/change features.

I you are just looking for a sounding board before you go to Canonical with an idea, then carry on.

Yes I can read. Apparently this title is really getting a few of you worked up. However, from what I can tell changing the title of a forum post after the post has been made isn't possible. Perhaps it would be worth while for you to go ahead and remove the "feature request" string from the title so that none of the other robots begin to loop.

---

### Post by SeijiSensei on 2019-05-16
Linux supports filenames up to 255 characters in length. Maybe you should use more descriptive directory names than "BMFamily".

---

### Post by TheFu on 2019-05-16
> **SeijiSensei said:**
> Linux supports filenames up to 255 characters in length. Maybe you should use more descriptive directory names than "BMFamily".

There are 2 parts to a full filename.  The directory and the filename.  The maximums for each are controlled by the file system. Most have the filename part limited to 255 bytes, while the directory part is either unlimited or 4KB limited.  Just depends on the OS and file system.

[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)  This is always a handy link.

In the old days (1995), the total path was limited to 255 bytes on many systems. The program/project I was working on at the time ran up against that limitation so we had to recompile everything from the kernel up to support longer paths.  We ended up buying a source code license for a commercial DBMS and my jobs was to recompile it for all 12 platforms that we supported so the longer paths could be used.

---

