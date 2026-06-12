---
title: "Wine prefixes for 32 and 64 bit applications"
date: 2023-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by neurofunk161987 on 2023-07-28
Hello,

So i need help with with wine prefixes.I'm new to linux so please eli5.I want to run two games:one si world of warcraft witch is a 32 bit application and the second one is League witch of coure its 64 bit.When i install lutris and setting up for league i get error message when i try to install wow saying i need 32 bit wine.So how can i have both of the games to run.I've read that i can add prefixes and how to to it but i just dont get it(im doing exactly what it says on wine forum but without any succes)
Ive tried with bottles too and saddly no succes either.Im on ubuntu 23.04

---

### Post by grahammechanical on 2023-07-30
How did you install Wine? As I understand it, Wine is a 32 bit program. When we install it, either through Ubuntu Software or through setting up the Wine repository following Wine instructions, then certain 32 bit libraries should install so that wine can run.

The Intel and AMD 64 bit CPU are backwards compatible with 32 bit programming code. So, we install Ubuntu amd64 and we can run both 64 bit programs and 32 bit programs like Wine. To run 64 bit Windows applications under Wine you need to give Wine a prefix. This should help:

[https://www.reddit.com/r/winehq/comments/o6qo0q/how_to_install_wine_64bit/](https://www.reddit.com/r/winehq/comments/o6qo0q/how_to_install_wine_64bit/)

Regards

---

### Post by grahammechanical on 2023-07-31
I find that winetricks is useful for working with WINE. Winetricks is in Ubuntu software.

When I load Winetricks I get a message saying

> You are using a 64-bit WINEPREFIX. Note that many verbs only install 32-bit versions of packages. If you encounter problems, please retest in a clean 32-bit WINEPREFIX befor ereporting a bug.

After clicking OK I get a small dialog where I choose to use the default wineprefix or create a new prefix. Clicking that option brings up a dialog where I can choose an architecture 32 or 64 and give a label to the new prefix. Then Winetricks presents a dialog where I can choose the default wineprefix or the new prefix I have created. Then I get a dialog with multiple options including uninstall, etc.

Regards

---

### Post by mastablasta on 2023-08-01
> **neurofunk161987 said:**
> Hello,

So i need help with with wine prefixes.I'm new to linux so please eli5.I want to run two games:one si world of warcraft witch is a 32 bit application and the second one is League witch of coure its 64 bit.When i install lutris and setting up for league i get error message when i try to install wow saying i need 32 bit wine.So how can i have both of the games to run.I've read that i can add prefixes and how to to it but i just dont get it(im doing exactly what it says on wine forum but without any succes)
Ive tried with bottles too and saddly no succes either.Im on ubuntu 23.04

let me simplify this explanation - Wine prefix is like a C drive with new Windows install (well actually juts small part of the OS). then you install a game there and any libraries (reverse engineered or original ones) it might need. the game then things it is running on Windows OS, but in fact it is running inside a prefix pretending to be windows. 
installers such as Lutris, Proton (on Steam), Play on Linux and such usually install each game into it's own prefix. this is not necessary but it makes it less messy (no conflict between libraries) and easy to uninstall - you just delete the prefix (or rather the folder that has it).
so just like widnows OS, prefix can also be either 32 bit (used for older games and apps) or 64bit (mostly used for new games and apps). so each game goes to it's own prefix and then they will run separately. i have about 9 prefixes in PlayonLinux app, 1 in Lutris and close to 25 in Steam.  each of them is their own contained folder and separated. each time you install a game in lutris it will create it's own prefix.

Lutris uses scripts that help you with install. the scripts configure and select the correct prefix. they also pull in any needed libraries. so unless you are doing manual install, this is likely not the issue. 

i assume by League you mean League of Legends? that one should work with Lutris. I've been trying to find time to try it out myself.    

How to install in lutris without using scripts (manual install):
[https://www.reddit.com/r/wine_gaming/comments/ejoh2x/manually_installing_games_with_lutris/](https://www.reddit.com/r/wine_gaming/comments/ejoh2x/manually_installing_games_with_lutris/)

back to your issue - you might need to install 32 bit libraries. probably wine32: 
```
sudo apt install wine32
```

you might also want to add i386 libraries:
```
sudo dpkg --add-architecture i386
```

---

