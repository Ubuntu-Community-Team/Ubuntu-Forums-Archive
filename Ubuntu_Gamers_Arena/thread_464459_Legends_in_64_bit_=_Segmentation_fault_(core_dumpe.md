---
title: "Legends in 64 bit = Segmentation fault (core dumped)"
date: 2007-06-04
forum: Ubuntu Gamers Arena
---

### Post by fakie_flip on 2007-06-04
I am trying to play the game in 64 bit Ubuntu Feisty Fawn Linux using 32 bit libs. These are the 32 bit libs that I have installed.

```
chris@ubuntu:/usr/local/games/legends$ dpkg -l | grep ia32
ii  ia32-libs                                  1.5ubuntu9                             ia32 shared libraries for use on amd64 and i
ii  ia32-libs-gtk                              25                                     gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                              12                                     KDE ia32 shared libraries for with OpenOffic
ii  ia32-libs-sdl                              1.0ubuntu3                             ia32 shared libraries of sdl related package
chris@ubuntu:/usr/local/games/legends$ 
```

I also have these

```
ii  lib32asound2                               1.0.13-1ubuntu5                        ALSA library (32bit)
ii  libc6-i386                                 2.5-0ubuntu14                          GNU C Library: 32bit shared libraries for AM
ii  lib32stdc++6                               4.1.2-0ubuntu4                         The GNU Standard C++ Library v3 (32 bit Vers
ii  linux32                                    1-3                                    Wrapper to set the execution domain
```

The game will not start from the menu or by running runlegends. I used the loki gui installer to install the game. After it was finished running the loki gui nstaller gave me the choice to start the game. I did that, and it worked even with sound. I even reinstalled Legends, and it worked again. However I still can't run the game with runlegends or from the menu. ldd shows that I have all of the libs that I need.

```
chris@ubuntu:/usr/local/games/legends$ ldd LinLegends
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ed3000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ecf000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7ddd000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7dcf000)
        librt.so.1 => /lib32/librt.so.1 (0xf7dc6000)
        libSDL-1.3.so.0 => ./libSDL-1.3.so.0 (0xf7d54000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d2d000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bec000)
        /lib/ld-linux.so.2 (0xf7efe000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7be8000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7be3000)
chris@ubuntu:/usr/local/games/legends$ ldd LinLegends | grep not
chris@ubuntu:/usr/local/games/legends$ runlegends 
chris@ubuntu:/usr/local/games/legends$ ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$
chris@ubuntu:/usr/local/games/legends$ linux32 runlegends
chris@ubuntu:/usr/local/games/legends$ linux32 ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$
```

Then I tried running the update script. Here is what I get from running the update script.

```
chris@ubuntu:/usr/local/games/legends$ sudo ./update 
Password:
rsync --progress --stats -zrvc rsync://update.legendsthegame.net/commonlegends .
receiving file list ... 
27 files to consider

Number of files: 27
Number of files transferred: 0
Total file size: 141930411 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 953
File list generation time: 0.567 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 83
Total bytes received: 993

sent 83 bytes  received 993 bytes  195.64 bytes/sec
total size is 141930411  speedup is 131905.59
rsync --progress --stats -zrvc rsync://update.legendsthegame.net/lin32legends .
receiving file list ... 
13 files to consider
runlegends
         180 100%  175.78kB/s    0:00:00 (xfer#1, to-check=1/13)

Number of files: 13
Number of files transferred: 1
Total file size: 15600767 bytes
Total transferred file size: 180 bytes
Literal data: 180 bytes
Matched data: 0 bytes
File list size: 487
File list generation time: 0.062 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 109
Total bytes received: 703

sent 109 bytes  received 703 bytes  324.80 bytes/sec
total size is 15600767  speedup is 19212.77

Update completed succesfully.
chris@ubuntu:/usr/local/games/legends$ runlegends
chris@ubuntu:/usr/local/games/legends$ linux32 ./runlegends 
chris@ubuntu:/usr/local/games/legends$ ./LinLegends 
./LinLegends: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory
chris@ubuntu:/usr/local/games/legends$ ls
common                libogg.so.0      lindedicated  ReadMe_legals.txt  update
default.keybinds.txt  libopenal.so     LinLegends    ReadMe.txt
install.sh            libSDL-1.2.so.0  linux.txt     runlegends
legends               libSDL-1.3.so.0  main.cs       show
legends.ico           libvorbis.so.0   OPENAL32.DLL  uninstall
chris@ubuntu:/usr/local/games/legends$ echo $LD_LIBRARY_PATH 
/home/chris/.32bitLibs
chris@ubuntu:/usr/local/games/legends$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./
chris@ubuntu:/usr/local/games/legends$ ./LinLegends Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$ linux32 ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$ 
```

I was searching around on Google and forums. I found this command. Every lib it says I need, I can find them with the locate command.

```
chris@ubuntu:/usr/local/games/legends$ objdump -x LinLegends | grep NEEDED
  NEEDED      libpthread.so.0
  NEEDED      libdl.so.2
  NEEDED      libX11.so.6
  NEEDED      libXext.so.6
  NEEDED      librt.so.1
  NEEDED      libSDL-1.3.so.0
  NEEDED      libm.so.6
  NEEDED      libc.so.6
chris@ubuntu:/usr/local/games/legends$ locate libpthread.so.0
/lib32/libpthread.so.0
/lib/libpthread.so.0
chris@ubuntu:/usr/local/games/legends$ locate libdl.so.2
/lib32/libdl.so.2
/lib/libdl.so.2
chris@ubuntu:/usr/local/games/legends$ locate libX11.so.6
/usr/lib32/libX11.so.6.2.0
/usr/lib32/libX11.so.6
/usr/lib/libX11.so.6.2.0
/usr/lib/libX11.so.6
chris@ubuntu:/usr/local/games/legends$ locate libXext.so.6
/usr/lib32/libXext.so.6.4.0
/usr/lib32/libXext.so.6
/usr/lib/libXext.so.6.4.0
/usr/lib/libXext.so.6
chris@ubuntu:/usr/local/games/legends$
```

I know that I have all of the libs that the game needs, or else it would not have started from the loki gui installer, so what is the problem, and how do I fix it? Why is the game only starting from the installer?

---

### Post by fakie_flip on 2007-06-04
Nvm, I solved the problem.

---

### Post by Clay_Banger on 2007-06-04
would you mind explaining to us what you did to fix it? if someone else comes along this thread with the same problem, it wont help them at all.

---

### Post by itchy8me on 2008-11-23
how'd ya fix it?.. i have the same problem on opensuse 11 64 bit

---

