---
title: "Find drive letter with batch script."
date: 2008-11-20
forum: Windows
---

### Post by lakotajames on 2008-11-20
How can I make a program/script that will edit a text file on another drive to include the drive letter of the directory the program/script was launched from?  I need to run it from a DVD.  it should move a couple files to the a folder on the hard drive and edit the text file that was moved to include the path to the DVD. then launch the program.  after the program ends, I need it to erase the files it moved onto the hard drive.  I could do this myself with a batch file, but I don't know how to find the drive letter it is run from.  Actually, it wouldn't have to be a batch file, I just thought that it would be the easiest way to do it.

---

### Post by mocoloco on 2008-11-21
[http://www.robvanderwoude.com/batchhowto.html]("http://www.robvanderwoude.com/batchhowto.html")

```
@echo off
:: Grab the drive letter this file exists on
set SRCDRV=%~dp0
:: Copy some stuff from source drive to user's temp folder
copy %SRCDRV%data\thing.exe %TEMP%.
:: --Do more useful stuff. --
:end

```

I used to be a bit of a batch hacker back in the day.  Rob's got lots of very cool tricks on that site.  Like the smart usage of the %temp% variable, which it sounds like you may want to use.
[http://www.robvanderwoude.com/tempfiles.html]("http://www.robvanderwoude.com/tempfiles.html")

---

### Post by lakotajames on 2008-11-21
thanks, you helped me a lot.

---

### Post by lakotajames on 2008-12-03
hmmm... i almost have it working.  this is what i have so far: 

```

C:
MD %TEMP%\Odyssey
COPY %~dp0\Files\acwin.exe %TEMP%\Odyssey
%~dp0\Files\config.bat > %TEMP%\Odyssey\acsetup.cfg
cd %TEMP%\Odyssey
START "" acwin.exe

```
the only thing that doesn't work is the ```
START "" acwin.exe
```line.  Any ideas?

---

### Post by skillllllz on 2008-12-03
Try this:

```
@ECHO OFF
MD %TEMP%\Odyssey
SET FOLDER=%TEMP%\Odyssey
COPY %~dp0\Files\acwin.exe %FOLDER%
%~dp0\Files\config.bat > %FOLDER%\acsetup.cfg
START "%FOLDER%\acwin.exe"
```

---

### Post by lakotajames on 2008-12-03
Nope.  Still doesn't work.  The files are still copied and written correctly, but it still will not launch acwin.exe.

---

### Post by skillllllz on 2008-12-03
Then try removing the quotes from the last line I provided.

---

### Post by lakotajames on 2008-12-03
nope, that doesn't work either.
I figured out that the problem is in this line:
```
%~dp0\Files\config.bat > %FOLDER%\acsetup.cfg

```
acsetup.cfg is exactly the way it is supposed to be, but everything after that line no other commands (for example, ECHO SUCCESS) will do anything.  the problem is that acwin.exe needs acsetup.cfg to run, so i need that line to be before the start line.

---

### Post by mocoloco on 2008-12-05
Not sure why you're redirecting from a batch file to the .cfg file, usually doesn't work that way.  Can you list what's in config.bat?

---

