---
title: "Question on output of klamav run"
date: 2009-11-30
forum: Security
---

### Post by anewguy on 2009-11-30
I installed klam antivirus from the repositories over the weekend.  I also tried installing Internet Explorer 8 (I wanted to play shockwave game - not supported in Linux) via the information on this link:

[http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html]("http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html")

Well, IE8 didn't cooperate at all, so I'm just leaving it as is.  I did run a klam anti-virus scan starting at "/" and it gave me several warnings for things I had to quarantine, and I don't understand why it did or what might happen (e.g., did I quarantine something needed by Ubuntu?).

The list of files quarantined follows:

[email]dave@dave-desktop:~/.klamav[/email]/quarantine$ ls -al
total 117704
drwx------ 2 dave dave     4096 2009-11-30 13:34 .
drwxr-xr-x 3 dave dave     4096 2009-11-30 13:34 ..
-r-------- 1 dave dave 16883056 2009-11-28 03:19 6C2E9E33d01:Mon November 30 2009 04-11-40-188 am
-rw-r--r-- 1 dave dave  1481576 2009-10-20 05:20 beam:Mon November 30 2009 04-18-08-961 am
-rw-r--r-- 1 dave dave  1481576 2009-10-20 05:20 beam:Mon November 30 2009 05-03-07-724 am
-rw-r--r-- 1 dave dave  1612648 2009-10-20 05:20 beam.smp:Mon November 30 2009 04-18-08-695 am
-rw-r--r-- 1 dave dave  1612648 2009-10-20 05:20 beam.smp:Mon November 30 2009 05-03-07-379 am
-rw-r--r-- 1 dave dave  1060356 2009-06-04 01:01 fppkg:Mon November 30 2009 04-12-54-684 am
-rw-r--r-- 1 dave dave  1060356 2009-06-04 01:01 fppkg:Mon November 30 2009 04-57-58-876 am
-r-------- 1 dave dave 16883056 2009-11-28 03:19 IE8-WindowsXP-x86-ENU.exe:Mon November 30 2009 04-11-04-868 am
-rw-r--r-- 1 dave dave  1502668 2009-05-14 12:01 libcfitsio.so.3.140:Mon November 30 2009 04-17-03-120 am
-rw-r--r-- 1 dave dave  1502668 2009-05-14 12:01 libcfitsio.so.3.140:Mon November 30 2009 05-02-02-576 am
-rw-r--r-- 1 dave dave   739684 2009-11-05 05:31 libclamav.so.6.0.5:Mon November 30 2009 04-17-15-796 am
-rw-r--r-- 1 dave dave   739684 2009-11-05 05:31 libclamav.so.6.0.5:Mon November 30 2009 05-02-14-892 am
-rw-r--r-- 1 dave dave   953100 2009-10-22 14:32 libexempi.so.3.2.1:Mon November 30 2009 04-17-31-876 am
-rw-r--r-- 1 dave dave   953100 2009-10-22 14:32 libexempi.so.3.2.1:Mon November 30 2009 05-02-30-996 am
-rw-r--r-- 1 dave dave   244896 2009-06-22 08:54 libgsf-1.so.114.0.15:Mon November 30 2009 04-16-45-276 am
-rw-r--r-- 1 dave dave   244896 2009-06-22 08:54 libgsf-1.so.114.0.15:Mon November 30 2009 05-01-45-412 am
-rw-r--r-- 1 dave dave  3797704 2009-09-19 12:35 libkio.so.4.2.0:Mon November 30 2009 04-16-29-828 am
-rw-r--r-- 1 dave dave  3797704 2009-09-19 12:35 libkio.so.4.2.0:Mon November 30 2009 05-01-30-196 am
-rw-r--r-- 1 dave dave   383960 2009-10-22 20:09 libpackage2.so:Mon November 30 2009 04-16-24-552 am
-rw-r--r-- 1 dave dave   383960 2009-10-22 20:09 libpackage2.so:Mon November 30 2009 05-01-24-980 am
-rw-r--r-- 1 dave dave   156446 2009-06-04 01:01 libpzipper.a:Mon November 30 2009 04-14-51-619 am
-rw-r--r-- 1 dave dave   156446 2009-06-04 01:01 libpzipper.a:Mon November 30 2009 04-59-52-992 am
-rw-r--r-- 1 dave dave   252152 2009-08-17 12:11 libxpinstall.so:Mon November 30 2009 04-17-56-654 am
-rw-r--r-- 1 dave dave   252152 2009-08-17 12:11 libxpinstall.so:Mon November 30 2009 05-02-55-421 am
-rw-r--r-- 1 dave dave 13161860 2009-11-09 07:54 libxul.so:Mon November 30 2009 04-16-55-412 am
-rw-r--r-- 1 dave dave 13161860 2009-11-09 07:54 libxul.so:Mon November 30 2009 05-01-55-300 am
-rw-r--r-- 1 dave dave    20760 2009-10-20 04:57 prim_zip.beam:Mon November 30 2009 04-18-07-496 am
-rw-r--r-- 1 dave dave    20760 2009-10-20 04:57 prim_zip.beam:Mon November 30 2009 05-03-06-205 am
-rw-r--r-- 1 dave dave  8119486 2009-08-31 17:12 wine_gecko-1.0.0-x86.cab:Mon November 30 2009 04-20-45-368 am
-rw-r--r-- 1 dave dave  8119486 2009-08-31 17:12 wine_gecko-1.0.0-x86.cab:Mon November 30 2009 05-05-41-024 am
-r-------- 1 dave dave 19635712 2009-08-03 23:42 xul.dll:Mon November 30 2009 04-12-28-500 am
-rw-r--r-- 1 dave dave    39736 2009-06-04 01:00 zipper.o:Mon November 30 2009 04-14-52-182 am
-rw-r--r-- 1 dave dave    39736 2009-06-04 01:00 zipper.o:Mon November 30 2009 04-59-53-534 am


Can anyone tell me what these things are, why klamav wanted to quaratine them, etc.?

I am so used to the "Linux can't get viruses, etc." talk that I am confused as to why I had anything show up.

Thanks in advance!

Dave :)

---

### Post by bodhi.zazen on 2009-11-30
I do no thave an explicit answer for you , rather some advice.

First, there are reports that some viruses will run in wine. If you feel you were affected by such a virus you should report it to winehq ;)

Also see the security sticky, there is a short section on wine.

Second, in my opinion Linux antivirus scanners are not so great. There are a ton of false positives.

Google search those files :

[http://www.google.com/search?q=klamav+beam&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=klamav+beam&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

And so on for the other files ;)

Considering there are no known active viruses that run on Linux, and the sheer number of false positives, I do not run antivirus.

---

### Post by anewguy on 2009-11-30
Thanks, Bodhi.Zazen.  I really didn't think I had a Windows-type virus, and I just didn't understand the Linux ones.  Since there are so many false positives, I think I'll also just disable the anti-virus for now.  I feel a little guilty in that I'd hate to forward an email with a virus to a friend who is a Windows user, but in the long run there is only so much I can do.

Thanks again!

Dave :)

---

