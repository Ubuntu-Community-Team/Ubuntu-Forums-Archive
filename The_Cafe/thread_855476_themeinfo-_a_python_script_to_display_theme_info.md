---
title: "themeinfo- a python script to display theme info"
date: 2008-07-10
forum: The Cafe
---

### Post by dbbolton on 2008-07-10
Due to my constant stalking of the "Post Your Desktop" thread and lack of anything better to do, I wrote a python script to display information about the current user interface. I've got virtually no feedback about it through Sourceforge, so I decided that the Ubuntu Forums would be a good place to get some input.

Specifically, I want to have it tested by other users to find flaws, as well as get feature requests from other users. If anyone is interested in contributing, let me know and I will add you to the developer team on Sourceforge.

You can find links to download themeinfo and read documentation about it here: [http://themeinfo.sourceforge.net](http://themeinfo.sourceforge.net)

Thanks for reading :)

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/themeinfo-default-thumb.png[/IMG]]("http://themeinfo.sourceforge.net")

---

### Post by dracule on 2008-07-10
Nice!!!!!

---

### Post by BDNiner on 2008-07-10
I tried it out and it works great i just had a couple questions not relating to this script but not necessarily about it. first of all how do i add /home/bdniner/bin to my path, so that i can run commands that are in it for anywhere in the tree. and secondly you said in the README file that just run 'themeinfo' and the command should run, i have to run 'python themeinfo'. it is trivial but i wanted to know if i can have the same setup you have.

Thank you for the great work.

---

### Post by BDNiner on 2008-07-10
The first flaw that i have, maybe it is not a flaw but i don't have a desktop background. I use the vertical gradient plugin i guess it would be called in Appearance Preferences so that my background blends from one color to the next. so this option show up blank when using your script.

---

### Post by dbbolton on 2008-07-10
> **BDNiner said:**
> I tried it out and it works great i just had a couple questions not relating to this script but not necessarily about it. first of all how do i add /home/bdniner/bin to my path, so that i can run commands that are in it for anywhere in the tree. and secondly you said in the README file that just run 'themeinfo' and the command should run, i have to run 'python themeinfo'. it is trivial but i wanted to know if i can have the same setup you have.

Thank you for the great work.
That's a really good question. I actually have no idea how I got ~/bin in my path. I thought it was by default but I guess it got set auto-magically.

If you aren't sharing your computer with any other user who might want to use the script, you could just put it in /usr/bin and set the permissions so that you can write and execute it.

Another option is to put the script in your home folder, and then you can run it by typing ./themeinfo since the she-bang line in the script will make python execute it.

---

### Post by dbbolton on 2008-07-10
> **BDNiner said:**
> The first flaw that i have, maybe it is not a flaw but i don't have a desktop background. I use the vertical gradient plugin i guess it would be called in Appearance Preferences so that my background blends from one color to the next. so this option show up blank when using your script.
Which desktop environment?

---

### Post by BDNiner on 2008-07-10
gnome.

ty, putting it in the home directory allows me to run it. 

I have followed other people's tutorials where they have reference the /home/user/bin directory, and the fact that it is supposed to be there by default but none of the 3 ubuntu machines i use have that directory. i have created it but i don't know how to add it to the path of my executable directories.

---

### Post by smartboyathome on 2008-07-10
Would you be able to add E17 to this, so that it tells what theme we are using from E17? Then I would love this. :D

---

### Post by dbbolton on 2008-07-10
> **BDNiner said:**
> gnome.

ty, putting it in the home directory allows me to run it. 

I have followed other people's tutorials where they have reference the /home/user/bin directory, and the fact that it is supposed to be there by default but none of the 3 ubuntu machines i use have that directory. i have created it but i don't know how to add it to the path of my executable directories.
I added an option for GNOME users who don't have an image file as the background in version 0.4.4. It's on the downloads page now.

> **smartboyathome said:**
> Would you be able to add E17 to this, so that it tells what theme we are using from E17? Then I would love this. :D

I can, as long as E17 puts the name of your current theme in a text file somewhere on your computer. I don't know anything about E17 though. Do you know if it does?

(I'm having the exact same problem with Fluxbox)

---

### Post by Jesuses Left Leg on 2008-07-10
Nice theme script. Best one I've used so far. Works perfectly for XFCE.

---

### Post by monstermudder78 on 2008-07-10
Ok, stupid python question:  Why can't I get it to execute without typing 'python' first?
```
$ themeinfo
bash: themeinfo: command not found

```

```
$ python themeinfo

Ubuntu 8.04.1

  Metacity:              Human
  GTK:                   Clearlooks
  Font (Apps):           Sans 10
  Font (Terminal):       monospace 12
  Icons:                 JungleBlack
  Wall:                  792191425_ac00528d38_o.jpg

 Thursday 10 July 2008


```

---

### Post by dbbolton on 2008-07-10
> **monstermudder78 said:**
> Ok, stupid python question:  Why can't I get it to execute without typing 'python' first?
```
$ themeinfo
bash: themeinfo: command not found

``````
$ python themeinfo

Ubuntu 8.04.1

  Metacity:              Human
  GTK:                   Clearlooks
  Font (Apps):           Sans 10
  Font (Terminal):       monospace 12
  Icons:                 JungleBlack
  Wall:                  792191425_ac00528d38_o.jpg

 Thursday 10 July 2008


```
@BDNiner and @monstermudder78

Enter this command:
```

$PATH
```Or find PATH= in the output of this command:
```
env
```If it doesn't say "/home/USERNAME/bin", then you can add it to the path like so :

```
[FONT=monospace]
[/FONT]PATH=$PATH:$HOME/bin
export PATH

```Alternatively, you can put themeinfo in one of the directories already in your path.

---

### Post by Yes on 2008-07-10
Really neat, but since it seems to thing that I'm using Gnome it lists my Metacity theme rather than my Openbox theme.  I have run gnome-settings-daemon so that I can use the GTK theme and icons that I set in Gnome, is that why?

---

### Post by BDNiner on 2008-07-10
Thank you so much it works now. It took me a second to realise that i has to set bg_from_gconf = True and turn the other one off. Now I am looking at having the script display the hex values for the primary and secondary colors.

Well it displays the hex values from gconf instead of the ones from Appearances Preferences, which is not a big deal since you can also enter the values into gconf.

---

### Post by dbbolton on 2008-07-10
> **Yes said:**
> Really neat, but since it seems to thing that I'm using Gnome it lists my Metacity theme rather than my Openbox theme.  I have run gnome-settings-daemon so that I can use the GTK theme and icons that I set in Gnome, is that why?
Make sure that in the "Window Manager" options, you have:

```

include_mt = False
include_ob = True

```

---

### Post by Yes on 2008-07-10
There we go!

Really, really nice work :)

---

### Post by monstermudder78 on 2008-07-10
> **dbbolton said:**
> @BDNiner and @monstermudder78

Enter this command:
```

$PATH
```Or find PATH= in the output of this command:
```
env
```If it doesn't say "/home/USERNAME/bin", then you can add it to the path like so :

```
[FONT=monospace]
[/FONT]PATH=$PATH:$HOME/bin
export PATH

```Alternatively, you can put themeinfo in one of the directories already in your path.

Thanks!  The script worked perfect before, now it works perfect the way I want it to :D

---

### Post by dbbolton on 2008-07-10
> **Yes said:**
> There we go!

Really, really nice work :)

> **monstermudder78 said:**
> Thanks!  The script worked perfect before, now it works perfect the way I want it to :D

Thanks :)

---

### Post by dbbolton on 2008-07-11
I just added a new feature that will automatically configure the output if you are using one of the following setups:

gnome        
gnome+emerald
gnome+openbox

xfce
xfce+emerald
xfce+openbox

kde
kde+emerald
kde+openbox

kde4
kde4+emerald
kde4+openbox


You can download the newest version here: [https://sourceforge.net/project/platformdownload.php?group_id=233270](https://sourceforge.net/project/platformdownload.php?group_id=233270)

Hopefully it works for everyone (crosses fingers)

---

### Post by dbbolton on 2008-07-12
I added another feature to make custom configurations easier (in version 0.5.1). Now when you are setting up the script, you just have to type in a number to indicate your choice, rather than setting everything to true/false :)

---

### Post by BDNiner on 2008-07-15
Good work. i guess you changed the script again. did you remove the option for having horizontal or vertical gradients. i can't find it in the script and was going to add it again for my computer.

---

### Post by Lostincyberspace on 2008-07-15
> **BDNiner said:**
> I tried it out and it works great i just had a couple questions not relating to this script but not necessarily about it. first of all how do i add /home/bdniner/bin to my path, so that i can run commands that are in it for anywhere in the tree. and secondly you said in the README file that just run 'themeinfo' and the command should run, i have to run 'python themeinfo'. it is trivial but i wanted to know if i can have the same setup you have.

Thank you for the great work.
Check out here for how to add a place to your path.

[http://ubuntuforums.org/showthread.php?t=650327](http://ubuntuforums.org/showthread.php?t=650327)

---

### Post by dbbolton on 2008-07-15
> **BDNiner said:**
> Good work. i guess you changed the script again. did you remove the option for having horizontal or vertical gradients. i can't find it in the script and was going to add it again for my computer.
It's still there- option 2 under Wallpaper Options.

---

### Post by picpak on 2008-07-27
I've edited your script to detect Nitrogen's wallpaper, sakura's terminal font and the GTK set with lxappearance. You have to change the config appropriately to use these.

---

