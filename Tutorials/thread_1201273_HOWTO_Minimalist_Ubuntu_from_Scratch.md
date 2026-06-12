---
title: "HOWTO: Minimalist Ubuntu from Scratch"
date: 2009-06-30
forum: Tutorials
---

### Post by fatalGlory on 2009-06-30
I have recently inherited an old laptop with only 512mb of ram (shared with video).  I noticed that my media editing desktop monster with all the compiz eye candy etc. uses 300mb of ram just to sit idly on the desktop and I thought "that kind of install will not cut it on the lappy".

So I decided to have a go at installing a minimalistic ubuntu, installing only the components I definitely needed, from the ground up (I call it "ground up ubuntu" - yay coffee metaphor!).  Some of the steps involved were less than obvious (hence writing a tutorial for it), but the result was a fully functional desktop with a 40mb memory footprint.  **Not at all bad.**  This process is still fairly easy with Ubuntu, but I did learn a lot about how the components of a linux desktop fit together in the process.

This is my first time writing a tutorial like this, so go easy, I'm happy to make corrections.

**Step 1:** Install base system from Alternate CD
You'll have to grab the Alternate CD (latest at time of writing is 9.04 Jaunty) to install the base system (no desktop, no lamp stack, pretty much just enough to use apt-get).

**1.1 - Preamble**
After booting the Alternate CD, select your language then choose **Rescue a Broken System** from the menu.  You'll have to tell it your country and your keyboard layout, then it will configure a bunch of stuff including DHCP, so you have network access.  Next you'll have to choose a hostname and set up your time zone info.  Finally a bunch of hardware detection occurs.

**1.2 - Partitioning and Installation**
At this point, you'll be shown some info about the partitions detected (or not detected) on the system.  Whichever it is, choose **Go Back** to be taken to a list of system rescue tasks.  Choose [b]Install Base System[b] from the list.  From here the steps are very similar to the standard ubuntu desktop install, just follow the instructions to set up partitions and install the base system.

**Step 2: Adding a Desktop Environment**
After you finish installing the base system and reboot, you're left with a login prompt.  Enter your username and password and you get given a command line.  This is technically a complete linux system, but doesn't let us do much.  We need to add a few things in order to make our computer feel like it belongs in the post 1970s.

**2.1 - X Server**
An X server is the program that actually displays a graphical desktop on your linux machine, to install one, run the following command:
```
sudo apt-get install xserver-xorg xinit
```
*xinit* is primarily useful for giving us the *startx* command which actually starts up the X server.  However, if we run *startx* now, X will terminate and drop us back to the command line.  Why?  Because we have no window manager to take over control once X starts.

**2.2 - Window Manager (fluxbox)**
Since we're going for a lean and mean install, I chose to use [fluxbox](http://www.fluxbox.org/screenshots/) for the window manager.  It's very lightweight and makes me feel hardcore (since it is much more expert friendly than joe average friendly).  If you don't like fluxbox, feel free to modify this step to your tastes (maybe try xfce).

As well as fluxbox, we're going to need to install a terminal emulator so that we can use the command line to do other tasks once fluxbox has taken over and we lose our current command-line.  To install fluxbox with a terminal emulator, use these commands:
```
sudo apt-get install fluxbox xterm
```
With that done, we can load our shiny new desktop by running:
```
startx
```
Once you're in the fluxbox desktop environment, you can run programs by right-clicking the desktop and finding them in the menu, or the faster way, but pressing **Alt-F2** to get the run dialog and just typing the name of the program you want to run.  To get the terminal emulator up so we can install more stuff, press alt-F2 and enter *xterm*

**Step 3: Adding a file manager**
There are lighter weight file managers out there, but they hurt my eyes, so I chose to install **thunar.**  Be aware that it does drag in some xfce dependencies and if you *really* need to keep things super-light, there are some other options like [xfe.](http://roland65.free.fr/xfe/)

**3.1 - Installing thunar**
Install thunar with the simple command:
```
sudo apt-get install thunar
```

**3.2 - Making it not ugly**
If you run thunar, you may notice that all the icons are the same dinky piece-of-paper thing.  This is annoying.  If i wanted no graphical description of my files, I'd have stuck with the command line, so we're going to fix it.  We're going to install an icon theme called tango and a theme chooser app for gtk programs (like thunar).  Enter these commands:
```
sudo apt-get install tango-icon-theme lxappearance
```
After these have been installed run lxappearance by just typing its name at an Alt-F2 prompt, then you can select you're preferred gtk theme, icons, etc.

**Step 4: Adding Sound Capabilities**
This one caused me some headaches.  After reading a *lot* of hype lately about the new and improved Open Sound System version 4 (OSSv4), I decided that it must be my new lightweight sound solution.  I installed it, and it seemed to work fine, but the promised benefits were not there.

If I turned on virtual mixing, I got bad crackly sound with low volume, if I turned it off, I could only get one application to play sound at once.  So I decided to revert back to ALSA (which as it turns out, was easy and not so bad at all).

**4.1 - Installing ALSA**
To install ALSA and enable sound, install these packages:
```
sudo apt-get install alsa-base alsa-utils
```

**4.2 - Adding ourselves to the audio group**
Next we need to add our user to the *audio* group so that our apps can access the sound card:
```
sudo usermod -a -G audio *your_username*
```

To get these permissions to apply, we need to log out and log back in.  Right-click the fluxbox desktop and select **Exit** in the menu.  This will end the X session and drop you back to your original command line.  From here, use the command:
```
exit
```
to log out and then log in again as normal.  Use the command:
```
startx
```
again to get back into fluxbox.

**Step 5: Adding some basic applications**
I installed some basic applications to enable me to actually get stuff done with this machine:
```
sudo apt-get install firefox mplayer audacious abiword gnumeric evince eog geany xarchiver
```

Firefox: web browser
Mplayer: media player with heaps of options
Audacious: Winamp-like music player
Abiword: Word Processor
Gnumeric: Spreadsheet App
Evince: PDF viewer
Eye of Gnome: Image Viewer
Geany: Text Editor/Simple Programming IDE
Xarchiver: gui frontend for several archive file types

**Step 6: Tweaks**
This is just some stuff to make the computer a little more user friendly.

**6.1 - Being able to set wallpaper in fluxbox**
By default, there is no proper wallpaper setting application in fluxbox, to get one, run the command:
```
sudo apt-get install feh
```

To actually set the wallpaper, run a command that looks like this:
```
fbsetbg -f /path/to/image.jpg
```

It is also a good idea to edit your fluxbox init file so that the previously set wallpaper is loaded again each time you start fluxbox.  Open the file with:
```
geany ~/.fluxbox/init
```
add the line:
```
fbsetbg -l
```
to the end, save and close.

**6.2 - Current Battery Level**
If you're installing on a laptop like me, you'll want a way to see the current battery level, time left to recharge, etc.  Install the acpi tool with:
```
sudo apt-get install acpi
```
To run the tool and see the current batter stats, simply run:
```
acpi
```
at the command line.

**Step 7: Checking the Memory Footprint**
With all this stuff done, its time to see the fruits of our labour and see just how little memory our new lean-and-mean, ubuntu-from-the-ground-up system uses.

**7.1 - Install conky**
Conky is a nifty and lightweight little system monitor, install it with:
```
sudo apt-get install conky
```

**7.2 - Check your results**
Reboot so you get a picture of your system truly at idle, no extra apps running.  To do this, use the command:
```
sudo shutdown -r now
```
The *-r* means reboot, if you want to shut the system down, use *-P* instead (note uppercase P).
After the reboot, login, run startx, then run conky with Alt-F2, it will tell you your current memory usage, cpu usage, chunkiest apps, etc.  Come here and tell us all your results!

***I get 40.75Mb of memory in use after a clean boot.***

**Wrapping Up - Some Notable Exclusions**
Here's some of the stuff that I notably skipped installing.

**A Login Manager (gdm, kdm, etc.)**
who needs it?  I'm happy logging in from a command line and then running startx.  You might even fool some n00b into thinking that this is a text-only install.

**Pulseaudio**
When I go to do the ground-up install of my big, media editing, desktop machine, I'll no doubt need pulseaudio for some stuff, but for this little lappy, I don't see the point.  If for some reason I ever decide I need to be able to watch a movie and listen to music at the same time, I'll just live with them being at the same volume all the time ;)

---

### Post by jpeddicord on 2009-07-07
Very comprehensive. Approved, and thank you for your tutorial contribution!

---

### Post by RedSquirrel on 2009-07-07
Good job. :)

You can use the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") to install the base system.

For the X Window System, I prefer to install the **xorg** meta package.

In addition to being a good wallpaper setter, **feh** works well as an image viewer. ;)

Here is an article with more info about setting the background (wallpaper):

[http://fluxbox-wiki.org/index.php?title=Background](http://fluxbox-wiki.org/index.php?title=Background)

---

### Post by fillintheblanks on 2009-07-07
this is very much like archlinux install no ?

---

### Post by RedSquirrel on 2009-07-07
> **fillintheblanks said:**
> this is very much like archlinux install no ?

The general idea is similar (building up from the base system, adding only the packages you want).

However, with Ubuntu, most of the configuration is done automatically. With an Arch install, the procedure is more detailed and manual/hands-on.

---

### Post by nikhilbhardwaj on 2009-08-07
it's all perfect
but there should be a graphical login manager
not kdm,gdm etc
try SLIM
it reads your .xinitrc which is needed by startx too
and it has great themes
and it's very very light

---

### Post by BaroqueBloke on 2010-05-28
Thanks for the walkthrough!  I only have one problem:  the wireless and ethernet devices in my netbook are both atheros and are not detected by the rescue-system step.  I went and completed the installation anyways and now need to figure out how to get either or working to progress.  

Any thoughts?  

Thanks!

---

### Post by IngvardM on 2011-10-24
> **BaroqueBloke said:**
> Thanks for the walkthrough!  I only have one problem:  the wireless and ethernet devices in my netbook are both atheros and are not detected by the rescue-system step.  I went and completed the installation anyways and now need to figure out how to get either or working to progress.  

Any thoughts?  

Thanks!

Hey there!
Hope, my answer isn't too late for you, mate.
What you should do is - enter the BIOS setup (with the USB inserted, if you are installing it from a USB), go to a boot menu and set to boot from LAN first, then from USB.

If this doesn't help - feel free to email me.
Good luck and best regards.

---

### Post by yoreei on 2012-09-09
You can also make this system even lighter by:
1) Compiling the kernel
2) Using IceWM instead of Fluxbox (or even flwm for extreme simplicity)
3) No need to install Conky. The 'top' command does the job.
4) PCmanfm is a file manager that is way lighter than Thunar but kinda looks the same. I prefer it to Thunar because without losing functionality or eyecandy I gain lotsa free RAM and HDD space.
5) Dillo is also a very light browser (actually the lightest gui browser I've ever seen) but I do not recommend it for multimedia browsing (no java, javascript, flash, css isn't fully supported yet). I personally use it when I just want to check something quickly on Wikipedia and I don't want to wait for the other browsers to start.
6) Sticking to one graphics library (for example using only gtk, qt or fltk applications) help decrease memory usage (because then only one library needs to be loaded in memory). FLTK apps are faster and lighter (I really like it for this exact reason) and I always try to stick to FLTK apps. The problem is that few people develop on and use FLTK whcih results in less FLTK applications. 
7) Regularly cleaning you system with 'bleachbit', 'gconfcleaner' and 'localepurge'. The last actually does it's things automatically every time you install new software once it is configured on the first run.

The guide is nice. I am going to try the above methods on my old lappy too.

---

