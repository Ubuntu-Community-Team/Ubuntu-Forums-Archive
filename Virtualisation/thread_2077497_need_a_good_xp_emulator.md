---
title: "need a good xp emulator"
date: 2012-10-28
forum: Virtualisation
---

### Post by majorburt on 2012-10-28
i need a good Windows XP emulator that can fool the Zune software into working because i really don't want to swap my beloved Zune for something else.

anyone got any ideas about how to do this or better yet, how to run the Zune software on Linux?

I have Linux 12.04 by the way.

---

### Post by Habitual on 2012-10-28
Virtualbox+Windows XP installed.

---

### Post by c911darkwolf on 2012-10-30
+1 to Habitual

Goto your Software Manager and search for virtualbox and install it.

Then run it and click *new* and follow the steps.

It will ask you things like the following:

**Which Operating System?** Just pick from the drop down box Windows & Windows XP

**How much RAM?** I suggest 512 to 1024.  Remember this takes away from your normal RAM so don't over due it or it might bog your system down.  I mostly use mine for running netflix, but have 4 gigs and dedicate a full 1024mb to my VM.

**Create Virtual Disk**Here you can accept the default type and then you get to pick Dynamic or Fixed.  Dynamic means it only takes up as much space as  it has to have and you set a Maximum of how large the virtual disk can get (again this is taking space form your normal harddrive and DYNAMIC is great for smaller hard drives)  Or you can pick Fixed and make a set size of the harddrive (this is slightly faster and better if you have plenty of space to spare.)

**Additiona options**  Once your done before you start your machine i suggest you right click your virtual machine and goto settings.  Here you can goto DISPLAY and turn on 2d & 3d accleration and increase the virtual video card memory up to 128mb.  Now this is virtual not REAL graphics card memory, this is just to fool applications to let you install and run applications with a video requirement. so if you start installing games you won't get too far.

**Processor**You can also designate how many of your processors are allowed to power the PC.  i have a 3.01ghz quad core and only use 1 and it runs great.  Now close out

**Last Step**Now start your machine, it will prompt you to pick either the drive your install cd is in or to navigate to the location of your ISO to install windows xp or what ever OS your wanting.

**Guest Addons** to get some better support and allow better mouse intergration once you finishing installing with the VM open and running, click settings on the VM window and click "install guest addons".  

Now once you boot up you have windows.  You can right click the virtual machine on the manager and make a shortcut to your desktop if you want.  

**Now the issue here is WINXP is a licensed software**.  So your options are reinstall it every 30 days and keep using the trial, or have a License key.   There may be other options, but they won't be discussed on this forum.


Good Luck

I run Netflix on mine mostly and it has the follow specs and runs really fast.

os: Windows XP Home
Processor: 1 cpu 3.01 ghz
Ram: 1024
Virtual Harddisk: Dynamic 50gig

---

### Post by majorburt on 2012-10-30
> **c911darkwolf said:**
> +1 to Habitual

Goto your Software Manager and search for virtualbox and install it.

Then run it and click *new* and follow the steps.

It will ask you things like the following:

**Which Operating System?** Just pick from the drop down box Windows & Windows XP

**How much RAM?** I suggest 512 to 1024.  Remember this takes away from your normal RAM so don't over due it or it might bog your system down.  I mostly use mine for running netflix, but have 4 gigs and dedicate a full 1024mb to my VM.

**Create Virtual Disk**Here you can accept the default type and then you get to pick Dynamic or Fixed.  Dynamic means it only takes up as much space as  it has to have and you set a Maximum of how large the virtual disk can get (again this is taking space form your normal harddrive and DYNAMIC is great for smaller hard drives)  Or you can pick Fixed and make a set size of the harddrive (this is slightly faster and better if you have plenty of space to spare.)

**Additiona options**  Once your done before you start your machine i suggest you right click your virtual machine and goto settings.  Here you can goto DISPLAY and turn on 2d & 3d accleration and increase the virtual video card memory up to 128mb.  Now this is virtual not REAL graphics card memory, this is just to fool applications to let you install and run applications with a video requirement. so if you start installing games you won't get too far.

**Processor**You can also designate how many of your processors are allowed to power the PC.  i have a 3.01ghz quad core and only use 1 and it runs great.  Now close out

**Last Step**Now start your machine, it will prompt you to pick either the drive your install cd is in or to navigate to the location of your ISO to install windows xp or what ever OS your wanting.

**Guest Addons** to get some better support and allow better mouse intergration once you finishing installing with the VM open and running, click settings on the VM window and click "install guest addons".  

Now once you boot up you have windows.  You can right click the virtual machine on the manager and make a shortcut to your desktop if you want.  

**Now the issue here is WINXP is a licensed software**.  So your options are reinstall it every 30 days and keep using the trial, or have a License key.   There may be other options, but they won't be discussed on this forum.


Good Luck

I run Netflix on mine mostly and it has the follow specs and runs really fast.

os: Windows XP Home
Processor: 1 cpu 3.01 ghz
Ram: 1024
Virtual Harddisk: Dynamic 50gig

that sounds alot like dual booting with Windows XP. 
what is the difference other than the fact that you are running it on top of Linux instead of being able to choose between Windows and Ubuntu?

---

### Post by c911darkwolf on 2012-10-30
It is very similar:

The only CON to using a VM is the video card issue.  You can't do anything that requires a gaming card like Deadspace 2/stracraft 2/ Intensive Video editing/ ect..

You can play movies/netflix/flash games/ect..  

The reason i use a VM instead of dual booting is that fact that i can alt tab between my VM WinXP & my Linux OS easily.

Also if i'm running something very large (compiling, major install, ect..) that is gonna take a while i can leave my linux working and alt tab over to my VM machine which works like normal because the resources it's using are dedicated to it.


So basically when i'm programming i can compile a large file and alt tab over and watch Fullmetal Alchemist without my computer freezing/locking up.


Think if your in Zune and you want to do something that is only WinXP... would you rather reboot your pc, do this one thing and then reboot again to reload Zune? 

Or would you prefer to click a link and a windows box pop up and you can do your thing while zune hums away in the background.



Virtual Machines also allow you to test run some of the many MANY flavors of linux without commiting to one.

---

### Post by c911darkwolf on 2012-10-30
Another interesting feature.


You can share your virtual machine on your local network...


I.e....  My wife & I both use linux Distro's and I have a dedicated PC that runs Virtual Machines.  My wife can connect over and pick/drop files off the virtual machine and so Can I.


I did find this link to run Zune on Ubuntu using WINE program.

[http://www.ehow.com/how_7317935_use-zune-ubuntu.html](http://www.ehow.com/how_7317935_use-zune-ubuntu.html)


PLEASE BACKUP your data before you test something...   You never know how it will work

---

### Post by majorburt on 2012-11-05
thanks for all the info on this!!

i got it all set up except for one thing. where would i get a .iso of Windows xp? 
i really don't want to torrent(ie: [www.thepriatebay.se](www.thepriatebay.se)) a copy simply because i don't know if its been changed or altered to "nuke" the network its connected to or something like that.

---

### Post by Cheesemill on 2012-11-06
You have to purchase a physical CD (if you can still find one for sale anywhere).

---

### Post by CaptainLinux on 2012-11-06
If you have a valid license key for Windows XP but no disc, you should be able to find a reputable source for the MD5/SHA1 hash of the ISO. You could then have some confidence in verifying the authenticity of any XP ISO you download off of the internet.

---

### Post by majorburt on 2012-11-08
> **CaptainLinux said:**
> If you have a valid license key for Windows XP but no disc, you should be able to find a reputable source for the MD5/SHA1 hash of the ISO. You could then have some confidence in verifying the authenticity of any XP ISO you download off of the internet.

gonna work on getting a copy of xp (hoping for a licence key) and try it out as soon as i can.

wish me luck!!!

---

### Post by Habitual on 2012-11-09
> **majorburt said:**
> ...i really don't want to torrent(ie: [www.thepriatebay.se]("http://www.thepriatebay.se")) a copy....

Wisdom doesn't come with age ;)

---

### Post by slickymaster on 2012-11-09
Wine will run most windows utilities and some games well.

You can get it [here]("www.winehq.org/").

---

### Post by wiebeest on 2012-11-09
Wine offers the best performance. 

But if you want to go the path of virtualisation, then **VMWare player** (*which is also free*) offers much superior performance compared to VirtualBox. 

Check the comparison on Phoronix: "VMware Virtualization With OpenGL Still Smacks Oracle VirtualBox":

[http://www.phoronix.com/scan.php?page=article&item=vmware_virtualbox_osx&num=1]("http://www.phoronix.com/scan.php?page=article&item=vmware_virtualbox_osx&num=1")

---

### Post by CharlesA on 2012-11-09
> **Habitual said:**
> Wisdom doesn't come with age ;)
What he said. Does wisdom come with warnings? :p

---

### Post by markbl on 2012-11-09
> **wiebeest said:**
> 
Check the comparison on Phoronix: "VMware Virtualization With OpenGL Still Smacks Oracle VirtualBox":

Those benchmarks are on a Mac OSX host though.

---

### Post by wiebeest on 2012-11-15
> **markbl said:**
> Those benchmarks are on a Mac OSX host though.

Hmm, yes, now that you mention it. My bad. 

But could the mentioned performance benefit through vmware over virtualbox also count for Ubuntu as a host? 

Googling for "ubuntu host vmware player versus virtualbox" seems to provide the same outcome over- and over again. 
Vmware wins performance-wise. Not so many results though with an Ubuntu/Linux host. 

From my own experience. A few months ago I had problems with running an older Windows XP game properly through Wine (The Godfather 1 the game). 
Since it's actually quite an older directx9 game, I figured it could possibly run through a virtual windows xp setup.  
And indeed, it certainly did run better in virtualbox than native under wine, but it ran even more better (read: faster fps-wise) through vmware.


So it's definitely something for **majorburt** to have a look at in comparison.

---

### Post by majorburt on 2012-12-07
> **wiebeest said:**
> Hmm, yes, now that you mention it. My bad. 

But could the mentioned performance benefit through vmware over virtualbox also count for Ubuntu as a host? 

Googling for "ubuntu host vmware player versus virtualbox" seems to provide the same outcome over- and over again. 
Vmware wins performance-wise. Not so many results though with an Ubuntu/Linux host. 

From my own experience. A few months ago I had problems with running an older Windows XP game properly through Wine (The Godfather 1 the game). 
Since it's actually quite an older directx9 game, I figured it could possibly run through a virtual windows xp setup.  
And indeed, it certainly did run better in virtualbox than native under wine, but it ran even more better (read: faster fps-wise) through vmware.


So it's definitely something for **majorburt** to have a look at in comparison.

totally forgot about this thread! 

does vmware require a disk of the OS like with VirtualBox?


ps: I might end up marking this thread as solved depending on if i want to peruse this further. i cant seem to find the Zune software that supports the ZuneHD anymore. :(

---

### Post by CharlesA on 2012-12-07
Yes. Both use a virtual disk and need to be loaded via CD.

---

### Post by majorburt on 2012-12-21
> **CharlesA said:**
> Yes. Both use a virtual disk and need to be loaded via CD.

do you know of any trustworthy sites where i can get an image of one of the OSes (either full or trial)?

---

### Post by deadflowr on 2012-12-21
Here's an interesting thread I remember reading a few weeks ago about Ubuntu and Zune:

[http://ubuntuforums.org/showthread.php?t=2079916]("http://ubuntuforums.org/showthread.php?t=2079916")

---

### Post by CharlesA on 2012-12-21
> **majorburt said:**
> do you know of any trustworthy sites where i can get an image of one of the OSes (either full or trial)?
I don't know of anywhere you could download a copy of XP, but it's still up for sale on some sites like Amazon, but most of them do not sell XP any more.

---

### Post by majorburt on 2013-02-16
> **CharlesA said:**
> I don't know of anywhere you could download a copy of XP, but it's still up for sale on some sites like Amazon, but most of them do not sell XP any more.

decided to install windows 7 instead. if i get my hands on a copy of xp, might use virtualbox if i NEED xp.

thanks for all the help!!!

---

