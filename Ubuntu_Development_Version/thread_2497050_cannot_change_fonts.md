---
title: "cannot change fonts"
date: 2024-04-21
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-04-21
Hello,

as the title mentions, under gnome-tweaks->Fonts it is not possible to change the default font value. It changes as an option and reverts back. Neither the size is possible to change.

Regards!

---

### Post by #&amp;thj^% on 2024-04-21
Sounds like a good bug-report.

Claus7 will this work still?
```
gsettings set org.gnome.nautilus.desktop font 'Ubuntu 10'
```

If Not this should still work:
```
gsettings set org.gnome.desktop.interface text-scaling-factor (value) 
```

Yep change (value) to your liking.

---

### Post by Claus7 on 2024-04-21
Hello,

> **1fallen said:**
> Sounds like a good bug-report.

Claus7 will this work still?
```
gsettings set org.gnome.nautilus.desktop font 'Ubuntu 10'
```

> $ gsettings set org.gnome.nautilus.desktop font 'Ubuntu 10'
No such schema &#8220;org.gnome.nautilus.desktop&#8221;

Also I notice that Ctrl+c/v is not working in my pc. I have to right click and do copy paste. Edit: it is not working using gnome-terminal.
Thank you for your response *1fallen*.

Regards!

---

### Post by #&amp;thj^% on 2024-04-21
I edited my post while you doing the first suggestion.

I'm very rusty on Gnome sorry. :)

---

### Post by Claus7 on 2024-04-21
Hello,

I think that the second command you propose is the same as going to settings->Displays->scale and changing the value from there. Affirmative, I can change both the scaling under settings and using your command, e.g.:
gsettings set org.gnome.desktop.interface text-scaling-factor 1.25

Regards!

---

### Post by #&amp;thj^% on 2024-04-21
Bug on "gnome-tweaks".

See if it lasts first though.
And the "Ctrl+c/v" is just a Gnome thing it might get fixed with updates, or Gnome Devs wil just ignore it....

---

### Post by corradoventu on 2024-04-21
On my Ubuntu Noble in nautilus "Ctrl+c/v" works fine.
for the font see:
```
corrado@corrado-n7-nn-0420:~$ gsettings get org.gnome.desktop.interface font-name
'Ubuntu Sans 11'
corrado@corrado-n7-nn-0420:~$
```

---

### Post by Claus7 on 2024-04-21
Hello,

> **corradoventu said:**
> On my Ubuntu Noble in nautilus "Ctrl+c/v" works fine.
affirmative, I noticed the problem using gnome terminal and issuing commands at the time. I checked it e.g. with gedit and found out that copy-paste is working fine there.
> **corradoventu said:**
> 
for the font see:
```
corrado@corrado-n7-nn-0420:~$ gsettings get org.gnome.desktop.interface font-name
'Ubuntu Sans 11'
corrado@corrado-n7-nn-0420:~$
```
instead of issuing the command I went via dconf editor, which changes the font. Also the change is shown under gnome-tweaks. Want some more testing and report back. 
Edit: made the changes in question. I used dconf in order to avoid any typo. Gnome-tweaks is not as it used to. It doesn't pick up the last font and size you have used and if you want Ubuntu Sans for example, you have to pick up Ubuntu Sans Regular, where the Regular is not displayed. As *1fallen* mentioned it seems a bug of gnome-tweaks. I think I will wait a little and report it.

Regards!

---

### Post by Claus7 on 2024-04-22
Hello,

after today's updates of gnome-tweaks problem solved.

Regards!

---

### Post by Claus7 on 2024-04-22
Hello,

> **Claus7 said:**
> ...
Also I notice that Ctrl+c/v is not working in my pc. I have to right click and do copy paste. Edit: it is not working using gnome-terminal.
...

for some reason the shortcuts for gnome-terminal changed during the upgrade. In order to fix the issue I went to: hamburger icon->preferences->shortcuts and under Edit I changed the copy-paste shortcut keys.

Regards!

---

### Post by jbicha on 2024-04-22
Ctrl+C can't be used for copying in terminals by default for ancient historical reasons. So it's usually Shift+Ctrl+C and Shift+Ctrl+V

---

