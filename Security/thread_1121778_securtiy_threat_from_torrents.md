---
title: "securtiy threat from torrents"
date: 2009-04-10
forum: Security
---

### Post by kiridude on 2009-04-10
I was wondering, what is the security threat in Ubuntu from torrents? 

I am basically downloading movie files, or music files from an unknown source(s) and then opening them...

---

### Post by cdenley on 2009-04-10
There is the unlikely possibility that there is a remote security flaw in your torrent client which can be exploited by a peer. This is the type of risk you take whenever establishing a connection over the internet.

Then, there is the unlikely possibility that the file itself contains an exploit for a security vulnerability in a library or application that is used to parse or decode the files you download.

These possibilities exist regardless of what software you use, and ubuntu is probably safer as far as these security concerns go.

Another possiblity is that a torrent contains a malicious launcher that disguises itself as a movie or music file. If you unwittingly double-click the launcher, which may appear to have a name like "Movie.Title.avi" and use the multimedia icon, then all kinds of malicious things can be done with your permissions. This is a flaw in gnome, and has been fixed in Ubuntu 9.04.

---

### Post by bodhi.zazen on 2009-04-10
The risk of running a torrent is small. Running a torrent does open a port and if your torrent client has an exploit, known or unknown, you are vulnerable.

You can simply use apparmor to confine torrents (which is what I do).

I have posted profiles here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/)

IMO the greater risk would be what you are downloading via a torrent. If, for example, you download executable code from untrusted sources. Torrents are the primer breeding grounds of social engineering, IMO, so just take care.

---

### Post by kiridude on 2009-04-10
bodhi.zazen, can executable code be hidden in a movie, image, music, pdf file? I mean, I can identify executables, but not too sure about if they can be disguised in the aforementioned files.

---

### Post by bodhi.zazen on 2009-04-10
> **kiridude said:**
> bodhi.zazen, can executable code be hidden in a movie, image, music, pdf file? I mean, I can identify executables, but not too sure about if they can be disguised in the aforementioned files.
 
Yes, although that is a very rare and sophisticated attack vector. I have seen it one one server where a malicious image was uploaded via ftp.

---

### Post by cdenley on 2009-04-10
I would be more worried about launchers which appear to be a video, audio, or image file.

---

### Post by kiridude on 2009-04-11
Thanks for your replies guys.

cdenley, I'm not sure what you mean by

> launchers which appear to be a video, audio, or image file. 

If I download a file, it will be .avi or .wmv, or .jpg, or whatever the format may be.

From what I understand, a launcher is a "shortcut." Would the launcher you're talking about have a differnet extension, or no extension as other apps appear? 

How would it "appear" to be a media file?

Thanks

---

### Post by ubuntu27 on 2009-04-11
> **kiridude said:**
> 

cdenley, I'm not sure what you mean by

> launchers which appear to be a video, audio, or image file. 

If I download a file, it will be .avi or .wmv, or .jpg, or whatever the format may be.

From what I understand, a launcher is a "shortcut." Would the launcher you're talking about have a differnet extension, or no extension as other apps appear? 

How would it "appear" to be a media file?

Thanks

I believe he is referring to a bug in GNOME that allowed a launcher to act as an executable file, something like that. 

I saw a thread that was talking about it today, there  a link to a youtube video where it displayed how using a launcher that ends with .desktop file type can be a malware.

---

### Post by cdenley on 2009-04-11
> **kiridude said:**
> Thanks for your replies guys.

cdenley, I'm not sure what you mean by



If I download a file, it will be .avi or .wmv, or .jpg, or whatever the format may be.

From what I understand, a launcher is a "shortcut." Would the launcher you're talking about have a differnet extension, or no extension as other apps appear? 

How would it "appear" to be a media file?

Thanks

A launcher is not displayed by nautilus using the filename. It is displayed using the name and icon specified within the launcher. Therefore, it can be displayed in nautilus as a ".avi" file, and use an icon which indicates it is a video file, yet still be a launcher which executes an arbitrary command. You can tell the difference by right-clicking, and going to properties, though.

---

