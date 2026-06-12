---
title: "Debian SID Respositores in Ubuntu"
date: 2005-08-11
forum: Ubuntu Backports
---

### Post by xbaez on 2005-08-11
Well I installed the debian SID repositories in Ubuntu

#Debian
/etc/apt/sources.list
deb [ftp://ftp.us.debian.org/debian](ftp://ftp.us.debian.org/debian) unstable main contrib non-free #Sid

# mplayer
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main #Multimedia

I went to synaptic, and told it to prefer the latest versions always

Now I'm downloading linux-image-2.6.12 as well as eclipse (both of them, were not in Ubuntu)

I had to update initrd-tools though


My question is

1) Is Debian SID better than Ubuntu or the other way around?
2) Am I going to break my system?

---

### Post by AndyAWS on 2005-08-11
1) I don't know  :???: 

2) Probably  [-X

---

### Post by Mez on 2005-08-12
1) Sid is more unstable than ubuntu, and etch would probably be the same "quality" as breezy is

2) Yes, there are incompatibilities between ubuntu and debian as we have been doing transitions at different times to debian, for example, the gcc4 transition. This means that debian packages are binary incompatible with ubuntu, so unless you're building things from source, then you will break your system... and if you are building from source, you're going to have some problems anyway

---

### Post by xbaez on 2005-08-12
Well Mez I see from your **we have been doing transitions...** that you're part of the Ubuntu team right?

Well let me tell you something

I was in love with Ubuntu, awesome distro.
Then one day, Samba broked, really, I can't check my shares, not even from my local PC

What should I do in this cases?
I mean part of Ubuntu's 'magic' is its great support, but I suppose that some package from the repositories (I use backports) broked samba

Here is the link to my samba post:
[http://www.ubuntuforums.org/showthread.php?t=48205](http://www.ubuntuforums.org/showthread.php?t=48205)

Here is the list of packages that I installed, the day in which I remember was the last day in which Samba worked:

Commit Log for Tue Aug  9 07:42:18 2005


Removed the following packages:
gnome-volume-manager
gwget
hplip-base
hplip-data
mplayer-386

Installed the following packages:
3ddesktop (0.2.7-1ubuntu1)
acidrip (0.14-0.0)
aegis-virus-scanner (0.1.0-1)
alsaplayer (0.99.76-0.2ubuntu2)
alsaplayer-alsa (0.99.76-0.2ubuntu2)
alsaplayer-common (0.99.76-0.2ubuntu2)
alsaplayer-daemon (0.99.76-0.2ubuntu2)
alsaplayer-esd (0.99.76-0.2ubuntu2)
alsaplayer-gtk (0.99.76-0.2ubuntu2)
alsaplayer-nas (0.99.76-0.2ubuntu2)
alsaplayer-oss (0.99.76-0.2ubuntu2)
alsaplayer-xosd (0.99.76-0.2ubuntu2)
amavis-stats (0.1.12-5)
amavisd-new (20030616p10-5)
amavisd-new-milter (20030616p10-5)
analog (2:5.32-12ubuntu1)
apache2-threaded-dev (2.0.53-5ubuntu5.2)
apt-doc (0.6.35ubuntu2)
apt-howto-en (1.8.10.1-2)
aptconf (0.8)
asterisk-chan-capi (0.3.5-8)
asterisk-dev (1:1.0.6-2)
asterisk-gtk-console (1:1.0.6-2)
asterisk-h323 (1:1.0.6-2)
asterisk-web-vmail (1:1.0.6-2)
atari800 (1.3.2-1)
atop (1.14-1)
awstats (6.3-1)
bacula (1.36.1-1)
bacula-client (1.36.1-1)
bacula-common (1.36.1-1)
bacula-console (1.36.1-1)
bacula-director-common (1.36.1-1)
bacula-director-sqlite (1.36.1-1)
bacula-fd (1.36.1-1)
bacula-sd (1.36.1-1)
bash3 (3.0-10)
bash3-doc (3.0-10)
basket (0.5.0-1~5.04ubp1)
bastille (1:2.1.1-11)
bchunk (1.2.0-1)
beep-media-player (0.9.7-1ubuntu1)
bindgraph (0.1-2)
bittornado (0.3.12-4~5.04ubp2)
bittornado-gui (0.3.12-4~5.04ubp2)
bkp (0.5.2-1)
bmp-skins (0.1-2~5.04ubp1)
cdrtoaster (1.12-2)
checksecurity (2.0.7-1)
debconf-doc (1.4.42ubuntu4)
debian-goodies (0.23)
dgen (1.23-6)
dh-buildinfo (0.8)
dh-consoledata (0.7.48ubuntu2)
dhcp3-server (3.0.1-1ubuntu4)
divx4linux-dev (5.0.1-1~5.04ubp1)
dnstracer (1.8-1)
doc-linux-html (2004.11-1)
doc-linux-text (2004.11-1)
dosemu (1.2.1-3)
drip (0.8.3.2+0.9.0-rc3-5)
eroaster (2.2.0-0.8-2ubuntu1)
esound-clients (0.2.35-2ubuntu2)
faac (1.24-0.0)
fast-user-switch-applet (0.2.2-0ubuntu1~5.04ubp1)
festival (1.4.3-16)
festlex-cmu (1.4.0-6)
festlex-poslex (1.4.0-5)
festvox-kallpc16k (1.4.0-5)
filelight (0.6.4.1-1)
flac (1.1.1-4)
gcc-3.3-doc (1:3.3.5-8ubuntu2)
gngeo (0.6.4-1)
gngeogui (0.1-2)
gnoise-gnome (0.1.15-4)
gnome-blog (0.7-4ubuntu1)
gnome-user-share (0.4-1)
gnopernicus (0.10.5-0ubuntu1)
gnuboy-sdl (1.0.3-1)
gnuboy-svga (1.0.3-1)
gnuboy-x (1.0.3-1)
gnumeric-doc (1.4.3-6ubuntu1~5.04ubp1)
gnumeric-plugins-extra (1.4.3-6ubuntu1~5.04ubp1)
gnuplot (4.0.0-2)
gnuplot-nox (4.0.0-2)
gnuplot-x11 (4.0.0-2)
gok (1.0.3-0ubuntu1)
googlizer (0.3-2)
gpaint (0.2.4+0.3.0pre4-1)
graveman (0.3.12-4-2~5.04ubp1)
grisbi (0.5.3-1)
grub-doc (0.95+cvs20040624-14ubuntu2)
grub-splashimages (1.0)
gsnes9x (3.12-6)
gtk2-engines-gtk-qt (0.60-1ubuntu1)
gtkpod-aac (0.88.1-0.0~5.04ubp1)
gtktalog (1:1.0.4-2)
gtoaster (0.2002083100+1.0Beta6-2.1)
guitar (0.1.4-10.1)
gwget2 (0.7-3.1ubuntu1)
hardware-monitor (1.2-1.1ubuntu1)
hpoj (0.91-3ubuntu4)
hpoj-xojpanel (0.91-3ubuntu4)
htmldoc (1.8.23-1.2)
k3b-i18n (0.11-2)
kaquarium (1.0-beta-3)
kcd (0.1.3.1-6)
kcdlabel (2.12-KDE3-2)
kcheckgmail (0.5.0-1)
kcpuload (1.99-8)
kdiff3 (0.9.87-1ubuntu1)
keybled (0.65-1)
kfish (2.01-5)
kfocus (1.0.2-13)
knapster2 (0.5-4)
knemo (0.3.1-2ubuntu1)
knetload (2.3-2)
kompose (0.5-2)
konq-speaker (0.4-kde3.1-7)
konversation (0.18-1ubuntu1~5.04ubp2)
korn (4:3.4.0-0ubuntu10)
kphone (1:4.0.5-2)
kubuntu-desktop (0.40)
kurush (0.11-1)
kwave (0.7.2-2ubuntu1)
lame-extras (3.96.1-1)
libapr0-dev (2.0.53-5ubuntu5.2)
libarchive-tar-perl (1.22-1)
libarchive-zip-perl (1.14-1)
libatspi1.0-0 (1.6.3-0ubuntu1)
libcapi20-2 (1:3.6.2005-01-03-4ubuntu1)
libcdaudio0 (0.99.9-2ubuntu0.2)
libcdio0 (0.68-2)
libcln3 (1.1.9-1)
libcompress-zlib-perl (1.33-3)
libconfig-inifiles-perl (2.38-3)
libconvert-tnef-perl (0.17-4)
libconvert-uulib-perl (1.0.3-2)
libcurses-perl (1.08b-1)
libdb4.2-dev (4.2.52-17ubuntu1)
libestools1.2c102 (1:1.2.3-8)
libfile-mmagic-perl (1.22-1)
libfile-scan-perl (1.38-1)
libgail-gnome-module (1.1.0-1)
libgconfmm-2.6-1 (2.10.0-0ubuntu1)
libglademm-2.4-1 (2.6.0-0ubuntu1)
libgnome-mag2 (1:0.12.0-0ubuntu1)
libgnome-speech3 (1:0.3.6-1)
libgnome-vfsmm-2.6-1 (2.10.0-0ubuntu1)
libgnomecanvasmm-2.6-1 (2.10.0-0ubuntu1)
libgnomemm-2.6-1 (2.10.0-0ubuntu1)
libgnomeuimm-2.6-1 (2.10.0-0ubuntu1)
libgtk-imlib-perl (0.7009-1.1)
libgtk2-gladexml-perl (1.001-1)
libhowl0 (0.9.8-2)
libicu28 (2.8-4)
libio-multiplex-perl (1.08-1)
libio-zlib-perl (1.04-1)
libiso9660-0 (0.68-2)
libldap2-dev (2.1.30-3ubuntu3.1)
libnet-perl (1:1.19-1)
libnet-server-perl (0.87-2)
libsp1 (1.3.4-1.2.1-43)
libticables3 (3.8.7-1)
libticalcs4 (4.5.5-1)
libtifiles0 (0.6.1-2)
libunix-syslog-perl (0.100-4)
libvcdinfo0 (0.7.20-2ubuntu1)
libwine-cil (0.3-4)
libwine-dev (0.0.20050419-1~5.04ubp1)
libwine-gl (0.0.20050419-1~5.04ubp1)
libwine-nas (0.0.20050419-1~5.04ubp1)
libwine-print (0.0.20050419-1~5.04ubp1)
libwine-twain (0.0.20050419-1~5.04ubp1)
libwxgtk2.5.3-python (2.5.3.2ubuntu4)
libxml-grove-perl (0.46alpha-11)
libxml-perl (0.08-1)
linux-doc (2.6.10-7)
linux-doc-2.6.10 (2.6.10-34.3)
linux-k7 (2.6.10-7)
linuxdoc-tools (0.9.21)
linuxdoc-tools-info (0.9.21)
linuxlogo (4.09-1)
lsdvd (0.10-0.0)
magicdev (1.1.6-2)
mail-notification (1.1-3~5.04ubp1)
mailman (2.1.5-7)
make-doc (3.80-9)
mdnsresponder (0.9.8-2)
memprof (0.5.1-9)
modutils (2.4.26-1ubuntu3)
mplayer-k6 (1:1.0-pre6-0.3ubuntu6)
mplayer-k7 (1:1.0-pre6-0.3ubuntu6)
mrproject (0.13-0.4~5.04ubp1)
mypasswordsafe (0.0.20041004-2build1~5.04ubp1)
nautilus-open-terminal (0.2-1ubuntu1~5.04ubp1)
nestra (0.66-7)
netmon-applet (0.4-9)
netspeed (0.10-2ubuntu3)
nvidia-glx-dev (1.0.7174-0ubuntu1)
ogle-mmx (0.9.2-2)
okle (0.4+cvs20040727-3)
openoffice.org-evolution (1.1.3-8ubuntu2.3)
openoffice.org2-evolution (1.9.79.2-0ubuntu2)
perl-suid (5.8.4-6ubuntu1)
pxlib1 (0.4.3-1)
python-gnome2-extras (2.10.0-0ubuntu1)
python2.4-gnome2-extras (2.10.0-0ubuntu1)
qalculate (0.7.1-1)
quick-lounge-applet (2.9.1-0ubuntu2)
quick-reference-en (1.07-18)
quick-reference-es (1.07-18)
raidtools2 (1.00.3-17ubuntu1)
raidutils (0.0.4-4)
rcalc (0.3.99-4)
revelation (0.4.3-1~5.04ubp1)
rhythmbox-applet (0.1.7-1~5.04ubp1)
screem (0.12.1-1ubuntu1)
selinux-doc (1.14-1)
selinux-utils (1.18-3)
serpentine (0.6.1-0ubuntu1~5.04ubp1)
siege (2.60b1-4)
snes9express (1.42-2)
snes9x-common (1.42-2)
snes9x-opengl (1.42-2)
snes9x-x (1.42-2)
sp (1.3.4-1.2.1-43)
sqlite (2.8.15-3)
squid-cgi (2.5.8-3ubuntu1.2)
squid-prefetch (1.0-1)
squidclient (2.5.8-3ubuntu1.2)
squidguard (1.2.0-5)
ssh-askpass-fullscreen (0.3-1)
stars (0.12+1-1)
stella (1.4.1-1)
texinfo (4.7-2.2ubuntu1)
tiemu (1.65-6)
ubuntu-calendar-december (4.12)
ubuntu-calendar-february (5.02)
ubuntu-calendar-january (5.01)
ubuntu-calendar-march (5.03)
ubuntu-calendar-november (4.11)
ubuntu-calendar-october (4.10)
udftools (1.0.0b3-9)
vcdimager (0.7.20-2ubuntu1)
webmin-bandwidth (1.210a-2~5.04ubp1)
webmin-dhcpd (1.210a-2~5.04ubp1)
webmin-tunnel (1.210a-2~5.04ubp1)
whowatch (1.6.0-5)
wwwstat (2.0-2)
wxpython2.5.3 (2.5.3.2ubuntu4)
xcdroast (0.98+0alpha15-1.1)
xfce (3.8.18-2ubuntu1)
xlogmaster (1.6.0-8)

So what I am saying is that I've heard comments that Debian is really stable, even if you use Mepis, and download stuff from the 'testing' and 'unstable' repositories

I really dislike to have a 'perfect' distro, and from one day from another (I even tried reinstalling samba, installing previous versions...) samba stops working at all

---

### Post by jobezone on 2005-08-12
[QUOTE=Mez]1) Sid is more unstable than ubuntu, and etch would probably be the same "quality" as breezy is

2) Yes, there are incompatibilities between ubuntu and debian as we have been doing transitions at different times to debian, for example, the gcc4 transition. This means that debian packages are binary incompatible with ubuntu, so unless you're building things from source, then you will break your system... and if you are building from source, you're going to have some problems anyway[/QUOTE]
 I was using Testing(etch), and a week ago I switched to Unstable. The system has been very stable. I'm actually surprised at it, the X.Org transition went smoothly, the udev installation, etc. installed and are funcioning fine.

---

### Post by xbaez on 2005-08-12
So what is the correct way to use Debian?

Should I download the entire 2 DVD Sid release, then download the Testing (etch) and then download sid?

I don't know but from my experience Debian is the most difficult distro to install

When I tested the previous version (woody), it was the absolute only distro (believe me, I've tested a dozen) that wasn't even able to show me a graphical display
Man that was 1980 for me, so I never tested again

Then camed Mepis, amazing, but it's update process was incompatible (from 2004.06 to 3.3)

And then came Ubuntu, everything works fine here

Except that samba broked, I don't know why

However I belive that Debian and the Debian based distros are amazing, the true spirit of open source (plus, the distros that deal better with my hardware, only distros that are able to boot Vmware Workstation 5 with full HD 160GB+ detection)

---

### Post by Velvet Elvis on 2005-08-12
Might I suggest adding as few packages at a single time as possible rather than going through synaptic and choosing packages at random just to see what they do?  If you want to play with something new, install that and just that.  This makes it possible to tell what hosed your system and when.

There is absolutely no reason to add a bazillion packages like you did.  

I'm willing to bet you need to reinstall gnome volume manager btw.

---

### Post by xbaez on 2005-08-12
what is gnome volume manager?

Well from my point of view if you use SuSE 9.2 and install absolutely everything that comes with it, I see no reason for it to brake

Problem here with Ubuntu is that I'm using backports, maybe that was the problem?

---

### Post by Velvet Elvis on 2005-08-12
If you don't know what it is, you shouldn't have removed it.  That's kinda like removing the transmission from your car so that you'll have more room for car stereo gear.

[http://packages.ubuntu.com/hoary/gnome/gnome-volume-manager](http://packages.ubuntu.com/hoary/gnome/gnome-volume-manager)

Universe is ported from the unstable branch of debian and is not official supported.    That means you're taking your chances by using it.  Most stuff there works fine but I've found that there are a few broken packages that can screw up your system.  If you only install one package and its deps at a time, it's easy to see where the problem started and undo it.    

SuSE is a commercial product that costs the better part of $100.  Ubuntu is free.  It's not fair to compare the two.

---

### Post by xbaez on 2005-08-12
From what I know you can download SuSE Professional 9.2 from [www.novell.com/linux](www.novell.com/linux)

And apart from that (believe me), I think that Ubuntu IS better than SuSE

I mean, there is nothing better than apt-get (I've tested many many distros)

The problem right now is that I THINK that the unstable branch of Debian seems more stable than the 'universe' or 'backports' repositories of Ubuntu

I've posted my question at Ubuntuforums, Linuxquestions, read the Samba HowTO, and now I even registered at the Samba lists

Really, I need this machine to work (samba, Vmware, Crossover...) and the worst part is that it was working fine before that update

I went through the entire repository, and checked all the packages. I didn't "randomly" selected the packages, allthough now I recognize that there were too many packages at once.

Any suggestions?

---

### Post by Velvet Elvis on 2005-08-12
Maybe reinstall ubuntu-desktop?

I don't know if there is a dpkg option that would return you to a vanilla ubuntu or not.  If there is, I'd go with that.

---

### Post by AndyAWS on 2005-08-12
You should remove anything that came from debian unstable or debian-marrillat, that would be a good start, there may be incompatabilities there.

Also, as mentioned above, I think you need gnome-volume-manager, I'm not sure why you would want to remove that.

---

### Post by jobezone on 2005-08-12
[QUOTE=xbaez]So what is the correct way to use Debian?

Should I download the entire 2 DVD Sid release, then download the Testing (etch) and then download sid?

I don't know but from my experience Debian is the most difficult distro to install

When I tested the previous version (woody), it was the absolute only distro (believe me, I've tested a dozen) that wasn't even able to show me a graphical display
Man that was 1980 for me, so I never tested again

Then camed Mepis, amazing, but it's update process was incompatible (from 2004.06 to 3.3)

And then came Ubuntu, everything works fine here

Except that samba broked, I don't know why

However I belive that Debian and the Debian based distros are amazing, the true spirit of open source (plus, the distros that deal better with my hardware, only distros that are able to boot Vmware Workstation 5 with full HD 160GB+ detection)[/QUOTE]
 You have 3 choices on installing Unstable:

1 - Get the 1st Sarge CD ([http://www.debian.org/CD/](http://www.debian.org/CD/), (you only need the first really, because most things you need will be in there. Afterwards you can apt-get them). Install it, change the /etc/apt/sources.list file to point to unstable(renaming every "sarge" or "stable" entry to "unstable"), update and dist-upgrade.
2 - You can also install "testing" [http://cdimage.debian.org/pub/cdimage-testing/daily/i386/current/](http://cdimage.debian.org/pub/cdimage-testing/daily/i386/current/) , then upgrade to unstable.
3 - Or use this network install ([http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)), then after being asked to choose the APT mirrors, and choosing them, choose to edit the file by hand, and manually change them to point to "unstable".

... But if you're still very new to linux, I recomend sticking with Ubuntu (or reinstalling it). The main reason is that Ubuntu has some great support here in the forums and just by searching here, you can learn a lot of the system.

---

### Post by Kimm on 2005-08-12
as far as I know, this *might* work, I messed around a bit with debian unstable packages from theis site and updated some software (that acctually did break my system and I ended up having to update a bunch of other packages aswell, my libc6 for example is replaced, along with libgtk2.0-0...) but my system still works. As you acctually added the acctual repository you'll probably get less problems then me... but I cant be completely sure... it'll pretty much not be Ubuntu any more though

---

### Post by jobezone on 2005-08-12
[QUOTE=Kimm]as far as I know, this *might* work, I messed around a bit with debian unstable packages from theis site and updated some software (that acctually did break my system and I ended up having to update a bunch of other packages aswell, my libc6 for example is replaced, along with libgtk2.0-0...) but my system still works. As you acctually added the acctual repository you'll probably get less problems then me... but I cant be completely sure... it'll pretty much not be Ubuntu any more though[/QUOTE]
 I agree, xbaex mixed two different repositories which were never tested or meant to be used together.

---

### Post by xbaez on 2005-08-16
no wait Ubuntu stopped working BEFORE I did those tests
I followed the Ubuntu guide, was using multiverse, universe, and backports

Then I tested that, I had to reinstall anyway

I tested Mepis for a few days
really Ubuntu FEELS better

---

### Post by xbaez on 2005-08-16
I installed 
apt-listbugs and found this:

[B]samba: Security 
 update breaks systems[/B]

Do you think that is why my entire system collapsed?

---

### Post by baustiech on 2005-09-22
[QUOTE=Velvet Elvis]If you don't know what it is, you shouldn't have removed it.  That's kinda like removing the transmission from your car so that you'll have more room for car stereo gear.

[http://packages.ubuntu.com/hoary/gnome/gnome-volume-manager](http://packages.ubuntu.com/hoary/gnome/gnome-volume-manager)

Universe is ported from the unstable branch of debian and is not official supported.    That means you're taking your chances by using it.  Most stuff there works fine but I've found that there are a few broken packages that can screw up your system.  If you only install one package and its deps at a time, it's easy to see where the problem started and undo it.    

SuSE is a commercial product that costs the better part of $100.  Ubuntu is free.  It's not fair to compare the two.[/QUOTE]



-----------------

Actually, you know, I feel that it has nothing to do with price.  The main reason for us here (just outside of washington dc) to take up ubuntu was because, finally, someone did it right and put out a distro that is fast, relatively stable, minimalist and easily maintained.

IMO, Ubuntu is what Redhat long ago tried to be and what Fedora might have been; instead, one went for big money and the other includes everything under the sun, and, to boot, mucks around with tons of unnecessary undercarriage work.

Also, I agree, Debian was gawd-awful in terms of uninstallability due to sheer complexity.  My "basic" installs on Deb resulted repeatedly in literally hundreds of questions before install completed -- for this single, stupid reason, Deb remains, IMO, ridiculously uninstallable.  That one thing, at least for us here, precluded it.

Happily, Ubuntu has swung (probably a wee bit too far, by, for instance, not including sshd in default install) in the opposite direction toward extreme minimalist, yet with everything immediately and expertly available online.

Smooth move.

---

### Post by xbaez on 2005-09-22
[QUOTE=baustiech]-----------------

Actually, you know, I feel that it has nothing to do with price.  The main reason for us here (just outside of washington dc) to take up ubuntu was because, finally, someone did it right and put out a distro that is fast, relatively stable, minimalist and easily maintained.

IMO, Ubuntu is what Redhat long ago tried to be and what Fedora might have been; instead, one went for big money and the other includes everything under the sun, and, to boot, mucks around with tons of unnecessary undercarriage work.

Also, I agree, Debian was gawd-awful in terms of uninstallability due to sheer complexity.  My "basic" installs on Deb resulted repeatedly in literally hundreds of questions before install completed -- for this single, stupid reason, Deb remains, IMO, ridiculously uninstallable.  That one thing, at least for us here, precluded it.

Happily, Ubuntu has swung (probably a wee bit too far, by, for instance, not including sshd in default install) in the opposite direction toward extreme minimalist, yet with everything immediately and expertly available online.

Smooth move.[/QUOTE]
 Yeah I also think Ubuntu is THE MAIN distro out there
I mean, take a look at Mandrivia, RedHat... RPM based distros

Here in Ubuntu as long as you have the dependencies you can install anythin that you want

In the RPM based distros (for instance SuSE's RPM packages are not compatible between 9.1, 9.2 and 9.3!), there are different RPMs for every distros, and (like SuSE) for every release of the distro

That means that between SuSE Professional 8.2 and SuSE Professional 9.3 there are at least 4 diffrent RPMs for the same packages

Ubuntu is neat.
I expect my upgrade to Breezy to be a Breeze ;)

---

### Post by az on 2005-09-22
Debian Sid is a bunch of pieces lying on the floor.

Debian testing is what those peices look like when you try to put them together.

Debian stable is what happened the last time everybody in debian got together and made the thing work all-around.

Ubuntu is debian Sid made to work all-around.  The way they do that is to take a small subset of packages from sid, put them together and fix them up.

When someone who is using Ubuntu wants a newer toy, they can take them from Debian Sid and watch their system break, or find a kind backporter who has taken the package from Sid and built and tested it on the latest Ubuntu.


"
samba: Security 
update breaks systems

Do you think that is why my entire system collapsed?"


Probably, if you had stuck with the version of Samba in Hoary, you would not be in this trouble.

---

### Post by xbaez on 2005-09-22
OR build you own .debs like I did with amarok 1.3 :)

Debian is what you mentioned BUT they are (Like Ubuntu) 100% open source, so they deserve my respect :)

---

### Post by az on 2005-09-23
Let me clarify my profound respect for debian and FLOSS.  Nothing derogatory was meant by my last post.

---

