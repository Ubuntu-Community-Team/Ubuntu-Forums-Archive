---
title: "New Pangolin strange splash screen"
date: 2010-09-22
forum: System76 Support
---

### Post by Plecebo on 2010-09-22
My girlfriend has been using my Gazelle Ultra off and on and decided she wanted an Ubuntu laptop of her own. 

Took delivery of a Pangolin Performance yesterday. 

We fired it up last night and the first thing we noticed is that the Ubuntu splash screen is SUPER low color depth. The Ubuntu words and progress dots that highlight to show the progress of the boot process had these green halo's around them. I thought at first it would go away after the initial configuration and setup stuff was done, but it didn't.

Once passed the splash screen everything works like a dream. Is this the Ubuntu splash screen bug that is mentioned here? [http://ubuntuforums.org/showthread.php?t=1469217](http://ubuntuforums.org/showthread.php?t=1469217) even though ours is an ATI vs Nvidia machine?

Any advice is appreciated.

---

### Post by ajgreeny on 2010-09-22
Yes, I think it is all the same problem, ie, plymouth, and its proper display being impossible with several nvidia and ATI cards.

I gave up trying to get it to work on my desktop computer and uninstalled the default **plymouth-theme-ubuntu-logo**, or whichever theme is default, and installed the **plymouth-theme-text**, which still displays wrongly, but is not nearly so noticeable or annoying.

On my machine with an ATI 9200SE card this simply sends a darkening colour blue band of about 10mm across the bottom of the screen.  This still changes after a few seconds into a low resolution display, but as I said, it just does not look so obviously wrong

---

### Post by isantop on 2010-09-22
ajgreeny's got it correct. It's a plymouth limitation. 

We do have an ad-hoc solution available on our knowledge base at [http://knowledge76.com/index.php/Fixing_Green_Artifacts](http://knowledge76.com/index.php/Fixing_Green_Artifacts)

Note that this won't get it 100% fixed. The image will appear streched horizontally, since the Pangolin only appears to support the vesa mode for 1024x768. But, the green artifacts will be gone.

---

### Post by HotShotDJ on 2010-09-23
Ignore my post.  I just realized that you are working with an ATI video adapter.  My post was for the NVidia.  I apologize for the spam.

---

