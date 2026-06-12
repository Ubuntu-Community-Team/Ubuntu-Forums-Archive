---
title: "BlueVue Device Manager on Ubuntu"
date: 2009-11-07
forum: Tutorials
---

### Post by lank23 on 2009-11-07
If you would like to make the BlueVue Device Manager from [http://www.bluetreewireless.com/](http://www.bluetreewireless.com/) run under Ubuntu take these steps.  I was told by tech support that it was a winDoz only program....ha ha ha...not with Java dude......Enjoy.

1: D/L the manager, here [http://www.bluetreewireless.com/cmsfiles/software/bvdm_1.7.9.exe]("http://www.bluetreewireless.com/cmsfiles/software/bvdm_1.7.9.exe")

2: Right click on the file and select open with Archive manager

3: Extract the " $[31] " folder to your home location folder rename to DManger.

4: Download [http://rxtx.qbang.org/pub/rxtx/rxtx-2.1-7-bins-r2.zip]("http://rxtx.qbang.org/pub/rxtx/rxtx-2.1-7-bins-r2.zip") and extract the the files to ~/DManager folder

5: Open "~/DManger/javax.comm.properties" file and comment out the last line, save the file.

5: Open ~/DManger/scripts/startupApplication.sh and change the 
```
export BVDMData=./data
```
to read
```
export BVDMData=~/DManager
``` and save the file

6: Copy the ~/DManager/scripts/startupApplication.sh to the ~/DManager/startupApplication.sh

7: open a term and do
```
 chmod 777 startupApplication.sh
```

8: Now it is time to run the program
```
./startupApplication.sh

```

9: Enjoy :D

---

### Post by stonem on 2011-11-16
Thanks, I found this post very helpful, but I would like to note some changes required for v. 1.7.10

Well, there is no startApplication.sh anymore, so I did this:

Adjustments:
1. bvdm_1.7.10.exe is downloadable from [http://www.sixnet.com/department/industrial-wireless-software-firmware-182.cfm](http://www.sixnet.com/department/industrial-wireless-software-firmware-182.cfm)
2. I extracted this .exe with 7zip, and found the files were in a folder called "$_OUTDIR".  The big clue is it's the one with all the .jar's
3. I ported/simplified the startupApplication.bat to the following:
```

#!/bin/bash

export BVDM_VERSION=1.7.10
export BVDMData=~/DManager

cd $BVDMData
java -cp "*" DMLauncher btConfigPath $BVDMData/cfg/ $@

```
and saved that as startupApplication.sh, made executeable etc.

Otherwise the rest of the instructions were spot on.


Thanks again lank, never would have gotten anywhere without your post.

---

### Post by lank23 on 2011-11-17
stonem

Glad it helped.

lank23

---

