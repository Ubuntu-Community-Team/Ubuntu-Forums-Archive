---
title: "I am in love with Ubunutu and especially the forum design :D"
date: 2018-01-29
forum: Ubuntu, Linux and OS Chat
---

### Post by amiga500 on 2018-01-29
Hey,

There is something about the forum here ubuntuforums.org the color theme, the look, the feel is so satisfying and it screams ubuntu and I am in love, in love, in love, in love with Ubuntu in every way. If it wasn't for a fact that specific programs do not work with Ubuntu I would have left windows 10 long time ago and moved to ubuntu for the rest of my life as my main OS. However, putting this aside. I have one request and suggestion if possible. The one thing that makes ubuntu a little bit discouraging is the way when you need to install programs how you need to go to the terminal and do so many scripts just to get a single program installed. That is to say if everything went smoothly. One thing I loved about how Mac OS X does thing is that you double click the icon it mounts it like a CD image..double click install or drag and drop to your location and you are done. Then you eject the mounted image and poof you are done.

Is this something possible with Ubuntu?

---

### Post by yetimon_64 on 2018-01-30
> **amiga500 said:**
> ...The one thing that makes ubuntu a little bit discouraging is the way when you need to install programs how you need to go to the terminal and do so many scripts just to get a single program installed...

No, the terminal is only one option for installing, you can also use Synaptic or the Software Centre (both GUI applications). Unless of course you are compiling from source code or are installing from non Ubuntu repository sources.
 
Most programs the average user needs can be found in the software centre or can be installed with a GUI application like Synaptic.

I must admit I personally like to install with the terminal as I find it much faster to load than a GUI application and is very quick and easy to use for me, however if a problem crops up I switch to Synaptic (GUI application installer).

New users often find the software centre an easier installer to use than the terminal. You really don't need to use the terminal to install the vast majority of applications in Ubuntu but can do so if you wish.

Here is a link for you to peruse that shows how to install using the software center, gdebi for .deb files from non ubuntu sources, Synaptic Package Manager, the terminal using apt-get commands (what your comments refer to :-)) and from PPA's (personal package archives) and source code (these last 2 also use the terminal ;-)).
 [https://itsfoss.com/remove-install-software-ubuntu/]("https://itsfoss.com/remove-install-software-ubuntu/")

Also a link for how to use gdebi instead of software center (linked in the previous linked guide, gdebi is a much "lighter" application for installing than the software center)...
[https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/)

---

### Post by poorguy on 2018-01-30
I personally like to use Synaptic Package Manager as I can see exactly what is to be installed.

---

### Post by speedwell68 on 2018-01-30
As said you can install using the GUI, however installing via the terminal is way faster.  I can have an install running in the terminal in the time it takes to load the Ubuntu Software Centre.

---

### Post by amiga500 on 2018-01-30
Out of curiosity...is it technically impossible to write an installer that takes over terminal installation and unite all of forms of installation in a GUI installer mechanism and make it a standard? I am only asking if it is technically possible not saying will do it or something just wondering the technical possibility. So far I am getting the assumption with Linux it is impossible and everything is done through terminal because it can't be done ever in technical terms. Now I am just wondering if this is done intentionally by all Linux community because they love terminal or it is done because it is impossible with Linux.

---

### Post by oldfred on 2018-01-30
Have you actually tried the gui installers Software Center or Synaptic as mentioned in several of the above posts.
Try them, I think you will find them very usable.

---

### Post by amiga500 on 2018-01-30
Aren't they like google play or microsoft store. You have to install and get only what software they want to show you or is it like google seach I can type whatever program I want, it finds it and install it?

---

### Post by yetimon_64 on 2018-01-31
> **amiga500 said:**
> Aren't they like google play or microsoft store. You have to install and get only what software they want to show you or is it like google seach I can type whatever program I want, it finds it and install it?

You have more control of what software you have access to with the Ubuntu repositories. You can be very selective or can enable all the standared repos or even add other sources to the system with PPA's (personal package archives).

All the installers be they Synaptic, the Software Center or the terminal with apt-get commands all operate through whichever repositories you have enabled in /etc/apt/sources.list or from entries in the directory /etc/apt/sources.list.d. These repositories/PPAs can be easily enabled/disabled via the GUI utility "Software and Updates" (see the 2 attached screen shots). From the 2 attached screenshots you can see various repositories and PPA's (personal package archives) from which I can install applications using the GUI installers or with, my personal preference, the terminal. From whatever sources you have enabled you can "search" for applications using synaptic or the software center, but it would not be like searching the whole web with google as such.
[ATTACH=CONFIG]278394[/ATTACH]  [ATTACH=CONFIG]278395[/ATTACH]

Whichever entries above that have a ticked selection box beside them is where the GUI installers or the terminal can select an application from in my system's set up.

Apart from the above repos and PPAs I can also use gdebi (or the software center) to install from downloaded debian installers (.deb files), though I would recommend to a new starter to stick to the official repositories and not download from unknown sources on the internet. There are some reputable sources outside the official repos that supply such installers (Google and Skype come to mind there amongst some other well known entities). There are increased security risks using such sources from outside the official repos. Even using PPAs as I am doing as shown above carries some risks, particularly with respect to breaking my system.

If an application is not in the repos, does not have a PPA available but source code is available you can download and build the application for yourself from such source code. This last option is DEFINITELY NOT recommended for a new starter to Ubuntu/Linux. Apart from system breakage there are definite security implications from using such methods, you would need to be able to check the source for yourself or have someone else you trust check the source for you. Such applications would not be automatically updated and would need to be manually managed by the user where they are used.

Hope this helps a bit, others here may be able to add more software related tips; regards, yeti.

---

### Post by amiga500 on 2018-01-31
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAH!!!!!!!!!!!!!!! UBUNTU IS SO MUCH FUN!!!! LIKE PLAYING THE BEST ONLINE RPG GAME ON EARTH WITH THE LARGEST MAP EXISTED ON HUMAN HISTORY WITH ENDLESS WEAPON CUSTOMIZATION, PETS, ETC

Heheh I love Ubuntu!!

---

### Post by yetimon_64 on 2018-01-31
> **amiga500 said:**
> AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAH!!!!!!!!!!!!!!! UBUNTU IS SO MUCH FUN!!!! LIKE PLAYING THE BEST ONLINE RPG GAME ON EARTH WITH THE LARGEST MAP EXISTED ON HUMAN HISTORY WITH ENDLESS WEAPON CUSTOMIZATION, PETS, ETC...


Ouch! my [s]ears[/s] eyes are now a hurtin' :). 


> **amiga500 said:**
> ...Heheh I love Ubuntu!!
Yep, it sure is a flexible system and fun "beast" to play/experiment with ;) Cheers, yeti.

---

### Post by SantaFe on 2018-01-31
> **amiga500 said:**
> Hey,

There is something about the forum here ubuntuforums.org the color theme, the look, the feel is so satisfying and it screams ubuntu and I am in love, in love, in love, in love with Ubuntu in every way. 

I like the forum look also, just wish that there was an Ubuntu-MATE Green forum skin as well as the traditional Ubuntu one.  :D

But then I do use prefer the MATE spin over the Gnome one. ;)

---

