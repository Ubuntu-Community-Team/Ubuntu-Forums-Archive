---
title: "HTML Links"
date: 2009-04-16
forum: Ubuntu Studio
---

### Post by Pakia on 2009-04-16
Any help would be appreciated,
I have my index.html file on my sda1 patrition.
I have a htm page on my sdb1 drive which is mounted through mnt
The folder is database
The file search.htm
I have made a link <a href="../mnt/database/search.htm"> in the index.html file

I`m sure it is a simple error somewhere can anyone help?

---

### Post by Stochastic on 2009-04-16
Well I'm still not sure exactly what your issue is, but it looks like that link is badly formed.

> **Pakia said:**
> I have made a link <a href"../mnt/database/search.htm"> in the index.html file

should probably be ```
<a href="../mnt/database/search.htm">
```

---

### Post by Pakia on 2009-04-16
I tried that it still does not point to the page in question? Do you have any other advice?

---

### Post by benj1 on 2009-04-16
first i would use an absolute address (from root) also file prefix 

```
<a href="file:///mnt/database/search.htm">
```

---

### Post by Pakia on 2009-04-16
Tried that still no luck. Any other suggestions? All highly appreciated.

---

### Post by benj1 on 2009-04-16
are you sure its in mnt, my second partition mounts in media/disk

---

### Post by Pakia on 2009-04-16
Am sure that is the way I set it up as I am using xubuntu. Have even tried full path home/bme/mnt/database/search.html and everything else I can think of. Your time appreciated

---

### Post by benj1 on 2009-04-16
when you cd to that path does it work? alternatively when you open it up in nautilus does it show that path?

also is it monunted ?

---

### Post by Pakia on 2009-04-16
I use thunar file manager I changed the permissions can get into the folder fine. Have a desktop shortcut and i have files in there.

---

### Post by benj1 on 2009-04-16
im guessing its the link from your home directory, is it a hard link or a symlink? 
also try using a path from root
eg
/mount/disk/database/search.html 

instead of through the shortcut in your home folder

---

### Post by Pakia on 2009-04-16
It is a hard link. Have tried through root to no avail.

---

### Post by Pakia on 2009-04-16
Is their an alternative to <a href=" in html to define a path?

---

### Post by benj1 on 2009-04-16
> **Pakia said:**
> Is their an alternative to <a href=" in html to define a path?

not as far as im aware
```
<a href="file:///path/path">path</a>
```
is the only way i am aware of to do it.

if you are using the full path, and the second hard drive is mounted i don't see why it wouldnt work.
the only things i can think of is a spelling mistake some where or something to do with the hard drive, try putting your search.htm file on your first hard drive and see if you can access it there.

---

### Post by Pakia on 2009-04-16
I came right in an unconventional way. I made a shortcut to the file which I placed in the folder where my index file is and it is re routing it to the second drive. Thanks for the help.

---

### Post by AinsleyKath on 2009-04-17
hi,
   Use the full path on the tag.


[Web Designers Chennai](http://yellowpages.sulekha.com/chennai/business-services/website-services/web-design/636.htm), [Web Designer Chennai](http://yellowpages.sulekha.com/chennai/business-services/website-services/web-design/636.htm), [Web Designing Chennai](http://yellowpages.sulekha.com/chennai/business-services/website-services/web-design/636.htm), [Web Development Company Chennai](http://yellowpages.sulekha.com/chennai/business-services/website-services/web-development/636.htm).

---

