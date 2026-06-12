---
title: "Adding UCE Software to Ubuntu 13.04"
date: 2013-08-08
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-08-08
On one of my machines, I'm needing to run Ubuntu 13.04 instead of 12.04 for hardware compatibility. I tried installing UCE 12.04 and upgrading to 12.10 then to 13.04, but the upgrade flopped. I need to do a clean install of Ubuntu 13.04 in order to get Ubuntu running stable.

I was wondering if there's a way I could manually convert Ubuntu 13.04 to "UCE" by installing most of the software packages in UCE. If someone could list the various packages I'd need to install (Bible apps, other additional included custom tools, how to get the Bible wallpapers, etc.), that'd be great.

About the only thing I wouldn't have out of the box is dansguardian, and I could work on that later if need be.

Thanks!

Nathan

---

### Post by ibjsb4 on 2013-08-08
I do not run UCE, but was wondering if this compatibility problem is kernel related.  12o4 offers two kernels; a 3.2 and a 3.5 updated version.  Have you tried running the updated kernel?

In terminal:

```
uname -r
```

Will tell you what kernel your running.

---

### Post by skimo12 on 2013-08-09
Hi parkernathan, If you look through this forum, there's a couple of places where all the packages are listed. Please have a look. If I come across the list again, i'll post you a link here, but i've definitely seen it. It's not a list of the packages, i.e. with Dansguardian etc, from what i remember, but at least it has the bible software.

---

### Post by skimo12 on 2013-08-09
Hi again parkernathan. Have a look at [http://ubuntuforums.org/showthread.php?t=251293&highlight=software](http://ubuntuforums.org/showthread.php?t=251293&highlight=software) 
..and [http://ubuntuforums.org/showthread.php?t=2142486&highlight=software](http://ubuntuforums.org/showthread.php?t=2142486&highlight=software)
..that's all i could find right now, but maybe it doesn't give the details that you were looking for. 

For a super-definitive answer, (smile), I guess that the alternative would be to install 12.04, export the list of packages, and compare with the UCE12.04. If you're game, I can do one of them :)
...and yes, i think that the dansguardian angle would be quite difficult.

There's also some functionality within the Ubuntu Software Centre. By looking at that, i could see that the following were added:
Bibledit-Gtk
Bibledit-BibleTime
Bibledit-Xiphos
OpenLP

---

### Post by skimo12 on 2013-08-09
Ok. I've burned a fresh uce1204 to a usb stick and i now have the list of installed packages, using the following command
sudo dpkg --get-selections >skimo12_uce1204.txt
..i then needed to gzip the file because it was too large to be loaded onto the forum (19.5kb limit)

@parkernathan, I guess you can do this on your ubuntu 12.04 system and find out what needs to be added. 
It would be great if you put that list up on the forum (I hope that it's not against forum guidelines). 

Cheers.

---

