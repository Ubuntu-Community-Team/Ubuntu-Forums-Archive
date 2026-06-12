---
title: "HELP !! :( I Cant Do Dual Boot With Windows 7 ????"
date: 2010-11-24
forum: Server Platforms
---

### Post by AnkurOn on 2010-11-24
I Need To Install Ubuntu Server Edition On My Windows 7.
I AM Running Win 7 With 3GB Ram And 2.10 GHz Dual CPU .
I want To dual Boot Ubuntu Server Edition 10.10 in My Win 7.
 but When i try to install it It Says that u have found only one partion . Would you like to format the whole partion . This Format will delete all the Files and Ubuntu will be installed.
I Dont want that as i need Dual boot.
Please help me out.
Did i Go Wrong In Burning down  the Iso Image ??
Help Me Soon

---

### Post by arrrghhh on 2010-11-24
If you didn't leave any space for Ubuntu, you'll have to resize the drive.  I've have mixed results resizing NTFS partitions thru the Ubuntu installer, I would recommend using [EASEUS's software](http://www.partition-tool.com/personal.htm) (free for Windows/"home" use) to resize your Windows partition.  Basically just leave some free (raw) space to install Ubuntu to, I would recommend at least 20gb.

---

### Post by AnkurOn on 2010-11-24
I Can get 50-60 GB of Space but it should show partions first .
until and unless it shows me partions options how can i choose
I have 3 drives each of 60 GB Free leaving 90 GB Of C Drive ...
so i dunno what exactly problem is
hope you will help soon for this problem !! :(

---

### Post by arrrghhh on 2010-11-24
> **AnkurOn said:**
> I Can get 50-60 GB of Space but it should show partions first .
until and unless it shows me partions options how can i choose
I have 3 drives each of 60 GB Free leaving 90 GB Of C Drive ...
so i dunno what exactly problem is
hope you will help soon for this problem !! :(

So you need to explain this a little better.

Do you have 3 separate hard drives?  Or is there one hard drive that you've partitioned into 3 sections, maybe 4 including the 90GB C:?

I think there's a handy script you can run that will show us everything we need to see, let me try to find it.

Found it, please see [this post](http://ubuntuforums.org/showpost.php?p=10107348&postcount=5) and post your results here.

---

### Post by cmileto on 2010-11-24
Try this with a desktop install instead of the server install.

---

### Post by yettiman2208 on 2010-11-25
I agree with cmileto.

I have had mixed results attempting to partition on the fly with Server.

However, the desktop edition has a much easier way to do it. Just follow the instructions and it will resize and keep the data.

-a large yetti

---

### Post by angryfirelord on 2010-11-25
Are you using guided partitioning or did you select the manual option?

---

