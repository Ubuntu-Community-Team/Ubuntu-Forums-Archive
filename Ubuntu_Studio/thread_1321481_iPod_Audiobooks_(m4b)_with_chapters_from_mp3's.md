---
title: "iPod Audiobooks (m4b) with chapters from mp3's"
date: 2009-11-10
forum: Ubuntu Studio
---

### Post by pathos_84 on 2009-11-10
Long time reader, first time poster.

**My goal:** To create iPod ready Audiobooks with chapter markers from a series of mp3's using only the command line. Let's assume that, for whatever reason, I don't have the source media (CD, tape, etc)

**Rationale:** I recently acquired a 5th generation iPod Nano. As those familiar with iPods might know, book files are appropriately tagged with the Audiobook media type to avoid getting mixed in with music. They are further broken down into chapters in the iPod menu interface for individual selection. 

I have been able to calculate the length of each individual chapter as an mp3 (exiftool), combine them (mp3wrap), and convert them to m4a/m4b (pacpl + lame + faac). So, in the end, I have the entire book as a m4b and the position at which each chapter begins. 

Currently, I am using pacpl to create m4a's of each individual chapter. Then, I turn to a Windows tool (Chapter and Verse) to stitch the whole thing together with chapter markers. Using Windows generally disgusts me when I have Ubuntu command line tools at my disposal. Help me. :(

Here are some resources I have found informative:
Background on the file format - [http://en.wikipedia.org/wiki/M4b](http://en.wikipedia.org/wiki/M4b)
Marking chapters, sorta - [http://forums.ilounge.com/showthread.php?t=202606](http://forums.ilounge.com/showthread.php?t=202606)
The Windows tool: [http://lodensoftware.com/chapter-and-verse/](http://lodensoftware.com/chapter-and-verse/)

Thanks in advance.

---

### Post by pathos_84 on 2009-11-11
In the meantime, I figured I should post a quick howto on converting mp3's to m4a's.

**First, install the necessary packages:**
```
sudo apt-get install pacpl lame faac mp3wrap
```[B]
Optionally combine all mp3's into one:[/B]
```
mp3wrap combined.mp3 file1.mp3 file2.mp3 file3.mp3 ...
```[B]
Finally, covert mp3's to m4a's:[/B]
```
pacpl --to m4a combined.mp3
```pacpl conveniently preserves the ID3 tag of the original mp3 in the m4a. Awesome. 

This is much easier than previously developed methods on this forum:
[http://ubuntuforums.org/showthread.php?t=180073](http://ubuntuforums.org/showthread.php?t=180073)

---

### Post by kerzane on 2010-06-03
Any success with this? Or any other solutions? This would be great, make a very powerful resource out of open source audiobook collections.

---

### Post by pathos_84 on 2010-06-07
> **kerzane said:**
> Any success with this? Or any other solutions? This would be great, make a very powerful resource out of open source audiobook collections.

I have yet to test it, but an app called M4Baker was developed by another forum member which looks pretty damn slick. Props to him.

Details: [http://ubuntuforums.org/showthread.php?t=1431384](http://ubuntuforums.org/showthread.php?t=1431384)

---

### Post by Calgarym25 on 2010-10-01
Does anyone know how to convert an iPod Audiobook (M4B) to an MP3?  My friend bought the iTune version of a book, but I do not have iTunes or an iPod, but I do have an MP3 player (cowon J3), but it does not play M4B files. Is there anything I can do?  I have found many free software sites, but I get an error everytime I try to open the file after it downloads.

---

### Post by Lighthorse01 on 2011-09-04
> **Calgarym25 said:**
> Does anyone know how to convert an iPod Audiobook (M4B) to an MP3? My friend bought the iTune version of a book, but I do not have iTunes or an iPod, but I do have an MP3 player (cowon J3), but it does not play M4B files. Is there anything I can do? I have found many free software sites, but I get an error everytime I try to open the file after it downloads.
 
   Sony soundforge will convert them. load then save as

---

