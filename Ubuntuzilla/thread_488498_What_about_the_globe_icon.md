---
title: "What about the globe icon?"
date: 2007-06-30
forum: Ubuntuzilla
---

### Post by Bob Pendleton on 2007-06-30
Hi, just used ubuntuzilla.py, now I want to update the globe icon on my desktop bar that opens firefox (it still takes me to 1.5 instead of 2.0)  I think what I want to do is set properties for this launcher.  The "old" value is firefox %u, but that still gets me to 1.5.  Evidently the script didn't remove the old version of firefox.  So where do I look for the new version?  I keep my own downloaded s/w in /usr/pkg, and when I first tried to download firefox 2.0 I unzipped the archive there, but clicking on the firefox icon /usr/pkg/firefox/firefox-bin does not work.  Where did ubuntuzilla put the thing?

Thanks for your help;)

bob pendleton

---

### Post by Bob Pendleton on 2007-06-30
Well, my son helped me make it work, as originally downloaded to /usr/pkg/firefox, I had to run the shell script to complete the installation.  I still don't know where the python script put the firefox folder.  Hmm.m..mm...;)

---

### Post by nanotube on 2007-06-30
hi,
all that info is on the homepage for ubuntuzilla :)
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

it puts the downloaded software into /opt 
so firefox would go into /opt/firefox, e.g.

the default firefox link in /usr/bin also gets pointed to the new firefox in /opt

the repositories version stays on your computer, and becomes /usr/bin/firefox.ubuntu

so earlier, when your icon linking to 'firefox %u' didn't work, that probably means the script didn't finish successfully, or you didn't run it. :)

hope that clears it up. :)

---

