---
title: "System for remote viewing of hi res files"
date: 2008-03-10
forum: Server Platforms
---

### Post by nonaguy on 2008-03-10
My company is looking to provide access over the internet to a 4.0Tb database comprised of approximately 60,000 ~70 Mb high resolution full-color TIFF documents. What we have planned is a web-based application for viewing these TIFFs over a remote WAN connection with minimal bandwidth utilization, which would only require the end users install a Java Virtual Machine. 
We would install VMWare in a Windows 2003 Server environment, and install a Linux OS on it, such as Ubuntu 7.10 as a backend with our main webserver. We would then have X11 over SSH to use the Linux system as an application server to run a program like Evince Document Viewer to view the TIFFs. 
So what do you think, a good idea or is it terrible? Also, has anyone faced a situation like this before, and if so, what did you do? Does anyone have any suggestions or anything?

---

### Post by p_quarles on 2008-03-10
Moved to Server Platforms.

---

### Post by koenn on 2008-03-10
Sounds like an interesting idea.
Some questions came to mind :

Why run Ubuntu in VM on Windows ? Unless you have other reasons for virtualization, where's the benifit in it ?

You'll be exporting a 'X showing the TIFF' instead of the TIFF itself. Whether that actually saves any bandwith depends on the clients screen resolution, I suppose ? Or the resolution X offers ? 
Do you know how much bandwith you'll save ? Do you plan to measure  or calcultae this ? 

I don't quite see where the Java VM fits in - is it to run / serve as an X client - is this  where are you going to ssh in from / export X to ?

---

### Post by astrotech226 on 2008-03-10
Have you actually tried a test of opening a few of these 70 meg tiffs on a decent machine and zoom in on them and then pan around?

Here's the problem I see.  You are going to run this inside a VM on a Windows box.  You really have this backwards.  This app is going to needs *LOTS* of ram so it should be the primary OS.  If you really need Windows, install it in a VM or on a different server.

Can explain a little more about what you are trying to do?  I'm just guessing, but you might be better off creating thumbnails or lower res copies to let people view the images.  Then do they buy the images or download them?  At that point, give them access to the full res version.

---

### Post by nonaguy on 2008-03-11
I misunderstood what it is we were trying to do, we are not going to run Windows 2003 on the backend. What we thought about was running Linux on the backend to host the database. What we would have VMWare for is the most stripped down version of Linux we could get, with only the most essential functions needed, and the Evince viewer. The VMWare would be used to isolate the X11 over SSH that would allow access to the Evince viewer to view the documents. 
We need a JVM to run the applet in the clients browser that would run the X11. 
As to why we are using hi res TIFFS, we are dealing with historical documents dating back around three hundred years. Some of these are only viewable with 200x zoom and 2400 dpi.

---

### Post by tubezninja on 2008-03-11
> **nonaguy said:**
>  Also, has anyone faced a situation like this before, and if so, what did you do? Does anyone have any suggestions or anything?

I'm involved in a similar project, though we are not using the TIFF files as our presentation format.  The plan is to use the TIFFs for preservation purposes, but the presentation will be in JPEG2000, using an [Aware]("http://www.aware.com/imaging/digitalarchives.htm") SDK which will convert the TIFFs to JP2, and serve the images much more quickly than it would take people to download a TIFF.

Aware is commercial software though, and can run $10,000-$14,000 for the whole package.  So, this may or may not be in the realm of possibility for you.

FWIW: The Aware thing is something we're migrating TO.  At present, we're using the open source [djvulibre]("http://djvu.sourceforge.net/") to convert our presentation files in to djvu format.  The drawback here is that users have to install a [djvu plugin]("http://www.lizardtech.com/download/dl_download.php?detail=doc_djvu_plugin&platform=win") to view the files, and it's not a plugin most people are familair with.

---

