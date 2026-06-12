---
title: "Accessing folders outside of Wine drive_C folder"
date: 2008-12-23
forum: Wine
---

### Post by jukingeo on 2008-12-23
Hello all,

I would like to know how do you reference access to folders outside of the designated "drive_C" folder?

For example, I have a program that I want to access my music files from that is stored on another folder outside of the "drive_C" folder.

As of now I been using two music lists, but this is redundant and takes up hard drive space.  So I hope there is a way I can access outside folders.

If so, I need to know how I would point to those outside folders as I have to specify a path within a configuration file.

Thank You...and Happy Holidays!

Geo

---

### Post by Temposs on 2008-12-23
> **jukingeo said:**
> Hello all,

I would like to know how do you reference access to folders outside of the designated "drive_C" folder?

For example, I have a program that I want to access my music files from that is stored on another folder outside of the "drive_C" folder.

As of now I been using two music lists, but this is redundant and takes up hard drive space.  So I hope there is a way I can access outside folders.

If so, I need to know how I would point to those outside folders as I have to specify a path within a configuration file.

Thank You...and Happy Holidays!

Geo

EDIT: You should be able to access any file from a program in Wine. I know when I'm using a file chooser in Wine, I can easily access any file on my computer, so it should be possible...

EDIT: Disregard below, I missed that you were looking at Wine :-P

_____________________________________________________

I'm not sure what you mean by "drive_C" folder.

However, if you mean anything that is on your local filesystem, then I can start from there.

If you have some other partition or external drive already loaded/mounted on your computer, you can usually find it in the path "/media". In that folder you should find all your difference drives/partitions, I believe. You need to look for yourself what the particular drive you want to use is called.

Hope this helps :-)

---

### Post by Temposs on 2008-12-23
OK, I've got it!

To create a path outside of "drive_C", you should prepend "Z:" before the path you'd normally write, except all slashes should be backslashes :-)

Hope this is helpful!

EDIT: As an example:
Z:\home\temposs\Projects\useful\useful.py

---

### Post by pmooney78 on 2008-12-28
You can also configure Wine to map specific Windows drive letters to specific points on your Linux filesystem. By default, Wine maps drive Z:\ to the root of the filesystem (at /). This is kind of insecure, since that means that malicious Windows programs can read files anywhere in your filesystem. I removed the Z:\ drive when I installed Wine and created other drive letters that map onto other places in my file system (so D:\ maps to /media/Music, E:\ to /media/Externa, and so forth).

It's all in the "Drives" tab of the "Wine Config" application, which should be in your Wine menu.

Hope that helps.

---

### Post by jukingeo on 2009-01-07
> **Temposs said:**
> 

I'm not sure what you mean by "drive_C" folder.

I don't know if you have been using Wine, but there is a folder created within Wine called "drive_C".  This is where Wine searches from when you are working with installed programs.  The problem is that I have a Windows Jukebox program that I am testing in both Windows XP and in Linux running under Wine.  With that in mind, I need to access THE SAME music files.   These files are outside of the "drive_C" folder designation and navigating outside that constraint is my issue.  I don't know what to do.

> 

If you have some other partition or external drive already loaded/mounted on your computer, you can usually find it in the path "/media". In that folder you should find all your difference drives/partitions, I believe. You need to look for yourself what the particular drive you want to use is called.

Hope this helps :-)

The problem is that Wine, like Windows, is looking for a drive letter.  So I can set up programs and files within that "drive_C" designation and that is no problem...but I don't know what to do when it comes to navigating outside of this folder.

Hope that clears things up a bit as I am not referring to normal "system" navigation, but navigation via Wine (specifying drive paths for Wine programs, etc).

> **Temposs said:**
> OK, I've got it!

To create a path outside of "drive_C", you should prepend "Z:" before the path you'd normally write, except all slashes should be backslashes :-)

Hope this is helpful!

EDIT: As an example:
Z:\home\temposs\Projects\useful\useful.py

Ok, so then to get out of the Wine drive constraint you have to specify the path with "z".  I will try that and see what happens.


Thanx,

Geo

---

### Post by jukingeo on 2009-01-07
> **pmooney78 said:**
> You can also configure Wine to map specific Windows drive letters to specific points on your Linux filesystem. By default, Wine maps drive Z:\ to the root of the filesystem (at /). This is kind of insecure, since that means that malicious Windows programs can read files anywhere in your filesystem. I removed the Z:\ drive when I installed Wine and created other drive letters that map onto other places in my file system (so D:\ maps to /media/Music, E:\ to /media/Externa, and so forth).

It's all in the "Drives" tab of the "Wine Config" application, which should be in your Wine menu.

Hope that helps.


I am usually pretty careful with what I install on my system, but I will keep that in mind.

Thanx,

Geo

---

