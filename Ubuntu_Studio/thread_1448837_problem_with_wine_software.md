---
title: "problem with wine software"
date: 2010-04-07
forum: Ubuntu Studio
---

### Post by 14279 on 2010-04-07
hay...
i have a problem with my wine software,i cant find it in my applications toolbar.
when i go to the ubunto center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
[COLOR=#000099]                                          [/COLOR]when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]i really need held [COLOR=#000099]because i need a windows program for my [/COLOR][COLOR=#000099] studies...


tnx to all!!
[/COLOR][COLOR=#000099]                  [/COLOR]

---

### Post by lisati on 2010-04-07
Try:
```
man wine
```

Also see: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Dayofswords on 2010-04-07
i read somewhere on the forums that wine is a little buggy when it comes to icons and stuff in the application menu

---

### Post by 14279 on 2010-04-07
its says to download "wineconsole" and i can't find it in the ubuntu center...

---

### Post by Dayofswords on 2010-04-07
if you want a single package, you can type```
sudo apt-get install wineconsole
```
put in your password and then it will install

---

### Post by 14279 on 2010-04-07
> **Dayofswords said:**
> if you want a single package, you can type```
sudo apt-get install wineconsole
```put in your password and then it will install


i dont know my password
how can i recover it?

---

### Post by lisati on 2010-04-07
> **14279 said:**
> i dont know my password
how can i recover it?

Use the password you'd use to log in.

---

### Post by 14279 on 2010-04-07
david@david-desktop:~$ sudo apt-get install wineconsole
[sudo] password for david: 
Sorry, try again.
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wineconsole


I'M SORRY.... REAL NOOB

---

### Post by sandyd on 2010-04-07
can do run ```
ls ~/.local/share/applications
``` and ```
ls ~/.wine/drive_c/"Program Files"/
```p.s. what application are you trying to install?

---

### Post by sandyd on 2010-04-07
> **lisati said:**
> Try:
```
man wine
```

Also see: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

and this is not a *bash mod* thing, but why do most mods use 'man' to teach users how to use an application? the manual, a lot of times covers a lot of stuff that might be useful, but most users will likely not read it cause its so long...

---

### Post by cong06 on 2010-04-07
> **carlee said:**
> but most users will likely not read it cause its so long...
Not to mention the fact that users that aren't familiar with installing applications via command-line wouldn't find much use with the information from the man page.

14279: If the output from carlee's commands shows that you haven't used wine at all yet, and there's nothing fishy blocking the icons, then the easiest to get the menus back would *probably* be to reinstall.

---

### Post by 14279 on 2010-04-09
> **cong06 said:**
> Not to mention the fact that users that aren't familiar with installing applications via command-line wouldn't find much use with the information from the man page.

14279: If the output from carlee's commands shows that you haven't used wine at all yet, and there's nothing fishy blocking the icons, then the easiest to get the menus back would *probably* be to reinstall.


i used wine a mount ago and i deleted it..
i tried to install itunse and i allowd autorun,it really messtup my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.

what can i do?

---

### Post by 14279 on 2010-04-09
> **carlee said:**
> can do run ```
ls ~/.local/share/applications
``` and ```
ls ~/.wine/drive_c/"Program Files"/
```p.s. what application are you trying to install?


itunes...
this is what i get when i post the codes...

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 




i dont really know what it means ...
is there an option to recover wine?

---

### Post by 14279 on 2010-04-09
hay...
i need held with wine..
i already opened a thread with a lot of information about my problem...

this is the address of the old post.

[http://ubuntuforums.org/showthread.php?p=9087545#post9087545](http://ubuntuforums.org/showthread.php?p=9087545#post9087545)

tnx to all!

---

### Post by SnickerSnack on 2010-04-09
You don't need an icon in the menu in order to use wine, though you can make one if you want one.  Reinstalling (as suggested) might work to put one there for you.

You can do anything you want with wine from the command line, and then put a wine menu in the main menu with the things that you commonly use wine for.

Right click on the menu and select "Edit Menus".  Then you can add whatever you want.  In the main menu, you can add a "New Menu" and call it "Wine".  Then you can add a "New Item" inside of the Wine menu, and call it, say, Solitaire and then make the command "wine ~/.wine/Programs/solitaire" (or wherever the program is).

---

### Post by 14279 on 2010-04-09
> **SnickerSnack said:**
> You don't need an icon in the menu in order to use wine, though you can make one if you want one.  Reinstalling (as suggested) might work to put one there for you.

You can do anything you want with wine from the command line, and then put a wine menu in the main menu with the things that you commonly use wine for.

Right click on the menu and select "Edit Menus".  Then you can add whatever you want.  In the main menu, you can add a "New Menu" and call it "Wine".  Then you can add a "New Item" inside of the Wine menu, and call it, say, Solitaire and then make the command "wine ~/.wine/Programs/solitaire" (or wherever the program is).


there is a problem with the wine app.
its installd but i cant find the location.
how can i find the wine app?
i reinstall it more then 10 times with no luck...
i tried to do what you wrote, but i don't know which command to give the shortcut.

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..



any help for a fresh noob?




david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found


and 



david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

---

### Post by 14279 on 2010-04-09
hay...
i have a problem with my wine software,i cant find it in my applications tool-bar.
when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
i used wine a mount ago and i deleted it..
i tried to install itunse and i allowed auto-run,it really messed up my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

i dont really know what it means ...

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..

david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found

and 

david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...


[COLOR=#000099]

[/COLOR]

---

### Post by 14279 on 2010-04-09
hay...
 i have a problem with my wine software,i cant find it in my applications tool-bar.
 when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
 when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
 i used wine a mount ago and i deleted it..
 i tried to install itunse and i allowed auto-run,it really messed up my computer..
 so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
 Common Files  Internet Explorer  iPod  iTunes  QuickTime
 david@david-desktop:~$ ls ~/.local/share/applications
 alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
 david@david-desktop:~$ 
 
 i dont really know what it means ...

 when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..
 
 david@david-desktop:~$ wine
 Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
        wine --help                   Display this help and exit
        wine --version                Output version information and exit
 david@david-desktop:~$ wine location
 wine: could not load L"C:\\windows\\system32\\location.exe": Module not found
 
 and 
 
 david@david-desktop:~$ wine notepad.exe
 david@david-desktop:~$ wine start FILE.bat
 fixme:exec:SHELL_execute flags ignored: 0x00000500
 Application could not be started, or no application associated with the specified file.
 ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...


[COLOR=#000099]

[/COLOR]

---

### Post by 14279 on 2010-04-09
hay...
i have a problem with my wine software,i cant find it in my applications tool-bar.
when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
i used wine a mount ago and i deleted it..
i tried to install itunse and i allowed auto-run,it really messed up my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

i dont really know what it means ...

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..

david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found

and 

david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...

---

### Post by Bachstelze on 2010-04-09
WINE is just something that lets you run Windows programs, you can't run WINE itself. What program are you trying to run?

---

### Post by 14279 on 2010-04-09
hay...
i have a problem with my wine software,i cant find it in my applications tool-bar.
when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
i used wine a mount ago and i deleted it..
i tried to install itunse and i allowed auto-run,it really messed up my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

i dont really know what it means ...

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..

david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found

and 

david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...

---

### Post by 14279 on 2010-04-09
hay...
i have a problem with my wine software,i cant find it in my applications tool-bar.
when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
i used wine a mount ago and i deleted it..
i tried to install itunse and i allowed auto-run,it really messed up my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

i dont really know what it means ...

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..

david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found

and 

david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...

---

### Post by 14279 on 2010-04-09
itunes

---

### Post by Bachstelze on 2010-04-09
Then you must navigate to the directory were the iTunes setup program is located and run

```
wine itusesetupprogram.exe
```

---

### Post by 14279 on 2010-04-09
> **Bachstelze said:**
> Then you must navigate to the directory were the iTunes setup program is located and run

```
wine itusesetupprogram.exe
```


david@david-desktop:~$ wine itusesetupprogram.exe
wine: could not load L"C:\\windows\\system32\\itusesetupprogram.exe": Module not found

---

### Post by JEBB on 2010-04-09
I got the same result:  wine: could not load L"C:\\windows\\system32\\itusesetupprogram.exe": Module not found

---

### Post by Mi*6d@# on 2010-04-09
Please mention what your Ubuntu version is.

Anyway, if you are having any problems, try reinstalling wine
```
sudo apt-get purge wine && sudo apt-get install wine
```
and deleting WINE prefix (beware that Windows apps installed on Linux /home partition are kept there!)
```
rm -rf .wine
```

---

### Post by Hikayu on 2010-04-09
> **14279 said:**
> hay...
i have a problem with my wine software,i cant find it in my applications tool-bar.
when i go to the Ubuntu center i could see that its installed and i have the [COLOR=#000099]option[/COLOR] to remove it but thats the only option.
when i write "wine help" in the terminal i get----------[COLOR=#000099]wine: could not load L"C:\\windows\\system32\\executable.exe": Module not found

[/COLOR]
i used wine a mount ago and i deleted it..
i tried to install itunse and i allowed auto-run,it really messed up my computer..
so i deleted wine and i erased it from the [I]Application menu 
[/I]when i check in the Ubuntu center i can see that its install, i have the option to delete the program,but i cant find the program anywhere in my computer.[COLOR=#000099]

[/COLOR]this is what i get when i post the codes..

david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

i dont really know what it means ...

when i try to open a windows software,i right click on the software and i have the option to open it with wine,but when i try to open with wine it does not respond..

david@david-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
david@david-desktop:~$ wine location
wine: could not load L"C:\\windows\\system32\\location.exe": Module not found

and 

david@david-desktop:~$ wine notepad.exe
david@david-desktop:~$ wine start FILE.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

any help for a fresh noob?

tnx...

I'd say it's time for a complete re-installation of your wine directory. It's simple.

1) Enter the Synaptic Package Manager ( System > Administration > Synaptic Package Manager)

2) Search for "wine"

3) Mark it for "Complete Removal"

4) Head to your home directory ( Places > Home Folder)

5) Press Ctrl+H

6) Type ".wine" without doing anything. This will highlight a file. Press Enter.

7) Select "Program Files" And cut it onto your Desktop/anywhere

8) Delete ".wine"

9) Go here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

10) Select the latest. Choose from one of the rows depending on your CPU architecture.

11) Reinstall wine using the deb file you downloaded.

12) Cut your old "Program Files" into your new ".wine" directory.



_*After note:*_

I suggest using "winetricks" for installing dlls or stuff such as direct-x etc.

---

### Post by Hikayu on 2010-04-09
If you need winetricks, open a terminal window and type :

```
wget www.kegel.com/wine/winetricks
```
Than:
```
chmod 777 winetricks
```
And finally:
```
./winetricks
```

And install what you need,

Cheers,
Hikayu

---

### Post by cariboo on 2010-04-09
Please don't create multiple threads on the same subject, I have merged your 7 threads.

---

### Post by cong06 on 2010-04-11
> **14279 said:**
> 
david@david-desktop:~$ ls ~/.wine/drive_c/"Program Files"/
Common Files  Internet Explorer  iPod  iTunes  QuickTime
david@david-desktop:~$ ls ~/.local/share/applications
alacarte-made.desktop  mimeapps.list  ubuntu-software-center.desktop  wine
david@david-desktop:~$ 

You say you reinstalled wine a few times..
I think the reason the wine icon is missing from your menu, then, is because of the ~/.local/share/applications/wine file

try running:
```

rm -r ~/.local/share/applications/wine*

```
This code will delete all "customizations" that have occurred with your menus regarding wine. The default is (of course) to have the icon showing when it's installed.

This should immediately bring back your icons if this is the problem.

This should make it so you don't have to:
```

rm -rf ~/.wine/

```
and I would suggest you wait in deleting this folder until you've tried fixing the menus (unless you enjoy downloading and installing your windows content again)

---

