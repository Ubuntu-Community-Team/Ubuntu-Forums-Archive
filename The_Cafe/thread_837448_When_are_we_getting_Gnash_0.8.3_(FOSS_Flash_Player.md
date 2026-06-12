---
title: "When are we getting Gnash 0.8.3? (FOSS Flash Player)"
date: 2008-06-22
forum: The Cafe
---

### Post by spoons on 2008-06-22
It's been released, but when is it coming to Ubuntu? :)

Updates:
Native fullscreen support (from AS) has been implemented.
Long command line options are properly supported.
You can view detailed movie information from the GTK GUI.
An option in Preferences to initially display a movie as a blank ("Click here to start") screen has been added.
A "dump" GUI to dump a movie to disk has been added.
Cairo rendering performance has been improved.
Support for the OpenOffice Impress SWF exporter has been fixed.

---

### Post by fluteflute on 2008-06-22
October probably  - with Intrepid.

---

### Post by spoons on 2008-06-22
> **fluteflute said:**
> October probably  - with Intrepid.

Well that's sad. :( I was hoping it would be backported into Hardy.

---

### Post by FranMichaels on 2008-06-22
> **spoons said:**
> Well that's sad. :( I was hoping it would be backported into Hardy.

I was able to build it. However, it has the same issue gnash has always had for me, audio out of sync. Also, the one in the repos (0.8.2) gave me no sound which is even worse. Anyway, using swfdec in the meantime.

Anyway, try your hand at building gnash, it gave very good error messages with ./configure, even the command to install what you are missing. If you've never built any software from source before, make sure to download the ubuntu package build-essential.

[http://www.gnashdev.org/](http://www.gnashdev.org/)

Get the tarball, extract it.
go the directory (gnash-0.8.3)
```
./autogen.sh
```

```
./configure
```
Run this a few times, it will tell you "error you need blah blah, here is the command on debian systems apt-get install packageso on and so forth"

After you get no errors (just some warnings, I didn't get the dependencies needed for the test suite or debugger, shame on me :KS)

Here is the final configure command I used
```
./configure --enable-gui=gtk --disable-debugger --enable-media=ffmpeg
```

from there 
```
make
```

Or if you have a dual-core, make -j2

From there do a sudo make install or checkinstall

It did take a very long time to compile. The longest in my experience I think, even more time than SDLMESS. So be patient. 

Good luck :guitar:

---

### Post by phaed on 2008-06-22
How well does it play YouTube videos?  I know the controls on one of the players didn't work at all.  I will definitely switch when Gnash can handle all Flash objects on YouTube.

Also, does Gnash suffer from the same bug as the Adobe Flash player where drop-down menus get drawn behind Flash objects?  For a good example, go to walmart.com and try the menus.

---

### Post by kahlil88 on 2008-08-11
Is there perhaps an "unofficial" DEB package somewhere?

---

### Post by th3james on 2008-08-11
I can't wait for this (or swfdec) to become a viable alternative to flash, I'm so sick of being adobe dependant (since they made it abundantly clear they don't care about linux (or 64-bit anything...))

As soon as it can play youtube fine, I'm in!

---

### Post by mips on 2008-08-11
> **spoons said:**
> It's been released, but when is it coming to Ubuntu? :)


I no longer use ubuntu & one of the benefits of using a rolling release distro is that you get the new software. Just checked my repos and 0.8.3-2 is available to me :)

---

### Post by circlemaster on 2008-08-14
Second this! I see no reason to keep 0.8.2 as the latest stable, 0.8.3 works much better.

---

### Post by spoons on 2008-08-14
Wow... I wasn't expecting someone else to dig this up, quite a few people are interested in this it seems!

0.8.4 is scheduled for this month according to the gnash wiki. I hope the Ubuntu guys don't neglect to put this one in the repos too. :(

Rolling release mips? Debian Sid? :) Perhaps I'm on the wrong side here!! :lolflag:

---

### Post by the_darkside_986 on 2008-08-14
I believe what is holding back Adobe Flash for 64-bit systems is the open source component--ActionScript core VM, available from the Mozilla Tamarin project. Building it on AMD64 is NOT just a ./configure away, believe me. There is experimental 64-bit code but it doesn't work or compile last time I tried. The proprietary parts of Flash might not be too heavily dependent on 32-bit architecture.

---

### Post by phrostbyte on 2008-08-14
> **the_darkside_986 said:**
> I believe what is holding back Adobe Flash for 64-bit systems is the open source component--ActionScript core VM, available from the Mozilla Tamarin project. Building it on AMD64 is NOT just a ./configure away, believe me. There is experimental 64-bit code but it doesn't work or compile last time I tried. The proprietary parts of Flash might not be too heavily dependent on 32-bit architecture.

Flash is based on a early-mid nineties codebase, I wouldn't be suprised if there is still 16-bit-ish code in it. It's usually easier to add features when you account for them early in the development process.

---

### Post by spoons on 2008-08-14
Perhaps that's why they use a completely different engine for flash 9 compared to flash 8 and below?

---

### Post by mips on 2008-08-15
> **spoons said:**
> 
Rolling release mips? Debian Sid?

Arch Linux.

---

### Post by stmiller on 2008-08-15
> **phaed said:**
> How well does it play YouTube videos?  I know the controls on one of the players didn't work at all.  I will definitely switch when Gnash can handle all Flash objects on YouTube.


Gnash 0.8.3 handles youtube extremely well. And runs wonderfully in a 64bit browser/64bit OS. The bad thing is that CPU spikes to 90%+ to playback youtube with gnash. So slower computers may have some trouble...

---

### Post by insane_alien on 2008-08-15
it can be in hardy now if one of you backports it. thats the beauty of OpenSource. build a deb submit it to the backports team, if it gets accepted the entire community will have access to it.

better yet, join the backports team and do this for any other packages you think are getting a bit behind.

---

### Post by mips on 2008-08-15
> **stmiller said:**
> Gnash 0.8.3 handles youtube extremely well. And runs wonderfully in a 64bit browser/64bit OS. The bad thing is that CPU spikes to 90%+ to playback youtube with gnash. So slower computers may have some trouble...

Have to agree that it performs very well. I have however not noticed the 'spike of death' yet but maybe it has something to do with my quad core or the fact that I'm running 0.8.3-2?

---

### Post by spoons on 2008-08-26
> **insane_alien said:**
> it can be in hardy now if one of you backports it. thats the beauty of OpenSource. build a deb submit it to the backports team, if it gets accepted the entire community will have access to it.

better yet, join the backports team and do this for any other packages you think are getting a bit behind.

I'm rubbish at compiling, any takers? :D

---

### Post by drascus on 2008-08-30
umm I tried compiling this thing via the instructions posted. wow this things a beast. or maybe I am bad at compiling. any who I get this when I run checkinstall...

>  /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libmozsdk.la' '/usr/local/lib/gnash/libmozsdk.la'
/usr/bin/install -c .libs/libmozsdk.so.0.0.0 /usr/local/lib/gnash/libmozsdk.so.0.0.0
(cd /usr/local/lib/gnash && { ln -s -f libmozsdk.so.0.0.0 libmozsdk.so.0 || { rm -f libmozsdk.so.0 && ln -s libmozsdk.so.0.0.0 libmozsdk.so.0; }; })
(cd /usr/local/lib/gnash && { ln -s -f libmozsdk.so.0.0.0 libmozsdk.so || { rm -f libmozsdk.so && ln -s libmozsdk.so.0.0.0 libmozsdk.so; }; })
/usr/bin/install -c .libs/libmozsdk.lai /usr/local/lib/gnash/libmozsdk.la
/usr/bin/install -c .libs/libmozsdk.a /usr/local/lib/gnash/libmozsdk.a
chmod 644 /usr/local/lib/gnash/libmozsdk.a
chmod: changing permissions of `/usr/local/lib/gnash/libmozsdk.a': No such file or directory
make[3]: *** [install-pkglibLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/drascus/Desktop/gnash-0.8.3/plugin/mozilla-sdk'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/drascus/Desktop/gnash-0.8.3/plugin/mozilla-sdk'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/drascus/Desktop/gnash-0.8.3/plugin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK



I couldn't tell what was exactly relevant so I posted a bunch anyway. Does anyone know how to fixes this error so I can finish up my install. I think I got all the dependencies but maybe I missed one. I used the list of build dependencies on this page:

[https://launchpad.net/ubuntu/intrepid/+source/gnash](https://launchpad.net/ubuntu/intrepid/+source/gnash)

OK thanks I hope someone has the solution.

---

### Post by llelectronics on 2008-08-31
I have made unoffical packages for ZevenOS. 
Its 0.8.3 compiled with Gstreamer + the mozilla plugin. 

But be aware somehow the packages screwed up a little bit so gdebi won't work. Only a sudo dpkg -i *.deb works. You need to uninstall 0.8.2 first. 
Maybe someone can take a look at this. Someone with greater knowledge then me ;)

Here are the 3 files. (Don't bother when thereis written something about 0.8.2. I didn't change the control file. As I was lazy that day building the stuff):
[URL="http://zevenos.com/files/gnash/gnash_0.8.3-0ubuntu0_i386.deb"]
http://zevenos.com/files/gnash/gnash_0.8.3-0ubuntu0_i386.deb[/URL]
[http://zevenos.com/files/gnash/gnash-common_0.8.3-0ubuntu0_i386.deb]("http://zevenos.com/files/gnash/gnash-common_0.8.3-0ubuntu0_i386.deb")
[http://zevenos.com/files/gnash/mozilla-plugin-gnash_0.8.3-0ubuntu0_i386.deb]("http://zevenos.com/files/gnash/mozilla-plugin-gnash_0.8.3-0ubuntu0_i386.deb")

---

### Post by ssam on 2008-08-31
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) explains how to request backports (and under what conditions they can happen)

---

### Post by damoxc on 2008-08-31
[http://packages.debian.org/sid/gnash](http://packages.debian.org/sid/gnash)

It's already packaged over in Sid.

---

### Post by Swarms on 2008-08-31
[https://launchpad.net/~gnash/+archive](https://launchpad.net/~gnash/+archive)
Made me able to install 0.8.3 :confused:

---

### Post by drascus on 2008-08-31
Swarms Wow thanks for the link. I now have Gnash installed. just tested it out and it plays videos from every video sharing site I could throw at it. Much appreciated. all I had to do was insert the apt lines and install from synaptic. Absolutely brilliant!!

---

### Post by Swarms on 2008-08-31
I thought I had missed something since people were struggling with compiling and unofficial debs. :P

---

### Post by helliewm on 2008-08-31
Can't get gnash too work in You Tube?

---

### Post by drascus on 2008-08-31
helliewm if you have the version that is in synaptic 0.8.2 you can't watch youtube videos because youtube has changed their flash player. If you use the link swarms provided to add the repository for version 0.8.3 you should be able to play youtube videos. If you can't then you must have done something wrong because it works for me without an issue at all.

---

### Post by helliewm on 2008-09-01
Thanks I was using gnash out of the repos. I did not know that. Will use the latest gnash.

Helen

---

### Post by andrew.46 on 2008-11-26
Hi:

> **drascus said:**
> OK thanks I hope someone has the solution.

Old problem with checkinstall. Try running checkinstall as:

```
checkinstall --fstrans=no
```

and all should be well :-).

  Andrew

---

