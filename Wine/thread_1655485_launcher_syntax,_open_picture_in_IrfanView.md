---
title: "launcher syntax, open picture in IrfanView"
date: 2010-12-29
forum: Wine
---

### Post by cagliostro on 2010-12-29
Maverick Meerkat, Wine 1.3.10 installed, got IrfanView 4.28.

(In past I had used IrfanView 3.98, but the newer Wine can handle the more recent IrfanView...I think.)

I want pictures to load **in** IrfanView. Previously used this shell script, similar to one that works in Puppy Linux. But in Ubuntu all I can do is get it to start IrfanView itself, not to load pictures in IrfanView:

#!/bin/sh
# Purpose: To convert Linux-style filename to Windows-style to pass as an
# argument to Irfanview
Filename=${1//\//\\}
#this is my installation path to Irfanview
wine "/home/david/.wine/drive_c/Program Files/IrfanView/IrfanViewPortable.exe" "$Filename"

_________________________

IrfanView works, no need to set an argument. With old version shift-G was dark, now works perfectly.

In Ubuntu, am using the script (command on one line):

#!/bin/sh
# Purpose: To convert Linux-style filename to Windows-style to pass as an argument
# to Irfanview within wine. This is my installation path to Irfanview Portable 4.28
wine /home/david/.wine/drive_c/Program\ Files/IrfanView/IrfanViewPortable.exe "Z:\\$(echo "$@" | sed 's/\//\\/g')" $@


Simply right-click on .jpg, and set "Open With" to whatever you name this script file. Thanks anyway, found the answer.

---

