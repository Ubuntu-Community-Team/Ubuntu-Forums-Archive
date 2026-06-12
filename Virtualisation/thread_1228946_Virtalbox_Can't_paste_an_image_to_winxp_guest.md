---
title: "Virtalbox: Can't paste an image to winxp guest"
date: 2009-08-01
forum: Virtualisation
---

### Post by briwood on 2009-08-01
My HostOS is ubuntu 8.04.  My guestOS is Windows XP.  I have vbox guest additions installed. I can paste text copied from any application on the host into any application on the guest.  I cannot past an image copied to clipboard on the host to the guest.  Is copying images supported by vbox?

Here's what I've tried:

Host: goto webpage in firefox select/copy text
Guest: paste
Works

Host: in firefox right click image > Copy Image.  
Guest: clipboard is empty

Host: in gimp open jpg. select all > copy
Guest: clipboard is empty.

In the previous two tests I've confirmed that the copied image appears in the Host's clipboard.

My ultimate goal is to copy a screen capture on the host into OneNote running on the guest.  I'd also be interested in your favorite screen capture apps for Ubuntu.

Thanks for any help.

Brian

---

### Post by briwood on 2009-08-04
so, can other people paste images to their windows guests without problems?

---

### Post by SecretCode on 2009-08-06
I don't think pasting images is supported by the virtualbox shared clipboard. See [http://forums.virtualbox.org/viewtopic.php?f=7&t=20825](http://forums.virtualbox.org/viewtopic.php?f=7&t=20825) ... wait, that was your thread anyway! 

I'm surprised there are no other comments, on this forum or there. Maybe nobody else even tries to do this?

---

