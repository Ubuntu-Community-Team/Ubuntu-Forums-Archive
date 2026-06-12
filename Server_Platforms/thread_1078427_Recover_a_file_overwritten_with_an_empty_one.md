---
title: "Recover a file overwritten with an empty one??"
date: 2009-02-23
forum: Server Platforms
---

### Post by kenquad on 2009-02-23
Please forgive me posting a Debian issue here, but since the two OS's are so closely related and this community is so helpful, I thought it would be okay.

Without getting into too much detail, I have a file on my HD that accidentally got overwritten with an empty one of the same name.  This is a VERY important file!

Does anyone know of an "un-delete" utility that might be able to retrieve the previous version of the file??

Any help would be SO greatly appreciated!!!!

---

### Post by volkswagner on 2009-02-23
It may be gone.

Check to see if the OS auto-saved the old version.

```
ls -alt /directory/location/
```

You may see the file name only once.  If you see a second instance with a "~" you may be able to recover from that one.

like

filename.ext and filename.ext~

Good luck

---

### Post by cdenley on 2009-02-23
If this file is very important, DO NOT MOUNT THE FILESYSTEM unless you mount it read-only. If you simply leave the system running, if the data is still there, it will eventually get overwritten. What type of file was it? Was there a specific string of characters you can search for?

---

### Post by kenquad on 2009-02-23
Thanks for the suggestions, folks.  

There are no hidden ~ backups (where are those irritating things when I need them, anyway?).  

On the other idea, I think I see where you are going with this.  Through research since my last post, I discovered the strings command, which I used to dump the entire contents of /dev/hda1 into a whopping 11.5 GB text file.  

The good news is, grep shows at least certain parts of my lost data in here.  Yeah!

The bad news is, I haven't been able to figure out a way to get this absurdly huge file open in an editor so I can extract the needed part!  Bummer!  Also sorrowfulness!

Any ideas of how to do it?  Split the file maybe?  Just a 1.-something GHZ Pentium 3 server box with 256MB RAM.

---

### Post by kenquad on 2009-02-23
Update:

Got the file split up using the (get this) *split* command.  Grepped the resulting pieces to find that the data I needed was in the very first piece!  Pretty sweet.  Extracted it using Jujuedit on Windows.

Now there are still problems to work out, but these are related to the data itself and not relevant to this discussion.  Thanks for your help!

---

### Post by kenquad on 2009-02-24
Just an update, everything is recovered and working.

```
strings
```

One of the most useful commands I've ever seen!):P

---

### Post by Poleh on 2009-02-24
I love a story with a happy ending :) =D>

---

