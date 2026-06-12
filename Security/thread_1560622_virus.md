---
title: "virus"
date: 2010-08-25
forum: Security
---

### Post by austicorn on 2010-08-25
i have got  a virus in my pen drive and i am unable to delete it in ubuntu. i am also unable to change its property from an auto execute program, or bring about any other change to the file. it shows itself as an icon similar to recycle bin in windows vista in the windows vista o.s. i am a new user to ubuntu, please help me to solve this problem.

---

### Post by sharathcshekhar on 2010-08-25
If you are using new version of Ubuntu, you should have the format option when you right click on the pen drive icon when it appears in the Desktop.
If not, you can open the terminal and force erase by good old 
rm -rf /mounted/path/
But be very careful when you give the path. If you go wrong, due to a typo you will end up deleting everything!

---

### Post by Maverick_Meerkat on 2010-08-25
Greetings,

As a last resort, and assuming any other data on that drive is backed up, You can always format the drive. That would effectively erase most any virus.

---

### Post by OpSecShellshock on 2010-08-25
Formatting is most likely the way to go. Until that happens, I'd advise you not to put the drive into a Windows machine at all.

---

### Post by jre6 on 2010-08-25
You may do one of the following:

[LIST]
[*]Format the drive by right-clicking the drive and selecting the option.
Or, typing the following in the terminal:
```
rm -rf /media/somename
```where "somename" is the path name of the pen drive after succeeded by "/media". For example, if it is "/media/40A3-113B" then you would type:
```
rm -rf /media/40A3-113B
```
[*]Use Wine to run a windows antivirus and remove the virus. If you have got an internet connection, you may directly type the following in the terminal and remove it:
```
sudo apt-get install wine
```Other wise, download the wine and libaudio2 packages from packages.ubuntu.com. However, Wine, not being a perfect Windows emulator, may not be able to run an antivirus.
[*]As for the icon that appears, see if there is a file called autorun.inf in the pen drive. Open it. You will see a line something like the following:
```
ICON=someicon.ico
```Find the icon and delete it. And then delete autorun.inf.
[/LIST]

---

### Post by wacky_sung on 2010-08-25
I never encourage people to use wine just to make Ubuntu communicate with Window OS.First of all,it will cause more issue such as virus, trojan, malwares, etc.To ease those virus issue is just to use Ubuntu OS alone and all those window issue will never be able to incorporate into it.

As for window it is always good run a [sandboxing]("http://www.sandboxie.com/") in which it will eliminated all those virus issues if you are scared of it.

---

