---
title: "The people is not using wineasio anymore?"
date: 2012-05-01
forum: Ubuntu Studio
---

### Post by Splashmania on 2012-05-01
Is the people using wineasio yet? or is another way to execute the vst with jack, becouse im having troubles to find the sources of that

---

### Post by LucaFiore on 2012-05-01
I'm also looking for information these days.
if I find something, I will contact you.

bye

---

### Post by sgx on 2012-05-01
its attached to the first post here:

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

also

[http://pkgs.org/opensuse-11.4/packman-i586/wineasio-0.9.0-5.2.i586.rpm.html](http://pkgs.org/opensuse-11.4/packman-i586/wineasio-0.9.0-5.2.i586.rpm.html)

try 

sudo alien -d name-of-rpm to make a debian package and

sudo dpkg -i name-of-deb

run command regsvr32 wineasio.dll
wine will confirm it has registered.

Other are in basic google searches.
Cheers

---

### Post by Splashmania on 2012-05-01
The rpm is only for 32 bits and the other one regserv32 cant load wineasio.dll

---

### Post by sgx on 2012-05-02
> **Splashmania said:**
> The rpm is only for 32 bits and the other one regserv32 cant load wineasio.dll
Hi, in case of a typo, its  regsvr32

Did the alien-d command make a .deb?

I would try it on all the rpms you can find via google.

Here is a page for compiling wineasio

[http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO](http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO)

I would ask falk regarding latest 64 bit wine,
there is a KX forum

[http://www.linuxmusicians.com/viewforum.php?f=47](http://www.linuxmusicians.com/viewforum.php?f=47)
Cheers

---

### Post by Splashmania on 2012-05-02
I've copied the wineasio.dll evrywhere but it dont is loaded, one thing is i can see the library in winecfg window in the library tab i switch it but nothing happens.

---

### Post by Splashmania on 2012-05-02
Anyone with a trick for that?

---

### Post by eric71 on 2012-05-03
I don't recall the specifics but I was playing with wineasio on a Kubuntu 12.04 beta release and it took a little work to figure out that usr/lib/wine was no longer the correct place for wineasio. On my 32 bit system it was now  /usr/lib/i386-linux-gnu/wine. Copying the wineasio.dll.so binary there and running regsvr32 wineasio.dll worked.

I'm not sure if FalkTX's debs have been updated to reflect this yet, because I haven't played with it since.

Edit: One other point for those using wineasio - I use it with Reaper, and the past few updates of Reaper haven't quite played nice with wineasio. When upgrading an already installed Reaper, everything worked OK, but when installing for the first time on a new Kubuntu install there were problems. i could select wineasio for sound, but no inputs or outputs were listed and I would get errors when trying to play anything. Downloading and installing Reaper 4.151 from back in January allowed everything to work again.

---

### Post by sgx on 2012-05-03
wine is focused on games and office apps, so keep the old
known-to-work versions on some media, with all the dependencies.

I can't say that basic multitrack recording with wine and reaper
has improved any since reaper v3.05, and wine 1.2, a tribute to those able and willing to explore new features, but without huge benefit
to the end result. 

I have a wine 1.4 with wineasio in /usr/lib/wine
Cheers

---

### Post by K.Stoyanov on 2012-05-07
well if something is not evolving, we have to thow it in the trash, just like my win98 cd..pity, wineasio was nice app..

---

### Post by sgx on 2012-05-08
If it works, use it, I use it 5 days a week.
It's not like me, getting tired at work, and
going home at dinner time. It never sleeps.

:popcorn:

---

### Post by Splashmania on 2012-05-08
Absolutely the fix to make it work was install the kxstudio repos, Install first ubuntu studio is not a option it symply dont work, with no more excuses, or the installation is broken in amd64 or is simply forgotted, if one developper wants contacme to know how the system must work to make music im opened

---

### Post by sgx on 2012-05-08
Need to know what you want to do musically. Typical wineasio
user will use reaper as host/daw for some favorite vstplugins,
used in their windows setup, and run a few standalone apps like Absynth, Addictive Drums, Amplitube etc

In winecfg, wine 1.3 and earlier, choose alsa instead of jack,
in the audio tab. Wine 1.4 handles this in an odd way.
Might be older is better.

Do audio files playback OK, using vlc, aqualung, xmms etc ?
If your Ubuntu version is an issue, 10.04 was very good,
if your hardware is compatible. What soundcard and video card?

Output from commands

cat /proc/asound/cards
aplay -l
arecord -l
aconnect -i
aconnect -o

Cheers

---

### Post by Splashmania on 2012-05-08
Sorry maybe i explained wrong. My setup is working thanks to kxstudio and ffado, right now im saying what all the system to make music in linux seems stay in a unfinishable alpha state, it can be well to test things or learn basics but is not workable musically talking. It can be the best system to make music made ever but is the worst because have no supports from the distros, it needs big reinforcements. cool ui designers, the programers must listen the music makers. is 2012 and the project is freeze in the 90's.

Is necessary a completly reorganitzation of the audio production, if it no change its nothing to do
Regards

---

### Post by sgx on 2012-05-08
KX is making great progress. I like running various combos
of vst plugins and linux apps. There are a few things like
Rhino, 1977, and Head Case, that I keep XP around for. Most
plugins and apps that don't use dongles, will work in wine/Reaper.

The 'alpha' level of things is temporary. Once people
stop upgrading stable systems with new untested versions,
recording projects are a breeze.  

The coders have to eat, it takes lots of work to create things,
and keep them up to date. A lot of software is made for
personal use, and kindly shared, never meant to compete with
commercial products. Both can be used to greatadvantage.

Cheers

---

### Post by Splashmania on 2012-05-09
Is what im saying,  if it no change its nothing to do
maybe is time to pay someone to make this working, to create a nice base or pulish the one what we have and make it workable, is necessary create a stable standard for midi/audio conections. 
ubuntu, yes have a good look but if you try to make a song on it is terribly, i've passed two weeks to do all my hardware working, but now ive tried make a song but simply i can't is an unworkable system for that purpose, and no because is a bad system to that is because is not refined and the programmers are not listening the musicians.
I dont want a tons of programs for conect in/outs, i want one (core audio from apple got the linux idea and did it work) i want what if i want make a song start to do it not think if i must conect the cables of the piano and mpc and the surface controller to any plugin on every chnnel on every project.
the system have good capabilities but if no change the way is nothing to do with the musicians. i dont know if i talk for every musician but i considered me an advanced audio user.
regards.

---

### Post by K.Stoyanov on 2012-05-16
i converted the rpm to deb, installed the deb, and

regsvr32 wineasio.dll
Failed to load DLL wineasio.dll

Edit: Fixed!

now wineasio.dll.so have to be located in /usr/lib/i386-linux-gnu/wine

moving the file there and regsvr32 succeeded

---

### Post by sgx on 2012-05-16
> **Splashmania said:**
> 
the system have good capabilities but if no change the way is nothing to do with the musicians. i dont know if i talk for every musician but i considered me an advanced audio user.
regards.Reaper works in linux, so songs that require lots
of connections, can be based in reaper, and the project
can be recalled intact, as it moves forward. The reaper output is just another instrument to linux, and can be routed to linux apps for more processing, and recording if desired.

aj-snapshot works pretty well recalling linux audio apps
like rakarrack and hydrogen, can be downloaded at

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)  or you may find it
using synaptic and kx repositories.
Cheers

---

