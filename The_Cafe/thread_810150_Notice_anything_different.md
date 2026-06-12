---
title: "Notice anything different?"
date: 2008-05-28
forum: The Cafe
---

### Post by ShodanjoDM on 2008-05-28
Take a look below (click to enlarge):

[ATTACH]71875[/ATTACH]

---

### Post by chinchilla2392 on 2008-05-28
Tabs :o

---

### Post by FuturePilot on 2008-05-28
Took me a while.
But I've got to know how and where can I get it? :D

---

### Post by zmjjmz on 2008-05-28
...
want.

---

### Post by chinchilla2392 on 2008-05-28
> **FuturePilot said:**
> Took me a while.
But I've got to know how and where can I get it? :D

i got it straight away ;)
no idea where to find it.. lol..
im not too bothered.

---

### Post by FuturePilot on 2008-05-28
> **chinchilla2392 said:**
> i got it straight away ;)
no idea where to find it.. lol..
im not too bothered.

Hehe. The funny thing was I was staring at them for almost a whole minute before it hit me. **they were right in front of my face**:shock:

---

### Post by swoll1980 on 2008-05-28
> **ShodanjoDM said:**
> Take a look below (click to enlarge):

[ATTACH]71875[/ATTACH]

I want some! Give me tabs please. Are you just teasing me or what?

---

### Post by ShodanjoDM on 2008-05-28
> **FuturePilot said:**
> Took me a while.
But I've got to know how and where can I get it? :D

If you don't mind compiling from source, you can get it. But beware however, that **_this feature is still in development_** although it's already usable. It's originally intended for GNOME 2.24 in next September.

Before you start, you might want to read this [article]("http://arstechnica.com/journals/linux.ars/2008/05/27/gnome-file-manager-gets-tabbed-file-browsing") first.

Aside from the usual build-essential, you'll need subversion:

```
$sudo aptitude install subversion
```

For the dependencies (needs source repositories enabled in sources.list iirc):

```
$sudo apt-get build-dep nautilus
$sudo aptitude install gnome-common
```

To make it tidy and organized, I always make a Download/Subversion directories in my home folder, so here's my preference:

```
$cd ~/
$mkdir -p Download/Subversion
$cd Download/Subversion
```

And then pull all the sources:

```
$svn co http://svn.gnome.org/svn/nautilus/branches/multiview nautilus-multiview
```

However, you need to uninstall nautilus and nautilus-data first. In my case, I have successfully removed them that also automatically removed nautilus-cd-burner and nautilus-sendto packages. I don't know if it's the same with the "ordinary" Ubuntu installation since I'm using Ubuntu Studio.

Do let me know if it also affects other packages in your installation before pressing enter:

```
sudo apt-get remove nautilus nautilus-data
```

Then the usual dance:

```
$cd nautilus-multiview
$./autogen.sh --prefix=/usr
$make
$sudo make install
```

> PS: if you want to disable tracker/beagle integration, you can use this in the ./autogen.sh stage:

```
./autogen.sh --prefix=/usr --disable-tracker --disable-beagle
```

Thanks to [ryanhaigh]("http://ubuntuforums.org/member.php?u=506606") for his excellent [howto]("http://ubuntuforums.org/showthread.php?p=4524368") about removing beagle & tracker integration.

You'll need to log out, but before that, rename/remove .nautilus directory in your home folder. I took a "safer" approach by just renaming it:

```
mv ~/.nautilus ~/.nautilusx
```

Don't worry, the .nautilus folder will be automatically created after you log in again.

After that log out and log back in.

**Caution:** In my case, after I finished installing the "new" Nautilus, aptitude informed me that there are several uneeded packages that it wants to remove. Two of them are gvfs and gvfs-backend. I don't want any of them to be autoremoved, so I fired up Synaptic, located the said packages and unchecked "Automatically Installed" mark under Package menu.

EDIT: Added missing dependency (gnome-common)

---

### Post by quinnten83 on 2008-05-28
Will this be available in the next Gnome release, because then I'd just as soon wait. I can compile but I use my machine to be productive so I don't like to mess about with it.

---

### Post by zachtib on 2008-05-28
I'm guessing he's not using nautilus?

---

### Post by ShodanjoDM on 2008-05-28
> **zachtib said:**
> I'm guessing he's not using nautilus?

It *is* Nautilus :D

---

### Post by ShodanjoDM on 2008-05-28
> **quinnten83 said:**
> Will this be available in the next Gnome release, because then I'd just as soon wait. I can compile but I use my machine to be productive so I don't like to mess about with it.

Yup. As written in ars-technica article, it's planned for Gnome 2.24, with atleast another new feature (small icon view) as well.

---

### Post by zachtib on 2008-05-28
> **ShodanjoDM said:**
> It *is* Nautilus :D

Ok, NOW I'm interested...

8.10 is gonna rock

---

### Post by Ebuntor on 2008-05-28
> **ShodanjoDM said:**
> If you don't mind compiling from source, you can get it. But beware however, that this feature is still in development although it's already usable. It's originally intended for GNOME 2.24 in next September.

Before you start, you might want to read this [article]("http://arstechnica.com/journals/linux.ars/2008/05/27/gnome-file-manager-gets-tabbed-file-browsing") first.

Aside from the usual build-essential, you'll need subversion:

```
$sudo aptitude install subversion
```For the dependencies (needs source repositories enabled in sources.list iirc):

```
$sudo apt-get build-dep nautilus
```To make it tidy and organized, I always make a Download/Subversion directories in my home folder, so here's my preference:

```
$cd ~/
$mkdir -p Download/Subversion
$cd Download/Subversion
```And then pull all the sources:

```
$svn co http://svn.gnome.org/svn/nautilus/branches/multiview nautilus-multiview
```However, you need to uninstall nautilus and nautilus-data first. In my case, I have successfully removed them that also automatically removed nautilus-cd-burner and nautilus-sendto packages. I don't know if it's the same with the "ordinary" Ubuntu installation since I'm using Ubuntu Studio.

Do let me know if it also affects other packages in your installation before pressing enter:

```
sudo apt-get remove nautilus nautilus-data
```Then the usual dance:

```
$cd nautilus-multiview
$./autogen.sh --prefix=/usr
$make
$sudo make install
```

You'll need to log out, but before that, rename/remove .nautilus directory in your home folder. I took a "safer" approach by just renaming it:

```
mv ~/.nautilus ~/.nautilusx
```Don't worry, the .nautilus folder will be automatically created after you log in again.

After that log out and log back in.

**Caution:** In my case, after I finished installing the "new" Nautilus, aptitude informed me that there are several uneeded packages that it wants to remove. Two of them are gvfs and gvfs-backend. I don't want any of them to be autoremoved, so I fired up Synaptic, located the said packages and unchecked "Automatically Installed" mark under Package menu.

I do run into a few problems.
I use Hardy and when I enter "sudo apt-get remove nautilus nautilus-data" not only  will nautilus-cd-burner, nautilus-data etc be removed but also ubuntu-desktop.

When I try to run "./autogen.sh --prefix=/usr" I get the message: "You need to install gnome-common from the GNOME CVS".

---

### Post by Bungo Pony on 2008-05-28
It's about bloody time they started implementing that!

However, I'll wait until it's officially released to get it.

---

### Post by visionaire on 2008-05-28
you mean this? we have this centuries ago :lolflag:

---

### Post by Kernel Sanders on 2008-05-28
Want!!!!

---

### Post by idn on 2008-05-28
could someone post a deb or it? looks awesome....

---

### Post by ShodanjoDM on 2008-05-28
> **Ebuntor said:**
> I do run into a few problems.
I use Hardy and when I enter "sudo apt-get remove nautilus nautilus-data" not only  will nautilus-cd-burner, nautilus-data etc be removed but also ubuntu-desktop.

When I try to run "./autogen.sh --prefix=/usr" I get the message: "You need to install gnome-common from the GNOME CVS".

The ubuntu-desktop package is only a meta-package. It helps in installing all of the standard ubuntu packages. I think it's safe to remove if it's the only additional package as you mentiononed above.

Oops sorry, you'll need to install gnome-common package first.

```
sudo aptitude install gnome-common
```

I'll update the instruction soon.

Anyway, I would like to remind everyone interested in this once again:

This feature is still in development so although I found it usable, but your mileage may vary. Proceed with caution.

---

### Post by ShodanjoDM on 2008-05-28
> **visionaire said:**
> you mean this? we have this centuries ago :lolflag:

Yeah, a much needed but long delayed feature in Nautilus...

Makes me wonder whether it'll be a wiser move if GNOME dev team drop Nautilus - and redirect its development efforts to PCManFM - or not 
:lolflag:

---

### Post by ShodanjoDM on 2008-05-28
> **idn said:**
> could someone post a deb or it? looks awesome....

I tried making it wit checkinstall, but ran into some problems when i tried installing the .deb package. So sorry :(

I need to start learning to make 'proper' debian packages soon.

---

### Post by quanumphaze on 2008-05-28
Does the new one support multiple wallpapers? I remember someone mentioning they were making it.

I miss my desktop icons.

Else can I make PCManFM do multiple backgrounds (Properly or letting Compiz do it by drawing a transparent BG). FYI PCManFM draws the desktop too.

---

### Post by Gourgi on 2008-06-09
> **quanumphaze said:**
> Does the new one support multiple wallpapers? I remember someone mentioning they were making it.
i tried that but no support yet
maybe it is develloped in a different branch :confused:

---

### Post by LightB on 2008-06-10
Hmm... something that's been in Konqueror since forever. Now I hope Thunar copies this.

---

### Post by EnigMattic on 2008-07-14
Word to the wise:
After following this guide, Nautilus opened by default in the spacial rather than browser mode if tried with items from the 'Places' menu or folders on the desktop.

To resolve this, simply open Nautilus and Edit-->Preferences-->[Behaviour], then check the 'Always open in browser windows' box...

Ta-da! :-)

Now if only there was a button to open a new tab...

---

### Post by EnigMattic on 2008-07-14
Ok, new problem...
Clicking or right-clicking on .iso files causes Nautilus to crash and restart :-(

---

### Post by nycste on 2008-07-26
great thread just showing my support, im still learning how to compile simple programs so compiling something so big isnt for me ill wait lol

more views and tabs are a huge plus, and hopefully some other goodies


anyone know if you can allow nautilus in list view to show

currently
file.name 10MB

to instead say like in windows
file.name 10000KB give or take a few

---

### Post by TBOL3 on 2008-07-26
Wow, I hope canonical does what it did with firefox, and puts it in the next version, if not, let's hope getdeb will have it (I can't for the life of me track all of the dependencies to compile from source).

---

### Post by Methuselah on 2008-07-26
Aren't there some window managers (I think compiz and fluxbox) taht support 'smashing' windows together into tabs?
With that you can emulate tab functionality missing from apps quite well.

---

### Post by Tomosaur on 2008-07-26
> **EnigMattic said:**
> Ok, new problem...
Clicking or right-clicking on .iso files causes Nautilus to crash and restart :-(

EDIT: On closer inspection, this seems to happen with any file that nautilus needs to work out what type of file it is (i.e: everything except directories).

I can't imagine the nautilus devs have screwed up this badly, so for now I'm going to give them the benefit of the doubt and see whether I've simply missed some compilation option.

EDIT 2: Screw it, I'm going back to old nautilus :P

---

### Post by BackwardsDown on 2008-07-26
> **TBOL3 said:**
> Wow, I hope canonical does what it did with firefox, and puts it in the next version, if not, let's hope getdeb will have it (I can't for the life of me track all of the dependencies to compile from source).

The current version of Nautilus in Intrepid (Alpha 3 of the next version) has tabs.

---

