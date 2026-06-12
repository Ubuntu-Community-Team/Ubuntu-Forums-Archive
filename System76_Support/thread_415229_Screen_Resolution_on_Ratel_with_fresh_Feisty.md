---
title: "Screen Resolution on Ratel with fresh Feisty"
date: 2007-04-20
forum: System76 Support
---

### Post by iba10753 on 2007-04-20
Well, I got in a little over my head last night and this morning.  I've got a new Ratel with the NVidia video chipset and my own 20" flat screen monitor.  Since early this morning, I've been playing with Wine and Crossover to see how I'm going to run some of the Windows applications I've got to keep around for business reasons.

At some point, a restart just hung with the speakers shouting out the first few notes of the login sound.  The desktop never did appear.  Multiple shutdowns and restarts resulted in the same behavior each time.  So, it was time for me to admit that I screwed something up big-time.

I had already downloaded the Feisty Live CD yesterday and thought this would be a great opportunity to reload my system from scratch.  That installation went quickly and without a hitch.  After logging in, I could get no better than 1024x768 resolution.  However, I remembered that the NVidia driver was one of those "Restricted" drivers so I went to the Restricted Driver Manager and found that I could download the NVidia restricted driver.  That download and install went without a hitch also.

However, I still can't get anything higher than 1024x768 resolution and about 54Hz refresh.  I seem to remember that the resolution I was able to achieve after taking delivery of the Ratel was 1600x1200 with at least 60Hz refresh.

Is there anybody who can throw me a clue about how to get this puppy back up to the higher resolutions that I know it's capable of?

Thanks,
Ben Askew

---

### Post by IgnacioMiller on 2007-04-20
Did you reinstall the System76 driver? [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

And if that does not offer you more choices then you'll have to edit your xorg.conf for the higher resolution and refresh rate: a process that I am by no means an expert in. I'll leave that to someone else to help you with. However, you should be able to find a how to on the forum pretty easily just by searching for your desired resolution.

---

### Post by iba10753 on 2007-04-20
Thanks, Ignacio.  Yes, I have loaded the System76 Driver CD but Feisty has support for the Ratel without the need for the CD.  In other words, there is nothing on the System76 Driver CD that is available to fix this problem.

What would be really great is if someone at System76 could gather up the factory xorg.conf file from one of their Ratel builds and email it to me.  I'd probably have to buy someone a cold one the next time I'm in Denver!

Thanks again,
Ben

---

### Post by thomasaaron on 2007-04-20
Hi, iba.

Try this from a terminal:

sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
ctrl-alt backspace to reset

Then go to:
System > Preferences > Screen Resolution and select appropriate resolution.

---

### Post by iba10753 on 2007-04-20
Thanks, Tom.

The apt-get told me that I had the latest version.
The dpkg-reconfigure surprised me with the amount of stuff I had to make decisions on but I tried my best to take most defaults.  I chose "nv" as the video device.
Ctrl-Alt-Backspace didn't allow me to change the resolutions above 1024x768.

I've got it up to 1600x1200 now.  Here's how I did it:

Went into the Restricted Drivers Manager and unchecked the NVidia.  Closed and restarted.
Edited the xorg.conf file to have "1600x1200" in each of the appropriate lines.
Went back into the Restricted Drivers Manager and checked the NVidia.  Closed and restarted.
Upon restart, I was able to choose as high as 1600x1200 with 50Hz refresh.  If I choose to go with lower resolution, I usually get choices of slightly higher refresh rates.

It wouldn't hurt my feelings to get an original Ratel xorg.conf file off of the Feisty build only because I have no educated idea what I did to get it working.  However, it's operating like it should be so I'll just have to quit being so anal about it for now.

Thanks again,
Ben

---

### Post by thomasaaron on 2007-04-23
There should have been an nvidia option in the dpkg-reconfigure program. It's not the same as nv.

---

### Post by iba10753 on 2007-04-23
Yes, there was, but I had seen so many references to "nv" in other threads I checked out before asking my initial question....I opted to go that route.  I'll go through the whole routine again and choose nvidia this time.  That way, I'll at least know that I'm configured the way I'm supposed to rather than the lucky guess I somehow ended up with.

Thanks again,
Ben

---

