---
title: "Filename length suggestions"
date: 2018-07-20
forum: Ubuntu, Linux and OS Chat
---

### Post by jason.jackal on 2018-07-20
I am in the mist of converting over to Ubuntu/Linux, and was brainstorming about the max filename length of files. I am concerned that filename lengths might be too long for sharing with Mobile phones, tablets and other resources. Due to the latter, has anyone given much thought on this topic and if so - what issues if any have they seen.

Currently I am thinking that a 32 character filename length would be great. This is based on the MSDOS 8 character length.

---

### Post by wildmanne39 on 2018-07-20
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by TheFu on 2018-07-21
The limits for total path and filename are set by the kernel and file system used.   These limits on Linux are generous - I think 4096 for the total path.  I don't have any idea about the filename limit, but 255 characters seems reasonable.
/usr/src/linux-headers-4.4.0-130/include/uapi/linux/limits.h
shows:
```
#define PATH_MAX        4096    /* # chars in a path name including nul */
```

I've worked places long ago when 256 characters was the total path limit and we routinely overfilled that enough that we modified the length and rebuilt the kernels for all  connected systems - almost  1000 Unix systems.  This also meant rebuilding other code, since those headers are used by lots of normal applications and servers.

MSDOS is long dead.  I would ignore it.  Even FAT16 has extensions to allow much longer filenames.

[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) will probably be helpful in your quest.

All current smartphones run OSes based on Unix.  That means you can look up their file system limits and for Android, you can find the source code with limits.h where the PATH_MAX is set.

---

### Post by TheFu on 2018-07-23
Test it on your devices.

I created a directory patch over 280 characters long in my /tmp/ directory and put an mp3 files deep down it.  Then I copied this over to my Android phone on the internal storage. Check that everything copied and the mp3 file was there.  It was.

If you care about really long file names (not directories) too, test it.  Make a very long filename using the characters you normally would.  A few characters aren't allowed by different file systems, so those should be avoided to avoid problems. For example, avoiding :/\%|$~& characters is a good idea. Personally, I avoid tabs, spaces, newlines and all brackets/parenthesis.  Spaces make scripting just a little harder, so I avoid them and use _ where ever a space is.  Have a few scripts that fix filenames for that.

There is a file system limits table on wikipedia which lists these things for all the popular file systems linked above. Lots of answers inside there.

Test it.

---

