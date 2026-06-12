---
title: "Integrating with Nautilus/Archine Manager?"
date: 2010-03-10
forum: Ubuntu Dev Link Forum
---

### Post by Kopachris on 2010-03-10
I need to make a program to read and write VP (Volition Package) archives—not too difficult, since the spec is open and easy to implement—but I need to integrate it with File Roller (GNOME's Archive Manager).  Could anyone show me where to go to find details on doing that?  GNOME's dev library didn't have anything useful (or maybe I just wasn't looking hard enough).  Any help would be greatly appreciated.  Thanks!

In case you're curious, here's a bit of info about VP archives:
The VP format was invented by Volition Inc. to package multiple files into a single file while retaining the directory structure.  There is no compression.  This format was used for Volition's FreeSpace series, and is still in use by the FreeSpace 2 Source Code Project.  Currently, the SCP doesn't have any good modding tools for Linux.  I'm trying to remedy that.
The header of a VP file is always a char[4] with the value of "VPVP", followed by the version number, the offset to the file index, and the number of files.
```

char header[4]; //Always "VPVP"
int version;    //As of this version, still 2.
int diroffset;  //Offset to the file index
int direntries; //Number of entries

```After that comes all of the files, with no space or null-termination between them.  After the files is the index, which takes the form of a series of entries like this:
```

int offset; //Offset of the file data for this entry.
int size; //Size of the file data for this entry
char name[32]; //Null-terminated filename, directory name, or ".." for backdir
int timestamp; //Time the file was last modified, in unix time.

```So reading and writing these things isn't hard, I just don't know how to integrate it with File Roller.

---

### Post by Kopachris on 2010-03-11
Anyone?  All right, if I don't figure it out on my own and no one seems willing/able to help me, I'll just have to make it a standalone app.  How disappointing.

---

