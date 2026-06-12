---
title: "How to install latest version of WINE on 8.10 Intrepid Ibex"
date: 2009-04-09
forum: Wine
---

### Post by aaroncoffman on 2009-04-09
Follow instructions [**_here_**]("http://ubuntuforums.org/showthread.php?t=624644") but use the following for step 4.

```
## Wine, Ubuntu Intrepid Ibex (8.10)
deb http://wine.budgetdedicated.com/apt intrepid main
deb-src http://wine.budgetdedicated.com/apt intrepid main 
```

Have a fantastic day!

---

### Post by anjilslaire on 2009-04-09
Welcome to the forums :)

Or, just follow the official install howto from WineHQ:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

> 
First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following into your terminal:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - 
```

Next, add the repository to your system's list of APT sources:

For Ubuntu Intrepid (8.10):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
``` 

Then update APT's package information by running 
```
sudo apt-get update
``` You can now install Wine normally or by typing '
```
sudo apt-get install wine
``` into the terminal.


---

### Post by aaroncoffman on 2009-04-09
> 
Or, just follow the official install howto from WineHQ:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
Ugh! Sorry if I missed that somewhere! 
Thanks! obviously I am new to linux so I'm still learning commands! I do enjoy learning tho'!
> Welcome to the forums 
Thanks!

---

