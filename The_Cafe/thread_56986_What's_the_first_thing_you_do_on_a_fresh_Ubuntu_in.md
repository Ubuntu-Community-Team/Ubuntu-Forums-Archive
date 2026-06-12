---
title: "What's the first thing you do on a fresh Ubuntu install?"
date: 2005-08-14
forum: The Cafe
---

### Post by c-m on 2005-08-14
I've decided that my hard drive is in a terrible state with a mixture of reiserfs, vfat and ntfs partitions. 

Anyway i'm going to complete a fresh install tomorrow on an 80gb drive. I was just wondering what is the first thing that **you** do on a fresh install?

 :razz:

---

### Post by wellery on 2005-08-14
I have a mixture of reiserfs, vfat and ntfs partitions aswell but i don't have a problem with it. I usually run updates after i install just to make sure i have all the latest security fixes. After that i setup lots of things in no particular order including the fstab, printer, autologin, mouse (side buttons), autologin,  applications using the extra repositories which are at th ubuntu guide.

---

### Post by RastaMahata on 2005-08-14
Mount my external drive, import my files, including my asoundrc and sources.list
install my asoundrc, disable esd, restart alsa
install the gnome clipboard daemon, the num lock daemon
update my sources.list, go to synaptic, remove evolution, install: flashplayer-mozilla evince sun-j2sdk1.5 libdvdcss2 leafpad gstreamer-mad gstreamer-plugins
totem-xine w32codecs serpentine rar unrar nvidia-glx
Leave it updating and installing for the night
Wake up, "sudo nvidia-glx-config enable", edit xorg.conf and disable dri, restart xorg, login and check everything, restart whole system (freshness effect ;))

---

### Post by aysiu on 2005-08-14
1. Well, first I edit my /etc/X11/xorg.conf to get the proper VertRefresh and HorizSync ranges in.
2. I enable extra repositories.
3. I get all the updates/upgrades I need.
4. I get Firefox from Mozilla (yes, I prefer it to the Ubuntu Firefox)
5. I get Thunderbird from Mozilla 
6. I copy back my .mozilla and .thunderbird settings from backup.
7. I copy back my themes and wallpapers from backup.
8. I get my multimedia codecs.

Of course, everyone has her own process...

---

### Post by xequence on 2005-08-14
Make sure everything is working right then...

- Get my music and other files off my mp3 player
- Update firefox and/or everything else
- Customize the look

---

### Post by kvidell on 2005-08-14
It's been awhile but last time I did a fresh Ubuntu install I ran Ubuntu-Geek's whizzy-script, sans a few repositories and installed items... then I clean up the sound system, install a few custom things I like here and there, do any kernel changes I need then reboot it and let it hang out and use as needed :)

- Kev

---

### Post by super on 2005-08-14
first thing i do on a fresh install?
mp3/w32codecs

makes everthing that follows a heck of a lot more enjoyable  :razz:

---

### Post by crane on 2005-08-14
Install install quake3........play quake3..........surf the forums :)

---

### Post by Ubunted on 2005-08-14
- Un-mute my Audigy 2 in alsamixer
- Switch to Clearlooks
- Add backports
- Updates
- Swap kernels for the k7
- Install nvidia drivers, Firestarter, Flash, Java, media codecs, browser plugins, xine, Thunderbird, Azureus, gnomebaker, etc etc etc...
- Rebuild my Firefox bookmarks, preferences and extensions
- Get Folding@Home running

---

### Post by BWF89 on 2005-08-14
When I was allowed to duel-boot with Fedora Core 2 back in December the first thing I did was:

-Customise the Start button bar by adding and removing buttons & features
-Download the Firefox .tar and install it
-Put some sites in my favorite places
-Register my AIM account on GAIM

---

### Post by earobinson on 2005-08-21
hit up this site

---

### Post by qalimas on 2005-08-21
1. enable all repositories
2. update everything
3. the add-on cd, to take care of java, codecs, azureus, etc, etc
4. run updates again, to make sure everything the add-on cd installed is updated
5. download the nvidia drivers and enable glx
6. customize the look and feel
7. install anything i may have missed thats important
8. install a few games

---

### Post by darkmatter on 2005-08-21
Install as server, edit sources.list, update, install X, E 17, full media support, browsers, irssi, etc. update rc.d, setup my iptables. The list goes on.

Oh...I also install the most robust OS there is. Emacs. :-P

---

### Post by thecrimsonking on 2005-08-21
install KDE.

---

### Post by cowlip on 2005-08-21
I get rid of the top gnome panel bar, and sometimes instal KDE :)

---

### Post by Lovechild on 2005-08-21
1) remove Openoffice.org as it is a monstrousity and replace it with Abiword and GNUmeric
2) replace firefox with epiphany (I want an integrated desktop)
3) remove gnomemeeting
4) remove *sane
5) install skype and libqt3-mt (need to be able to call my gf)
6) remove eog
7) change theme to standard clearlooks using human or bluecurve icons

---

### Post by Stormy Eyes on 2005-08-21
[QUOTE=c-m]I was just wondering what is the first thing that **you** do on a fresh install?[/QUOTE]

1. Install Openbox.
2. Configure my system to use pure ALSA. ESD sucks. OSS sucks, aRts sucks. Only ALSA works well enough with my Audigy to please me.

---

### Post by jyank on 2005-08-21
This isn't specific to Ubuntu, because I've only had to install it once, but when I'm trying out a distro I usually:

1)Mount my NTFS drive and set it mount at boot
2) Download audio codecs
3)Get my playlist going
4)Mess with theme/updating files

---

### Post by skoal on 2005-08-21
Great topic.  Fresh, funky, and informative.  Informative since the very question infers "must haves" _before_ a fresh install, like:
> skoal@morpheus:///media/cdrom/data/backup $ ls
apt-sources.tar.gz  doom3         rc5.tar.gz    xorg.tar.gz
blacklist.tar.gz    fonts.tar.gz  skoal.tar.gz
With the exclusion of the non-essential 'doom3' savedgames folder, you can see that everything else I saved from a prior Ubuntu install is ready to go for the fresh and funky new one.  I can pick up right where I left off.  So, to answer your question, the very first thing I do is reinstall these mighty essential backup files...

Great question!  Mod parent +5 funky fresh cold medina

\\//_

---

### Post by bored2k on 2005-08-21
Put everything black.
Update SOME packages
Get BitTornado running

---

### Post by sapo on 2005-08-21
[QUOTE=xequence]Make sure everything is working right then...

- Get my music and other files off my mp3 player
- Update firefox and/or everything else
- Customize the look[/QUOTE]

sure... you dont have to reboot to install every single app.. so the mp3 keeps rockin on the background [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

---

### Post by Arktis on 2005-08-22
1.) Update with synaptec.

2.) Download the most optimal precompled kernel.

3.) Download additional software packages needed for compiling things from source.

3.) Install 3d graphics drivers.

5.) Install MPlayer.

6.) Perform a large ammount of minor tweaks and customizations, and remove unwanted software packages.

---

