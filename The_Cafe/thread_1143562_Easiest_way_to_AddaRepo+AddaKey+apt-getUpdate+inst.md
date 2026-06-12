---
title: "Easiest way to: AddaRepo+AddaKey+apt-getUpdate+installSomething"
date: 2009-04-30
forum: The Cafe
---

### Post by juancarlospaco on 2009-04-30
[CENTER][B][SIZE="3"]Easiest way to: 
AddaRepo+AddaKey+apt-getUpdate+installSomething[/SIZE][/B][/CENTER]

Hi!!! from Argentina, *(so dont complain for my english :) )*
i been reading Blogs and i think they don't make things easy for Beginners,
i mean..., to install something on Windows just clicking a link,
the same with Ubuntu, but no one uses easy methods.

Example, Add a Repo+Add a Key+apt-get update+install a Theme on Blogs:

"[B][COLOR="DarkGreen"]Go to Terminal and type:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1781bd45c4c3275a34bb6aec6e871c4a881574de

then run :

sudo gedit

and open the file /etc/apt/sources.list and add this line at the end:

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

save and close. 

now run on Terminal:

sudo aptitude update

when finish run:

sudo apt-get install aquadreams-theme[/COLOR][/B]"



New Users *(maybe windows users)* read and feel like:
 --->:confused:--->:(--->#-o--->](*,)--->[-X


I think to make installation instructions more begginer-user friendly,
begginer users don't know what's *"keyserver.ubuntu.com"* or *"ppa"*, 
and don't want to learn, just want easy to follow steps to install things like on Windows,
and Ubuntu can make it easy, just like that *(**Working Example**)*:

**[COLOR="DarkGreen"]Jaunty 9.04:**
**1)**Copy the next line, press ALT+F2, paste on the upcoming window, and click "Run":[/COLOR]
```
**xterm -e "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1781bd45c4c3275a34bb6aec6e871c4a881574de ; sudo wget http://mac4deb.googlepages.com/gkrepo -O /usr/bin/gkrepo ; sudo chmod --verbose +x /usr/bin/gkrepo ; sudo gkrepo deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main ; sudo apt-get update"**
```

[COLOR="DarkGreen"]**2)**Click on the Screenshot of the desired theme to Install.[/COLOR]

[[IMG]http://i243.photobucket.com/albums/ff135/Ubuntips/headtheme-aqua.jpg[/IMG]]("apt:/aquadreams-theme")

[[IMG]http://i243.photobucket.com/albums/ff135/Ubuntips/wild-shine-presentation.jpg[/IMG]]("apt:/wild-shine-theme")



Working Example 2, Add Medibuntu:

**[COLOR="DarkGreen"]Jaunty 9.04:**
**1)**Copy the next line, press ALT+F2, paste on the upcoming window, and click "Run":[/COLOR]
```
**xterm -e "sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update ; sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list ; sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update"**
```

[COLOR="DarkGreen"]**2)**[Click here to install google earth]("apt:/googleearth")[/COLOR]




[LIST]
[*]**[SIZE="3"]Anyone knows a more easy method to install???[/SIZE]**
[*]**[SIZE="3"]What do you think???[/SIZE]**
[/LIST]
[SIZE="1"](without using strange things like klik*(is dead)*,0install*(few apps)*,etc just using the power of APT)[/SIZE]

---

### Post by Ocxic on 2009-04-30
Use Software sources under the System->admin menu

---

### Post by billgoldberg on 2009-04-30
I use this, for example here with this command to install most codecs available for Ubuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

But in general I don't think it's a good idea.

Such type of commands seem super complicated, while they aren't, and could turn off people.

If you give them a few lines to copy/paste and explain what each line does, they might learn something or at least understand what is going on and will not be afraid of the CLI anymore.

---

### Post by Polygon on 2009-04-30
i really dont like how complicated it is to add a third party repo now. In addition to adding the lines to software sources, you have to open a text editor, copy and paste the key into it, save it somewhere, then go to authentication and add the key. while i can do it from the command line, the syntax is a bit weird to learn, and especially for adding a key, i have no idea where to get that hexadecimal number that comes after keyserver.ubuntu.com...

---

### Post by juancarlospaco on 2009-04-30
> **Ocxic said:**
> Use Software sources under the System->admin menu

Common people don't understand the Software Sources Window,
they want to click something on the website and get the stuff installed.
And sometimes just click, *"Close"* on the Refresh Repo pop up, 
and can't install the app before.


> **billgoldberg said:**
> I use this, for example here with this command to install most codecs available for Ubuntu:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```
But in general I don't think it's a good idea.
Such type of commands seem super complicated, while they aren't, and could turn off people.
If you give them a few lines to copy/paste and explain what each line does, they might learn something or at least understand what is going on and will not be afraid of the CLI anymore.

This don't work on the *"Run Popup"* (its a single command launch), users need to use Terminal,
and New Users don't like to open a Terminal to install things,
New users don't want to learn, just want to install a program to work with it,
in example, on Windows no one knows whats the diference between an *" .exe"* and a *" .msi"*,
they just want to install and use, users want easy to use install method.


> **Polygon said:**
> i really dont like how complicated it is to add a third party repo now. In addition to adding the lines to software sources, you have to open a text editor, copy and paste the key into it, save it somewhere, then go to authentication and add the key. while i can do it from the command line, the syntax is a bit weird to learn, and especially for adding a key, i have no idea where to get that hexadecimal number that comes after keyserver.ubuntu.com...

The Hexa key is ALWAYS from proyect documentation :P
the same steps to do it via CLI, but with semicolon *" ; " *or *" && "*


I have been passed a lot of people to Ubuntu, and when they are new users,
this is the problem, they say... 
[LIST]
[*]*" Ubuntu allways need Terminal to install things, just like D.O.S. on 1980. "*
[*]*" I don't want to install a program on a presentation using Terminal, is not nice to public. "*
[*]" i don't think to say to my clients how to install things using a Terminal, and say before it's a new modern system better than Windows Vista "
[/LIST]


so i use the recipe:

**[COLOR="DarkGreen"]Ubuntu-Release-Here[/COLOR]**:
1)Copy the next line, press ALT+F2, paste on the upcoming window, and click "Run":
Code:

xterm -e " **[COLOR="DarkGreen"]steps to add the repo, add the key, refresh repos, separated by ;[/COLOR]** "

2)Click on the Screenshot of the desired program to Install.


and users feel like:
:-k--->:o--->:D--->=D>

---

