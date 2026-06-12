---
title: "Login error ($HOME/.dmrc)"
date: 2009-06-28
forum: Security
---

### Post by mhdbnoimi on 2009-06-28
Hi All,

First of all, I'm not sure if this post is in the right place (security diss.), so please forgive if I mistaken. 

Before logging-in to my account I get the following error message and all my configurations (like screen resolution) disappeared!

```
User's $HOME/.dmrc file is being ignored. This prevents the default session and laguage from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by another user.
```

I tried to fix this problem by deleting .dmrc file, but it didn't fix the problem!

Then I tried to change $HOME directory permissions (as shown in the attached picture), but it didn't fix the problem too!

Could you please help me?

---

### Post by handyguy on 2009-06-28
I found this link [http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052) when I had the same problem. I got this from accidentely copying my home folder as root. I don't think this is a security problem but am a newb in high school and I just happened to have the same problem. If I am wrong someone please correct me.

---

### Post by mhdbnoimi on 2009-06-28
Thanks, it's working well now.

---

### Post by AoSteve on 2009-06-28
You know, just to give some headway on this as well.  Sharing your home folder will cause that same error upon bootup.   :)   I learned that with my desktop system I used with my HDtv.  :)   Sharing the home folder is a security risk if you have the possibility of others playing with your configuration files in the home folder!  :)

Just figured I'd put that out for you just incase you ever decide to share that folder and don't realize why the error comes up.

---

