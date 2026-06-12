---
title: "New project - TimeSaver (testers wanted)"
date: 2006-07-29
forum: The Cafe
---

### Post by cro.smiley on 2006-07-29
I've recently started developing simple time managment application and now I need someone to test it.

With TimeSaver user can easyly manage many tasks each with his own name, type, duration, description and status. Task can also run a command after it's time passes. 

Sessions can be saved to xml file that can also be used for report view.
Sample report view check [here]("http://timesaver.sourceforge.net/samples/sample%20report.xml").

More about project read here: [timesaver.sourceforge.net]("http://timesaver.sourceforge.net")
If you are interested in testing it, here is [download link]("http://prdownloads.sourceforge.net/timesaver/tsaver-0.3.tar.gz?download").

Thank you in advance and I hope I will recive some feedback.

[IMG]http://sourceforge.net/dbimage.php?id=82234[/IMG]

---

### Post by cro.smiley on 2006-08-01
New beta version is out.
Application is much stable, some bugs are fixed and new features added.
Session saving and report view is improved.

New features:
[LIST][*]New session option[*]Session status view[*]Task editing[*]Custom task type[*]Gnome shortcut[*]Tasks can be paused[/LIST]

Project has over 100 downloads and I've recieved a few feedbacks.
But there is still much to test and you are welcome to send your critique.

[Download on sourceforge.net]("http://prdownloads.sourceforge.net/timesaver/tsaver-0.4.tar.gz?download")
More about project: [timesaver.sourceforge.net]("http://timesaver.sourceforge.net")

[IMG]http://timesaver.sourceforge.net/images/tsaver_beta3.jpg[/IMG]

---

### Post by Engnome on 2006-08-01
no debs #-o

---

### Post by cro.smiley on 2006-08-01
> **Engnome said:**
> no debs #-o

You can check now. I've just made first debian package using instructions from [this thread]("http://www.ubuntuforums.org/showthread.php?t=51003"). It worked ok at me, but there could still be some dependencies problems.

You can try it and give me a report if you wish.
If it is possible, maybe I'll put it in Ubuntu repository someday.

---

### Post by cro.smiley on 2006-08-31
New beta release is out.

Check new features and news: [http://timesaver.sourceforge.net]("http://timesaver.sourceforge.net")
Wiki pages: [http://www.bluwiki.org/go/TimeSaver]("http://www.bluwiki.org/go/TimeSaver")
Download: [sources on sourceforge.net]("http://sourceforge.net/project/showfiles.php?group_id=170378&package_id=194451")

[IMG]http://img371.imageshack.us/img371/4481/tsaverbeta05jy9.jpg[/IMG]

I need testers to help me debug and improve application.
So if you have some free time feel free to try TimeSaver and send me your feedback.

NOTE: [wxWidgets]("http://www.wxwidgets.org/") are required.

---

### Post by Stone123 on 2006-08-31
Zdravo : 

stone123@ubuntu:$ tsaver 
tsaver: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory

So it is some deps that are not met.

Running on edgy knot  lastest kernel 2.6.17-6-386

Installed : libwxgtk2.6-dev

And its working.

---

