---
title: "perl: warning: Setting locale failed"
date: 2008-12-29
forum: Server Platforms
---

### Post by wminor on 2008-12-29
Hi,

I have a fairly fresh install of ubuntu server 8.04 running on my dedi, and i keep getting the following error in a variety of situations:


perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = (unset),
LC_ALL = (unset),
LANG = "en_GB.ISO-8859-15"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


I have searched this forum and found some similar problems... but none of the suggested solutions seem to be working for me.

If anyone could shed some light on this (i am relatively new to linux) it would be most helpful.

Thanks in advance.

W

---

### Post by vpsville on 2008-12-29
You need to run this command:

apt-get install language-pack-en

---

### Post by wminor on 2008-12-29
Thanks...

I tried that, and it installed succesfully, but i still get that same error :(

---

### Post by wminor on 2009-01-02
if someone could just tell me where i can find the file for locales settings i can have a go at sorting this out... but at the moment i am a bit stupmed.

Thanks

W

---

### Post by wminor on 2009-01-03
FIXED!!!

I followed the instructions in this thread: 

[http://ubuntuforums.org/showthread.php?t=319397](http://ubuntuforums.org/showthread.php?t=319397)

I had done this once already but obviously made a mistake. Having corrected this i now don't get the error where I used to (so far at least!)

---

