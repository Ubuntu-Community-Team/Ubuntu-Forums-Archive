---
title: "using wine"
date: 2007-02-23
forum: Ubuntu Christian Edition
---

### Post by jhmac77 on 2007-02-23
I followed these instructions and I guess I did'nt download Filezilla.  How do you do that?  I have it on Windows XP.  I never figured out how to use z:\home\username\.wine\drive_c\Program Files\Filezilla.  

Using Wine
A bit about Wine... I don't know how it works, but it does seem to work with a lot of simple Windows programs. I'll show you how I get Filezilla to work in Linux, as an example. 

I download the setup.exe file for Filezilla. When I double-click on it, Wine will try to open the file. Then, the installer appears, just as if I were using Windows. Instead of installing Filezilla to 

C:\Program Files\Filezilla\
, I'm going to override the default installation location and install it to 
z:\home\username\.wine\drive_c\Program Files\Filezilla
. For some reason, 
z:\
is what Wine calls my Ubuntu partition. 

from [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by shane2peru on 2007-02-24
Ok, click on this link:

[http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149&release_id=475423](http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149&release_id=475423)

Now go down to the Filezilla_2_2_30a_setup.exe and click on that.  That should download it to your computer.  You can save it to your desktop or your home folder.  Once it is done, you will need to double click that file and wine should open it and follow the instructions.  It will automatically put an icon on the desktop.

Shane

---

