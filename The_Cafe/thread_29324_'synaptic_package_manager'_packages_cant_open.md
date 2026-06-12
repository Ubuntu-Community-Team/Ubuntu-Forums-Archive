---
title: "'synaptic package manager' packages cant open"
date: 2005-04-23
forum: The Cafe
---

### Post by dwkreutzer on 2005-04-23
[SIZE=1]1[/SIZE][FONT=Arial]arial[/FONT] i can download packages from synaptic, but i cant open them! do they automatically get put in applications or whatever? because if they do, for some reason it doesn't work. tell me if there's some obvious thing i'm missing, because i'm pretty much the newest noob ever.

---

### Post by Brunellus on 2005-04-23
[QUOTE=dwkreutzer][SIZE=1]1[/SIZE][FONT=Arial]arial[/FONT] i can download packages from synaptic, but i cant open them! do they automatically get put in applications or whatever? because if they do, for some reason it doesn't work. tell me if there's some obvious thing i'm missing, because i'm pretty much the newest noob ever.[/QUOTE]
 synaptic downloads and installs packages (and any dependencies) automatically.  

Mark all the packages you wish to install, and then click ACCEPT.  a dialog will pop up with the number of packages being installed and so on. click OK, then let apt do its thing.  

Much cooler than RPM, eh?

---

### Post by jimmy on 2005-04-24
okay, i did that, but where does it put them in the computer after i've downloaded them?

---

### Post by HungSquirrel on 2005-04-24
[QUOTE=jimmy]okay, i did that, but where does it put them in the computer after i've downloaded them?[/QUOTE]
 The answer is: a number of places.  It puts configuration files in /etc, binary files in  /usr/bin, libraries in /usr/lib, and so on.  To see where a package has installed its files, in Synaptic select the package, click Properties, and go to the Installed Files tab.  You'll see that it has put its stuff in lots of differen directories.

---

### Post by TravisNewman on 2005-04-24
usually RUNNING the programs is just a matter of typing a command or creating a launcher. Unfortunately, a lot of packages in Universe don't give you a launcher, so it can be confusing  at first.

---

### Post by seven on 2005-04-24
In most cases, just write the name of the programs
(if you install xchat, run xchat, if you installed gaim run gaim...)
To get all the files that the package installed , find it in synaptic 
double click it -> properties -> "Installed Files"

---

### Post by jimmy on 2005-04-25
okay, thanks everybody. i hope at least one of those ways works

---

