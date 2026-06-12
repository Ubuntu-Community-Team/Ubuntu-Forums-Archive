---
title: "HOWTO: Auto mount a drive in DOSBOX"
date: 2006-05-07
forum: Tutorials
---

### Post by Master Shake on 2006-05-07
Here's a simple one.

First off, I may say that if you're a REAL retro-gamer, you cannot beat Dosbox!  All those classic MS DOS games are at your fingertips in this excellent "emulator".  I'm currently enjoying Prince of Persia, Populous, Jungle Strike, Thexder 1 and 2, and the DOS version of Sim City 2000.

Here we go:

This works with version 0.63-2 of Dosbox, which is in the repositories.

**INSTALLING DOSBOX**

1) Click *SYSTEM* then *ADMINISTRATION *then *SYNAPTIC PACKAGE MANAGER*

2) Enter your password

3)  Click any line in the upper left window, then type **DOS**  This will take you down to dosbox.  Right click the box and select *MARK FOR INSTALLATION*

4) Click Apply.

Synaptic will download and install DOSBOX.

**HOW TO AUTOMOUNT DRIVE**

1) Open a terminal session, and it should take you to your home directory.  If not, type **cd /home/yourname/**

2) Create a directory to store your DOS programs in.  I called mine dosprog, so I typed **mkdir dosprog**  The full pathname to  this file is *home/yourname/dosprog*

3) Open dosbox by typing **dosbox**

4) You are now in the dosbox shell.  Neat, huh?  Note that it automatically puts you at the Z:\ drive  We want to change that.  Try typing in the dos command **C:**  Note that it says the drive doesn't exist.  We could mount the C drive everytime we open dosbox by typing **mount c /home/yourname/dosprog** everytime, but why do that whendosbox can create a configuration file to take care of that for you!  But first we need to create the file.

5) At the dosbox Z:\ prompt, type in **config -writeconf /home/yourname/dosbox.conf** You now have the configuration file.

6) Type **exit**.  This puts you back in your terminal session

7) Type **sudo gedit dosbox.conf**  This will open the dosbox configuration file.

8 )  Scroll down the dosbox.conf file to this section:

```
[autoexec]
# Lines in this section will be run at startup.
```

Type the following in on a new line:

**mount c /home/yourname/dosprog**

This will automatically mount the C: drive to your dosprog directory.

8a) If you want dosbox to automatically start on the C: drive, enter **C:** on a new line after your mount line.

(for more info on what the dosbox.conf file can do, check the FAQ at [http://dosbox.sourceforge.net/wiki/index.php?page=dosbox.conf](http://dosbox.sourceforge.net/wiki/index.php?page=dosbox.conf) )

9) Save and quit gedit.

10) Now at the terminal prompt, type in **dosbox**  It should auto mount the C: drive, (and if you followed step 8a, it will also start you on the C: drive)

That's all there is to it!

Now get out there and find yourself some abandonware!

---

### Post by tombott on 2007-05-07
Nice post cheers, I had DosBox installed but was trying to figure out how to get the dosbox.conf created so your post really helped thanks!

---

### Post by dfreer on 2007-06-08
Thanks for the post! I knew I had done it before but couldn't remember how.

---

### Post by bobbob1016 on 2007-07-11
Most people might want to add "C:" without quotes after the mount line, to automatically go to the C drive.

---

### Post by motin on 2007-08-08
DosBox would for some reason not recognize my config file. 

Solution:
```

mkdir ~/.dosbox
dosbox
# Enter withing DosBox:
config -writeconf /home/YOURUSERNAME/.dosbox/dosbox.conf
exit
# Back to terminal:
cd ~
echo 'dosbox -conf ~/.dosbox/dosbox.conf' > bin/dosbox.sh
chmod u+x bin/dosbox.sh
# Then start dosbox with:
~/bin/dosbox.sh

```

---

### Post by marenkar on 2007-10-12
thanks for the howto!

Btw, when I try to run tt(tt.exe) it says i need it to run on win32, how do i do this?

---

### Post by Vitamin-Carrot on 2007-10-30
Is there anything in the conf file you can edit to increase the size of the display for certain games?

And i dont mean alt + enter for full screen either.

---

### Post by Igron on 2009-08-07
> **motin said:**
> DosBox would for some reason not recognize my config file. 

Solution:
```

mkdir ~/.dosbox
dosbox
# Enter withing DosBox:
config -writeconf /home/YOURUSERNAME/.dosbox/dosbox.conf
exit
# Back to terminal:
cd ~
echo 'dosbox -conf ~/.dosbox/dosbox.conf' > bin/dosbox.sh
chmod u+x bin/dosbox.sh
# Then start dosbox with:
~/bin/dosbox.sh

```
You can do it another way:
```
mv ~/.dosbox/dosbox.conf ~/.dosboxrc
```
and after that just run 'dosbox' without arguments.

So, dosbox checks file "~/.dosboxrc" while running, neither "dosbox.conf".

---

### Post by geniusthemaster on 2009-11-20
optimized by yours truly ... the perfect dosbox.conf copy and paste over your old conf for maximum happiness. ```
[sdl]
fullscreen=false
fulldouble=false
fullresolution=original
windowresolution=original
output=opengl
autolock=true
sensitivity=100
waitonerror=true
priority=highest
mapperfile=mapper.txt
usescancodes=true
[dosbox]
language=
machine=vga
captures=capture
memsize=32
[render]
frameskip=0
aspect=false
scaler=supereagle
[cpu]
core=auto
cycles=20000
cycleup=0
cycledown=0
[mixer]
nosound=false
rate=22050
blocksize=1024
prebuffer=44
[midi]
mpu401=uart
device=oss
config=
[sblaster]
sbtype=sb2
sbbase=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050
[gus]
gus=true
gusrate=22050
gusbase=240
irq1=5
irq2=5
dma1=3
dma2=3
ultradir=C:\ULTRASND
[speaker]
pcspeaker=true
pcrate=22050
tandy=auto
tandyrate=22050
disney=false
[joystick]
joysticktype=auto
timed=true
autofire=false
swap34=false
buttonwrap=true
[serial]
serial1=dummy
serial2=dummy
serial3=disabled
serial4=disabled
[dos]
xms=true
ems=true
umb=true
keyboardlayout=none
[ipx]
ipx=false
[autoexec]
mount C /media/Iomega HDD/dos
C:
cd bstone
```
:popcorn::p;):D:o:):P:KS

---

### Post by prijilps on 2010-01-22
can anyone help with this???? How can i compile c programs using dosbox???????

---

### Post by reble on 2010-03-17
[SIZE=3]I have the C drive were dosbox is mounted. I have 3 hard drives, C, D, and E. D I use for storage and quick refrence, E hd has all my games on it. How do I mount a 2nd hard drive and directory in dosbox?[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]Steve[/SIZE]

---

### Post by milton antonio on 2010-11-22
amigo no puedo descargar el programa , lo descargo pero me sale solo un acceso directo mas nada, ayudame por favor , esq esta puede ser una herramienta q nesecito gracias

---

### Post by screamingturnip on 2010-11-23
> **milton antonio said:**
> amigo no puedo descargar el programa , lo descargo pero me sale solo un acceso directo mas nada, ayudame por favor , esq esta puede ser una herramienta q nesecito gracias

[http://www.ubuntu-es.org/?q=forum](http://www.ubuntu-es.org/?q=forum)

---

### Post by matrixnis on 2011-01-31
same as in ms dos...you need to find compiler and put it in to folder whre your cobol programs are,,,,

i have diferent question...

i need to mount network drive in dos box or dosemu...to aces dos programs on my windows server...

> z:/mount g smb://nijansaserver/d/

i tried this but it does not work...

---

### Post by Robert Lock on 2012-12-01
Six years on, this advice is just as good now as it was then.  Thanks! :cool:

---

