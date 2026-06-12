---
title: "Patrick's install script for a fackin' good system."
date: 2006-10-11
forum: The Cafe
---

### Post by PatrickMay16 on 2006-10-11
I install ubuntu on old computers a lot, which I give to friends or relatives to use when their computer is broken or if they never had a computer before.
Often they're with low amounts of memory and slower processors than GNOME would like, so I've decided to make this script to get the basic stuff installed to make the job quicker. Maybe you guys would like to see it, so here it is.

The script is supposed to be run on a fresh server install of Ubuntu, with the universe and multiverse enabled.

```

cd ~/
echo Lets configure a fackin good system.
echo Make sure universe and multiverse repositories are enabled. && sleep 3
sudo apt-get install icewm rox-filer menu x-window-system-core gaim mozilla-browser xmms audacity xscreensaver rxvt grun sox pmount
sudo dpkg-reconfigure xserver-xorg
echo WHOA, oh man. 
echo IT IS NOT OVER YET, BOY
wget http://dusthillguy.netfirms.com/configs.tar.bz2
tar -xvjf configs.tar.bz2
rm configs.tar.bz2
sleep 2
echo Processing FACKIN, please wait...
sleep 1; echo .; sleep 1; echo .; sleep 1; echo .;
play ~/.masb.mp3 > /dev/null &
echo Thanks. Now type startx

``` 

I dunno how well it works or if it works at all, since I haven't tried it yet.

---

### Post by slimdog360 on 2006-10-11
I'll have to give that a try next time I loose my mind.

---

### Post by Polygon on 2006-10-11
server install as in it doesnt have gnome or kde or whatever installed?

ill try it out sometime

---

### Post by prizrak on 2006-10-11
A suggestion for improvement:
Have the script actually enable the universe and multiverse repos. Don't ask for actual commands tho, I don't remember them :)

---

### Post by aysiu on 2006-10-12
How about this? I modified and cut out a little bit from Nanotube's Firefox installation script: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
if grep -q "5.10" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse' >> /etc/apt/sources.list
 
elif grep -q "6.06" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main' >> /etc/apt/sources.list

elif grep -q "development" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main' >> /etc/apt/sources.list
 
else
  echo "This script only works on Breezy, Dapper, or Edgy."
  exit 1
fi
``` Of course, once Edgy's fully released, you'd have to change the code to this: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
if grep -q "5.10" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse' >> /etc/apt/sources.list
 
elif grep -q "6.06" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main' >> /etc/apt/sources.list

elif grep -q "6.10" /etc/issue ; then
		sudo echo 'deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main' >> /etc/apt/sources.list
 
else
  echo "This script only works on Breezy, Dapper, or Edgy."
  exit 1
fi
``` This assumes that you have a vanilla sources.list with no extra repositories installed. It also doesn't take into account localized mirrors (by country).

---

### Post by Anonii on 2006-10-12
> **PatrickMay16 said:**
> I install ubuntu on old computers a lot, which I give to friends or relatives to use when their computer is broken or if they never had a computer before.
Often they're with low amounts of memory and slower processors than GNOME would like, so I've decided to make this script to get the basic stuff installed to make the job quicker. Maybe you guys would like to see it, so here it is.

The script is supposed to be run on a fresh server install of Ubuntu, with the universe and multiverse enabled.

```

cd ~/
echo Lets configure a fackin good system.
echo Make sure universe and multiverse repositories are enabled. && sleep 3
sudo apt-get install icewm rox-filer menu x-window-system-core gaim mozilla-browser xmms audacity xscreensaver rxvt grun sox pmount
sudo dpkg-reconfigure xserver-xorg
echo WHOA, oh man. 
echo IT IS NOT OVER YET, BOY
wget http://dusthillguy.netfirms.com/configs.tar.bz2
tar -xvjf configs.tar.bz2
rm configs.tar.bz2
sleep 2
echo Processing FACKIN, please wait...
sleep 1; echo .; sleep 1; echo .; sleep 1; echo .;
play ~/.masb.mp3 > /dev/null &
echo Thanks. Now type startx

``` 

I dunno how well it works or if it works at all, since I haven't tried it yet.
Try making it less like your PC is coming to an orgasm.

---

### Post by slimdog360 on 2006-10-12
> **Anonii said:**
> Try making it less like your PC is coming to an orgasm.
hahhaa

---

### Post by chaosgeisterchen on 2006-10-12
Fackin' great but incomplete ;)

I like your style but am more a KDE addict (as I only have PCs above 1,96 GHz)

---

