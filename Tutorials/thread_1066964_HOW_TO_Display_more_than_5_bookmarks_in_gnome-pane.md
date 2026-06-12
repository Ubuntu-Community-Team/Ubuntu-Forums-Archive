---
title: "HOW TO: Display more than 5 bookmarks in gnome-panel &quot;Places&quot; menu"
date: 2009-02-11
forum: Tutorials
---

### Post by w0ng on 2009-02-11
Derived from:
[http://brainstorm.ubuntu.com/idea/14381/](http://brainstorm.ubuntu.com/idea/14381/)
[http://ubuntuforums.org/showthread.php?t=733808](http://ubuntuforums.org/showthread.php?t=733808)

1) Open Terminal

2a) Install apt-build
```
sudo apt-get update
sudo apt-get install apt-build
```

2b) Configure apt-build:
[list][*]Optimization level: **Medium**
[*]Add apt-build repository to sources.list: **Yes**
[*]Architecture: **<SELECT YOUR ARCHITECTURE>**[/list]

3) Install files required to build gnome-panel from source and download the source
```
sudo apt-get build-dep gnome-panel
sudo apt-build source gnome-panel
```

4) Navigate to the downloaded gnome-panel source folder and open the menu items file
```
cd /var/cache/apt-build/build/gnome-panel-*
sudo gedit gnome-panel/panel-menu-items.c
```

5) Set the the maximum number of bookmarks to display before placing them in the *Bookmarks* submenu 

Find the line:
[php]if (g_slist_length (add_bookmarks) <= MAX_ITEMS_OR_SUBMENU) {[/php]
and replace it with:
[php]if (g_slist_length (add_bookmarks) <= 20) {[/php]
Save the file.

6) Install the modified gnome-panel and restart it
```
sudo ./configure
sudo make
sudo make install
killall gnome-panel
```

Before and after pics:
[img]http://img178.imageshack.us/img178/7450/beforenr0.jpg[/img] [img]http://img19.imageshack.us/img19/2271/afterup4.jpg[/img]

---

### Post by schnauzer93 on 2009-03-10
Instead of changing ```
 if (g_slist_length (add_bookmarks) <= MAX_ITEMS_OR_SUBMENU) {
```
you could change ```
#define MAX_ITEMS_OR_SUBMENU 5
```to whatever you want. That way, it would work with volumes, too. Personally, I think this should reside in a configuration file, so one doesn't have to edit the source and recompile to fix such a trivial issue. But that's just me.

---

### Post by binbash on 2009-03-11
Both works fine but i prefer changing MAX_ITEMS_OR_SUBMENU

---

### Post by w0ng on 2009-03-16
If Network Places and Removeable Media aren't a concern, changing MAX_ITEMS_OR_SUBMENU is the way to go.

---

### Post by nielsrune on 2009-04-27
Thank you so much for this.
The five item limit is so annoying. And the last time i tried to compile from source the whole system went wrong.
It seemed like I installed the originale gnome-panel instead of Ubuntu's edit.
Guess it had something to do with the .dsc anf .diff.gz files, but i never figured it out then.
So I was surprised your guide not included these files in any way, but it seemed thorough, so I followed the guide, and it works just fine!

Thanks

---

### Post by vahnx on 2009-05-12
Thanks. I wasn't sure on the archetecture. I know the Q6600 is AMD64 and that didn't appear as an option, so I chose the amd10 (or whatever is was) and it worked.

---

### Post by juamez. on 2009-05-15
If I'd do this, would I lose all customizations made to my panels, like applets (and their settings), custom icons, etc? Or would everything just stay the way it is now, with the larger number of bookmarks and volumes the only change noticable?

---

### Post by mc4man on 2009-06-17
> If I'd do this, would I lose all customizations made to my panels, like applets (and their settings), custom icons, etc?

I think you should be ok there, posted a bit more in the nautilus thread

---

### Post by juamez. on 2009-06-18
I followed the instructions from the startpost with the difference that I changed the line in the third step from this:
```
sudo apt-get build-dep gnome-panel
```
to this:
```
sudo aptitude build-dep gnome-panel
```
... because I would get an error, dependency problems, if I didn't.

That was all I had to change from the instructions, which worked nicely.

I also noticed my launchers and applets and everything is just the way it was, with the exception of more bookmarks and devices visible underneath eachother. Yay!

Conclusion:
1) it works
2) the configuration of the gnome-panel is completely kept and reused

---

### Post by loomsen on 2009-06-26
> [COLOR="DarkRed"]sudo[/COLOR] ./configure
[COLOR="DarkRed"]sudo[/COLOR] make

moooep!

OUCH! 
You shouldn't, you really shound NOT build packages as root. Most probably you'll run into segmentation faults, wondering why, cause a Seg Fault only tells you it just seg faulted.

Regressions based upon these commands are very likely.

---

### Post by Messyhair42 on 2009-07-10
thank you, worked great. much easier to navigate between subfolders of subfolders

edit: worked great again w/ new installation (Lucid)

---

### Post by JohnLau on 2009-07-10
I filed a bug report on launchpad for this because I don't think it is proper to hard-code this...
[http://ubuntuforums.org/showthread.php?t=1066964:(](http://ubuntuforums.org/showthread.php?t=1066964:()

---

### Post by Elep.Repu on 2009-07-11
Gathered from throughout. The Right way!

1. Install apt-build

```
sudo apt-get update
sudo apt-get install apt-build
```2b) Configure apt-build:
[LIST]
[*]Optimization level: **Medium**
[*]Add apt-build repository to sources.list: **Yes**
[*]Architecture: **<SELECT YOUR ARCHITECTURE>**
[/LIST]
3) Install files required to build gnome-panel from source and download the source

```
sudo aptitude build-dep gnome-panel
sudo apt-build source gnome-panel
```4) Navigate to the downloaded gnome-panel source folder and open the menu items file
```

cd /var/cache/apt-build/build/gnome-panel-*
sudo gedit gnome-panel/panel-menu-items.c
```5) Set the the maximum number of bookmarks to display
```

#define MAX_ITEMS_OR_SUBMENU 5

```
I changed it to 30. 
Save.

6) Install the modified gnome-panel and restart it

(Sudo is necessary. Otherwise is _does not_ work. :)
```

sudo ./configure
sudo make
sudo make install
killall gnome-panel
```

---

### Post by loomsen on 2009-07-12
not in this build directory... whatever

---

### Post by exozito on 2009-07-18
Thank you! It worked for me!

---

### Post by Messyhair42 on 2009-08-07
can this also be done for the "Removable Media" section? i've got another linux install and its 4 partitions show up here, as well as an NTFS partition, my DVD drive and any usb media i have plugged in and after 5 it defaults to the drop down menu too.

---

### Post by mc4man on 2009-08-07
> can this also be done for the "Removable Media" section?

'Removable media' should also be included, in other words not just limited to bookmarks, see screen

---

### Post by thenyboy on 2009-08-28
I have a problem while i'm writing this command on Terminal

I write sudo apt-get build-dep gnome-panel
And i get this:


> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
**E: No se pudo encontrar un paquete de fuentes para gnome-panel**

it says: **Could not find a source package for gnome-panel**

What can i do to fix it? I can't go on because of this messege. :(

Regards!!!

---

### Post by mc4man on 2009-08-29
> Could not find a source package for gnome-panel

if not resolved by now you need to enable "Source code" for the ubuntu repos in your sources.

Easiest way is to open System -> Admin.. -> Software Sources and on main page ck. the box that says "Source code", then click close and reload.

Make sure the box gets an actual check mark, not just turn a color

---

### Post by thenyboy on 2009-08-31
You are a Genious!!! Thanks a lot!!!!

I could do it doing what you told me. :D

Really, thank you!!!!


Regards From Argentina!

---

### Post by Benchamoneh on 2009-09-03
This is an excellent guide, many thanks! I'd been looking for a way to around this stupid restriction for eternity and I'm glad someone much smarter than me figured it out.

On another note why is such a simple modification so cumbersome? I love that you can do things like this in Linux don't get me wrong - open source is great for reasons just like this, but seriously recompiling the whole panel just to change one setting is a little like overkill. I think this UI restriction needs to be addressed in a future release, maybe a gconf option or setting? (though I'd imagine this wouldn't be a simple task!)

---

### Post by davidY on 2009-09-08
Is it possible for anybody to give a deb or a ppa for this?? pretty please :KS:KS

---

### Post by alibabajr on 2009-09-19
Thanks, worked fine for me and find it very useful

---

### Post by theZoid on 2009-09-23
My solution was to install Ubuntu System Panel, screenie below.  I prefer this much over the standard menu:

---

### Post by ninjapirate89 on 2009-09-23
> **theZoid said:**
> My solution was to install Ubuntu System Panel, screenie below.  I prefer this much over the standard menu:

Never saw that menu before. How can I get it? Link?

---

### Post by ninjapirate89 on 2009-09-23
Just finished! Thank you very much. :D

---

### Post by John Baptist on 2009-09-29
JohnLau: I agree this is a bug. At the very least, this should be a (hidden) gconf option, but ideally there should be a GUI way to modify this parameter. Even better, gnome-panel should detect an appropriate value based on the size of your screen.

However, the link you posted is not to a bug report, but to this thread. Did you post the wrong link?

---

### Post by Beetroot Dog on 2011-02-05
I realise that this is an old thread, but is there any way - outside of recompiling gnome panel - to change this?

Not sure why, but these smaller things seem to incite my Computer Rage the most.

---

### Post by mulp on 2011-11-19
> **Beetroot Dog said:**
> I realise that this is an old thread, but is there any way - outside of recompiling gnome panel - to change this?

Not sure why, but these smaller things seem to incite my Computer Rage the most.

same here, anyone?

---

### Post by ageofsteam on 2012-01-12
I tried this, and it doesn't seem to work...   This is the error I'm getting:

<code>
checking for intltool >= 0.40.0... ./configure: line 4284: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
</code>

I tried to update intltool, and it doesn't seem to be working...  (My panel has been having weird problems lately, though- every time I try to add the quick-lounge-panel it crashes...)

Is it possible to somehow make a package for this, as someone else said?

---

### Post by xteJCHL on 2013-10-11
In case you don't wanna build gnome-panel from sources, you can simple patch it in binary! 

Here is patch for Ubuntu 11.04 natty:
```

gnome-panel
00049D9E: 08 7F
00049FD0: 08 7F
0004A252: 08 7F

```

Disassembling, patching, backuping, replacing and restarting gnome-panel takes less then 5 minutes.
That is how i did it.

---

