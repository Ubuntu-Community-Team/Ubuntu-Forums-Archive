---
title: "usb?"
date: 2011-07-30
forum: Server Platforms
---

### Post by thobiasn on 2011-07-30
Is there a way to move files to a usb stick? If so please describe how. Thanks!

---

### Post by doperative on 2011-07-30
> **thobiasn said:**
> Is there a way to move files to a usb stick? If so please describe how. Thanks!

[Copy Files To USB Memory Stick]("http://ubuntuclips.org/videos_7.html")

---

### Post by Wim Sturkenboom on 2011-07-30
Drag and drop ? OK, it's a server without a GUI?

Usually memory stick are mounted in the directory /media, so check that directory.
Next use the *cp* command to copy files

examples:
copy a file
```

cp /path/to/yourfile /media/yourusbstick

```

copy a directory
```

cp -R /path/to/yourdirectory /media/yourusbstick

```

If you knew this but it does not work, you have to indicate where you're problem is.


PS
Don't forget to unmount before pulling it out
```

umount /media/yourusbstick

```

---

### Post by thobiasn on 2011-07-30
Yes its without GUI. Well i tryied doing as you said. But i can't find the location of the usb. I cd to media and when i check the did content this is what i get:
floppy and floppy0

---

### Post by crazy hatter on 2011-07-30
perhaps you may write a shell to fiand the files or the directory.if not ,use the command of 'mount&#8216;.personally&#65292;i think&#65292;it is too terrible for me to use ubuntu without GUI&#12290;

---

### Post by thobiasn on 2011-07-30
so i typed mount, sorry to be a noob, but what now? :p

---

### Post by Wim Sturkenboom on 2011-07-30
> **thobiasn said:**
> so i typed mount, sorry to be a noob, **but what now**? :pRead the output and determine which one is your usb stick. Or post the output here between [noparse]```
 and 
```[/noparse] ;)

Other steps if you can't find it there
check the last 15 lines of dmesg immadiately after you've inserted the usb stick
you should see a reference to /dev/sdX where X is a, b, c etc in one of those lines as well as to /dev/sdX1
```

dmesg |tail -n 15

```

you can then mount /dev/sdX1 like
```

mount /dev/sdX1 /media

```
and copy the files as indicated earlier; after that unmount with
```

umount /media

```


If you don't come right, post the output of the respective commands here.


PS:
when mounting on /media, the original contest of the /media directory will (temporarily) be unaccessible till you unmount

---

