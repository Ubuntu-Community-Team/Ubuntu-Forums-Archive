---
title: "All files marked as read-only on Windows XP Guest"
date: 2007-12-11
forum: Virtualisation
---

### Post by portach king on 2007-12-11
Hi,
Well I started using Virtualbox 1.5.2 on my Ubuntu 7.10 Host (with Windows XP SP2 Home Edition as guest) about a month ago and had it running flawlessly until last week.
I decided to try an set-up some shared folders and to do so installed guest additions. Since then things have not been right.

First, I managed to get the shared folders to work, but they were marked as read-only..
So I decided to try again using a Samba network. Again, I got it to share, but the files were once again marked permanently as read-only (even though I configured smb.conf specificaly not to do this..)

However, it was when I gave up on the shared network and go back to my slightly cumbersome though reliable technique of transferring the files to usb drive and then connecting that to virtualbox, the real shocker came.
All files on my usb drive are now also marked read-only.

After investigating a little further, almost all files on my virtual machine are tainted with the read-only tag. It makes the entire system useless to me as I can't edit or save any files.
Needless to say, right-click, properties, and unchecking read-only does nothing.

I'm hugely regretting installing the guest additions as it is the only major thing I can remember changing on the system.
I also followed [this guide]("http://support.microsoft.com/kb/256614") when first trying to remove the read-only from the files shared. I didn't work and I have since removed the file that it created. It didn't change anything.

Thanks in advance for any advise and for reading.
So I guess the only thing to write next is:

Help!

---

