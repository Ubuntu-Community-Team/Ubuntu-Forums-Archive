---
title: "How can I set a wine program as the default program to open certain file formats?"
date: 2009-08-26
forum: Wine
---

### Post by nechus on 2009-08-26
Hello

I'm using the Windoze program IrfanView 4.25 to open image files. I want to use it as the default program to open these files. I looked at the properties of the link that wine created on my desktop, where I found the following command:
[FONT=Courier New]env WINEPREFIX="/home/nelson/.wine/IrfanView" wine "C:\Archivos de programa\IrfanView\i_view32.exe"[/FONT]

When I click on that link, IrfanView starts correctly, but when I want to set IrfanView as the default program to open image files and add this command to the programs listed under the "Open with" tab of image files, the... system(?) thinks that the program I want to use is called "env", not "IrfanView".

Is there a way to solve this?

Thanks

---

### Post by taslinux on 2009-08-29
Hi, Nechus.

I had a similar problem. I solved it by creating a bash script, which I assigned to the file type by right-clicking on the file, Properties/Open With/Add/Use a custom command/Browse, and browsing to the script. The script could be called irfan.sh and would read

#!/bin/bash

QUICKPARLOCATION="c:\\[path to application]"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

In your case I'm guessing the path would be something like

Program Files\\Irfan View\\Irfan View.exe

Note the double backslashes.

After you write the script and put it someplace, make sure you make it executable: right-click, Properties/Permissions, Execute: tick 'Allow executing file as program'

---

### Post by nechus on 2009-08-29
Thank you. I followed your instructions and this is the resulting script, but it still won't work. I might have made some mistake. Could you have a look at it, please?

#!/bin/bash

QUICKPARLOCATION="c:\\Archivos de programa\\IrfanView\\i_view32.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

Regards

---

### Post by taslinux on 2009-08-29
I just downloaded Irfan View 4.25 to try it myself. It seemed to install properly through Wine, but it will not run, either with a right-click on the .exe file and Open with Wine..., or through the Wine programs menu. I run Ubuntu 9.04. How did you get IrfanView to open?

---

### Post by taslinux on 2009-08-29
Hi again.

There is quite a bit about installing IrfanView under Ubuntu on the Web. I have installed the necessary extra Microsoft files, re-installed IV 4.25, but still cannot get it to run.

Getting back to your shortcut problem, it looks to me like your bash script is OK - I did not notice (sorry!) that you had posted the path

C:\Archivos de programa\IrfanView\i_view32.exe

in your first message.

I also re-checked my own bash script to the other Windows application, and yes, it works fine.

Interesting!

---

### Post by nechus on 2009-08-29
Hola!

Yes, installing IrfanView 4.25 was a nightmare. It was quite simple until 4.10, but then things started to get complicated. I found a tutorial somewhere on how to install it:

------------------------------------------------
Downlad winetricks:
Code:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Use winetricks to install "stuff" needed for IrfanView:
Code:

WINEPREFIX=~/Desktop/IrfanView sh winetricks mfc42 comctl32

Start IrfanView installer:
Code:

env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/iview425_setup.exe

IrfanView installer is placed on my Desktop - adjust path accordingly

Start IrfanView:
Code:

env WINEPREFIX=~/Desktop/IrfanView wine "C:\Program Files\IrfanView\i_view32.exe"

------------------------------------------------

Until 4.10 I was able to install IrfanView both with Wine and Crossover, and the latter always set IrfanView automatically as one of the programs listed under the "Open with" tab, and it worked well.:-s

---

