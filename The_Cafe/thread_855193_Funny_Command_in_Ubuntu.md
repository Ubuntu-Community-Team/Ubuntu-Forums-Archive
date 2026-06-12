---
title: "Funny Command in Ubuntu"
date: 2008-07-10
forum: The Cafe
---

### Post by sharks on 2008-07-10
try this

sudo apt-get moo

and if u know anything please post it here

---

### Post by sisco311 on 2008-07-10
aptitude -v moo
aptitude -vv moo
...

---

### Post by sharks on 2008-07-10
yes: aptitude -v moo
aptitude -vv moo
aptitude -vvv moo
aptitude -vvv moo

and prss alt+f2 and then type this **free the fish**

---

### Post by fatality_uk on 2008-07-10
Have started my UF timer to see how long it is before this gets merged or placed into recurring... :D

tick tick tick...

---

### Post by TBOL3 on 2008-07-10
You know, on my old computer, I did type in free the fish, but I could never get the fish to go away.  A would type it in now if anyone would tell me how to get rid of the fish.

---

### Post by diafanos on 2008-07-10
Just do Alt+F2 and type 
```

killall gnome-panel

```

---

### Post by Masoris on 2008-07-10
```
$ sudo apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
$ yes
```
I didn't know that before, there are command names 'yes'. 'Yes' command makes me more moo.
:lolflag::lolflag::lolflag:

---

### Post by Dr Small on 2008-07-10
In a terminal, type:
```
zenity --about
```

Then with the About Dialog up, just type:
```
zen
```

---

### Post by bruce89 on 2008-07-10
Alt+F2 then *gegls from outer space*. Who said Linux didn't have games?

---

### Post by pofigster on 2008-07-10
```
sudo apt-get install cowsay
```
then:
```
cowsay Whatever you want the cow to say!
```

---

### Post by LordDelta on 2008-07-10
Xd

---

### Post by dracule on 2008-07-10
what does the "yes" command do? all it does it make an infinite thing of "y"'s

---

### Post by Hells_Dark on 2008-07-10
an infinite thing of "whatever you want".

$yes "ok"

---

### Post by RiceMonster on 2008-07-10
> **pofigster said:**
> ```
sudo apt-get install cowsay
```
then:
```
cowsay Whatever you want the cow to say!
```

Cowsay rules, checkout my signature.

---

### Post by dracule on 2008-07-10
[QUOTE=RiceMonster]fortune | cowsay -f tux.cow [/QUOTE]
ahhh! dude that is pretty cool

---

### Post by edm1 on 2008-07-10
Not exactly a command but there's a good easter egg in open office:

1. create a new sheetin openoffice.org Calc (spreadsheet)
2. enter this formula in a cell :
=game()
and validate (validation button or enter)
3.the cell will display "say what?"
4. Enter this formula:
=GAME("StarWars")
5. a new window will open with a little game star war game.
6. But if you type again this formula, the cell will return the display "oh no, not again!"

---

### Post by MaxIBoy on 2008-07-10
I accidentally typed "aptitude -vvvvvvv mo," and got this (the funny part is at the bottom)


> Unknown command "mo"
aptitude 0.4.9
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends	Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  [B]This aptitude does not have Super Cow Powers.
[/B]

---

### Post by dracule on 2008-07-10
wth... yes is at version 6.10

why would you need multiple versions of a prgram that just repets something?

---

### Post by bruce89 on 2008-07-10
> **dracule said:**
> what does the "yes" command do? all it does it make an infinite thing of "y"'s

It is for things like *fsck* when it asks for confirmation to fix things.

---

### Post by the_hardy_kid on 2008-07-10
cowsay -f dragon.cow ROAR, fear me...

lol

---

### Post by TBOL3 on 2008-07-11
None of these *.cow files work, am I doing something wrong?

---

### Post by Jim! on 2008-07-11
Thankyou for this thread! I could remember there was a command to get a 'cow' to show up in the terminal but I couldn't remember what it was! Why would I want to make a cow appear in the terminal? Cause its awesome;) Also that "free the fish" thing i freakin awesome:D

---

### Post by Ocxic on 2008-07-11
+1

---

### Post by the_hardy_kid on 2008-07-11
> **TBOL3 said:**
> None of these *.cow files work, am I doing something wrong?

Well are you sure cowsay is installed?

```
sudo apt-get install cowsay
```

---

### Post by dracayr on 2008-07-21
cowsay is nothing, try espeak

dracayr

---

