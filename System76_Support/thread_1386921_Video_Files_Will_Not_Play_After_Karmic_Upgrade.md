---
title: "Video Files Will Not Play After Karmic Upgrade"
date: 2010-01-21
forum: System76 Support
---

### Post by jpoRS on 2010-01-21
Hello All,

I have been busy at work recently, and didn't have the time to do a full install to upgrade to Karmic, so I just did it through Update Manager.  I know, lame shortcut, but what is done is done.

Now whenever I try and play any movie (any format) it will not play.  .avi, .wmv, and the like give me error codes like <code>No suitable decoder module:
VLC does not support the audio or video format "WMV2". Unfortunately there is no way for you to fix this.</code>

Replacing "WMV2" with whatever type of file it is.  I get a similar but different error in Banshee or Totem as well.  .flac produces no error message, but will not play.

Panp4i, running Karmic upgraded from Jaunty, and I haven't tried much yet.

Thanks!
jim

---

### Post by jml on 2010-01-21
jim, have you checked your sources list?  When Ubuntu does an upgrade it automatically disables any third party repositories like medibuntu.  And the update usually removes any orphaned apps or codecs. You might want to check your sources list and make sure that you have the necessary repositories enabled.  You may have to reinstall any third party apps, or codecs that were removed.  Then you should be good to go. Good luck.

Joe

---

### Post by thomasaaron on 2010-01-21
And if that doesn't work, try this...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by jpoRS on 2010-01-21
I was hopping you wouldn't say that.  Sigh.

When jml confirmed my suspicion that was the problem, I tried to re-enable medibuntu, and once again a mess I made of my repositories came back to haunt me so I bit the bullet and went back to do the right thing - fresh install.

After a fresh install, and following the standard medibuntu instructions, everything is back to normal.

Moral of the story- Shortcuts don't work.

Thanks everyone.
jim

---

### Post by jml on 2010-01-21
Don't be too hard on your self, Jim.  In a perfect world, upgrading should be easier than a clean install.  But as long as there is a need for third party repositories, upgrades will always be a bit of a pain.  Later.

Joe

---

