---
title: "What would happen if....."
date: 2009-07-07
forum: The Cafe
---

### Post by dragos240 on 2009-07-07
Since we linux users can make 2 folders for example, called folder A and folder a, in the same directory, what would happen if we tried to copy this to a flash drive, and put 2 documents in each, what would a windows computer do? Windows cannot create 2 folders that are the same name, even if they are different cases. For example,

If I tried to create folder hello-world and HeLlO-WoRlD, in windows, I would get an error, In linux. There would be 2 folders that are case-sensitive. What would happen?

---

### Post by Tibuda on 2009-07-07
If the Flash drive filesystem is FAT or NTFS, I don't think you'll be able to create the two folders. I have to test it.

---

### Post by wojox on 2009-07-07
I think it would use an array folder a and a(1)

---

### Post by Gizenshya on 2009-07-07
> **wojox said:**
> I think it would use an array folder a and a(1)

^^ what he said.

and in doing that, it would probably rename them to that if you changed anything.

Ubuntu will let you create folders in FAT and NTFS volumes with names that would conflict in a non-case-sensitive OS.

---

### Post by Tibuda on 2009-07-07
```
20:43:43 /media/KINGSTON$ ls
20:43:47 /media/KINGSTON$ touch tmp
20:43:52 /media/KINGSTON$ ls
tmp
20:43:52 /media/KINGSTON$ mkdir Tmp
mkdir: cannot create directory `Tmp': File exists
20:44:04 /media/KINGSTON$ ls
tmp
20:44:06 /media/KINGSTON$ 
```

---

### Post by dragos240 on 2009-07-07
It seems it's a matter of filesystems not OS'. I wonder if you could somehow create 2 different folders with the same name, but different cases in a FAT filesystem. Does someone know how?

---

### Post by Gizenshya on 2009-07-07
Know how?  It's simple.  right-click, and create folder named whatever.

Then, right-click again, and create another one with the same name, but one or more cases different.

For example, I have "TEST" and "test" in my shared NTFS volume as I type this.

Or, use the terminal and type in, for example:

```
$: mkdir TEST
$: mkdir test
```

and verify with dir

---

### Post by Tibuda on 2009-07-07
> **dragos240 said:**
> It seems it's a matter of filesystems not OS'. I wonder if you could somehow create 2 different folders with the same name, but different cases in a FAT filesystem. Does someone know how?

Try to create the folder in a Linux FS, and move it to the Windows FS. Something like:
```
mkdir -p ~/tmp/tmp
mkdir ~/tmp/Tmp
mv ~/tmp /media/KINGSTON
ls /media/KINGSTON/tmp
```
I'll try it now.

---

### Post by Gizenshya on 2009-07-07
^^^ why?

just use mkdir.  no need to do any of that.

---

### Post by dragos240 on 2009-07-07
> **Gizenshya said:**
> ^^^ why?

just use mkdir.  no need to do any of that.

/media/disk$ mkdir OOOOO
mkdir: cannot create directory `OOOOO': File exists

The directory already in there was ooooo not OOOOO, it seems it knows.

---

### Post by Tibuda on 2009-07-07
> **Gizenshya said:**
> ^^^ why?

just use mkdir.  no need to do any of that.

I have already tried only mkdir in my previous reply, but it didnt worked. Move the two folders from Ext4 to Fat won't work also.
```
20:54:08 ~$ mkdir -p ~/tmp/tmp
20:54:08 ~$ mkdir ~/tmp/Tmp
20:54:08 ~$ ls tmp
tmp  Tmp
20:54:08 ~$ mv ~/tmp /media/KINGSTON
mv: inter-device move failed: `/home/danielrmt/tmp/Tmp' to `/media/KINGSTON/tmp/Tmp'; unable to remove target: Is a directory
20:54:08 ~$ ls /media/KINGSTON/tmp
tmp
```

---

### Post by dragos240 on 2009-07-07
Same result.

---

### Post by Tibuda on 2009-07-07
Gizenshya, you said you are testing in NTFS. My guess is that NTFS is case-sensitive. That's correct?

** opens google

---

### Post by Gizenshya on 2009-07-07
I'm on wubi, installed through Vista.  terminal of ubuntu 9.04, writing the below on Vista's NTFS volume.

```
gaijin@gaijin-desktop:/$ cd host/test
ME@Me-desktop:/host/test$ mkdir TEST
ME@ME-desktop:/host/test$ mkdir test
ME@ME-desktop:/host/test$ mkdir TeSt
ME@ME-desktop:/host/test$ mkdir TEst
ME@ME-desktop:/host/test$ mkdir tEsT
ME@ME-desktop:/host/test$ dir
test  tEsT  TeSt  TEst	TEST
ME@ME-desktop:/host/test$ 
```

---

### Post by dragos240 on 2009-07-07
> **Gizenshya said:**
> I'm on wubi, installed through Vista.  terminal of ubuntu 9.04, writing the below on Vista's NTFS volume.

```
gaijin@gaijin-desktop:/$ cd host/test
ME@Me-desktop:/host/test$ mkdir TEST
ME@ME-desktop:/host/test$ mkdir test
ME@ME-desktop:/host/test$ mkdir TeSt
ME@ME-desktop:/host/test$ mkdir TEst
ME@ME-desktop:/host/test$ mkdir tEsT
ME@ME-desktop:/host/test$ dir
test  tEsT  TeSt  TEst    TEST
ME@ME-desktop:/host/test$ 
```

You still use dir? ls is where it's at!

Also echo * does the trick too.

---

### Post by Tibuda on 2009-07-07
[quote="http://en.wikipedia.org/wiki/NTFS"]Allowed characters in filenames:
In Posix namespace, any UTF-16 code unit (case sensitive) except U+0000 (NUL) and / (slash).
In Win32 namespace, any UTF-16 code unit (case insensitive) except U+0000 (NUL) / (slash) \ (backslash) : (colon) * (asterisk) ? (Question mark) " (quote) < (less than) > (greater than) and | (pipe)[/quote]

So NTFS is case sensitive in Posix systems and insesitive in Win32?

My curiosity is burning me. I'll format my flash drive to NTFS and see if it works.

Gizenshya: can see that folders from Windows Explorer?

---

### Post by Gizenshya on 2009-07-07
> **danielrmt said:**
> Gizenshya, you said you are testing in NTFS. My guess is that NTFS is case-sensitive. That's correct?

** opens google

ooops, misread it at first. Ugh, this thread is confusing lol.  all the negatives and OS/FS combos :p

I assumed that NTFS would be the same as FAT in that.  In retrospect, apparently that wasn't such a safe assumption...

*awaits response from your google visit*

---

### Post by Gizenshya on 2009-07-07
ooops, double-post.

how do I delete this?

---

### Post by Gizenshya on 2009-07-07
> **dragos240 said:**
> You still use dir? ls is where it's at!

Also echo * does the trick too.

old windows habit :(

---

### Post by dragos240 on 2009-07-07
> **Gizenshya said:**
> ooops, double-post.

how do I delete this?

Report your post and request it to be removed in the reason box.

---

### Post by Gizenshya on 2009-07-07
> **danielrmt said:**
> So NTFS is case sensitive in Posix systems and insesitive in Win32?

My curiosity is burning me. I'll format my flash drive to NTFS and see if it works.

Gizenshya: can see that folders from Windows Explorer?

win32.  OK, stupid question time!  Does that include 64-bit?

I haven't tried reading it with Vista yet.  I suppose I'll restart and try, though.

So, for FAT (FAT32?) though it is case-insensitive regardless?

---

### Post by Tibuda on 2009-07-07
I formated my flash drive to NTFS, and created two folders with the same name:
```
21:23:48 ~$ cd /media/KINGSTON
21:23:52 /media/KINGSTON$ ls
21:23:52 /media/KINGSTON$ mkdir tmp
21:23:52 /media/KINGSTON$ ls
tmp
21:23:52 /media/KINGSTON$ mkdir Tmp
21:23:52 /media/KINGSTON$ ls
tmp  Tmp
21:23:52 /media/KINGSTON$
```

Then I opened the flash drive in my father XP laptop. Windows Explorer was able to see both tmp and Tmp folders, but I was not able to create a TMP folder (See screenshot).

---

### Post by Tibuda on 2009-07-07
> **Gizenshya said:**
> win32.  OK, stupid question time!  Does that include 64-bit
I don't know. I see no reference for 64 bit in that Wikipedia article.

---

### Post by dragos240 on 2009-07-07
> **danielrmt said:**
> I formated my flash drive to NTFS, and created two folders with the same name:
```
21:23:48 ~$ cd /media/KINGSTON
21:23:52 /media/KINGSTON$ ls
21:23:52 /media/KINGSTON$ mkdir tmp
21:23:52 /media/KINGSTON$ ls
tmp
21:23:52 /media/KINGSTON$ mkdir Tmp
21:23:52 /media/KINGSTON$ ls
tmp  Tmp
21:23:52 /media/KINGSTON$
```Then I opened the flash drive in my father XP laptop. Windows Explorer was able to see both tmp and Tmp folders, but I was not able to create a TMP folder (See screenshot).

How interesting. But there's something I don't understand, if you created 2 folders with the same name in linux, why did windows try to create the other folder?

---

### Post by Tibuda on 2009-07-07
> **dragos240 said:**
> How interesting. But there's something I don't understand, if you created 2 folders with the same name in linux, why did windows try to create the other folder?

I have tried to create it, not Windows. But it didn't worked. Looks like Windows is case-sensitive when writing to NTFS, but insensitive when reading.

---

### Post by dragos240 on 2009-07-07
> **danielrmt said:**
> I have tried to create it, not Windows. But it didn't worked. Looks like Windows is case-sensitive when writing to NTFS, but insensitive when reading.

Can it open both folders and load a different file from each?

---

### Post by TBOL3 on 2009-07-07
other way around.  Windows is insensitive when writing, but sensitive when reading.  Weird.

---

### Post by Tibuda on 2009-07-07
> **TBOL3 said:**
> other way around.  Windows is insensitive when writing, but sensitive when reading.  Weird.
Weird...

> **dragos240 said:**
> Can it open both folders and load a different file from each?

I created a file in Notepad and saved it in Tmp/test.txt. Now the file is visible in both tmp and Tmp folders. When I open Nautilus, tmp is empty, and the file is only in Tmp. Then I create another file in tmp/test2.txt from Linux. Windows can only see the test.txt file in both folders. Looks like when I open the tmp folder, it opens Tmp.

---

### Post by dragos240 on 2009-07-07
> **danielrmt said:**
> Weird...



I created a file in Notepad and saved it in Tmp/test.txt. Now the file is visible in both tmp and Tmp folders. When I open Nautilus, tmp is empty, and the file is only in Tmp. Then I create another file in tmp/test2.txt from Linux. Windows can only see the test.txt file in both folders.

How about this, create a different document containing different text in both folders under the same name. So windows will open one, but read the other, I wonder what will happen.

---

### Post by Tibuda on 2009-07-07
> **dragos240 said:**
> How about this, create a different document containing different text in both folders under the same name. So windows will open one, but read the other, I wonder what will happen.

Renamed both files to test.txt, and added the folder name (tmp or Tmp) to its content. Windows can only read the file from Tmp.

My conclusion from this "experiment": don't rely on case insesitivity if you plan to use your files in Windows.

---

### Post by Gizenshya on 2009-07-10
I just happened to be in Vista and I came across the test folders (I forgot about them the other day) :P

so, discussion continued...

two folders named "test" but with different cases.  Ubuntu sees two folders.  In one I put "file 1.txt" (containing the text string "file 1"), the same thing in the other test folder, except with "file 2".  Vista recognized the folders as different (visually, anyway), BUT both folders had the same contents ("file 1.txt~" and "file 2.txt").  The tilde made the error you see, but when I opened it up with a test editor it had the correct "file 1" character string.  Again, the same contents were in each folder, one of each file, with file 1 having a tilde after its name.  (See Attachment)

This begs the question.. Did Vista physically copy the files, or are they simple the same files on disk, but referenced in two different places?  And, if the latter is true, is it possible to do this with larger files on a bigger scale and have, say, a 1 GB thumb drive with, say, 50GB of reported used space?  (But it actually is the same file listed over and over again). :p

Could this flaw be exploited somehow?  Hmmm..

I tried to get several sindows in one shot so I wouldn't have to post about 5 different attachments.  The shot is from Vista 64 Ultimate, with all available updates as of this post.

---

