---
title: "now i really messed it up!!!do i reinstall os"
date: 2010-09-23
forum: Ubuntu Studio
---

### Post by jklopez on 2010-09-23
I'm not sure if i have ubuntu studio,i installed ubuntu 10.04....i installed lmms v0.4.8-0ubuntu1~lucid1(lmms) via software center but i get no sound so i've been looking for help online and came across ..[http://lmms.sourceforge.net/wiki/index.php?title=Installation#Installing_LMMS_from_Git....and](http://lmms.sourceforge.net/wiki/index.php?title=Installation#Installing_LMMS_from_Git....and) said about some corrections that must be made to get the sound working so i did what it said i also followed a couple post here and other places and installed things like jack/alsa/pules audio configured all sorts of things people said to do and still nothing so i got pissed and started playing with sound(system/preference/sound,lmms is listed like 6 times in there)played with alsa mixer,alsamixergui,gnome alsa mixer,jack control,pules audio,gstreamer properties....and along the way not only did i manage to not get it working but know no music,videos or movies will play ,you double click them and the app opens up normal and the buttons work ,it says playing but they don't play ,the numbers don't count and my computer is fine besides that, all else works ,what should i do,what did muck up...thnx:guitar:

---

### Post by jklopez on 2010-09-23
i got my sound back and lmms now has sound but it's with pulse audio and it's labled bad latancy for a reason it sucks ,sounds crack and pop sometimes and before raising the buffer(anything more than 20 ms is not good) how do i get it to work with alsa witch i here is the best sounding and less latant...please ,i don't want to shoot in the dark again and risk doing some permanent damage and by the way any idea how to get fl studio 8 xxl working in wine ,i managed to install it but it wont open at all...

---

### Post by JC Cheloven on 2010-09-23
> **jklopez said:**
> (...) how do i get it to work with alsa witch i here is the best sounding and less latant (...)

You have this simple way of temporarily disabling pulse:

1) Create a file ~/.pulse/client.conf and stuff it with a single line that reads ```
autospawn=no
```
2) When you'll use an audio app that doesn't like pulse, disable pulse before, issuing this command at terminal ```
pulseaudio -k
``` LMMS, and other apps using alsa, should be able to do it without the interference of pulseaudio now.

3) When you're done and want pulse back again, type at a terminal ```
pulseaudio -D
```

Note: as for your worries, this is absolutely non invasive to your system, and absolutely reversible ;)
EDIT: of course, the sound icon at your upper panel (it's for pulse) will be inoperative in the meanwhile

---

### Post by jklopez on 2010-09-23
cool thnx but i have more ??  ,when you say create a file ~/.pulse/client.config do you mean a folder or a text document ,how do i do this and whats (~) is that a root or a location...little more info please....i'm new to linux...thnx again

---

### Post by cchhrriiss121212 on 2010-09-24
Hi
~ means your home folder, and any file with a . in front is a hidden file/folder. So navigate to your home folder, then press ctrl+h to see hidden files, find the file and open it with gedit, which is a simple text editor.

---

### Post by JC Cheloven on 2010-09-24
Ok, sorry, one never knows how much explanation is needed. So, although Chris almost did it, here it is:
> **JC Cheloven said:**
> 
1) Create a file ~/.pulse/client.conf and stuff it with a single line that reads autospawn=no

~ is shortland for /home/jklopez (assuming jklopez is your username in the system). Your user directory. 

.pulse is a hidden directory (as it begins with "."). To see hidden directories press ctrl-H in nautilus as Chris said. If you don't find .pulse just create it using nautilus (left button mouse for example...). 

client.conf is a text documment. You should create it if it doesn't exists. And you should edit it with gedit (the default text editor), as indicated.

Cheers
JC

---

### Post by jklopez on 2010-09-24
my bad guys , first i should have told you i'm a noob , thnx ,you guys have been very helpful...so i did what you guys said , i went to ~ and found .pulse ,i double clicked it and inside are varios files and folders ,i right clicked and created new document and named it client.conf  ,next i opened it with gedit and put a line of text {autospawn=no} ,so now to disable pulse i just type in terminal pulseaudio -k and to enable type pulseaudio -d but when i typed pulseaudio -k it took the command but when i typed pulseaudio -d it gave me the error {Failed to parse command line.} ,what did i do wrong....p.s. just a quik side question ,how do i post screen shots here?

---

### Post by JC Cheloven on 2010-09-24
> **jklopez said:**
>  (...) but when i typed pulseaudio -d it gave me the error {Failed to parse command line.} ,what did i do wrong
Please note that the unix/linux command line is case sensitive. It should be ```
pulseaudio -D
```with capital "D"

> ....p.s. just a quik side question ,how do i post screen shots here?Just scroll down when writting. You'll find a section "Attach files". Several graphical formats are allowed, including png (which is good for screenshots).

Cheers
JC

---

### Post by RaumTrug on 2010-09-24
heh yheah, 2 b a n00b iz fun! ;)

man, first: you create that file, and within you hopefully have "autospawn=no" without any brackets or such...

then you need to log in and out (just do a computer restart...:P)

when you go to a terminal entering "pulseaudio -k" you have to watch for the volume-control thing in your tray, if it disappears, you've done everything "successfully", and your system is running on "pure alsa" from then. if it stays, you've done something wrong.

now, when you want to have pulse back, it's not "pulseaudio -d", but "pulseaudio -D", linux is nitpicky on type cases, and correct spelling. sorry, it has been made by nerds...

also, if you're within the "pulseaudio -k" mode, without access to your speaker icon in the tray, you might find some alsa mixer helpful, to control the volume of sound (yeah, ubuntu designers were so fond of pulse they didn't take into account people doing without...). "simplest" is the command "alsamixer" in terminal, but you might want to install a package like "gnome-alsamixer" or the like, as those are better to control & understand.

watch out, you're close to completely uninstalling pulseaudio, as audio works fine without, even better & more smooth... ;)

---

### Post by jklopez on 2010-09-24
thnx guys you :guitar:....it worked!!!

---

### Post by JC Cheloven on 2010-09-25
> **jklopez said:**
> thnx guys you :guitar:....it worked!!!

Sweet :)
Could you please mark it as solved (see "thread tools" at the top of the thread). It's customary over here, so that others can see it when searching.

---

### Post by iiiears on 2010-09-25
I saw the guitar and wondered if you have tried Jokosher for track mixing/editing?

---

