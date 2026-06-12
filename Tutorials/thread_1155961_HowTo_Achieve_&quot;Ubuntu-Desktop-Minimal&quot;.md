---
title: "HowTo Achieve &quot;Ubuntu-Desktop-Minimal&quot;"
date: 2009-05-11
forum: Tutorials
---

### Post by TheShiv on 2009-05-11
I've noticed on brainstorm.ubuntu.com that there are a few people who would like to have an ubuntu-desktop-minimal edition instead of the default ubuntu-desktop which bundles software that not all of us use. 

I'm one of those users who likes to build his system from the ground up, so I wrote this simple post-install script which will give you a complete minimal desktop.

After running this script your system will look the same as a fresh install of ubuntu just without all the added software.

The first step to accomplish this is install a base system either using the Ubuntu Minimal CD (I use this along with my personal repository to create quick installs) or you can use the Ubuntu Server edition.

Once the base installation completes, login and run the following script, then reboot.

***Note: This script is for users who use the gnome environment.***

```

#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#			  essentials of an Ubuntu Desktop.
#######################################################################
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet \
human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk gnome-screensaver gnome-utils
echo "[*] Installing Application Essentials"
sudo apt-get install -y gcalctool tsclient

```

**The actual script I use also includes:**
epiphany-browser : Lighter equivalent to firefox.
vlc;vlc-plugin-* : For media etc.
openoffice.org-writer : Office Writer
openoffice.org-calc : Office Spreadsheet
openoffice.org-impress : Office Presentation

After using this script I've lowered the memory usage from around 250-350mb to about 80-90mb. All of the themes are there, the network-manager, gedit, restricted hardware tool, etc.

I use this setup for Old & New Desktops/Laptops. I purchased a Netbook recently (ASUS eeePC 1000HD) and found this script makes it run very well.

Of course this is just a starting template, you will want to modify it to add the packages you use.

-TheShiv

---

### Post by jpeddicord on 2009-05-12
Approved and thank you for your tutorials & tips contribution!

---

### Post by abhiroopb on 2009-05-13
No offence, but how is this useful at all? I mean all you are providing is a list of apps to install. Its an interesting concept, but perhaps it may be useful to come up with a list of programs that can be removed, startup applications that can be stopped, applications that load during boot that you don't need (e.g. bluetooth).

Something simple like:

sudo apt-get remove ekiga etc etc. Might be useful.

Again just trying to understand how this could be effectively used.

---

### Post by ericreboisson on 2009-05-13
> **abhiroopb said:**
> No offence, but how is this useful at all? I mean all you are providing is a list of apps to install. Its an interesting concept, but perhaps it may be useful to come up with a list of programs that can be removed, startup applications that can be stopped, applications that load during boot that you don't need (e.g. bluetooth).

Something simple like:

sudo apt-get remove ekiga etc etc. Might be useful.

Again just trying to understand how this could be effectively used.

I fully agree with abhiroopb

---

### Post by tomstrummer on 2009-05-13
> **abhiroopb said:**
> No offence, but how is this useful at all? I mean all you are providing is a list of apps to install. Its an interesting concept, but perhaps it may be useful to come up with a list of programs that can be removed, startup applications that can be stopped, applications that load during boot that you don't need (e.g. bluetooth).

Something simple like:

sudo apt-get remove ekiga etc etc. Might be useful.

Again just trying to understand how this could be effectively used.
Well, if you read his entire post, he said you should start with a "minimal" or "server" install, in which case there isn't anything to remove.  This is a lot more efficient than doing the default install and then removing a bunch of stuff, not to mention there are usually user conig files and other cruft left behind after you remove everything.

---

### Post by abhiroopb on 2009-05-13
> **tomstrummer said:**
> Well, if you read his entire post, he said you should start with a "minimal" or "server" install, in which case there isn't anything to remove.  This is a lot more efficient than doing the default install and then removing a bunch of stuff, not to mention there are usually user conig files and other cruft left behind after you remove everything.

That is true, but still this seems just like an install command that installs a few packages. Perhaps a more complete list with all possible packages which people can choose to install, etc.

---

### Post by mdmadph on 2009-05-13
> **abhiroopb said:**
> That is true, but still this seems just like an install command that installs a few packages. Perhaps a more complete list with all possible packages which people can choose to install, etc.

It's an install command that installs a few packages **from a minimal install.**  

If you're not interested in starting from a minimal install, this isn't for you.  Stop bashing it and go complain elsewhere.

---

### Post by abhiroopb on 2009-05-13
> **mdmadph said:**
> It's an install command that installs a few packages **from a minimal install.**  

If you're not interested in starting from a minimal install, this isn't for you.  Stop bashing it and go complain elsewhere.

This is why people get put of by linux threads. I phrased my comments quite clearly. I did not intend to bash the author or his howto. I merely wanted to comment on how this could be improved, and where exactly this would be useful.

Even starting from a minimal install, this is still a simple apt-get install nothing more. Perhaps it may be more useful (like I have already suggested) to include which startup applications and bootup applications can be stopped.

---

### Post by PandaPop on 2009-05-13
Now using this script, thank you very much! (would have to a agree a list of apps to remove would help alot of people)

---

### Post by MySchizoBuddy on 2009-05-13
What affect did this have on battery life?

---

### Post by bbourgoine on 2009-05-13
Seems to me the "post what to remove from a 'full install'" folks could be well-served by a simple listing of what packages are installed.  That could then be compared to a list of what's installed on their machines, and the difference would be the list of what packages to remove.

Maybe just the output of 'dpkg --get-selections' would be enough?

---

### Post by Rever75 on 2009-05-13
Good how to, I like this better then rummaging around looking for applications to purge or daemons to stop at such and such a run level. This gives me a very minimal install and I don't have to know what files to install to get a minimal gnome-desktop, since you just told me. Again thanks!

---

### Post by kiepmad on 2009-05-13
What this does it pretty easy to explain.

After installing a server or minimal installation, you're computer has basically only the things that it really needs to run.

When you install the packages included in the script, you get an useable computer system, you just need to add the different applications that you need. (eg office, browser, image processor, pdf reader, multimedia player, etc.)

This is a more actually a more logical way to install an Operating System, because there will be less clutter However, this method generally needs more computer knowledge, because in most cases you cannot simply do what you want, you need to install the packages first. (though I think the average Ubuntu user is able to make use of this)

This is in contrast to a base install, where packages that user might need are already installed to make the OS easier to use.


If you want to take this process to the next step, you might want to have a look at archlinux, though I reckon, that Arch is a lot more difficult too grasp, because you need to edit your config files to after installation.

Hope that clarifies the pourpose of this script.

---

### Post by abhiroopb on 2009-05-13
Thanks for the clarification.

I would like to try this out, but I'm a little worried there are applications that I am using right now that I am unaware off. Something like network manager or volume manager, etc. Which is very important but its not obvious that they are running.

In general I find that Ubuntu does not come with that many useless applications.

---

### Post by gastly on 2009-05-13
hmm...nice idea, I'd love to try it out!
Thanks :)

And, if you could include a list of apps for kde users as well, that would be great :)

---

### Post by govtrust on 2009-05-13
Thanks to the OP. I am much more comfortable with a GUI than the command line and would still like to get the benefits of a minimal install on older equipment.
For me it is much easier to add programs on top of a minimal install then to search for programs to remove. I find if I install packages myself I have some idea where the files are located and the dependencies they require.

---

### Post by fbnaia on 2009-05-13
I have used [**_Ubuntu Light script_**]("http://tomfichtner.de/linux/wiki/Installation") for some time now, it gives you a lot of options of what to install (window managers, file managers, browsers, panels, etc.) and also a little insight about what packages to choose. 

It's not maintained, i think it's at "Version 0.1" from 2008-05-13,
but it does work, i installed using this script since 8.04 Hardy as a base to setup a Pentest / Forensic setup, i even upgraded through 8.10 intrepid and 9.04 jaunty with no problems.

I haven't tried it recently, but if you are going to start from scratch its worth a try.

As for stuff to remove, there is a lot of information about that here at the forums.

---

### Post by sideshowmel on 2009-05-13
I think this is a great idea... far better, faster, more efficient to never install something in the first place than to go through removing unwanted packages IMHO.  Doing the full install then removal seems awfully wasteful in terms of time and bandwidth.

One more layer to add to this... USB install.  I run my server with no optical drive, so a USB install piece tacked onto this would really make this the true minimalist lover's guide! :)

---

### Post by pd0x on 2009-05-13
Thanks for the post.  My stepmom has an old desktop that I think this would work lovely on and I have been meaning to install ubuntu on it for some time.

I would also like to try the install on a laptop. You mentioned that you have used this minimalist install for laptops.  Have you had any trouble with ACPI with this install?  I am not aware if /usr/sbin/laptop_mode, powernowd, etc. comes with the core, though I expect it should. 

I also agree with sidewhowmel to install usb support from the beginning.

Overall great! Just wondering about your experience with ACPI?

---

### Post by basketcase on 2009-05-13
I want to try this out.  I've got a Via PicoITX board at the house that I chopped up Ubuntu to get it to a smaller foot print.  

I hated when I wanted gnome that I did gnome-desktop and I got games, and other apps packaged with gnome, when I really didn't want them.  Later to find out, that I couldn't remove certain things because gnome-desktop was a dependent.  

I'll give this a shot when I get a chance.

---

### Post by triplenine on 2009-05-13
How does the final footprint of this method compare to that of the Netbook Remix version of Ubuntu? I have UNR on my Mini 9 but feel that there is a bunch of bloat that I cannot excise thoroughly.
-999

---

### Post by lepa71 on 2009-05-13
So I followed your guide, but I can't start X. It gives me black screen.

Any help

---

### Post by upbeat.linux on 2009-05-13
I've included the link to the [**_Ubuntu minimal CD_**]("https://help.ubuntu.com/community/Installation/MinimalCD") to help users out:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

As a suggested improvement you could cut down on resources by installing [**_fluxbox_**]("https://help.ubuntu.com/community/Fluxbox"):

[https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by wickedbadawesome on 2009-05-13
first off, good idea with the minimal install. I have been doing something similar to this for some time now - I love the idea of picking and choosing what you want on there. In reply to those guys who's handles i don't even remember now, who were bashing it - If you dont know how to read through the repository list of ready to download and install or remove then maybe you should do that first, and do not rely upon people to give you EVERYTHING... figure it out man, and why not add it to the forum instead of complaining about it, most people who complain just want to cry a little and not offer any real solutions, if you don't have a solution then you cant justifiabley call it a promblem, as his is a solution better then yours

peace, Im mobile

---

### Post by joelbrock on 2009-05-13
i <3 this and will use this often!  I'm a little ashamed i didn't think of doing this myself.  I deploy ubuntu for my FOSS POS cash registers and lately i've been using debian because ubuntu has been bordering on bloatware.  Now i can stick with ubuntu AND cut the memory footprint.  Anything to improve performance.....

---

### Post by quixote on 2009-05-13
Very useful.  I've been looking for something like this for a low-memory netbook that's lying around, currently with a stripped down version of Debian on it.

Unlike abhiroopb, I don't really know what the absolute minimum essential packages are, so going the uninstall route, I don't know where to stop.  I found this out the hard way when I tried it and wound up having to reinstall my whole system because I dumped something critical!

And I didn't even know Minimal CD existed.

So thanks for the post!  I'll be using it.

---

### Post by ashmew2 on 2009-05-13
> **abhiroopb said:**
> No offence, but how is this useful at all? I mean all you are providing is a list of apps to install. Its an interesting concept, but perhaps it may be useful to come up with a list of programs that can be removed, startup applications that can be stopped, applications that load during boot that you don't need (e.g. bluetooth).

Something simple like:

sudo apt-get remove ekiga etc etc. Might be useful.

Again just trying to understand how this could be effectively used.

I've tried doing stuff like sudo apt-get remove ekiga..You can do it , but in the end you are just left with a bunch of *unfixable* broken dependencies..

Oh and i think the script's pretty neat...Ive been looking for something like this for quite some time now!!
Thanks TheShiv. :D

---

### Post by spambait9876 on 2009-05-13
Another case of: "I am looking for a hammer.  Therefore everything I see must be a hammer, or it's useless." ?

---

### Post by ashmew2 on 2009-05-13
> **kiepmad said:**
> What this does it pretty easy to explain.

After installing a server or minimal installation, you're computer has basically only the things that it really needs to run.

When you install the packages included in the script, you get an useable computer system, you just need to add the different applications that you need. (eg office, browser, image processor, pdf reader, multimedia player, etc.)

This is a more actually a more logical way to install an Operating System, because there will be less clutter However, this method generally needs more computer knowledge, because in most cases you cannot simply do what you want, you need to install the packages first. (though I think the average Ubuntu user is able to make use of this)

This is in contrast to a base install, where packages that user might need are already installed to make the OS easier to use.


If you want to take this process to the next step, you might want to have a look at archlinux, though I reckon, that Arch is a lot more difficult too grasp, because you need to edit your config files to after installation.

Hope that clarifies the pourpose of this script.

+1.And if you want to take it to even higher than the level that Arch Linux sets , then you are a geek xD :P And you need Linux From Scratch and/or Gentoo..Portage ftw :P

---

### Post by ashmew2 on 2009-05-13
> **spambait9876 said:**
> Another case of: "I am looking for a hammer.  Therefore everything I see must be a hammer, or it's useless." ?

Well its more of a I need a hammer , I'm a carpenter..So i probably dont need the Alienware Laptop right now..Even if i do , i can buy it whenever i want.. ;)

---

### Post by Ecclesia on 2009-05-13
I can't believe I somehow missed that you could install from a base system.  I used to install debian like this, but didn't really see a way to do that with Ubuntu.  Thank you to OP for putting this up.  It would be nice to see scripts for base systems with other managers/environments.  I've got an old computer I might use to play around with this - more likely using XFCE, though I'm also curious how minimal you could make KDE. If I have time I'll post my findings.  My older computers crawl with a base Xubuntu install, so I'll be looking for the differences.

---

### Post by optevo on 2009-05-13
For anyone who is interested, there's an article on Distrowatch along a simlar line - except they do their minimal install using (the even lighter) Xfce desktop:

[http://distrowatch.com/weekly.php?issue=20090504#feature]("http://distrowatch.com/weekly.php?issue=20090504#feature")

---

### Post by jbruced on 2009-05-13
> **abhiroopb said:**
> This is why people get put of by linux threads. I phrased my comments quite clearly. I did not intend to bash the author or his howto. I merely wanted to comment on how this could be improved, and where exactly this would be useful.

Even starting from a minimal install, this is still a simple apt-get install nothing more. Perhaps it may be more useful (like I have already suggested) to include which startup applications and bootup applications can be stopped.


You are not understanding the intent of the post. Sorry.

---

### Post by jbruced on 2009-05-13
> **joelbrock said:**
> i <3 this and will use this often!  I'm a little ashamed i didn't think of doing this myself.  I deploy ubuntu for my FOSS POS cash registers and lately i've been using debian because ubuntu has been bordering on bloatware.  Now i can stick with ubuntu AND cut the memory footprint.  Anything to improve performance.....

Very interested in what POS software you're running on Ubuntu.

---

### Post by jbruced on 2009-05-13
Excellent post, thank you!

Much needed for some of us.

---

### Post by Jeffsmashkot on 2009-05-14
Correct me if I'm wrong, but the last line of your script:
```
sudo apt-get -y gcalctool tsclient
```
is missing 'install' so it should be:
```
sudo apt-get install -y gcalctool tsclient
```

Without that, you get an error.  Just a FYI.

---

### Post by powel212 on 2009-05-14
I like the idea so I ran this on an old Pentium III. The instll process was about 65min. When it was all done I had no network access and therefore no internet. "Network adapter not configured" was what I was told. There were 2 lan cards in the box so I pulled one out and tried it again hoping to remove any possible redundancy and confusion. And then re-installed the whole thing again from scratch. After booting into the mini-desktop Once again no network adapter... Anyone else experience this problem?

When I go home I am going to put a new network card I have onthe shelf in the box and try it again.

Powel

---

### Post by Wollombi on 2009-05-14
To Paraphrase:

> "And Saint Attila raised the laptop up on high, saying, "O Lord, bless this thy ubuntu, that with it thou mayst blow thine enemies to tiny bits, in thy mercy." And the Lord did grin. And the people did feast upon the lambs and sloths, and carp and anchovies, and orangutans and breakfast cereals, and fruit-bats and large chu..."

Well, anyhow, THANKS, TheShiv for posting this!

---

### Post by utnubuuser on 2009-05-14
See: "#!CrunchBang Linux" at:[http://crunchbanglinux.org/]("http://crunchbanglinux.org/")

---

### Post by big_danmahony on 2009-05-14
This is awesome,I'm always happy to speed up my Ubuntu.

I'm just wondering though,is there an install cd to get this basic desktop working? (something that includes the script from the first post)
I can only use wireless where I am.
Any replies would be very appreciated.

---

### Post by TheShiv on 2009-05-14
Firstly, thank you for everyone who commented on my post. Feedback is always nice to read whether negative or positive; it always helps. I apologize for not writing back sooner. I was on a business trip which had me a tad tied up. I have read all comments and will try to answer everyones questions. I also apologize for just dumping the script on everyone without extra help. I guess I figured everyone was used to apt-get and could go from there.

Anyhow on to the comments (trying to answer them in the order received):

**abhiroopb**: I have another script that I use to do that I call "TweakBuntu". It removed packages based on laptop/desktop for the different versions of Ubuntu. I felt that it was counter-productive since it's a waste of time to install packages you know you aren't going to use and uninstall anyway. I figured if I posted a script like this I would get "flamed" by the Linux guru's of the world. Thank you for showing me not everyone can be satisfied. If you would like to use that script I will gladly send it your way.

**myschizobuddy**: I have seen battery life last longer using this method. I can't give you an exact figure because it depends on what you are using on your system (application wise). The more cpu power you are using the faster you will eat through your battery. However using this method if you don't install added background resources like compiz etc you should see a change in your battery life.

**gastly**: I unfortunately have only used KDE for about an hour. I never really liked it because I felt it used too many resources for my taste. I will try to figure out the equivalent of my script for KDE on a test machine later today.

**pdox**: ACPI support is installed with the ubuntu minimal package, it works just as well. laptop-mode is not however and since I never set up hotkeys etc on my laptops I've overlooked this. If you are using this method on a laptop you will probably want to use this
```
apt-get install laptop-mode-tools ubuntu-laptop-mode wpasupplicant
```
That should get you started for using your laptop.

**triplenine**: I prefer using this on my netbook because with my particular netbook (ASUS 1000HD) compiz doesn't play so well with my graphics card which I believe is a known problem and on the fix list for Jaunty. I normally just install maximus (apt-get install maximus) which makes all your windows maximize and fit to the tiny netbook, but unfortunately without compiz you will not be able to use the netbook-remix pretty menu. Good thing though is that you will use less power and your battery should last a little longer. Also it should be faster since no compiz will free some memory and lighten the load on your graphics.

**lepa71**: I'll be glad to try to assist you with the problem. The system you have tried this on. Have you used the normal ubuntu install before with success? Just want to make sure it's not a hardware compatibility issue.

**jeffsmashkot**: Thank you very much for catching that mistake in the script. It has been fixed; I was in a rush that day to get it posted because I had a deadline to finish.

**powel212**: What kind of network card are you using? Could you post the contents of your /etc/network/interfaces (remove anything you wish to remain private if any)

**utnubuuser**: I actually have a laptop with crunchbang on it and I love it for it's simplicity. However, I've found that OpenBox isn't the best window manager for all users, especially anyone fairly new since you have to learn how to configure the menu list. Although Crunchbang does have a nice gui I noticed to assist you with that. This is geared more towards people who want to keep gnome.

For those of you who stated I should recommend packages for users. The reason I did not do this is because I love linux for it's ability to suit my needs and my needs don't suit everyone's needs. When I first started with linux (so so many years ago) I didn't know what to use so I experimented until I found what I liked and what worked and then I stuck with that and added a little a long the way. Customizing linux to suit you as an individual is one of the more fun things about it. But if you would like me to tell you some of the packages I use then I will gladly.

**_Terminals:_**
gnome-terminal (default with gnome installation)
terminator (use it for doing the same thing for different systems etc)
guake (have to love the quake style console)

**_Burning:_**
brasero (default with normal ubuntu installation)
k3b (a really nice piece of burning software)
cdrecord (servers dont have gui's or at least shouldnt ;))

**_Browsers:_**
Firefox (on higher end machines, firefox has become a tad bloated)
Epiphany (on lower end machines, is awesome on netbooks)
lynx (for command line only systems)

_**Messaging:**_
Pidgin (i always loved gaim, never tried anything else)

**_E-Mail:_**
Evolution (all of my jobs used exchange so I was limited on choices)

**_Office:_**
OpenOffice (just what I got used to, i've heard koffice is good as well)
Dia & Kivio (my Visio replacements)
*To be honest, I work with huge documents for my job and openoffice doesn't work too well with the latest microsoft formats and tables, so I run Windows 7 in a virtualbox environment for documents. I wish microsoft would stop being a baby and make office for linux like they did for mac. That would be one M$ product I would love ;)

**_Web Development:_**
BlueFish editor (really nice for web coding)

**_Programming:_**
gedit (if it's small I just do it in gedit or nano)
MonoDevelop (I just started using this but am starting to like it for certatin developments)

**_Subversion:_**
subversion (duh)
Rapid-SVN (I just started trying this out, and it allows me a more visual look at large repositories. It's nice :))

**_Media:_**
vlc (I always removed ubuntu's totem and install vlc with all the plugins, it's a great media player)

Most of the tools I use are security related as I'm a security engineer. If anyone is interested in penetration tools for use with ubuntu systems I can give you ample of those.

You will notice a lot of the software I listed above is what you would normally find while doing a google search for "best software for this ..." Just because it's ranked the best however doesn't mean it's best for you. I've tried too many packages to count and that's really what you have to do is experiment. The packages listed above are based off whats on my work desktop. Each computer I own has a different purpose and the applications vary fairly heavily from eachother.

Good luck and if you have any more questions let me know! If you would like I can work on a larger more detailed script as I really geared this one for the somewhat experienced user who gears his or her machines to an exact state of what they want without worrying about the uninstallation of base packages which they may not use.

*I guess you can't really call it a script since it's just a few apt-gets. I really just got sick of uninstalling everything so I installed minimal and apt-get one package at a time until it finally came together, and then thought others might want to do the same without going through the process of figuring it out.*

Not a bad turn out for my first post :)
Thanks again for your comments,

-TheShiv

---

### Post by Lunik on 2009-05-14
I just got a little courage and tried that myself... Took me 2 or 3 hours to install everything (slow connection -_-) and 2 more to install my programs and backups.

Only problem I got was at the begining with the DHCP from my wireless router, but then I used a cable to connect directly and everything went fine.

So far everything seems much more responsive then before, Im using only 40% of the partition (instead of 58%), and even firefox for some reason is using much less memory (???).

I really recommend. Thanks OP!

Edit:
I just remembered... I had to edit the /etc/network/interfaces file and clean the primary interfaces list to network manager work.

---

### Post by TheShiv on 2009-05-14
Another thing I can add since people are talking time wise with the ubuntu minimal install (since it downloads all the packages). If you don't want to use minimal you can use ubuntu server edition, which gives you the command line without all the Xserver applications.

Or a really neat thing is having your own private Ubuntu mirror. I have one at my house on a really old PIII machine with 256mb of memory. I also built one at my work since I do a lot of minimal installs. A minimal install using your own repository is incredibly fast, and the best thing is that once it's done you don't have to waste time updating as it has the latest packages.

If you have an old PC and would like to do this just do:
```
apt-get install apt-mirror
```

You need a sizable harddrive. I use a 250gig (because I have more than an ubuntu repository). The size for backing up my entire Ubuntu repository which includes Hardy/Intrepid/Jaunty with both 32-bit and 64-bit (I use both) is 103Gigs. But if you just stored the version you use with your architecture it would be much less.

After installing **apt-mirror** you will have a new file in /etc/apt called mirror.list here's an example of mine for Ubuntu.

```
############# config ##################
#
set base_path    /repository
#
# if you change the base path you must create the directories below with write privlages
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript	$var_path/clean.sh
set defaultarch  i386
set nthreads     5
set _tilde 0
#
############# end config ##############

#-------------------------------------------------------------------------------------------------
# Ubuntu	(Jaunty x32/x64)
#-------------------------------------------------------------------------------------------------
deb-i386 http://archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu jaunty main main/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu jaunty restricted restricted/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu jaunty universe universe/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu jaunty multiverse multiverse/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty main main/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty restricted restricted/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty universe universe/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu jaunty multiverse multiverse/debian-installer

#-------------------------------------------------------------------------------------------------
# Ubuntu	(Intrepid x32/x64)
#-------------------------------------------------------------------------------------------------
deb-i386 http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu intrepid-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu intrepid main main/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu intrepid restricted restricted/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu intrepid universe universe/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu intrepid multiverse multiverse/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid main main/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid restricted restricted/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid universe universe/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu intrepid multiverse multiverse/debian-installer

#-------------------------------------------------------------------------------------------------
# Ubuntu	(Hardy x32/x64)
#-------------------------------------------------------------------------------------------------
deb-i386 http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu hardy main main/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu hardy restricted restricted/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu hardy universe universe/debian-installer
deb-i386 http://archive.ubuntu.com/ubuntu hardy multiverse multiverse/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu hardy main main/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu hardy restricted restricted/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu hardy universe universe/debian-installer
deb-amd64 http://archive.ubuntu.com/ubuntu hardy multiverse multiverse/debian-installer

#-------------------------------------------------------------------------------------------------
# Apt Mirror Clearning
#-------------------------------------------------------------------------------------------------
clean http://archive.ubuntu.com

```

Next I add to my /etc/crontab
```
0  1	* * *	root	apt-mirror /etc/apt/mirror.list && /repository/var/clean.sh
```

Which updates my mirror every night at 1am while I'm sleeping. Of course you need to change /repository to the path where you are going to store your repository.

If you are planning to do a lot of minimal installs (since it is faster than cd/dvd [if you have your own repository]) then I highly recommend creating one.

You will also need to install either apache or use an FTP server so that your installs can pull packages from this repository. Apache may be easier since you can just link your repository to your docuroot (this is what I do). For instance my repository is located at **/repository/mirror/archive.ubuntu.com/ubuntu** so I type:
```
ln -s /repository/mirror/archive.ubuntu.com/ubuntu /var/www/ubuntu
``` This allows me to go to [http://my.mirror.box/ubuntu](http://my.mirror.box/ubuntu) and see the packages and this also allows me to use the minimal install cd and manually put in my mirror. /var/www is the default docuroot for a fresh install of apache2 (if you are using apt-get).

If I went too fast another user on ubuntu forums has posted a very detailed howto which may actually help you further. It can be located at: [http://ubuntuforums.org/showthread.php?t=599479](http://ubuntuforums.org/showthread.php?t=599479)
by **bmk789**

Having my own repository has saved me so much time cutting my minimal installs from 1-3 hours to 10-15 minutes. It's also nice for new Ubuntu releases, i just add the repo, wait one night wake up in the morning and do an dist-upgrade and it flies right through (anyone who updates to the new release as soon as it's released knows how bogged down the public mirrors can be)

-TheShiv

---

### Post by thejinx0r on 2009-05-14
The script din't actually work for me.
Not sure why. But I'm assuming that saving stuff in notepad and then running it doesn't help.

I ended up just typing the apt-get install commands and it works now. Just got to tweak it to my likings now :)

---

### Post by powel212 on 2009-05-14
I got it working with the new-er LAN card.

It's all up and running now. Yes it is worth it. Much lighter and more responsive now. Cut my boot time in half from the full intrepid install.

after boot using 125m of RAM

I also like the epiphany browser. It runs way better on the old Copermine intel 733Mhz Chip. I've used Midori in the past as a light browser but epiphany seems to have more options.

Very glad I did it.

I mostly use this machine as a testing station because I manage a network file/print-server at work and when I run into trouble there I do my testing on the home network.

Thanks for the post.

Powel

It does take some time though. Base setup then installation took about 65 Minutes all in.

---

### Post by sandy8925 on 2009-05-14
Some suggestions:

1) installing mplayer rather than vlc would be much better. It supports playing almost any media.

2) Some people say that open office is too slow and sluggish. i definitely agree. it's to slow for me. could you suggest some better alternatives ? for word processing i have ehard that scribus and abiword are lighter.

Also can we install and use the foll:

wine
Nvidia drivers (from website)
skype
compiz

---

### Post by powel212 on 2009-05-14
What does the "-y" part of sudo apt-get -y install... do?

P

---

### Post by Sealbhach on 2009-05-14
> **powel212 said:**
> What does the "-y" part of sudo apt-get -y install... do?

P

If you run "man apt-get" you get lots of information on how to run the apt-get command. Here's the part about -y:

       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install a unauthenticated
           package or removing an essential package occurs then apt-get will
           abort. Configuration Item: APT::Get::Assume-Yes.

.

---

### Post by bailout on 2009-05-14
I agree that a tutorial from the other end ie what to remove would also be good but the place for that is another howto not this one. What would help for both approaches is a guide to what processes ubuntu standard installs and runs. This would help people starting from a minimal install to know what functionality they are missing with the minimal install approach and how to add the bits they need. Applications such as browser, office etc are obvious but the underlying processes and services are not.

How reliable is upgrading a minimal install to a new ubuntu release?

---

### Post by bailout on 2009-05-14
Another issue with adding packages to a minimal install is the ubuntu dependency packaging. I have just installed unr to my netbook and am adding some extra apps. Digikam requires a huge number of additional packages installed (81). I accept that being a kde app it needs a lot of extra kde libs but not this many. I also looked at installing abiword. That has plugins that are optional, according to the description but ubuntu insists on installing them with abiwod.

It seems that ubuntu package managers add any related package as a needed dependency instead of an option and this must limit how lite a ubuntu install can be even starting from a minimal install and adding just what you want.

---

### Post by Ozitraveller on 2009-05-14
I have found these quite useful:

debian minimal desktop installation
[http://wiki.dennyhalim.com/debian-minimal-desktop-installation](http://wiki.dennyhalim.com/debian-minimal-desktop-installation)

InstallationLowMemorySystems
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Minimal Xubuntu 9.04
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

---

### Post by powel212 on 2009-05-15
Is there a way to return to previous state?

First we install the base system and end up with a command line system.

Then we install the desktop environment.

But if we make a mess of the install is there a way to dump the desktop environment we just installed and return to the state where we just had the command line install?

I've made a mess of it a couple of times now and having to re-install te base system each time is a bit time consuming. I am also trying some different configurations in VirtualBox and so it would be nice to try one desktop environment and then ditch it and try another.

Powel

---

### Post by TheShiv on 2009-05-15
Hello again,

**[SIZE="4"][COLOR="Blue"]Sandy[/COLOR][/SIZE]**:
You can install all you've asked. Here's how

For *Wine*: 
```
sudo apt-get install wine
```

For *Nvidia* you can add the drivers from apt-get depending on the card you have. It may be better however if you stick to downloading this installer via the Nvidias website. If you want to see what's available for Nvidia in the repository type:
```
sudo apt-cache search nvidia
```
This will return packages matching nvidia. You will probably want to find out through a simple google search which installer will install drivers for your card. Another good suggestion is the Ubuntu Hardware Drivers located in "System > Administration > Hardware Drivers" I use this to install my Nvidia drivers and it works very well.

For *Skype* you need to add the skype repository to your sources list. This can be achieved by doing:
```
sudo echo "deb http://download.skype.com/linux/repos/debian/ stable non-free" >> /etc/apt/sources.list
```
Now you can 
```
sudo apt-get install skype
```

For *Compiz* you can install different levels depending on what you are going to use it for. You can just do:
```
sudo apt-get install compiz
``` which will install everything you need to use compiz. Or you can install the "compiz-core" which should install a less bloated compiz. You will probably want to install "compizconfig-settings-manager" which should help you in configuring it.
```
sudo apt-get install compizconfig-settings-manager
```

**[SIZE="4"][COLOR="Blue"]bailout[/COLOR][/SIZE]**:
Upgrading a minimal install to the next release of ubuntu works just as well as a normal install. The only difference between the normal install of ubuntu and a minimal install is just that, it installs only what is required for the OS to run and then you can build your system from the ground up. Doing a release upgrade will still verify which packages you have installed and upgrade them and any of their dependencies to the next version.

About the apt-get installing packages that aren't required. There's only one way really to get away from that, which is to download the source tarballs and build the applications you want from the source. I do this for a lot of applications I use due to the need to update them to the next version without waiting for them to be approved and released by the package maintainers. Installing from the source will allow you to customize the install of that application to the level you may be looking for. If you would like to do this I would recommend installing the development essentials which should alleviate some problems you may run into, you can do that by:
```
sudo apt-get install build-essential
```

**[SIZE="4"][COLOR="Blue"]powel212[/COLOR][/SIZE]**:

If you want to go back to the original way it was before you installed the desktop, the easy way would be to just "**sudo apt-get --purge remove the.packages.you.installed**"; using apt-get remove with the --purge will remove configuration files and no longer needed files once used by that package. Then after it's installed you should be able to remove it's dependencies with "**sudo apt-get --purge autoremove**" which will also clean up any files no longer needed by these packages. When you are removing a package you know you will not use again it's always best to use the --purge option. So simply put, just use that command to remove what you installed and it should do a pretty good job of cleaning up any messes. Here's how to clean up the packages I had you install on the first post (you will want to modify it to include any other packages you may have installed and want to remove):
```

echo Remove 1st Packages
sudo apt-get --purge remove \
gnome-core \
gdm \
network-manager-gnome \
fast-user-switch-applet \
human-theme \
x11-xserver-utils \
tangerine-icon-theme \
gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk \
gnome-screensaver \
gnome-utils

echo Remove First Packages Dependencies If Any
sudo apt-get --purge autoremove

echo Clean Up Downloaded Packages
sudo apt-get clean && sudo apt-get autoclean

```

---

### Post by powel212 on 2009-05-15
After multiple attempts and and multiple configurations I have just one question.

Why does the network manager always show "Device not managed" and yet I can access the network?

P.

---

### Post by polygonal on 2009-05-15
It's all dandy and good but ... there is no sound! I installed the vanilla ubuntu 9.04 a few days ago, and no problem with sound there, so there is something missing in this minimal installation. Any idea?

Also, I rather like the new notification system, but this minimal installation only gives the older notifications. What package should I install to get the new notifications?

---

### Post by anonymous_user on 2009-05-16
For the new notifications install "notify-osd".

As for your sound, have you ran any mixer and made sure the sound isn't muted?

---

### Post by agel1 on 2009-05-16
i need to know if using the server edition, i don't need internet connection (my computer (a desktop) use wifi).?

i need to print the script, or save it with some extensions and run it when the install finish.?

thanks

---

### Post by polygonal on 2009-05-16
> **anonymous_user said:**
> For the new notifications install "notify-osd".

As for your sound, have you ran any mixer and made sure the sound isn't muted?

I figure the notifications out, too. For the sound, I checked mixer to make sure everything is on high and nothing is muted, and also tried adding any packages remotely related to audio. My last try is installing ubuntu-desktop without the recommended packages, and I still don't have sound! All I have now is unbelievably ugly "beeps" that completely drive me nuts. The "Sounds" app under System - Preferences did not give any sound when I tried "Test" with any options there. :frown:

---

### Post by agel1 on 2009-05-17
> **agel1 said:**
> i need to know if using the server edition, i don't need internet connection (my computer (a desktop) use wifi).?

i need to print the script, or save it with some extensions and run it when the install finish.?

thanksi move my computer close to the modem and install without problems in like 1:20, the installation only use 1.4gb and is a little faster than a normal ubuntu installation

can somebody tell me how to put update manager in administration.?

---

### Post by mfarley on 2009-05-18
I've followed the minimal method outlined here, however now I need to add network printers and can't find the GUI tool in System -> Administration.  How do I add printers?  (9.04)

---

### Post by agel1 on 2009-05-19
i think is better if somebody make a (iso) to install this way, because the people who use wifi cant use it, and the download of the packages is really slow

i dont know if it is possible

---

### Post by evaldas on 2009-05-19
It is preferred to use aptitude from the very beginning instead of apt-get, because aptitude builds installed packages database, so you can always remove/purge the package (installed with aptitude) with all the dependencies that got installed originally:
```
aptitude purge --purge-unused package [more packages]
```
With aptitude also you can install packages without recommended or suggested packages:
```
aptitude install --without-recommends --without-suggests package [packages]
```

---

### Post by luptinpitman on 2009-05-20
As far as the Network Manager Applet not displaying correctly I found a discussion here about others having similar problems though not related to this very cool minimal install.

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606")

Relevant fix post:

> If like me you *want* your connection to be managed by the network manager, you probably want to update your /etc/NetworkManager/nm-system-settings.conf with something like this :

[main]
plugins=keyfile

[ifupdown]
managed=true

You should of course save your former nm-system-settings.conf in case something goes wrong.

Now why it doesn't show up correctly upon first minimal install I can't say, but this did the trick for me.  Had to reboot after change, logout didn't get it done.

Thanks for the original post on how to do this thing!  Hate all the extra crap that comes with the standard desktop install.

---

### Post by mkvnmtr on 2009-05-20
Well In used your list of programs to start my minimal install and I should thank you. Less struggling than any of the few times I have done it. I used it to replace my regular 9.04 install and I don't believe I will use a complete disk again. Everything I need seems to be working and the only thing In have found I didn't need was some bluetooth programs. Quickly removed. I think I will do the same thing on my Mac powerpc box.
On my old equipment I seem to get some bugs on  a full install that I don't find with a minimal. Have no idea what they are from and they seem to be different on every distro upgrade.

---

### Post by Emper on 2009-05-21
I found a better solution to the Network Manager problem. Just remove (or comment) the options below "primary network interface" in /etc/network/interfaces

---

### Post by agel1 on 2009-05-22
everybody should install UBUNTU like this, is faster than windows 98 in a core 2 quad computer

---

### Post by j0hn00 on 2009-05-23
i'm loving the minimal install over the standard install. two problems though... 

1. i can't get my system to restart. it hangs at "deconfiguring network device". i have to eventually hold the power button down to shutdown.

2. i've installed extra language packs, but can't seem to get scim bridge to work correctly. after installing additional language packs on a standard install, a small keyboard icon appears in the notification area and i'm able to switch input languages with "ctrl+space".

any ideas? any help would be appreciated.

---

### Post by gonzaleuro on 2009-05-26
How to achieve Ubuntu minimal install in a netbook (NC10) without access to a cdrom drive. I have install the .iso image to a usb pendrive and boot the netbook from it, but then I dont know what to do.

Can anybody help me?

---

### Post by agel1 on 2009-05-27
> **gonzaleuro said:**
> How to achieve Ubuntu minimal install in a netbook (NC10) without access to a cdrom drive. I have install the .iso image to a usb pendrive and boot the netbook from it, but then I dont know what to do.

Can anybody help me?you need to use the alternate cd and when you boot press f4 and select minimal installation then when the installation finish, boot into your new system and run 
------------------
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
-------------------

you need internet connection

---

### Post by j0hn00 on 2009-05-28
> **j0hn00 said:**
> i'm loving the minimal install over the standard install. two problems though... 

1. i can't get my system to restart. it hangs at "deconfiguring network device". i have to eventually hold the power button down to shutdown.

2. i've installed extra language packs, but can't seem to get scim bridge to work correctly. after installing additional language packs on a standard install, a small keyboard icon appears in the notification area and i'm able to switch input languages with "ctrl+space".

any ideas? any help would be appreciated.

just in case anybody had the same problem or is interested in the solution...

1. i found a solution in thinkwiki
edit the /etc/init.d/alsa-utils file
search for "stop)" and right below it add
ifconfig eth0 down
ifconfig wlan0 down

2. in the gnome panel, go to add/remove and search for language support and install it. it takes care of everything just like under the standard install.

with the minimal install, my system went from (upon boot)
processes: 230 -> 211
memory: 410mb -> 220mb

---

### Post by Ozitraveller on 2009-06-01
I thought I would add this if anyone was interested.

```
#! /bin/bash
# chmod +x UbuntuSetup.sh

sudo apt-get update && sudo apt-get upgrade

#######################################################################
# Xubuntu-Desktop-Minimal: Post-install script to install only the bare
#     essentials of an Xubuntu Desktop.
#######################################################################

echo "[*] Installing Xubuntu Essentials"
sudo apt-get install dontzap && sudo dontzap --disable
sudo apt-get -y install xorg xdm xfce4 xfce4-goodies
sudo apt-get -y install network-manager-gnome xubuntu-default-settings

echo "[*] Installing Application Essentials"
sudo apt-get -y install gdebi-core synaptic xinit gparted
sudo apt-get install epiphany-browser
sudo apt-get install conky leafpad dillo
sudo apt-get install iotop

sudo apt-get -y remove bluez-utils bluez-gnome

sudo apt-get -y install logrotate localepurge
sudo apt-get autoremove
sudo apt-get clean
```

---

### Post by Ozitraveller on 2009-06-01
Checkout full Circle magazine 21 and 22 to install Cruncheee, they show you how to install from a usb stick.

---

### Post by k3lt01 on 2009-06-05
There are many ways to do this. [Here]("http://www.psychocats.net/ubuntu/minimal") is but another one and this is what I do.

---

### Post by Ozitraveller on 2009-06-06
Nice :)

---

### Post by Teddy_P on 2009-06-06
TheShiv,
I did this to one of our computers that have been lagging while on the net. It works great and the fan that drives us crazy hardly ever comes on any more.

Thank you
Teddy

---

### Post by bongo_950 on 2009-06-07
Has anyone been able to do this exact same thing on the Hardy?

---

### Post by k3lt01 on 2009-06-07
> **bongo_950 said:**
> Has anyone been able to do this exact same thing on the Hardy?I have done Hardy the way tat is described in the link I posted, so thereis no reason why it couldn't be done the way Shiv describes.

---

### Post by ekss on 2009-06-10
thank you

---

### Post by fellowweb on 2009-06-14
Thank you for the great skript, TheShiv!
 
This is even perfect for people who want to set up some kind of home server, although they don't want to miss out on a GUI - at least for the time it takes to get slowly accustomed to the Linux command line.
 
As the desktop does not need to look that perfect than, I left out additional packages (**gnome-themes-ubuntu**, **ubuntu-artwork** and **gnome-screensaver**). Instead of apt-get I use aptitude.
 
The GNOME system essentials then look something like this:
```
sudo aptitude -y install **gnome-core gdm network-manager-gnome fast-user-switch-applet **\ 
**human-theme x11-xserver-utils tangerine-icon-theme jockey-gtk gnome-utils**
```As essential applications, I installed:

[LIST]
[*]**system-config-samba** (GUI for SMB configuration, also installs **samba**)
[*] **gnome-nettool** (GUI for several network tools such as ping etc.)
[*] **ntfsprogs** (tools for unproblematic use of NTFS file systems)
[*] **vino** (VNC server instead of tsclient as a VNC client)
[*] **update-manager** (addition to Synaptic for Ubuntu updates)
[*]**gdebi** (simple GUI tool for installing .deb files)
[*]**system-config-printer-gnome** (graphical configuration for CUPS, for HP printer also install **hplib**)
[*]**brasero** (GUI for burning DVDs/CDs)
[*]**gparted** (graphical partition manager)
[*]**epiphany** (as mentioned by TheShiv)
[*]**language-pack-gnome-XX **and **language-pack-gnome-XX-base **(with XX representing your local language, e.g. **de**)
[/LIST]
As others asked for how to graphically setup the printer, **system-config-printer-gnome** ist the way to go.
 
Regarding **vino**: If you really want to remote control your Ubuntu PC in a convenient way, I have found **[Nomachine's NX]("http://www.nomachine.com/select-package-server.php?id=1&ids=2")** to be extremely helpful and comfortable. For private use it's free. Therefore, in essence, I do not use VNC at all.
 
The new script then looks like this:
```

#!/bin/bash
#######################################################################
# Ubuntu-Minimal for Home Servers: Post-install script to install only the bare
#              essentials of an Ubuntu Home Server with GNOME.
#######################################################################
echo "
[*] Installing Gnome Essentials"
sudo aptitude -y install **gnome-core gdm network-manager-gnome fast-user-switch-applet **\ 
[B]human-theme x11-xserver-utils tangerine-icon-theme jockey-gtk gnome-utils
[/B]echo "
[*] Installing Application Essentials"
sudo apt-get install -y **system-config-samba gnome-nettool ntfsprogs vino update-manager **\
**gdebi system-config-printer-gnome brasero** **gparted** **epiphany**

```I am not that well experienced with Ubuntu. However, I hope that everything is correct and that this might be helpful for some of you.
 
In case of questions, there are probably much more experienced people out here than me. So please do not rely on my little expertise. ;)

Eventually one plea: Please don't try to get me into the argument of running a GUI on a server. Each to his own.

---

### Post by scales on 2009-06-16
humm great idea, but it doesnt seem to work for me.  i installed the cli version and am unable to run the script.  i did remember to make it executable too! anyone else have problems? also i would love to add compiz to this, but apt-get install compiz didnt give me enough stuff?

---

### Post by j0hn00 on 2009-06-24
> **scales said:**
> also i would love to add compiz to this, but apt-get install compiz didnt give me enough stuff?

i had the same problem. after installing compiz and simple-ccsm, some dependencies were missing. installing avant-window-navigator pulled in all the dependencies and compiz started working correctly.

---

### Post by pwebster25 on 2009-07-07
I just ran this list of apps as an apt-get script.  It sure beats adding ubuntu-desktop and then trying to removing all the junk.  I was just trying to add a gui to my server without all the bells and whistles.  It would be nice if they had just a barebones version of gnome.

---

### Post by fellowweb on 2009-07-08
> **pwebster25 said:**
> It would be nice if they had just a barebones version of gnome.
  
Isn't this gnome package something like a "barebones version of gnome"?

---

### Post by sigurnjak on 2009-07-08
Lately i have been messing with some P3 systems  with ati rage on board video and 256 mb ram and came with this combo for a light and speedy set up :

no. 1     sudo apt-get install xorg slim lxde vlc synaptic
no. 2     sudo apt-get --no-install-recommends install firefox-3.0
no. 3     sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Then go to synaptic and add what you need via gui , nice and easy for new folk .

This way i end up with very usable system  needing only 64 mb ram .
As for compiz questions , is it not kind of strange going for minimal install and then adding compiz ?

And for minimal printer interface try this :
[http://localhost:631/](http://localhost:631/)

It is cups web interface

Enjoy folks ! Hope this help someone !:p

---

### Post by ace214 on 2009-07-08
Thanks for putting this idea in my brain. Thought I would add my two cents.

With regard to your advice about setting up an apt-mirror, it is probably more practical for people to use aptoncd and add the CD to the sources.list or set up apt-cacher.

---

### Post by Crunchy the Headcrab on 2009-07-12
Thanks for this.  I think it is a precious tool for beginners.  I don't think the default jaunty is totally stable for whatever reason.  However, I've had much better results by doing a minimal install and then updating.  You inspired me to do a custom kde install, which is running like an absolute dream and looks fantastic!

---

### Post by Crunchy the Headcrab on 2009-07-12
> **fellowweb said:**
> Isn't this gnome package something like a "barebones version of gnome"?
Indeed.  It's hard to get a more barebones version of gnome than gnome-core.  To the person that asked the original question: just don't download some of the other tweaks if you don't like them.

---

### Post by sanicki on 2009-07-15
Please continue to update this script as new Ubuntu versions are released. I am using it as the base for a number of [kiosks for my local library.]("http://tinyurl.com/ppl-kiosk")

My only problem is that the screensaver needs to be clicked to wake, moving the mouse does nothing. Anyone have any idea how to correct that?

Thanks in advance for any assistance.

---

### Post by zbeckerd on 2009-07-16
Excellent.  I have been thinking about this since Jaunty came out.  What I plan to do is do a install onto a old p3 T22 for starters.  My main goal though will be to install a minimal setup on my main box and then run virtual box for anything heavier so that when I break it I can go back.  Should be fun.
I just finished installing jaunty on a Zaurus handheld.  That definitely got me back to working from the command line.

I did the install on the T22 and the memory requirements are less but boot time is greater then the stock 9.04 install.  It is snappier.  But I now plan to dual boot with puppy as it does most of what I need for older hardware.

Still this is much less bloat!

---

### Post by vikjon0 on 2009-07-18
Yes, I agree this is great and together with remasterys I can create my own distro.

The problem is that autologin does not work. I am sure it is a small thing but I have no idea where to look.

Does it work for anyone else? Any ideas?

//J

---

### Post by stauntonel on 2009-07-19
Minimal install was the reason i changed my os to Debian.
But for some reason my new laptop does not like Debian.
Something to do with fancontrol and overheating cpu...
After installing kubuntu this way, no problems with overheating!
1-0 for ubuntu! Wifi works, out of the box even with GPA! 2-0
df -h told me this minimal install was using 1.3 gig. Debian needs mutch less 2-1.

one thing that doesnt work thoug is sound so i installed alsa.
What puzzles me is where is the good old alsaconf util?

---

### Post by vikjon0 on 2009-07-19
> The problem is that autologin does not work.

OK, it now works. I have no idea what is was, but I made a new minimal install and added ONLY
sudo apt-get install xorg gdm  gnome-core 

I will contiue and see if it breaks again when I add more stuff.

---

### Post by vikjon0 on 2009-07-19
I have updated the list for Ubuntu 9.04 and I think also made it more complete.


Display Manager&Desktop  
------------------------
sudo apt-get -y install xorg gdm  gnome-core 

Reboot and you have a basic desktop!
(exlude gdm and you can start manually with "startx" instead)
You can now start add utilities and applications.


Gnome basics
------------
gnome-system-tools gnome-utils x11-xserver-utils 



Remaining system utilities
--------------------------
and stuff that will make it look like a standard ubuntu desktop

apport-gtk  (frot end crash report system)
jockey-gtk
usplash
update-manager 
notify-osd 
update-notifiers
network-manager-gnome
fast-user-switch-applet


Themes etc
gnome-screensaver 
ubuntu-artwork human-theme tangerine-icon-theme gnome-themes-ubuntu xcursor-themes


---Network manager fix
sudo nano /etc/network/interfaces
Comment out the lines below "primary network interface"
(This is the solution that match the standard 9.04 setup)


laptop
---------------
laptop-mode-tools 
ubuntu-laptop-mode 
apmd 		-advanced power management
powernowd	-CPU speed (not only for laptops?)

---

### Post by spike_naples on 2009-07-20
I find it quite useful for beginners like me who want a near "naked" install. I'm one of the kind of users who would want to install everything that is familiar and quite useable. 

Thanks.

---

### Post by vikjon0 on 2009-07-20
Standard applications that is pre-installed in the full desktop 9.04. (not complete list)

firefox (or use: epiphany-browser epiphany-extensions)
brasero         -CD/DVD writer
gnome-nettool
nautilus-share  -share a folder by righ click
gdebi  		- offline package manager
vino 		-vnc Remote desktop access
system-config-printer-gnome  
usb-creator
powernowd	-CPU speed

---

### Post by Bart_D on 2009-07-22
> **TheShiv said:**
> ...```

#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#			  essentials of an Ubuntu Desktop.
#######################################################################
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet \
human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk gnome-screensaver gnome-utils
echo "[*] Installing Application Essentials"
sudo apt-get install -y gcalctool tsclient

```...

I won't be using a script format, but rather just straight from the command line.  Will this command, after minimal CD, give me everything that the OP has listed in his script?:

```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
```

Also, what does this do: 
```
sudo apt-get install -y gcalctool tsclient
```

---

### Post by Ozitraveller on 2009-07-22
Yes

'gcalctool' is the desktop calculator that has been proposed for GNOME 2.4. 

tsclient (Terminal Server Client) is a frontend for rdesktop and other remote desktop tools.

---

### Post by Bart_D on 2009-07-22
Thanks.

I don't need either of those.  That's comforting!

---

### Post by TheShiv on 2009-07-24
> **Bart_D said:**
> I won't be using a script format, but rather just straight from the command line.  Will this command, after minimal CD, give me everything that the OP has listed in his script?:

```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
```

Also, what does this do: 
```
sudo apt-get install -y gcalctool tsclient
```

Sorry, I haven't replied to this thread in forever. Unfortunately, I've been incredibly tied up with work and have been flying all around the east coast.

Bart_D: Yes, that will accomplish the same thing. I guess in the initial making of this thread I could have just put apt-lines, I put things in shellscripts just to make them more automatic for me with less typing and that's what I pasted. Some people will not consider it a script because it doesn't have functions and variables etc. I consider a script anything that does something for you automatically.

If anyone has any more questions I'm going to start monitoring this thread again. I was reviewing the past posts and was very pleased at how everyone has been helping each other and even saw some users posting modifications for Kubuntu and the latest Jaunty release. Great work to those who've helped in my place. I appreciate it.

---

### Post by Ozitraveller on 2009-07-26
I would normally do this after the install

# So simply disable and uninstall/remove bluetooth from Ubuntu.
sudo apt-get --purge remove bluez-utils bluez-gnome

sudo apt-get -y install logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

---

### Post by Ozitraveller on 2009-07-27
This might be nice too.

I have a smaller screen on my old pc, so this will save real estate.

Install a Simplified Nautilus for Ubuntu
sudo sh -c "echo 'deb [http://ppa.launchpad.net/0-launchpad-mejlamej-nu/ppa/ubuntu](http://ppa.launchpad.net/0-launchpad-mejlamej-nu/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A93A0AB
sudo apt-get update && sudo apt-get upgrade

---

### Post by lavezarez on 2009-07-27
thanks for this how-to and those who posted what applications should be included in the minimal config.

will implement this with my old desktop soon-to-be samba server :D

---

### Post by omichaels on 2009-07-27
> **lepa71 said:**
> So I followed your guide, but I can't start X. It gives me black screen.

Any help

Likewise, X won't start. I executed the following on a fresh 8.04 LTS Server build
```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils xinit
sudo apt-get install -y gcalctool tsclient

```I had to replace "gnome-themes-ubuntu" with "gnome-themes" as the former was reported as not found in the archive.

Attempting to execute startx manually (from console) returns:
X: cannot stat /X11/X (No such file or directory), aborting. \ giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

I am very keen to get a minimal desktop up and running but am a total noob so would appreciate any suggestions.

---

### Post by omichaels on 2009-07-28
> **lepa71 said:**
> So I followed your guide, but I can't start X. It gives me black screen.

Any help

Seems that Xorg was not installed as a part of dependency resolution. The following command solved my problem:

```
sudo apt-get install xorg
```Hope it works as well for others


Thanks, TheShiv, for contributing this - it is just what I was seeking

---

### Post by jpope on 2009-07-28
Thanks for this guide. I installed this setup on my EeePC 100HE and it runs beautifully. Also, after installing [eee-control]("http://greg.geekmind.org/eee-control/") and having a low memory footprint, I am getting ~6 hours of battery life. Was getting under 4 hours on the UNR and therefore was staying in XP more than Ubuntu... 

Thanks again.

---

### Post by lavezarez on 2009-07-29
After installing the minimal desktop, and installing the packages TheShiv posted,  I am unable to install samba properly because the "Sharing Options" is missing when I right-click on any of the home folders.

I already did **sudo apt-get install samba**, and did **sudo apt-get update**

Hope you guys can help. :)

Thanks!

---

### Post by Ozitraveller on 2009-07-29
I think maybe this needs to be installed:

nautilus-share

Nautilus Share allows you to quickly share a folder from the GNOME Nautilus file manager without requiring root access.

---

### Post by fellowweb on 2009-07-30
@lavezarez: **system-config-samba** is a great way to configure Samba with a GUI. In my opinion, it is superiour to the options in Nautilus.
 
See my earlier post in this thread:
 
> **fellowweb said:**
> As essential applications, I installed:

[LIST]
[*]**system-config-samba** (GUI for SMB configuration, also installs **samba**)
[*] **gnome-nettool** (GUI for several network tools such as ping etc.)
[*] **ntfsprogs** (tools for unproblematic use of NTFS file systems)
[*] **vino** (VNC server instead of tsclient as a VNC client)
[*] **update-manager** (addition to Synaptic for Ubuntu updates)
[*]**gdebi** (simple GUI tool for installing .deb files)
[*]**system-config-printer-gnome** (graphical configuration for CUPS, for HP printer also install **hplib**)
[*]**brasero** (GUI for burning DVDs/CDs)
[*]**gparted** (graphical partition manager)
[*]**epiphany** (as mentioned by TheShiv)
[*]**language-pack-gnome-XX **and **language-pack-gnome-XX-base **(with XX representing your local language, e.g. **de**)
[/LIST]
As others asked for how to graphically setup the printer, **system-config-printer-gnome** ist the way to go.

---

### Post by sdlinux on 2009-07-30
> **TheShiv said:**
> 
I'm one of those users who likes to build his system from the ground up, so I wrote this simple post-install script which will give you a complete minimal desktop.

After running this script your system will look the same as a fresh install of ubuntu just without all the added software.

The first step to accomplish this is install a base system either using the Ubuntu Minimal CD (I use this along with my personal repository to create quick installs) or you can use the Ubuntu Server edition.

-TheShiv

I'm confused, to install a minimal install, first install the minimal install and then run your script? 

Shouldn't it be, first install the desktop version and then run your script? Maybe I am just biased cus I installed the desktop version and I am looking for something more minimalistic.

---

### Post by lavezarez on 2009-07-30
hi felloweb, hi ozitraveller:

i have installed nautilus package yesterday, and did the following to check my packages:

**apt-cache showpkg nautilus-share**
[I]Package: nautilus-share
Versions: 
0.7.2-4ubuntu1 (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: 12abf75bd52cbea4113eeeaace72c2db[/I]

[B]
apt-cache showpkg system-config-samba[/B]
[I]Package: system-config-samba
Versions: 
1.2.63-0ubuntu4 (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
                  MD5: 13f517dcaf1f933317ac20e696b0e8c5[/I]


but still, no sharing options.

would could be missing? :(

Thanks again for your support.

---

### Post by jpope on 2009-07-30
> **sdlinux said:**
> I'm confused, to install a minimal install, first install the minimal install and then run your script? 

Shouldn't it be, first install the desktop version and then run your script? Maybe I am just biased cus I installed the desktop version and I am looking for something more minimalistic.

Actually, the desktop version installs all of the stuff in the script plus many, many more packages. 

When you start with the minimal install cd, you are only installing the very basic things that the OS will need to run. At that point the OS is only a command line and the script will install the packages needed to have a graphical interface. You will not be able to get much more minimalistic than this approach.

---

### Post by lavezarez on 2009-07-31
> **sdlinux said:**
> I'm confused, to install a minimal install, first install the minimal install and then run your script? 

Shouldn't it be, first install the desktop version and then run your script? Maybe I am just biased cus I installed the desktop version and I am looking for something more minimalistic.


the post assumes you haven't installed the desktop version, or at least willing to remove the desktop version and use the minimal cd install instead.  you can get it [here]("https://help.ubuntu.com/community/Installation/MinimalCD").  then run the scripts.

---

### Post by fellowweb on 2009-08-01
> **lavezarez said:**
> [B]
apt-cache showpkg system-config-samba[/B]
[I]Package: system-config-samba
Versions: 
1.2.63-0ubuntu4 (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
                  MD5: 13f517dcaf1f933317ac20e696b0e8c5[/I]

  
**system-config-samba** does not integrate into Nautilus. However, it is extremely simply. Just open System > Administration (Using a German system I don't know the exact title, it's the second point in the menu below Settings) > Samba.
 
Then you have a graphical interface which is really self explaining. Also have a look at this [Howto for **system-config-samba** on Feodora]("http://www.labtestproject.com/configure_samba_file_server_on_fedora"), which works identically.

---

### Post by Ozitraveller on 2009-08-05
I just found this:
[http://banshee-project.org/~abock/meerkat/](http://banshee-project.org/~abock/meerkat/)

Might be useful if you are running this minimal ubuntu on a netbook.

---

### Post by scales on 2009-08-05
cool i like the look, makes it a little more chrome-ish.

I like the concept/idea of a minimaly gnome.  i really would like a similar thing for xubuntu.  the best i could find was [http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

not bad but i dont think it installs much of the basic things like archiver, picture viewer, screensaver, etc.  anyone have advice on this?  maybe i should start a new thread.


EDIT: nevermind i found one
[http://ubuntuforums.org/showthread.php?t=1225393&highlight=xubuntu+minimal&page=2](http://ubuntuforums.org/showthread.php?t=1225393&highlight=xubuntu+minimal&page=2)

---

### Post by Ozitraveller on 2009-08-05
Try here:
[http://ubuntuforums.org/showthread.php?t=1155961&page=8](http://ubuntuforums.org/showthread.php?t=1155961&page=8)

---

### Post by vikjon0 on 2009-08-10
> not bad but i dont think it installs much of the basic things like archiver, picture viewer, screensaver, etc. anyone have advice on this? maybe i should start a new thread.

What I do is to keep a standard desktop installation in a virtual machine. When I need a functionality I check in standard what the name is and install it in my "minimal"

---

### Post by vikjon0 on 2009-08-10
I noticed that sometimes extra packages that I do not want is automatically installed.

If you really want to do it minimal / bit by bit you might want to use:

sudo apt-get --no-install-recommends install 

It will only install the really necessary packages.

---

### Post by Ozitraveller on 2009-08-10
I've patched together some other threads I've seen and come up with this so far. I was thinking it might be nice to make this into a script/program that allowed users to select what they wanted to install or create a Ubuntu-Desktop-Minimal install via Synaptic. Just my 2 cents. :)

```

#! /bin/bash
# chmod +x ubuntu.sh

#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#     essentials of an Ubuntu Desktop.
#######################################################################

echo "[*] Update System"
sudo apt-get update && sudo apt-get upgrade

echo "[*] Installing Ubuntu Essentials"
sudo aptitude install gnome-core gdm 
sudo aptitude install gnome-utils gnome-system-tools x11-xserver-utils
sudo aptitude install human-theme tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver 

sudo apt-get install dontzap && sudo dontzap --disable

echo "[*] Installing Application Essentials"
# sudo apt-get install apport-gtk
# sudo apt-get install jockey-gtk
sudo apt-get install usplash
# sudo apt-get install update-manager 
# sudo apt-get install notify-osd 
# sudo apt-get install update-notifiers
sudo apt-get install network-manager-gnome
# sudo apt-get install fast-user-switch-applet

# sudo apt-get install system-config-samba
# sudo apt-get install system-config-printer-gnome
# sudo apt-get install startupmanager

sudo apt-get install synaptic firefox brasero
# sudo apt-get install conky msttcorefonts wine htop gdebi-core gparted
# sudo apt-get install sun-java6-jre sun-java6-plugin

# ---Network manager fix
# sudo nano /etc/network/interfaces
# Comment out the lines below "primary network interface"
# (This is the solution that match the standard 9.04 setup)

echo "[*] Removing Unecessary Services"
# sudo update-rc.d -f xserver-xorg-input-wacom remove
sudo update-rc.d -f bluetooth remove

sudo apt-get --purge remove bluez-utils bluez-gnome

echo "[*] Cleanup"
sudo apt-get install logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

echo "[*] Done - Time to Reboot"

```

---

### Post by WiseGuy1020 on 2009-08-31
This idea worked fine for me except for a few hiccups. If you add wpa-supplicant, make sure you add sudo apt-get install linux-headers-2.6.28-15-generic or whatever kernel you are using. 

I had just installed build-essentials and when I was compiling the ralink driver for my wireless card (works out-of-box but w/o 802.11n) it was not finding wpa_supplicant and thus could not connect to a WPA2 network.

D

---

### Post by lb02f962 on 2009-09-07
Hello everybody.

I just want to put my two cents in here :)

I was googeling around and found some very interesting "minimal-distribution" HOWTOs for ubuntu, xubuntu (and even opensuse) on distrowatch:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

With aid of this thread here and the links above I came to the following installation procedure (Please note that the following code is not recommended for productive systems):

**HOW I DID MINIMAL-UBUNTU-GNOME-DESKTOP**

° Install from ubuntu alternate CD a minimal command line system and boot it. (493M)
° Remove some "unnecessary" packages (please help me to improve this list in [this post here]("http://ubuntuforums.org/showthread.php?t=1259422")):
```

sudo apt-get remove aptitude tasksel apparmor rsync command-not-found-data ufw at bind9-host libbind9 memtest86+ w3m language-pack-en binutils-static bash-completition python update-manager-core update-motd openssh-client
#473M

```° Install minimal gnome system ready to install more apps
```

sudo apt-cdrom add
sudo apt-get install --no-install-recommends xserver-xorg gdm metacity nautilus gnome-panel gnome-session synaptic 
#gnome-session makes gdm able to start gnome.
#618M

```With this you have a really minimal gnome-desktop (look into the menu, it's empty) but you can install more apps easily with synaptic. 

Here some suggestions for further applicatons:
° Install network, sound & printer support
```

network-manager-gnome cups foomatic-db-engine alsa-utils 
#config printer with http://localhost:631 (yes you need a browser for that), config sound with "alsamixer"

```° Install utilities (from here you need internet, nautilus-cd-burner & alsamixergui are only available online, not on CD)
```

gnome-system-tools gnome-mount file-roller gnome-terminal gedit eog evince nautilus-cd-burner alsamixergui

```° Internet, Office & Multimedia
```

thunderbird pidgin firefox flashplugin-installer gufw openoffice.org-writer openoffice.org-calc openoffice.org-impress gimp xsane mplayer libdvdread4 
#sudo /usr/share/doc/libdvdread4/install-css.sh to enable encrypted DVD
#Install abiword & gnucalc instead of openoffice if you don't need impress.
#Install brasero + totem + gnome-media instead of nautilus-cd-burner + mplayer + alsamixergui. This is more gnomeish but takes a little more space

```With this I end up in a fully usable office/multimedia system using only 1.2G hard drive and understanding the package tree.

lorenz

p.s. Just quickly the same for xubuntu:
[B]
HOW I DID MINIMAL-UBUNTU-XFCE-DESKTOP[/B]

° Install from xubuntu alternate CD a minimal command line system and boot it. (493M)
° Remove some "unnecessary" packages (see above)
° Install minimal xfce system ready to install more apps
```

sudo apt-get install --no-install-recommends xserver-xorg gdm xfdesktop4 xfwm4 thunar synaptic
#568MB

```

---

### Post by khughitt on 2009-09-12
Thank for the guide! Worked great for me using 9.04 64-bit Mini from a USB stick. In case anyone is interested, i've attached the list of packages that are installed after the second step (Gnome, etc. is installed) is completed.

---

### Post by hariks0 on 2009-09-14
I would rather like to have it the other way around. That is, a script or how to for installation of the packages/applications/codecs [you know what i mean] that does not come with Ubuntu. Also shipping of alternate CDs instead of live ones for those who are already using the previous version of the present ubunu release will be of great help for upgradation.

---

### Post by udutronik on 2009-09-23
Great thread, this is very useful for someone like me who wants to install ubuntu on a netbook with maximal performances...

Upon achieving this install, there is one tool that I'd like to add : the GUI to add network printers. I know it can be done with web interface but I like the "auto-detect" feature of gui tool... 

The question is : What is the name for this package?

---

### Post by khughitt on 2009-09-23
> **udutronik said:**
> Upon achieving this install, there is one tool that I'd like to add : the GUI to add network printers. I know it can be done with web interface but I like the "auto-detect" feature of gui tool... 

The question is : What is the name for this package?

I believe the package you are looking for is:

system-config-printer-gnome

A few more packages which may be useful to install are:

language-selector gftp gnome-system-tools gconf-editor file-roller gdebi

---

### Post by Ozitraveller on 2009-09-23
9.10 (Karmic Koala)

I've updated my script because I wanted to install Karmic (9.10) alpha 5 a couple of weeks ago. All the major stuff just worked, however, I did not install any of :
human-theme tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver 

Hopefully this weekend I will have a chance to install the new splash ( and remove usplash)

sudo apt-get install ubuntu-xsplash-artwork
sudo apt-get install xsplash

---

### Post by yoshic on 2009-09-24
thanks a lot! it works flawlessly in my old gateway notebook, :P

---

### Post by zevans on 2009-10-08
> It seems that ubuntu package managers add any related package as a needed dependency instead of an option and this must limit how lite a ubuntu install can be even starting from a minimal install and adding just what you want.

Yes, that does seem to happen a lot. Two examples I have come across recently are: 

Akonadi (the KDE PIM stuff) forcing use of mysql when it supports sqllite perfectly well in the version Karmic is built from.

Digikam dragging in all the Marble libraries. Geotagging should be an option because very few people use it, and frankly Marble may be pretty but it's not the most efficient interface.

Grrr. Thanks for sharing. :-)

---

### Post by moiecoute on 2009-10-21
> **Ozitraveller said:**
> 9.10 (Karmic Koala)

I've updated my script because I wanted to install Karmic (9.10) alpha 5 a couple of weeks ago. All the major stuff just worked, however, I did not install any of :
human-theme tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver 

Hopefully this weekend I will have a chance to install the new splash ( and remove usplash)

sudo apt-get install ubuntu-xsplash-artwork
sudo apt-get install xsplash

Are you guys planning to do an upgrade or complete re-install with Karmic minimal ?

I am in the same boat running a minimal install and I don't want the upgrade manager to install all the bloat (things I don't want) on upgrade.

Thanks

---

### Post by k3lt01 on 2009-10-22
> **moiecoute said:**
> Are you guys planning to do an upgrade or complete re-install with Karmic minimal ?

I am in the same boat running a minimal install and I don't want the upgrade manager to install all the bloat (things I don't want) on upgrade.

ThanksI think it should just update the programs you already have installed, so it wont add anything unless the newer versions have new dependencies.

---

### Post by Ozitraveller on 2009-10-24
I'm still going to do a clean install as ext4 is now the default. And I'm not sure whether all the package names are still the same, most should be, but I need to check. For instance has grub2 replaced grub...

---

### Post by k3lt01 on 2009-10-24
I updated to Karmic yesterday and it replaced older versions of each program and deleted programs that are not supported by Canonical anymore (in Karmic at least) such as Grub. If you have 3rd party repos you will have to put them back in your list like previous versions have required it. Apart from Empathy doing dumb things it is plain sailing.

---

### Post by mxWorld on 2009-10-28
TheShiv, thanks a lot..
i looked for this "how to"

---

### Post by mfarley on 2009-10-29
Anyone know when the new minimal iso will show up here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

??  I'm itching to install it!

---

### Post by Ualpa on 2009-10-29
It's not there... but it's here:

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)

;)

> **mfarley said:**
> Anyone know when the new minimal iso will show up here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

??  I'm itching to install it!

---

### Post by mfarley on 2009-10-29
> **Ualpa said:**
> It's not there... but it's here:

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)

;)

That iso was created 2 weeks ago -- it's not the final version.  Or is it good enough since it downloads fresh packages?

---

### Post by unicycletim on 2009-11-04
> **mfarley said:**
> Anyone know when the new minimal iso will show up here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

??  I'm itching to install it!

it's up there now

---

### Post by Ozitraveller on 2009-11-04
I tried the new mini.iso without any issues.

---

### Post by corsakh on 2009-11-08
He guys for those who have used Arch, how does this minimal install Ubuntu compare to that of Arch Linux in terms of speed and efficiency?

---

### Post by MathiasIce on 2009-11-10
Here's what I have: The Mini Iso burned on a CD, the Ubuntu Studio Alternate ISO burned on a DVD, 2 DVD drives in my computer, and no internet access when I try to do an install with the mini cd. Everything I need is on the Ubuntu Studio DVD. Is there some way to tell the Mini install process to access the Ubuntu Studio DVD to get the RT Kernel and packages/programs I want off of it? I'm wanting to do a minimal install of Ubuntu Studio.

Thanks.

---

### Post by vikjon0 on 2009-11-10
> **MathiasIce said:**
> Here's what I have: The Mini Iso burned on a CD, the Ubuntu Studio Alternate ISO burned on a DVD, 2 DVD drives in my computer, and no internet access when I try to do an install with the mini cd. Everything I need is on the Ubuntu Studio DVD. Is there some way to tell the Mini install process to access the Ubuntu Studio DVD to get the RT Kernel and packages/programs I want off of it? I'm wanting to do a minimal install of Ubuntu Studio.

Thanks.

It is possible to refer to a CD in the source list. In one installer it was also possible to scan a number of discs as part of the installation process. Dont remember what distro...if it was debian maybe you can set that up. Would be nice.

---

### Post by rabidbadger on 2009-11-10
> **vikjon0 said:**
> It is possible to refer to a CD in the source list.

```
$ man apt-cdrom
```

---

### Post by cheshire on 2009-11-13
I have a pentium 3 laptop I would like to try this out on to optimize for speed.  However, I am totally new to linux and do not know what you mean by writing a script.  Would someone mind giving explaining that process or pointing me in the right direction to find that information?  Thanks.

---

### Post by Ventil on 2009-11-15
Hi all
I installed minimal ubuntu 9.10. Then installed most software u guys suggested. But I have 1 problem now. 

When I put SD-card in to the notebook, plugin camera, mobile phone, put CD in, nothing happens. I put CD in, click on CD-ROM in nautilus and nothing happens. I think I need to install something more but don't know what it is. Everything worked fine in 9.04 minimal ubuntu for me. But not in 9.10. Can someone help me please? 
Thank you

---

### Post by Ventil on 2009-11-16
> **Ventil said:**
> Hi all
I installed minimal ubuntu 9.10. Then installed most software u guys suggested. But I have 1 problem now. 

When I put SD-card in to the notebook, plugin camera, mobile phone, put CD in, nothing happens. I put CD in, click on CD-ROM in nautilus and nothing happens. I think I need to install something more but don't know what it is. Everything worked fine in 9.04 minimal ubuntu for me. But not in 9.10. Can someone help me please? 
Thank you

 Found my solution. I just needed to install "gvfs-backends". Everything works now.

---

### Post by lloydlloyd on 2009-11-19
Just thought i'd add my two cents
I use the server cd, set up lamp usually, then add the following

> sudo apt-get install acpi-support alsamixergui alsa-utils app-install-data-commercial cups eog evince file-roller firefox flashplugin-installer foomatic-db-engine gcalctool gdebi gdm gdm-guest-session gedit gimp gnome-app-install gnome-applets gnome-core gnome-menus gnome-mount gnome-panel gnome-power-manager gnome-screensaver  gnome-session gnome-system-tools gnome-terminal gnome-themes gnome-themes-ubuntu gnome-utils gnome-volume-manager gthumb gucharmap gufw human-theme jockey-gtk libdvdread4 libgnomevfs2-extra menu metacity mplayer nautilus nautilus-cd-burner nautilus-sendto nautilus-share network-manager-gnome notify-osd openoffice.org-calc openoffice.org-writer pidgin smbfs synaptic system-config-printer-gnome tangerine-icon-theme thunderbird tsclient ubuntu-artwork ubuntu-restricted-extras ubuntu-xsplash-artwork update-manager update-notifier usplash usplash-theme-ubuntu vinagre vino x11-xserver-utils xcursor-themes xorg xsane xscreensaver xserver-xorg xsplash 

any advice/tips to tidy this up further would be appreciated.

---

### Post by ron999 on 2009-11-21
Hi
I've done the minimal xfce install using the Psychocats website, it's OK.

Like this:-
```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
sudo /etc/init.d/gdm start
```


Now I'd like to try with Gnome using the script from this thread.

But excuse me for asking, how do you run a script after installing from the minimal CD. From what I remember all that I had was a 'dos' prompt. 
How do I run a script from there?

(I suppose that I could install a terminal then copy and paste the 'script' from a floppy disc or whatever, but this seems dumb.)
:confused:

---

### Post by ron999 on 2009-11-22
Bump
Can somebody answer please.
How do I run a script after I've installed the minimal CD?
:confused:

---

### Post by Ozitraveller on 2009-11-22
Hi

Try this:

[http://mattiasgeniar.be/2008/10/29/how-to-mount-a-usb-hard-disk-through-command-line-linux/](http://mattiasgeniar.be/2008/10/29/how-to-mount-a-usb-hard-disk-through-command-line-linux/)

# I usually copy the script from my usb to my home folder 
cp /mnt/usb-storage/script-name.sh .

# make it executable
chmod +x script-name.sh

# Then execute it
sudo ./script-name.sh

---

### Post by ron999 on 2009-11-23
OK, thanks for that Ozitraveller.
I understand now.
:D

---

### Post by ron999 on 2009-11-24
> **lloydlloyd said:**
> Just thought i'd add my two cents
I use the server cd, set up lamp usually, then add the following



any advice/tips to tidy this up further would be appreciated.
**eog** doesn't need to be installed because it's already included with gnome-core.
Likewise gedit, nautilus, gnome-panel, gnome-menus, gnome-session, gnome-applets and gnome-terminal.

Check it out here:-[http://packages.ubuntu.com/karmic/gnome-core]("http://packages.ubuntu.com/karmic/gnome-core")

---

### Post by lloydlloyd on 2009-11-25
> **ron999 said:**
> **eog** doesn't need to be installed because it's already included with gnome-core.
Likewise gedit, nautilus, gnome-panel, gnome-menus, gnome-session, gnome-applets and gnome-terminal.

Check it out here:-[http://packages.ubuntu.com/karmic/gnome-core]("http://packages.ubuntu.com/karmic/gnome-core")

sweet. thanks for that

---

### Post by bapoumba on 2009-11-28
Ping [TheShiv]("http://ubuntuforums.org/member.php?u=691298") and the members who have taken over this thread: [http://ubuntuforums.org/showpost.php?p=8401398&postcount=68](http://ubuntuforums.org/showpost.php?p=8401398&postcount=68)

Cheers :)

---

### Post by Bruce M. on 2009-11-28
Partial quote:

> **tomstrummer said:**
> not to mention there are usually user conig files and other cruft left behind after you remove everything.

That's the key right there, even doing the GUI thing with Synaptic and choosing "Mark for complete removal" doesn't take all the dependencies etc out, it removes the .DEB file from the cache and like tomstrummer said, the config files are still there as well.

KUDOS to the OP.

Have a nice day
Bruce

---

### Post by brandon88tube on 2009-11-28
Quick question that I could use a quick reply to. How would I go about installing a command-line system from the normal live cd? Is there an option I can type in under the boot options to achieve this? I don't feel like wasting time downloading another iso and then wasting another disc if possible.

---

### Post by ron999 on 2009-11-28
@brandon88tube
Hi
I don't know the answer to your question.
But the file size of the minimal iso is only 12MB - It doesn't take long to download.
I used a CD-RW disc.
:cool:

---

### Post by brandon88tube on 2009-11-28
Lol, I actually don't seem to have any CD-RW's on hand that I can think of. Also, I might have an issue with the mini.iso as I have to use wireless to connect online and I'm not sure if it installs that with the minimal version.


EDIT: Actually  I found some CD-RW's that have some stuff I'll just erase. Going to give it a shot and hope I can get my wireless working with it.

---

### Post by brandon88tube on 2009-11-28
So far not looking good. The mini.iso didn't work as I suspected due to the fact it couldn't detect my usb wireless.

---

### Post by X1R1 on 2009-11-29
Very nice, a time saver if you ask me :D

good work

---

### Post by meindian523 on 2009-11-29
To all the guys who achieved a minimal KDE install:

Please post instructions!! Specially KDE4.3, if possible.

---

### Post by MooPi on 2009-11-30
Your idea prompted me to try a minimal Gnome install. In the recent past I've been using the minimal install to set up OpenBox systems and a small collection of apps to fill in the desktop. I'm pleasantly pleased with the Gnome install. It's not my cup of tea but it's much easier for Linux noobs to grasp a Gnome desktop than OpenBox. The minimal Gnome install used less resources than I expected and works fine on older equipment and netbooks. Thanks for your suggestion. Besides the gnome-core and gdm ,gnome-volume-manger I installed ,htop, xarchiver, scrot, evince, synaptic, Transmission bittorent, xlockmore, Brasero, (themes to taste), vorbis-tools, cplay cdparanioa, easytag, xine & plugin, Abiword. This rounded out a small lean install that does not tax low resource systems.

---

### Post by meindian523 on 2009-11-30
Thanks to TheShiv, I now have a way to introduce Ubuntu to 128 megs and less RAM systems without feeling guilty of leaving my acquaintances with a less than ideal set of applications. I know Xubuntu etc exist to address these, but I wouldn't give unto others what I wouldn't accept myself. :)

---

### Post by k3lt01 on 2009-11-30
> **meindian523 said:**
> Thanks to TheShiv, I now have a way to introduce Ubuntu to 128 megs and less RAM systems without feeling guilty of leaving my acquaintances with a less than ideal set of applications. I know Xubuntu etc exist to address these, but I wouldn't give unto others what I wouldn't accept myself. :)
How very profound.

---

### Post by Ozitraveller on 2009-11-30
I decided to split my script, it just gives better control to make sure the desktop is working, before I start adding the apps.

EDIT: I decided to add some more info so it's all in one place.

How To Mount A USB Hard Disk Through Command Line (Linux)
[http://mattiasgeniar.be/2008/10/29/how-to-mount-a-usb-hard-disk-through-command-line-linux/](http://mattiasgeniar.be/2008/10/29/how-to-mount-a-usb-hard-disk-through-command-line-linux/)

Here&#8217;s how to mount a USB hard disk drive (ie; external storage) on a Linux server, through the command line.

First, attach the hard disk and turn it on. Then look in /var/log/messages for a message similar to the ones shown in bold. This will tell you the device-location of your recently attached hdd.
```

server#: tail -f /var/log/messages -n 25

&#8211; MARK &#8211;
kernel: usb 4-1: new high speed USB device using &#8230;
kernel: usb 4-1: configuration #1 chosen from 1 choice
kernel: scsi9 : SCSI emulation for USB Mass Storage devices
kernel: SCSI device sde: 586072368 512-byte hdwr sectors (xx MB)
kernel: sde: Write Protect is off
kernel: SCSI device sde: 586072368 512-byte hdwr sectors (xx MB)
kernel: sde: Write Protect is off
kernel:  sde: sde1
kernel: sd 9:0:0:0: Attached scsi disk sde
&#8211; MARK &#8211;


```

The external storage can be found in /dev/sde1, as shown in the message-log (the last lines).
Make a new directory, and mount the device to that point.
```

mkdir /mnt/usb-storage
mount /dev/sde1 /mnt/usb-storage

```

And now you can navigate to /mnt/usb-storage and find your content of the external storage.


mini-core.sh
```

#! /bin/bash

sudo apt-get update && sudo apt-get upgrade
# sudo aptitude safe-upgrade && sudo aptitude full-upgrade

# echo "[*] Installing Ubuntu Essentials"
sudo apt-get -y install gnome-core gdm xinit gnome-utils gnome-system-tools x11-xserver-utils

sudo apt-get -y install xsplash ubuntu-xsplash-artwork

sudo apt-get -y install human-theme
sudo apt-get -y install humanity-icon-theme
sudo apt-get -y install gnome-themes-ubuntu
sudo apt-get -y install ubuntu-artwork
sudo apt-get -y install xcursor-themes
sudo apt-get -y install gnome-screensaver

sudo apt-get -y install network-manager-gnome
sudo apt-get -y install network-manager-pptp pptp-linux tsclient
sudo apt-get -y install system-config-samba
sudo apt-get -y install system-config-printer-gnome
sudo apt-get -y install startupmanager
sudo apt-get -y install gnome-volume-manager

echo "[*] Cleanup"
sudo apt-get install -y logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

echo "[*] Enable firewall"
sudo ufw enable

echo "[*] Done - Time to Reboot"
sudo reboot

```


mini-apps.sh
```

#! /bin/bash

echo "[*] Installing Application Essentials"
# sudo apt-get install gufw
# sudo apt-get install ufw
sudo apt-get install gdebi
sudo apt-get install synaptic
sudo apt-get install gparted
sudo apt-get install firefox
sudo apt-get install brasero
sudo apt-get install conky
sudo apt-get install msttcorefonts


```

Make it executable
```

chmod +x mini-core.sh

```

Then execute it
```

sudo ./mini-core.sh

```

And then when I have a running desktop, I run the second script.

---

### Post by bapoumba on 2009-12-01
> **brandon88tube said:**
> <snip>
Completely OT for one post: your avatar fooled me, brandon88tube!
I was thinking: who's this member with burnt beans I am not aware of, and why are the beans not located as usual :lol:

---

### Post by DannoXYZ on 2009-12-06
Thanks for the great guide & script! I just tried to install the latest 9.10 Netbook Remix on my 701-2G and it wouldn't work. I tested the ISO in a VM and the installed package takes up 2.5gb! Is there a way to modify your script to take an Ubuntu-minimal install up to the Netbook Remix GUI with a minimum amount of disk-space? I don't need any games, bluetooth, gcc, Evolution, etc. Just basic Netbook Remix with Firefox and OpenOffice word-processor.

Can I do the minimal-install and apt-get install the following?

1. go-home-applet 
2. window-picker-applet 
3. notification-area-applet 
4. mixer-applet 
5. clock

I take it the underlying dependencies would automatically be installed as well?

Thx.

---

### Post by Ozitraveller on 2009-12-08
Hi DannoXYZ

I sent you a PM yesterday suggesting CrunchBang as an alternative, as friend installed it on his 701 and it has taken about 1.7gb of space.

I remembered I'd seen this before:
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

#these line into /etc/apt/sources.list
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) karmic main
#then do:
#$ sudo aptitude install go-home-applet human-netbook-theme maximus ume-launcher window-picker-applet
#$ sudo /etc/init.d/gdm restart


> **DannoXYZ said:**
> Thanks for the great guide & script! I just tried to install the latest 9.10 Netbook Remix on my 701-2G and it wouldn't work. I tested the ISO in a VM and the installed package takes up 2.5gb! Is there a way to modify your script to take an Ubuntu-minimal install up to the Netbook Remix GUI with a minimum amount of disk-space? I don't need any games, bluetooth, gcc, Evolution, etc. Just basic Netbook Remix with Firefox and OpenOffice word-processor.

Can I do the minimal-install and apt-get install the following?

1. go-home-applet 
2. window-picker-applet 
3. notification-area-applet 
4. mixer-applet 
5. clock

I take it the underlying dependencies would automatically be installed as well?

Thx.

---

### Post by Ozitraveller on 2009-12-08
Somebody else with the same idea.
[http://linuxdroid.blogspot.com/2009/12/how-to-install-lightweight-ubuntu.html](http://linuxdroid.blogspot.com/2009/12/how-to-install-lightweight-ubuntu.html)

---

### Post by lb02f962 on 2009-12-17
> **bbourgoine said:**
> Seems to me the "post what to remove from a 'full install'" folks could be well-served by a simple listing of what packages are installed.  That could then be compared to a list of what's installed on their machines, and the difference would be the list of what packages to remove.

Maybe just the output of 'dpkg --get-selections' would be enough?

Your post is already quite old but I did something like this (with ubuntu 9.10):
```

lori@ubuntu-normal-desktop# dpkg --get-selections > full_gnome.txt
lori@ubuntu-minimal-cli# dpkg --get-selections > full_cli.txt
lori@ubuntu-extreme-minimal-cli# dpkg --get-selections > mini_cli.txt

```Have a look at the attached files to see what are the overlaps and the differences. A simple
```
awk '{print $1}' *.txt | sort | uniq [-u|-d] 
```can be really helpful.

Please also have a look at this thread [http://ubuntuforums.org/showthread.php?t=1259422](http://ubuntuforums.org/showthread.php?t=1259422)

---

### Post by aklo on 2009-12-17
Very usefull thank you. Just what a lot of us needed. Personally, i don't use most of the software that ubuntu 9.1 install by default especially the media players...heck why don't they include VLC it is like the best out there.

I do suggest the developer of ubuntu have this feature for every release.
Bare minimum and normal edition.


:popcorn:

---

### Post by andath10 on 2009-12-17
Correct me if im wrong but i think vlc isnt included because it already includes some codecs that ubuntu cant legally included them by default (same concept as with ubuntu restricted essentials i think). Had seen a brainstorm asking the same thing when i was searching why also:P

As for the minimum instal myself install minimal cd first and after this just

xorg gdm gnome-core synaptic software-center. 

Found this method better than default install because:

1) you know exactly what you have in your machine
2) always install the most recent version of all packages instead of having to update after install
3) i personally configure every software piece i install one by one without having a massive amount of software to bring to my needs at once (mostly because in the second example i always forget something)
4)doing faster disk backups with clonezilla in case something i do goes wrong (since I am a new linux user)
5) and most important imo... learning the system and how it works a little better. Having installed linux before the default way, i didnt know what's was going on underneath (an advantage for ppl who just want things to work, but not for me)

and just a little question.. what i lose in general by installing gnome-core and xorg  packages with -no-recommends on them?

---

### Post by tenach on 2009-12-17
Sounds like I'll need to give this a try!  I always end up installing Ubuntu, removing all the applications I can/don't use, updating, then configuring.

---

### Post by t_tovenaar on 2009-12-24
> **abhiroopb said:**
> Thanks for the clarification.

I would like to try this out, but I'm a little worried there are applications that I am using right now that I am unaware off. Something like network manager or volume manager, etc. Which is very important but its not obvious that they are running.

In general I find that Ubuntu does not come with that many useless applications.

Without having read the entire topic I agree with abhiroopb. To me it seems easier to remove unwanted software from a basic install as I believe one would think twice before removing apps like network manager or volume manager, etc. 

For now I'll just continue reading this topic. ;)

---

### Post by dzon65 on 2009-12-25
As for "old" ,low spec systems this is a good configuration.By Glenn nl:
xorg
gdm
xfce4
gdebi
epiphany-browser
thunderbird
xfce4-terminal
synaptic
gpaint
abiword
gnumeric
xubuntu-default-settings
xubuntu-restricted-extras
xfce4-taskmanager
xfce4-screenshooter
dmz-cursor-theme
file-roller
pidgin
mousepad
ristretto
xfburn
xfce4-notifyd


xfmedia






It uses about 60mb ram.
And your configuring goes on of course.

---

### Post by johnnyhostile on 2009-12-26
Hey all,

I made my own script for setting up a minimal - it's a rough draft but should still work:

[http://instigatorband.com/ubuntu_minimal.sh](http://instigatorband.com/ubuntu_minimal.sh)

Feel free to edit it to your liking!

EDIT: just finished running this on a VM, 857 packages... yikes! Hope you have a good conenction! You may want to remove some of the packages I have marked to install also, there may be some stuff the average or minimalist user doesn't want.

PEACE!

---

### Post by johnnyhostile on 2009-12-26
> **johnnyhostile said:**
> Hey all,

I made my own script for setting up a minimal - it's a rough draft but should still work:

[http://instigatorband.com/ubuntu_minimal.sh](http://instigatorband.com/ubuntu_minimal.sh)

Feel free to edit it to your liking!

EDIT: just finished running this on a VM, 857 packages... yikes! Hope you have a good conenction! You may want to remove some of the packages I have marked to install also, there may be some stuff the average or minimalist user doesn't want.

PEACE!

oops, needs more work yet. I'll be updating it later.

---

### Post by johnnyhostile on 2009-12-26
> **johnnyhostile said:**
> oops, needs more work yet. I'll be updating it later.

OK -- all done. I had some custom xorg.conf settings in there that messed up X.

---

### Post by ron999 on 2009-12-26
............

---

### Post by aerodown on 2010-01-01
can anyone tell me how to get minimal ubuntu without games, office suite. im trying to install ubuntu under vmware workstation and i already install ubuntu desktop 9.10..but most of them something that i dont use. so im trying to install from minimal cd. 
 
ive been googling and read forum but most of them is for an old build of ubuntu i think?
 
i just need ubuntu 9.10 default login, default desktop. what package did i need to achieve this? thanks.

---

### Post by Gramps on 2010-01-01
[http://ubuntuforums.org/showthread.php?t=1155961&page=1](http://ubuntuforums.org/showthread.php?t=1155961&page=1)

---

### Post by k3lt01 on 2010-01-01
> **gramps said:**
> [http://ubuntuforums.org/showthread.php?t=1155961&page=1](http://ubuntuforums.org/showthread.php?t=1155961&page=1)lol

---

### Post by tenach on 2010-01-01
Hmm, I kind of wish I had known a bit more when I was installing Ubuntu on older machines.  Going this route would have been much nicer and cleaner than installing Ubuntu and removing everything I didn't want.

---

### Post by Ozitraveller on 2010-01-11
I thought I'd add this link, as it's an interesting read and heading in a similar direction:

Masonux: LXDE-based Ubuntu spinoff that sticks to its roots
[http://ubuntuforums.org/showthread.php?t=1248322](http://ubuntuforums.org/showthread.php?t=1248322)

---

### Post by HellionDarkLord on 2010-01-12
I decided to try this with the Karmic 64bit minimal cd.

The only problem I have is that fast-user-switcher doesn't work and asks to be deleted.  I can't find fast-user-switcher thing in synaptic.

This is working so beautifully now I can hardly believe it.  I bought a crappy laptop not knowing anything about laptops and hated it until now.  It runs this version of Ubuntu that I built from minimalcd like a dream come true!  I installed and set up prelink and now it's totally amazing and faster than my desktop which is an MSI AM2+ Mobo with 8 gigs ram and a phenom x3 proc with an nvidia 260 GTX ocv4. (totally screaming fast)

I think I'll do this with my desktop too and blow away the youtubers with their "fast boot times" stuff lol!

Thanks lots!

HD

---

### Post by k3lt01 on 2010-01-12
> **HellionDarkLord said:**
> The only problem I have is that fast-user-switcher doesn't work and asks to be deleted.  I can't find fast-user-switcher thing in synaptic.Thats because you install it via the Panel itself. Right click on the Panel, click Add To Panel and scroll down until you find it. Also in later versions, maybe Karmic as well, it is called "Indicator Applet Session" not Fast User Switch Applet.

---

### Post by HellionDarkLord on 2010-01-13
> Thats because you install it via the Panel itself. Right click on the Panel, click Add To Panel and scroll down until you find it. Also in later versions, maybe Karmic as well, it is called "Indicator Applet Session" not Fast User Switch Applet.]

Wow thanks for that!! I wondered what the Indicator Applet  was in the startup applications. Now I know! thanks

So I should tell it to delete from config then when it asks right?

---

### Post by hwttdz on 2010-01-20
Yup, you can delete fast user switch applet, and install indicator-applet-session and then add that to the panel.  

Here's mine:
#!/bin/bash
#install everything I want
sudo apt-get install abiword build-essential compiz compizconfig-settings-manager curl  epiphany-browser epiphany-extensions evince file-roller firefox gcalctool gconf-editor gdebi gdm gedit glchess gnome-app-install gnome-core gnome-screensaver gnome-themes-ubuntu gnome-utils gnumeric human-theme indicator-applet-session jockey-gtk nautilus-open-terminal nautilus-wallpaper network-manager-gnome openssh-server pidgin powermanagement-interface powertop rhythmbox simple-ccsm sshfs tangerine-icon-theme thunderbird totem transmission ubuntu-artwork vlc x11-utils x11-xserver-utils 

#fetch and install flash for 64 bit
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz) -O ~/flash_64.tar.gz
tar -zxf flash_64.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

---

### Post by stars on 2010-01-20
how is the ram usage on the minimal gnome installs? after a standard install and a little disabling of services and unneeded things i'm using 92mb once booted to this desktop.

---

### Post by Ozitraveller on 2010-01-26
Hi

Does anyone know what the audio layers are and in what order are they and what I need to make vlc play music? I'm looking for an explanation here if possible.

sound card, card drivers, ......., alsamixer?, pulseaudio?, vlc

Cheers

---

### Post by PatrickMoore on 2010-01-31
one thing ive noticed with 9.10 is that with a minimal install gdebi installer does not work well has anyone noticed this as well?

---

### Post by onamattuphere on 2010-02-13
To the OP and contributers: Thanks for these ideas.

Is it possible to do a minimal install which would run alongside one's current Ubuntu setup and then choose which one to boot up in GRUB?

---

### Post by vikjon0 on 2010-03-15
I am running without gdm, just starting with startx. Now with karmic I am getting permissions problems. When I plugin a usb drive I get "not authorized". If I install gdm it works fine. Anyone knows how to fix this?

---

### Post by johnraff on 2010-03-15
> **vikjon0 said:**
> I am running without gdm, just starting with startx. Now with karmic I am getting permissions problems. When I plugin a usb drive I get "not authorized". If I install gdm it works fine. Anyone knows how to fix this?
You could try changing the line in .xinitrc that starts your desktop environment to:
exec ck-launch-session *yourstartupcommand*
ie precede whatever command you were using with ck-launch-session .
No guarantees though... :)

---

### Post by vikjon0 on 2010-03-16
> You could try changing the line in .xinitrc that starts your desktop environment to:
exec ck-launch-session yourstartupcommand
ie precede whatever command you were using with ck-launch-session .

Can you tell me more about this? I found ck-launch-session when I googled for a solution and I tried typing in command line
ck-launch-session startx

Did not work.

Do I have to manually tweak the policykit as well? I have tried that but not in combination perhaps.

---

### Post by johnraff on 2010-03-17
> **vikjon0 said:**
> Can you tell me more about this? I found ck-launch-session when I googled for a solution and I tried typing in command line
ck-launch-session startx

Did not work.

Do I have to manually tweak the policykit as well? I have tried that but not in combination perhaps.
Do you have an .xinitrc file in your home folder? If not, startx is presumably running your default window manager directly. What window manager or desktop environment are you using? If, for example, you are running openbox then try creating an .xinitrc file in your home folder with this code:```
#!/bin/bash
exec ck-launch-session openbox

```Change the openbox command to whatever you're using. Lxde and xfce use startup scripts so the command would be startlxde or startxfce4.

---

### Post by vikjon0 on 2010-03-18
> Do you have an .xinitrc file in your home folder? If not, startx is presumably running your default window manager directly. What window manager or desktop environment are you using? If, for example, you are running openbox then try creating an .xinitrc file in your home folder with this code:
Code:
Ok, I see you point. I need to apply it directly not on startx. I need to understand the startx process better. All I know is that the latest installed wm will start with startx...

I will look into that but I actually fixed my urgent problem yesterday with:
> 
sudo apt-get install policykit-1 devicekit-power
sudo nano /var/lib/polkit-1/localauthority/50-local.d/custom-actions.pkla
[Actions for xbmc user]
Identity=unix-user:xbmc
Action=org.freedesktop.devicekit.disks.*;org.freed esktop.devicekit.power.*;org.freedesktop.consoleki t.system.*;org.freedesktop.hal.storage.mount-removable;org.freedesktop.hal.device.volume
ResultActive=yes
ResultAny=auth_admin
ResultInactive=yes 

---

### Post by Morganvd on 2010-03-24
I am going to try this this weekend, I always wanted to have ubuntu but with my own person selection of applications like Google Chrome. I believe adding the apt repo should do the trick. Thanks a mil for the tut as I believe I have just fallen in love with my ubuntu again

---

### Post by AlexanderDGreat on 2010-03-25
First here's my background. Upgrading from 8.10 to Jaunty, bad, errors, failed, forced to do fresh install. 2nd, from 9.04 to 9.10, upgrade via CD from desktop -- bad, errors, headaches, conflicts, streams of errors and unknown cryptic messages filled my screen.

Now if I do this on Karmic now, and I upgrade to Lucid Lynx -- will my history with Ubuntu upgrades repeat? Or should I do this now on my laptop and other pc's, for it is beneficial because of the low incidence of installations?

Bottomline: Can I do this and when I upgrade to LL, it's going to be smooth? TAL (thanks a lot).

---

### Post by Ozitraveller on 2010-03-25
If you are talking about a full install of Ubuntu then maybe you have the forum. This thread is discussing the "Ubuntu-Desktop-Minimal".

:)

---

### Post by XFX Distorted on 2010-03-29
my minimal desktop is
```
base system with Kernel 2.6.31.20 i386
apt-get --no-install-recommends install ubuntu-desktop
```Its the bare minimum i can get just gnome/x11
nothing else, no apps, no games just a empty workspace

---

### Post by rykel on 2010-04-01
Hi,

How about the other way round... having a bloated Ubuntu Karmic install and wanting to trim it down to a mere 2GB install?

---

### Post by vikjon0 on 2010-04-01
> How about the other way round... having a bloated Ubuntu Karmic install and wanting to trim it down to a mere 2GB install?

What is the question? Either you start over (recommended) or you remove the packages you dont want.
sudo apt-get purge <package>

If you are asking what packages you can remove with out loosing anything you want to keep, that is pretty hard for us to tell as you can imaging.

sudo apt-get purge gnome-core will clean it up pretty good ;)

---

### Post by Ozitraveller on 2010-04-10
Here's a basic Lucid script:

> 
#! /bin/bash

sudo apt-get update && sudo apt-get upgrade

# echo "[*] Installing Ubuntu Essentials"
sudo apt-get install gnome-core gdm gnome-utils gnome-system-tools x11-xserver-utils

sudo apt-get install plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label gnome-themes-selected
sudo apt-get install gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver
sudo apt-get install network-manager-gnome nm-applet startupmanager

sudo apt-get install firefox synaptic

echo "[*] Cleanup"
sudo apt-get install logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

echo "[*] Enable firewall"
sudo ufw enable
sudo ufw status

echo "[*] Done - Time to Reboot"
sudo reboot


---

### Post by gfendle on 2010-04-12
> **Ozitraveller said:**
> Here's a basic Lucid script:

Excellent starting point, thanks very much. Just what I was looking for since so much has changed since 9.04.

If someone is doing a clean install from, say, the alternate CD, wouldn't it be prudent to do a dist-upgrade, too?

---

### Post by Ozitraveller on 2010-04-12
Clean install from 9.04 or the current Lucid beta 2?

---

### Post by gfendle on 2010-04-13
> **Ozitraveller said:**
> Clean install from 9.04 or the current Lucid beta 2?
Sorry, should have said, clean from Lucid Alternate CD beta 2 rather than the minimal.

As an aside, I did some tests on a spare computer the other day. Clean installed 9.04, per the original start of this topic, upgraded to 9.10, then upgraded to 10.04. It didn't go that well. It was the transition from 9.04 to 9.10 that was the problem and broke my fairly basic but customised partitioning. 

I've got a clean install of Lucid up now and starting to build it up from scratch.

---

### Post by mörgæs on 2010-04-13
Does anyone have experience with a minimal install, where the desktop environment is LXDE in stead of Gnome? 

Lubuntu (with LXDE) appears to be one of the lightest and fastest of the Buntus when talking of a full install, so I figured that a minimal install with LXDE might be worth trying.

---

### Post by Ozitraveller on 2010-04-13
I'd probably wait a bit, 'coz pcmanfm2 (file manager) is still under development and not everything is in the official repos yet.

---

### Post by Ozitraveller on 2010-04-13
Try this

> 
#! /bin/bash

sudo apt-get update && sudo apt-get upgrade

# echo "[*] Installing Lubuntu Essentials"
sudo apt-get install lxde lxde-icon-theme plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label 

echo "[*] Done - Time to Reboot"
sudo reboot


---

### Post by mörgæs on 2010-04-14
Thanks, that looks easy.

---

### Post by emarkay on 2010-04-27
> **Ozitraveller said:**
> Here's a basic Lucid script:


A shame you can't get by without Plymouth now anymore...  :)

---

### Post by Tom_Light on 2010-04-27
Hey there! 

First of all, big thanks for figuring this stuff out. I'm a recent Linux convert (left Apple b/c started to really hate all the big-brother'ing they are doing these days, and how they seem to care more about putting out near-useless kitschy products than make useful operating systems...but that's a rant for another day) and the thing's I've found on this forum really have helped me out.
[COLOR=black]
Anyway, I have a couple questions about [Ozitraveller]("http://ubuntuforums.org/member.php?u=1552")'s script in[/COLOR] post #203 for 10.04:

1) I plan on making my own backgrounds, icon sets, and plymouth booting background. The only thing I really see myself wanting are the Radiance and Ambiance themes. Is there a way I could just get these two themes? (I understand Gnome-core probably comes with a default theme -- that's fine.)

 >>> Or would it be easier, especially in regards to the booting background, to just install the ubuntu boot background and later go in and modify that background manually, so that I don't have to mess around with directing plymouth to the correct image file?

2) I'm going to be installing to a netbook. Do I still need the 9.04 recommended apps (from wayyy earlier in the thread) or have these changed? The ones from before were:

laptop-mode-tools ubuntu-laptop-mode wpasuppliment apmd

Should anything be added/replaced?

3) A big draw for choosing Ubuntu over other distros for me was the new super fast boottime they've been showing off for 10.04. Is that going to be there or is there something else I need to install?

4) On the script in post#203, are there any steps where I should be using --no-install-recommends ? 

5) Is the new social networking crap included with gnome-core (or somewhere else), or is that extra stuff forgotten with this type of install ('Cause I don't want it).

Thanks for the help!

---

### Post by Paqman on 2010-04-30
> **Ozitraveller said:**
> Here's a basic Lucid script:

There's a much more powerful and flexible one in my sig ;)

---

### Post by Chesamo on 2010-04-30
[Shameless plug.](http://minimal-desktop.blogspot.com/p/guide.html) (Lucid guide will be up shortly; the current version of the script is on the [Launchpad](https://launchpad.net/ubuntu-desktop-minimal).)

---

### Post by simonxs on 2010-04-30
> **Chesamo said:**
> [Shameless plug.](http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/) (Lucid guide will be up shortly; the current version of the script is on the [Launchpad](https://launchpad.net/ubuntu-desktop-minimal).)



niiiiice. I will try it out in about a week when the dust has settled. I have a laptop, does the script install laptop utilities?
or do I have to install them manually?

---

### Post by Chesamo on 2010-05-01
> **simonxs said:**
> niiiiice. I will try it out in about a week when the dust has settled. I have a laptop, does the script install laptop utilities?
or do I have to install them manually?
Define "Laptop utilities".

(Also, may I ask that questions related to my script go in that thread? I don't check this one regularly.)

---

### Post by James79 on 2010-05-04
For my fellow Ubuntu minimalists, I would like to make aware of 2 issues I came accross when trying to install Xubuntu 10.04. Hopefully this will save others from the grief I had ;)


Firstly: installing the desktop from the cd would fail with "file not found". apt-get update would work, but installation would fail.

Turns out, while "apt-get update" looks for a cdrom at /media/apt, "apt-get install" looks for it at /cdrom (note: *not* /media/cdrom). The solution is to mount the cd at a second mountpoint manually:

sudo mount /dev/cdrom /cdrom

Proceed as usual with the install.


Secondly: you may find, if you installed network manager, that its icon does not appear. This is because your network card is being managed by the /etc/network/interfaces file... leaving no unmanaged cards for NM, thus it won't bring up the icon in the system tray. Solution: edit that file, comment out the line below "auto eth0" so it looks like this:

#iface eth0 inet dhcp

Reboot.


I don't know if either of these issues constitute bugs, but I certainly didn't encounter either in the last couple of releases.

---

### Post by k3lt01 on 2010-05-05
> **Chesamo said:**
> [Shameless plug.](http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/) (Lucid guide will be up shortly; the current version of the script is on the [Launchpad](https://launchpad.net/ubuntu-desktop-minimal).)You might want to make an obvious correction to that page, 10.04 is Lucid Lynx not Karmic Koala as you have written. Otherwise nice work.

---

### Post by FatalChaos on 2010-05-06
Does anyone have any statistics or benchmarks on how much more efficient doing a minimal installation is on lucid lynx?

---

### Post by xxxxiangxxxx on 2010-05-09
Agreed. 

Also, could anyone post the amount of space it takes and the RAM usage just for a comparison?

---

### Post by mörgæs on 2010-05-09
I have a minimal 9.04 using about 80 MB memory after a boot.

---

### Post by Paqman on 2010-05-10
> **mörgæs said:**
> I have a minimal 9.04 using about 80 MB memory after a boot.

I'd second that. About 80MB RAM and 1.2GB on the hard drive.

---

### Post by dirtylobster on 2010-05-12
> **Ozitraveller said:**
> Here's a basic Lucid script:

#! /bin/bash

sudo apt-get update && sudo apt-get upgrade

# echo "[*] Installing Ubuntu Essentials"
sudo apt-get install gnome-core gdm gnome-utils gnome-system-tools x11-xserver-utils

sudo apt-get install plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label gnome-themes-selected
sudo apt-get install gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver
sudo apt-get install network-manager-gnome nm-applet startupmanager

sudo apt-get install firefox synaptic

echo "[*] Cleanup"
sudo apt-get install logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

echo "[*] Enable firewall"
sudo ufw enable
sudo ufw status

echo "[*] Done - Time to Reboot"
sudo reboot

Thank you very much!

I added notify-osd and indicator-applet-session (the lack of this package gave me an error when logging in).

I also had to comment out the last line in /etc/network/interfaces (iface eth0 inet dhcp) to get the wifi-icon to show in the notification area.

---

### Post by Ozitraveller on 2010-05-12
I did that script for, I think, the last alpha. I usually do ok on the dialog that pops up when I first login and I never get bothered again.

:)

---

### Post by dirtylobster on 2010-05-13
I need to install a .deb file and I know I can do it from the command line with "dpkg -i xxxx.deb" but what's the program that enables me to double click run it or run it directly from the browser when downloaded? Thanks!

edit: nvm found it, gdebi.

---

### Post by kero4 on 2010-05-21
Hi,

I posted this up in the install section but seems I am trying to accomplish the same thing as described in this thread through a different means and not sure it's the right way?

Can some of you take a peak and let me know what is going on and or if what I am trying to accomplish is worth the time and effort.

[http://ubuntuforums.org/showthread.php?t=1489272](http://ubuntuforums.org/showthread.php?t=1489272)

Thanks

Rod

---

### Post by Ozitraveller on 2010-05-22
Ok, I suggest you do a command-line install using the mini.iso
from here : [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) 
it's about 50MB.

And then give the script on [http://ubuntuforums.org/showthread.php?t=1155961&page=21](http://ubuntuforums.org/showthread.php?t=1155961&page=21) a try. Hint: type it in by hand it's probably going to be easier to start off. If you look further back on this thread #149 I showed how to run the script from a usb stick.

Remastersys:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)


Note: I've done this myself today so I know it works. You might like to install notify-osd and indicator-applet-session as well.

---

### Post by lakelovers on 2010-06-28
mini.iso or Lucid alternative? I've read this discussion front to end and find all the suggestions, twists and turn a bit confusing. I'm pretty dumb when it comes to "programming." I like the clarity of Chesamo's instructions but have a question. He says to use an "alternative.iso" to begin with rather than the mini. iso. What's the difference and will either or both work with his script? Guess I should ask him directly.

---

### Post by Ozitraveller on 2010-06-28
The mini.iso is suggested because it is small and will only setup and command-line environment e.g. like a DOS environment without windows over the top, no gui interface. Whereas, the alternative.iso (text based installer) is quite large and can be used to setup the full desktop environment. There is also a desktop.iso (this is the "Livecd" and has a graphical installer). Both alternative and desktop iso's can be used to install a command-line system.

Most go mini because it's small to download.

---

### Post by quirkification on 2010-06-29
I JUST reformated several hours ago, and have fixed adobe flash, reinstalled conky and google chrome with all my extensions...which should really sync(THATS A PAIN)

Is it still safe for me to run these codes?

---

### Post by Ozitraveller on 2010-06-29
> **quirkification said:**
> I JUST reformated several hours ago, and have fixed adobe flash, reinstalled conky and google chrome with all my extensions...which should really sync(THATS A PAIN)

Is it still safe for me to run these codes?

Not quite sure what you mean by safe?

---

### Post by quirkification on 2010-06-29
> **Ozitraveller said:**
> Not quite sure what you mean by safe?

haha, just that modifications i have done...whose will be deleted too and i wil have to reinstall conky and setting for compiz again.

Ill probably just do the codes...when will i be this close again???

---

### Post by mörgæs on 2010-06-30
If "do the codes" means installing using **apt-get install <some package>**, then you are completely safe. It is the same process as the one used by Synaptic.

---

### Post by lakelovers on 2010-06-30
I can't get my computer to boot from the CD. I changed the bios to make the cd drive the first boot, but it won't boot. I've not had this problem before. I re-burned the mini cd, but it still doesn't boot. What's my solution?

**Edit:** My problem, I've discovered, is that the "iso" image that I download can not be burned to a CD, in workable form. I used the download page in Ubuntu, but the download file wont work. In the Ubuntu instruction for burning a CD, it says that if the download has only one file, it will not work. So, where can I get a workable mini.iso?

---

### Post by rykel on 2010-07-01
> **vikjon0 said:**
> What is the question? Either you start over (recommended) or you remove the packages you dont want.
sudo apt-get purge <package>

If you are asking what packages you can remove with out loosing anything you want to keep, that is pretty hard for us to tell as you can imaging.

sudo apt-get purge gnome-core will clean it up pretty good ;)

I know how to remove packages I do not want, no challenge in that. It is all the "invisible" programs - esp. all the “lib*" files that stay scattered all over the root filesystem -- together, they make up the BULK of my installation - that I am trying to remove without crashing my system to the point of a reinstall.

Any ideas?

---

### Post by k3lt01 on 2010-07-01
> **rykel said:**
> I know how to remove packages I do not want, no challenge in that. It is all the "invisible" programs - esp. all the “lib*" files that stay scattered all over the root filesystem -- together, they make up the BULK of my installation - that I am trying to remove without crashing my system to the point of a reinstall.

Any ideas?
[Read this thread]("http://ubuntuforums.org/showthread.php?t=140920"), if you follow it it will remove any un-needed libs etc when you uninstall programs.

---

### Post by frodowiz on 2010-07-10
thanks for the  tip.  i have a card reader in my laptop that i use to boot  up in with a system rescue  install. was looking to build  a custom rescue install with a light ubu 10.04. i think ill go this way rather than  chopping away at a full install. much easier to add than remove.
 
Frodo

---

### Post by frodowiz on 2010-07-10
> **lakelovers said:**
> I can't get my computer to boot from the CD. I changed the bios to make the cd drive the first boot, but it won't boot. I've not had this problem before. I re-burned the mini cd, but it still doesn't boot. What's my solution?
 
**Edit:** My problem, I've discovered, is that the "iso" image that I download can not be burned to a CD, in workable form. I used the download page in Ubuntu, but the download file wont work. In the Ubuntu instruction for burning a CD, it says that if the download has only one file, it will not work. So, where can I get a workable mini.iso?
 
 
re download and compare the fingerprints.  i only ever had  1 iso  not work from another distro and its because just the right bits got sent  to another dimension during download. the keys didnt match.

---

### Post by Gorilllanobaka on 2010-08-10
Hello every one...

 I like this whole idea of achieving an minimal Desktop...

I must say although i love Ubuntu along of the years it has turned from something nice into something  very close to bloatware...No disrespect though...;)

Here is my try...Icewm+roxfiller (The blue of the mc hurts my eyes) and a screen shot..
Lemme know if you like it and if you want more screen shots...


[IMG]http://i38.tinypic.com/xbfwbc.jpg[/IMG]

As you can see i am still working on it..The poor conky is half way trough done..But i feel kinda lazy ..

What you can see there is a fully functional Ubuntu with a synaptic underneath and a seamonkey (only the browser) flash plugin ,skype ,feh ,irssi  ,build-essential leafpad,nano gxine  and of course the lovely scrot

If anyone can go lower that that....:D

Regards...

PS: [COLOR=Red][B]Maybe somebody can help me with setting up the sound though??
That would be forever appreciated[/B][/COLOR]
I tried to compile the alsa-utils the older version to get the alsaconf to work without succes.

Cheers!

---

### Post by rykel on 2010-08-11
> **Gorilllanobaka said:**
> Hello every one...

 I like this whole idea of achieving an minimal Desktop...

I must say although i love Ubuntu along of the years it has turned from something nice into something  very close to bloatware...No disrespect though...;)

Here is my try...Icewm+roxfiller (The blue..... *Snipped*
Cheers!


What you have done is very respectable AND good to us Linux lovers... but unfortunately, to the untrained eyes, it is DOS-ish and is bound to be TOO minimal already. LOL

---

### Post by Gorilllanobaka on 2010-08-11
> **rykel said:**
> What you have done is very respectable AND good to us Linux lovers... but unfortunately, to the untrained eyes, it is DOS-ish and is bound to be TOO minimal already. LOL

Well i seldom use the desktop icons anyway...The bling is just doing my head in ...
And compiz.... i really see no point in having it..
It`s 3D decorative useless effects ( when you are working they are covered by the opened windows and therefore hidden..99.999% of the time the blingy effects, they are just running in background eating cycles and RAM)
 Well,they are there only to force you to upgrade your hardware 

Now because i am human and i like some colors on the screen i will look around for a nice conkyrc file to "pimp up" my desktop..;)

On the down side i can not get the stupid sound to work on it...I got spoiled by Puppy linux where you just run alsaconf to have your stuff detected..

---

### Post by Ozitraveller on 2010-08-11
I like it! :)

Would you mind describing what you have done + installed.

I would normally not install compriz either and I would reduce the  number of desktops to 1.

I have something similar for my freenx server.

---

### Post by Gorilllanobaka on 2010-08-12
*[SIZE=4]@ Ozitraveller[/SIZE]*

What i actually have done is...I went to the Ubuntu download page an grabbed one of their 32 server  versions, installed it and then apt-get my way trough 

Icewm
synaptic (I am lazy)
Seamonkey (only the browser)
flash plugin ,
skype ,
feh ,
irssi ,
build-essential 
leafpad,
nano 
gxine 
 scrot
rox-filer (I initially started with MC but looks like my eyes does not like the blue background anymore so i switched on to rox-filer )

I added conky (Still working on it as you can see from the screenshot)

I decided there is no reason to install pmount or the equivalent since i can do it manually ...

alsa-utils (man.. i really hate the fact that they took out alsaconf out..I have been so spoiled by Puppy linux...they still keep alsaconf there..)

As a result i really do not know how to make ther sound work ...Still reading the effing manual except for the fact that the manual it does not help at all...

Right...what else??
I am working in compiling the latest version of pidgin and i wanna install Btransmission but not before fixing the sound...

That`s all i can think of at the moment..

Regards

---

### Post by Ozitraveller on 2010-08-12
> **Gorilllanobaka said:**
> *[SIZE=4]@ Ozitraveller[/SIZE]*

What i actually have done is...I went to the Ubuntu download page an grabbed one of their 32 server  versions, installed it and then apt-get my way trough 

Icewm
synaptic (I am lazy)
Seamonkey (only the browser)
flash plugin ,
skype ,
feh ,
irssi ,
build-essential 
leafpad,
nano 
gxine 
 scrot
rox-filer (I initially started with MC but looks like my eyes does not like the blue background anymore so i switched on to rox-filer )

I added conky (Still working on it as you can see from the screenshot)

I decided there is no reason to install pmount or the equivalent since i can do it manually ...

alsa-utils (man.. i really hate the fact that they took out alsaconf out..I have been so spoiled by Puppy linux...they still keep alsaconf there..)

As a result i really do not know how to make ther sound work ...Still reading the effing manual except for the fact that the manual it does not help at all...

Right...what else??
I am working in compiling the latest version of pidgin and i wanna install Btransmission but not before fixing the sound...

That`s all i can think of at the moment..

Regards

Thanks Gorilllanobaka :)

x11-xserver-utils?

---

### Post by Gorilllanobaka on 2010-08-13
> **Ozitraveller said:**
> Thanks Gorilllanobaka :)

x11-xserver-utils?

Of course...

Hang on  ..I got an idea... Here ...Lemme /var/lib/dpkg/info/ it for you..

> 

adduser                        install
adobe-flashplugin                install
alsa-base                    install
alsa-utils                    install
apt                        install
apt-transport-https                install
apt-utils                    install
apt-xapian-index                install
aptitude                    install
aspell-en                    deinstall
base-files                    install
base-passwd                    install
bash                        install
bash-completion                    install
bind9-host                    install
binutils                    install
bsdmainutils                    install
bsdutils                    install
build-essential                    install
busybox-initramfs                install
busybox-static                    install
byobu                        install
bzip2                        install
ca-certificates                    install
command-not-found                install
command-not-found-data                install
conky-all                    install
console-setup                    install
console-terminus                install
consolekit                    install
coreutils                    install
cpio                        install
cpp                        install
cpp-4.4                        install
cpu-checker                    install
dash                        install
dbus                        install
dbus-x11                    install
debconf                        install
debconf-i18n                    install
debianutils                    install
defoma                        install
dhcp3-client                    install
dhcp3-common                    install
dictionaries-common                install
diffutils                    install
dmidecode                    install
dmsetup                        install
dnsutils                    install
docbook-xml                    install
dosfstools                    install
dpkg                        install
dpkg-dev                    install
e2fslibs                    install
e2fsprogs                    install
ed                        install
eject                        install
elinks                        deinstall
esound-clients                    install
esound-common                    install
fakeroot                    install
feh                        install
file                        install
findutils                    install
fontconfig                    install
fontconfig-config                install
friendly-recovery                install
ftp                        install
fuse-utils                    install
g++                        install
g++-4.4                        install
gamin                        install
gcc                        install
gcc-4.4                        install
gcc-4.4-base                    install
gconf2                        install
gconf2-common                    install
geoip-database                    install
gettext-base                    install
ghostscript                    install
giblib1                        install
gksu                        install
gnome-keyring                    install
gnome-mime-data                    install
gnupg                        install
gnupg-curl                    install
gpgv                        install
grep                        install
groff-base                    install
grub-common                    install
grub-pc                        install
gsfonts                        install
gvfs                        install
gxine                        install
gxineplugin                    install
gzip                        install
hdparm                        install
hicolor-icon-theme                install
hostname                    install
hunspell-en-us                    install
icewm                        install
icewm-common                    install
ifupdown                    install
indicator-application                install
info                        install
initramfs-tools                    install
initramfs-tools-bin                install
initscripts                    install
insserv                        install
install-info                    install
installation-report                install
intel-gpu-tools                    install
iproute                        install
iptables                    install
iputils-arping                    install
iputils-ping                    install
iputils-tracepath                install
irqbalance                    install
iso-codes                    install
javascript-common                deinstall
kbd                        install
klibc-utils                    install
landscape-common                install
language-pack-en                install
language-pack-en-base                install
language-selector-common            install
laptop-detect                    install
launchpad-integration                install
leafpad                        install
less                        install
libaa1                        install
libacl1                        install
libapparmor-perl                install
libapparmor1                    install
libappindicator0                install
libarchive1                    deinstall
libart-2.0-2                    install
libasound2                    install
libaspell15                    deinstall
libatasmart4                    install
libatk1.0-0                    install
libatk1.0-data                    install
libatm1                        install
libattr1                    install
libaudio2                    install
libaudiofile0                    install
libavahi-client3                install
libavahi-common-data                install
libavahi-common3                install
libavahi-glib1                    install
libavcodec52                    install
libavutil49                    install
libbind9-60                    install
libblkid1                    install
libbonobo2-0                    install
libbonobo2-common                install
libbonoboui2-0                    install
libbonoboui2-common                install
libbsd0                        install
libbz2-1.0                    install
libc-bin                    install
libc-dev-bin                    install
libc6                        install
libc6-dev                    install
libc6-i686                    install
libcaca0                    install
libcairo-perl                    install
libcairo2                    install
libcap-ng0                    install
libcap2                        install
libcdio-cdda0                    deinstall
libcdio-paranoia0                deinstall
libcdio10                    deinstall
libck-connector0                install
libclass-accessor-perl                install
libcomerr2                    install
libcroco3                    install
libcups2                    install
libcupsimage2                    install
libcurl3-gnutls                    install
libcwidget3                    install
libdatrie1                    install
libdb4.8                    install
libdbus-1-3                    install
libdbus-glib-1-2                install
libdbusmenu-glib1                install
libdbusmenu-gtk1                install
libdevmapper1.02.1                install
libdirectfb-1.2-0                install
libdns64                    install
libdrm-intel1                    install
libdrm-nouveau1                    install
libdrm-radeon1                    install
libdrm2                        install
libedit2                    install
libeggdbus-1-0                    install
libelf1                        install
libept0                        install
libesd0                        install
libexif12                    deinstall
libexpat1                    install
libffi5                        install
libflac8                    install
libfont-afm-perl                install
libfontconfig1                    install
libfontenc1                    install
libfreetype6                    install
libfribidi0                    install
libfs6                        install
libfuse2                    install
libgail18                    install
libgamin0                    install
libgc1c2                    install
libgcc1                        install
libgconf2-4                    install
libgcr0                        install
libgcrypt11                    install
libgdbm3                    install
libgdu0                        install
libgeoip1                    install
libgif4                        install
libgksu2-0                    install
libgl1-mesa-dri                    install
libgl1-mesa-glx                    install
libglade2-0                    install
libglib-perl                    install
libglib2.0-0                    install
libglu1-mesa                    install
libgmp3c2                    install
libgnome-keyring0                install
libgnome2-0                    install
libgnome2-canvas-perl                install
libgnome2-common                install
libgnome2-perl                    install
libgnome2-vfs-perl                install
libgnomecanvas2-0                install
libgnomecanvas2-common                install
libgnomeui-0                    install
libgnomeui-common                install
libgnomevfs2-0                    install
libgnomevfs2-common                install
libgnomevfs2-extra                install
libgnutls26                    install
libgomp1                    install
libgp11-0                    install
libgpg-error0                    install
libgphoto2-2                    deinstall
libgphoto2-port0                deinstall
libgpm2                        install
libgs8                        install
libgsf-1-114                    install
libgsf-1-common                    install
libgsm1                        install
libgssapi-krb5-2                install
libgstreamer-plugins-base0.10-0            deinstall
libgstreamer0.10-0                deinstall
libgtk2-perl                    install
libgtk2.0-0                    install
libgtk2.0-bin                    install
libgtk2.0-common                install
libgtop2-7                    install
libgtop2-common                    install
libgudev-1.0-0                    install
libgvfscommon0                    install
libhal-storage1                    install
libhal1                        install
libhtml-format-perl                install
libhtml-parser-perl                install
libhtml-tagset-perl                install
libhtml-tree-perl                install
libhunspell-1.2-0                install
libice6                        install
libicu42                    deinstall
libid3tag0                    install
libidl0                        install
libidn11                    install
libimlib2                    install
libimobiledevice0                deinstall
libindicator0                    install
libio-string-perl                install
libisc60                    install
libisccc60                    install
libisccfg60                    install
libiw30                        install
libjack0                    install
libjasper1                    install
libjpeg62                    install
libjs-jquery                    install
libjson-glib-1.0-0                install
libk5crypto3                    install
libkeyutils1                    install
libklibc                    install
libkrb5-3                    install
libkrb5support0                    install
liblaunchpad-integration1            install
liblcms1                    install
libldap-2.4-2                    install
liblircclient0                    install
liblocale-gettext-perl                install
liblockfile1                    install
libltdl7                    install
liblua5.1-0                    install
liblua50                    deinstall
liblualib50                    deinstall
liblwres60                    install
liblzma1                    install
libmad0                        install
libmagic1                    install
libmagickcore2                    install
libmagickwand2                    install
libmailtools-perl                install
libmng1                        install
libmodplug0c2                    install
libmpcdec3                    install
libmpfr1ldbl                    install
libncurses5                    install
libncursesw5                    install
libnewt0.52                    install
libnih-dbus1                    install
libnih1                        install
libnl1                        install
libnotify1                    deinstall
libnspr4-0d                    install
libnss3-1d                    install
libntfs-3g75                    install
libntfs10                    install
libogg0                        install
liboil0.3                    install
libopenobex1                    deinstall
liborbit2                    install
libpam-ck-connector                install
libpam-gnome-keyring                install
libpam-modules                    install
libpam-runtime                    install
libpam0g                    install
libpango-perl                    install
libpango1.0-0                    install
libpango1.0-common                install
libpaper-utils                    install
libpaper1                    install
libparse-debianchangelog-perl            install
libparted0debian1                install
libpcap0.8                    install
libpci3                        install
libpciaccess0                    install
libpcre3                    install
libpcsclite1                    install
libpixman-1-0                    install
libplist1                    deinstall
libplymouth2                    install
libpng12-0                    install
libpolkit-agent-1-0                install
libpolkit-backend-1-0                install
libpolkit-gobject-1-0                install
libpopt0                    install
libpostproc51                    install
libproxy0                    deinstall
libpulse0                    install
libpython2.6                    install
libqt4-dbus                    install
libqt4-network                    install
libqt4-xml                    install
libqtcore4                    install
libqtgui4                    install
librarian0                    install
libreadline6                    install
librpc-xml-perl                    install
librsvg2-2                    install
librsvg2-common                    install
libruby1.8                    deinstall
libsamplerate0                    install
libsasl2-2                    install
libsasl2-modules                install
libschroedinger-1.0-0                install
libsdl1.2debian                    install
libsdl1.2debian-alsa                install
libselinux1                    install
libsepol1                    install
libsexy2                    deinstall
libsgutils2-2                    install
libsigc++-2.0-0c2a                install
libslang2                    install
libsm6                        install
libsmbclient                    install
libsndfile1                    install
libsoup-gnome2.4-1                deinstall
libsoup2.4-1                    deinstall
libspeex1                    install
libsqlite3-0                    install
libss2                        install
libssl0.9.8                    install
libstartup-notification0            install
libstdc++6                    install
libstdc++6-4.4-dev                install
libsub-name-perl                install
libsysfs2                    install
libtalloc2                    install
libtasn1-3                    install
libterm-readkey-perl                install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-wrapi18n-perl                install
libthai-data                    install
libthai0                    install
libtheora0                    install
libtiff4                    install
libtimedate-perl                install
libts-0.0-0                    install
libudev0                    install
libunique-1.0-0                    deinstall
liburi-perl                    install
libusb-0.1-4                    install
libusb-1.0-0                    deinstall
libusbmuxd1                    deinstall
libuuid1                    install
libvorbis0a                    install
libvorbisenc2                    install
libvte-common                    install
libvte9                        install
libwavpack1                    install
libwbclient0                    install
libwebkit-1.0-2                    deinstall
libwnck22                    deinstall
libwrap0                    install
libwww-perl                    install
libx11-6                    install
libx11-data                    install
libxapian15                    install
libxau6                        install
libxaw7                        install
libxcb-atom1                    install
libxcb-aux0                    install
libxcb-event1                    install
libxcb-render-util0                install
libxcb-render0                    install
libxcb-shape0                    install
libxcb-shm0                    install
libxcb-xv0                    install
libxcb1                        install
libxcomposite1                    install
libxcursor1                    install
libxdamage1                    install
libxdmcp6                    install
libxext6                    install
libxfixes3                    install
libxfont1                    install
libxft2                        install
libxi6                        install
libxine1                    install
libxine1-bin                    install
libxine1-console                install
libxine1-ffmpeg                    install
libxine1-misc-plugins                install
libxine1-x                    install
libxinerama1                    install
libxkbfile1                    install
libxml-libxml-perl                install
libxml-namespacesupport-perl            install
libxml-parser-perl                install
libxml-sax-expat-perl                install
libxml-sax-perl                    install
libxml2                        install
libxmu6                        install
libxmuu1                    install
libxpm4                        install
libxrandr2                    install
libxrender1                    install
libxres1                    deinstall
libxslt1.1                    deinstall
libxss1                        install
libxt6                        install
libxtst6                    install
libxv1                        install
libxvmc1                    install
libxxf86dga1                    install
libxxf86vm1                    install
linux-firmware                    install
linux-generic                    install
linux-image-2.6.32-21-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-sound-base                install
locales                        install
lockfile-progs                    install
login                        install
logrotate                    deinstall
lsb-base                    install
lsb-release                    install
lshw                        install
lsof                        install
ltrace                        install
lzma                        install
make                        install
makedev                        install
manpages                    install
manpages-dev                    install
mawk                        install
mc                        deinstall
menu                        install
midori                        deinstall
mime-support                    install
mlocate                        install
module-init-tools                install
mount                        install
mountall                    install
mtools                        install
mtr-tiny                    install
nano                        install
ncurses-base                    install
ncurses-bin                    install
net-tools                    install
netbase                        install
netcat-openbsd                    install
ntfs-3g                        install
ntfsprogs                    install
ntpdate                        install
obex-data-server                deinstall
openssh-client                    install
openssl                        install
os-prober                    install
parted                        install
passwd                        install
patch                        install
pciutils                    install
perl                        install
perl-base                    install
perl-modules                    install
pidgin-ppa                    deinstall
plymouth                    install
policykit-1                    install
policykit-1-gnome                install
powermgmt-base                    install
ppp                        install
pppconfig                    install
pppoeconf                    install
procps                        install
psfontmgr                    install
psmisc                        install
python                        install
python-apport                    install
python-apt                    install
python-cairo                    install
python-central                    install
python-dbus                    install
python-debian                    install
python-gdbm                    install
python-glade2                    install
python-gnupginterface                install
python-gobject                    install
python-gtk2                    install
python-httplib2                    install
python-launchpadlib                install
python-lazr.restfulclient            install
python-lazr.uri                    install
python-minimal                    install
python-newt                    install
python-oauth                    install
python-openssl                    install
python-pam                    install
python-pexpect                    install
python-pkg-resources                install
python-problem-report                install
python-pycurl                    install
python-serial                    install
python-simplejson                install
python-smartpm                    install
python-software-properties            install
python-support                    install
python-twisted-bin                install
python-twisted-core                install
python-wadllib                    install
python-xapian                    install
python-zope.interface                install
python2.6                    install
python2.6-minimal                install
rarian-compat                    install
readline-common                    install
rox-filer                    install
rsync                        install
rsyslog                        install
screen                        install
scrollkeeper                    install
scrot                        install
seamonkey-browser                install
sed                        install
sensible-utils                    install
sgml-base                    install
sgml-data                    install
shared-mime-info                install
skype                        install
software-properties-gtk                install
strace                        install
sudo                        install
synaptic                    install
sysv-rc                        install
sysvinit-utils                    install
tar                        install
tasksel                        install
tasksel-data                    install
tcpd                        install
tcpdump                        install
time                        install
tsconf                        install
ttf-dejavu-core                    install
tzdata                        install
ubuntu-keyring                    install
ucf                        install
udev                        install
udisks                        install
ufw                        install
unattended-upgrades                install
update-manager-core                install
update-notifier-common                install
upstart                        install
usbutils                    install
util-linux                    install
uuid-runtime                    install
vim-tiny                    deinstall
wget                        install
whiptail                    install
wireless-crda                    install
wpasupplicant                    install
x-ttcidfont-conf                install
x11-apps                    install
x11-common                    install
x11-session-utils                install
x11-utils                    install
x11-xfs-utils                    install
x11-xkb-utils                    install
x11-xserver-utils                install
xauth                        install
xbitmaps                    install
xfonts-100dpi                    install
xfonts-75dpi                    install
xfonts-base                    install
xfonts-encodings                install
xfonts-scalable                    install
xfonts-utils                    install
xinit                        install
xinput                        install
xkb-data                    install
xml-core                    install
xorg                        install
xorg-docs-core                    install
xserver-common                    install
xserver-xorg                    install
xserver-xorg-core                install
xserver-xorg-input-all                install
xserver-xorg-input-evdev            install
xserver-xorg-input-mouse            install
xserver-xorg-input-synaptics            install
xserver-xorg-input-vmmouse            install
xserver-xorg-input-wacom            install
xserver-xorg-video-all                install
xserver-xorg-video-apm                install
xserver-xorg-video-ark                install
xserver-xorg-video-ati                install
xserver-xorg-video-chips            install
xserver-xorg-video-cirrus            install
xserver-xorg-video-fbdev            install
xserver-xorg-video-geode            install
xserver-xorg-video-i128                install
xserver-xorg-video-i740                install
xserver-xorg-video-intel            install
xserver-xorg-video-mach64            install
xserver-xorg-video-mga                install
xserver-xorg-video-neomagic            install
xserver-xorg-video-nouveau            install
xserver-xorg-video-nv                install
xserver-xorg-video-openchrome            install
xserver-xorg-video-r128                install
xserver-xorg-video-radeon            install
xserver-xorg-video-rendition            install
xserver-xorg-video-s3                install
xserver-xorg-video-s3virge            install
xserver-xorg-video-savage            install
xserver-xorg-video-siliconmotion        install
xserver-xorg-video-sis                install
xserver-xorg-video-sisusb            install
xserver-xorg-video-tdfx                install
xserver-xorg-video-trident            install
xserver-xorg-video-tseng            install
xserver-xorg-video-v4l                install
xserver-xorg-video-vesa                install
xserver-xorg-video-vmware            install
xserver-xorg-video-voodoo            install
xterm                        install
xulrunner-1.9.2                    install
xz-utils                    install
zlib1g                        install




---

### Post by Ozitraveller on 2010-08-13
Thanks Gorilllanobaka appreciate your effort:)

---

### Post by stars on 2010-08-15
During a fresh install, I use the mini iso, (just type cli once the disc boots and follow the directions) then apt-get the basics (for me) to get started: 

xorg xfonts-terminus openbox openbox-themes obconf obmenu menu xcompmgr lm-sensors hddtemp sysv-rc-conf denyhosts alsa chromium-browser conky  

This allows me to have a good foundation, from there I apt-get based upon my needs for the specific machine. For example on the newest computer I built I've also installed:

dvd+rw-tools irssi mencoder ffmpeg dvdauthor scrot feh
unzip unrar rtorrent

At this time, I use this machine solely for burning dvds, converting media to dvd, torrents and irc.

Though, as another user mentioned previously in this thread, by using --no-install-recommends install ubuntu-desktop one can achieve a minimal Gnome, then add applications of the users choice, I do this as well on some machines.

After using the above minimal install of Gnome it only uses 20 to 25MB more (give or take since I cannot remember the exact number) than the Openbox install method once I edit Gnome to my personal liking.

---

### Post by Gorilllanobaka on 2010-08-16
Has anybody actually managed to get the sound working on one of these mini-installs ???

I have been trying for a while and i could not make it..

If anybody managed to get the sound working on minimal installations, would you please tell me HOW you did it??

Cheers!

---

### Post by LightningCrash on 2010-08-16
How is the desktop responsiveness of the deadline scheduler vs CFQ?

---

### Post by Gorilllanobaka on 2010-08-16
Dude.. it went right over my head..I am not a pro and you`ve just lost me...

If you ask how responsive the system is...Well.. it is blazing fast...I only use around 40-60 MB of ram out of 718 MB RAM...


Cheers

---

### Post by wankel786 on 2010-08-17
If I were to install a base system using the 10.04 minimal cd, when 10.10 comes out and I upgrade from within my install, will this install the full 10.10 ubuntu desktop or would it only install what I had in my minimal system?

---

### Post by Ozitraveller on 2010-08-17
> **wankel786 said:**
> If I were to install a base system using the 10.04 minimal cd, when 10.10 comes out and I upgrade from within my install, will this install the full 10.10 ubuntu desktop or would it only install what I had in my minimal system?

You should only need to update rather than upgrade and it's only update what you have originally installed.

---

### Post by rgihix on 2010-08-18
exactly what I have been looking for!  I have an installer that requires a GUI (in linux land who would have thought??).  I wasn't able to get the ssh -X route to work.  Again, thanks!!

---

### Post by mörgæs on 2010-08-23
Ubuntu 10.04: If you want a system which informs you about available updates, remember to install both **update-manager** and **update-notifier**. 

Many of the instructions I have seen have forgotten to mention this. 

More details here:
[http://ubuntuforums.org/showthread.php?t=1557339](http://ubuntuforums.org/showthread.php?t=1557339)

---

### Post by Ozitraveller on 2010-08-23
I intentionally don't install these: update-manager, update-notifier, as I don't find them useful in maintaining a minimal install

:)

---

### Post by athoopal on 2010-08-28
hi!
intend installing a ubuntu-minimal on a HTPC. It is a amd64 with 1g ram and a ati hd4670 card. have used TheShiv post as a basis and modified it with a lot of copy paste. I do need a torrent client and folder share over my wireless network from a ubuntu-netbook and a windows XP machine. Can somebody tell me if this script is ok?

#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#			  essentials of an Ubuntu Desktop.
#######################################################################
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core slim fast-user-switch-applet \
x11-xserver-utils localepurge\
jockey-gtk gnome-utils epiphany-browser
sudo apt-get install xorg xterm wdm icewm icemc wmctrl menu gksu synaptic gdebi--no-install-recommends
sudo aptitude install wicd python-wicd wicd-daemon wicd-gtk thunar smbfs smbc ncurse client pyneighborhood
sudo aptitude install linux-restricted-modules-generic
sudo add-apt-repository ppa:team-xbmc
sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9F10E6AE 9317790E
sudo apt-get install xbmc
sudo apt-get update && sudo apt-get install qbittorrent
echo "[*] Installing Application Essentials"
sudo apt-get update
sudo service wdm start

---

### Post by Ozitraveller on 2010-08-29
#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#                          essentials of an Ubuntu Desktop.
#######################################################################
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:team-xbmc
sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com sudo apt-get update && sudo apt-get upgrade
9F10E6AE 9317790E

echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core slim fast-user-switch-applet \
x11-xserver-utils localepurge\
jockey-gtk gnome-utils epiphany-browser
sudo apt-get install xorg xterm wdm icewm icemc wmctrl menu gksu synaptic gdebi--no-install-recommends
sudo aptitude install wicd python-wicd wicd-daemon wicd-gtk thunar smbfs smbc ncurse client pyneighborhood
sudo aptitude install linux-restricted-modules-generic
sudo apt-get install xbmc
sudo apt-get install qbittorrent

echo "[*] Installing Application Essentials"
sudo service wdm start
***************

Something like this ... :)

Enjoy

---

### Post by tubunu on 2010-09-11
Excuse my ignorance, but is the minimal Ubuntu installation suitable to run on a low end system with PIII/192RAM? or do I need to look into lightweight distros instead?

The only applications I will need on this PC are: Ubuntu base components, Chromium, sylpheed, VLC, and a wireless network.

---

### Post by quixote on 2010-09-11
Even with minimal ubuntu, I believe you're bumping up against the limits there, given what you want to run.

---

### Post by tubunu on 2010-09-11
Thanks, I'm looking now at lightweight distros.

---

### Post by mörgæs on 2010-09-11
> **tubunu said:**
> Excuse my ignorance, but is the minimal Ubuntu installation suitable to run on a low end system with PIII/192RAM? or do I need to look into lightweight distros instead?

The only applications I will need on this PC are: Ubuntu base components, Chromium, sylpheed, VLC, and a wireless network.

I am writing this from a Compaq Armada with 192 MB memory running a full Lubuntu 10.04. It works fine, and of course a minimal desktop would be even better. 

First install the command-line-only system from this ISO:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then 

```
sudo apt-get install lubuntu-desktop
```and finally after a boot

```
sudo apt-get clean
```The other Buntus are far heavier than Lubuntu and not worth trying on this hardware.

Here is the result of **free -m** with Chromium runnning:

```

             total       used       free     shared    buffers     cached
Mem:           181        177          3          0         11         80
-/+ buffers/cache:         84         96
Swap:          528         20        508
```That is, 84 MB used. Remember to have wired internet access throughout the installation.

Edit: Adding Flashblock to Chromium or Firefox is a great boost to performance on an old machine.

If you want to have more than one keyboard layout, here is how:
[http://ubuntuforums.org/showpost.php?p=10231776&postcount=8](http://ubuntuforums.org/showpost.php?p=10231776&postcount=8)

If you are not satisfied with the selection in the default Lubuntu package, here is a script allowing you to pick and choose:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by Ozitraveller on 2010-09-12
I'm running on a PII/500 with 389MB ram and is ok, 192 would be pushing it I think. Dillo is a very light browser.

Suggest: PuppyLinux, DSL, TinyCore this is probably the smallest GUI based, beyond that there is command-line....

---

### Post by elkguy on 2010-09-18
If I follow this:

```
#! /bin/bash

sudo apt-get update && sudo apt-get upgrade

# echo "
[*] Installing Ubuntu Essentials"
sudo apt-get install gnome-core gdm gnome-utils gnome-system-tools x11-xserver-utils

sudo apt-get install plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label gnome-themes-selected
sudo apt-get install gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver
sudo apt-get install network-manager-gnome nm-applet startupmanager

sudo apt-get install firefox synaptic

echo "
[*] Cleanup"
sudo apt-get install logrotate localepurge
sudo apt-get autoremove && sudo apt-get clean all && sudo apt-get autoclean all

echo "
[*] Enable firewall"
sudo ufw enable
sudo ufw status

echo "
[*] Done - Time to Reboot"
sudo reboot                      
```And remove plymouth and gmd, will it boot without anything graphical and require me to login via CLI?
(Because that's what I want to do)

Also, another question... How would I run this file in the CLI after installing Ubuntu Minimal?

Third question.... Do I still have to install notify-osd in this version of Ubuntu Minimal?

---

### Post by Ozitraveller on 2010-09-19
The answer to your 1st question is yes.

I explained about copying the script from my usb stick here:
November 23rd, 2009
[http://ubuntuforums.org/showthread.php?t=1155961&page=15](http://ubuntuforums.org/showthread.php?t=1155961&page=15)

I don't install these : notify-osd ...

Note:
I've also switched to chromium browser from firefox.

Also because I have a wired internet connection I would usually install these :  network-manager-gnome nm-applet, unless I wanted to vpn into work, or go wireless.

I'm looking into OpenBox and fluxbox now...

---

### Post by nandita on 2010-09-19
i have problems setting up internet connection on ubuntu could u help me plz

---

### Post by mörgæs on 2010-09-19
> **nandita said:**
> i have problems setting up internet connection on ubuntu could u help me plz

Welcome to the forum. Please open a new thread rather than posting in this one, and remember to give a thorough and detailed description of hard- and software.

---

### Post by Trymtor on 2010-09-30
Hello everybody!
Ubuntu 10.10 Maverick has already released RC. 
Can you show me a script to install a minimal Maverick.
Thankyou!

---

### Post by SteveDee on 2010-09-30
This is an interesting thread, and I have been playing around with a mini install in VirtualBox to get an idea how suitable it might be. I plan to use the minimal install for all new installations, once I've decided which Window Manager(s) to go with.

One of the things I wanted to check was wifi configuration. I don't think I can rely on the VM for this, so for now I have simply added LXDE, IceWM & Fluxbox via Synaptic to my 10.04+Gnome based laptop, which allows me to select one of these WMs as I logon.

My problem is that I can't see how to configure wifi from these WMs. I can still get to the Gnome Control Panel from these light weight WMs (which shows the correct settings) but my wifi only works in a Gnome session. So I have 2 questions:-
1. why is my wifi not working when I run a WM other than Gnome?
2. if I were to use a mini install and use (say) LXDE, presumably the Gnome Control Panel would not be available, so how would I control/configure wifi?

---

### Post by Ozitraveller on 2010-09-30
> **Trymtor said:**
> Hello everybody!
Ubuntu 10.10 Maverick has already released RC. 
Can you show me a script to install a minimal Maverick.
Thankyou!

See #264 post :), there are also many others who have posted scripts in this thread.

---

### Post by Ozitraveller on 2010-09-30
> **SteveDee said:**
> This is an interesting thread, and I have been playing around with a mini install in VirtualBox to get an idea how suitable it might be. I plan to use the minimal install for all new installations, once I've decided which Window Manager(s) to go with.

One of the things I wanted to check was wifi configuration. I don't think I can rely on the VM for this, so for now I have simply added LXDE, IceWM & Fluxbox via Synaptic to my 10.04+Gnome based laptop, which allows me to select one of these WMs as I logon.

My problem is that I can't see how to configure wifi from these WMs. I can still get to the Gnome Control Panel from these light weight WMs (which shows the correct settings) but my wifi only works in a Gnome session. So I have 2 questions:-
1. why is my wifi not working when I run a WM other than Gnome?
2. if I were to use a mini install and use (say) LXDE, presumably the Gnome Control Panel would not be available, so how would I control/configure wifi?

Hope this helps :)
[http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page)
[http://lxde.org/lxde](http://lxde.org/lxde)
LXNM
Lightweight network connection manager. LXNM is a helper daemon for LXDE supporting wireless connections (Linux-only).

---

### Post by SteveDee on 2010-10-01
Thanks for the info.

I've put a mini build together in a virtual machine, now I need to try it on some real hardware.

This is the current status of lxnm: [http://wiki.lxde.org/en/LXNM](http://wiki.lxde.org/en/LXNM)
...so I try and use NM.

---

### Post by Rodney9 on 2010-10-01
[SIZE=3]SOLVED
It was hardware issue I have now fixed.[/SIZE]

> I have tried 3 times to install the Ubuntu Minimal CD, the same problems happens each time, I can not get to the command prompt.

All 3 installed fine, I reboot when told , remove cd , then I get grub and it doesn't matter which I pick, the curser just blinks for 10 seconds then the screen goes into saver mode and I can not get it to wake up.

Ubuntu full and Zenwalk all install fine , what's going on , any clues ?Thanks for any help,
Rodney

---

### Post by Rodney9 on 2010-10-02
It is all working now, what a brilliant idea, Thank You !

---

### Post by SteveDee on 2010-10-03
> **Ozitraveller said:**
> Hope this helps :)
[http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page)
[http://lxde.org/lxde](http://lxde.org/lxde)
LXNM
Lightweight network connection manager. LXNM is a helper daemon for LXDE supporting wireless connections (Linux-only).

Well, I progressed from a virtual machine to installing mini-unbutu 9.04 onto a real machine. It works great using the lxde desktop environment!

Getting the wireless to work was a bit of a struggle, but its now running using lxnm rather than Gnome.

I couldn't get the lxdm display manager to work so I'm using its ugly cousin wdm.

I have attached my notes as a text file rather than filling the page with boring detail.

---

### Post by cg-cnu on 2010-10-22
Hey guys... This is a very great thought and it exactly fits my need. I want to achieve the minimal.

I tried but i have some problems.

as said in the instructions... 

I have downloaded the ubuntu 10.10 minimal.
created a bootable cd.
started command line installation  and did pretty much as said here.....[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

but when choose the mirror location........I am getting the error message of bad archive mirror. I am getting the same message if i change the location and select a different one.

I am a noob and struck with it...pls help me.

---

### Post by mörgæs on 2010-10-22
Hi, welcome to the forum.
Please post the exact error message.

(Did you have wired internet access while installing, by the way?)

---

### Post by Ozitraveller on 2010-10-22
> **SteveDee said:**
> Well, I progressed from a virtual machine to installing mini-unbutu 9.04 onto a real machine. It works great using the lxde desktop environment!

Getting the wireless to work was a bit of a struggle, but its now running using lxnm rather than Gnome.

I couldn't get the lxdm display manager to work so I'm using its ugly cousin wdm.

I have attached my notes as a text file rather than filling the page with boring detail.

here is the lubuntu-desktop package:
[http://packages.ubuntu.com/lucid/lubuntu-desktop](http://packages.ubuntu.com/lucid/lubuntu-desktop)
lxnm is not mentioned I think it was replace with gnome-network-manager from 9.10.

You might find it better to use the lxde part from 9.10 LTS rather than 9.04 as it's more mature.

:)

---

### Post by cg-cnu on 2010-10-23
> **mörgæs said:**
> Hi, welcome to the forum.
Please post the exact error message.

(Did you have wired internet access while installing, by the way?)

Hey......Thanks for your reply.:)

Actually I got the error message of "Bad archive mirror"
and it has a pretty large error message which I didn't remember. Now I don't have the access to my pc. :(
So, I will again install it tomorrow and note down the message and post it here. 

Pls stay with me......I will post it.

---

### Post by SteveDee on 2010-10-23
> **Ozitraveller said:**
> 
...you might find it better to use the lxde part from 9.10 LTS rather than 9.04 as it's more mature.

:)

Thanks for the info. I chose 9.04 for the test as I have a number of computers with Intel graphics. So 9.10 tends to be unstable and 10.04 is a complete disaster.

However 10.10 has now arrived and I have conducted 2 clean installs of Lubuntu on 2 Compaq D510s, which boot in 25s, shutdown in 4s and run like a charm. They tick-over with cpu around 2% and memory 80-90MB, leaving plenty of resources for my big fat apps (like Firefox & OpenOffice).

---

### Post by k3lt01 on 2010-10-23
> **Ozitraveller said:**
> You might find it better to use the lxde part from 9.10 LTS rather than 9.04 as it's more mature.Just clarifying that the LTS is 10.04 not 9.10.

---

### Post by Ozitraveller on 2010-10-23
> **cg-cnu said:**
> Hey guys... This is a very great thought and it exactly fits my need. I want to achieve the minimal.

I tried but i have some problems.

as said in the instructions... 

I have downloaded the ubuntu 10.10 minimal.
created a bootable cd.
started command line installation  and did pretty much as said here.....[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

but when choose the mirror location........I am getting the error message of bad archive mirror. I am getting the same message if i change the location and select a different one.

I am a noob and struck with it...pls help me.

These might help too, it gives you up-to-date info on the state of the repo.
Official Archive Mirrors for Ubuntu
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by amjjawad on 2010-12-17
Before I read this thread, I managed to install a lighter system on my +11 years laptop (which has NO CD-Drive and NO LAN - had to connect the HDD to my PC) and it's almost broken. First, I installed Ubuntu Server 10.04 and then installed Fluxbox, Openbox and Icewm. It was working and nothing wrong except I forgot to install wicd so I had to go back, connect the HDD of that laptop to my PC and install from there but I tried the use the minimal CD this time. Unfortunately, it did not work. Had to format, install Ubuntu Server once more, installed Fluxbox only (yes, I know, I already installed xinit) with wicd and some other packages. It did not work :(

I'm trying to install Mint Fluxbox right now.

I'd love to start from scratch and build the system package by package but that laptop is a real pain (ask me about it) and if a tiny thing goes wrong, boom, the whole thing will stop working.

Gnome will not work on that laptop (don't ask me about the hardware specifications :)  ). I then saw this post but it's too late now to try it.

Good luck and nice guide :)

---

### Post by Dezfor on 2011-03-08
Thanks for script! Works like a charm.
I've installed basic Ubuntu's system from alternative CD. System size was 439,2 MB :)
Then I've installed Xserver and Gnome-core using script:
> apt-get update && apt-get upgrade
apt-get install xorg x-window-system-core xinit x11-xserver-utils
apt-get -y --no-install-recommends install gnome-core

---

### Post by Ozitraveller on 2011-03-14
Hi All

Just wondering whether anyone had tried this? I'm interested in the performance when compared to a mini ubuntu or lubuntu. BTW, maverick or natty only. I thought my niece might like a custom install with unity-2d on her netbook, currently running lubuntu 10.04.

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d
# sudo apt-get dist-upgrade

# This will install all of the necessary dependencies to run Unity 2D, including a "Unity 2D" session that you'll need to login with.

# Then do the following:
#  * log out
#  * log back in and choose the "Unity 2D" session in the drop-down menu at the bottom of the login screen
#  * you will then be running Unity 2D

---

### Post by Czarcasmo on 2011-04-16
Hi all.

I have plenty of space to host, but I am curious if anyone is interested in creating a ubuntu minimal ("Mubuntu" ... or something) spin people can install. 

PM me if interested.

Czar.

---

### Post by mörgæs on 2011-04-16
Thanks for the offer, but one of the advantages of a minimal install is having a number of choices during the install (which should be part of the regular Ubuntu install as well). A good example is here:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

If you only have wired internet access and a script like this one, there is no need for a new Buntu.

---

### Post by jack0 on 2011-04-20
I bet there is a way to point the apt-get util to a cd/dvd

just like when you insert an ubuntu install cd into an already installed system, and synaptic? asks you to add this disk to the repositories.


I mean, i would rather not to use the internet as the source for the packages, if i already downloaded the hole cd (or a usb stick =) ), that would be faster i guess.

I bet you geniuses know how to do that

---

### Post by Ozitraveller on 2011-04-21
Try here:
Ubuntu Documentation > Ubuntu 10.04 > Adding, Removing and Updating Applications
[https://help.ubuntu.com/10.04/add-applications/C/index.html](https://help.ubuntu.com/10.04/add-applications/C/index.html)

---

### Post by mörgæs on 2011-04-21
> **jack0 said:**
> I bet there is a way to point the apt-get util to a cd/dvd

just like when you insert an ubuntu install cd into an already installed system, and synaptic? asks you to add this disk to the repositories.


I mean, i would rather not to use the internet as the source for the packages, if i already downloaded the hole cd (or a usb stick =) ), that would be faster i guess.

I bet you geniuses know how to do that

I would recommend installing from the web, whenever available. This way you will know that all packages are in their newest state.

---

### Post by ArielSonique on 2011-04-25
> **jack0 said:**
> I bet there is a way to point the apt-get util to a cd/dvd


I think this does the trick: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by linuxyogi on 2011-05-05
Hi, I am trying to install Natty Minimal

[http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso)


I there a way to configure pppoe ?

I need a working DSL connection to download the packages.

---

### Post by frodowiz on 2011-05-07
i cant say for sure but i know mose dsl modems have  a place to configure this. just set mine a few days ago after replacing the cruddy att modem.. check out your modem portal set-up page and look for pppoe

---

### Post by spam12345 on 2011-05-16
> **jack0 said:**
> I bet there is a way to point the apt-get util to a cd/dvd

just like when you insert an ubuntu install cd into an already installed system, and synaptic? asks you to add this disk to the repositories.


I mean, i would rather not to use the internet as the source for the packages, if i already downloaded the hole cd (or a usb stick =) ), that would be faster i guess.

I bet you geniuses know how to do that

> 
If you want Ubuntu to install any current packages from the CD rather  than via the Internet, then make sure your Alternate CD is in the drive  and run:
             $ sudo apt-cdrom add

         Now we'll update the system:
             $ sudo apt-get update
             $ sudo apt-get dist-upgrade

I found it from: [http://www.abforum.be/showpost.php?p=35873&postcount=1](http://www.abforum.be/showpost.php?p=35873&postcount=1)

---

### Post by lo.j on 2011-05-19
hi all,
i'm also trying to have an ubuntu minimal installation based on **natty narwhal**, with unity therefore...

cannot understand which packages are part of the *unity-core*...

thanks.

---

### Post by Rodney9 on 2011-06-16
I just created a Maverick 10.10 minimal for my laptop.

I added the window manager, Openbox, I then added the just software I wanted ie for my ipod, and Thunderbird email, Firefox browser, Skype, etc. etc.
It all adds up to just over 3 Gb and boy is it fast !!!
My desktop 10.4.2 is 13Gb and slower.

---

### Post by Ozitraveller on 2011-06-17
> **Rodney9 said:**
> I just created a Maverick 10.10 minimal for my laptop.

I added the window manager, Openbox, I then added the just software I wanted ie for my ipod, and Thunderbird email, Firefox browser, Skype, etc. etc.
It all adds up to just over 3 Gb and boy is it fast !!!
My desktop 10.4.2 is 13Gb and slower.

Hi Rodney9

Would you mind describing what you did to setup your 'Maverick 10.10 minimal'. I'm sure there would be some new to the thread who would like to try this out.

Thanks

Ozi

---

### Post by Rodney9 on 2011-06-17
> **Ozitraveller said:**
> Hi Rodney9

Would you mind describing what you did to setup your 'Maverick 10.10 minimal'. I'm sure there would be some new to the thread who would like to try this out.

Thanks

Ozi

It was quite easy, nothing original, I borrowed other peoples brilliant ideas and used what suited me.
I followed this site - [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
found it very good.
Then I used the script from this site -
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
I picked which pieces I wanted from it, I chose no to a desktop as I had already installed Openbox. Seeing i did not use one of the desktop environments from Andy's script I did have to install Alsa for sound
Then it was just a matter of tweaking Openbox to my liking and addding any software that the script didn't have through Synaptic ie gtkpod, gpodder to use my ipod shuffle.
Openbox sites I uses included - [http://openbox.org/](http://openbox.org/)
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[https://urukrama.wordpress.com/openbox-guide/](https://urukrama.wordpress.com/openbox-guide/)

And when I got it to a working and usable stage, I made a clone with [Clonzilla]("http://clonezilla.org/") I ended up making three clones, after all it was 3Gb, It was like saving in a game.

---

### Post by orbtron on 2011-06-27
Hi, This sounds like a good idea and would like to try it out. Just need to know something.  Can this be done in VMware ? 

As I have tryed Installing 11.04 Minimal, It installs fine just won't boot. It goes too the 11.04 and then to a blank screen with a blinking _ and just sits there. 

Just wondering if its something to do with VMware.

Regards
Orbtron

---

### Post by Ozitraveller on 2011-06-27
Yes vmware or virtualbox work just fine. How have you got the virtual machine setup? Number of cores, ram, etc...

---

### Post by mörgæs on 2011-06-28
> **orbtron said:**
> 
As I have tryed Installing 11.04 Minimal, It installs fine just won't boot. It goes too the 11.04 and then to a blank screen with a blinking _ and just sits there. 

Just wondering if its something to do with VMware.

Regards
Orbtron

For how long did you wait at the blinking underscore?

I don't know Vmware, but for a normal installation the underscore (given that it really is persistent, not just slow) could indicate that you need boot options. There are some links in this post:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by c-1000 on 2011-06-28
if youre doing a minimal install of 11.04 you have to hit "ctrl-alt-f1" at the blinking cursor.

...i guess its a 'new feature' ;)

---

### Post by lo.j on 2011-06-28
> **c-1000 said:**
> if youre doing a minimal install of 11.04 you have to hit "ctrl-alt-f1" at the blinking cursor.

...i guess its a 'new feature' ;)

try this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658)

---

### Post by capink on 2011-06-28
deleted

---

### Post by orbtron on 2011-06-28
> **Ozitraveller said:**
> Yes vmware or virtualbox work just fine.  How have you got the virtual machine setup? Number of cores, ram,  etc...

Thanks for confirming, Yea the vmware config seems to be setup fine.

> **mörgæs said:**
> For how long did you wait at the blinking underscore?
 

I left it sitting for over an hour, lol. Thanks for the link :) 


> **lo.j said:**
> try this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658)

Alt+F1 dropped me to a prompt :) Thanks for the link, now I can maybe get somewhere :o 

Regards
Orbtron

---

### Post by vikjon0 on 2012-01-06
Just installed gnome-core (no recommend) on Oneric. Do I miss something or is this a total nightmare?

Everything is installed...including Network manager & GDM. What is up Ubuntu? Do a solution exist for gnome on Ubuntu or it is time to move on?

---

### Post by Ozitraveller on 2012-01-06
> **vikjon0 said:**
> Just installed gnome-core (no recommend) on Oneric. Do I miss something or is this a total nightmare?

Everything is installed...including Network manager & GDM. What is up Ubuntu? Do a solution exist for gnome on Ubuntu or it is time to move on?

Not sure what version of gnome you are intending to install Classic Gnome (Gnome 2) or Gnome 3? I'm using xubuntu, crunchbang, and archlinux these days.

---

### Post by vikjon0 on 2012-01-07
> Not sure what version of gnome you are intending to install Classic Gnome (Gnome 2) or Gnome 3?

Not sure, but the problem is not gnome but the way Ubuntu have packaged it. I need to find another package than gnome-core, and perhaps there is a classic package that will suite me better. 

Of course another solution is to use something else than gnome.

---

### Post by frodowiz on 2012-01-10
> **abhiroopb said:**
> This is why people get put of by linux threads. I phrased my comments quite clearly. I did not intend to bash the author or his howto. I merely wanted to comment on how this could be improved, and where exactly this would be useful.

Even starting from a minimal install, this is still a simple apt-get install nothing more. Perhaps it may be more useful (like I have already suggested) to include which startup applications and bootup applications can be stopped.


i was quite put off by this poster's attitude.. i wanted to pound him for his inconsiderations but after reading his comment 3 or 4 times, i decided his comments  do more than i could..   this tutorial is well done,prompt and efficient but what makes it even more so is that it is applied where it belongs.. a minimal install is where customizing begins, not after bloating your ubuntu then realizing you didnt need 4 ways to open a text file.. unfortunately most will never understand that until they have  tried it the hard way..

i would have had more respect for the poster had he even tried studying apt and its magic then dissed the method but he sounds like a hothead and too impatient to reap anything but his own frustration.. i wish i could be nice  like most of the community..

ive used this method several times on different installs.. now im gonna use it for ubu11.10.. thank you for  the tutorial, you are appreciated

---

### Post by vikjon0 on 2012-01-13
Ok on oneric you can use 
gnome-session-fallback --no-install-recommends

Looks ok, but I still pretty upset that core was not allowed to remain core.

---

### Post by aliancemd on 2012-05-27
Installing this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
And then:
```
sudo apt-get install kde-plasma-desktop kubuntu-low-fat-settings
```

---

### Post by king9174 on 2012-05-29
This is going to come in handy for my new project. It abit of a mash of ubuntu and chrome OS. If anyone has opinions on such a distro please feel free to pm me. Its basically ubuntu but works along the same lines as chrome OS or more accurately a chromebook. The idea of having a lightweight distro that boots in under a minute, but has more than a little web browser for the user interface. Lets you save files and create documents like an OS should. Making full use of ubuntu one to backup to cloud lightening your HDD and there for quickening any start up process that slows you down.

---

### Post by Stanwilliamsmusic on 2012-06-28
Great tutorial! 


I built my last system   in a similar manner.
 I got  the maverick 10.10 minimal  .iso  and  just installed the stuff that I wanted  and or  needed from the terminal, and I installed the Gnome-desktop, that was Gnome2.xx

I wish support had not ended for it, it really ran great and bug free on the hardware compared to  a normal full install.  and as you said not as resource intensive as the full install was. 
 ( I installed the normal full version  on a different partition to see the difference) .

---

### Post by Froggus on 2013-01-24
Does anyone have any recommendations for a basic media player. It must have internet access with flash, a media player (VLC or Mplayer) a jpeg viewer/slideshow, remote control from android tablet. Based on latest version of ubuntu 12.10. (Preferably without unity desktop) 
Has anyone done this and what setup did you use?

---

### Post by Ozitraveller on 2013-01-24
Sorry I can't help you that, these days I use debian sid, or #! Wheezy. There quite a few #! crunchbang music guys if you care to visit, they a friendly and will be able to help you.

Ozi

---

### Post by Froggus on 2013-01-24
thanks ill check out crunchbag

---

