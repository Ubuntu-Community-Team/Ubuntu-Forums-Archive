---
title: "LibreOffice 4.0.1 Final (2013-03-06)"
date: 2013-03-06
forum: The Cafe
---

### Post by The Spectre on 2013-03-06
LibreOffice 4.0.1 Final is Released...

[http://www.libreoffice.org/download](http://www.libreoffice.org/download)

[ATTACH=CONFIG]239832[/ATTACH]

---

### Post by MadmanRB on 2013-03-06
And still no PPA

---

### Post by vasa1 on 2013-03-06
> **MadmanRB said:**
> And still no PPA
Maybe there's a shortage of someone to do the work?

---

### Post by Jakin on 2013-03-06
I have the normal LibreOffice ppa which gave the upgrade to 4.0.1.1 just yesterday. I must say libreOffice is much faster than before, but haven't really explored new features.

---

### Post by na5h on 2013-03-07
LibreOffice 4.0.1 is now available through the main PPA:
sudo add-apt-repository ppa:libreoffice/ppa

...the Unity appmenu is working too!

---

### Post by The Spectre on 2013-03-07
I have found it Quicker to just Download the deb files from [http://www.libreoffice.org/download/?nodetect](http://www.libreoffice.org/download/?nodetect) and install LibreOffice manually.

Sometimes it takes forever for the PPA's to get updated. (I'm impatient)

Plus you cant get much easier than "sudo dpkg -i *.deb" to install it.

Just follow the instructions in the README file included in the Download and you should be fine.

---

### Post by neu5eeCh on 2013-03-07
Document Foundation keeps touting its compatibility with DOC & DOCX. But there's one item -- so simple, so basic, so elementary, so freaking uncomplicated and obvious -- that, to my knowledge, they still haven't done anything about it. Is it possible to vertically center text without creating boxes, frames and balancing spoons on ones nose? Conversely, up through 3.6, if I vertically centered a wee tiny period ---> . <--- with Word, just one little pixel (not even a DOCX file but DOC), and tried to open it with LO. LO would barf all over my laptop. Has this changed? :popcorn:

---

### Post by na5h on 2013-03-08
> **The Spectre said:**
> I have found it Quicker to just Download the deb files from [http://www.libreoffice.org/download/?nodetect](http://www.libreoffice.org/download/?nodetect) and install LibreOffice manually.

Sometimes it takes forever for the PPA's to get updated. (I'm impatient)

Plus you cant get much easier than "sudo dpkg -i *.deb" to install it.

Just follow the instructions in the README file included in the Download and you should be fine.

The manual download didn't have support for the Unity appmenu. Don't know whether they've fixed it yet...

---

### Post by vanadium on 2013-03-08
> **na5h said:**
> 

...the Unity appmenu is working too!
It isn't. That is, the menu is indeed hidden in the top bar, but you cannot open it using the usual hotkeys, e.g. alt+f to open the file menu. For this reason, I still disable the global menu, although I like it very much if it works well as in other applications.

---

### Post by ssam on 2013-03-08
> **VTPoet said:**
> Document Foundation keeps touting its compatibility with DOC & DOCX. But there's one item -- so simple, so basic, so elementary, so freaking uncomplicated and obvious -- that, to my knowledge, they still haven't done anything about it. Is it possible to vertically center text without creating boxes, frames and balancing spoons on ones nose? Conversely, up through 3.6, if I vertically centered a wee tiny period ---> . <--- with Word, just one little pixel (not even a DOCX file but DOC), and tried to open it with LO. LO would barf all over my laptop. Has this changed? :popcorn:

I guess that is this issue [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=36117](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=36117)

If you have a simple doc/docx file with vertically aligned text that LO fails to open attach it to the bug.

---

### Post by The Spectre on 2013-03-08
> **na5h said:**
> The manual download didn't have support for the Unity appmenu. Don't know whether they've fixed it yet...

You are 100% Correct.:D

 Manual Install[COLOR=#ffffff] -------------------------------------------------------[/COLOR]PPA Inatall
[ATTACH=CONFIG]239896[/ATTACH]       [ATTACH=CONFIG]239897[/ATTACH]

Originally LibreOffice 4.0.1 would not come up when I added the Main PPA **[FONT=Ubuntu][COLOR=#333333]ppa:libreoffice/ppa [/COLOR][/FONT]**[COLOR=#333333]so [/COLOR]I ended up trying the 4.0.x PPA **ppa:libreoffice/libreoffice-4-0**.
[B][FONT=Ubuntu][COLOR=#333333]
[/COLOR][/FONT][/B][FONT=Ubuntu][COLOR=#333333]That allowed me to install [/COLOR][/FONT]LibreOffice 4.0.1 but the appmenu did not work correctly plus the LibreOffice Toolbar Menu looked different and Not in a good way.

So I installed it Manually and like you pointed out the appmenu was not working but at least the Toolbar Menu looked the way it is supposed to.

I just tested the **ppa:libreoffice/libreoffice-4-0 **in VirtualBox and it is now working correctly also. 

Maybe they were still uploading some of the Packages or maybe something was FUBAR that has since been fixed. 

I wonder if it matters which PPA is used, the Main PPA or the 4.0.x PPA to keep LibreOffice 4 up to date?

---

### Post by rewyllys on 2013-03-08
> **The Spectre said:**
> . . . .I just tested the **ppa:libreoffice/libreoffice-4-0 **in VirtualBox and it is now working correctly also. 

Maybe they were still uploading some of the Packages or maybe something was FUBAR that has since been fixed. . . .
Reassured by your comments, I just followed **na5h**'s suggestion of adding the LibreOffice ppa, ignored the warning that appears in the terminal, added 
```
sudo apt-get update
``` and, using the Synaptic Package Manager, easily installed LibreOffice 4.0.1 in Linux Mint Maya (which is based on Ubuntu 12.04).

LO 4.0.1 appears to be functioning just fine.

---

### Post by neu5eeCh on 2013-03-08
> **ssam said:**
> I guess that is this issue [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=36117](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=36117)

If you have a simple doc/docx file with vertically aligned text that LO fails to open attach it to the bug.

Yeah...  :roll: That's *my* bug report.  Apparently, I'm not squeaking loudly enough.:biggrin:

---

### Post by na5h on 2013-03-09
> **The Spectre said:**
> I wonder if it matters which PPA is used, the Main PPA or the 4.0.x PPA to keep LibreOffice 4 up to date?
Well...the 4.0.x PPA will only get updates for LibreOffice 4, whereas the main PPA will get updates for future versions as well (and will update LibreOffice 4 to the next version when it becomes available).

---

### Post by helotbc on 2013-03-11
Any word on when LOv4 will be added to the repo's?

---

### Post by pqwoerituytrueiwoq on 2013-03-12
Version 4.0.1.2 (Build ID: 400m0(Build:2)) is in the raring repos

---

