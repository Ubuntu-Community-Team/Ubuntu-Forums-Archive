---
title: "Data move to server - prep - name conventions"
date: 2020-01-16
forum: Server Platforms
---

### Post by aljames2 on 2020-01-16
I have approx 150k files on my windows system storage drive.  Is it necessary to rename files & directories to remove spaces.  I'm not talking about system, application, program data.  Just static stuff like photos, music, PDFs, etc.  In the windows world all files and directories have naturally readable naming convention.  In Linux, we prefer no spaces:  my-homework-assignment  vs. My homework assignment    [https://ubuntuforums.org/showthread.php?t=2412915&highlight=file+convention](https://ubuntuforums.org/showthread.php?t=2412915&highlight=file+convention)
Is it a good idea to fix the naming convention on data who's new home is Linux?  If so, is there a script or utility that can assist with this task?

---

### Post by TheFu on 2020-01-18
Necessary? Probably not.  

If you will be scripting anything that works on multiples of those files, it will let your scripts be slightly less complex since passing in file globbed lists naturally will break filenames using spaces.

I use the **rename** tool. It uses perl regex language for pattern matching, which is extremely powerful. A full semester class on regex would barely scratch the surface of the capabilities for that tool.  Replacing spaces in filenames is trivial.  The harder characters are those used by your shell which have special meaning - %, *, $, !, &, and - if used at the beginning of filenames. [], {}, () can also cause dumb issues.  Create a file named "-this will be a problem.txt".  Try to delete it from a command prompt.  I'll wait. .... did you figure out how to delete that file?

There are slightly different acceptable characters between different file systems like NTFS and EXT2/3/4. This means that some filenames could cause issues on Linux that weren't any problem for NTFS.  OTOH, you can use ':' characters on Linux which are forbidden on NTFS.  **any** character can be used in native Linux file systems, but some will cause issues later, especially in scripts.  Many tools on Linux are created by regular people and not everyone will take the extra effort to ensure every possible character can be handled correctly.

---

### Post by aljames2 on 2020-01-18
My plan is to keep an windows (original) version backup of the storage date on a separate drive in case need to refer back to an original...likely an external NTFS drive that can be mounted in an emergency to recover something.  Other than that, I'm debating using a windows shell process to do the renaming or move it all over to the ubuntu server and do the renaming there.  It probably doesn't matter unless I want to keep a copy of both the original and new-name versions side by side on the windows ntfs backup drive, perhaps that could be useful.  

Most of the characters i have to deal with are "spaces" in filenames and directory names, and "()" at the end of some files like music files that indicate the version of the song such as "(Live)" or a numerical value inside the paren.

---

### Post by TheFu on 2020-01-18
I'd use **rsync**.

---

