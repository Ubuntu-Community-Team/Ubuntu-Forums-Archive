---
title: "Problems with PyLOTRO"
date: 2010-09-16
forum: Wine
---

### Post by dadush777 on 2010-09-16
Hello :)

Ive installed LOTRO on my Ubuntu 10.10 , 

and I launched the PyLOTRO, enter my Game Directory, My Account Details but then I can't get past this post in the log : 

Checking Account Details...

it does that forever... what can be the problem here?

Thanks alot!

---

### Post by ajackson on 2010-09-17
I'm not trying to be funny but could you repost your question in [this thread]("http://ubuntuforums.org/showthread.php?t=386480")? Having all the LotRO related stuff in one place makes it easier to keep track.

Also please elaborate more, how did you install LotRO and PyLotRO, wine version, etc. Also is this a newly created F2P account that hasn't been logged onto before?

---

### Post by tochirov on 2010-09-24
so here I am, I have a LOTRO account thats F2P I have downloaded it both on a windows partition in win7 (it runs just dandy there) and copied it over to my .wine/drive_c/Program files/LOTRO directory,  AND I have done a straight install using wine on the mordor installer files. and it installed with no problems. 

I am attempting to run it with Pylotro 1.13.exe  
I set the game directory correctly. I tell it to patch. (I have tried the patch2.dll trick) it patches almost instantly and reads **finished** without any other updates, I have no idea if that is whats not working or not.   I've installed vcrun2003, and 2005trial with winetricks 

I've tried it every which way I can think of and I am completely stumped... advice? 

Long Story Short: when I attempt to login I get ---> 

Checking account details...                and it just hangs there forever. 

the news page eventually updates, the login continues to hang. 

here's the output from terminal if its helpful: 

fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e67c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
Traceback (most recent call last):
  File "PylotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 295, in txtPasswordEnter
  File "PylotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 289, in btnLoginClicked
  File "PylotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 306, in AuthAccount
  File "PylotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.PyLotROUtils", line 529, in __init__
AttributeError: 'NoneType' object has no attribute 'status'
fixme:imm:ImmReleaseContext (0x10062, (nil)): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub

---

### Post by tochirov on 2010-09-24
oh, wine is set to Win2k if thats helpful...  I have tried multiple diffrent ways of the install, multiple tweaks, still nothing.

---

### Post by Shakz on 2010-09-27
[[COLOR=#444444]http://www.youtube.com/watch?v=a7jAWw-fP4c[/COLOR]]("http://www.youtube.com/watch?v=a7jAWw-fP4c")
 
There are a series of vids for installing lotro from start to finish available as well.

---

### Post by lobfredd on 2010-09-28
I think this problem is related to Ubuntu 10.10.
I have the same problem.
I installed 10.10. and got the error, then i installed 10.04 and it worked just fine!
then i did a update to 10.10 and same error again. so?

---

### Post by slave-zeo on 2010-10-13
Same for me, 10.10 does not work for me with lotro. I tried wine 1.2.1, 1.3.x and crossover games. all the same outcome.

going back to 10.04 till it's fixed.

EDIT: Weirdness abound! I went back to 10.04 and set it up the way I always have and now LOTRO is doing the same thing as 10.10. Starts the launcher and then once you login it does nothing.

---

### Post by slave-zeo on 2010-10-14
OK, I got it fixed under 10.10. I had to use the native linux pylorto launcher to get it to work. It has to be a problem with the pylotro wine version.

Add this to your apt get repositories list

  deb [http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu) lucid main

and then 

  sudo apt-get update

and then

  sudo apt-get install pylotro

You'll find a application launcher icon in the games menu. click it and configure as normal. Make sure you use the correct patcher .dll and update it first. 

Worked like a charm for me.

---

