---
title: "deleted file from samba share"
date: 2008-08-17
forum: Server Platforms
---

### Post by guilly on 2008-08-17
I posted this thread in the beginners thread but with no feedback so I'll give it a shot here, a user has deleted some folders off a samba share. Is there some form of trash folder where the files go. I do not make backups of these folders but it would be nice to be able to get them back.

Thanks

---

### Post by HalPomeranz on 2008-08-18
There is no trash folder; the files have been deleted.

However, you may be able to use a forensic tool like foremost to recover some of the deleted files (foremost is in the repositories and you can install it via Synaptic or "sudo apt-get install foremost").

You can read the manual page once you install the package, but a typical command line would be:

```

foremost -vd -t all /dev/sda1

```

"-v" means "be verbose" so that the program tells you what it's doing
"-d" means follow indirect block pointers (a MUST for Unix file systems)
"-t all" means look for all file types that foremost recognizes (see the manual page if you want to look for specific file types)
"/dev/sda1" is the name of the file system you want foremost to search through-- this may be different on your machine

I should warn you that even if foremost is able to recover the data, it won't be able to recover the original file names.  So you'll end up having to look at the all recovered files in order to figure out what they are and whether you want them or not.

---

### Post by guilly on 2008-08-18
Ok, great thanks for the advice like I said the files weren't that important or else I would of made back ups. So I think I'll just cut my loses.

Is there a way to implement a trash on samba shares then maybe just run a weekly script to empty the trash ?? 

Thanks again.

> **HalPomeranz said:**
> There is no trash folder; the files have been deleted.

However, you may be able to use a forensic tool like foremost to recover some of the deleted files (foremost is in the repositories and you can install it via Synaptic or "sudo apt-get install foremost").

You can read the manual page once you install the package, but a typical command line would be:

```

foremost -vd -t all /dev/sda1

```

"-v" means "be verbose" so that the program tells you what it's doing
"-d" means follow indirect block pointers (a MUST for Unix file systems)
"-t all" means look for all file types that foremost recognizes (see the manual page if you want to look for specific file types)
"/dev/sda1" is the name of the file system you want foremost to search through-- this may be different on your machine

I should warn you that even if foremost is able to recover the data, it won't be able to recover the original file names.  So you'll end up having to look at the all recovered files in order to figure out what they are and whether you want them or not.

---

### Post by HalPomeranz on 2008-08-18
> **guilly said:**
> 
Is there a way to implement a trash on samba shares then maybe just run a weekly script to empty the trash ?? 


Apparently there is a way to do this, although I've never personally implemented it:

[http://www.techiesabode.com/show/show_tips_w.php?tip_id=20](http://www.techiesabode.com/show/show_tips_w.php?tip_id=20)

---

