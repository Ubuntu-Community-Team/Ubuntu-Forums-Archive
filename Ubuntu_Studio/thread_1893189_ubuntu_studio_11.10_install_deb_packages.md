---
title: "ubuntu studio 11.10 install deb packages"
date: 2011-12-09
forum: Ubuntu Studio
---

### Post by noisemaker? on 2011-12-09
hello,

i have downloaded a deb package... wine asio deb package... i want to use it with the nord modular g2 demo software.. which is an modular synthesizer.. it is very good... the demo software has full functionality of the G2 Hardware device but not polyphon.. well how ever... if you want a modular synthesizer this is a very good choice...

try out Nord Modular G2 Demo Software yourself... it is Windows so you need to use wine.. works very well

but this is not the problem...

i want to use wine asio so... so i can record / sample the stuff i did at the nord modular g2 demo software via jackd into renoise... i think you get me...

i have downloaded wine asio deb file from another thread in this forum... but how do i install deb package in studio 11.10?

in normal 11.10 i can just right click and select install with software installer

can someone help please

---

### Post by jejeman on 2011-12-09
To instal deb file one can use dpkg
```
sudo dpkg -i some_file.deb
```
Or install gdebi for gui experience.

---

### Post by sgx on 2011-12-09
> **noisemaker? said:**
> hello,

i have downloaded a deb package... wine asio deb package... i want to use it with the nord modular g2 demo software.. which is an modular synthesizer.. it is very good... the demo software has full functionality of the G2 Hardware device but not polyphon.. well how ever... if you want a modular synthesizer this is a very good choice...

try out Nord Modular G2 Demo Software yourself... it is Windows so you need to use wine.. works very well

but this is not the problem...

i want to use wine asio so... so i can record / sample the stuff i did at the nord modular g2 demo software via jackd into renoise... i think you get me...

i have downloaded wine asio deb file from another thread in this forum... but how do i install deb package in studio 11.10?

in normal 11.10 i can just right click and select install with software installer

can someone help please

after dpkg -i name-of.deb

run the command    regsvr32 wineasio.dll

The terminal output will confirm success.

Now windoze audio apps will be able to utilize wineasio as the asio driver.

Cheers

---

### Post by drumaliens on 2011-12-11
Sorry to slight thread jack but I have been through this process and installed winasio. I can get Reaper to recognise winasio under the asio input option. However, when I plug in my M-Audio Fast Track USB nothing happens can't get any sounds. I do start jack before starting Reaper. 

Do I have to install the asio windows drives for the M-Audio in wine so I can get a connection ??

If I choose WaveOut I can see the M-Audio and use it out of the box so I guess these drivers are in the kernel.

---

### Post by jejeman on 2011-12-11
> Do I have to install the asio windows drives for the M-Audio in wine so I can get a connection ??This defenetly not.

---

### Post by sgx on 2011-12-12
> **drumaliens said:**
> Sorry to slight thread jack but I have been through this process and installed winasio. I can get Reaper to recognise winasio under the asio input option. However, when I plug in my M-Audio Fast Track USB nothing happens can't get any sounds. I do start jack before starting Reaper. 

Do I have to install the asio windows drives for the M-Audio in wine so I can get a connection ??

If I choose WaveOut I can see the M-Audio and use it out of the box so I guess these drivers are in the kernel.
If you have the basic FastTrack, not the Pro model, it is picky about where it works. In one distro, it shows up and is detected correctly, and remains silent, yet works perfect in another one. It may be the kernel modules, it may be jackd2 Vs jackd1, maybe the alsa version, or combos of
these and other factors. Mine works with Bodhi linux, an ubuntu based
lite linux using E17 gfx. As mentioned, no driver installs are necessary.

---

### Post by noisemaker? on 2011-12-12
> **jejeman said:**
> To instal deb file one can use dpkg
```
sudo dpkg -i some_file.deb
```Or install gdebi for gui experience.


thanks...

---

### Post by mortenmeldal on 2012-02-26
Hi, Im newbie, help.
I am running AMD64 with Ubuntu 11.10 64bit version. I try to make my FLstudio 10.10 work and for this I desparately need a 64 bit working (with ubundu studio 11.10 64 bit) asio, e.g. wineasio or preferably another asio that handle 24 bit input. I understand that wineasio is the only existing connection to jack from windows applications.

I am new to linux and would like to migrate to ubundu studio to minimize delay in FL-studio recording

None of the excellent advices given in forums and other places on the net works and even though i recovered the wineasio.dll.so from a debfile 386 it cant be copied to Usr/lib32.wine. None of the advice for "make" or "make install" works and I believe the problem is directly related to the structure of the 64 bit Ubuntu Studio. The "make" command issued in the wineasio directory (yes, containing the Steinberg header) end with the following. 

gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:39:24: fatal error: wine/debug.h: No such file or directory
compilation terminated.
make: *** [asio.o] Error 1


I did install the multilib, gcc g++ and other suggestions but nothing woeks. It seems that files the package need are in wrong locations.

I would love if someone with expertise in this could come up with a viable solution to this problem so those who prefer the 64 bit environment can continue to enjoy this otherwise wonderful ubuntu studio environment.


Alternatively, if you can, point me to an open source which is as powerfull as FL-Studio 10 (FL-Studio 10 is actually quite versatile so it will be really though to match with open source).

Kind regards
 Morten

---

### Post by tiagovaz on 2012-10-10
Hey, I've just written a step by step which could help you with wineasio building process: [http://acaia.ca/~tiago/posts/Reaper_+_wine_+_jack_in_a_64bit_Debian_GNU__47__Linux_system/](http://acaia.ca/~tiago/posts/Reaper_+_wine_+_jack_in_a_64bit_Debian_GNU__47__Linux_system/)

---

