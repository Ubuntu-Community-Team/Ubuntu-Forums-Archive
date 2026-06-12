---
title: "Ubuntu One Download Location"
date: 2010-05-10
forum: Ubuntu One (CLOSED)
---

### Post by lfitz on 2010-05-10
Hi, I found out where Ubuntu One downloads music from the music store.
[I]/home/user/.local/share/ubuntuone/Purchased from Ubuntu One/

[/I]I would like to change this folder to:
*/home/user/Music/*

Is this done in RhythmBox or Ubuntu One?  Also, I moved the MP3s from the default location and they disappeared from my cloud storage, is it possible to turn this off?  With a custom or default location?

When does the sync take place?  I know its after the purchase but it seems to take a while to start.

All of this is for 10.04.

Also, I googled this but couldn't find anything related.  Thanks for the input!

---

### Post by joshuahoover on 2010-05-11
> **lfitz said:**
> Hi, I found out where Ubuntu One downloads music from the music store.
[I]/home/user/.local/share/ubuntuone/Purchased from Ubuntu One/

[/I]I would like to change this folder to:
*/home/user/Music/*

Is this done in RhythmBox or Ubuntu One?  Also, I moved the MP3s from the default location and they disappeared from my cloud storage, is it possible to turn this off?  With a custom or default location?

Please see this FAQ about why we store the files in a hidden folder: [https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?](https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?)

> When does the sync take place?  I know its after the purchase but it seems to take a while to start.

It should be fairly quick. We've been trying to get the file sync service performing better overall as the load from new users with 10.04 and higher usage of file sync in general has put a lot of stress on our servers. Is it taking minutes or hours for you to see song purchases to appear on your computer?

Thank you,

Joshua

---

### Post by lfitz on 2010-05-11
> **joshuahoover said:**
> 
It should be fairly quick. We've been trying to get the file sync service performing better overall as the load from new users with 10.04 and higher usage of file sync in general has put a lot of stress on our servers. Is it taking minutes or hours for you to see song purchases to appear on your computer?

At first, meaning when I first installed Lucid ( the day it came out :) ) the time seemed completely random.  Now, it starts quickly... within a few minutes or so.  

Thanks for the reply about the hidden folder!

Liam

---

### Post by tjwolf on 2010-05-25
> **joshuahoover said:**
> Please see this FAQ about why we store the files in a hidden folder: [https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?](https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?)

Joshua

Hi Joshua,
Like the original poster, I would like to put my purchased music in the same directory as the rest of my collection ($HOME/mp3).  Keeping things centralized not only makes maintenance/backup easier, but it's also important when it comes time to run iTunes (via VirtualBox) so I can sync my family's iphones/itouches (if there's now an easy way in Linux to sync without itunes I'm all ears).  Anyway, keeping saved music "in the cloud" isn't really a priority for me.  I'm buying from the Ubuntu One music store (and Amazon) because I can't stand the iTunes music store.

Any help/info on how to tell Rythmbox and/or UbuntuOne to use my desired download location would be much appreciated.

Thanks,
Tom

---

### Post by joshuahoover on 2010-05-27
> **tjwolf said:**
> Hi Joshua,
Like the original poster, I would like to put my purchased music in the same directory as the rest of my collection ($HOME/mp3).  Keeping things centralized not only makes maintenance/backup easier, but it's also important when it comes time to run iTunes (via VirtualBox) so I can sync my family's iphones/itouches (if there's now an easy way in Linux to sync without itunes I'm all ears).  Anyway, keeping saved music "in the cloud" isn't really a priority for me.  I'm buying from the Ubuntu One music store (and Amazon) because I can't stand the iTunes music store.

Any help/info on how to tell Rythmbox and/or UbuntuOne to use my desired download location would be much appreciated.

Thanks,
Tom

Hi Tom,

It's not possible to tell Ubuntu One to save music purchased from the store to a different location. You should be able to copy your music from ~/.ubuntuone/Purchased from Ubuntu One to your $HOME/mp3 folder and then you'd need to remove the duplicate entries for that music from Rhythmbox manually.

Thanks,

Joshua

---

### Post by greenarrow-stef on 2010-10-31
I just make a symbolic link to access it more conveniently:

ln -s $HOME/.local/share/ubuntuone/Purchased\ from\ Ubuntu\ One $HOME/Music/UbuntuOne

---

### Post by Plecebo on 2010-11-18
creating a symbolic link to the location creates another issue. Mainly that Rhythmbox now sees the files double in my library. 

Once at the .local location and once at the Music location. 

In my opinion this is a big problem for ubuntu one. For me it means I rip the files out of the .local location and paste them into the Music location. I like letting Rhythmbox manage my music, and I also like to be able to have all my music in one location (not .local and Music). 

I hope another method is worked out soon, under this method I'm a lot less likely to reach for Ubuntu One when Amazon is so much easier.

---

### Post by jgandt on 2011-03-08
> **Plecebo said:**
> creating a symbolic link to the location creates  another issue. Mainly that Rhythmbox now sees the files double in my  library. The UbuntuOne Music Store plugin accesses the gnome configuration at startup and manually adds the music location into the config.

Now that's just silly if you're a bit more slick and want to put all of your music in ~/username/Music

[B]Here's what I did:

DISCLAIMER:
execute this hack at your own risk. I take zero responsibility for any actions you may take based on the below (or above). Don't attempt this if you really don't know what you're doing...
[/B]
**1) shutdown rhythmbox (make sure the process is no longer running!)**

**2) symbolic link to ubuntuone music directory:**

ln -s /home/<username>/.ubuntuone/Purchased\ from\ Ubuntu\ One/   /home/<username>/Music/Purchased\ from\ Ubuntu\ One


[B]3) unset rhythmbox's default library location:

[/B]gconftool-2 --unset /apps/rhythmbox/library_locations
(rhythmbox should reset this value back to ~/Music by default on startup. if it doesn't you can re-add it in the rhythmbox preferences)

[B]WARNING:
HACK BELOW:[/B]
**4) manually edit the ubuntuone music store plugin:**

comment out lines 207-213 (add a '#' to the beginning of the line) (THESE LINES MAY CHANGED OVER TIME!) in /usr/lib/rhythmbox/plugins/umusicstore/MusicStoreWidget.py
( must sudo to edit it )
(It's essentially the bottom 7 lines of the add_u1_library function)


restart rhythmbox. you may have to remove the songs in your library (don't delete the files dingbat, just remove them from your library)

'tis all.

---

