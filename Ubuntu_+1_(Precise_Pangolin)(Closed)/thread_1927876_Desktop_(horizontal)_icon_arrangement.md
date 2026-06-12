---
title: "Desktop (horizontal) icon arrangement"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by EgoGratis on 2012-02-18
In this thread and in one or two more i complaint nobody AFAIK is doing any development on desktop management:

[http://ubuntuforums.org/showthread.php?t=1925064](http://ubuntuforums.org/showthread.php?t=1925064)

Today number of icons on my desktop passed one vertical line and i noticed something is different. For very long time arrangements of icons looked just like messy pile because they didn't follow straight horizontal lines. This is different in Precise Pangolin! It actually works and icons are arranged in straight horizontal lines!

Is this specific to Ubuntu or other stock Gnome 3 distributions have it to? Thanks to the person responsible for this one and making it work!

---

### Post by EgoGratis on 2012-02-18
Never mind i was wrong and didn't test it good enough. If icon/folder/file name gets longer same old behavior reoccurs!

---

### Post by EgoGratis on 2012-02-20
I investigated this a bit more and actually i made some progress. If in dconf-editor org > gnome > nautilus > desktop > text-ellipsis-limit is set to 1 after:

-Restarting Nautilus
-Enabled option Keep Aligned
-Organize Desktop by Name

Then you get nice straight horizontal lines in icon layout. This is posible becouse only one line of text is displayed and to be honest i prefer it like this!

But there is one problem thumbnails must be disabled because they don't play along. In dconf-editor there is setting for thumbnail size and if it's set as default icon size only thumbnails that are greater width then hight play along.

Too bad there isn't any option to disable thumbnails just for the desktop or just for icon view then in Nautilus thumbnails could still be used and on desktop nice layout would be possible too.

I hope something like this will be possible in the future.

---

