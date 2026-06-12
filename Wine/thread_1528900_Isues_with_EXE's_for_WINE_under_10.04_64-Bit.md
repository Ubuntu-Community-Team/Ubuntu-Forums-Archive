---
title: "Isues with EXE's for WINE under 10.04 64-Bit"
date: 2010-07-11
forum: Wine
---

### Post by TonyFordz on 2010-07-11
Hello,

I have never had this problem with past versions of Ubuntu but now that I have upgraded to 10.04 I am unable to install anything under WINE with an EXE extension. How the hell do I disable Ubuntu from safe guarding against exe files, or better yet how do I add the exe files I want to be trusted to what ever it is that is blocking them?

[IMG]http://i31.tinypic.com/2dtui5v.jpg[/IMG]

The above image shows the error I get with each EXE I try to install with WINE, and I know how to install them.

Can someone help before I get really upset & go back to windows... I really want to use Linux but so many problems, errors, and other things that I never have problems with under windows. Linux is safer, faster, and more reliable but its to much of a headache having to fix & try to make things work with it.

---

### Post by howefield on 2010-07-11
Try right clicking the exe file and select properties, click the permissions tab and check the "Allow executing file as program".

Then close your way back out, right click on the file and select Open with Wine Windows Loader (or whatever it is - can't quite remember the exact wording)

---

### Post by Dr_Willis on 2010-07-11
you basically set the file (the .exe) to be 'executable' and this warning goes away. Ive no idea why its really set up this way. Unless its to safeguard against accidently running malware.

Right click on the .exe, Properties menu -> Permissions tab - set it to be 'executable'

One VERY annoying issue with this 'feature' is that you want to run a exe from a optical drive, you cant set the executable bit.

You must use the terminal to run them in this case. ie:

```
wine /media/cdrom/gameinstaller.exe
```

I notice you are installing paint.NET, I do recall seeing mention of a port of that to linux (or a clone or somthing)  

Have fun.

Here we go...

Paint.NET for MONO. avail in .deb packages.



[http://www.webupd8.org/2009/09/paintnet-for-linux-paintmono.html](http://www.webupd8.org/2009/09/paintnet-for-linux-paintmono.html)

---

### Post by TonyFordz on 2010-07-11
Thanks everyone the 1st 2 posts solved my problem.

Thank you very much!

[IMG]http://i30.tinypic.com/335cuh1.jpg[/IMG]

---

### Post by elliotn on 2010-07-11
Mark the thread solved please

---

### Post by TonyFordz on 2010-07-11
How do I mark it solved I tried to edit my main one & there was no option & I don't see one here either...

Not trying to be noooooob, but where is the option?

---

### Post by howefield on 2010-07-11
Try "Thread Tools"

---

### Post by Iowan on 2010-07-11
Moved to Wine.

---

