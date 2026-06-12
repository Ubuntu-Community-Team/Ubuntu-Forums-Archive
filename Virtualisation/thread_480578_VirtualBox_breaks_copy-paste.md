---
title: "VirtualBox breaks copy-paste"
date: 2007-06-21
forum: Virtualisation
---

### Post by Cirrocco on 2007-06-21
I did quite a bit of testing on this bug, and here's what I got.

When VirtualBox is running a client OS (in this case Windows XP), the copy aspect of the copy-paste function breaks.
Turning off the Client OS restores my copy functionality.

Here's what I mean by "breaks":
I will copy some text and paste it here as an example:
```
Å¸Å¸ 
```
see?  That's a copy of some text out of this post, and look at the crap that paste spits out.  (So this doesn't have to do with me closing the window containing the original text.)

Here's what I mean by the 'copy aspect of copy-paste': after I start glipper I can see what I just copied.  glipper shows "Å¸Å¸ " and Pasting it pastes exactly what glipper says is on the clipboard.  so therefore paste is working fine - it's copy that's screwed up.

Also note:
-both methods of copy-paste do the same thing. I'm referring to: Right-Click->Copy, Right-Click->Paste, as well as: Edit->Copy, Edit->Paste

-If I select text and middle click, I can successfully copy text, but this doesn't work on files - which brings me to my next point:

-this problem of copy-paste also affects my ability to move/copy files, so it's not just limited to text.

Has anyone else encountered this problem?

---

### Post by felicity on 2007-06-22
I'm not experiencing this problem. 

Have you tried changing the settings for Shared Clipboard in VirtualBox settings dialog? Have you installed any software on the guest OS that might be causing this?

---

### Post by Cirrocco on 2007-06-26
turning off the shared clipboard fixes this.
too bad really - shared clipboard is a cool feature.

---

### Post by crayzbytes on 2008-02-07
I ran into the same problem. I switched the shared clipboard from bidirectional to guest to host (which is really the only use case I care about) and it seems to work fine.

---

### Post by steveg944 on 2008-04-12
Thanks Cirrocco and crayzbytes. I was having th same problem. I changed my setting to "host to guest" and it is now working fine.

This is a little annoying, but better than nothing.

---

### Post by fjgaude on 2008-04-12
VMware server works both ways for text with the clipboard, that's why I use it and not VBox.

---

### Post by KAding on 2008-07-06
Apparently this happens when you have an old version of the Guest Additions driver installed.

I reinstalled the Guest additions (upgrade from 1.5 -> 1.62) and everything works fine again.

---

### Post by mikerobinson on 2008-09-13
> **KAding said:**
> Apparently this happens when you have an old version of the Guest Additions driver installed.

I reinstalled the Guest additions (upgrade from 1.5 -> 1.62) and everything works fine again.

Thanks so much! This worked for me.

---

