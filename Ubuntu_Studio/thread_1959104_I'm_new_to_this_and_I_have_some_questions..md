---
title: "I'm new to this and I have some questions."
date: 2012-04-15
forum: Ubuntu Studio
---

### Post by Cr1scoD1sco on 2012-04-15
Hello, I apologize that I'm just asking questions when the point of a forum is to discuss things and not just ask questions.  That being said, I want to try many things in Ubuntu, but I'm not totally sure what I can and cannot do.  

I have been running Ubuntu Studio 11.04  on an old computer for about a week now.  From what I can tell, the programs are working fine.  I chose to use Ubuntu Studio mainly to use Ardour and a few other applications. Here's where I start getting problems. On a separate computer, I run Windows XP.  About a year ago, I made an Impulse buy of Pro Tools SE bundled with a regular M-Audio Fast Track (not Fast Track Pro).  Little did I know how awful SE is, especially on Windows. Anyway, I plan on, in the future, buying a Macbook Pro and Logic Pro or buying Sonar. I decided in the mean time to try Ardour in Ubuntu Studio.  Now, I thought this would work out great because I could still use my Fast Track for Ardour.  I plugged the Fast Track into the USB input of my computer and started up windows. The computer gave power to the Fast Track and I could hear my guitar, however I could not hear anything going on in Ubuntu and when I recorded into ardour, there were no signs of it recognizing any sounds. So my first question is, will a regular M-Audio Fast Track work in Ubuntu? If not, what would you suggest I do instead? What USB Audio Interfaces will work with Ubuntu?

The second thing I'm wondering is about Wine.  I have done some reading and it appears that some programs, such as Pro Tools, do not work well if they work at all in Ubuntu.  I would like to try a demo of Sonar or Pro Tools in Ubuntu using wine but I want to know if it's worth it and if I will be able to delete them afterwords?

Lastly, my computer isn't connected to the internet, so whenever I want to download something, I have to use another computer (running Windows) to download it to a disc and then download it from that disc.  My question is, what would you suggest I use to connect my computer to the internet.  I'm thinking of using a wireless card, but do I need to buy a specific one because it's running Linux instead of Windows or another OS? If so, which one would you suggest? I would like to keep it pretty cheap.

Any and all help is greatly appreciated :)

---

### Post by jejeman on 2012-04-15
Wired netwrok connection is always the best.

---

### Post by sgx on 2012-04-15
I have a Fast-Track, probably the same or older, works fine,
look at the rakarrack topic on the main page, and follow the
steps, and look at the mentioned wiki links, and search
youtube for qjackctl ardour.

Use reaper for hosting vsts in wine. You must install wineasio,
and run the command

regsvr32 wineasio.dll

Run winecfg to open a prefs panel, and in the audio area, choose alsa.

wine reaper422-install.exe

simple to launch installers, or windows apps. The windows folders will be in a new .wine folder, so enable showing hidden files.

Dongled, pace, ilok, macromedia plugins won't work, most others will.

Cantabile 1.2lite and windows energyXT2 also are good
vst host options. Some with FLStudio are successful, reaper
is the best option for most.

Forums are dead without questions, and new users!
Cheers

---

### Post by sgx on 2012-04-15
There are ways to install ubuntu into windows, called
wubi, or mint4win (for the ubuntu Mint version).

Ubuntu gets installed like a windows app in a folder.
When you reboot, there will be a page to choose booting
windows or ubuntu.  You'll need hard-disk space, 15 gig as I recall,
but it works. You should be able to use what windows uses to get online, and apply what you learn to the separate linux setup.
Uninstalling is just as easy as installing, should you so desire.

The package manager synaptic, has the option in prefs/files to keep
downloaded packages (they have a .deb extension.)
Then installing apps, or re-installing them, will leave them in

/var/cache/apt/archives  where you can retrieve them for later manual
installation elsewhere. Google up a wubi or mint4win page, and have some coffee :guitar:

Cheers

---

### Post by chugtairizwan on 2012-04-18
Window 7 must be installed when you want to install Ubuntu.and have to accommodate space for our Ubuntu installation. To this end,use the GParted partitioning tool to resize (shrink) the Windows installation and create new partitions for Ubuntu.:)

---

