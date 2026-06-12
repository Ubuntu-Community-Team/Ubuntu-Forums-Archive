---
title: "Truecrypt installation"
date: 2010-02-18
forum: Security
---

### Post by PalapaGuy on 2010-02-18
This is a real noob question.  

I downloaded truecrypt Linux version, giving me a file named truecrypt-6.3a-ubuntu-x86.tar.gz.  I assume that's the archive.

Double clicking on that produced file truecrypt-6.3a-setup-ubuntu-x86.  I assume that's the executable.

When I try to run that, I get a "could not display ... unknown filetype" error.  

Could someone tell me what I'm doing wrong?  I plan to run truecrypt under the easycrypt GUI.

---

### Post by mkvnmtr on 2010-02-18
I have build -essential and gdebi installed on my system. When I right click on the truecrypt package it offers the option to open with the package installer which is gdebi. I do not remember if that was part of the default install or I had to install it myself.

---

### Post by 2hot6ft2 on 2010-02-18
Removed this part

Hmm, guess not. Ok what I did was without extracting it put it in your home folder and in a terminal
Applications > Accessories > Terminal
 run
```
sudo apt-get install alien
```
when that finishes run
```
sudo alien truecrypt-6.3a-ubuntu-x86.tar.gz
```
That will create the deb file for you to double click on to install it.

---

### Post by 2hot6ft2 on 2010-02-18
After you install it you can find it under
Applications > Accessories > TrueCrypt

---

### Post by PalapaGuy on 2010-02-18
Downloaded alien fine but terminal isn't finding the truecrypt file on my desktop.  Tried your exact command and also tried including the path /home/george/desktop ........  Any suggestions?

---

### Post by 2hot6ft2 on 2010-02-18
> **PalapaGuy said:**
> Downloaded alien fine but terminal isn't finding the truecrypt file on my desktop.  Tried your exact command and also tried including the path /home/george/desktop ........  Any suggestions?
I corrected it. I forgot that Terminal starts in your home folder not the desktop so just move it (truecrypt-6.3a-ubuntu-x86.tar.gz) to your home folder and try again.

Sorry about that I use nautilus open terminal in whatever folder I'm in at the time so much I forgot.

---

### Post by adam814 on 2010-02-18
I didn't need alien for it.  I extracted the executable, navigated to the folder in the terminal and ran it.  I had two options for install (automatic install or generate .deb).  I chose to generate a .deb and install it myself.

---

### Post by PalapaGuy on 2010-02-18
OK, but I get an error message when I try to move the file out of the downloads folder.  sheeesh ... !

---

### Post by FuturePilot on 2010-02-18
Make sure you selected the .deb option when you downloaded it. Right click the tar.gz and select Extract Here. Double click the file that was extracted and select Run. Select Install Truecrypt. Accept the license and Gdebi will open. Then just click the Install button.

---

### Post by PalapaGuy on 2010-02-18
My bad.  Forgot to capitalize "Download."  Terminal says it created the .deb file. so once I find it ....

Thanks much.

---

### Post by 2hot6ft2 on 2010-02-18
Glad you got it going. I think I did it the way adam814 says back when I installed it but there's more that 1 way to get it done and you may find alien useful later on.

You may find this useful later too.
If you want a right click option to open a terminal in whatever folder you're currently in use this
```
sudo apt-get install nautilus-open-terminal
```
then to stop nautilus (don't worry it just closes any open folders)
```
killall nautilus
```
then when you open another folder "Open In Terminal" will be one of the options when you right click. Sure a time saver.

---

### Post by PalapaGuy on 2010-02-18
Thanks guys.  It's all good.  Up and running.

---

### Post by 2hot6ft2 on 2010-02-18
You're welcome. You can mark the thread as solved using the Thread Tools at the top. Enjoy

---

