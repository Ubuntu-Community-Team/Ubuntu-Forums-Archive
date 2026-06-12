---
title: "[WINE] USB Help?"
date: 2010-02-16
forum: Wine
---

### Post by Eyaare on 2010-02-16
So I have this Ion Discover DJ kit, which came with MixVibe's Cross software. The software appears to work in WINE, except for the fact that it won't let me do anything unless the kit's connected. That's how the software is supposed to run. Problem is, the USB kit I need to run won't work with WINE.

Also, when I type "winecfg" into terminal I get this message:

fixme:mixer:ALSO_MixerInit No master control found on Ion Discover DJ, disabling mixer

Thing works fine on Linux, Mixxx even recognizes that it is the Ion Discover DJ midi controller, although Mixxx won't let me use the jog wheels, which is why I need this.

(Mixxx isn't run through WINE)

---

### Post by chronos00 on 2010-04-06
The precompiled version of Wine, available at the Ubuntu repositories, does not support USB connections (I guess this is because this feature is not tested).

If you wish to use a USB device through Wine, you will need to download the source code, apply a patch and compile.

Here you can find some instructions:
[http://wiki.winehq.org/USB]("http://wiki.winehq.org/USB")

Regards.

---

### Post by Dustout on 2011-05-11
i'm having the same issue, it is unfortunate that there is no fix :(

---

### Post by chronos00 on 2011-05-11
As I said before, the solution is to compile wine from source indicating you want USB support.
You can follow instructions in the link in my previous post.

---

### Post by sabersong on 2011-12-25
I tried the instructions in the link, but the patch fails to apply.

---

### Post by howefield on 2011-12-26
Thread moved to the "*Wine*" forum.

---

### Post by gleedadswell on 2012-01-26
Hi sabersong.  What sorts of error messages do you get when you try to apply the patches?  I just applied them and it worked.

I'll be testing out a program running under wine which needs to connect to devices via usb tomorrow.  I'll post back here with my experiences.  If it all worked I'll post a HOWTO.

---

### Post by gleedadswell on 2012-01-27
Still working on it...

Now I must rant.

The Windows registry, and REGEDIT, which is used to view it are the ugliest things I have ever seen in all of computerdom!

---

