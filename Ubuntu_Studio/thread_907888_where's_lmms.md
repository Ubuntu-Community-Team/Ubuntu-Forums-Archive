---
title: "where's lmms?"
date: 2008-09-01
forum: Ubuntu Studio
---

### Post by raucous on 2008-09-01
So im running hardy and i just installed LMMS but he sure is elusive. gone 'n hid somewheres in my os n even my search engine cant find him. used the ol' synaptic but looks like i need a new myelin sheath er something - done slipped away on me. i'd be much obliged if someone could help me find the sucker. golly, i done seen the question asked before but aint nobody got an answer. 

best regards, 
moses humphrey harrold isaiah whitehouse the umpteenth.

---

### Post by raucous on 2008-09-01
got myself some wine though!

---

### Post by Stochastic on 2008-09-01
open terminal
type ```
lmms
```
hit enter


where else has this been asked and not answered?

p.s. type ```
locate lmms
``` to see a list of the files on your computer with 'lmms' in the filename

---

### Post by thorgal on 2008-09-02
you can also check this in synaptic :

highlight the installed package, click on properties in the top menu, select the "Installed files" tab and you will see all files that this package installed on your system. The executable binary will most likely be in /usr/bin

If it does not show up in your desktop manager, chances are that the package maintainer did not provide the little bit of extra installation procedure that should notify the desktop manager of the newly installed app.

---

### Post by littletinman on 2008-09-02
just add a launcher on your menu and type > lmms for the command

---

### Post by tuxxy on 2008-09-02
Once you have added the launcher to your menu, click the image box and it should auto select the lmms icon for you

---

### Post by raucous on 2008-09-07
ok, I'm halfway there. 

I can now type LMMS into terminal which opens the program, but if I close the terminal LMMS closes as well. I also found signs of Panel - Launcher but i cant open it, so I dont know if that would help me create the icon.

Now what?

Thanks in advance...

---

### Post by Stochastic on 2008-09-08
right click anywhere on your desktop,
choose: Create New Launcher
in the 'Command' field, enter: lmms
choose which ever icon you want to use, then close the dialog

---

### Post by paulg on 2008-09-08
With Gnome and [I think] KDE (can someone confirm this?) hit alt+F2 to open a 'single use' terminal command line to run a program that might not have a launcher for or might be faster than opening a program several menus deep in your launcher. It will remember the most commonly used programs in a pull down list. 

And since I actually use FluxBox, for those Box users out there, in a convenient location (such as near the top of your first menu) add an item to run the application 'fbrun' which gives you the same functionality with a right click of the mouse.

---

### Post by thorgal on 2008-09-09
> **raucous said:**
> ok, I'm halfway there. 

I can now type LMMS into terminal which opens the program, but if I close the terminal LMMS closes as well. I also found signs of Panel - Launcher but i cant open it, so I dont know if that would help me create the icon.

Now what?

Thanks in advance...

hehe, that's something you have to learn from unix ;)
So let me give a crash course about processes and terminal.

if you want to launch a program from the terminal and escape the process binding to the terminal in order to get the command prompt back (which will allow you to kill the terminal without killing the program you launched), you need to add & after the program command, in this case :

```

lmms &

```

if you forget the & and nevertheless want to escape the terminal binding of the process manually, you need to know the other unix trick :

so let's say you typed lmms in the terminal, now you have to type Ctrl-z (press the control key and z at the same). This will suspend the process. To put it in the "background" of running process (to get back the terminal prompt without killing the program, you type
```

bg

``` 

if you want to put back the process in the "foreground", you type
```

fg

```


so in general, when you launch a program from a terminal without putting in the background of running processes :

```

my_program

```

if you want to put it in the background of running processes at launch time :

```

my_program &

```

if you want to put it back in the foreground
```

fg

```

put it back in the background:

```

Ctrl-z
bg

```

when in the foreground, you want to suspend it only ?
```

Ctrl-z

```
Note: you can suspend ANYTHING. Let's say you're copying a huge file over to a local or remote directory, you can ctrl-z it if you started the copying from the terminal (whether you used cp or scp or whatever terminal copying utility). To resume, use 'fg'. Very convenient I tell you :)

still in the foreground, want to kill it ?
```

Ctrl-c

```

when in the background, want to kill it anyway ?
```

kill -9 `pgrep my_program`

```


all this geekish unix shell stuff is REALLY useful! there is of course much much more ...

---

### Post by paulg on 2008-09-09
Thanks thorgal, nice little summary there and a couple things I didn't know.

A little further off topic but I'll share what I've been using lately in place of backgrounding. I use a program called 'screen'. There's a great summary of 'screen' and it's common uses at [debian-administration.org here]("http://www.debian-administration.org/articles/34"). Think of it as a window manager for terminals. If your remote terminal session gets terminated or you log out of an X session and you were running something with 'screen', the 'screen' terminal will be backgrounded and you can reconnect after logging back in. Great for terminal programs that like to run in the foreground or take a while to complete (compiling, updating, downloading etc).

To get my post back on topic, another way to search for/locate files on a system is the find command.

```
find . -name *.pdf 
find /. -name "*vacation*"
find /home/username/. -name .bash*
```
[LIST=1]
[*]The first example will find all files or folders in the current directory (searching recursively into sub folders) that end with .pdf.
[*]The second example will start at the root folder and search for all files/folders on a system that contain the word "vacation" in the name.
[*]The third example will start in username's home directory (again searching sub directories/files recursively - you get the picture) and return [hidden] folders/files that start with .bash.
[/LIST]

I should also mention that this is case sensitive. The first example for instance will not return files that end with ".PDF" so you'd need to search for these separately.

---

### Post by raucous on 2008-09-14
hey i got the icon, and im running it well. thanks all.

so what out there can go toe-to-toe with reason and fruityloops in the linux world?

lmms looks like it has potential but it's a little cheesy.

regardless, thanks for the insight and im off to take a swing at lmms.

---

