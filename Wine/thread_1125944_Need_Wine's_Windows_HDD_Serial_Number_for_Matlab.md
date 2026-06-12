---
title: "Need Wine's Windows HDD Serial Number for Matlab"
date: 2009-04-14
forum: Wine
---

### Post by mithbuntu on 2009-04-14
How can I find wine's emulated HDD's disk serial number?

I need this for the license.dat file for matlab.  It will not run without it.

```

HOSTID=DISK_SERIAL_NUM=2c989666


```

The serial num listed above doesn't work because that's my real windows installation's hdd's serial.

---

### Post by mithbuntu on 2009-04-14
Apparently, you can set wine's disk serial number by placing a file called ".windows-serial" with the serial inside it inside the drive_c dir. 

So, now Matlab runs, but... it doesn't really work:
```

Undefined function or variable 'ispc'.
Warning: MATLAB did not appear to successfully set the search path. To avoid
this
warning the next time you start MATLAB, use
http://www.mathworks.com/access/helpdesk/help/techdoc/ref/pathdef.shtml
to help troubleshoot the "pathdef.m" file. To recover for this session
of MATLAB, type "restoredefaultpath;matlabrc".
Warning: Duplicate directory name: C:\Program Files\MATLAB\toolbox\local.
Warning: Initializing Handle Graphics failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:UndefinedFunction
Undefined function or method 'colordef' for input arguments of type 'double'.
> In matlabrc at 104
Warning: Initializing Java preferences failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:UndefinedFunction
Undefined function or method 'usejava' for input arguments of type 'char'.
> In matlabrc at 129
??? Undefined function or variable 'ispc'.

Error in ==> reporterrorlogs>isComputeServer at 337
if ispc

Error in ==> reporterrorlogs at 14
if isdeployed || ~isInteractive || isComputeServer  || ~isJavaAvailable || ~getCheckForLogFiles

Error in ==> matlabrc at 265
reporterrorlogs

>> ls
??? Undefined function or variable 'ls'.

>> x = [1, 2, 3]

x =

     1     2     3

>> plot(x)
??? Error using ==> plot
Unable to find the proper "@graph2d" directory.

>> plot(x)
??? Error using ==> plot
Unable to find the proper "@graph2d" directory.

>> x^2
??? Error using ==> mpower
Matrix must be square.

>> x^2
??? Error using ==> mpower
Matrix must be square.

>> x = [1, 2, 3];
>> x = 1;
??? Undefined function or method 'workspacefunc' for input arguments of type 'cell'.

```

Meh..

---

### Post by asdfoo on 2009-04-14
> **mithbuntu said:**
> Apparently, you can set wine's disk serial number by placing a file called ".windows-serial" with the serial inside it inside the drive_c dir. 

So, now Matlab runs, but... it doesn't really work:
```

Undefined function or variable 'ispc'.
Warning: MATLAB did not appear to successfully set the search path. To avoid
this
warning the next time you start MATLAB, use
http://www.mathworks.com/access/helpdesk/help/techdoc/ref/pathdef.shtml
to help troubleshoot the "pathdef.m" file. To recover for this session
of MATLAB, type "restoredefaultpath;matlabrc".
Warning: Duplicate directory name: C:\Program Files\MATLAB\toolbox\local.
Warning: Initializing Handle Graphics failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:UndefinedFunction
Undefined function or method 'colordef' for input arguments of type 'double'.
> In matlabrc at 104
Warning: Initializing Java preferences failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:UndefinedFunction
Undefined function or method 'usejava' for input arguments of type 'char'.
> In matlabrc at 129
??? Undefined function or variable 'ispc'.

Error in ==> reporterrorlogs>isComputeServer at 337
if ispc

Error in ==> reporterrorlogs at 14
if isdeployed || ~isInteractive || isComputeServer  || ~isJavaAvailable || ~getCheckForLogFiles

Error in ==> matlabrc at 265
reporterrorlogs

>> ls
??? Undefined function or variable 'ls'.

>> x = [1, 2, 3]

x =

     1     2     3

>> plot(x)
??? Error using ==> plot
Unable to find the proper "@graph2d" directory.

>> plot(x)
??? Error using ==> plot
Unable to find the proper "@graph2d" directory.

>> x^2
??? Error using ==> mpower
Matrix must be square.

>> x^2
??? Error using ==> mpower
Matrix must be square.

>> x = [1, 2, 3];
>> x = 1;
??? Undefined function or method 'workspacefunc' for input arguments of type 'cell'.

```

Meh..

did you install matlab in Wine?

---

### Post by mithbuntu on 2009-04-15
Yes, I did, but it seems to keep crashing at 97% install and I don't know why...

Matlab 2007b
Latest Wine (x.x.19)

---

### Post by asdfoo on 2009-04-15
> **mithbuntu said:**
> Yes, I did, but it seems to keep crashing at 97% install and I don't know why...

Matlab 2007b
Latest Wine (x.x.19)

Well, that's probably why it doesn't work! Not installed properly.

You should submit a bug report at [http://bugs.winehq.org](http://bugs.winehq.org) - I also recommend testing an earlier version of Wine to see if it used to work, then you can run a Regression Test to provide the information to developers to fix the issue.

[http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting)

---

### Post by GoingDown on 2009-04-16
There seems to be native Linux version of Matlab available:

[http://www.mathworks.com/products/matlab/requirements.html]("http://www.mathworks.com/products/matlab/requirements.html")

Why not to use it?

---

### Post by mahasmb on 2009-05-25
Thanks a lot!

Copying my Windows HDD Serial# to that .wine-serial file fixed my problem! (I was getting a "License Manager Error -9" that wouldn't let me run MATLAB)

BTW. The way I did it was that I installed MATLAB in Windows XP. And then I just copied the MATLAB folder to .wine/drive_c/Program Files/ in Ubuntu.

I followed the instructions here: [http://appdb.winehq.org/appview.php?iVersionId=5385&iTestingId=5290](http://appdb.winehq.org/appview.php?iVersionId=5385&iTestingId=5290)

Now MATLAB runs fine!

---

