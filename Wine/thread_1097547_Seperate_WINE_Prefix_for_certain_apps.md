---
title: "Seperate WINE Prefix for certain apps ?"
date: 2009-03-16
forum: Wine
---

### Post by killpotts on 2009-03-16
I have seen several instances where certain apps benefit from being installed under a seperate Wine prefix so that it can be wiped/rebuilt without affecting other programs ( Namely apps that tend to either botch up the registry with errors, or have a 30 day trial limitation but the activation doesn't work in WINE so you can't buy it and need to wipe everything if you want to use it again, or need conflicting settings. )

But I have never seen any explanation on how exactly this can be done. Does anyone know ?

---

### Post by killpotts on 2009-03-16
I tried to do it as this page explains with no luck:

[http://wiki.jswindle.com/index.php/WINEPREFIX](http://wiki.jswindle.com/index.php/WINEPREFIX)

Problm is it really isn't very concise. I tried the command it gave ( # export WINEPREFIX=$HOME/.wine-wow/ ) But it did not do anything.

I'm in need of some kind of instruction/tutorial that is a bit more explanatory and in steps then just "Poop this into your konsole/terminal, recompile something, and hope it works" 

Any help would be appreciated. :popcorn:

---

### Post by cogadh on 2009-03-16
I don't know why people insist on doing that export stuff, it's not necessary and there is an easier way to do it. To create a new prefix, just run this (make the prefix name anything you want):
```
wineprefixcreate ~/.newwineprefix
```
When you want to use that prefix to do anything, including configuring it, you need to specify the prefix in the command:
```
WINEPREFIX=~/.newwineprefix winecfg
WINEPREFIX=~/.newwineprefix wine foo.exe
WINEPREFIX=~/.newwineprefix wine uninstaller
```
That's really all there is to it.

---

### Post by killpotts on 2009-03-16
Ahh, that makes a lot more sense then what they are saying...but it did not work.

I did this:

```

wineprefixcreate ~/.Winetwo

```

It gives me this error:

```

Unknown option /home/Potts/.Winetwo
Usage: /usr/bin/wineprefixcreate [options]

Options:
  -h, --help                 Display this message
      --prefix <dir>         Directory to create (default: $WINEPREFIX or ~/.wine)
  -q, --quiet                Don't print status messages
  -w, --wait                 Wait for the wineserver to exit before returning

```

Not sure what to do next.

---

### Post by cogadh on 2009-03-16
Crap. Sorry about that, I'm an idiot today. The command to create it should be:
```
wineprefixcreate --prefix ~/.Winetwo
```
I also realized I made a mistake on how to use the new prefix once created, I left out "env" on the command, so the samples should actually look like this:
```
env WINEPREFIX=~/.newwineprefix winecfg
env WINEPREFIX=~/.newwineprefix wine foo.exe
env WINEPREFIX=~/.newwineprefix wine uninstaller
```
Sorry for the confusion, I blame it on my lack of sleep.

---

### Post by killpotts on 2009-03-16
Ahh, I should have gotten that on my own. :P


I managed to create the Prefix and get it all working, but ran into a related problem when actually installing the piece of software I need to do this thing for. I need to install a winetricks in order to get it working, so I tried:

```

WINEPREFIX=~/.Winetwo wget http://kegel.com/wine/winetricks && sh winetricks msxml3

```

And the installer for that came up and ran ( It's an XML extension )...but upon reviewing its actions I found it is installing into the normal /.wine prefix. :(

Should it be ok ?

---

### Post by cogadh on 2009-03-16
Nope, you need to use that "env" command that I missed earlier in order to make winetricks install the stuff in your new prefix:
```
env WINEPREFIX=~/.Winetwo sh winetricks msxml3
```

---

### Post by killpotts on 2009-03-16
That managed to work. For some reason I had to type exactly what you had and drop the Wget.

---

### Post by cogadh on 2009-03-16
the "wget" is just a terminal comand to download something from the web, in this case, the winetricks script. Since already did that the first time you ran the command, you don't need to do it again.

---

### Post by binbash on 2009-03-17
playonlinux does this easily.You do not need to mass with codes  : )

---

### Post by Morganvd on 2010-04-03
I seem to be having a lot of trouble with playonlinux steam works download counter strike and it bombs. I want to try create my own prefix

---

### Post by alexthunder on 2010-05-29
I have problem using 2 wineprefixes.

When I go to /home/user/.wine3/drive_c/Program Files/Folder_Two and launch the program info.exe, everything works fine.

Also if I cd to the directory and launch the program 
```
cd "/home/user/.wine3/drive_c/Program Files/Folder_Two"
env WINEPREFIX=/home/user/.wine3 env 'LANG=ru_RU.utf8' wine info.exe
```everything works fine

However if I launch it like this:
```
env WINEPREFIX='/home/user/.wine3' env 'LANG=ru_RU.utf8' wine 'c:/Program Files/Folder_Two/info.exe'
```I get the program c:/Program Files/Folder_One/info.exe from /home/user/.wine launched. 
This is really weird, because I don't have Folder_Two in /home/user/.wine and i don't have Folder_One in /home/user/.wine3
What am I doing wrong?

---

### Post by cogadh on 2010-05-29
I'm not sure it really matters, but it could be your use of **'** instead of **"**.

---

### Post by alexthunder on 2010-05-30
> **cogadh said:**
> I'm not sure it really matters, but it could be your use of **'** instead of **"**.
Thank you. I've tried every possible combination of ' and ". At first I was using " for the file path, but it wasn't working.

---

### Post by Morganvd on 2010-07-24
For WINEPREFFIX i found a niffty little app her on the forum called GWINE that creates bottles and intergrates with winetricks.

[http://ubuntuforums.org/showthread.php?t=1346038&highlight=gwine](http://ubuntuforums.org/showthread.php?t=1346038&highlight=gwine)

Has been a great help

---

### Post by Elcivor on 2010-09-06
sorry for necro-posting..

so how do I install a game via a dvd and let it install into that prefix?

---

### Post by schtufbox on 2010-09-06
> **Elcivor said:**
> sorry for necro-posting..

so how do I install a game via a dvd and let it install into that prefix?
Open a terminal at the dvd.

```
env WINEPREFIX=~/.newwineprefix wine setup.exe
```

Replacing .newwineprefix with whateve ryour prefix is called and setup.exe with whatever the installer is called.

If it's an MSI file then try

```
env WINEPREFIX=~/.newwineprefix wine msiexec /i setup.msi
```
again changing .newwineprefix as appropriate and setup.msi to the actual msi file.

---

### Post by thed0ctor on 2012-04-06
Hey I'm trying to run the wineprefixcreate command but it says unknown command... Am I missing something?

---

### Post by Toz on 2012-04-06
It's deprecated. See: [http://wiki.jswindle.com/index.php/Wineprefixcreate]("http://wiki.jswindle.com/index.php/Wineprefixcreate"). I believe it is now run automatically when a prefix that doesn't exist is referenced (as per instructions on post #17).

---

