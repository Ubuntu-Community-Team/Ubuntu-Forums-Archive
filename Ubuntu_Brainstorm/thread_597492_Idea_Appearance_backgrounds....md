---
title: "Idea: Appearance: backgrounds..."
date: 2007-10-30
forum: Ubuntu Brainstorm
---

### Post by Rinzwind on 2007-10-30
Suggestion: add an option to have the wallpapers randomize. 

[img]http://tuxicity.files.wordpress.com/2007/08/screenshot-appearance-preferences-1.png?w=145&h=128[/img]

It would require is a slider with some choices 5, 10, 15, 20, 30, 45, 60, 120 minutes and 'never'.

Changing the wallpaper from commandline seems very easy:

```
gconftool-2 --type string --set
/desktop/gnome/background/picture_filename 
{/dir/to/picture/picture.png}
```

Easy and it makes your background a lot more interesting. 
So why not have this is Gnome? :)

---

### Post by smartboyathome on 2007-10-30
> **Rinzwind said:**
> Suggestion: add an option to have the wallpapers randomize. 

[img]http://tuxicity.files.wordpress.com/2007/08/screenshot-appearance-preferences-1.png?w=145&h=128[/img]

It would require is a slider with some choices 5, 10, 15, 20, 30, 45, 60, 120 minutes and 'never'.

Changing the wallpaper from commandline seems very easy:

```
gconftool-2 --type string --set
/desktop/gnome/background/picture_filename 
{/dir/to/picture/picture.png}
```

Easy and it makes your background a lot more interesting. 
So why not have this is Gnome? :)

This is already provided with drape (i think it is called). Search for Wallpapers in synaptic, and you should get it.

---

### Post by Neon Lights on 2007-10-30
> **smartboyathome said:**
> This is already provided with drape (i think it is called). Search for Wallpapers in synaptic, and you should get it.
Yeah, but it'd be nice to have it by default and integrated with the appearance thing, instead of having to download and configure it separately.
I'd like it if you can have it change like, a new one for each day. :D That'd be awesomeness.

---

### Post by smartboyathome on 2007-10-30
> **Neon Lights said:**
> Yeah, but it'd be nice to have it by default and integrated with the appearance thing, instead of having to download and configure it separately.
I'd like it if you can have it change like, a new one for each day. :D That'd be awesomeness.

Someone better transfer code from drape to it then. ;)

---

### Post by 23meg on 2007-10-30
I don't think that code can go upstream, since this is GNOME, where configuration interfaces are kept simple and to the point, and adding extra functionality that's of use to a small subset of the user base is usually left up to third party applications and for the users themselves to pick and choose.

---

### Post by jusmurph on 2007-10-31
wallpaper-tray is great for this.

---

### Post by Rinzwind on 2007-10-31
> **smartboyathome said:**
> This is already provided with drape (i think it is called). Search for Wallpapers in synaptic, and you should get it.

That's where I had the idea from.

Its name is desktop drapes:
1. crashes alot. At least once every time I touch the slider;
2. does not scan the directory it's told to scan;
3. never wants to remember the pictures I added to it.

I use it due to there not being a better(!) alternative but I hate using it.Having it at 'desktop appearance' would have been an excellent addition to an allready very excellent Gnome.

By the way: if your 1st sentence is a valid argument why did Compiz Fusion make it into Gnome? Since it was allready provided... 
I believe that if it makes things better it should be considered. It's just an idea :)  

> **23meg said:**
> I don't think that code can go upstream, since this is GNOME, where configuration interfaces are kept simple and to the point, and adding extra functionality that's of use to a small subset of the user base is usually left up to third party applications and for the users themselves to pick and choose.

True. True. But it would be very nice to have :( I like my desktop to be fancy. 
Guess I'll have to make my own desktop drapes to fulfill my wishes :D

---

### Post by tubasoldier on 2007-10-31
KDE has this built in. And is really one of the only reasons I use KDE more. Its nice to have a different wallpaper for each workspace.

But it won't matter what you want. The Gnome devs have already decided that simplicity is key and functionality will loose out no matter how simple the configuration is.

---

### Post by jusmurph on 2007-10-31
> **Rinzwind said:**
> That's where I had the idea from.

I use it due to there not being a better(!) alternative but I hate using it.Having it at 'desktop appearance' would have been an excellent addition to an allready very excellent Gnome.

```

sudo apt-get wallpaper-tray
```

It does all of that! Seriously.

---

### Post by tubasoldier on 2007-10-31
> ```
sudo apt-get wallpaper-tray
```

It does all of that! Seriously.

yes, it does do all of that, and does it quite well. But you need to know that it has never worked properly either. You have to configure it using gconf-editor. Which I think is no big deal, but the graphical interface to it sucks. It also puts yet another icon in your notification area.

---

