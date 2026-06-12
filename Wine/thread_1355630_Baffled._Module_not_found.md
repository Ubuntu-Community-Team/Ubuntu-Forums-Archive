---
title: "Baffled. Module not found"
date: 2009-12-15
forum: Wine
---

### Post by oldmankit on 2009-12-15
I previously had wine running nicely on Jaunty. I've upgraded to Karmic and now it doesn't work.  Actually, several things don't work anymore.  I have deleted all ~/.wine directories, made a fresh install, and run winecfg from the terminal.  When I select the audio tab, it autodetects my settings, but the following error comes out at the terminal:

fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

Anyway, what's more, when I run 'wine progremon.exe', which used to run fine under Jaunty, now I get:

wine: could not load L"Z:\\home\\kit\\downloads\\progemon.exe": Module not found

I can't find any solutions on the net.  All help is appreciated.

oldmankit

---

### Post by oldmankit on 2009-12-16
bump

---

### Post by oldmankit on 2009-12-19
Bump bump

---

### Post by oldmankit on 2009-12-21
Bump bump bump

---

### Post by Soulcage on 2009-12-21
The error looks like what happens when you misspell the file or you forgot to cd to the directory.

---

### Post by oldmankit on 2009-12-22
> **Soulcage said:**
> The error looks like what happens when you misspell the file or you forgot to cd to the directory.

Thanks for the suggestion, but it's definitely the right location.

However, you got me thinking, and it ended up as a problem with permissions.  I'd copied the file or a FAT32 partition.

It's working fine now.

Thanks for your time to reply!

---

### Post by symon1980 on 2010-03-03
what do you mean? can you explain how you fixed the problem?

im getting the same error
"wine module not found"

---

### Post by oldmankit on 2010-03-05
> **symon1980 said:**
> what do you mean? can you explain how you fixed the problem?

im getting the same error
"wine module not found"

Soulcage wrote that the most likely error is that you have made a typo with the name of the program you're trying to open.

My problem was the I had copied the file from a FAT partition.  Linux file permissions don't work on FAT partitions.  If you don't know much about permissions, check this page out: [https://help.ubuntu.com/community/FilePermissions.]("https://help.ubuntu.com/community/FilePermissions")  When I copied the program onto  my ext3 linux partition, I didn't have executable permissions.  The following code would fix it:

```
sudo chmod 755 progremon.exe
```

(You may not need to use sudo.) Replace progremon.exe with the correct name and location of the program you're opening.

---

