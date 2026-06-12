---
title: "Consequences of giving PHP scripts a high memory limit?"
date: 2010-05-28
forum: Server Platforms
---

### Post by Vunutus on 2010-05-28
I have an Ubuntu server running in our small office. Among its many duties is report generation. It uses PHP and DOMPDF (a PHP library for converting HTML/CSS to PDFs for printing). PHP's default memory limit of 32MB is not even close to being enough to pull large amounts of data from the database and generate images/tables/PDFs with that data.

I increased the memory limit to 64MB and that is adequate for reports under 3 pages or so (varies based on table complexity, images, etc). If any user tries to generate a report longer than that, PHP just throws a "out of memory" error and doesn't make the report.

My question is: what are the possible consequences of increasing the memory limit yet again to 128MB or maybe even higher? The server isn't terribly powerful. It has 2GB RAM and 4GB swap space. I know that isn't much but this is a small office and at most I can only see two or three people trying to run reports at the same time. As for security, apache is currently only serving pages in the local network, but sometime within the next year I'll probably have it hosting a public website (currently using a hosting service). Is a high memory limit a potential security risk when exposed to the internet?

EDIT: Sorry, PHP's default memory limit is 16 not 32 as I said. Question still stands, however

---

### Post by Keith_K on 2010-05-28
None outside of resource management. Any modern server should have no problem with 128mb, which I believe is recommended with php v5.

---

### Post by RyanRahl on 2010-05-28
Filling up your memory without the proper swap and cache clearing settings will cause your server to be sluggish for sure. I wrote this on my facebook and I think it applies here so im going to copy it and hopefully it will help: 

> This is for all my tech friends. I've been noticing some memory problems in some of my Debian Linux based systems when a job stops it still leaves data in the memory cache. Now, Linux has a pretty good memory management where it will store cache data in the RAM before it sends anything to the swap space and it is supposed to clear this memory to make way for new active processes. Sometimes it does not do this lol. At first I thought it was a memory leak but found that some application caches were not clearing the space, mostly very specific Apache2~MySQL interactions. There is hope though, just simply run this command (must be root):

root@localhost:/# sync; echo 3 > /proc/sys/vm/drop_caches

I use this now on a server set up as a cron job to run every hour to keep things going even smoother than before. A more practical application for the desktop user would be to make a launcher in GNOME to clear up all that junk you web browser is leaving, go ahead and load up Firefox or Chrome till your system wants to halt and then run the command. If you've got a lot of RAM and the browsers won't have the desired effect try TARing and unTARing a DVD ISO. You'll see. If your system does lock then press ctrl+alt+F1 and run the command from there. 

Another performance tunning note about this is the use of Swappiness. You can change the frequency the system swaps at by echoing a value from 0 to 100 in this file, 0 being avoid swapping for as long as possible and 100 being swap processes out of physical memory as fast as possible and move them to cache (the default value is 60). This should be increased if you are constantly switching applications and decreased if you run very large or bloated applications. The file can be found here:

/proc/sys/vm/swappiness

If you run large applications like OpenOffice or a video editor(AviDemux, Blender, etc.) but still need your IM program, Email Client and Browser you can create extra swap space aside from your swap partition with the 'mkswap' command, it's a great temporary fix. You can make this change permanently by adding an entry to the fstab file but I recommend actually increasing your swap partition size if you need a permanent fix.

So that was a few thoughts from me about memory tuning. I hope this helps someone, I think I'm going to write tech notes more often and maybe start some discussion.

It may not be too terribly specific to your situation but it is adaptable to anything you want. I just really didn't want to revise it for this post. Hope it helps.

---

### Post by Vegan on 2010-05-29
Rather than wate time with the swap partition, go buy another stick of RAM.

---

### Post by RyanRahl on 2010-05-29
> **Vegan said:**
> Rather than wate time with the swap partition, go buy another stick of RAM.

Very good point, always preferable but not always possible. I've seen mkswap used on flash drives and it seemed to work well.

---

### Post by Vunutus on 2010-06-01
> **Vegan said:**
> Rather than wate time with the swap partition, go buy another stick of RAM.

Our tech budget is non-existent so that seems unlikely :D

---

