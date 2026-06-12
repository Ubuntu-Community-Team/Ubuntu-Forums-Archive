---
title: "My Week with Ubuntu... and nothing else!"
date: 2005-08-14
forum: The Cafe
---

### Post by Donshyoku on 2005-08-14
I have been playing with Linux versions off and on for a few years.  Really ever since I discovered it and got the cable internet routed to my room.  I have been a pretty strong Windows user and became a bit of a gamer.  Lately, the gaming scene is becoming pretty stale, and I am more and more often booting into Linux to fiddle around.  I know a bit, but not as much as most, and I have decided to take the crash course and throw myself into Ubuntu (I have installed Hoary probably ten times, off and on).  With Ubuntu being the most enjoyable distribution for me, I have decided that this will be my first real forced learning experience with Linux.

So, please, pump me up and keep an eye on this thread as I post my joys and woes on this week.  

Right now, I am off to reformat the hard drive, giving Ubuntu the full chunk save for a small swap partition.  Whoo! :)

---

### Post by DJ_Max on 2005-08-14
Ok, I'll try my best....

We don't need to stinkin' spyware protections, we don't need no stupid anti-virus, we don't gotta pay for firewalls. YAY!!

We don't gotta reformat once a month, we can edit the kernel, YAY.

*As a cheerleader*
Give me a **U**, give me a **B**, give me a **U**, and so on and so..

*Jumps* GO Ubuntu and Open Source Software released under GPL, BSD and like licensing!!

---

### Post by Donshyoku on 2005-08-14
Yay, I'll never switch back now! :razz: 

I just got it all installed, so now I am working on setting up some programs, mainly Smeg for editing my menu.  There are just a few items in there, like the multiple volume monitors, that I can do without.

To make this thread interesting, I will just resay what I said in the other post.  I have all of the repositories in the standard Ubuntu installation set to universe, but I am still getting the error that Smeg cannot be found.  Any clues?

---

### Post by aysiu on 2005-08-14
Smeg may be in backports.
Did you do this?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Donshyoku on 2005-08-15
Worked, thanks!  All set now!

Just for the spirit of it, what are the backports?  Seems to me like they are mirrors for files from older versions of Ubuntu from what I have seen, but well... I haven't seen much, heh!

---

### Post by RastaMahata on 2005-08-15
[QUOTE=Donshyoku]Worked, thanks!  All set now!

Just for the spirit of it, what are the backports?  Seems to me like they are mirrors for files from older versions of Ubuntu from what I have seen, but well... I haven't seen much, heh![/QUOTE]
 backports alone are update versions taken from the next version in the works (breezy).
backports-extras are programs you couldnt find in official repositories because of legal problems (java, dvdcss, w32codecs, etc)...

---

### Post by Donshyoku on 2005-08-15
Thanks for the info!

Next question is really just cosmetic, but something I have been wondering about while browsing customization on gnome-look.org.

How do I change the splash screen for Ubuntu?  The files I downloaded are just images it looks like, unless I clicked the wrong links, but I am not exactly sure how it works or where to place the image file.

Thanks again!

---

### Post by RastaMahata on 2005-08-15
[QUOTE=Donshyoku]Thanks for the info!

Next question is really just cosmetic, but something I have been wondering about while browsing customization on gnome-look.org.

How do I change the splash screen for Ubuntu?  The files I downloaded are just images it looks like, unless I clicked the wrong links, but I am not exactly sure how it works or where to place the image file.

Thanks again![/QUOTE]
 [http://art.gnome.org/faq.php#q8](http://art.gnome.org/faq.php#q8)

> To change the splash screen, put the downloaded image in an unobtrusive location (since it will need to remain there as long as you want it to be the splash screen). A logical location would be ~/.gnome/splash.png (or .jpeg if the image is a JPEG). Then, edit the GConf key /apps/gnome-session/options/splash_screen using the Configuration Editor (Panel menu->System Tools->Configuration Editor) or the commandline tool gconftool-2.

---

### Post by Donshyoku on 2005-08-15
Thanks, for the help.  Off to try that now.  

Then, I am giving it a break for the night.  Tomorrow, my goal is to try DVD playback.  I have installed the libdvdcss2 package and the xine-ui package, but I am still not getting DVD playback in Totem, and I don't see Xine as a real player listed in my menu.  I am assuming, totally blindly, that it just installed some shared libraries or something.  

Nonetheless, I will research tomorrow before I post.  It seems that a lot of this is coming from the Ubuntu Guide and FAQs that you are linking too.  Sorry for not doing my research first, I simply find it easier to post here and then look.  If and when I don't find what I want, I can pop back on here for an answer.

Thanks again, and I am going to try the splash now.  Tomorrow is DVD playback! \\:D/

---

### Post by Donshyoku on 2005-08-15
First off, I am an idiot.  Xine is installed completely.  It placed itself into its own menu category.  Heh, heh!

Anyway, I got the splash working.  I have one more question about it though... it shows the custom splash, but I still have that ugly brown in the background of the splash.  So, is there a way to change this color or am I stuck with it?

Well, I am off for the night, I will be back tomorrow.  I am sure you just can't wait! :razz:

---

### Post by RastaMahata on 2005-08-15
[QUOTE=Donshyoku]First off, I am an idiot.  Xine is installed completely.  It placed itself into its own menu category.  Heh, heh!

Anyway, I got the splash working.  I have one more question about it though... it shows the custom splash, but I still have that ugly brown in the background of the splash.  So, is there a way to change this color or am I stuck with it?

Well, I am off for the night, I will be back tomorrow.  I am sure you just can't wait! :razz:[/QUOTE]
 dvd playback in totem: install the totem-xine package
change background color in splash screen: sudo gdmsetup (or System > Administration > second option (Configure Login Screen). Second Tab, "Background color":
[[IMG]http://img67.imageshack.us/img67/8708/pantallazoconfiguracindelapant.th.png[/IMG]](http://img67.imageshack.us/my.php?image=pantallazoconfiguracindelapant.png)

---

### Post by Donshyoku on 2005-08-15
Up and running with all of that, a big thanks again.

I don't have any dillemas right now, so I am going to focus on getting some of my music put on here.  Never tried OGG before, but I'll give it a shot and see what happens. :)

---

### Post by RastaMahata on 2005-08-15
good luck!

---

### Post by Donshyoku on 2005-08-15
OK, well, I have encountered something else with Sound Juicer trying to rip some CDs.

What happens is that I enter the information (for mixes) or allow it to update from the servers.  It begins to extract the music showing an unknown rip speed and unknown time remaining.  As soon as the correct rip speed and time remaining appear, the progress freezes.  I have to Force Quit to get it to cancel.  From there, I have to log off in order to access the disc again.  Once I log back on, the desktop is distorted, mainly the icons on the panels.  The computer then locks up, and I have to manually reboot.

Any thoughts on what the problem could be?  Should I try a different ripper, and if so, which one?

Thanks, again!

---

### Post by Stormy Eyes on 2005-08-15
Did you turn on DMA for your CD-ROM drive? The Ubuntu Guide covers DMA.

---

### Post by Donshyoku on 2005-08-15
I hate to be a drag, but I have been messing with Linux all day, and tonight I went ahead and installed Windows again.   Personally, it was my fault, I was messing with some things a bit too deep for me, I think, and ruined my Ubuntu installation to the point that it would not boot.  There were a few things that I wanted to do in Windows that just work for me.  I am going to give Ubuntu another shot here soon, and I must say that I learned a lot even in this short while of Linux and nothing else.  Right now there is a few things I want to do in Windows, and hopefully, I can give Linux another shot here soon.  

I know, I am bad. [-X 

I do wish to say thanks for all of the support.  And I am going to give it another shot, just not at this moment.  With everyone in the house going back to school and work tomorrow, I should have some time to veg alone and muddle through it.

Enabling DMA is top notch for the next run!

---

