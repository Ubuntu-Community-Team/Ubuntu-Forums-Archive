---
title: "jedi academy game installation"
date: 2011-07-02
forum: Wine
---

### Post by falcon12 on 2011-07-02
hey everybody i am having trouble installing a game called star wars jedi knight jedi academy with wine. the game is a two cd installation so i mount the nrg files with furious iso mount and then i run the installation on the mounted cd 1 all goes well until it gets to 47 percent and asks for cd 2 and gives me a little search box to find the location i tell it the correct location (i am 100% positive about this) and the i hit ok and it gives me this error message

Setup could not find a file on the specified path or disc.
Please check that the proper disk is inserted or specify a new path.

any ideas this is driving me crazy ive been at it for hours with no luck.

---

### Post by falcon12 on 2011-07-02
and sorry i think this is in the wrong thread oops

---

### Post by Iowan on 2011-07-02
Moved to Wine.

---

### Post by kaldor on 2011-07-02
Hi. I'm quite into JKA myself, and probably play it way too much :)

Myself and a few others I know run this game in WINE quite frequently. I assume you have either two .iso images or two CDs.

Mount or Run CD 1. There will be a setup.exe somewhere in the disk's folder. Run it with WINE. Once it asks for CD2, unmount disc 1 and mount disc 2. Press OK after a few second when you're sure it's ready, and it will continue. That's all I ever needed to do.

---

### Post by falcon12 on 2011-07-04
ok i tried installing again it got to 47 percent as usual and asked for cd two (for some reason they arent iso's they are NRG files) so i tried to unmount cd 1 and it wont let me i get this error

Unable to unmount Stawars_Jedi_Knight_-_Jedi_Academy_1_nrg
umount: /home/falcon/Stawars_Jedi_Knight_-_Jedi_Academy_1_nrg is not in the fstab (and you are not root)
 any ideas ive tried everything to unmount it but with no success

---

### Post by falcon12 on 2011-07-04
so yay i got it to work!!! i ended up just putting all the cd contents on my hard drive but now i have a new problem when i hit jamp.exe it gets me to the menu i hit new game and then i create my character and then i hit go and it says

Error: disk 1 not in drive 

im sooo close this is killing me!!!!!!help!!!

---

### Post by Einder on 2011-07-24
I'm running Ubuntu 10.04 LTS and I can get the game to install ok, but every time I try to boot the game or join multi-player mode I have trouble. I've tried registry fixes and everything else, nothings working. If I try to go into single player I get wrong disc inserted. If I try and boot into multi-player it acts like it's going to boot then closes out. I don't know if this is just an issue with my wine version or what. Don't know if anyone else has had this problem but if you have and fixed it then please let me know how. If not then I'll keep working at it and if I get it fixed I'll post the solution.

---

### Post by Einder on 2011-07-24
So I found out that if you install playonlinux and then use that to install Jedi Academy you avoid most of the errors. I personally am still have some sort of program error when it tries to load, but at least it's reading the right disc now. Try using playonlinux and hopefully it'll solve your problem

---

### Post by falcon12 on 2011-09-03
> **Einder said:**
> So I found out that if you install playonlinux and then use that to install Jedi Academy you avoid most of the errors. I personally am still have some sort of program error when it tries to load, but at least it's reading the right disc now. Try using playonlinux and hopefully it'll solve your problem

hmm i actually have fixed my problem and the game runs as smooth as if it were on windows (aka perfectly)
when you had wine did you try running it in windowed mode and also do you have winetricks? winetricks basically installs the nessicary required things to run the game such as direct x and others.  here is a link to it [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) just copy and paste to a notepad or something and save it. next right click the file and go to properties then permissions and check open file as executable. then close the properties panel and double click the file it will ask you if you want to display the file run in command prompt or run hit run. now there are many things you have to check in this but there are also alot of youtube tutorials that will explain this better. anyway i recommened the one by gregeriah on youtube check it out heres the link [http://m.youtube.com/index?desktop_uri=%2F&gl=US#/watch?v=ejcDUNIqSeQ](http://m.youtube.com/index?desktop_uri=%2F&gl=US#/watch?v=ejcDUNIqSeQ) sorry if this leads you to a mobile version of youtube im doing this from my phone :P and sorry if there are alot of typos i hope this helps anyone trying to get the game running good luck

---

