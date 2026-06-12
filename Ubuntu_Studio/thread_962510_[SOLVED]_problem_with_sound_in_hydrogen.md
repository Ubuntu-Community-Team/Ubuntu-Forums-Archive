---
title: "[SOLVED] problem with sound in hydrogen"
date: 2008-10-29
forum: Ubuntu Studio
---

### Post by simtaalo on 2008-10-29
im running hydrogen v0.9.3

ive used hydrogen before with no problems, but since upgrading to linux mint 5, which is 64-bit system ive been having problems getting any sound out of it.

ive tried using the jack drivers, ALSA and OSS and i cant get any of them to work.

what is wierd is that i used to have similar problems with audacity, but since upgrading ive managed to get that working fine but now i cant use hydrogen.

audacity is using the portaudio driver and works fine, so i thought i would try the same settings in hydrogen, but when i click portaudio it says "not compiled"

my computer is a HP laptop dv6174ea, it uses on-board sound card. i know its not ideal but just using it until i get my tascam us-428 setup. in the meantime i just want to be able to sketch some ideas out.

can anyone help? either to get it working using alsa/jack, or to help get the portaudio driver compiled?

any help much appreciated :)

---

### Post by simtaalo on 2008-11-06
well i didnt work out how to get the portaudio driver compiled, but the solution to getting sound was as simple as switching to the alsa driver and typing "default" in.

someone on the hydrogen forum also gave this advice

[quote=pablomme@hydrogen forum]To get hydrogen 0.9.4-svn compiled with all the optional functionality built in, run the following in a terminal 


Pre-install

sudo apt-get install subversion scons g++ libsndfile1-dev libportaudio-dev libportmidi-dev libasound2-dev libjack-dev liblash-dev zlib1g-dev libtar-dev liblrdf0-dev libqt4-dev
mkdir "$HOME/bin" "$HOME/tmp"

Install / update

cd "$HOME/tmp"
svn co [http://hydrogen-music.org/svn/trunk](http://hydrogen-music.org/svn/trunk) hydrogen
cd hydrogen
scons prefix="$HOME/bin/hydrogen" portaudio=1 lash=1 portmidi=1
scons prefix="$HOME/bin/hydrogen" portaudio=1 lash=1 portmidi=1 install

Run

$HOME/bin/hydrogen/bin/hydrogen

Each time you want to upgrade to the latest svn, just re-run the "Install / update" bit.

By the way, some minor issues with the related documentation, in case a developer wants to fix it:

* Scons warns if you are missing libraries, which is very useful, but it doesn't check for libflac++-dev .
* The wiki page [http://hydrogen-music.org/devel/wiki/development%3Aqt4compile](http://hydrogen-music.org/devel/wiki/development%3Aqt4compile) omits zlib1g-dev as a required library.
* The wiki page does not mention that portaudio=1 and portmidi=1 require libportaudio-dev and libportmidi-dev, respectively.[/quote]

---

