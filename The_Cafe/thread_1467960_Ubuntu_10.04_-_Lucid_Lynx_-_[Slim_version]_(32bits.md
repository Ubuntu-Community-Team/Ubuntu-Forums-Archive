---
title: "Ubuntu 10.04 - Lucid Lynx - [Slim version] (32bits&amp;64bits)"
date: 2010-05-01
forum: The Cafe
---

### Post by tikilou on 2010-05-01
_**Ubuntu 10.04 - Lucid Lynx - *Slim***_

Hello, I have build a slim version of ubuntu , without additionnaly software (she don't have mono, fspot,  rythmbox... Look the screenshots :) )

The 32-bit version should work without errors, I have the machine for testing.


For the 64bit version, I could not test because I dont have a compatible  processor for this, so I ask you to be indulgent, and say me an error...

I  also want to especially thank Gage, which left me with access via an  SSH tunnel to a machine in order to make this build with him computer,  otherwise it would not have been possible. ;)

_**[COLOR=mauve]Download :[/COLOR]**_

[[COLOR=green]**Download Ubuntu 10.04 Lucid Lynx - LTS - Slim - i386**[/COLOR]]("http://mug.gs/1/dBBiZ1")

[[COLOR=red]**Download Ubuntu 10.04 Lucid Lynx - LTS - Slim - amd64**[/COLOR]]("http://%3Cfont%20color=%22red%22%3E%3Cb%3EVersion%2064bits%3C/b%3E%3C/font%3E") {please wait}


_**[COLOR=mauve]Screenshots :[/COLOR]**_

[[IMG]http://pix.louiz.org/upload/thumb/1272679405.png[/IMG]]("http://pix.louiz.org/?img=1272679405.png")  [[IMG]http://pix.louiz.org/upload/thumb/1272679425.png[/IMG]]("http://pix.louiz.org/?img=1272679425.png")  [[IMG]http://pix.louiz.org/upload/thumb/1272679468.png[/IMG]]("http://pix.louiz.org/?img=1272679468.png")  [[IMG]http://pix.louiz.org/upload/thumb/1272679483.png[/IMG]]("http://pix.louiz.org/?img=1272679483.png")

All screens are in French, but all languages are available, as usual ! ;)



As you can see, it's light, all unnecessary services and applications have been uninstalled.

[COLOR=#000000]This  idea came to me a slim version of the large number of people finding  less and less on their behalf in the version "fat" of ubuntu, tired of  having to uninstall everything to reinstall their software usual, is  stuck with having a netinstall [/COLOR]and  commands instead of something direct loan, and often quite anxious about  the remarks of some of their promised everything on Debian, they are  keeping it often to remind them that Debian is not Ubuntu, it don ' has  not necessarily all packages, interoperability with the PPA repository, or the  graphical tools, and it requires many times the shell.


**_Two errors are found in the 64bits version !_**
```
Couldn't update ICEauthority file /var/lib/gdm/.ICEauthority
``````
There is a problem with the configuration server.
/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256
```**_For repair it, launch this command :_**
   ```
sudo chmod 755 /etc/gconf/gconf.xml.* && cd /var/lib/ && sudo chown -R gdm:gdm gdm
```[FONT=Verdana]
[/FONT]
[COLOR=#000000]Please be patient, I can't access on a computer 64bits to regenerate the 64bit iso and upload it actually :)
[/COLOR]


Ps:  KDE version (Kubuntu slim) is expected soon, and a version LXDE (Lubuntu  slim) will come when it will be available in stable version. 

Ps2 : I'm very sorry for my english, he is not terrible... (Si un Français passe par là et propose une traduction potable...  )

Ps3 : Clean packages are listing [here]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3435922#p3435922")

---

### Post by praveesh on 2010-05-01
Sounds interesting . How much is the size of iso ?

---

### Post by tikilou on 2010-05-01
> **praveesh said:**
> Sounds interesting . How much is the size of iso ?

[COLOR=#000000]The iso size is[/COLOR][COLOR=#000000] approximately 520Mo ([/COLOR][COLOR=#000000]some differences between 32&64bits version)[/COLOR][COLOR=#000000] [/COLOR] :)

But on the installation, you win approximately 1Go ! ;)

---

### Post by Falc7 on 2010-05-01
Looking forward to Kubuntu slim

---

### Post by tica vun on 2010-05-01
You could easily lose a few more GB by getting rid of openoffice, evolution, firefox, the antisocial networking stuff and documentation packages. Also by replacing gnome with a lighter DE, if you must have one.

---

