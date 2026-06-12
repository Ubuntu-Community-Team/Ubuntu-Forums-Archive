---
title: "HOWTO: (Successfully) Make &amp; Run a Py2Exe Executable!"
date: 2010-07-16
forum: The Cafe
---

### Post by Sailor5 on 2010-07-16
Ahoy Sailors!

[IMG]http://a.imagehost.org/0446/error-small.jpg[/IMG] 

[COLOR=red]This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem.[/COLOR] Error is explained 

[COLOR=Red][SIZE=6]Python Versions
[SIZE=1] [COLOR=Black]So before we even being to compile or edit anything, We need to start with which version of Python we are using, Generally older releases will build smaller executables, This is due to the main Python dll being smaller, As so is the msvcr*.dll. To give you an example here is the journey of my small Windowless Twisted networking application.

Ver ----------      File size (Everything compressed together)

2.6 ----- -----               1.8MB
2.4               [/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][SIZE=6][SIZE=1][COLOR=Black]----- ----- [/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][SIZE=6][SIZE=1][COLOR=Black]1.4MB
2.3               [/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][SIZE=6][SIZE=1][COLOR=Black]----- -----[/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][SIZE=6][SIZE=1][COLOR=Black] 800KB   [/COLOR][/SIZE] 
[/SIZE][/COLOR] 
So as we can see there is a pretty steep decline in size going from version to version, For a little extra Py2.3 uses msvcrt.dll which is on almost all Windows os's by default & therefore no longer needs to be packaged.

Now your script may need some things that are in the newer releases of Python, So you may not be able to go back that far (For me the Twisted engine stopped at 2.3), However if size is a problem then using an older version is definitely a KB saver. 

[SIZE=5][SIZE=6][COLOR=Red]Compiling Package?
[COLOR=Black][SIZE=1]So lets get the basics out the way. First create a Python script name it compile.py and paste this[/SIZE][/COLOR][/COLOR][/SIZE][/SIZE]```
from distutils.core import setup
import py2exe
 
setup(console=['hello.py'])
```Replace the above hello.py with that of the name of your Python script. Then we can run this file from CMD (Or make a nice batch file) By using```
C:\python26\python compile.py py2exe
```Py2Exe now makes two folders in that of the dir which your Compile.py script resides in, One folder named dist, And the other build (Don't need to bother with that one) Inside of dist you will find your .exe file, Which is almost ready to be shipped over the internet!

[COLOR=Red][SIZE=6]'This application has failed...' Error!
[COLOR=Black][SIZE=1]Now there has been a few topics made about this on various websites, To clear everything up, If your using Python26 make sure you have these two files in amongst your dist folder. MSVCR90.dll & Microsoft.VC90.CRT.manifest (Not sure if name varies) They both reside in your Python's installation directory. Copy them both and your package is ready to go!

[SIZE=6][COLOR=Red]File size!
[COLOR=Black][SIZE=1]I also was a tad concerned about the file size when I first compiled my python script. We can compress all the files inside of a self extracting archive, But were better of as well trimming some un-needed modules.

You should have a zip archive called library.zip (use winrar or 7zip to compress the content again as it's not at maximum compression level) inside of which lays your modules which will be travailing around with your .exe, However modules that aren't needed also get packaged, So either by knowledge or trial & error, Delete some of those modules & see if your executable works. & with that you can trim your package size. 

And with that you've got your working tiny-fied Python based PE executable ready to go! You may now comment and applaud.
[/SIZE][/COLOR][/COLOR][/SIZE][/SIZE][/COLOR][/SIZE][/COLOR]

---

