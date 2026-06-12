---
title: "Software Center &amp; WINE"
date: 2012-04-19
forum: Ubuntu Studio
---

### Post by dik909 on 2012-04-19
My goodness !  the simplest of things is not appearing in 'Ubuntu Software Center' for me:  the SEARCH bar.  

Am I mistaken in thinking that there was once a search function available when searching for a program in the software center ?

------------------

WINE is just simply not showing up when I search for it; I can find the 'uninstall' and 'configure' portions of the program, but the main program is not visible/searchable.  What gives ??

---

### Post by josephmills on 2012-04-19
> **dik909 said:**
> My goodness !  the simplest of things is not appearing in 'Ubuntu Software Center' for me:  the SEARCH bar.  

Am I mistaken in thinking that there was once a search function available when searching for a program in the software center ?

------------------

WINE is just simply not showing up when I search for it; I can find the 'uninstall' and 'configure' portions of the program, but the main program is not visible/searchable.  What gives ??

Hello there lets look at what repo you have enabled on your system. 
please open lxterminal
```
cat /etc/apt/sources.list
```
also have you have tried to look under apt for them ? 

Joseph

---

### Post by kc1di on 2012-04-19
go to software center edit tab and look under software sources (it's at the bottom of the list) make sure you have a checkmark in the box in front of Universe.  I would also make sure that multi universe is checked also.

Wine shows up here no problem.

---

### Post by dik909 on 2012-04-19
> **kc1di said:**
> go to software center edit tab and look under software sources (it's at the bottom of the list) make sure you have a checkmark in the box in front of Universe.  I would also make sure that multi universe is checked also.

Wine shows up here no problem.

both were checked - still no 'search' abilities.

---

### Post by dik909 on 2012-04-19
> **josephmills said:**
> Hello there lets look at what repo you have enabled on your system. 
please open lxterminal
```
cat /etc/apt/sources.list
```
also have you have tried to look under apt for them ? 

Joseph

i did what you suggested, but am not sure what i'm supposed to be looking for after that...??

---

### Post by jejeman on 2012-04-20
Copy output here, for us to see.

---

### Post by kc1di on 2012-04-20
> **dik909 said:**
> both were checked - still no 'search' abilities.
go to a terminal and enter the following one line at a time

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update

```
if you get any error messages doing the apt-get update please post them here so we can see what's happening.

then try searching in software center again.

If it still does not work try this again from the terminal:
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by kc1di on 2012-04-20
if none of the above works for you lets just skip software center for now and get wine installed for you.

In the terminal type the following commands:

```
sudo apt-get update
sudo apt-get install wine
sudo apt-get install synaptic
```

---

