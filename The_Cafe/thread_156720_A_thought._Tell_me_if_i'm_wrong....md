---
title: "A thought. Tell me if i'm wrong..."
date: 2006-04-07
forum: The Cafe
---

### Post by GarethMB on 2006-04-07
Upgrading from breezy to dapper can be done by editing the sources list. 

At present there is no tool to auto upgrade.

Gedit has a replace all function. 

Is it not possible for someone to write a shell scriprt that:
a) runs sudo gedit /etc/apt/sources.list
b) brings up the replace box by doing which ever process ctrl and r is.
c) writes breezy in the first box.
d) writes dapper in the second box.
e) presses replace all.
f) runs dist-upgrade.

Is it too complex to make a script write stuff in a program, because this seems really obvious to me so i must be missing something obvious. And please don't flame, its really an innocent question.:-k

---

### Post by GeneralZod on 2006-04-07
Even easier than that! :) Just type in

```

cat /etc/apt/sources.list | sed "s/breezy/dapper/g"

```

(don't worry; it won't actually make any changes) and read through the output.

An extra three lines would be able to re-direct the output to a temporary file; replace the sources.list with this new temporary file (sed may have this functionality built in already - I've never actually used it before :)) and run dist-upgrade.

Just one of many reasons why a UNIX-y enviroment *rocks my world* \\:D/

---

### Post by taurus on 2006-04-07
Yes, at this point, you need to replace breezy with dapper if you want to upgrade your machine to dapper when it comes out, June 1st.  However, you could write a script to first copy /etc/apt/sources.list to /etc/apt/sources.list.bak (in case you screw something up).  Second, search for "breezy" and replace it with "dapper" in /etc/apt/sources.list.  Third, run "sudo apt-get update" and then finally upgrade it with "sudo apt-get upgrade."  Shouldn't be too hard so what are you waiting for?  You have about 7 1/2 weeks to perfect it.  ;)

---

### Post by aysiu on 2006-04-07
It's probably quite easy for someone who knows shell scripting, but it's almost not worth it.

After all, it's probably about the same amount of effort for someone to download the script, make it executable, and then run it, as it does to edit the sources.list file and do a dist-upgrade.

Maybe it would be something like this? ```
#!/bin/bash
cd /etc/apt
mv sources.list sources.list_breezy
sed 's/breezy/dapper/g' sources.list_breezy >sources.list
apt-get update
apt-get dist-upgrade
``` I'm pretty confident this would work.

So you would do something like this ```
sudo gedit /usr/local/bin/upgrade.sh
``` or ```
sudo kwrite /usr/local/bin/upgrade.sh
``` Paste in the code and save. Then ```
sudo chmod +x /usr/local/bin/upgrade.sh
sudo upgrade.sh
```

---

### Post by GarethMB on 2006-04-07
[QUOTE=GeneralZod]Even easier than that! :) Just type in

```

cat /etc/apt/sources.list | sed "s/breezy/dapper/g"

```

(don't worry; it won't actually make any changes) and read through the output.

An extra three lines would be able to re-direct the output to a temporary file; replace the sources.list with this new temporary file (sed may have this functionality built in already - I've never actually used it before :)) and run dist-upgrade.

Just one of many reasons why a UNIX-y enviroment *rocks my world* \\:D/[/QUOTE]
Ok. So all an automated upgrader for breezy to dapper needs to be is a 4 line shell script? Why are the developers making such a fuss/stalling over the need for a upgrade program, when the solution could be this easy?

---

### Post by SeanTater on 2006-04-07
Because it is not always that easy. Sometimes the repositories are in mid-development and does not install correctly, sometimes some packages have problems and do not run. Sometimes the servers are down. Sometimesthings needs to be attended to interactively, which the script cannot handle.  You will probably want the convenience of being able to open it from the menu. You probably want a few settings, for example, if such-a-server is down, use such-a-server. etc.. etc..

---

### Post by aysiu on 2006-04-09
It just occurred to me that something's missing from my script.

Does anyone know how the script would be able to tell if someone is running Ubuntu and then do ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` at the beginning of the script or, for Kubuntu, ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

Or... to make things complicated, people who have both ```
sudo apt-get update
sudo apt-get install ubuntu-desktop kubuntu-desktop
```

I believe the metapackage should be installed before the dist-upgrade.

---

### Post by briancurtin on 2006-04-09
[QUOTE=aysiu]It just occurred to me that something's missing from my script.

Does anyone know how the script would be able to tell if someone is running Ubuntu[/QUOTE]
im not using ubuntu at the moment, but cant you tell somewhere in the output of "uname -a" that its ubuntu? on arch if i do "uname -r" i get 2.6.16-ARCH which i could parse and make sure that it contains "ARCH". somewhere in the "uname" command there should be a flag that might output what you are looking for, but you would have to do something to pick the string apart and ensure that it has what you want.

---

### Post by aysiu on 2006-04-09
Thanks for the suggestions.

```
uname -a
``` appears to identify I'm using Kubuntu. It doesn't, however, identify that I also have Ubuntu (Gnome) installed.

Also, I don't know how to turn that into a proper if/then statement with variables and such. I'm not a programmer.

---

### Post by aysiu on 2006-04-15
Okay, my poor attempt at a script is a piece of crap.

I tried it, and I even tried it with modifications.

Any *real* programmers out there want to write this script. I'm guessing it'll be very popular around May 31 or June 1.

The script should do these things:

1. Determine whether someone's using Gnome, KDE, XFCE, or some combination thereof.

2. ```
sudo apt-get update
``` and then ```
sudo apt-get install *appropriate-desktop* *other-desktop*
```

3. Make a backup copy of the /etc/apt/sources.list file.

4. Find and replace Breezy for Dapper in the sources.list

5. ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Any takers?

---

