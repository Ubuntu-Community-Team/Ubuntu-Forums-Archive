---
title: "Unable to install program."
date: 2011-05-16
forum: Wine
---

### Post by DigitalAlcatraz on 2011-05-16
I am trying to install a program(FL Studio 10) on wine and am getting this message: 
"Cannot load get.mfx. This object might need an external program or library not yet installed"
I am getting no results in Synaptic package Manager or Ubuntu Software Center. :-|

---

### Post by gsmanners on 2011-05-16
[FL Studio 10]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23334") should work fine, but you probably need a newer version of Wine to run it.

[wine1.3]("apt://wine1.3")

see [http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

---

### Post by DigitalAlcatraz on 2011-05-17
Still Getting the same message.

---

### Post by ambar686413 on 2011-05-17
at first update the software packages... by ```
sudo apt-get update
```...then again install wine 1.3... hope it will work fine...@ DigitalAlcatraz

---

### Post by DigitalAlcatraz on 2011-05-17
Didn't Help. I still get the same message. Please Help, I don't want to boot into windows ever again.:)

---

### Post by ambar686413 on 2011-05-17
**[SIZE="3"]which version of ubuntu are you using???? if it is older, then uninstall it and again install the new version of ubuntu.. you may upgrade to ubuntu 11.04.. or may download it from [/SIZE]**[http://http://www.ubuntu.com/download/ubuntu/download]("http://http://www.ubuntu.com/download/ubuntu/download")....** [SIZE="3"]now install wine and you can run any .exe file in your system[/SIZE]**.:)

---

### Post by virtual_m on 2011-05-17
^
can't run any .exe file under wine ;)

[i can't start traktor pro @ ubuntu 11.04 and wine 1.2.x]

---

### Post by SynonM on 2011-05-17
I don't know for sure, but you might need directx (the .exe)
I just watched a video somewhere ... that's what the guy did.

---

### Post by ambar686413 on 2011-05-18
**[SIZE="2"]Now i can understand your problem correctly. you must upgrade from wine 1.2 to thr version wine 1.3.. If you then run any exe file you will be successful..[/SIZE]** ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo add-apt install wine
```

---

### Post by DigitalAlcatraz on 2011-05-18
> **gsmanners said:**
> [FL Studio 10]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23334") should work fine, but you probably need a newer version of Wine to run it.

[wine1.3]("apt://wine1.3")

see [http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

I think that's what gsmanners asked me to do. And I'm running Natty Narwhal 11.04

---

### Post by ambar686413 on 2011-05-18
[B][FONT="Century Gothic"][SIZE="3"]Have you used wine 1.3?.. if then the problem shouldn't happen. if you cant run FL studio, then reinstall ubuntu 11.04 in your system,.
[/SIZE][/FONT][/B]:popcorn:

---

### Post by DigitalAlcatraz on 2011-05-19
Will you please tell me something which will work and not just waste my time:confused:

---

### Post by gsmanners on 2011-05-19
Sorry but you need to provide more information than just a generic complaint if you want more help.

---

### Post by DigitalAlcatraz on 2011-05-20
I am running Wine 1.3 on Ubuntu 11.04 Natty Narwhal on my system. I am trying to Install FL Studio 10, but on opening the .exe it is giving the error message "Cannot load get.mfx. This object might need an external program or library not yet installed". The installer is running fine on windows(which i try avoid using).
The Specs of my system are 
Biostar T5XE Motherboard
Intel Core i7 860 @2.8 Ghz
2 X 2GB Corsair Corsair XMS 3 Ram @1600 MHZ
Sapphire ATI Radeon 5770 GPU
Corsair Hydro H70 Heat Sync
Cooler Master Xtreme Power Plus 600W PSU
I have set permissions allowing it to be executed.
Hope it helps so that you can help me;)
PS Feel Free to ask for any more information if required.

---

### Post by gsmanners on 2011-05-20
Wine is a tricky beast, at times. Backup whatever data you have on your "C: drive" and then delete the "~/.wine" folder. Then run winecfg again and try installing FLS 10 again. That's all I can think of to do.

---

### Post by koneella on 2011-05-22
i had the same problem. try this download latest wine SOURCE code [http://sourceforge.net/projects/wine/files/Source/wine-1.3.2.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.3.2.tar.bz2/download) ->extract->terminal->
 sudo apt-get install flex bison xorg-dev
cd to souce-code folder i have /home/user/Downloads/wine-1.3.20
then type this
./tools/wineinstall
if u get errors download those libs and try again .tools/wineinstall

---

### Post by liquip on 2011-06-02
I've got the same problem. Tried what koneella suggested (installed Wine 1.3.2) and the progress went fine without any errors, but I still get the same error-message when opening the Fl Studio installer (FLS10.exe).

E: Downloaded a new FL Studio installer and now it is working!

---

