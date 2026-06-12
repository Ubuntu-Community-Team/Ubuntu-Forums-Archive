---
title: "What do you remove on a clean install?"
date: 2007-10-06
forum: The Cafe
---

### Post by nickburns on 2007-10-06
I often clear out some packages after a clean install, what packages do you remove?

---

### Post by hessiess on 2007-10-06
when gusty is relised the furst thing thats going to go is compez-fution

the only thing i've removed from fisty is gnome games

---

### Post by bobbocanfly on 2007-10-06
```
sudo apt-get remove ekiga evolution totem serpentine gdm tomboy f-spot rhythmbox
```

Probably a whole lot more.

---

### Post by Skye on 2007-10-06
I remove ekiga, all of the accessibility stuff (I think the package name is orca) and anything related to bluetooth.

---

### Post by Nano Geek on 2007-10-06
> **bobbocanfly said:**
> ```
sudo apt-get remove ekiga evolution totem serpentine gdm tomboy f-spot rhythmbox
```Probably a whole lot more.Why GDM?

---

### Post by wersdaluv on 2007-10-06
> **bobbocanfly said:**
> ```
sudo apt-get remove ekiga evolution totem serpentine gdm tomboy f-spot rhythmbox
```

Probably a whole lot more.

What DM do you use?

---

### Post by p_quarles on 2007-10-06
The beauty of installing a command-line system is that you don't need to remove anything, just add what you do want. I highly recommend it.

---

### Post by nickburns on 2007-10-06
So do you install the server then install xserver and x11?

---

### Post by p_quarles on 2007-10-06
No, the server edition uses a slightly different kernel; I wouldn't use that for a desktop. You choose the "Command line installation" option at the initial disk menu. 

After that, yes, you install xorg and whichever desktop manager/GUI you want.

---

### Post by RAV TUX on 2007-10-06
> **nickburns said:**
> I often clear out some packages after a clean install, what packages do you remove?

```

sudo apt-get remove openoffice.org-core
```

---

### Post by mthei on 2007-10-06
Things I have removed:
-Gnome Games (all I have in that section of my menu are three emulators and the version of Minesweeper that comes with Wine)
-Ekiga Softphone
-Everything Bluetooth related, as has been mentioned, except for that one package that's stuck with the Ubuntu-Desktop metapackage
- Tomboy Note
- Orca

And as of this thread, I had removed Totem, which I had thought was a part of the Ubuntu-Desktop package, as I'm sure it was in 6.10. In fact, there are a lot of applications that were attached to the package in Edgy that are not in Feisty. I hope even less is so in Gutsy.

---

### Post by Frak on 2007-10-06
> **RAV TUX said:**
> ```

sudo apt-get remove openoffice.org-core
```
Same here, OO.o is WAY too slow for my taste.

Abiword and Gnumeric do just fine :)

---

### Post by RageOfOrder on 2007-10-06
Absolutely nothing. A clean install of Gentoo comes with absolutely nothing but the essentials.

Not even X :)

---

### Post by nickburns on 2007-10-07
I have come to the conclusion that the way to go is to start with the command line install (off the alternate cd) and build up your system as you need it.  I have a working version of ubuntu with firefox and other necessary software and still under a Gig.  No bells and whistles but still happy that it is clean and very small on my HDD.

---

### Post by kadath on 2007-10-07
I used to remove just about *everything* GNOME/Ubuntu comes with, so I just switched to Xubuntu permanently. It doesn't come with the crap GNOME apps, and Xfce is awesome.

I still have to uninstall some stuff on Xubuntu though, like OpenOffice Writer and Thunderbird.

---

### Post by Malta paul on 2007-10-07
The way I upgrade is: 
 I first use 'APTonCD' and save my extra configuration files on a CD.
All my personal files are already on a separate partition including any files I have transfered from my /Home Directory.
As my system is on a separate partition I reformat it during installation of the system using the manual format choice.
Then I selectively restore my configuration files from the back-up 'APTonCD' CD
This may not be the best way, but it works :)

---

### Post by Laterix on 2007-10-07
Well, here it is

```
sudo apt-get remove example-content ekiga f-spot gnome-games gnome-games-data xsane xsane-common evolution evolution-common evolution-plugins evolution-exchange evolution-data-server evolution-data-server-common evolution-webcal openoffice.org-evolution desktop-effects compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
```

---

### Post by FuturePilot on 2007-10-07
totem-mozilla
Replace with Mplayer

---

### Post by lzfy on 2007-10-07
Openoffice and some other kde apps which I don't remember right now.

---

### Post by RAV TUX on 2007-10-07
> **Frak said:**
> Same here, OO.o is WAY too slow for my taste.

Abiword and Gnumeric do just fine :)

I usually follow it up with:
```

sudo apt-get install koffice
```

---

### Post by bobbocanfly on 2007-10-07
> **asjdfwejqrfjcvm msz34rq33 said:**
> Why GDM?

Sorry, i dont remove it, i just dont boot into it, so when i startup, i get a CLI environment, then i can 'startx' if i want a GUI.

---

### Post by p_quarles on 2007-10-07
> **RAV TUX said:**
> I usually follow it up with:
```

sudo apt-get install koffice
```
Have to agree with you there. Koffice is fantastic.

---

### Post by Frak on 2007-10-07
> **RAV TUX said:**
> I usually follow it up with:
```

sudo apt-get install koffice
```
Just tried koffice, thanks RAV

Just proves how KDE may not be the best DM, but the apps for it are amazing. :)

---

### Post by capink on 2007-10-07
The alternate cd did not work for me and I wanted a minimal system. I found that removing packages individually would be difficult as I will have to delete a lot of packages manually. So I made myself a script that will keep only the packages I am interested in (which I feed to the script as list saved in a file) and remove the rest of the packages. So now I experiment with a lot of packages and whenever my system gets cluttered I run the script again.

---

