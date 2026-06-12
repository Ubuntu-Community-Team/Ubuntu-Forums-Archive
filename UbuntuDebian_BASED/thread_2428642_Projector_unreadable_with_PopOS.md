---
title: "Projector unreadable with PopOS"
date: 2019-10-07
forum: Ubuntu/Debian BASED
---

### Post by tomtom447 on 2019-10-07
So I think this is an issue with sort but my projector looks blurry and the text is nearly invisible on any background at any resolution. The only way to get around this is if I set the text size to 4.50, overscale the screen to 200% (making windows extend off screen), with the resolution at 600X800 and even then its bad. The projector is set to HD and on both Windows and Android it looks fine. I have tried using a monitor as a second display and for a second it looks better until something updates it or moves on screen. I'm not sure if I should replace X or the desktop environment or if I need a driver. Perhaps the projector isn't being detected correctly. I do have a HDMI switch on the projector if that's the issue idk. Any help please?

---

### Post by Autodave on 2019-10-07
Could you give us some info on your system?  How are you connecting the projector to the computer?

---

### Post by tomtom447 on 2019-10-07
I’m connecting through a Display port to HDMI adapter to a HDMI cable for the projector. The projector is a Spacekey 1080P (RD810). The computer is a mini PC with a Quad Core i5-3470 16GB ram, no graphics card. I have PopOS (for better Steam support), Mythbuntu (with Plex), Android and Windows (came with the system, don’t really use but keep it just in case). I might get a graphics card if I can find one that is both low profile, short and runs on low power as the power supply is 440W but I don’t trust that rating.

---

### Post by QIII on 2019-10-07
Moved to Ubuntu/Debian BASED.

---

### Post by TheFu on 2019-10-08
Projectors support specific resolutions and specific refresh rates.  So, if you want to use a computer to drive the projector, then you should set the supported resolution and refresh rates.

I find using **lxrandr** the easiest tool for that, but don't know of your OS has that tool in the repo. You can force it with **xrandr**, a CLI tool.  I use a project at home to playback media, but use a raspberry pi for the playback.  I also give Linux presentations around the world and run into all sorts of projectors.  Generally, the 1920x1080@60 hz *just works*.

---

### Post by tomtom447 on 2019-10-08
Well both PopOS and Mythbuntu are based on Ubuntu/Debian. So repos aren’t going to be a problem. The projector is based on Panasonic hardware and has variable resolutions and refresh rates but “should work with” 1080P at 60Hzs. As stated it works fine on most res in Windows and Android, so I’m just wondering if it has to do with the x windowing system drivers or the DE.

---

### Post by TheFu on 2019-10-08
> **tomtom447 said:**
> Well both PopOS and Mythbuntu are based on Ubuntu/Debian. So repos aren’t going to be a problem. The projector is based on Panasonic hardware and has variable resolutions and refresh rates but “should work with” 1080P at 60Hzs. As stated it works fine on most res in Windows and Android, so I’m just wondering if it has to do with the x windowing system drivers or the DE.

Nope.  Purely resolution and refresh rates. Nothing else matters.

---

### Post by tomtom447 on 2019-10-08
The projector seems to switch to 720i 60Hzs but even that doesn’t work. I tried LXDE and LXQT with Lxrandr but still the same. Actually in when editing in gnome, in monitor settings I get a black box under the window that goes away when I open another window.
When I said it looks blurry I should clarify that it looks like much of the image seems missing like parts of the letters and pieces of everything, it also looks blurry like bad prescription glasses.
It gets better for a second after changing the res but as soon as anything moves its back to unreadable.
I don’t think it’s just resolution.

---

### Post by TheFu on 2019-10-08
A few stupid questions.

Is the projector in focus?  One of my projectors needs about 2 min to warm up, so if it gets out of focus for any reason, I know to wait a few minutes before bothering to focus.

Is 720i supported?  That isn't a normal resolution for projectors that I'm aware.  720p is the standard.  Get out the projector manual, pick one of those resolutions. Probably one of the 1080i or 1080p ones would be best.

The Display Port ---> HDMI converter needs to be "active".  I had some issues with a converter (display port -- VGA) because the adaptor didn't pass through the EDID information from the monitor back to the GPU.  Ended up having to pull the monitor EDID data using a different computer, store the data in a binary file, then force the GPU to use that EDID file.  It was a pain.  The converter specifically claimed to support my 1200p resolution, but when I pulled the EDID data going through it, it only showed 1080p as the highest resolution.  Display Port is a pain.  Wish I didn't buy a GPU that didn't have VGA support.

---

### Post by tomtom447 on 2019-10-08
The projector is in focus but it might have some additional settings to adjust to fine tune things.

The projector lists supported resolutions from 800x600 to 1920x1080.

So how do I get EDID information? I don’t have a dedicated graphics card so I’m not to sure how the Intel integrated gpu is managed by X. I’m also wondering how something like Xvesa or XFree86 would do.

---

### Post by TheFu on 2019-10-08
The manual, the REAL manual, will list all the supported display modes, probably in a table.

You'll need to get comfortable web searching for some answers.  "linux edid" is the search I'd use.  I don't remember the command used 7 months go, 5 times.  Because I have an nvidia card, the way I forced the correct EDID information to be used is proprietary and only for nvidia. Sorry.

That's really all I can offer. Good luck.

---

