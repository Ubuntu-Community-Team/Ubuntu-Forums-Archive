---
title: "How to export/import VNStat data"
date: 2012-09-05
forum: Server Platforms
---

### Post by apokkalyps on 2012-09-05
I am moving my server to new hardware and onto the new LTS, building it from scratch.

I really need to take my vnstat data with me, and I read somewhere you can export the database and import it somewhere else, which if I remember was only a matter of dropping the database files into a folder.  But unfortunatly I cannot find this documentation.

I would prefer to merge the data from the old server into the data on the new server, although if that is not possible I would settle with overwriting the new with the old.  

If anyone has had to do this, or knows how vnstat works well enough to have a good guess at how to do it, any suggestions would be appreciated!

---

### Post by Cheesemill on 2012-09-05
I think that all you need to do is copy the vnstat database file from the old machine to the new. I don't think it's possible to merge databases, you need to just copy the old db to the new machine.

You can find said database in /var/lib/vnstat/ named the same as your network device.
For example mine is:
```
/var/lib/vnstat/eth0
```By the way, I didn't know how to do this before you asked (although I do use vnstat), all I did was:
```
man vnstat
```to find out. Man pages are your best friend :)

---

### Post by apokkalyps on 2012-09-05
Excuse me for being irritated at being told to RTFM...

I had the man-page open already, not only does it not explain this other than to say that db files are in /var/lib/vnstat/, it adds further confusion by talking about options such as --savemerged, which it doesn't describe exactly what is being merged, or how, when or why to use it.  Also --dumpdb seems like it might be useful but there is no information in the man page about how to "import" anything dumped.  

I did try rsyncing files:
[LIST]
[*]/var/lib/vnstat/eth1
[*]/var/lib/vnstat/.eth1
[*]/var/lib/vnstat/wlan0
[*]/var/lib/vnstat/.wlan0
[/LIST]

from the old server to the new

Before I copied the dot-files, it said
> 
                      rx      /      tx      /     total    /   estimated
Error: Unable to open backup database "/var/lib/vnstat/.eth1".


then I copied the dot-files and it said

>                       rx      /      tx      /     total    /   estimated
Error: Database load failed even when using backup. Aborting.

It's as if the files are corrupted, but I can still run vnstat on the old server and it reads them fine.  
The old server is on vnStat 1.10, and the new server is vnStat 1.11

I even tried setting the owner/permissions to match the eth0 and .eth0 that were already on the new server, and same result.

---

### Post by Cheesemill on 2012-09-05
Interesting.

As I said I've never tried this before so just gave it a go. I copied my /var/lib/vnstat/eth0 (and .eth0) file to a fresh VM after installing vnstat on it and it's been imported with no problem.

My new VM is now showing the old stats from my workstation.

Did you already set up vnstat on the new server? The initial setup routine that is run when vnstat is installed probably needs to be run before the import will work.

I know that the --dumpdb switch has nothing to do with the import/export process, it's only used to output raw data to parse with another program.

Can you post the output of:
```
vnstat -D
```from the new server please.



Edit - A stupid question, but do your interfaces have the same name on both servers? I noticed that the file you are importing is eth1 whereas the default network adapter is usually eth0.

---

### Post by apokkalyps on 2012-09-06
Incidentally, yes, my new server has eth0.  The old server I was using eth1, and briefly wlan0.  The old server skipped eth0 (I think) because it had an on-board NIC which I wasn't using.  I was thinking this would make it easy to (if not merge) keep the old and new data side by side.  

Unfortunately I found this post
[http://forums.humdi.net/viewtopic.php?f=7&t=505](http://forums.humdi.net/viewtopic.php?f=7&t=505)

Where the VNstat author said that databases from 32 bit machines and 64 bit machines apparently are not compatible.  I had noticed a slight size difference between them.  That is upsetting.  

I wonder if it is possible to modify the binary files to make them work with 64 bit.

---

### Post by Cheesemill on 2012-09-06
> **apokkalyps said:**
> Where the VNstat author said that databases from 32 bit machines and 64 bit machines apparently are not compatible.  I had noticed a slight size difference between them.  That is upsetting.

Very upsetting :(

This would explain why my export/import worked and yours didn't.

---

