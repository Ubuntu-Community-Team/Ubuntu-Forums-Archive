---
title: "Path to data files using wine from a launcher"
date: 2011-03-15
forum: Wine
---

### Post by uaebuntu on 2011-03-15
Ubuntu 10.04 Kernal 2.6.32-29-generic Wine 1.2.2
Wineconfig Windows XP, Applcations Default settings ALSA Driver applied

Many years ago I got a copy of the Oxford Resource Shelf as a free offer from "The Guardian" a UK newspaper. This has been invaluable and one of the few things I keep my copy of XP on a VM for.

Thought I would try wine and junk that VM altogether, trouble is I don't have the installation CD anymore. I installed wine from the Synaptic package manager and copied the windows directory ORS to my /home/jim/ directory.

I can run it from the CLI and great joy has broken out. I now want to create a launcher, but following the instructions in the Ubuntu Wine Community documentation either nothing happens or when specifying the full path I get a pop up saying "no book files available"

I've attached a screen shot of the contents of /home/jim/ORS/ and they are there, the application is working but cannot find the path to data from the launcher. Can anyone help me here please?

---

### Post by ChipOManiac on 2011-03-15
Try moving the data ORS folder into ~/.wine/drive_c/Program Files/ and then running from there. The "no book files available" might be because it's looking for the path according to the way it was installed (which should be in the Program Files or in the C drive)

Hope this works

---

### Post by uaebuntu on 2011-03-15
Thanks.

There are a couple of things I need to clarify

I didn't install the program I copied it and the directory from a working windows XP SP3 installation, I do not have the install disk any longer.

It runs 100% from the CLI as shown on the terminal screenshot .png and finds the bookfiles.

What I can't do is set up the launcher. I tried putting the ORS directory under Program Files and running

sh -c cd /home/jim/.wine/drive_c/Program Files/ORS/; wine /home/jim/.wine/drive_c/Program Files/ORS/ORS.EXE

in the launcher and that didn't work.

I tried 

wine "C:\Program Files\ORS\ORS.EXE" from a terminal and that didn't work either

Still would like help in getting this to run from a launcher/menu

---

### Post by ChipOManiac on 2011-03-15
Okay, I think it's the launcher... try it as a shell script, I don't think launchers are capable of that type of work (but I'm prepared to be wrong :) )...

```

#/bin/bash

cd /home/jim/.wine/drive_c/Program Files/ORS/
wine ORS.exe

```

Save it somewhere under ORSRunner.sh (or someting but keep the .sh), right click on this file and in permissions check the box saying "Allow to run as program" or something.

Then in the launcher
```

gnome-terminal -e **Path To The Script**

```

And finish off

Hope it works...

---

### Post by uaebuntu on 2011-03-17
Thanks.

Tried the script as you said but if failed to run the cd command because it could not deal with the space between Program and Files.

I manually input the path with the same problem though the /Program Files/ directory was there.

Tried again using Tab to autofill the path and it inserted an extra backslash character.

This worked and ORS ran successfully. See screenshot.

Put the backslash in the path in the script, works perfectly. Put the script in the launcher and it also works.

---

### Post by uaebuntu on 2011-03-17
Forgot the screen shot:(

---

### Post by ChipOManiac on 2011-03-17
> **uaebuntu said:**
> Thanks.

Tried the script as you said but if failed to run the cd command because it could not deal with the space between Program and Files.

I manually input the path with the same problem though the /Program Files/ directory was there.


Forgot That :( You fould use "" and put the path in between

> **uaebuntu said:**
> 
Tried again using Tab to autofill the path and it inserted an extra backslash character.

This worked and ORS ran successfully. See screenshot.

Put the backslash in the path in the script, works perfectly. Put the script in the launcher and it also works.

=D> Attaboy!

---

