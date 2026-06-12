---
title: "switching DE/WM  experiment in Utopic = turbo unity!"
date: 2014-04-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-24
As usual (me and my experiments) ha:) I ventured to see if I could switch desktops from a terminal running out of Unity desktop. The purpose of the experiment  was to see if I could find a quicker macro to change DE without having to log off and log back in. I used fvwm-crystal. The experiment was a success   (with the help of a little terminal reminder called '--replace') .

 Here is experiment.

> 
Experiment:

To see if I could change DE/WM from termimal

Open terminal in Unity session. Ctrl+Alt+t

install fvwm-crystal

sudo apt-get install fvwm-crystal

I then entered fvwm-crystal at the command line in terminal that was Running in Unity.  An error came up and said it could not load "try --replace. I then entered fvwm-crystal -replace . The desktop then switched to fvwm-crystal (no log off/ log on required). All worked well. ( I just ignored the terminal errors scrolling by in the script).  I then entered 'unity' at the prompt in the terminal and the Unity desktop opened (while ignoring errors in terminal and worked exceptionally well with he exception that Unity was now in some sort of turbo-mode with the dash and loading of programs working much faster than normal after initially logging on. This all done in the newly converted Utopic Unicorn.


How is this topical to Utopic Unicorn?

It may come in handy with this new cycle as we explore and devise new tests for mir, unity8 etc and , also a surprise to me, I don't have to log off and log back in saving some downtime. The other added bonus is turbo-unity (as I call it) and I am wondering why this phenom is taking place.  One could assume that when I '--replace (d) unity with fvwm-crystal and back again that unity-desktop was already loaded in memory but I do not think this is the case.

```
ventrical@ventrical-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ventrical@ventrical-desktop:~$ 



```

---

### Post by ventrical on 2014-04-24
I think something happened to unity and it may have nothing to do with the experiment above.  After a hard reboot I still have this turbo-unity on this somewhat older Intel Core2Duo machine. Before I changed the sources list over to /utopic/ it was running more or less run-of-the-mill type speed.  There was this  sort of delay or log-jam but I expected it because it is an older machine. However, the unity-desktop dash and panel and programs are all working as if I had an SSD drive on this tower.
 Keeping at it ... I'll report back in as stuff happens :)

---

