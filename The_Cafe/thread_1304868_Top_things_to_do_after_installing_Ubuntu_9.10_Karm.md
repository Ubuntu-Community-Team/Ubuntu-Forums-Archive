---
title: "Top things to do after installing Ubuntu 9.10 Karmic Koala"
date: 2009-10-29
forum: The Cafe
---

### Post by DPic on 2009-10-29
[SIZE="4"]Hey guys, i put a lot of time and effort into writing this and i thought you might like it =][/SIZE]

[SIZE="6"]**[Top things to do after installing Ubuntu 9.10 Karmic Koala]("http://www.reddit.com/tb/9z2xk/")**
Please [Reddit]("http://www.reddit.com/r/linux/comments/9z2xk/top_things_to_do_after_installing_ubuntu_linux/")/[Digg]("http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2") and [(re)Tweet]("http://twitter.com/DPic/status/5279345397")/[Identi.ca]("http://identi.ca/notice/13282964")![/SIZE]

[SIZE="4"]Please let me know what you think![/SIZE]

[SIZE="5"]**Edit:** Wow! Thank you all so much for all the positive comments-- this really makes it worth it =] I'm trying really hard to get this up on [reddit]("http://www.reddit.com/r/linux/comments/9z2xk/top_things_to_do_after_installing_ubuntu_linux/")/[digg]("http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2") so upvotes and [(re)tweets]("http://twitter.com/DPic/status/5268183056") ([or identi.ca]("http://identi.ca/notice/13253178")) are GREATLY appreciated!

**Edit2:**The response to this post has been seriously overwhelming. I am taking criticisms and feedback into consideration and making appropriate fixes. 

I was really hoping i could get this to the frontpage of digg (even though we all know reddit is better), so i promise this is the last time i'll mention this: if anyone doesn't mind promoting this for me, it'd be greatly greatly appreciated! [http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2](http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2)[/SIZE]

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-29
Great!

---

### Post by ViRMiN on 2009-10-29
Wow, you found a lot of good stuff to do after installing 9.10!  You can tell you spent a lot of time doing what you've done alone, nevermind documenting it too!  Well done.

---

### Post by clancymf on 2009-10-29
Using Ubuntu for 2 years and alot of those were new to me.

---

### Post by jolure1 on 2009-10-29
I appreciate sharing so many tips about 9.10. Thanks.

---

### Post by nothingspecial on 2009-10-29
That is a great write up and I`m going to link it in my sig.

Cheers

---

### Post by rfruth on 2009-10-29
[SIZE="5"]tnx ![/SIZE]

---

### Post by dylan_newb on 2009-10-29
nice!!

---

### Post by andymorton on 2009-10-29
It's great. Thanks for posting it. :D:D

---

### Post by hoppipolla on 2009-10-29
That really is very, very good. I have been using Ubuntu and Linux for years and you've taught me a fair few tricks there!

Well done man! :)


Tweeted, and bookmarked on Delicious! :D

---

### Post by blur xc on 2009-10-29
Bookmarked-

Thanks!
BM

---

### Post by malimrav on 2009-10-29
> **hoppipolla said:**
> That really is very, very good. I have been using Ubuntu and Linux for years and you've taught me a fair few tricks there!

Well done man! :)


Tweeted, and bookmarked on Delicious! :D


This is another version of to-do after install for Karmic Koala x86_64:

1 &#8211; Expand the Software Repository List

sudo gedit /etc/apt/sources.list

CLEAR FIELD AND COPY THE LINES BELOV:


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) karmic main
deb [http://archive.getdeb.net/getdeb/ubuntu](http://archive.getdeb.net/getdeb/ubuntu) karmic-getdeb apps games
deb [http://ppa.launchpad.net/stani/ppa/ubuntu](http://ppa.launchpad.net/stani/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/lure/ppa/ubuntu](http://ppa.launchpad.net/lure/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/lure/ppa/ubuntu](http://ppa.launchpad.net/lure/ppa/ubuntu) karmic main 
deb [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

sudo apt-get update

IF SOME KEY MISSING THEN TYPE TH EFOLLOOWING COMMAND:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEYNUMBER
(replace KEYNUMBER with nubers)

sudo apt-get update


2. sudo apt-get install ubuntu-tweak gnome commander

Run ubuntu-tweak from Applications-System tools- Ubuntu-Tweak and from third party sources enable the following:
-Chromium, Empathy, Google, Google testing,Medibuntu,Mplayer, Opera,Tomboy, SMPlayer, Transmission stable, Ubuntu Mozilla Security Team,Ubuntu Tweak, Ubuntu X, 

Refresh list

3.Essential tools for compiling from sources

sudo apt-get install build-essential checkinstall cdbs devscripts dh-make fakeroot libxml-parser-perl check avahi-daemon

4.Nice Right Click Sub-Menus, Gedit,ccsm,cabextract and archivers

sudo apt-get install nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-collection-svn nautilus-script-manager nautilus-sendto nautilus-share nautilus-wallpaper unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller xarchiver glipper parcellite simple-ccsm gedit gedit-plugins

5. Restricted Extras
sudo apt-get install ubuntu-restricted-extras equivs

6.Multimedia
sudo apt-get install libxine1-ffmpeg mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0 icedax tagtool easytag id3tool lame libmad0 libjpeg-progs flac faac faad sox ffmpeg2theora flac libmpeg3-1 mpeg3-utils mpegdemux liba52-dev non-free-codecs totem-xine libxine1-all-plugins libxine1 libdmx1 libavifile-0.7c2 w64codecs libdvdcss2

7.More Multimedia
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer gstreamer-dbus-media-service gstreamer-tools

8.Partition Editor, Media Players, GIMP Plugins, Audio Editors,CD Ripper, DVD ripper, Download Manager, Inkscape, Xara Extreme, SK1 (Corel Draw Replacement, open .cdr files), CD & DVD Cataloging Program, Digikam, Showfoto, PDF Printer, Webcam viewer..........


sudo apt-get install gparted ntfsprogs mplayer-nogui smplayer vlc mozilla-plugin-vlc gimp-plugin-registry gimp-data-extras gimp2.0-quiteinsane gtkam-gimp gimp-gap gscan2pdf thunderbird realplayer filezilla filezilla-common sound-juicer googleearth inkscape skanlite ufraw gimp-ufraw digikam showfoto gtkvncviewer gthumb audacity gkrellm gkrellm-ibam ibam gkrellweather qcad xaralx dia-gnome blender cdcat alien cmake glabels scribus gwget libqt4-gui fuseiso cdrdao gnupg-agent gnupg2 pinentry-qt4 libksba8 libqt4-assistant isomaster dvgrab kino libreadline5 mjpegtools libwxsvg0 xine-ui cheese gnome-photo-printer pdfedit tcl8.5 tk8.5 python-imaging python-imaging-tk python-liblcms python-reportlab devede dvdisaster dvdrip avidemux dvdstyler dvdstyler-data cheese cups-pdf acetoneiso

!! You should make shotcuts-launchers for Cd & DvD cataloging program, the command for run is: cdcat, and for SK1(Corel), the command is sk1

9. Extra Fonts
sudo apt-get install ttf-dustin ttf-georgewilliams ttf-sjfonts ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon msttcorefonts ttf-freefont

10. Flash Player 64 bit
Download the file from here -
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
and extract it. You should get a file called "libflashplayer.so". If you
don't, make sure you downloaded it right.



sudo apt-get remove --purge flashplugin-nonfree

sudo apt-get remove flashplugin-installer

sudo apt-get remove --purge swfdec-mozilla

sudo cp ~/Downloads/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

well, that`s it, i hope i help!!

---

### Post by phrostbyte on 2009-10-29
Or all in one script:

```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xzvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
sudo mv libflashplayer.so /usr/lib/mozilla/plugin/libflashplayer.so

```

This *should * automatically download, extract, and install the alpha (yet far more stable) 64-bit flash player. I will admit that I did not test it though :\

---

### Post by phrostbyte on 2009-10-29
Anyone that's a really good guide and I commend your substantial effort on it. =D>

---

### Post by A_M_S on 2009-10-29
When i decide to install karmic i will use your tips.

Tnx.

---

### Post by andrew.46 on 2009-10-29
Great work, best post-installation guide I have ever seen!!!

Andrew

---

### Post by DodgeV83 on 2009-10-29
Great stuff!

For the record, however, it **is** possible to play WMA9 and even WMA 9 PRO 5.1 in Ubuntu 9.10

Install the SVN MPlayer with the instructions from this thread

[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

I was able to play some WMV VC-1 videos with 5.1 WMA9 Pro audio without issue :)

It's better than directing people to download illegal software right? ;)

---

### Post by andrew.46 on 2009-10-29
Hi Dodge,

> **DodgeV83 said:**
> 
Install the SVN MPlayer with the instructions from this thread

[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)


That thread has been closed along with all the testing section for Karmic Koala but the good news is that I have tested the guide under the release version and it runs very well. So I have just 10 minutes ago submitted the guide to the 'Tutorials and Tips' section where it should appear after moderation.

Andrew

---

### Post by sickly on 2009-10-29
nice one!

---

### Post by Ric_NYC on 2009-10-29
Congratulations! Amazing work, DPic.

---

### Post by dj-toonz on 2009-10-29
1) get the system how you want it :)
2) wait for the updates to start coming in ::D
3) wait till lynx 10.4 alpha comes out & start all the testing all over again ::D

like now :P

 f-spot fuse-utils grub-common grub-pc libfuse2 libpython2.6 libsmbclient
  libwbclient0 python2.6 python2.6-minimal samba-common samba-common-bin
  smbclient totem totem-common totem-mozilla totem-plugins update-manager

first lot

---

### Post by OpenGuard on 2009-10-29
Top quality content .. might be handy - thnx :)

---

### Post by bonfire89 on 2009-10-29
that is pretty freakin' awesome! I am definitely going to be making use of this!

---

### Post by fiona-conn on 2009-10-29
Hey, any idea what happened to the Flying Toasters screensaver? That seems to be missing from the screensaver list on my install, and any idea how to get it back?

---

### Post by PC_load_letter on 2009-10-29
Just voted, great stuff! Thanx DPic.

---

### Post by Plumtreed on 2009-10-29
Thanks, that is really excellent and how much work did you do?

That really is magic and you deserve a 'star':KS

---

### Post by Aemaeth on 2009-10-29
Roger that! 

  In the mix 5x5. Nice way to put a shine on the ol english there. This should mix things up a bit for the average jo. Rather inspiring id say, I think ill do something like this for the server edition, but this will be a hard act to follow...

---

### Post by whitefang5412 on 2009-10-29
Absolutely wonderful! I borked my 8.04 installation on my desktop and now I have a very good reason to install 9.10 and do some tweeks on it with the guide you posted! It's been bookmarked!

---

### Post by JillSwift on 2009-10-29
Color me impressed. Seriously. That's fab stuff.

---

### Post by ZombiesNTea on 2009-10-29
I'm not very saavy with programming or anything... what do you do with the stuff you label after "ATP Line" ?

---

### Post by OpenGuard on 2009-10-29
> **ZombiesNTea said:**
> I'm not very saavy with programming or anything... what do you do with the stuff you label after "ATP Line" ?

Paste it in the terminal ( Applications -> Accessories -> Terminal ).

---

### Post by ZombiesNTea on 2009-10-29
> **OpenGuard said:**
> Paste it in the terminal ( Applications -> Accessories -> Terminal ).

Thanks!

---

### Post by OpenGuard on 2009-10-29
> **ZombiesNTea said:**
> Thanks!

S***, I was wrong ( you are talking about software sources list, not the process of installing something, right ? ) .. Open System -> Administration -> Software sources and under the tab Other, click Add and paste it in.

---

### Post by jondecker76 on 2009-10-29
Thanks - this is a great list!

---

### Post by mustang on 2009-10-30
Cool list! Going to go back to this thread when I install Ubuntu over the winter break!

---

### Post by cptnazeroth on 2009-10-30
Very awesome. I Digg'd it. :)

---

### Post by DPic on 2009-10-30
Thanks everyone! You guys are great xD

---

### Post by Falc7 on 2009-10-30
I've install gnaural, but it dosen't seem to be in my menu anywhere (using kubuntu), can you help? I've tried typing gnaural in the search box but it dosen't find anything

---

### Post by kevdog on 2009-10-30
Good list however I wish you would at least put a list in each appropriate section of alternative software.  Towards the end of the review I kind of felt like you were just describing software you like to use.  

A lot of work put into that article.  I wish we had a lot more contributions like these.

---

### Post by bonfire89 on 2009-10-30
what is the difference between building gnome shell myself or using the apt-get command?

---

### Post by blur xc on 2009-10-30
> **bonfire89 said:**
> what is the difference between building gnome shell myself or using the apt-get command?

I'm no expert, but I think if you build it yourself you are getting the latest and greatest, while what's in the repo's are usually a bit behind.

then of course, if you build it yourself, I don't think you get automatic updates, like you would if you got it from the repo's...  but I may be wrong...

BM

---

### Post by drawkcab on 2009-10-30
Absolutely fantastic write-up.  Canonical should hire you immediately!

Anyway, I followed a few of your suggestions (thanks!) and I will share your article.

---

### Post by phend-one on 2009-11-03
Thank you so much for your contribution. It's been such a great help to get everything up and running, especially flash. ;)

---

### Post by Nerd King on 2009-11-08
First thing I did was install Arch.. then get a little fed up of it and go back to 9.04. Stability for the win.

---

### Post by Exodist on 2009-11-08
> **DPic said:**
> [SIZE=4]Hey guys, i put a lot of time and effort into writing this and i thought you might like it =][/SIZE]

[SIZE=6]**[Top things to do after installing Ubuntu 9.10 Karmic Koala]("http://www.reddit.com/tb/9z2xk/")**
Please [Reddit]("http://www.reddit.com/r/linux/comments/9z2xk/top_things_to_do_after_installing_ubuntu_linux/")/[Digg]("http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2") and [(re)Tweet]("http://twitter.com/DPic/status/5279345397")/[Identi.ca]("http://identi.ca/notice/13282964")![/SIZE]

[SIZE=4]Please let me know what you think![/SIZE]

[SIZE=5]**Edit:** Wow! Thank you all so much for all the positive comments-- this really makes it worth it =] I'm trying really hard to get this up on [reddit]("http://www.reddit.com/r/linux/comments/9z2xk/top_things_to_do_after_installing_ubuntu_linux/")/[digg]("http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2") so upvotes and [(re)tweets]("http://twitter.com/DPic/status/5268183056") ([or identi.ca]("http://identi.ca/notice/13253178")) are GREATLY appreciated!

**Edit2:**The response to this post has been seriously overwhelming. I am taking criticisms and feedback into consideration and making appropriate fixes. 

I was really hoping i could get this to the frontpage of digg (even though we all know reddit is better), so i promise this is the last time i'll mention this: if anyone doesn't mind promoting this for me, it'd be greatly greatly appreciated! [http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2](http://digg.com/linux_unix/Top_things_to_do_after_installing_Ubuntu_9_10_Karmic_Koala_2)[/SIZE]


Wow really big wall of text.. I feel so small now.. /cry

---

### Post by winjeel on 2009-11-08
That's an awesome list. Thanks.

---

### Post by Retrograde77 on 2009-11-08
Thats the article I used to install things after updating to Karmic.  Fantastic stuff, cheers for that :KS

---

### Post by shuttleworthwannabe on 2009-11-09
Great help! I have recommended this site to many fellows here in South Africa!

as an aside, I have also found ubuntu-tweak.com very helpful for someone who is scared of command line, and installing without browsing repo's not listed on the Ubuntu default sources.

Ta,
S

---

### Post by LequidMetal on 2009-11-27
Didnt expect to see such a comprehensive write-up when i clicked your blog link ! great article , keep it up .

---

### Post by NoaHall on 2009-11-27
How about removing pulse and using pure alsa?

---

### Post by DPic on 2009-12-12
I'm still getting tons of views on this post =]

Thanks for all the feedback, there will be a number of changes if and when i make one for Lucid!

---

