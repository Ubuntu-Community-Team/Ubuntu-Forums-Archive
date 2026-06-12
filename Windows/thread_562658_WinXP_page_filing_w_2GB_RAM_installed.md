---
title: "WinXP page filing w/ 2GB RAM installed"
date: 2007-09-29
forum: Windows
---

### Post by voided3 on 2007-09-29
Hello, I noticed that my desktop comp when I play games almost never has less than 800mb free of 2GB installed, so my question would be why do I still have a peak page file size of 330mb according to task manager? Even if you subtract 128mb for my AGP aperature, that's still 672mb free if all 128mb were filled (note: non-integrated graphics; I have a  256mb x1300 pro). On Linux it only uses the swap if the RAM is filled. Is there any way I can have such a setup on XP to squeeze some extra performance out of it, or is this just unnecessary? Thanks!

---

### Post by lisati on 2007-09-29
Please pardon the longwinded response: One option is to go to the Control Panel, click on "Performance and maintenance", then "system", On the "advanced" tab, click on the settings button for "Performance" and then on the "advanced" tab choose the "change" button for "virtual memory". choose your options!

I'm sure there's probably a less bloated approach somewhere......maybe not on Windows?

---

### Post by voided3 on 2007-09-29
Well, it isn't the size of the page file that's the issue (I have more than 60GB free on both of my internal drives), it's more of the fact that I think it's being used unnecessarily. I would assume that there would be some kind of modifiable registry key or something that would change this. Any ideas? Thanks!

---

### Post by Sunforge on 2007-09-29
Here's a guide to page files on windows that's worth reading:

[http://www.petri.co.il/pagefile_optimization.htm](http://www.petri.co.il/pagefile_optimization.htm)

---

### Post by voided3 on 2007-09-29
Thanks! The suggestion of moving the swap space to another non-system drive (I have two 160 GB IDE drives) and setting it as a fixed size is a very good one; I did it and it seems to have helped a bit (gee, sounds like what you do with a Linux swap partition.... I guess they know where to look to get the good ideas!).

---

### Post by Sunforge on 2007-09-30
Moving the pagefile is someting that I automatically do on servers to great benefit. If I have a machine with a spare hard drive in it I'll move the PF so that spare drive.

I've also experimented with getting rid of the pagefile completely but as the article says, if you look closely, Windows will still page stuff to the drive, albeit a lot less stuff than it did when it had a "full" pagefile. Don't try eliminating the pagefile if you've got less than 2 Gb of RAM though it can lead to some awkward moments.

---

