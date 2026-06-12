---
title: "Wine Installation/Run Issues"
date: 2009-12-26
forum: Wine
---

### Post by sleepysummer on 2009-12-26
Alright, I want to install and run Wine so I go to the official website, follow the first set of commands that says to go to software source etc and type in the command (used for KARMIC, which I just recently installed over Jaunty), it was added to the list in the window there and so I clicked close and some files were updated...

The next step listed is to run winecfg in the Run box, however the program is not found...

So me being a noob at this (now realising the mistake after reading the FAQ) I tried to run the uninstall through a sudo command and got this

me@SleepySummer:~$ sudo apt-get --purge wine
[sudo] password for me: 
E: Invalid operation wine
me@SleepySummer:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
me@SleepySummer:~$ 

I couldn't get the program working through the first steps so I referred to the FAQ and followed the instructions there to remove it manually, but the problem is this: .wine folder  is not there to delete x.x So thus I have RUN telling me its not there, the files are not there, Sudo says it's broken or something and Software Source window clearly says it is there.

Like I said, I'm a noob and need the almighty brains of you guys to direct me ^.^

---

### Post by beastrace91 on 2009-12-27
Try running the following: ```
sudo apt-get install wine1.2
```

~Jeff

---

