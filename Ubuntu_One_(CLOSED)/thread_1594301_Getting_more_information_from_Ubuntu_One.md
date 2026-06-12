---
title: "Getting more information from Ubuntu One"
date: 2010-10-12
forum: Ubuntu One (CLOSED)
---

### Post by duanedesign on 2010-10-12
There are a couple options for getting more info.

**[COLOR="Red"]u1sdtool[/COLOR]**
From the command line you can get the number of items in the queue with these commands run in the terminal:

```
u1sdtool --waiting-metadata | wc -l
```

and

```
u1sdtool --waiting-content | wc -l
```

you can track progress as the numbers get smaller. It syncs metadata first (folder structure) then content. You can remove the '| wc -l' from the command to get more details about the items in the queue.

**NOTE:** In Natty(11.04) and Oneiric(11.10) these commands have been combined into one command.

```
u1sdtool --waiting | wc -l
```

A good wiki page that provides information on using u1sdtool to get more info from Ubuntu One.
[Ubuntu One Client Control]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl")

**[COLOR="Red"]magicicada[/COLOR]**
There is also a project called [Magicicada]("https://launchpad.net/magicicada") that is a GUI for the Ubuntu One syncdaemon. It allows you to connect/disconnect and see the items in the queue. You can install it with these commands in a terminal:

For Lucid you will have to add the ppa. If you are on maverick and newer the package is in the repository and you can skip to the next command.
```
sudo add-apt-repository  ppa:chicharreros/ppa
```
install
```
sudo apt-get update; sudo apt-get install magicicada
```
You can launch the application from Applications > Accessories > Magicicada

**[COLOR="Red"]ubuntuone-indicator[/COLOR]**
Lastly there is a project that brings back the indicator some may remember from early versions of Ubuntu One. You can install it with these commands run in the terminal:

add the ppa
```
sudo add-apt-repository ppa:rye/ubuntuone-extras
```
install
```
sudo apt-get update; sudo apt-get install ubuntuone-indicator
```
to run the app issue this command
```
ubuntuone-indicator
```

You can add this command to System > Preferences > Startup Applications.

thank you,
duanedesign

---

