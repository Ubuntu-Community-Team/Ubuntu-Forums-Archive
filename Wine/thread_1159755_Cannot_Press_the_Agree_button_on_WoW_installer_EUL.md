---
title: "Cannot Press the Agree button on WoW installer EULA"
date: 2009-05-15
forum: Wine
---

### Post by Megaman20015 on 2009-05-15
I am using Ubuntu 9.04
Okay I installed wine 1.1.8 correctly
downloaded the installer and ran it with wine
it downloads patch 3.0.1 correctly
but when i scroll down the Eula to the bottom the Agree button remains inactive
I have tried ies4linux
still does not work
tried configuring it as Windows XP and that did not work
what should i do now?

---

### Post by mrblondeisback on 2009-05-15
make sure you're using the newest version of Wine, I had this problem. Check out winehq.org

---

### Post by linuxjuicer on 2009-06-03
i'm having the same problem. i checked my wine version is 1.0.1 stable, should i update to 1.1.22 under development version?

---

### Post by hikaricore on 2009-06-03
> **mrblondeisback said:**
> make sure you're using the newest version of Wine, I had this problem. Check out winehq.org

^

> **linuxjuicer said:**
> i'm having the same problem. i checked my wine version is 1.0.1 stable, should i update to 1.1.22 under development version?

---

### Post by Squelthas on 2009-06-08
Same problem, i'll try with another version of Wine and i reply ;D

---

### Post by Squelthas on 2009-06-09
I have this error: 

wine client error:0: version mismatch 0/386.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

:/

---

### Post by PROject-Emerald on 2009-06-09
You can go into the C:\Program Files\World of Warcraft folder and edit a value that makes it auto-accepted. Don't know which file, though.

---

### Post by garnold on 2009-10-02
Did you get this working? I'm having the same issue right now.

---

### Post by thom_raindog on 2009-10-03
The file you need to edit is: /path_to_WoW/WTF/Config.wtf

Make sure you have
```

SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"

```
in there and you should be fine.

---

### Post by mcneany on 2009-10-15
RE: thom_raindog and PROject-Emerald:

Your advice is of no use if the application has not yet been installed. 

Having same issue.

---

### Post by Dorito Style on 2009-11-26
I had this problem as well, this youtube video does a pretty good job of explaining the method that worked for me: [http://www.youtube.com/watch?v=aYU_r646PQ8&feature=youtube_gdata](http://www.youtube.com/watch?v=aYU_r646PQ8&feature=youtube_gdata)

---

### Post by Pikestaff on 2009-11-27
If updating Wine doesn't work for some reason, then this is how I solved the problem back in WotLK Beta: [http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html](http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html)

---

### Post by PhoeniX1992 on 2009-12-16
I've found a working and simple solution for this problem (I know this is an old thread, but it shows up at a google search for this problem, and by posting this, lots of people will be able to solve this problem.)
For windows there exists an apllication named "AutoIt", which allows you to manipulate windows. It also works under wine and is capable of manipulating applications opened with wine.
With the following script it is able to enable the grayed-out button and automatically clicking it. I've also added an pre-compiled .exe file which is directly executable with wine.

```
If WinExists("End User") = 1 Then

	ControlEnable("End User","","[CLASS:Button; INSTANCE:1]")

	ControlClick("End User","","[CLASS:Button; INSTANCE:1]")

	MsgBox(64, "Ubuntu WoW EULA Hack", "Succes!")

	Exit

Else

	MsgBox(48, "Ubuntu WoW EULA Hack", "Can't find EULA screen!")

	Exit

EndIf
```

Good luck you Linux WoW'ers out there :P

---

### Post by Alatar1 on 2009-12-18
[http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927)

---

### Post by Bwathke on 2009-12-18
> [http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927)
There is your solution update WINE and its all good to go. I had this problem (Only played the demo and hated it) I updated wine and its fixed.

---

### Post by AilesGrises on 2009-12-19
> **thom_raindog said:**
> The file you need to edit is: /path_to_WoW/WTF/Config.wtf

Make sure you have
```

SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"

```
in there and you should be fine.

I'm having the clicking yes inside the program like you thought, my config.WTF file is set like you listed, but it still shows it. Termination Without Notice specifically.

---

### Post by Nat90 on 2009-12-22
The EXE downloadable worked perfectly for me, just remember to execute it with the WOW install screen open and in the agree option

---

### Post by Gautam Kok on 2010-01-10
The problem with the button is that the installer uses HTML to activate the button. In Windows it uses Internet Explorer to do this. Wine does not have IE installed. Therefore you may download and install Internet Explorer easiest through the following steps:

Try this:

Install WINETRICKS: [http://wiki.winehq.org/winetricks:](http://wiki.winehq.org/winetricks:)
```
$ wget http://www.kegel.com/wine/winetricks
$ sh winetricks corefonts vcrun6
```It will now install the list of programs on the website up there ^. Thus, it might ask you for confirmation several times.

Now install it so that you can run winetricks as a command:
```
$ chmod +x winetricks
$ sudo mv winetricks /usr/local/bin
```
Now run the program by typing in the command:
```


$ winetricks
```Select IE6 and press OK. Now run through the installation.

When done, download the latest InstallWoW.exe from the website of WoW. Run the installer, wait for it to have downloaded the app and accept the EULA. The installation will now continue!

Enjoy!

---

### Post by pixla.cz on 2010-02-02
> **PhoeniX1992 said:**
> I've found a working and simple solution for this problem (I know this is an old thread, but it shows up at a google search for this problem, and by posting this, lots of people will be able to solve this problem.)
For windows there exists an apllication named "AutoIt", which allows you to manipulate windows. It also works under wine and is capable of manipulating applications opened with wine.
With the following script it is able to enable the grayed-out button and automatically clicking it. I've also added an pre-compiled .exe file which is directly executable with wine.

```
If WinExists("End User") = 1 Then

    ControlEnable("End User","","[CLASS:Button; INSTANCE:1]")

    ControlClick("End User","","[CLASS:Button; INSTANCE:1]")

    MsgBox(64, "Ubuntu WoW EULA Hack", "Succes!")

    Exit

Else

    MsgBox(48, "Ubuntu WoW EULA Hack", "Can't find EULA screen!")

    Exit

EndIf
```Good luck you Linux WoW'ers out there :P

Thanks man, you saved my day :)

---

### Post by ChameleonSaint on 2010-03-19
[SIZE=4]Thank-you the EULA exe worked for me also. 
I already had the latest version of Wine.[/SIZE]

---

### Post by fredrow on 2010-03-28
[SIZE=4]THX This worked perpect[/SIZE], as long as you run the hack when trying to click at the agree bottom

---

### Post by wolpertinger on 2010-06-29
Hello, after getting this problem, I tried this method.

> **Gautam Kok said:**
> The problem with the button is that the installer uses HTML to activate the button. In Windows it uses Internet Explorer to do this. Wine does not have IE installed. Therefore you may download and install Internet Explorer easiest through the following steps:

Try this:

Install WINETRICKS: [http://wiki.winehq.org/winetricks:](http://wiki.winehq.org/winetricks:)
```
$ wget http://www.kegel.com/wine/winetricks
$ sh winetricks corefonts vcrun6
```It will now install the list of programs on the website up there ^. Thus, it might ask you for confirmation several times.

Now install it so that you can run winetricks as a command:
```
$ chmod +x winetricks
$ sudo mv winetricks /usr/local/bin
```Now run the program by typing in the command:
```


$ winetricks
```Select IE6 and press OK. Now run through the installation.

When done, download the latest InstallWoW.exe from the website of WoW. Run the installer, wait for it to have downloaded the app and accept the EULA. The installation will now continue!

Enjoy!

Unfortunately it led me to another error i cannot figure: Here a mere copy parste of what i guess is important, guess there is a conflict with gecko but no idea...

###!!! ASSERTION: Expecting twice repeated dead-key character: 'rv == 2', file /usr/local/src/wine-mozilla/widget/src/windows/nsKeyboardLayout.cpp, line 390
Leaked URLs:
  file:///C:/windows/system32/gecko/1.0.0/wine_gecko/
  file:///C:/windows/system32/gecko/1.0.0/wine_gecko/

thx for your suggestions

Edit: this is when lauching wowinstaller.exe from terminal, if i just double-click on the install icon, there is just no change and EULA remains grey and unacceptable.

---

### Post by us3fourtwo4 on 2010-08-09
You're my hero.

---

