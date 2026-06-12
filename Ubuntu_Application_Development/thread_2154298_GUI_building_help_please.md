---
title: "GUI building help please?"
date: 2013-06-14
forum: Ubuntu Application Development
---

### Post by aaronmarsh632 on 2013-06-14
Hi,

How would I go about building a GUI for a command line program for ubuntu please? I have no experience with this so if anyone can point me to a tutorial would be great. I only have experience with autoit in windows which I use to build guis for windows cl tools.

Thanks

Aaron

---

### Post by oldfred on 2013-06-14
I have been tying to teach myself python with both qt & gtk, but if you just want a gui for bash:

 [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
Whiptail is a program that allows shell scripts to display dialog boxes
[http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail](http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail)
zenity, kdialog for kde


 Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

      
 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by aaronmarsh632 on 2013-06-15
Hi,

Thanks a lot for these links, I will have a good look through them all :)

---

### Post by JRV on 2013-06-15
Zenity is another option.  It is installed in Ubuntu by default.

For help:
```

man zenity

```
or
```

zenity --help

```

---

