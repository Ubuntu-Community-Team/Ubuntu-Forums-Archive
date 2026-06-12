---
title: "Slow syncing and &quot;'NoneType' object has no attribute 'get_rootdir'&quot; error"
date: 2012-04-23
forum: Ubuntu One (CLOSED)
---

### Post by TorturdChaos on 2012-04-23
I'm having a couple difficulties with Ubuntu One.

First, it doesn't seem to be syncing my files with my Windows XP machines I have it installed on.  I put my music folder into my Ubuntu one folder on my laptop with Ubuntu installed on it.  It took it a while, but it finished syncing on the files to my account on 04/11/12.  But as for 04/20/12 (last Friday) when I rebooted my computer only ~25% of my files where downloaded onto my Windows XP machine.  I know I'm trying to sync ~15gigs of data, but a week and a half and only 1/4 of my songs are sync'd to my Windows machine???  Something seems wrong there.

But Friday did some updates and needed to restart. Figured that might help it anyways.
But now when I launch the Ubuntu One client, it sits at "Getting Information..." forever, then finally comes up with the error:

```
AttributeError
"'NoneType' object has no attribute 'get_rootdir'"
```

and shows the Client, but whenever I click on the "Files" tab I get that same error.

EDIT:

Fixed the error by deleting the "syncdaemon" folder, but still no syncing.  When I look at the list of folders says last modified 04-10-12.

---

### Post by TorturdChaos on 2012-04-23
Well after deleting the "syncdaemon" folder it seems to be syncing again, at least judging from the total size change of the Ubuntu One folder.  But holy crap is it downloading slow...
Average of 150-200KB/s....

I have to say it would be very nice to see some more information in the client about syncing.  Like amount of data sync compared to total data.  And the speed its going at would be nice too.

---

