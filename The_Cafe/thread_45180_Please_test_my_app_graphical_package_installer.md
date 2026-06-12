---
title: "Please test my app: graphical package installer"
date: 2005-06-29
forum: The Cafe
---

### Post by psychicdragon on 2005-06-29
I've been learning to program in python using gtk and glade recently as it seems very popular in the ubuntu and gnome community. So I figured for my first real program I would try to make something useful.

I've made a simple program that will allow you to install a deb package by double clicking it in nautilus.

Here's a screenshot:
[[IMG]http://img247.echo.cx/img247/8237/screenshot0gs.th.png[/IMG]](http://img247.echo.cx/my.php?image=screenshot0gs.png)

This is a really preliminary version, I just started working on it today, but I would like some feedback to see if I'm on the right track.

Currently there is no threading (like sapo's app  :grin: ) so it will lock up for a couple of seconds while installing, this is my main priority for the next version. It will also generate an error message that makes no sense if you try to install a package with unmet dependencies, I'm also planning to correct this.

Anyway, try it out and please give me some feedback.

**Installation instructions:**

Download and then extract the attached archive

then run these commands:
```
sudo cp debinstaller /usr/bin
sudo chmod 755 /usr/bin/debinstaller
sudo mkdir /usr/share/debinstaller
sudo cp debinstaller.glade /usr/share/debinstaller
``` 
Select a deb file in nautilus
right click > Properties > Open With > Add
Use a custom command > debinstaller

Now you can double click on a deb in nautilus and it should launch the program.

---

### Post by gamehack on 2005-06-29
One suggestion, make a nautilus extension when you right-click on deb, let it display an option like "Install" or something like this and when clicked, let it start your program.

Regards

---

### Post by benplaut on 2005-06-29
does this hook into the repos to solve dependancies? (like Debins)

---

### Post by sapo on 2005-06-29
nice idea man!

If you want i can try to help hacking something in it  :grin:

Edit.. it worked.. give me an error but was cause the package was already installed...

nice idea.. very usefull!  :grin:

Print the error on a msg box would be nice.. :D

---

### Post by psychicdragon on 2005-06-29
[QUOTE=benplaut]does this hook into the repos to solve dependancies? (like Debins)[/QUOTE]In the future I would like to see it do this. Right now it's something I hacked together in an afternoon.

What is debins exactly? It doesn't seem to be in the repos. If there's already an applicaton that performs this function I wouldn't want to waste my time duplicating someone elses efforts.

EDIT:
[QUOTE=sapo]nice idea man!

If you want i can try to help hacking something in it  :grin:

Edit.. it worked.. give me an error but was cause the package was already installed...

nice idea.. very usefull!  :grin:

Print the error on a msg box would be nice.. :D[/QUOTE]Thanks for trying it out. That should be easy to implement but for today I'm done coding. I think I'm off to bed.

---

### Post by UbuWu on 2005-06-29
Very nice!

---

### Post by bored2k on 2005-06-29
I like your Terry Bogard and Blue Mary wallpaper :D

---

### Post by benplaut on 2005-06-29
[QUOTE=psychicdragon]What is debins exactly? It doesn't seem to be in the repos. If there's already an applicaton that performs this function I wouldn't want to waste my time duplicating someone elses efforts.[/quote]

it was suggested, and released, here:

[http://www.ubuntuforums.org/showpost.php?p=158724&postcount=49](http://www.ubuntuforums.org/showpost.php?p=158724&postcount=49)

might be good to just improve and update Debins, rather than starting from scratch.

Note: i'm not usre if debins actually works, i haven't tried it myself  :roll:

---

### Post by sapo on 2005-06-29
> 
How it works:
Debins begins by creating a miniature repository in your root directory, to where it copies the .deb to be installed. It then adds this repository to your source.list, updates, and apt-get installs it. Integration with apt made easy!


lol... nice idea to integrate with the apt-get :D

---

### Post by UbuWu on 2005-06-30
And how about gdeb, which is also mentioned in that thread? Anyone tried it?

---

### Post by psychicdragon on 2005-06-30
I just tried out gdeb. It seems to be at about the same point as mine but I was never actually able to install a package with it. If i run it from the console I get an error like this:```
error:
 command: x-terminal-emulator -e /bin/sh -c \"/usr/bin/dpkg -i bittorrent-4.0.2.linux_i686-2_all.deb && echo Installation done || echo Installation failed;echo Press enter to continue; read DISCARDED\"
 user: root
```I was able to install a package with debins. It seems to have a lot more features than mine so I'm not sure it's worth continuing on at this point.

---

### Post by UbuWu on 2005-06-30
[QUOTE=psychicdragon]I just tried out gdeb. It seems to be at about the same point as mine but I was never actually able to install a package with it. If i run it from the console I get an error like this:```
error:
 command: x-terminal-emulator -e /bin/sh -c \"/usr/bin/dpkg -i bittorrent-4.0.2.linux_i686-2_all.deb && echo Installation done || echo Installation failed;echo Press enter to continue; read DISCARDED\"
 user: root
```[/QUOTE]

Looks like it needs the xterminal package, although that is not listed as a dependency. Do you have that installed?

---

### Post by dolson on 2005-09-12
[QUOTE=UbuWu]Looks like it needs the xterminal package, although that is not listed as a dependency. Do you have that installed?[/QUOTE]

Digging up old threads, I know, sorry. But no sense starting a new one, right?

gdeb works a charm in Debian, but I just installed Ubuntu Breezy Preview, and gdeb does not work. I get the exact same thing as above. Yes, I have xterminal installed (even though x-terminal-emulator is not a part of the xterminal package, but is also installed on my system).

There's really no good reason that gdeb should be broken, and if I knew how to add bullets to Battle Pong, I'd fix gdeb myself. ;)

---

