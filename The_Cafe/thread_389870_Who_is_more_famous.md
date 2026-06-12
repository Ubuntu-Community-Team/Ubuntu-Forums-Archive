---
title: "Who is more famous?"
date: 2007-03-21
forum: The Cafe
---

### Post by chalimac on 2007-03-21
**Fame Kalibrato**r 0.2 released.

Find out who is more famous and quantify their relationship in numerical terms with this fame calibrator written in pyqt.

[[IMG]http://img354.imageshack.us/img354/6408/famekalibratorwr9.th.jpg[/IMG]](http://img354.imageshack.us/my.php?image=famekalibratorwr9.jpg)

Just enter two names or concepts and the program will quantify their fame and their degree of relatedness according to data from YahooSearch. It will also download random images associated with the query.

Some interesting queries:

Paris Hilton Vs Madonna
The Beatles Vs Rolling Stones
Luck Vs Destiny
Love Vs Sex
Marilyn Monroe Vs Arthur Miller
Marlon Brando Vs James Dean

... Have Fun!

If you find some curious results, post them in this thread. 

DOWNLOAD:

[http://www.kde-apps.org/content/show.php/Fame+Kalibrator?content=54990](http://www.kde-apps.org/content/show.php/Fame+Kalibrator?content=54990)

INSTALLATION (very easy):

Unpack, cd to kalibrator directory and run in terminal "python kalibrator.py" or "./kalibrator.py" if you turned the archive into executable.

It requires the pyqt module (if you installed Amarok you already have it).

---

### Post by karellen on 2007-03-21
:lolflag: yeap, the best way to waste your spare time ;)

---

### Post by spinflick on 2007-03-21
What's a hotel doing in the list? \\:D/

---

### Post by chalimac on 2007-03-21
> **spinflick said:**
> What's a hotel doing in the list? \\:D/

Where have you been the last 4 years?  ](*,)

---

### Post by spinflick on 2007-03-21
There's always one that will fall for it. :lolflag:

---

### Post by Engnome on 2007-03-21
[http://www.googlefight.com/](http://www.googlefight.com/)

---

### Post by DoctorMO on 2007-03-21
Practice my packaging skills, attached you can find a deb and the source packages. it should also create an icon in the menu for you ;-)

---

### Post by maxamillion on 2007-03-21
> **Engnome said:**
> [http://www.googlefight.com/](http://www.googlefight.com/)

zomg, funniest site I have seen in a while ..... linux > apple in googlefight ;)

---

### Post by floke on 2007-03-21
I couldn't resist this (and yes, I know its wrong so don't take it the wrong way....)

---

### Post by chalimac on 2007-03-21
> **DoctorMO said:**
> Practice my packaging skills, attached you can find a deb and the source packages. it should also create an icon in the menu for you ;-)

Thanks for the package but something is wrong in it. It created a "search" folder in my kubuntu desktop with the yahoo api. It also installs the yahoo module in python's path. That's problematic because people might have other versions of python. It is enough for the program to have the yahoo folder in the same directory. There is no need to insert the modules into python unless you plan to develop with them.

This small python apps generally don't need much packaging. Thanks for your efforts, anyway.

---

### Post by DoctorMO on 2007-03-21
No but you should always package you applications with the intent that they'll be installed in some form. some of the most annoying tools I know have been poorly packaged scripts.

As for your modules, well I would have given them a better name, class space is precious and stomping over someone elses libs locally or system wide is not a good thing. perhaps renaming yahoo to the name of your application, then they can be installed correctly or run from the directory without risk.

Besides my hope was that you didn't know how to package it and would take the example.

---

