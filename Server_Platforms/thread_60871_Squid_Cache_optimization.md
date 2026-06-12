---
title: "Squid Cache optimization"
date: 2005-08-29
forum: Server Platforms
---

### Post by kemu on 2005-08-29
We have Squid cache installed on two Ubuntu servers, and it works acceptably on each as a proxy. However, the cache does not always seem to work. Even on some static pages, a downloaded file will have to be re-downloaded by someone else (with a different IP) viewing the same page. At other times, it works fine. (A 2.4 MB picture on our University's site has to be re-downloaded each time while Microsoft's 10+ MB IM installer cached properly and now downloads instantly on request.)  Is there something simple I'm missing? How can I optimize Squid's caching and serving?

Squid actually seemed to run faster generally when it was configured to use only RAM cache, not hard drive cache.  (I can understand that for small, frequently accessed objects, of course, but the hard drive cache slowed things down to the extent our students asked us to turn it off.)  In fact, just sending machines through a Linksys gateway seems faster than using Squid.

Our main Squid cache is running on a desktop class machine (PIII, 600 MHz, 256 MB RAM) with only one hard drive.  I wish we could add a second drive just for the cache, but we have a limited budget.  Plus, we only have a 64K connection over a very spotty line, since we're four hours' drive from Nairobi.

Thank you very much for any help or suggestions.

---

### Post by gruepig on 2005-08-29
Re caching:  I can think of a few possibilities, though they're probably not too likely. Some pages may be set with the no cache directive.  Squid may be configured not to cache pages from certain IPs.  The cache dir might be full, so pages are getting expired from the cache.  Post your squid config.

Re performance: squid should run fine on that hardware.  The bottleneck is likely your disk.  What's are you using for a hard drive (IDE/SCSI, speed, etc)?  Is the cache on a separate partition? Also, what filesystem are you using; I'm sure ext2, ext3, and reiserfs will give pretty different performance for a squid cache, but I'm not sure which would be best; there may also be mount options (e.g., noatime?) that would help.

---

### Post by LordHunter317 on 2005-08-30
[QUOTE=kemu]Even on some static pages, a downloaded file will have to be re-downloaded by someone else (with a different IP) viewing the same page.[/quote]Are you sure the files aren't being sent Pragma: No-Cache?

With Apache's default configuration anyway, any files negoitiated on the basis of content are automatically marked No-Cache.  This frequently means image files on the web.  It's quite likely your server may be doing this, verify the file can actually be cached before doing so, and that it's being put in the cache.

> How can I optimize Squid's caching and serving?Make sure you're using the caching policy that best fits your site, and that you've tuned the cache parameters correctly.  This is difficult to guide, read the online squid documentation carefully, and pay attention to the logs.

> Squid actually seemed to run faster generally when it was configured to use only RAM cache, not hard drive cache.  (I can understand that for small, frequently accessed objects, of course, but the hard drive cache slowed things down to the extent our students asked us to turn it off.)That seems odd, like there is a misconfiguration.  Where you using diskd?  What filesystem?

---

### Post by kemu on 2005-08-30
Thank you for your help.  Just in case it wasn't obvious, I'm new to all this. :) We are using an IDE drive with one primary partition (plus a swap file partition) holding the OS and cache.  The file system is ext3.  There is still lots of space on the drive, since we only started this server a month ago.  I don't know the hard drive RPM, but it is probably around 5400.  (We're also using an old Compaq DeskPro as a test server for Squid, and its performance is about the same as the newer Dell.)  I'm attaching our conf file, and please forgive me for not cleaning it up first.  We used the default file and left the instructions in.

No, I'm not sure that the files are not being sent Pragma: No-Cache.  Our web host does use Apache, and perhaps they have the "No-Cache" still set as default.

I don't know how to use mount options to increase disk speed, but I'll look into that.

I did try to read all the Squid documentation, including all the FAQs, and I've been using Calamaris and Cachemgr to analyze the logs.  The problem is probably me -- simply that I'm still not sure how best to tune the cache parameters.  I also read the Webmin Guide's instructions for Squid, which is how I configured the cache in the first place.  By the way, one site said that caching requires very precise time measurements.  When Squid fails to look up a requested site, the error page says it was generated three hours ago, GMT (we're three hours ahead of GMT).  Might that be causing any cache problems, in case Squid is using GMT while our server is using GMT +3?

I'm not sure which instance of diskd is being used (I didn't know it was being used until you told me!), but there is one "diskd" file in /usr/bin and another in /usr/lib/squid.

FYI, if it helps, by far most cache entries in Cachemgr show up as follows:

KEY 56359023CA9896A9E35494FDE7AB9656
	STORE_OK      NOT_IN_MEMORY SWAPOUT_DONE PING_NONE   
	CACHABLE,DISPATCHED,VALIDATED
	LV:1123158556 LU:1123158566 LM:1122347667 EX:-1       
	0 locks, 0 clients, 1 refs
	Swap Dir 0, File 0X000EF6

Only some say "IN_MEMORY" and list the URL:

KEY 48B5C375F292F04DBCB1556E6632AEF8
	GET [http://www.statelocalgov.net/favicon.ico](http://www.statelocalgov.net/favicon.ico)
	STORE_OK      IN_MEMORY     SWAPOUT_DONE PING_DONE   
	CACHABLE,DISPATCHED,VALIDATED
	LV:1125033002 LU:1125033001 LM:1063908328 EX:-1       
	0 locks, 0 clients, 2 refs
	Swap Dir 0, File 0X0057AE
	inmem_lo: 0
	inmem_hi: 3913
	swapout: 3913 bytes queued

Please let me know if there is any more information I may provide, and thanks again.

---

