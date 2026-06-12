---
title: "noob needing help"
date: 2010-10-20
forum: Wine
---

### Post by shinigami otaku on 2010-10-20
okay i have a problem i recently downloaded RapeLay for windows(cause all the ones offering it for Linux was not actually for Linux and i had to pay if i wanted it)and me and my friend are trying to install it on wine but can't seem to get the install working. We know it does work [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5986](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5986)
but we are completely stumped for ideas and i have been wanting this game for ages but never got around to getting it until now.

Please help me to not only get this game working but also get more familiar with Linux which i love so very much.

---

### Post by amsterdamharu on 2010-10-20
What is the output if you copy and paste the following in the terminal (please copy and paste whatever is in the terminal)

```

sudo apt-get build-dep wine
mkdir custombuild && cd custombuild
wget http://bugs.winehq.org/attachment.cgi?id=28205 -O vertex_blend_sw-1.1.44.diff
wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2.tar.bz2
tar -xvjf wine-1.2.tar.bz2
cd wine-1.2/
patch -p1 < ../vertex_blend_sw-1.1.44.diff
./configure --prefix=${HOME}/wine-vertexfixed
make #THIS MIGHT TAKE MORE THAN 20 MINUTES TO FINISH
sudo make install
# NOW TO START RAPELAY
~/wine-vertexfixed/bin/wine 'RapeLay English.exe' 

```

---

### Post by shinigami otaku on 2010-10-20
> **amsterdamharu said:**
> What is the output if you copy and paste the following in the terminal (please copy and paste whatever is in the terminal)

```

sudo apt-get build-dep wine
mkdir custombuild && cd custombuild
wget http://bugs.winehq.org/attachment.cgi?id=28205 -O vertex_blend_sw-1.1.44.diff
wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2.tar.bz2
tar -xvjf wine-1.2.tar.bz2
cd wine-1.2/
patch -p1 < ../vertex_blend_sw-1.1.44.diff
./configure --prefix=${HOME}/wine-vertexfixed
make #THIS MIGHT TAKE MORE THAN 20 MINUTES TO FINISH
sudo make install
# NOW TO START RAPELAY
~/wine-vertexfixed/bin/wine 'RapeLay English.exe' 

```
it's 
snake@Metal-Gear-Systems:~$ sudo apt-get build-dep wine
[sudo] password for snake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.2' as source package instead of 'wine'
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded.
snake@Metal-Gear-Systems:~$

---

### Post by amsterdamharu on 2010-10-20
Ok, so it only executed the first command. Could you try the other commands until you get an error? And then paste whatever output there is in the terminal (put some code tags around it so it'll read better)?

The commands came from the link you posted in your first post, this will build a custom wine to be used with rapelay

---

### Post by ikt on 2010-10-20
wow what a horrific game :/

---

### Post by shinigami otaku on 2010-10-20
here are the last 20 lines 


race.o unicode.o user.o window.o winstation.o       -L../libs/wine -lwine ../libs/port/libwine_port.a   -Wl,--rpath,\$ORIGIN/`../tools/relpath /home/snake/wine-vertexfixed/bin /home/snake/wine-vertexfixed/lib` -Wl,--enable-new-dtags
LC_ALL=C sed -e 's,@bindir\@,/home/snake/wine-vertexfixed/bin,g' -e 's,@dlldir\@,/home/snake/wine-vertexfixed/lib/wine,g' -e 's,@PACKAGE_STRING\@,Wine 1.2,g' wineserver.man.in >wineserver.man || (rm -f wineserver.man && false)
LC_ALL=C sed -e 's,@bindir\@,/home/snake/wine-vertexfixed/bin,g' -e 's,@dlldir\@,/home/snake/wine-vertexfixed/lib/wine,g' -e 's,@PACKAGE_STRING\@,Wine 1.2,g' wineserver.de.man.in >wineserver.de.man || (rm -f wineserver.de.man && false)
LC_ALL=C sed -e 's,@bindir\@,/home/snake/wine-vertexfixed/bin,g' -e 's,@dlldir\@,/home/snake/wine-vertexfixed/lib/wine,g' -e 's,@PACKAGE_STRING\@,Wine 1.2,g' wineserver.fr.man.in >wineserver.fr.man || (rm -f wineserver.fr.man && false)
make[1]: Leaving directory `/home/snake/custombuild/wine-1.2/server'
Wine build complete.
snake@Metal-Gear-Systems:~/custombuild/wine-1.2$ 
have not tried to run the game yet but thank you for helping if it works. :)

---

### Post by shinigami otaku on 2010-10-20
okay it did not work everything in the folder is saying error invalid name

any ideas?

---

### Post by amsterdamharu on 2010-10-21
Looks like it went off without a problem until the make install command.

What file did you install and where did you get it?

I think you should install the file like so:


```
~/wine-vertexfixed/bin/wine '/home/snake/WHEREVER_YOUR_SETUP_FILE_IS/SETUP_FILE.exe'
```

---

### Post by shinigami otaku on 2010-10-21
well right now my graphics drivers died so i am going to install 10.10 on saterday then i will tell you but i still have not installed anything related to this topic except for what was in the replies.

---

### Post by e79 on 2010-10-21
> **ikt said:**
> wow what a horrific game :/

Hell yeah....who would want to play a sexual predator raping girls.....human nature is so disgusting sometimes....](*,)

---

### Post by shinigami otaku on 2010-10-22
> **e79 said:**
> Hell yeah....who would want to play a sexual predator raping girls.....human nature is so disgusting sometimes....](*,)

well it's not that bad it is far more tame than what you would think and far more tam than the other rape games from Japan.

---

### Post by e79 on 2010-10-22
> **shinigami otaku said:**
> well it's not that bad it is far more tame than what you would think and far more tam than the other rape games from Japan.

Not THAT bad heh ? Silly....

---

### Post by shinigami otaku on 2010-10-23
it's not but if you think it is than that is just you opinion.
no i am not endorsing rape i am merely saying that games that simulate it are far better because you don't go to jail from them.
but really it is no where near what you might think really you never see anything at all and nothing really happens.

---

### Post by ikt on 2010-10-26
> **shinigami otaku said:**
> no i am not endorsing rape i am merely saying that games that simulate it are far better because you don't go to jail from them.

What sort of motivation is that!

I don't think Quake 3 is far better than murdering someone in real life because I don't go to jail from it!

Far out the rape culture must be heavy wherever you are man to say something like that!!

---

