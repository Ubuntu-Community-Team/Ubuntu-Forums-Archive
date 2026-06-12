---
title: "Lprof 1.11"
date: 2006-01-19
forum: Requests
---

### Post by jasplund on 2006-01-19
Breezy-backports has lprof 1.10 but dapper has 1.11

[http://lprof.sourceforge.net/](http://lprof.sourceforge.net/)

Significant changes in this version include: 
 
1.A unified user interface with a greatly simplified work flow. 
2.The user interface and logic for placing the IT8.7 picker template has been hugely improved and will now work for skewed chart images that would have been impossible to use with the old picker template positioning user interface. The user interface is also much simpler to use. 
3.A new help system has been implemented and new documentation written for the help system. This includes information on how to use this version of LPROF and there is also has a section on how to create profiles for use with UFRAW. 
4.The charts for setting monitor gamma in the rough monitor profiler are now the Norman Koren gamma charts. These are being used with the permission of Norman Koren. These new charts will also help users set the black point for their monitors. See [http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html) for more information about these charts.  
5.LPROF now uses standard locations for saving and locating profiles by default. On Linux/Unix systems profiles will be saved to $HOME/.color/icc and when looking for profiles it will look in /usr/share/color/icc. On Windows systems it will use the default Windows directory for ICC profiles (normally c:\Windows\system32\spool\drivers\color). Users can specify other locations and LPROF will save this information to it's configuration directory and use those user specified directories. 
6.LPROF configuration and temporary files are now stored in $HOME/.lprof. 
7.On Linux systems SCons is now used as the build system. The SCons build is not currently working on Windows or other platforms. 
8.The library used to support tiff IT8.7 target images has been changed from QTiffIO to TiffIO for increased portability (QTiffIO does not work on Windows). LPROF can be built and will run without this library installed but it will not support the use of tiff files unless this library is installed. 
9.A new target reference file installer has been added. This installs target reference files in a standard location and also requires the user to select the correct picker template when installing a new target reference file. LPROF will automatically use the specified picker template when ever the user selects a target reference file in the Camera and Scanner Profiler tab. 
10.A significant amount of work has been done on Windows portability issues and most of the features are working on Windows systems. 
11.Some work has been done to insure that this will run on big-endian systems. This code still needs to be tested. (The development team only has access to little-endian hardware). 
12.A bunch of other bug fixes and improvements.

---

### Post by jasplund on 2006-01-28
?

---

