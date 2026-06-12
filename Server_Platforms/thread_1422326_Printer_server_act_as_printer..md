---
title: "Printer server act as printer."
date: 2010-03-05
forum: Server Platforms
---

### Post by artheus on 2010-03-05
Hey!

I was at a school a couple of days ago. A design school.
In the printer-room they had a desktop pc which acted as a printer server. And when they printed from a computer somwhere in the school network, the printer server took this job and put it in a list. And they had to go to the server, to make it print the queued jobs.

That is something I would really like to do at the server at work, as we're having some trouble finding drivers for all the kinds of Windows versions they've got.

So if the server could act as a printer, and we could only install one printer driver for that printerserver on the client computers, it would be perfect!
There is multiple printers installed on the server, so it has got to be possible to choose which printer to print from.

Both printers are HP.

Cheers,
Artheus

---

### Post by stlsaint on 2010-03-05
This should get you in the right direction. It was last used this past november so should still be valid minus a few minor changes maybe in CUPS!

[http://ubuntuforums.org/showthread.php?t=310450&page=3](http://ubuntuforums.org/showthread.php?t=310450&page=3)

---

### Post by mcarrara on 2010-03-05
I use Samba and Cups to print.  Samba can hand out the print drivers, either a universal PS driver or the actual Windows driver depending on how it is set up.  We have been using it for two years with only minor issues. We have over 200 computers and 9 printers.

I do NOT know if it can be set up to hold the job until you get to the server, but I wouldn't doubt it could be set up that way.  Samba documentation is long and detailed and mostly correct.  I have found a few time it is out of date which did cause some grief.

Mark

---

### Post by artheus on 2010-03-06
> **stlsaint said:**
> This should get you in the right direction. It was last used this past november so should still be valid minus a few minor changes maybe in CUPS!

[http://ubuntuforums.org/showthread.php?t=310450&page=3](http://ubuntuforums.org/showthread.php?t=310450&page=3)



Thank you! But this still requires the printer drivers to be installed on the client machines. Or am I wrong?

The thing is that I would want the server to look like a network printer on the client machines. So I could have 10 printers connected to the server, but only need to install one driver on the client machines, because of that some of the client machines have got some problems with installing the printer drivers.

And I would really want the print-jobs to wait on the server, until a person walks to the server, and set up the print job:

    * Choose printer
    * Choose paper source
    * Choose paper type
    * Additional options

Cheers,
Artheus

---

