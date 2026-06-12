---
title: "How To: Make Ubuntu 14.04 Look Better [GNOME]"
date: 2014-05-17
forum: Tutorials
---

### Post by creeperslayercraft on 2014-05-17
This will be an in-depth guide on making Ubuntu look pretty. However if you want the summarized version of it, watch this [SIZE=6]_**[video]("https://www.youtube.com/watch?v=lBCTk0XfD_Q")**_[/SIZE] on YouTube.
Unlike Unity, Gnome is pretty stylish to begin with. [SIZE=1]I'm not hating Unity, I just prefer Gnome over it since it's really responsive.[/SIZE] Here are 10 things you can do to even make it more stylish!

Here is the final look: And uh..don't mind the LoL forums tab.
[IMG]http://i.imgur.com/gGuoiK4l.png[/IMG]

_**SCREENSHOTS WILL BE ADDED SOON!**_


**#1 Update Gnome Shell**
I highly recommend updating Gnome since the default Gnome is 3.10. Having new features on is a fun thing to have.
_Note - one line at a time!_

```
sudo apt-get update && sudo apt-get dist-upgrade
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo apt-get update && sudo apt-get dist-upgrade
```

If you don't like it, it's cool! You can still do the 9 other things. 
```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:gnome3-team/gnome3-staging
```
[B]
#2 Install Themes[/B]
This is basically the heart of everything. Find a nice theme in the interwebs! If I were to choose then they would be the [Iris Light]("http://bit.ly/1iqVIvD") and [Iris Dark]("http://bit.ly/1o9TyEl").
Installing them is really easy to do.
First of all download the theme files, then extract them to a folder of your choice. Open up the terminal and type the following code. 
_Note - replace the text in bold with the actual theme folder location._
```
sudo cp -r **/theme/file/directory/** /usr/share/themes/
```
Once you've done that, run the Tweak Tool (it should be installed by default and change the themes. 

**#3 Install Icons**
Quite similar to #2 and it should be not much of a hassle. I really love the Numix Icon set and I suggest you to try it out. 
_Note - one line at a time_

```
sudo add-apt-repository ppa:numix/ppa
sudo apt-get update && sudo apt-get install numix-icon-theme
```
If you've got another icon set and want to install it (if they don't have a PPA for that), read [this post]("http://ubuntuforums.org/showthread.php?t=251567") since it pretty much covers up everything on installing icons.

#4 Installing a Dock
Since the dock is in the activities area (and you want to open, swap and close through programs with style), install Docky or Cairo Dock. Both of those docks are good but I prefer Docky.

```
sudo apt-get install docky
```

**#5 Getting a fantastic wallpaper**
If you find a wallpaper that matches with your theme and icon set, then that's awesome! [URL="http://www.lifehack.org/articles/technology/100-awesome-minimalist-wallpapers.html"]
Here[/URL] are **100** minimalistic wallpapers that you must definitely check out.

**#6 Conky-Harmattan **
This is definitely one of the best looking desktop modules.
Note that you need to install [conky]("apt:conky-all") and [curl]("apt:curl") for this program to work properly. Once you've done that, go ahead and [download]("http://www.deviantart.com/art/Conky-Harmattan-426662366") it.
There's an instructions manual that comes with the archive so I don't think it's necessary to post it here.

**#7 Changing the color schemes**
It's weird if your theme and color scheme don't match. You can easily 'harmonize' those 2 with [Elegance Colors]("http://bit.ly/1m1nYWY").
URGENT NOTE - You need to have the [User Theme extension]("http://bit.ly/1g1ND1M") installed! Visit GNOME extensions and get it installed. Without it, the changes won't apply. (correct me if I'm wrong!)
```
sudo add-apt-repository ppa:satyajit-happy/themes 
sudo apt-get update 
sudo apt-get install gnome-shell-theme-elegance-colors gnome-shell-extensions
```

Once you have it opened, just select the GTK Theme and hit apply! If the changes doesn't take place even with User Theme installed, alt + f2 then type 'r' to restart the interface.

**#8 Adding Transparencies**
Run Elegance Colors>Panel and click on the gradient (the one with 2 gradients beside each other) then select the totally transparent color. Repeat the same thing for the other one. Now it should look pretty!

**#9 Activities Dash --> Dock**
If you're fine with the dock in the activities panel, except you hate going through the process of showing it, you can now transfer the dock to the front page.
Just install the [Dash to Dock gnome extension]("https://bit.ly/RKt3HI") and it will magically change place! 

**#10 Move the clock/calendar from the center to the right**
This is something very trivial but it was a big change for me. By default the clock/calendar is placed at the center. FRIPPERY MOVE CLOCK MAKES THINGS SUPER EASY! Just switch it on (it's a [gnome extension]("http://bit.ly/1owLaMl")) and it should move by itself!

---

