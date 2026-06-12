---
title: "need to create raid 0 without altering install"
date: 2010-11-17
forum: Server Platforms
---

### Post by shanep-server on 2010-11-17
I have 10.04.1 on my server with a 250gb sata drive. I have all my files on this hard drive. I'm running out of space so I have another 250gb sata drive I need installed. I want to create raid 0 so I can expand my servers hard drive space. I don't want to lose my data on original hard drive or reinstall to create the raid.

Is there a way to achieve this with mdadm without altering the first hard drives data?

---

### Post by alastair on 2010-11-17
Yes - 

I did this on a qnap nas a while back - and wrote a note here :

[http://forum.qnap.com/viewtopic.php?f=147&t=23029#p97724](http://forum.qnap.com/viewtopic.php?f=147&t=23029#p97724)

See also the referenced web page for specifics.

---

### Post by BobMUK on 2010-11-18
> Yes -
I did this on a qnap nas a while back - and wrote a note here :

[http://forum.qnap.com/viewtopic.php?...t=23029#p97724](http://forum.qnap.com/viewtopic.php?...t=23029#p97724)

See also the referenced web page for specifics. 

That'll only work for RAID 1, not RAID 0.

You can't grow a RAID 0 array unfortunately.  You'd have to backup the data, create the array, then restore the data.

If you do plan to use RAID 0 then bear in mind you'll double your risk of data loss as compare to running a single drive.

---

