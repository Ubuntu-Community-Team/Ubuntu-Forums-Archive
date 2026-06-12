---
title: "Re: Samba doe's not share second harddrive"
date: 2012-07-31
forum: Server Platforms
---

### Post by smakarl on 2012-07-31
A copy/paste of what I emailed in previously...

Samba auto config taken / triggered from or triggered directly from file share options EXCELENT.
Almost all sharing on my Ubuntu / Windows XP network seems click & go.

I share Ubuntu < > Ubuntu < > Windows OK .

A big fault to correct : Secondary drives are not AUTO SET to share.----------
OR possibly secondary drives were not covered yet? ooops.

Example : My main system has a second drive where I have movies stored for the children.
When I boot Ubuntu on it, the second drive is not shared - even though under file options it & sob-directories are set to share.

To share this drive I am forced to boot and share from Windows. Then are the Ubuntu systems see all fine....

Please be in touch.

PD  any team members / groups here in Mexico (SMA)

---

### Post by wildmanne39 on 2012-07-31
Moved to own thread!

---

### Post by cariboo on 2012-07-31
In, order for your second drive to be shared automatically, it must be mounted at boot. Do you have your second drive setup properly in /etc/fstab?

---

