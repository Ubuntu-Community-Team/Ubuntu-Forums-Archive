---
title: "Mounting a Windows Server Share with Mac File Names"
date: 2008-03-04
forum: Server Platforms
---

### Post by cballinger on 2008-03-04
I know, this is a mess.

I'm trying to mount a share that's physically located on a windows server. The issue I'm having is caused by Mac users on the system. They insist on using slashes in the filenames ex. "2007/2008 Folder". When I mount a share that contains one of these folders, I can't access it. The filename shows up: "2007?2008 Folder". I tried tab auto completing the folder name as well as escaping the characters, but no luck. 

Any help would be hugely appreciated.

---

### Post by dmizer on 2008-03-04
what is your current method of mounting?  fstab, or via places > connect to server?

---

### Post by cballinger on 2008-03-05
I'm using server without a gui so I'm using:

mount -t cifs -o username=user,password=pass //path/to/folder /mnt

I've tried several iocharset options, utf8 and iso-8859-1, neither have made a difference.

---

### Post by dmizer on 2008-03-05
well, i thought there would be an option for you, but it looks like there may not be.  from man mount.cifs:
>       **mapchars**
             Translate  six  of the seven reserved characters ([COLOR="Red"]not backslash[/COLOR],
             but including the colon, question mark, pipe,  asterik,  greater
             than  and  less  than  characters)  to  the  remap  range (above
             0xF000), which also allows the CIFS client  to  recognize  files
             created  with such characters by Windows's POSIX emulation. This
             can also be useful when  mounting  to  most  versions  of  Samba
             (which  also forbids creating and opening files whose names con-
             tain any of these seven characters). This has no effect  if  the
             server does not support Unicode on the wire.

however, from reading it more closely ... it's still worth a shot.  so try this:
```
mount -t cifs -o username=user,password=pass,**mapchars** //path/to/folder /mnt
```

---

### Post by cballinger on 2008-03-06
No luck, still shows the question marks and the files are inaccessible. So this isn't possible?

---

### Post by dmizer on 2008-03-06
> **cballinger said:**
> No luck, still shows the question marks and the files are inaccessible. So this isn't possible?

i don't know ... i suspect there is probably a way, but it is not likely to be very user friendly.

you can try escaping the backslash with a \134 like so:
```
mount -t cifs -o username=user,password=pass,mapchars //path/to/folder\134with\134backslash /mnt
```

if that works, the obvious drawback will be that you would have to mount the slashed directory instead of browse to it.  it might be easier to look into making the slash an illegal filename/foldername character on the server.

---

