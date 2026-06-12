---
title: "Installing IE under Wine???"
date: 2010-08-22
forum: Wine
---

### Post by dougalkerr on 2010-08-22
Without going and joining yet another forum, I am hoping some good person here will know why I am having difficulty installing IE through Wine. Here is the text from Terminal after installing ies4linux;

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'.
  (Details: serial 12278 error_code 13 request_code 56 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I am running one of the latest versions of Wine, I think as the Ubuntu version is 10.04.
Any ideas folks?? I am trying to install a video viewer from a car seat manufacturer so that I can configure the colour of leather seats for my car...

Thanks..

---

### Post by kobylecki on 2010-09-01
I have exactly the same problem. Anyone can tell anything?

---

### Post by philinux on 2010-09-01
Move to Wine Forum.

---

### Post by lordhaworth on 2010-09-01
What is output of:

```

wine --version

```

---

### Post by Mark Phelps on 2010-09-01
> **dougalkerr said:**
> I am trying to install a video viewer from a car seat manufacturer so that I can configure the colour of leather seats for my car.

Before you go to a lot more trouble, you should check the WineHQ site below to confirm that your MS Windows app is listed and that it has a high compatibility rating: 

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If not listed, or low rating, you're most probably wasting your time trying to install the app under Wine.

---

### Post by bretticus on 2010-11-06
Have the same issue. Can you provide a link to the any subsequent forums posts (this is the only relevant posting I could find?) The author writes this to work on wine (kinda the point.) The problem is in the installer that appears to be python. 

$ wine --version
wine-1.2.1

$ python --version
Python 2.6.6

Error Message:
The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 4253 error_code 9 request_code 154 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

On second thought that may be a wine error message after all. I'll try upgrading wine. I did get a warning form the installer:

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

More to come...

Nevermind, 1.2.1 is the latest stable version. Anybody had any luck with this? I am doing a stupid Intuit QuickBooks App register (the most hassling idiot-inspired gateway setup I've ever done. If the all the previous hoops weren't enough, the IE-only final registration URL takes the cake!)

---

### Post by nigel on 2010-11-06
IES4Linux is a dead project i believe the last release was over 2 years ago closer to 3 actually.

[http://en.wikipedia.org/wiki/IEs4Linux](http://en.wikipedia.org/wiki/IEs4Linux)

I got the same errors you reported

---

### Post by dougalkerr on 2010-11-07
I am closing this thread. I have not needed to use IE since I started this thread. In fact I can't even remember what I was trying ti use it for.
I tried it again today out of curiosity since I have the latest UE of Ubuntu 10.10 installed and nope, it still gives the same error messages.

I agree with the last post - it is dead. I am not going to waste any more time trying to run Microsoft programs through Wine. If I have to use a MS program then it will be on a Microsoft loaded machine at work.
My own laptop and desktop machines are pure Linux these days and do everything I need without question.

Good luck to those of you that need IES4Linux I don't think you will be able to use it unless it is on an older version of Ubuntu.

---

