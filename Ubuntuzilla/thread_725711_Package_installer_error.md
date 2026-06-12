---
title: "Package installer error"
date: 2008-03-15
forum: Ubuntuzilla
---

### Post by mikeric on 2008-03-15
everytime i try to install ubuntuzilla i get Error: Dependency is not satisfiable: libstdc++5. Any help would be greatly appreciated. Im new to linux and ubuntu and just trying to get thunderbird working.

---

### Post by Bubba64 on 2008-03-16
Post your Distribution personally I had never heard of ubuntuzilla It is not even in my synaptic section you may not need it. You can get Thunderbird in synaptic.

---

### Post by mikeric on 2008-03-16
I was trying to install thunderbird and couldnt get it to work and found stuff on the forum for ubuntuzilla and followed the instructions. I have ubuntu 7.10. im new to it, just got it the other day.

---

### Post by Bubba64 on 2008-03-16
You can install it in the terminal just type sudo apt-get install thunderbird
You might want to make sure that you have opened all the repositories in system administration software sources first you can open all except most advise against source code. I have never had a bad update, but others have so anybody else wanting to chime in on any of this please do so. if you haven't opened the repositories yet you will probably get some backport and security updates so install all before you try for Thunderbird, good luck.

---

### Post by mikeric on 2008-03-16
Thanks for the quick reply, i tried that and this is what i got
> Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate

---

### Post by Bubba64 on 2008-03-16
Sorry try add remove in applications click all available in right top corner then type Thunderbird in search click install and hopefully this will do it. I t has been a while since I installed this program I forget how I did it. Also have you opened the other repositories.

---

### Post by mikeric on 2008-03-16
thanks for the help, i have thunderbird extensions in there but not the program.

---

### Post by Bubba64 on 2008-03-16
Here is a link that might help.
[https://help.ubuntu.com/community/Medibuntu?action=fullsearch&context=180&value=thunderbird&titlesearch=Titles](https://help.ubuntu.com/community/Medibuntu?action=fullsearch&context=180&value=thunderbird&titlesearch=Titles)
Save he page it has a search engine for links to answers to most of the questions you will have about your distribution like media stuff etc.

---

### Post by mikeric on 2008-03-16
I tried what that said and got the same thing i quoted in here earlier on.

---

### Post by Bubba64 on 2008-03-16
Since I am of no help here I know there are others on this forum who can instruct our new friend here, I hope one or more of you will help. Sorry I can't be of more help the key here I think is opening the repositories I am not sure if the Thunderbird program comes from the main repositories. I don't know if while trying to install this  originally that you might have removed Thunderbird from add remove, if you have chosen all available applications in add remove the program should be there as far as I know which isn't very far, and all the repositories are opened.

---

### Post by mikeric on 2008-03-16
what do i have to do to have all the repositories opened?

---

### Post by Theo148 on 2008-03-16
Well I'm not sure about that, but to get the libstdc++5 package and get Ubuntuzilla running properly, you could try

```
sudo apt-get install libstdc++5
```

That should install libstdc++5 and allow Ubuntuzilla to install.

---

### Post by mikeric on 2008-03-16
when i tried to install that i got this too. 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5


---

### Post by nanotube on 2008-03-16
hi,
refer to this thread, maybe it will be of help:
[http://ubuntuforums.org/showthread.php?t=713005](http://ubuntuforums.org/showthread.php?t=713005)

post your output of ```
apt-cache search libstdc
```

---

### Post by mikeric on 2008-03-16
Thats all i got
> libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6 - The GNU Standard C++ Library v3

---

### Post by Bubba64 on 2008-03-16
> **mikeric said:**
> what do i have to do to have all the repositories opened?

Here is a link to your question, if you ever decide to update your distribution through update manager having everything up to date with these repositories will save you the frustration you have experienced in trying to install Thunderbird. The repositories are not like Microsoft downloads or monitors to see if you have permission to have a program, but are a library of releases of the newest version of security updates and program updates. Good luck 
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by mikeric on 2008-03-17
thanks for the help, i didnt have the repositories enabled. everything is working fine now.

---

### Post by nanotube on 2008-03-17
> **mikeric said:**
> thanks for the help, i didnt have the repositories enabled. everything is working fine now.

cool. :)

---

