---
title: "Can't install wine"
date: 2010-02-15
forum: Wine
---

### Post by HappyFeet on 2010-02-15
I have all repos enabled, and added **ppa:ubuntu-wine/ppa** as directed. 

Wine shows up in synaptic, but I get 
```
wine1.2:
 Depends: ia32-libs but it is not going to be installed
 Depends: lib32asound2 but it is not going to be installed
 Depends: libc6-i386 but it is not going to be installed
 Depends: lib32nss-mdns but it is not going to be installed

```

I've googled and tried everything I know, but nothing works. Anyone have a clue? Btw, I'm running 64bit ubuntu.

---

### Post by Dracona on 2010-02-15
Have a look here. this might help.

[http://ubuntuforums.org/showthread.php?t=1340351](http://ubuntuforums.org/showthread.php?t=1340351)

---

### Post by HappyFeet on 2010-02-15
Thanks, but I tried that link before and it did nothing for me. 

I downloaded the .deb for wine-doors and still get errors. I'm at a loss. I had wine installed at one time, but got rid of it and want it back. Kind of strange I'm getting dependency errors.

---

### Post by Dracona on 2010-02-15
This  might be a stupid question, ( sorry if it is ), but have you tried to uninstall Wine?

I know i had a problem one time installing wine 1.2, was getting same errors. 


$ sudo apt-get remove wine
 $ sudo apt-get install wine1.2

this solved my problems.

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> This  might be a stupid question, ( sorry if it is ), but have you tried to uninstall Wine?

I know i had a problem one time installing wine 1.2, was getting same errors. 


$ sudo apt-get remove wine
 $ sudo apt-get install wine1.2

this solved my problems.

Yes I did. I even did 
```
sudo apt-get clean && sudo apt-get autoremove
```
and removed ~/.wine

When I run
```
sudo apt-get install wine1.2
```
it says there are broken packages. However, running 
```
sudo apt-get install -f
```
does not fix anything, and synaptic reports no broken packages. I am at a complete loss here. Any other ideas?

---

### Post by Dracona on 2010-02-15
check and see what preferred server you are using for the repositories, i usually let the system find the best server for my location.
you can get to this option by going to System,Administration, Software Sources. it will be located on the first Tab ( Ubuntu software)  near the bottom,  Download from: ( drop down window)



this info came from this link
[http://ubuntuforums.org/showthread.php?t=1309568](http://ubuntuforums.org/showthread.php?t=1309568)
This link deals with a person who has upgraded from jaunty to karmic.

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> check and see what preferred server you are using for the repositories, i usually let the system find the best server for my location.
you can get to this option by going to System,Administration, Software Sources. it will be located on the first Tab ( Ubuntu software)  near the bottom,  Download from: ( drop down window)



this info came from this link
[http://ubuntuforums.org/showthread.php?t=1309568](http://ubuntuforums.org/showthread.php?t=1309568)
This link deals with a person who has upgraded from jaunty to karmic.

Tried that also.

---

### Post by Dracona on 2010-02-15
try to disable the [I]ppa:ubuntu-wine/ppa. repository this is used to get the latest 1.1.38 ( unstable version ) then try to install wine from synaptic or sudo apt-get install wine.

this will get you the stable version1.0.1 . or at least it should. 
[/I]

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> try to disable the [I]ppa:ubuntu-wine/ppa. repository this is used to get the latest 1.1.38 ( unstable version ) then try to install wine from synaptic or sudo apt-get install wine.

this will get you the stable version1.0.1 . or at least it should. 
[/I]

Tried that, and synaptic still shows wine 1.2 as being available. Sounds like synaptic/apt is hosed.

---

### Post by Dracona on 2010-02-15
did you reload after disableing the wine ppa?

or 
sudo apt-get update

---

### Post by Dracona on 2010-02-15
another option might be to try to install it from the Ubuntu Software Center, under the Applications tab.

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> did you reload after disableing the wine ppa?

or 
sudo apt-get update

Yes.  I was hoping there was some weird/not well known fix for this. I have tried every normal thing that you are probably going to propose. It seems to me, that somehow synaptic/apt got corrupted somehow. I'm thinking about reinstalling, since it's the only way this is going to get fixed. It's a shame though, because everything else works flawless.

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> another option might be to try to install it from the Ubuntu Software Center, under the Applications tab.

I figured it wouldn't work, but I tried it anyway. Oh well. It's really weird that I have unresolved dependencies that can't be fixed. Like I said, my computer runs flawlessly otherwise.

---

### Post by Dracona on 2010-02-15
> **HappyFeet said:**
> Yes.  I was hoping there was some weird/not well known fix for this. I have tried every normal thing that you are probably going to propose. It seems to me, that somehow synaptic/apt got corrupted somehow. I'm thinking about reinstalling, since it's the only way this is going to get fixed. It's a shame though, because everything else works flawless.


to be honest, i am a recent convert (6 months maybe) from windows to ubuntu ( and happy at that! )
most of what i learn is by trial an error, ussually more error then anything. so doing the reinstall is my usual go to fix.  i ussually end up doing a reinstall once a week, becouse i cant leave well enough alone, and end up trashing something.  its only software, easily fixed by the magic repair ( install cd).  but at least i am learning as i go. just sometimes i go sloooow.  best of luck to you HappFeet
Dracona

---

### Post by Dracona on 2010-02-15
> **HappyFeet said:**
> I figured it wouldn't work, but I tried it anyway. Oh well. It's really weird that I have unresolved dependencies that can't be fixed. Like I said, my computer runs flawlessly otherwise.

just out of curiosity, what did it tell you when you tried it from the Ubuntu Software Center?

---

### Post by HappyFeet on 2010-02-15
> **Dracona said:**
> just out of curiosity, what did it tell you when you tried it from the Ubuntu Software Center?

Unresolvable dependencies. Btw, thanks a bunch for your time. I had wine running well before I uninstalled it.

---

### Post by Dracona on 2010-02-15
> **HappyFeet said:**
> Unresolvable dependencies. Btw, thanks a bunch for your time. I had wine running well before I uninstalled it.

you are very welcome, I do enjoy helping people, or at least trying to anyway. but i am surprised more people haven't got into this thread. maybe give it a day or two and someone will come up with the correct answers and we both will learn something.

be safe HappyFeet and best of luck to you

Dracona

---

### Post by HappyFeet on 2010-02-15
Thanks again. I'm not trying to blow my own horn, but I've probably done over 50 installs of ubuntu since 04, and even written a couple tutorials, but this one has me stumped. It's very frustrating, when I've always been able to fix anything in the past.

I'm thinking I have corrupt files somewhere that just won't allow me to install wine no matter what. It's probably easier for me to reinstall than spend days trying to figure it out. I can have my computer back up and running in a couple hours, doing a fresh install. Only god knows why this happened in the first place, but stranger things have happened. Take care and good luck.

---

### Post by AlexanderDGreat on 2010-02-17
Hey sir, have you tried this forum? It says something that a line must be removed because of old versions of wine. It's also marked solved: [http://ubuntuforums.org/showthread.php?t=1340351]("http://ubuntuforums.org/showthread.php?t=1340351")

---

