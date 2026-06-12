---
title: "Please help me in shell scripting"
date: 2009-08-09
forum: The Cafe
---

### Post by praveesh on 2009-08-09
I have created an add on cd(with the help of aptoncd ) for Ubuntu with some apps for my friend. I wish to create a bash script to be included in the cd, such that after the cd is added to the repository , my friend need to just double click on the shell script and click on run(not run in terminal). Please help me in this by providing the shell script. Is it possible to run a script without opening a terminal emulator?(ie without using cd /cdrom; ./script). Will a gksudo help?. Please provide me script preferably with gksudo . Please assume the packages to be installed be A,B,C,D . Thanks in advance.

---

### Post by praveesh on 2009-08-09
Two more doubts . 
1.Is there any command to add the cdrom to the repository
2. Is there any command to know the directory in which the shell script exists.

---

### Post by kevdog on 2009-08-09
You might want to take a look at zenity.

---

### Post by praveesh on 2009-08-09
> **kevdog said:**
> You might want to take a look at zenity.
what is zenity?please explain.

---

### Post by andru183 on 2009-08-09
ya i need how help starting out with bash if anyone knows somewhere to teach me?

---

### Post by &#32 Greg on 2009-08-09
> **praveesh said:**
> what is zenity?please explain.

Zenity is a dialog system for shell scripting.

What you'd have to do is write the script, then decide if it needs root access. If it needs root access, then when you make the desktop icon, you need gksu or something similar. You need to make sure that the script is chmod'ed to +x, of course. I'm pretty sure that you can run a pure shell script from out of a terminal from double clicking and it would just run, but it wouldn't show any output.

---

### Post by praveesh on 2009-08-09
> **andru183 said:**
> ya i need how help starting out with bash if anyone knows somewhere to teach me?
have a look at my signature. The linux documentation project([http://tldp.org](http://tldp.org)) May help you.

---

### Post by praveesh on 2009-08-09
> **  Greg said:**
> Zenity is a dialog system for shell scripting.
What you'd have to do is write the script, then decide if it needs root access. If it needs root access, then when you make the desktop icon, you need gksu or something similar. You need to make sure that the script is chmod'ed to +x, of course. I'm pretty sure that you can run a pure shell script from out of a terminal from double clicking and it would just run, but it wouldn't show any output.
thanks . But what I don't know is shell scripting . Sudo apt-get install A B C D didn't work(assume the packages to be installed be A,B,C  and D)

---

### Post by JohnFH on 2009-08-09
> **praveesh said:**
> thanks . But what I don't know is shell scripting . Sudo apt-get install A B C D didn't work(assume the packages to be installed be A,B,C  and D)

You need to add the CD to your software sources first.  Do this by going to System > Administration > Software Sources.  Select the 'Third Party Software' tab and click the 'Add CDROM...' button.  After adding the CD to your software sources you can then install your packages with sudo apt-get install A B C D as usual.

---

### Post by T-Train on 2009-08-09
I would suggest looking into creating your own CD.  This will allow you add a repository during the initial install.  The programs you want to add will be available at first boot.  You can automate the entire install to run without and prompts if you desire.  I created a CD not long ago and it wasn't very hard.  There are not a lot of examples around but once you understand the process it is simple.  Take a look at the instructions.  I would of course suggest testing you new image virtually with VirtualBox or VMware.

[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")

---

### Post by JohnFH on 2009-08-09
> **T-Train said:**
> I would suggest looking into creating your own CD.  This will allow you add a repository during the initial install.  The programs you want to add will be available at first boot.  You can automate the entire install to run without and prompts if you desire.  I created a CD not long ago and it wasn't very hard.  There are not a lot of examples around but once you understand the process it is simple.  Take a look at the instructions.  I would of course suggest testing you new image virtually with VirtualBox or VMware.

[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")

erm ... he has already created a repository CD using aptoncd.  Read the first post.

---

### Post by T-Train on 2009-08-09
Thanks for pointing out the obvious.  I was just suggesting a different option.

---

### Post by praveesh on 2009-08-09
> **T-Train said:**
> I would suggest looking into creating your own CD.  This will allow you add a repository during the initial install.  The programs you want to add will be available at first boot.  You can automate the entire install to run without and prompts if you desire.  I created a CD not long ago and it wasn't very hard.  There are not a lot of examples around but once you understand the process it is simple.  Take a look at the instructions.  I would of course suggest testing you new image virtually with VirtualBox or VMware.
[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")
thanks for the information. Iam planning to do that . But now , I don't have time . I have to give the cd immediately.

---

### Post by andru183 on 2009-08-10
> **praveesh said:**
> have a look at my signature. The linux documentation project([http://tldp.org](http://tldp.org)) May help you.

dude big help thanks!

---

### Post by Tibuda on 2009-08-10
> **praveesh said:**
> 2. Is there any command to know the directory in which the shell script exists.

```
dirname $0
```

---

### Post by phrostbyte on 2009-08-10
These forums have a programming section. It's probably better to ask there. :)

[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

