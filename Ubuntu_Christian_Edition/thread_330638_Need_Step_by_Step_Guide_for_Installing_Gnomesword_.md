---
title: "Need Step by Step Guide for Installing Gnomesword Modules"
date: 2007-01-03
forum: Ubuntu Christian Edition
---

### Post by chaplanger on 2007-01-03
I have sucessfully installed Gnomesword 2 -- Now I would like to download and install the modules from the Sword project.

I get as far as downloading the .zip files to my main desktop -- unzipping them and then I am stuck.  How do I get the module into the program modules 

For this example lets use ESV.zip
(1) I right click on the file and choose "Extract Here" which then produces the file: ESV.zip_FILES.

In Windows I could simply take out the two files found within here ("mods.d" and "modules") and drop them into the programs modules folders.  When I try this here I am told I don't have permissions to do this -- must mean I have to use command line and sudo -- this is where the logical progression escapes me.

My folder ESV.zip_FILES is located on my desktop (Home>David>Desktop) I do not know how to use the command line to get the unzipped modules into their roper home.

I have checked out "How to Install Anything in Ubuntu" and find that too many assumptions are being made and significant steps left out.

Any help here would be appreciated!



(which is located at usr/share/sword/modules/texts/ztext)

---

### Post by meng on 2007-01-03
Looks like you should extract them to ~/.sword
(~ is short for your home directory, in case you didn't know, e.g. /home/chaplanger)
[http://gnomesword.sourceforge.net/links.php](http://gnomesword.sourceforge.net/links.php)

BTW the "how to install" page doesn't pretend to cover installation of software MODULES, the instructions for doing this vary too much between different applications. Your critique is appreciated but I personally would not agitate for change.

---

### Post by chaplanger on 2007-01-03
> **meng said:**
> Looks like you should extract them to ~/.sword
(~ is short for your home directory, in case you didn't know, e.g. /home/chaplanger)
[http://gnomesword.sourceforge.net/links.php](http://gnomesword.sourceforge.net/links.php)

BTW the "how to install" page doesn't pretend to cover installation of software MODULES, the instructions for doing this vary too much between different applications. Your critique is appreciated but I personally would not agitate for change.

Thanks for the assist!  
BTW -- for those who have written the guide -- no offense intended.  Guess I was a bit frustrated at my own inability to synthesize and apply what I've been learning.  You all do a great job and of course it would be impossible to write a guide with every possible variation / contingency covered.

---

### Post by chaplanger on 2007-01-03
Well, I'm still stuck without getting any module installed -- here's what I did in terminal mode
----------------------------
david@david-desktop:~$ cd ~/.sword
[email]david@david-desktop:~/.swor[/email]d$ unzip ESV.zip
unzip:  cannot find or open ESV.zip, ESV.zip.zip or ESV.zip.ZIP.
[email]david@david-desktop:~/.swor[/email]d$ unzip ESV.zip_FILES
unzip:  cannot find or open ESV.zip_FILES, ESV.zip_FILES.zip or ESV.zip_FILES.ZIP.
[email]david@david-desktop:~/.swor[/email]d$ 
------------------------------------------------------------

So, I still have 27 modules waiting to be installed.  My use of two file names above ("ESV.zip" and "ESV.zip_FILES") is because I had extracted the original ESV.zip file to my deskto and wound up with the file ESV.zip_FILES.

I was expecting to at least get told that I didn't have permissions to install here. -- but didn't get that either.  I know I'm probably missing something painfully obvious. . . 
](*,)

---

### Post by meng on 2007-01-03
Yes I believe you are missing something obvious. Namely, that you are in the directory /home/david/.sword and trying to unzip a file that is in a different location (I think you said it might be on the desktop, which is /home/david/Desktop). unzip doesn't realize it has to look in there!!

So there are many ways to approach this, but one way would be:
cd ~/Desktop
mv *.zip ~/.sword/
cd ../.sword
unzip *.zip

Or else you could use the GUI: archive manager (file-roller) and choose the destination to extract to.

---

### Post by chaplanger on 2007-01-03
Meng, Thanks for hanging with me!  You've been awesome!
The steps you outline would have brought success without a doubt!

Prior to seeing this I did find a GUI way to do this as well.  Within GnomeSword the Module Manager is configurable.  It is possible for the Module Manager to rip the files from the web and install them directly into the program.  For instructions on how to accomplish this the GUI way check out:

[http://www.bible.org/assets/sword/gnomesword_install.html](http://www.bible.org/assets/sword/gnomesword_install.html)

Of course yo will need to substitute theURL from which you will be downloading the GnomeSword files (I would recommend finding the download page at  Crosswire.org since they have the full repository)

:D

---

### Post by LaserJock on 2007-01-04
Also note that there are quite a few modules in the Universe repo. In synaptic just do a search for "sword". There are a few commentaries, dictionaries, and Bible texts in 13 languages. We are trying to include as many as we can (licenses are the only problem ocassionaly)

-LaserJock

---

