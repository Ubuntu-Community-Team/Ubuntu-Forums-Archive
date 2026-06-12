---
title: "How do you point your python path to the newest version?"
date: 2006-11-19
forum: Windows
---

### Post by user1397 on 2006-11-19
my windows came with python ver. 2.2.1, but i recently installed python ver. 2.5, which lies in ```
C:\python25\python
```if i go to the command prompt, and i type "python", i am in the 2.2.1 version.  i want it to instead say version 2.5

i tried the instructions here: [http://docs.python.org/tut/node4.html](http://docs.python.org/tut/node4.html) where it says to type this: ```
set path=%path%;C:\python25
```, but it doesn't work for me, or else i just don't know how to set up that command's parameters.

does anyone know?

---

### Post by DaveBorealis on 2006-11-19
> **erik1397 said:**
> ```
C:\python25\python
```

Hello, the above is a Windows path. (?)

If you have something like ```
/usr/bin/python2.4
``` then either link /usr/bin/python to '/usr/bin/python2.5' OR add 'alias python='/usr/bin/python2.5' to '.bashrc' in your home directory, assuming that you're running python from the command line.

Best regards,
Dave

[oops!]  I just noticed the discussion forum is Windows.  Please ignore the above!

---

### Post by user1397 on 2006-11-19
> **DaveBorealis said:**
> [oops!]  I just noticed the discussion forum is Windows.  Please ignore the above!will do! :)

---

### Post by izalac on 2006-11-20
> **erik1397 said:**
> my windows came with python ver. 2.2.1, but i recently installed python ver. 2.5, which lies in ```
C:\python25\python
```if i go to the command prompt, and i type "python", i am in the 2.2.1 version.  i want it to instead say version 2.5

i tried the instructions here: [http://docs.python.org/tut/node4.html](http://docs.python.org/tut/node4.html) where it says to type this: ```
set path=%path%;C:\python25
```, but it doesn't work for me, or else i just don't know how to set up that command's parameters.

does anyone know?

That would have worked in DOS :P
In Windows XP, right click on My Computer, select Properties, click on Advanced tab, and then click on Environment Variables. Find path in the lower list (system variables), click Edit, and add your C:\python25 there. Be sure to watch out for other python directories, if you have any, replace that entry with yours. All entries are seperated by semicolon.

That's the official way of doing it.
The lazy way of doing it is just to create a file "python.bat" in your Windows directory, and type/paste the following code in it:
```
@C:\python25\python %1 %2 %3 %4 %5 %6 %7 %8 %9
```

---

### Post by user1397 on 2006-11-20
> **izalac said:**
> That would have worked in DOS :P
In Windows XP, right click on My Computer, select Properties, click on Advanced tab, and then click on Environment Variables. Find path in the lower list (system variables), click Edit, and add your C:\python25 there. Be sure to watch out for other python directories, if you have any, replace that entry with yours. All entries are seperated by semicolon.

That's the official way of doing it.
The lazy way of doing it is just to create a file "python.bat" in your Windows directory, and type/paste the following code in it:
```
@C:\python25\python %1 %2 %3 %4 %5 %6 %7 %8 %9
```thanks man! your instructions worked flawlessly, i didn't even know that existed in system properties.

---

### Post by izalac on 2006-11-20
> **erik1397 said:**
> thanks man! your instructions worked flawlessly, i didn't even know that existed in system properties.

In previous versions of DOS/non-NT windows it was contained in autoexec.bat, and could be modified using the set command.

Good thing that WinXP made stuff more simple :twisted:

---

