---
title: "difficulty accessing a file in ubuntu"
date: 2016-10-11
forum: Virtualisation
---

### Post by cbiodun on 2016-10-11
Hi All,

I'm using a software that needs to access some files to run. The software is having difficulty reading a file. Wondering what the best command is to give permission to a directory or all files in a directory in order to have my software access files to run successfully. I'm using a virtual machine in windows and I understand there may be issues with file/folder ownership. I've tried chmod/chown but with no luck.

---

### Post by nothingspecial on 2016-10-11
> **cbiodun said:**
> Hi All,

I'm using a software that needs to access some files to run. The software is having difficulty reading a file. Wondering what the best command is to give permission to a directory or all files in a directory in order to have my software access files to run successfully. I'm using a virtual machine in windows and I understand there may be issues with file/folder ownership. I've tried chmod/chown but with no luck.

Hi :)

You need to give some more information about what you are trying to do, what the files are, what software you are trying to run and which virtualisation you are using. Also, what you have tried so far and any errors you got.

---

### Post by cbiodun on 2016-10-11
thanks. im trying to use a remote sensing/satellite image processing software which needs to do some complex modelling by accessing some files that have been stored in a drive during installation. the file is in a sub directory.
i am using oracle VM virtual box as I ran out of space on my linux OS and i fear messing things up in attempting to increase partition space. 

as an ubuntu newbie, I've tried using chmod -R 777/chown 777 chmod to give permission to read files/folders.
this is the error I got if that will be useful:
-E- /home/swdev/ocssw/build/src/l2gen/aerosol.c: Error reading SDS acost from /home/chris/seadas-7.3.2/ocssw/run/data/oli/aerosol/aerosol_oli_r50f01v01.hdf.

'aerosol_oli_r50f01v01.hdf' is the file.
[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR]

---

### Post by howefield on 2016-10-12
Thread moved to the "*Virtualisation*" forum.

Are you running the application from the host and trying to access the file residing on a Virtual Machine ? I'm not sure it is clear what you are trying to do.

---

