---
title: "Can't install Canon DPP underr Wine 1.2"
date: 2010-11-09
forum: Wine
---

### Post by fishtoprecords on 2010-11-09
I'm trying to install Canon's DPP 3.6 from the Canon OEM disk.
When I cd to 

cd /media/CanonEOS202W
wine setup.exe

the program starts, and initially asks for a selection of the Americas or the rest of the world. I can mouse click on the buttons, and they appear to depress (change color, etc) but the program does not proceed. Its as if the mouse clicks are not registering

Ubunto 10.04 fully up to date.
Wine 1.2

Thanks
pat

---

### Post by |{urse on 2010-11-09
> Installation

First you need to download updater from Canon website.

If you don't have previously installed version of DPP create following registry key:

HKLM/Software/Canon/DPP 

 Now run the installer and continue until the "License agreement" appears. Now don't click anything. Open terminal or your favorite file manager and find CanonUPW_000 directory in one of the following directories and copy it somewhere:

C:/windows/temp/CanonUPW_000/ 
C:/users/username/Temp 

 Continue with installation, it will most likely crash. Now there should be some files in:

C:/Program Files/Canon/Digital Photo Professional/ 

 But it will not work yet. Now run following commands from command line:

cabextract -d "$INSTALL_DIR" "$SOURCE_DIR/INST/DPP/ENGLISH/resdata.CAB" 
cabextract -d "$INSTALL_DIR" "$SOURCE_DIR/INST/DPP/COMMON/program.CAB" 
cabextract -d "$INSTALL_DIR"/icc "$SOURCE_DIR/INST/DPPLIB/COMMON/DATA.CAB" 
mv "$INSTALL_DIR"/icc/*.dll "$INSTALL_DIR" 
cabextract -d "$INSTALL_DIR" "$SOURCE_DIR/INST/Image Handling Library/COMMON/IHL_CMN.CAB" 

 where $INSTALL_DIR refers to the directory where DPP should be installed (eg ~/.wine/drive_c/Program Files/Canon/Digital Photo Professional) and $SOURCE_DIR contains path to the previously copied CanonUPW_000 directory.

Now try to run DPP (wine may already created menu entry, depends on when the installer crashed) through menu or using wine DPPViewer.exe If it runs, you are almost done. If not, try to run:

regsvr32 "$INSTALL_DIR"/*.dll

 Now it should start and run.

Taken from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7813]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7813")

Looks like TONS of fun to install.

---

### Post by fishtoprecords on 2010-11-09
Er, thanks. Perhaps I should just stick with UfRaw.....

---

