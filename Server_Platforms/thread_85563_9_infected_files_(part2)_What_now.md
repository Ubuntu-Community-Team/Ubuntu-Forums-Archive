---
title: "9 infected files (part2) What now?"
date: 2005-11-02
forum: Server Platforms
---

### Post by user_stu on 2005-11-02
My previous post showed jumbled output from clamscan. Someone sugested I use the following:
clamscan -r -i --remove /

This completes fine and produces the output in the attached graphic.

So all the files it thinks are infected are related to Krita? Really? And it can't remove them... What do I do?

---

### Post by jrbj on 2005-11-02
[QUOTE=user_stu]My previous post showed jumbled output from clamscan. Someone sugested I use the following:
clamscan -r -i --remove /

This completes fine and produces the output in the attached graphic.

So all the files it thinks are infected are related to Krita? Really? And it can't remove them... What do I do?[/QUOTE]

From the ClamAV FAQ:
[http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)

> 
36. I get many false positives of Oversized.zip

    Whenever a file exceeds ArchiveMaxCompressionRatio (see clamd.conf man page), it's considered a logic bomb and marked as Oversized.zip . Try increasing your ArchiveMaxCompressionRatio setting. 


Someone correct me if I'm wrong, but I think you're ok.

---

### Post by user_stu on 2005-11-03
I installed Bitdefender for a second opinion and it returns the following. How do I know what I/O errors are? (The "9" could be virii or is that just coincidence?)


Results:
Folders           :733
Files             :2500
Packed            :35
Archives          :0
Infected files    :0
Suspect files     :0
Warnings          :0
I/O errors        :9
Files/second      :119
Scan time         :00:00:21

---

### Post by niko_ on 2005-11-03
I/O errors i guess are INPUT / OUTPUT errors

---

### Post by andlinux21 on 2005-11-03
looks like you're getting some false positives my friend:D

---

