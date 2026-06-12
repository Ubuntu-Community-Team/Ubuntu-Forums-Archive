---
title: "Really simple question"
date: 2011-03-04
forum: Wine
---

### Post by Canime on 2011-03-04
I've installed wine to run some programs that I have in a separate partition on the same hard disk. I intend to run programs that I have already installed on my windows system from linux, and I assume there is no need to re-install them into linux? 

So far they show just internet explorer and notepad. Is this true?

---

### Post by An Sanct on 2011-03-04
Yes, this is true. Only explorer and notepad are shown.

Wine has a kind of sandbox like architecture, it also has its own registry (so any settings under windows are not affecting wine), that means that if programs are more complicated, they will not perform correctly (dll/ocx/path dependencies, registry settings, file locations,...)

---

### Post by Canime on 2011-03-04
Great, but I am having some trouble in that I can't really locate any of them, and have fooled around needlessly trying to access them through the settings.

Let's see, If I go to wine settings and select the tab to configure and add programs, I get the opportunity to browse for programs to install? 

I've tried accessing these same programs through the Places menu option, getting limited results from the wine. Actually it is an error message saying the program cant run.

Am I to access these programs through that tab?

---

### Post by An Sanct on 2011-03-04
You can install MSi and exe (installations) through wine
Applications > Wine > Configure Wine, "Applications" tab, Add Application
Or by right clicking the installation file and selecting "Open With Wine Windows Program Loader"

Small note: installation may crash if it is not run from Wine c: drive (they sometimes just cannot handle it)

---

