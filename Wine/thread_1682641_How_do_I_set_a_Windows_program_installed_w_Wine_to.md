---
title: "How do I set a Windows program installed w/ Wine to be default editor for PDFs?"
date: 2011-02-06
forum: Wine
---

### Post by Rubicon421 on 2011-02-06
I have installed PDF Xchange Viewer with Wine and everything is working fine. Now I would like to set it to be the default program to open when double clicking a PDF. When I right click a PDF, Xchange Viewer is not one of the options but there are several repeat entries for Wine. 

Does anyone know how to select the exe file for Xchange Viewer as the default?

---

### Post by cchhrriiss121212 on 2011-02-06
Under properties, try selecting Open With>Other Application, then do a custom command like this:
```
wine pathtoyour.exe
```
So if it is in your documents folder for example:
```
wine /home/user/documents/xchange.exe
```

---

### Post by Rubicon421 on 2011-02-06
I was able to get the Xchange viewer associated with a PDF so that it opens when I double click a PDF, but it doesn't actually open the document. It just pulls up the program with no document opened.

---

### Post by compactbrain on 2011-02-07
hi,
what i have done to associate a file to a wine program is copy a shortcut to the desktop, right click and go to properties and copy the command from there and then select open with from the file and paste in the command and select always use,
always worked for me but maybe the programs a bit buggy running in wine

---

### Post by Rubicon421 on 2011-02-07
> **compactbrain said:**
> hi,
what i have done to associate a file to a wine program is copy a shortcut to the desktop, right click and go to properties and copy the command from there and then select open with from the file and paste in the command and select always use,
always worked for me but maybe the programs a bit buggy running in wine

I thought this was going to work but it still just opened the program without opening the PDF. The command I copied and pasted using your method was:

env WINEPREFIX="/home/droid/.wine" wine C:\\windows\\command\\start.exe /Unix /home/droid/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/PDF-XChange\ PDF\ Viewer/PDF-Viewer.lnk

---

### Post by steveneddy on 2011-02-07
[http://www.linux.com/archive/feature/113907](http://www.linux.com/archive/feature/113907)

Both are available in the repos.

```
sudo apt get install xfig

sudo apt-get install flpsed
```

No need for using a Windows based application on you Linux box now.

And I think Open Office will edit .pdf files - although you may need an extension for that functionality.

---

