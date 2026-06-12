---
title: "chmod command changed directory status to unknown"
date: 2011-03-27
forum: System76 Support
---

### Post by wazoo on 2011-03-27
I copied over a bunch of files (from a backup drive) to my new Nettop. Love the Nettop, but found that the permissions of some of the files wouldn't let me write to them. 

I thought I issued the right command from my home directory:
chmod -R u+w,go-w Documents/

which would, I thought, recursively give me the ability as user to read and write my files. Not sure what that "go-w" did.

Result? I can now read and write my files - with one big problem. The folders lower than the first level under Documents are now "unknown file types" for Nautilus, and won't open under anything else graphical. I can still move around in a terminal window.

How do I fix this - telling my system that directories are directories?

---

### Post by isantop on 2011-03-28
What are the owner and groups of all of the files?

---

### Post by wazoo on 2011-03-28
myname:myname

---

### Post by isantop on 2011-03-29
Can you browse and access them normally from the terminal?

---

### Post by wazoo on 2011-03-29
Yes I can. But graphically - whether in Nautilus or other programs - directories turn into files.

---

### Post by isantop on 2011-03-30
Do you still have the source files from the backup? You might consider copying them over again and starting over. I'm not exactly sure what's happened there. i can look into it, but it would probably be faster just to recopy.

---

### Post by wazoo on 2011-03-30
Yes, I was hoping to avoid that. I suspect I did something to "sticky bits."

---

### Post by alfalfa55 on 2011-03-31
> **wazoo said:**
> I copied over a bunch of files (from a backup drive) to my new Nettop. Love the Nettop, but found that the permissions of some of the files wouldn't let me write to them. 

I thought I issued the right command from my home directory:
chmod -R u+w,go-w Documents/

which would, I thought, recursively give me the ability as user to read and write my files. Not sure what that "go-w" did.

Result? I can now read and write my files - with one big problem. The folders lower than the first level under Documents are now "unknown file types" for Nautilus, and won't open under anything else graphical. I can still move around in a terminal window.

How do I fix this - telling my system that directories are directories?

This problem is not due to "sticky bits".  The problem is that "directories" use the permissions for "browsing" which means looking inside the directory without known a specific file.  You can correct the problem by bringing up a terminal and doing:
```

cd ~/Documents
find  .  -type  d  -print0 | xargs -0 chmod g+wx

```
The "0" is a zero not an upper case o.
if this fails with the GUI tool, repeat but change the 'g' to 'o'.  

The "go-w" was removing "write permission"  for both  "Group" and "Other".  Directory use the permissions slightly different than a regular file.

---

### Post by wazoo on 2011-05-08
Thank you! I wound up copying everything over, so didn't check back on this. But your explanation makes sense. I appreciate your taking the time.

---

