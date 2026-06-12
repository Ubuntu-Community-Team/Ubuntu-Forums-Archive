---
title: "e-Book Install"
date: 2007-04-15
forum: The Cafe
---

### Post by bookinstall on 2007-04-15
I made an e-Book CD, and used autorun.inf to install the book to Windows XP systems.
Using a cmd batch file to copy the files, and copy the shortcut to the first page, to  Windows/Programs/Start. To uninstall the book, simply delete the book folder, and shortcut in Windows/ Program Files/

A simple copying of one folder to C:/Book/, containing about 325 files, html, png, etc.
Not the usual e-book format, rather a multi-linked group of web style pages. 
To start the book, I open an html frameset, with 2 frames, with the left frame an index frame,
and the right frame a display frame.

I don't know how to do this copying of files for Linux. I did drag a copy of the Book folder (from my CD-ROM disk) to my ubunto desktop, and created a launcher to open the Frameset. This works to read the book.

I want to be able to start the frameset from the Menu Bar Applications, and not have my Book folder and launcher visible on my desktop.

However I need to know how to do the same simple install for Linux, by invoking a  simple terminal script.  I tried to add my Book folder to the file system, but could not do so. 

Thanks for any help!

---

### Post by Polygon on 2007-04-15
so, do you just want to move files to like the users home folder, and then execute the index.html for the e-book?

thats fairly simple using the mv command, and the commands for firefox which can be found here: [http://kb.mozillazine.org/Command_line_arguments#For_Linux_and_Mac_OS_X_users](http://kb.mozillazine.org/Command_line_arguments#For_Linux_and_Mac_OS_X_users)

mv is used like

mv /home/mark/desktop/file /home/markdesktop/folder1file

the first one is where the file is, the second one is where the file wants to go.

---

### Post by bookinstall on 2007-04-16
Thanks for the mv command example, and for the link. I read and bookmarked it. 

Perhaps autorun is available from the BIOS? and not only for Windows?
I need to know how to make this happen in Linux.

The files on my CD in the root directory are:
-------------------------------------------
autorun.inf
Cover Picture.ico	CD Icon
setup.bat
ptstart.exe
\Bk2CDNFS\		Book Files Folder
-----------------------------------------

To have the CD to autorun (to install files) when it is inserted into the Drive,
the autorun.inf file must be located in the CD-ROM root.
----------------------------------------------
[Autorun]

open=ptstart.exe setup.bat

icon="Cover Picture.ico"

label= Freedom For Believers 

------------------------------------------------------

shell\verb0\command=ptstart.exe C:\BK2CDNFS\Frameset2.htm /max

shell\verb0=Open Freedom for believers Book (from C: Drive)



shell\verb1\command=ptstart.exe \BK2CDNFS\Frameset2.htm /max

shell\verb1=Open Freedom for believers Book (from CD only)



shell\verb2\command=ptstart.exe Setup.bat /max

shell\verb2=COPY Book FILES and ICONS
------------------------------------------------
Notice that the first autorun statement is open=ptstart.exe setup.bat  

The three shell verbs are needed after autorun completes, so that a CD right click will provide a drop down options list.

ptstart.exe does the same job that start.exe does in Windows.
This is neccessary because Windows start.exe will not work from the CD ROM drive.

When autorun begins, it opens the setup.batch file which is also in the CD root directory.

Until you intentionally change the directory, The install CD ROM is the directory,
You don't know the drive letter (E: in my system) because there may be more than one CD Drive.
 ------------------------------------------------
Rem  Setup.bat  I am adding comments 


color fc
REM Change cmd window screen colors to red text on white background 


REM	INSTALL BOOK FILES  (WinXP)  

REM     NO REGISTRY SETTINGS are changed!

REM     SCREEN COLORS

REM	Yellow =  Copy Files, 

REM	Green  =  Finished

REM	White  = CHANCE TO ABORT INSTALL 

REM     CLOSE THIS WINDOW TO ABORT

pause


color e0

REM Change cmd window screen colors to black text on yellow background 

REM When the cmd window opens, CD E: will be the directory shown ahead of the prompt. 

REM Notice that ptstart.exe is in the CD root. 
REM It must also be present in \Windows\system32\ for this batch file to work.

REM Use complete directory C: path to Xcopy, and copy ptstart.exe to Windows\sysstem32\

C:\Windows\System32\Xcopy.exe  ptstart.exe C:\Windows\system32\


REM Copy the CD book folder Bk2CDNFS, and all files and sub folders, to C:\BK2CDNFS\


C:\Windows\System32\Xcopy.exe \Bk2CDNFS\*.* C:\Bk2CDNFS\ /s



REM 	Copy Shortcuts to "All Users"\Programs


C:\Windows\System32\xcopy \Bk2CDNFS\"Freedom For believers"\*.* C:\"Documents And Settings"\"All Users"\"Start Menu"\Programs\"Freedom For Believers"\*.*



REM 	End of Copy Shortcuts


color a0

REM Change cmd window screen colors to black text on green background

REM     INSTALL COMPLETE, Strike any key to continue

REM 	Ready to read "Freedom For Believers" Book
pause

REM Open Frameset2, and clear cmd screen and exit cmd window.

ptstart.exe C:\Bk2CDNFS\Frameset2.htm /max

cls
----------------------------------------------

I want to have my shortcut to appear in the Applications drop down list.
For all users to be able to use.

I do not assume that Firefox will be the web browser, and when Windows starts my
Frameset2.htm,  it uses the default web browser to begin reading my book.

I don't really know all the steps to install my book on Linux when the CD is inserted.

I think I need to know how to start a terminal to do the work of my batch file.
Does Linux have a command language like Windows Dos?

---

