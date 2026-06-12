---
title: "First Impressions of UCE"
date: 2012-08-07
forum: Ubuntu Christian Edition
---

### Post by Ardonel on 2012-08-07
This is a review of UCE 12.04, with my observations.

First thing I did upon downloading the image was to verify the md5. After imaging a usb stick with the iso file, I had it verify the installation media to ensure I had made a good image.

I have run UCE 12.04 on two different computers as a livecd/dvd, once as a VM in Virtualbox, and once as a full install as the only OS.

All installations exhibit an error on starting up with shotwell crashing with the following error:

"untiy-scope-shotwell crashed with IOerror in copyfile(): [Errno 2] No such file or directory: '/home/username/.shotwell/data/photo.db'"

Running in a live session, the users home is /home/Home. Running installed the home is /home/glevans2.

While I am not a huge fan of the unity desktop myself, it is very useable even by my 8 year old son. The fact that it is ubuntu at the core also means that any other DE/WM in the repos is available if you prefer something else.

The standard ubuntu backgrounds are ok, but the ones form wordtrace are excellent. (P.S. two of the stock ubuntu backgrounds are in there twice.)(Ubuntu & Tie my boat)

The package selection seems ok, but not knowing the end use for each individual situation, the games may or may not be necessary.

I would change the default program selection by adding Audacity for recording/editing audio, and possibly adding something like dropbox or spideroak for file sharing (yes, I know it has access to ubuntuone, but that may not be useful to people on a Microsoft platform).

The inclusion of a ppa manager is a nice touch, as well as having Dansguardian as an internet filter. I think having gimp is good, along with vlc media player. I haven't tested DVD playback yet, so will comment later.

For multimedia use at my old church, had to enable the medibuntu repos to install some of their apps. Not sure if we can have the repos installed and configured with no software installed, or just provide an easy pointer on how to add it and let the individual deal with the legality of the software for their use.

Overall, I think it is very adequate and customiseable. With the exceptions of any product specific branding, I find it very agreeable and acceptable, and look forward to seeing where the project goes.

This review started and finished before post-install script was known about by me. The review computer with a full install was a Gateway MT3705 laptop with 2 Gb of ram (you can google the rest of the specs if you really want to know).

---

### Post by stlsaint on 2012-08-07
EDIT: I will be patching shotwell to resolve the database issue. Problem is it is looking for a file that does not exist. After patch there will be no need to purge/reinstall anything with shotwell.

First off thank you very much for the review and feedback. I will address your issues accordingly.

1. In my opinion and experience shotwell is a mess. I have attempted to purge it from the install all together. Maybe they have fixed the scope by now. 
To test simple apt-get it: 
```
 sudo apt-get install unity-scope-shotwell
``` 
and that error should go away.

2. Thank you for the heads up on the wallpaper duplication...issue resolved.

3. As far as package selection we are already on a thin line with trademark usage so i will not be removing any default applications or anything that comes standard with vanilla ubuntu. 
I will take a look into audacity and see what its depends are and decide on a installation or not. More than likely it will be included in the post-installs script as an option to along with enabling medibuntu repos.

Again i thank you for the participation and all reviews and feedback is taken under serious consideration. Many new avenues are opened up with a post-install script which is why i sought to add it. Stay tuned! ;) 
Final release will come with these issues fixed.

---

### Post by linuxfan247 on 2012-08-07
I just sent a note to the "contact us" section about the boot issue, I had never heard of the christian issue till I found a link on the satanic ed. I like the theme & asthetics of course I felt guilt as a christian looking Sat-edition but, anyway I like creative distros not just the themes also, the features like in Ultimate edition this not hate just my opinion by the way I like ubuntu just cant get any current versions bought or downloaded to work on my pc just the old version seem to work.

---

### Post by stlsaint on 2012-08-08
Thank you linuxfan247 for you interest and comments. Please feel free to give feedback and participate in our forums.

---

### Post by skimo12 on 2012-10-27
I had a similar crash on startup with UCE 12.04. It just showed a crash dialog with unity-scope-shotwell. Unfortunately, I am not able to get a hold of the crash log. It was going to be sent to the developers by Ubuntu.

I ran the 
[COLOR=#000000][FONT=times new roman]sudo apt-get install unity-scope-shotwell[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]then 
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]sudo apt-get autoremove[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]This removed 
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Removing linux-headers-3.2.0-29-generic ...
Removing linux-headers-3.2.0-29 ...
Removing linux-headers-3.2.0-31-generic ...
Removing linux-headers-3.2.0-31 ...[/FONT][/COLOR]


Rebooted, and no more crash messages appeared. I guess this could be some kind of post-install step (sudo apt-get autoremove)

---

