---
title: "TabRite (tabwin43) mostly working"
date: 2009-07-04
forum: Wine
---

### Post by trulan on 2009-07-04
This is my first attempt at using wine so bear with me.

Tabrite is an old Windows tablature editor (formerly shareware, now a free download) for instruments with four, five, and six strings.  In its day, it was a valuable program and we have amassed a rather large collection of files for it.   There are a few bugs running under wine, but there were running in Windows too.  So far, I have been able to create and open files, print them, and generate midi files (they cannot be played from inside the program - bug exists in Windows too IIRC)

***Edit: revised installation instructions:***

1. Extract the .zip file somewhere in c:.
2. Make sure that mfc40.dll exists in c:/windows/system32.
3. Copy Tab.ttf from the .zip into c:/windows/fonts.  Make sure you have the standard Windows fonts there also.  (I think MS Sans Serif and Arial are the only ones needed)
4. Run setup.exe.
5. Copy the rest of the contents of the .zip into c:/Program Files/tabwin43.
And it should work.  If the installer throws errors about registering files, run the regsvr commands in post #3.

***End of edit - back to how I actually installed it:***

For reference purposes only - don't do it this way:
1. Extract zip file into ~/.wine/drive_c/tabwin43 (note - .wine is a hidden folder)
2. Double-click setup.exe
3. Click 'ignore' at the three warnings it throws (we'll fix them in a minute)
4. Copy Tab.ttf from tabwin43 into ~/.wine/drive_c/windows/fonts
5. Copy other needed fonts there as well (Don't know yet which ones are needed, I just dumped in all my windows fonts and it fixed it.)
6. Copy mfc40.dll (from windows XP) into ~/.wine/drive_c/tabwin43
7. Open a terminal.  Run the following commands:
```
cd ~/.wine/drive_c/tabwin43
wine regsvr32 HSlide32.OCX
wine regsvr32 MIDIIO32.OCX
wine regsvr32 MIDIFL32.OCX

```To start the program, run:
```
wine ~/.wine/drive_c/tabwin43/tabwin43.exe
```Or double-click tabwin43 from that directory.  If you run from the start menu, midi won't work.

If anyone finds this useful, or has any tips for a newbie like me, please let me know.

---

### Post by cogadh on 2009-07-05
About the only two changes I might suggest is putting the mfc40.dll in Wine's system32 directory and making the install directory in the Program Files directory instead of in the root of Wine's "C:" drive. The mfc40.dll file is normally found in the system32 directory on Windows and that is usually where Wine and applications expect to find it. A few of the apps I've used that try to install in the root of the "C:" drive have encountered some odd problems (possibly the cause of your midi issues?).

EDIT - Oooh, I just noticed something else. When running a Wine app from the terminal, it is best to change directories to that apps install directory first:
```
cd ~/.wine/drive_c/tabwin43
wine tabwin43.exe
```
That way the application already has its paths set correctly; think of it like the "Run in" line in a Windows shortcut.

---

### Post by trulan on 2009-07-05
OK, thanks for the tips.  I copied all the files from the .zip from c:/tabwim43 into c:/Program Files/tabwin43 (this was created by the installer).  Midi works now when run from the start menu.  I tried running the installer from there but won't install to the directory from which you are running setup.

I had to have mfc40.dll in the same directory as the .OCX files for the regsvr command to work, that's why I put it in the unzipped directory.  If I run:
```
cd ~/.wine/drive_c/windows/system32
wine regsvr32 HSlide32.OCX
wine regsvr32 MIDIIO32.OCX
wine regsvr32 MIDIFL32.OCX
```That works too, and is better.

Also, if I run setup now, it completes without the errors.  Maybe because mfc40.dll is already in place?  Or because the .OCX files are already registered?

I'll edit the first post and fix that stuff.

Midi files still don't play from inside the program (it generates them just fine).  Throws an 'automation' error.  I think it's a program bug, not wine's fault.

---

