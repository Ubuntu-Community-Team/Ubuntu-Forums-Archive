---
title: "Gnome Adds Fading Between Backgrounds"
date: 2009-02-06
forum: The Cafe
---

### Post by Vadi on 2009-02-06
Found today via MadsRH [blog post]("http://anotherubuntu.blogspot.com/2009/02/gnome-adds-fading-between-backgrounds.html") - Gnome has accepted patches from Ray Strode to make the backgrounds switch smoothly when changing the wallpaper.

**Video: [http://ezri.org/nautilusfade.ogv](http://ezri.org/nautilusfade.ogv)**

---

### Post by steeleyuk on 2009-02-06
Fedora has had something similar for a while, though not sure how long ago it was introduced.

---

### Post by billgoldberg on 2009-02-06
Things like that are important to give the DE a more finished look.

---

### Post by FuturePilot on 2009-02-06
Very nice. :D

---

### Post by Hells_Dark on 2009-02-06
I like that kind of small update :)

---

### Post by Paqman on 2009-02-06
Nice! :D

---

### Post by Polygon on 2009-02-06
now we just need a time based wallpaper system (like what mac os x has) and use that transition to fade between the wallpapers and i will be happy =)

---

### Post by days_of_ruin on 2009-02-06
Nice.

---

### Post by ByteJuggler on 2009-02-06
> **Polygon said:**
> now we just need a time based wallpaper system (like what mac os x has) and use that transition to fade between the wallpapers and i will be happy =)

It's already possible to specify an xml file as a wallpaper which switches wallpapers at given times.  My desktop is set up with the ["New Wave"]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave") theme, with the ["Day of Ubuntu"]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=day_of_ubuntu.tar.gz") wallpaper, which does this.

---

### Post by MikeTheC on 2009-02-06
About time. One step closer to looking as refined as Aqua...

---

### Post by billgoldberg on 2009-02-06
> **Polygon said:**
> now we just need a time based wallpaper system (like what mac os x has) and use that transition to fade between the wallpapers and i will be happy =)

This is already possible in kde 4 and it's also possible in gnome, but you'll need to get your hands dirty a bit.

---

### Post by pt123 on 2009-02-06
anyone know what happened to having the ability to have different wallpapers on the workspace
[http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/)

[http://gsocblog.jsharpe.net/](http://gsocblog.jsharpe.net/)

---

### Post by Islington on 2009-02-06
> **pt123 said:**
> anyone know what happened to having the ability to have different wallpapers on the workspace
[http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/)

[http://gsocblog.jsharpe.net/](http://gsocblog.jsharpe.net/)

This idea was marked as being in development the 11 May 08. Target release: Ubuntu 9.04 Jaunty Jackalope.

---

### Post by pt123 on 2009-02-06
> **Islington said:**
> This idea was marked as being in development the 11 May 08. Target release: Ubuntu 9.04 Jaunty Jackalope.

well the blog hasn't been updated the developer seems to have disappeared, Note it was slated for Ibex.

---

### Post by Paqman on 2009-02-07
> **Polygon said:**
> now we just need a time based wallpaper system (like what mac os x has) and use that transition to fade between the wallpapers and i will be happy =)

Check out gnome-look.org, I think there's a few solutions to do this there.

---

### Post by madjr on 2009-02-07
> **billgoldberg said:**
> This is already possible in kde 4 and it's also possible in gnome, but you'll need to get your hands dirty a bit.

another reason to use kubuntu 9.04 once it's out of beta :)

i hope they polish it clean this time like other distros

---

### Post by Polygon on 2009-02-07
> **Paqman said:**
> Check out gnome-look.org, I think there's a few solutions to do this there.

i mean a real GUI interface built into gnome, not some script.

---

### Post by Markske on 2009-03-26
How can I disable this fade effect?? 

coz every time I switch background the system has a hick-up (Xorg takes almost 2sec 100%cpu)

I use my own script to switch background every minute
/usr/bin/gconftool --type String -s /desktop/gnome/background/picture_filename "/...jpg"

but sins the fade effect its anoing

---

### Post by 3rdalbum on 2009-03-26
KDE 4 not only has this, but it has lots of lovely eye candy; when you switch between web tabs in Konqueror, it actually crossfades the page; awesome!

I think Gnome should focus one release on eye-candy so they have more flexibility to change the infrastructure to allow it. A nice-looking, quick-starting Gnome desktop might actually make me switch back to Gnome :-)

---

### Post by Vadi on 2009-03-26
I don't think Gnome's goal is to draw users away from KDE.

---

### Post by Redache on 2009-03-26
> I don't think Gnome's goal is to draw users away from KDE.

I agree, Gnome is aiming for a different user base than KDE. I prefer Gnome to KDE and even though KDE 4 is nice I just don't like the Workflow.

I personally don't see the big deal with having Wallpaper Fading.

---

### Post by crayzeewulf on 2009-04-29
> **Markske said:**
> How can I disable this fade effect??

I wish there was a way to disable this. Besides taking up CPU cycles, which some users may not be willing to give up, it also interferes with the 'WallpaperClock' screenlet. Everytime the screenlet updates the wallpaper, the screen fades back to an ugly brown color and then fades to the updated wallpaper. Ugh.

---

### Post by dcstar on 2009-09-03
> **crayzeewulf said:**
> 
........
Everytime the screenlet updates the wallpaper, the screen fades back to an ugly brown color and then fades to the updated wallpaper. Ugh.

IIRC you can change that by setting the Solid background colour to black from the default.

---

### Post by Exodist on 2009-09-03
> **Vadi said:**
> Found today via MadsRH [blog post]("http://anotherubuntu.blogspot.com/2009/02/gnome-adds-fading-between-backgrounds.html") - Gnome has accepted patches from Ray Strode to make the backgrounds switch smoothly when changing the wallpaper.

**Video: [http://ezri.org/nautilusfade.ogv](http://ezri.org/nautilusfade.ogv)**

THANK GOD!!

OSX has had this for over 6 years now.. Where supposed to be ahead of the crowd. This is past due but very welcome.

---

### Post by stwschool on 2009-09-03
For a lot of you guys on this thread, sudo apt-get install wallpaper-tray and put that tray on your panel. All your wallpaper needs are solved. Small, uses practically no memory/processor, job done. Gives smooth transitions, timed changes, etc.

---

### Post by Tristam Green on 2009-09-03
> **Exodist said:**
> THANK GOD!!

OSX has had this for over 6 years now.. Where supposed to be ahead of the crowd. This is past due but very welcome.

um...what crowd?  Windows didn't implement this until Vista in 2007, and that's a far bigger crowd than OSX.


Also, OP is 7 months old.

---

### Post by MasterNetra on 2009-09-03
I have mixed feeling about the wallpaper transition thing, yea its a nice affect but does crunch CPU cycles. I can live with it, but I also can live without it.

---

### Post by aaaantoine on 2009-09-03
I was going to say "Ubuntu has been doing this for a while."  Then I saw the post date.

KDE does this too, by the way.

Also I've noted (after observing a Mac at a presentation) that Mac OS fades out before switching screen resolutions.  Such elements of polish do make a difference.

---

### Post by Warpnow on 2009-09-03
This in no way, shape, or form improves my user experience.

If useless things keep getting added in I'm going to switch to XFCE.

---

