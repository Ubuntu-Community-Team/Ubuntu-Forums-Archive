---
title: "do you like the alt+f2 run dialog?? i don't.."
date: 2009-01-07
forum: The Cafe
---

### Post by smif1984 on 2009-01-07
Hi everybody,
I would like you to try a simple but very effective program i made during christmas holidays. It is a powerful substitute for the alt+f2 run dialog built-in into Gnome. Let me be clear:  tab completion can be improved and history control as well. So i did it.  

[http://www.gtk-apps.org/content/show.php/run?content=96644](http://www.gtk-apps.org/content/show.php/run?content=96644)

The program needs only python 2.5 to run and it is rapidly changing so check out often if there is an update available. 

PLEASE! report bugs and missing features to make me understand how to improve it further.. Suggestions are welcome!! 

See ya!!

UPDATE: web page updated!
UPDATE: a new version is out, try it and let me know!!

---

### Post by tjwoosta on 2009-01-07
nice job


i think this will make a perfect substitute for fbrun with my fluxbox install

---

### Post by bryonak on 2009-01-07
Just tried it, job well done!
I've attached a screenshot for those who want to see a direct comparison.


What I like about it as compared to Gnome's run:
Startup speed
"cycling" by tabbing
Running from history
"in terminal" and "as root" buttons, plus being able to do so with Ctrl/Shift


What I prefer in Gnome's run as opposed to yours:
When entering paths and there is only one available, Gnome's run "suggests" it by showing the rest of the path highlighted.
The list of applications to choose from. I know it's not easy to implement and probably not easy on the resources either, but it's still a great visual feedback. This is the very point that makes me still use Gnome's run instead of yours.


What I really dislike in Gnome's run (as in "do not repeat"):
It's slow. This seems to be coupled with Gnome's start menu lag after"a fresh boot. Alt+F2 before opening the start menu for the first time has a lag similar to the one of the start menu, but if I do it after clicking on the menu, it's usable instantly.


Additional suggestions:

Cycling by tabbing:
1. could you make the "suggested text" after the cursor highlighted? So it's easier to see what I wrote myself and what is "appended" and can be changed by cycling... I'm aware that the cursor staying at the same position indicates this, but IMO this could improve it.
2. could be complemented with said "list of applications to choose from", where the currently selected application is highlighted.
*EDIT:* 3. You could improve the sorting/autocompletion of the cycling: "gedit /etc/X11/xo<tab>" gives first xorg.conf~, then xorg.conf.xxxx (those changed by video driver installations and similar) and then the actual xorg.conf

Customizability: a settings dialog where you could turn off said application list and other things would be awesome. Though this may come as the tool matures, it's good to keep it in mind while designing the code.
This could also offer an option to turn off those X matches in path, Y in history numbers, because I have yet to decide whether I find them informative/helpful or too much clutter.

---

### Post by smif1984 on 2009-01-07
Hi, thanks for taking the time to try my software!
Well, actually the todo list is very long and i really would like to improve as much as i can. 

1) highlighting the "suggested" text could be a good idea which i already thought. It was initially difficult to implement such a feature because of the "weird" behaviour the highlighted text introduces when using left and rigth arrows. Actually i've just started with pygtk and at the beginning i left this feature apart because i focused on implementing the command completion. I initially thought to use two colors for the prefix, which is then completed, and the appended text, but it seems that this cannot be easily done, so i left it apart.

Anyway i'll try to implement this feature as i understand how to program it!!

2)Yes, it lacks some visual appeareance. I know it, but as this project is very young (two weeks), i focused more on more important stuff. It is however a must to do.

3)A dialog where to change some settings could be a nice feature.. I'll definitly think to it in the future!

Keep in touch!!

---

### Post by bryonak on 2009-01-07
You might want to keep an up-to-date "feature list" (as compared to Gnome's run) and "todo list" in your first posting, so people following your nifty tool can see the progress.


> **smif1984 said:**
> 
Keep in touch!!
sure ;)

---

### Post by smif1984 on 2009-01-16
HI, a new version is out, try and let me know. Also i've put a new screenshot to show you what i'm doing right now...See you..

---

### Post by Nepherte on 2009-01-16
This is the error I get when running the command in a terminal:
```
Traceback (most recent call last):
  File "/home/bart/.run/run.py", line 340, in <module>
    app=rundialog()
  File "/home/bart/.run/run.py", line 72, in __init__
    binaries = os.listdir(path)
OSError: [Errno 2] Bestand of map bestaat niet: '/usr/bin/perlbin/site
```

---

### Post by cardinals_fan on 2009-01-16
Dmenu renders run dialogs obsolete (for me).

---

### Post by smif1984 on 2009-01-16
> **Nepherte said:**
> This is the error I get when running the command in a terminal:
```
Traceback (most recent call last):
  File "/home/bart/.run/run.py", line 340, in <module>
    app=rundialog()
  File "/home/bart/.run/run.py", line 72, in __init__
    binaries = os.listdir(path)
OSError: [Errno 2] Bestand of map bestaat niet: '/usr/bin/perlbin/site
```

Hi thanks for trying my sofware,
can you translate what does "Bestand of map bestaat niet" means??

---

### Post by smif1984 on 2009-01-16
> **cardinals_fan said:**
> Dmenu renders run dialogs obsolete (for me).

Can you please explain why??

---

### Post by Nepherte on 2009-01-16
> **smif1984 said:**
> Hi thanks for trying my sofware,
can you translate what does "Bestand of map bestaat niet" means??
Hehe sure, didn't see it wasn't all in English. The translation is "File or directory doesn't exist" so I guess I have some unmet dependency. It seems to point to some perl thing although I have perl installed.

---

### Post by Nepherte on 2009-01-16
Here's some additional information:
```
[bart@diana perlbin]$ pwd
/usr/bin/perlbin
[bart@diana perlbin]$ ls
total 4
drwxr-xr-x 2 root root 4096 jun 30  2008 core

```

---

### Post by damis648 on 2009-01-16
The shortcut keys do not work for compiz users, so I modified the install script. I also made an uninstall script. :popcorn:

---

### Post by Hells_Dark on 2009-01-16
I love gmrun.

---

### Post by bryonak on 2009-01-16
Just gave it another try: you've improved nicely.
The interface is friendlier and less cluttered.

Now the only thing needed to make it really rock is a list ala gmrun (which is written in C and really fast, but also quite plain):
[IMG]http://www.ubuntugeek.com/images/gmrun/2.png[/IMG]



> **smif1984 said:**
> [QUOTE=cardinals_fan;6559590]Dmenu renders run dialogs obsolete (for me).

Can you please explain why??[/QUOTE]

DMenu is a very lightweight text based launcher that gives you a list of applications to launch based on what you typed.
Gnome Do is the feature-heavy lots-of-eye-candy counterpart. (There's others like Launchy, Katapult,..)

Many people prefer such launchers to the classical run dialog (or to docks, but that's another story), although there is still room for diversification.
I don't think that you can or should compete with Gnome Do, but instead write a fast, easy to use and helpful tool.
I guess your target audience are rather people who don't want to run Compiz for Gnome Do (or simply don't want their ressources hogged) but need a functional, efficient but still "graphical" way to launch their apps.

---

### Post by cardinals_fan on 2009-01-16
> **smif1984 said:**
> Can you please explain why??
1. The run box requires that I enter the whole command.  When it has autocompletion, it is usually awkward with the keyboard, necessitating the use of a mouse (your app may be better).  With dmenu, I just call it (Home-p on my ratpoison config) and start typing.  It filters automatically.

2. Dmenu is extremely minimal and light.

3. Dmenu is very configurable for many different purposes.  [This]("http://urukrama.wordpress.com/2008/07/09/dmenu-script-for-configuration-files/") is just one example.

---

