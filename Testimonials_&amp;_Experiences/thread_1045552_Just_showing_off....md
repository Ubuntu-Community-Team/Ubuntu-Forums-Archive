---
title: "Just showing off..."
date: 2009-01-20
forum: Testimonials &amp; Experiences
---

### Post by spcwingo on 2009-01-20
my first cli build!  I couldn't be happier with Ubuntu.  What else could have resurrected this old Dell Optiplex GX110 easier or more beautifully?  This old machine was destined for the landfill before I felt pity for it and lugged it home.  I fired up a live CD and immediately realized that it wasn't picking up anything on the PCI riser card.  A quick stop by e-bay and $6 later the hardware was all sorted out.  Since this was now just a spare machine, I decided to try my hand at a cli build.  It only took 4 hours to get me a fully loaded desktop, but why stop there?  I tweaked a couple more days and here it is:

[IMG]http://i91.photobucket.com/albums/k306/spcwingo/screenshot-2.png[/IMG]

[IMG]http://i91.photobucket.com/albums/k306/spcwingo/usage.png[/IMG]

[IMG]http://i91.photobucket.com/albums/k306/spcwingo/processor.png[/IMG]

As you can see, the specs are kind of low, but this thing is surprisingly quick.  Ya'll let me know what you think.

---

### Post by wolfen69 on 2009-01-20
great job. it's amazing how you can revive an old machine with a modern os. btw, what is the base desktop environment? i have done cli installs before, but always used xfce. looks awesome though.

---

### Post by Sorivenul on 2009-01-20
LXDE, yes? Your desktop looks nice and functional. Simple. Maybe you can build *my* next system. ;) Just kidding. Great work!

All in all a very nice setup, especially for your first time doing the CLI install. You can tell you thought it through as opposed to just throwing it together.

Cheers!

---

### Post by stalkingwolf on 2009-01-21
Nice.  What is the background picture?

---

### Post by spcwingo on 2009-01-21
Thanks guys.  @ wolfen69 and Sorivenul, It's LXDE.  I've never used it before this build.  I'm pretty impressed with it so far.  I have found it very light, simple, and stable.  @ stalkingwolf:  My background is a pic I got while in Baghdad, Iraq.  It's called, simply, the crossed sabres.  It's where Saddam used to have troop reviews, etc.  It's located in downtown Baghdad @ the now called "Green Zone".

---

### Post by zero244 on 2009-01-21
Looks great.........the Ubuntu variations are the best.
When you run Ubuntu no need for virus software...........if you change some hardware you dont have to call MS and hope they give you a new registration number.
Good luck

---

### Post by Crafty Kisses on 2009-01-21
Very nice my friend. :)

---

### Post by spcwingo on 2009-01-21
Thanks, guys.  The nagging little thing I have left is right after usplash stops and before X starts it gives a few lines of text.  It does the same thing right after X is exited and before usplash starts.  I can't figure out how to clean that up.  ](*,)  It's really no biggie...just irritating.  Any suggestions on how to correct this?

---

### Post by stalkingwolf on 2009-01-22
> @ stalkingwolf: My background is a pic I got while in Baghdad, Iraq. It's called, simply, the crossed sabres. It's where Saddam used to have troop reviews, etc. It's located in downtown Baghdad @ the now called "Green Zone".

Thats what I thought.

Well done and Thank You.

---

### Post by albinootje on 2009-01-24
> **spcwingo said:**
> 
As you can see, the specs are kind of low, but this thing is surprisingly quick.

Can you give some more details about how you installed this ?

Did you compile wbar (the dock) from source, or did you find a precompiled deb package somewhere ?
What are you using as web browser ?

---

### Post by albinootje on 2009-01-24
Okay, found the deb for wbar, and after that a wbar howto :
[http://www.deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/](http://www.deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/) :)

---

### Post by spcwingo on 2009-01-24
Sorry I'm just now getting back, albinootje.  Yes, I did find a deb for it.  After installing I wrote a start up script and made a .desktop file pointing to the script and placed the .desktop in the /home/*USER*/.config/autostart folder.  I also copied the dot.wbar file from /usr/share/wbar to /home/*USER*/ and renamed it .wbar.  If you need the script or the .desktop file just let me know and I'll post them.

---

### Post by gjoellee on 2009-01-24
You can fix the "old" interface running root/sudo applications by using this command if you want to:
```
sudo cp /home/$USER/.themes -C /root/.themes && sudo cp /home/$USER/.icons -C /root/.icons
```

---

### Post by steveneddy on 2009-01-24
Sweet! Looks great!

---

### Post by FrankVdb on 2009-01-31
Congrats! Good example of how to install Ubuntu on a low-spec system. 

I guess you started out with Ubuntu Server and went from there?

---

### Post by spcwingo on 2009-01-31
> **FrankVdb said:**
> Congrats! Good example of how to install Ubuntu on a low-spec system. 

I guess you started out with Ubuntu Server and went from there?

I started out with the mini CD, so, pretty similar.  The biggest difference being it's not running the server kernel.

---

### Post by FrankVdb on 2009-01-31
Thank's to your contribution, I just discovered there is indeed something like a "mini Ubuntu":

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's less than 10 MB, pretty incredible. It's even smaller - heck, a LOT smaller - than Puppy Linux or Damn Small Linux. Very nice.... Think I'll try this on an old machine gathering dust over here. Pity there are no minimal specs mentioned but I'll try.

Is LXDE faster than Openbox or Enlightenment? I have never tried either of them, you have made me curious...

---

### Post by spcwingo on 2009-01-31
> **FrankVdb said:**
> Thank's to your contribution, I just discovered there is indeed something like a "mini Ubuntu":

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's less than 10 MB, pretty incredible. It's even smaller - heck, a LOT smaller - than Puppy Linux or Damn Small Linux. Very nice.... Think I'll try this on an old machine gathering dust over here. Pity there are no minimal specs mentioned but I'll try.

Is LXDE faster than Openbox or Enlightenment? I have never tried either of them, you have made me curious...

While the iso is ~10MB the installed size is much bigger.  Most of the components installed are downloaded and installed.  It more like a Debian net install CD.  To answer your question about LXDE, it's not faster than openbox.  As far as E-16/E-17...I haven't used it at all.  Too much eye candy.  I'm more of a simplistic guy.  If light and fast is what you're after, you might want to give JWM a shot.  If you would like a guide to get you started, this is what got me motivated to give a cli build a shot:

[http://wiki.dennyhalim.com/ubuntu-minimal-desktop]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop")

Good luck and don't forget to post a few screenshots when it's finished.

---

### Post by spcwingo on 2009-02-04
> **spcwingo said:**
> Thanks, guys.  The nagging little thing I have left is right after usplash stops and before X starts it gives a few lines of text.  It does the same thing right after X is exited and before usplash starts.  I can't figure out how to clean that up.  ](*,)  It's really no biggie...just irritating.  Any suggestions on how to correct this?

For those wondering I fixed text before and after x by removing SLIM and installing GDM.  I really hate having to install GDM, but I guess "ya gotta do whatcha gotta do".

---

### Post by pauwl on 2009-02-05
Looks good indeed.

How're your boot times using older HW? Any tweaks there?

---

### Post by spcwingo on 2009-02-05
> **pauwl said:**
> Looks good indeed.

How're your boot times using older HW? Any tweaks there?

It's not too bad considering this thing POSTs at half the speed of smell.  I'd say around 1 min from power on to GDM.  No tweaks, just pure 800 Mhz muscle.  :lol:

---

