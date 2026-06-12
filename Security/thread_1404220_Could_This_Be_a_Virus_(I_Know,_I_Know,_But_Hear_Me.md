---
title: "Could This Be a Virus? (I Know, I Know, But Hear Me Out)"
date: 2010-02-11
forum: Security
---

### Post by Jonzer on 2010-02-11
Okay, I know the reaction mention of a virus is likely to provoke but please, hear me out. To set the scene, I am primarily a Windows Sys Admin of 11 years with a smattering of *nix knowledge garnered over the years. At home, I only have Ubunutu and OSX.

Now, I know I won't get any sympathy for my transport method for having received what I believe was a virus, as it must have been encapsulated in a zip/rar file containing mp3s downloaded from the internet.

I was using an 8GB flash drive to transfer said files from Ubuntu to Mac. After transferring the files I noticed, all of a sudden, that the root of the flash drive had started to fill up with files with nonsensical alphanumeric names and three letter file extensions (all extensions were different for each "file"). I pulled the drive and moved it back to Ubuntu. Not only was it full of these files (sorry, I cannot provide a screenshot but I was panicking as the drive contained sensitive, important data) but the sizes attributed to them by Ubuntu were nonsensical as it appeared to have more than the max 8GB. I was also unable to delete any of these files - they were greyed out and right clicking on them produced no context sensitive menu whatsoever. I moved my important files off and formatted, which solved the issue but it harked back to the "I Love You" virus of days of yore which, to my memory renamed all files as .VBS files (on Windows obviously), but whatever anomoly occured in this instance did appear to be renaming files and folders of its own accord.

The files in question had not been extracted from a zip/rar archive to my knowledge, but appeared after the fact. I scanned my Mac with iAntiVirus afterwards, which found no traces of virus. I have not yet scanned the Linux laptop, though I know already it will find nothing.

If nothing else, it is unusual, so I thought I would report it, like one does to the police for minor incidents that may later prove part of a larger case file. I would be interested to know if anything liek this has ocurred before to anyone's knowledge?

---

### Post by Kevbert on 2010-02-11
Sounds to me like file allocation table corruption rather than a virus. How old is the flash drive ? It may be on the way out.

---

### Post by Jonzer on 2010-02-11
I hear you. The drive is only 18 months old and a good make. I had only recently reformatted it using Windows a few months ago. I just ran a check disk utility on it there in Windows and it showed no errors. Like you, I am inclined to disbelieve it could be a virus (the same way I am inclined not to believe someone could create a perpetual motion machine). I will report back with any other developments should they come to light.

---

### Post by mkvnmtr on 2010-02-11
Put something else on the drive. Then on another drive download the same thing. That should tell you if it was the download or the drive.

---

### Post by Seq on 2010-02-11
Did you yank the drive out without ejecting it first?

---

### Post by Kevbert on 2010-02-11
Seq. Don't you mean unmounting it first ? You can do this by right-clicking on the drive icon and select unmount from the drop-down menu.
Even though the drive is a well known make, it could still be on the way out especially if it's in regular use (I had one that failed after just a year, by which time I had trouble reading and writing to it). A format only briefly resolved the problem.

---

### Post by saif_held on 2010-02-11
> **Jonzer said:**
> I just ran a check disk utility on it there in Windows and it showed no errors.

I wouldn't trust such tool/utility. Probably a bad section/sector.

---

### Post by Kevbert on 2010-02-12
Good point saif_held. Please take a look at [this]("http://www.linux.com/archive/feed/55366") article. With hard disks you can get badblocks showing up when you shut down the linux system (including any FAT partitions) but Windows chkdsk -v may not find them.

---

### Post by saif_held on 2010-02-12
Kevbert, I just read it. I hope the issue is fixed. If not wonder if there's a fix.

---

### Post by Kevbert on 2010-02-13
Saif_held. Unfortunately when you get badblocks showing, it normally is terminal, as it means the disk drive is on the way out. 
I see your from Amman, Jordan. Nice place, very friendly people. I've done the grand tour of Jordan. As well as Petra I've been to Jerash, Aqaba, Amman among other places and thoroughly enjoyed the place and hospitality.

---

### Post by saif_held on 2010-02-13
> **Kevbert said:**
> 
I see your from Amman, Jordan. Nice place, very friendly people. I've done the grand tour of Jordan. As well as Petra I've been to Jerash, Aqaba, Amman among other places and thoroughly enjoyed the place and hospitality.

I'm glad that you liked my country that much. We don't disappoint here and you're very welcome anytime. If you've decided to come here again give me heads up :)

---

