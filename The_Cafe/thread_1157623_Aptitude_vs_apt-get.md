---
title: "Aptitude vs apt-get"
date: 2009-05-12
forum: The Cafe
---

### Post by MontelEdwards on 2009-05-12
which do you perfer?
i like aptitude

---

### Post by Gannon8 on 2009-05-12
apt-get

Its a TON easier to filter through and get packages you want.

woot 1st post :)

---

### Post by Skripka on 2009-05-12
Niether...then again I'm an Archer ;)

---

### Post by Tipped OuT on 2009-05-12
:lolflag: Look at the poll.

EDIT: Ah dang it, some one voted for aptitude.

---

### Post by MontelEdwards on 2009-05-12
> **Tipped OuT said:**
> :lolflag: Look at the poll.

EDIT: Ah dang it, some one voted for aptitude.

Hahahaha

---

### Post by konqueror7 on 2009-05-12
apt-get, the command seems more logical in stating the functionality...:P

---

### Post by monsterstack on 2009-05-13
I prefer aptitude for removing applications. Its default behaviour is to autoremove, so you can completely purge stuff easily. And it doesn't mind if one your apps is spelt wrong, so whilst

```
sudo aptitude purge amarok vlc oepmoffice
```

will tell you spelt openoffice incorrectly, it will remove the other two apps. Whereas this:

```
sudo apt-get autoremove --purge amarok vlc oepmoffice
```

Won't work very well at all. This is why my favourite bash alias of all is:

```
alias nuke='sudo aptitude purge $@'
```

---

### Post by Lampi on 2009-05-13
I use apt-get to handle source code mostly, aptitude if I want to upgrade.

BTW: why should I use aptitude 'safe-upgrade' instead of 'aptitude upgrade'? What's the difference?

---

### Post by monsterstack on 2009-05-13
> **Lampi said:**
> I use apt-get to handle source code mostly, aptitude if I want to upgrade.

BTW: why should I use aptitude 'safe-upgrade' instead of 'aptitude upgrade'? What's the difference?

I don't know. Let me manpage that for you:

```
safe-upgrade
           Upgrades installed packages to their most recent version. Installed
           packages will not be removed unless they are unused (see the
           section &#8220;Managing Automatically Installed Packages&#8221; in the aptitude
           reference manual). Packages which are not currently installed may
           be installed to resolve dependencies unless the --no-new-installs
           command-line option is supplied.

           [B]It is sometimes necessary to remove one package in order to upgrade
           another; this command is not able to upgrade packages in such
           situations.[/B] Use the full-upgrade command to upgrade as many
           packages as possible.
```

That's cool. I didn't know that. Bog-standard "upgrade" seems to have been replaced by this action. Anyway the reason I voted for aptitude in general, however, is this:

```
sudo aptitude
```

---

### Post by lethalfang on 2009-05-13
Is there an equivalent of "sudo aptitude hold my-app" (i.e., do not upgrade to a newer version of an app) for apt-get?

---

### Post by monsterstack on 2009-05-13
> **lethalfang said:**
> Is there an equivalent of "sudo aptitude hold my-app" (i.e., do not upgrade to a newer version of an app) for apt-get?

As root:
```
echo 'vlc hold' | dpkg --set-selections
```
See if it works:
```

dpkg --get-selections|grep vlc
```

Works for me:
```

libvlc2						install
libvlccore0					install
vlc						hold
vlc-data					install
vlc-nox						install

```

To undo:

```
echo 'vlc install' | dpkg --set-selections
```

---

### Post by Lampi on 2009-05-13
> **monsterstack said:**
> ```
echo 'vlc hold' | dpkg --set-selections
```I usually go with this one - it's because of the KDE4 package manager: this one only checks the holds of "dpkg --set-selections", so if I put a package on hold using "aptitude hold", the KDE package manager will ignore this.

---

### Post by calrogman on 2009-05-13
Aptitude every time. Apt-get and synaptic just can't handle dependencies nearly as well as aptitude.

---

