---
title: "What are the first things that you do after having Ubuntu installed?"
date: 2007-04-06
forum: The Cafe
---

### Post by wersdaluv on 2007-04-06
I just installed Ubuntu.

I want to know the first things that you do after having a fresh new install of Ubuntu.
[B]
Edit:[/B]
Other than tweaking look and feel, what else do you tweak to make Ubuntu more personalized?

---

### Post by Somenoob on 2007-04-06
I Installed the official video driver(Fgrlx in my case) and multimedia codecs .

---

### Post by FuturePilot on 2007-04-06
I first install all of the updates. Then I install the Nvidia driver and Beryl. Then I install all the the extra codecs and stuff. Then all of the programs that I want.

---

### Post by futz on 2007-04-06
Set up Nautilus properly (stock config is totally useless - what are they thinking?).

Install NVidia drivers.

Edit xorg.conf to get proper screen resolution and make MX Revolution mouse work proper. Also edit so Wacom pad works right.

Set up desktop theme/wallpaper/etc. (hate the stock config). 

Set up keyboard shortcuts to suit. 

Set up autologon. No need for tight security - there's only me here. I like to punch the power button and go get a coffee. When I come back it's ready, not waiting for me to type in my logon so I can wait some more.

Install Automatix2 and add various software, fonts, codecs, change to totem-xine. Install Wine.

SSH to another of my computers on the network and drag over my browser shortcuts, wallpapers, icons & scripts for various programs (Foxit Reader, QuickPar, etc) and whatever else I need from there. 

Set up Firefox properly with stuff like 'browser.urlbar.autoFill = True' and shuffle the toobar to suit me (kill the Navigation Toolbar - it's for idiots).

Add all the software I can't live without.

Set up Tomboy and Weather Report on top panel.

Adjust panel colors and make bottom one autohide. Adjust bottom panel hide size to 1 px and delays to 0.

Set up Beryl.

That's probably pretty close to everything.

---

### Post by finer recliner on 2007-04-06
video codecs.
update to firefox 2.0 (dapper drake comes with 1.5)
update flash player
apply internet fix (i had problems with my university's on-campus firewall)
install thunderbird and setup email account.
install ntfs-3g and add my windows partitions to fstab file so i can access it's files.
ati drivers

...stuff like that. small tweaks to make sure everything works how i like it

---

### Post by Mateo on 2007-04-06
update, then get the MP3 codecs, then get the DVD thingy, then you got to make you some scripts to do routine tasks, then make some aliases so you don't have to type stuff like "sudo apt-get install" every time.

---

### Post by Sunflower1970 on 2007-04-06
I made myself a little Edgy cheatsheet of some of the things to do when doing a fresh install...numlockx gets set up, along with setting up my 5-button mouse. I set up my sources.list to add in other repos. Then, I update. After that, I get automatix to set up my nvidia drivers. Next is setting up everything in Firefox.
After that, it's time to play with the look of the desktop. Different wallpapers, themes, fonts, etc etc etc.

---

### Post by Mateo on 2007-04-06
yeah, numlockx is a must.

---

### Post by daynah on 2007-04-06
Everything they just said is covered in what I do.

I go to the Ubuntu Guide ( can't remember url, com org whatever it is, just google "ubuntu guide") and I literally... go down the list.

Obviously, don't do everything. But go down the list and think if you want each item or not. Remember when copying and pasting, middle click is also paste! Yay!

The only thing that may not be in Ubuntu Guide is to mount your Windows drives with readwrite (NTFS-3G). Or if it is, I don't like Ubuntu Guide's guide for it. I use this one: [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585). Rockin'.

I don't recommend Automatix, it's messed up every time I've used it or I've watched someone else used it (Usually with a "I wouldn't do that" and a "I told you so" bracketing the action). I would put Automatix in the same pile as Beryl. If you REALLY are THAT lazy, do it. But jeeze, how lazy are you, it's all in the Ubuntu guide.

Also, use aptitude!

Yeah, I'm not smart enough to know why we're supposed to use aptitude. I think I remember someone saying that it didn't matter anymore, but I think the cool thing to do lately is to be really passionate about aptitude being better than apt-get.

So... MAN! Aptitude is TOTALLY better than apt-get!!11! Don't you know ANYTHING! JEEZE!

:)  Have fun!

---

### Post by EdThaSlayer on 2007-04-06
The first things I do are:

1.Get all my data back(all the things I had on my previous Ubuntu, I always like fresh-installs)
2.Get all the necessary codecs to play everything
3.Install some necessary applications(firewall, Amsn, Deluge, etc...) 
4.Get flash and java for my web browser

---

### Post by AndyCooll on 2007-04-06
Essentially similar to everyone else:

1. Install updates.
2. Add additional users (the wife!) 
3. Install nfs and ssh and then edit my fstab so I can get access to my fileserver.
4. Install other software I use.
5. Edit a few settings.

Done!

:cool:

---

### Post by picpak on 2007-04-06
Setup panels
Install updates
Enable extra repos
Install codecs
Install all of the programs I use (I usually just go through Add/Remove and choose what I want)
Get Frostwire, Audacity 1.3 (basically programs not in the repos)
Setup the programs to my liking

This list will be even more shortened when Feisty comes out.

---

### Post by teet on 2007-04-06
> Set up Nautilus properly (stock config is totally useless - what are they thinking?).

I agree.  The first thing I do is turn the "location bar" on in nautilus by using gconf-editor.  I can't believe this still isn't turned on by default...

-teet

---

### Post by UltraMathMan on 2007-04-06
> **daynah said:**
> Everything they just said is covered in what I do.

I go to the Ubuntu Guide ( can't remember url, com org whatever it is, just google "ubuntu guide") and I literally... go down the list.

Obviously, don't do everything. But go down the list and think if you want each item or not. Remember when copying and pasting, middle click is also paste! Yay!

The only thing that may not be in Ubuntu Guide is to mount your Windows drives with readwrite (NTFS-3G). Or if it is, I don't like Ubuntu Guide's guide for it. I use this one: [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585). Rockin'.

I don't recommend Automatix, it's messed up every time I've used it or I've watched someone else used it (Usually with a "I wouldn't do that" and a "I told you so" bracketing the action). I would put Automatix in the same pile as Beryl. If you REALLY are THAT lazy, do it. But jeeze, how lazy are you, it's all in the Ubuntu guide.

Also, use aptitude!

Yeah, I'm not smart enough to know why we're supposed to use aptitude. I think I remember someone saying that it didn't matter anymore, but I think the cool thing to do lately is to be really passionate about aptitude being better than apt-get.

So... MAN! Aptitude is TOTALLY better than apt-get!!11! Don't you know ANYTHING! JEEZE!

:)  Have fun!

Iirc aptitude manages dependencies better than apt-get, namely if you install program X with apt-get or aptitude either will install program X and dependencies Y and Z. However when uninstalling program X apt-get will only remove program X (it will leave Y and Z installed). Aptitude will remove program X and dependencies Y and Z (assuming some other program doesn't need them of course).

In addition to what was already mentioned I have to do a ```
 sudo aptitude install htop build-essential openssh-server tilda
``` (what I can remember at the moment) and then head over to [http://interfacelift.com/wallpaper/]("http://interfacelift.com/wallpaper/") to pick up some awesome wallpapers, and of course [http://www.gnome-look.org]("http://www.gnome-look.org"). :)

---

### Post by karellen on 2007-04-06
set up my network connection
update all the system
install multimedia codecs
install favourite applications
modify the default look

---

### Post by daynah on 2007-04-06
UltraMathMan, if you install something with apt-get, will removing it with aptitute still get those dependencies or do you need to use aptitude through the whole process?

---

### Post by beercz on 2007-04-06
log in

---

### Post by ComplexNumber on 2007-04-06
the first thing i do is either:
a) install various packages such as nautilus-open-terminal, leafpad, etc.
or
b) install all the updates first just in case something gets broken
. then at least if something gets horribly broken, i haven't wasted any time setting anything up.

---

### Post by Happy_Man on 2007-04-06
Hmmm...let's see....

1. Update (they should do this when the system installs, it wastes time)
2. Drag all my files back over from my Windows partition (I don't have the ability to stick in a fifth partition, I have no idea how to set up extended partitions, and I usually don't touch my Windows install, so it works out. :))
3. Automatix2 and Envy to install Opera, codecs, drivers, etc. Then uninstall both.
4. Spend some good quality time wrestling to get Beryl installed 
5. Play with everything until I'm satisfied

Total time required: four hours (three on a good day), but it's so worth it.

---

### Post by picpak on 2007-04-06
> **Happy_Man said:**
> 1. Update (they should do this when the system installs, it wastes time)

I know...if the installer detects an internet connection, why not download the latest updates from the internet? Has this been brought up before?

---

### Post by UltraMathMan on 2007-04-06
> **daynah said:**
> UltraMathMan, if you install something with apt-get, will removing it with aptitute still get those dependencies or do you need to use aptitude through the whole process?

I believe you need to have installed it with aptitude to begin with - you could check the dependencies of a program originally installed with apt-get with ```
 aptitude show *program*
``` and then see if they are listed as being removed when you do ```
sudo aptitude remove *program*
``` however I'm fairly certain the program has to be installed with aptitude to begin with for the dependencies to be removed along with it.

---

### Post by Punker on 2007-04-06
1) Update/Update Manager 
2) Sound Card
3) Study/Other

---

### Post by Compucore on 2007-04-06
Configure it with the appropriate software on the system that way I like it. Install any and all updates ifneeded once its running. Add in Automatix2 a must for a canuck.  

Compucore

---

### Post by TravisNewman on 2007-04-06
> **futz said:**
> Set up Nautilus properly (stock config is totally useless - what are they thinking?).
...
Set up Firefox properly with stuff like 'browser.urlbar.autoFill = True' and shuffle the toobar to suit me (kill the Navigation Toolbar - it's for idiots).


I'm just curious as to what you think is setting up Nautilus properly... I'm always looking for ways to tweak it.

Also, what do you use in place of the nav bar, just keyboard shortcuts?

---

### Post by Cloudy on 2007-04-06
Get all the necessary codecs as well as flash and java for Firefox, download the Gmail Manager addon and a few other addons for Firefox, change the desktop background.

---

### Post by futz on 2007-04-06
> **panickedthumb said:**
> I'm just curious as to what you think is setting up Nautilus properly... I'm always looking for ways to tweak it.
1. Turn on Status Bar
2. Change view to View as List (icons are for (windoze) morons)
3. Change the left pane to Tree (if your Nautilus is not using Browser Windows, then turn them on)
4. Enable Location Entry (permanently, with gconf-editor)
5. Make a 'download' directory - everything that comes in gets dumped here and sorted from here to other directories (don't download to desktop like an idiot noob)
6. Make Bookmarks for download and other often-used dirs.
7. Setup Connect To Server's for any often-used network computers


> Also, what do you use in place of the nav bar, just keyboard shortcuts?
Ya. The nav bar is for people who can't remember a very few simple keyboard shortcuts. My mouse does back/forward, or back is ALT-LeftArrow and forward is ALT-RightArrow (most keyboards these days have back/forward keys too). Reload is F5 on all browsers (all properly written software should use F5 as Refresh). Stop is ESC. Home page is ALT-HOME.

Why lose a half inch of screen just so you don't have to memorize five easy shortcuts? And really all you need to remember is back/forward/reload. The other two aren't used very often. Screen real estate is precious. Use it for something useful, instead of using it to replace your memory.

---

### Post by TravisNewman on 2007-04-06
I disagree that it's all "noobish" but I see your point that it's more efficient.

So in FF do you put the address bar in the menu bar or use ctrl+L?

---

### Post by simorigin on 2007-04-06
edit xorg to use 1440x900 properly

install nvidia drivers

and install blender


after that pretty much change anything that I feel like no real prefernce

---

### Post by futz on 2007-04-06
> **panickedthumb said:**
> So in FF do you put the address bar in the menu bar or use ctrl+L?
Menu bar. Google bar goes into the shortcut pane.

Two more great keyboard shortcuts to make your browser easier to use: ALT-D puts you in the address bar, ready to type. CTRL-K puts you in the search bar, ready to type. You're going to type anyway - why reach for the stupid mouse?

---

### Post by TravisNewman on 2007-04-06
I hate using the mouse when I don't have to, and my wife is more adamant about it than I am. I never thought about totally disabling the nav bar though... I'm liking it so far!

---

### Post by futz on 2007-04-06
> **panickedthumb said:**
> I hate using the mouse when I don't have to, and my wife is more adamant about it than I am. I never thought about totally disabling the nav bar though... I'm liking it so far!
Ha! Another convert!

I switched to using every keyboard shortcut I could find years ago. Got bad carpal tunnel pain. Couldn't game anymore. Caused by the evil mouse. The RSI is mostly gone away now, but whenever I get a new game it comes back and I have to lay off the mouse for a while. 

Shortcuts are just faster and easier anyway.

---

### Post by Kedma on 2007-04-06
so how do you change the nv driver if you cant get to the desktop..??   system locks after login screen...  my second moniter goes into standby with an out of range error..  190mhzx147hz..  seems a little high.. its a pos I use for second display to keep and eye on my chat programs, and IM's while playing games, and doing other tasks...

my main screen is a Viewsonic G790 with a Geforce 7800GT behind it..

---

### Post by richbarna on 2007-04-06
Update, E17, Amarok, k3b, nVidia driver, Drag over the IceWeasel addons and Email settings (always backedup). Mount Gmail ftp drives,  add repos to  sources.list  +  gpg keys.
Go for the other software and codecs etc. Leave the desktop as standard, so many distros and so many programs, can't be bothered with wallpaper and transparent toolbars.
Editing and config all via the terminal (Yakuake).

---

### Post by futz on 2007-04-06
> **Kedma said:**
> so how do you change the nv driver if you cant get to the desktop..??   system locks after login screen...  my second moniter goes into standby with an out of range error..  190mhzx147hz..  seems a little high.. its a pos I use for second display to keep and eye on my chat programs, and IM's while playing games, and doing other tasks...

my main screen is a Viewsonic G790 with a Geforce 7800GT behind it..
Hit CTRL-ALT-F1 and login to a console. Then
```
sudo nano /etc/X11/xorg.conf
```
Scroll down to a section like this
```
Section "Device"
    Identifier     "NVIDIA 7950 GT KO"
    Driver         "nvidia"
EndSection
```
Yours will have a different video card and the Driver line will likely be "nv". Change that 'nv' to 'vesa' and try that.

To save your file, hit CTRL-X and then Y and then ENTER.

Then type in 'startx' (without the apostrophes) and ENTER.

If that doesn't get it at least displaying something, there are other tricks.

---

### Post by TravisNewman on 2007-04-07
My answer to this one:
* move everything to one panel
* turn off system sounds and ESD (using alsa directly)
* Copy over backed up xorg.conf (yes, it's easy to set up, except for the back button on my mouse, I always have to look that one up) and sources.list
* thanks to futz, I'll now be moving my address bar in firefox to the menu bar and removing the nav bar
* customizing Nautilus (I basically already did what futz said, plus enabling hidden files to be shown, and minus the location entry... I find the breadcrumb navigation pretty nice, and if I need it I can always click the button for it)
* remove help from the panel and add the terminal and a few other handy things
* go through synaptic and install everything that I need/want
* install a few debs that I have saved that I haven't found a repo for
* Customize the theme/wallpaper (currently using Murrina Fancy Candy, Tango icons, and "Innocent" wallpaper)
* Boot into KDE to check its progress. Promptly boot back into Gnome.
* Start up a terminal in one desktop, firefox in another, and save the session
* Get fstab configured properly
* reboot to make sure I didn't screw anything up
* bask in the glory that is my installation

---

### Post by futz on 2007-04-07
> **panickedthumb said:**
> * customizing Nautilus (I basically already did what futz said, plus enabling hidden files to be shown, and minus the location entry... I find the breadcrumb navigation pretty nice, and if I need it I can always click the button for it)
Or hit CTRL-L

---

### Post by TravisNewman on 2007-04-07
you're just full of time-savers :)
You should start a thread just about all the shortcuts you know!

---

### Post by raja on 2007-04-07
1. Install Beryl and get it going. Then find some nice emerald themes.
2. Install other programs I need.
3. Configure my session (terminal, firefox)
4. Of course, enable universe

---

### Post by heimo on 2007-04-07
> **panickedthumb said:**
> you're just full of time-savers :)
You should start a thread just about all the shortcuts you know!
ctrl+L to location bar works also in browsers, and it's _really_ useful. :)

EDIT: Oh, and to stay on topic. First I check updates and install some software - probably at least vlc and what ever I find missing (sometimes abiword). I usually change workspace switcher to show 5-6 desktops, change clock to 24h and to not show date... Hmm... Tweak couple settings in Firefox (smooth scrolling, disable ipv6), and in about 5 minutes I'll be doing some productive... well, some semi-productive work. Ubuntu out of the box is very close to what I want, most software is already there, defaults are quite good.

---

### Post by futz on 2007-04-07
> **heimo said:**
> ctrl+L to location bar works also in browsers, and it's _really_ useful. :)
Oh! So it does! Thank you!

---

### Post by stchman on 2007-04-20
After install.

- Fix hosts and hostname files
- Do the automatic update
- Install video drivers using Envy
- Select resolution
- Install wireless if on laptop
- Setup Nautilus with open terminal
- Do the one stop shopping with Add/Remove
      Nvu, K3B + MP3 plugin, Java 1.5 + Browser plugin, VLC, Ktorrent, Acrobat
- Update Openoffice.org to 2.2
- Install multimedia codecs
- Install build-essential
- Setup fstab for other possible partitions
- Setup printers
- Install M$ fonts

Ubuntu comes with so much there is not a terrible amount of setup needed.

---

### Post by Dyegov on 2007-04-20
I used to have to do a lot of very difficult things that involed the command line. Today with Feisty I just had to do some clicks and everything was done :)

From Add/Remove... I installed the programs I needed, and also all the codecs for mp3, dvd, java, flash, etc, letting my pc completely ready to be used with just some clicks :) I am so happy about it. Now I can finally do the big change, and don't look back to Windows ever again ;)

---

