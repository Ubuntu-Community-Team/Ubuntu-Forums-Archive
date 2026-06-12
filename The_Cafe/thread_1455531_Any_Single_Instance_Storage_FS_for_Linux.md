---
title: "Any Single Instance Storage FS for Linux?"
date: 2010-04-16
forum: The Cafe
---

### Post by CyberAngel on 2010-04-16
Hello,

I was wondering if there is such a thing for Linux (cause after some search I found that Microsoft has patented something similar).
A filesystem that is viable to store similar blocks of data using a single node on disk.
The initial question came to me while I was working with Dropbox and saw that it can upload some "huge in terms of size" files instantly.
That`s because it is checking the hash of the file and if someone else has already uploaded the file, it is not re-uploading it.
A company like Dropbox must have invented their own technologies, but I guess something like this, is something that the Storage specialists must have already think as it is a very efficient way to store the data and saving a lot of space.

---

### Post by jp7x7 on 2010-12-15
Sorry this is so late in coming.  No doubt you have found these for yourself, but just in case anyone else stumbles on this thread, there is:

[LIST]
[*]lessfs  ([http://www.lessfs.com/wordpress/](http://www.lessfs.com/wordpress/))
[*]opendedup  ([http://www.opendedup.org/](http://www.opendedup.org/))
[/LIST]

Probably others too but I am aware of at least these.

---

### Post by CyberAngel on 2010-12-16
Hey!

Thank you very much for these links!!! :)
In fact, I didn't do much of research after that post so I didn't know those projects!!
I will check them now though cause I am experimenting with storage these days!! :D

Thanks again for the reply!! It's never too late as you see and this will give answers to more people googling the same issue :)

---

### Post by Daveski on 2010-12-17
> **jp7x7 said:**
> 
[LIST]
[*]lessfs  ([http://www.lessfs.com/wordpress/](http://www.lessfs.com/wordpress/))
[/LIST]


I have played with lessfs, and I think it is getting pretty good now. Little tricky to understand when setting up, but once you have got your numbers right it performs really well.

---

