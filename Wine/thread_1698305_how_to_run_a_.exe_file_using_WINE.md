---
title: "how to run a .exe file using WINE"
date: 2011-03-02
forum: Wine
---

### Post by jeshrel on 2011-03-02
Hi,

I just installed wine and tried running a .exe file from a drive and it says 
  "The file '/media/Common/Down/VTC UBUNTU/VTC.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

What should i do to run a .exe file in ubuntu. Kindly help

---

### Post by howefield on 2011-03-02
Right click on the exe file and select properties. Then check "Allow executing as program" in the Permissions tab.

---

### Post by jeshrel on 2011-03-02
yes i did do that, but as soon as i would check allow executable file it automatically gets unchecked. what should i do in that case

---

### Post by mookie60 on 2011-03-26
ditto.   since switching to 10.04 (xbuntu) i have not been able to install anything in wine, as i can not set the executable bit on the .exe file.   on my system (even when using sudo w/thunar file browser), the execute checkbox is nowhere to be seen.  i looked-up doing it via commandline with chmod +x, and it seems to accept the command without complaint, but still can't execute via wine.

i found some links that mentioned that this is the new security default, but little about how to set the bit.   i did see some comments about how "simple" it is to bypass this new requirement, but nothing that explained how to do it - at least nothing i could understand.

it has been many months now, and i haven't been able to install a single program in wine.   i find a program i'd like to try in wine, it fails to install, i search about setting the exec bit, nothing i do works, i give up.  time passes, and i find something else to try in wine - repeat the process.   

like many things linux (which i desperately want to like), i'm sure this REALLY IS simple.   i just can't find the "linux for dummys" type of explaination.   

any help with this is greatly appreciated.

---

### Post by cogadh on 2011-03-26
Sounds like you are trying to run an executable that is on some kind of removable media, like a CD or DVD. In those cases, you cannot change the executable permissions because the media is not writable. All you need to do to get around this is "wine" the executable via the terminal, rather than through the file browser.

---

### Post by mookie60 on 2011-03-26
i'm not attempting this with a disc.   This is a .exe downloaded via the web, located in my Downloads folder.

yes, that worked - thank you.   Now the pgm i'm trying to run (yawcam) says i need need java installed - hopefully getting that into wine won't be too painful.   . . . obviously a different subject.

since thunar still does not show the execute option box for the file, can i assume this (hiding the option) is also part of the new security to prevent unwanted execution of files?

thank you so much

---

### Post by cogadh on 2011-03-26
Hiding that option is not part of the current Ubuntu security philosophy (it is very much available in Ubuntu and Kubuntu), it's probably just a limitation of Xubuntu's file manager.

---

### Post by dpatel on 2011-03-27
Judging by this: [http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

...you need to install the Team PPA...

> The main frustration with the built in packages is the ominous warnings about the "executable bit" that make no goddamn sense to most people.

---

### Post by Morbius1 on 2011-03-27
Wine doesn't have the ability to determine if a particular *.exe has a Linux executable bit set. It's not wine that brings up the error it's Linux:
[http://ubuntuforums.org/showpost.php?p=10548141&postcount=8](http://ubuntuforums.org/showpost.php?p=10548141&postcount=8)

---

### Post by jeshrel on 2011-04-06
no it is not a cd or dvd, it is just a file in one of my drives..

---

