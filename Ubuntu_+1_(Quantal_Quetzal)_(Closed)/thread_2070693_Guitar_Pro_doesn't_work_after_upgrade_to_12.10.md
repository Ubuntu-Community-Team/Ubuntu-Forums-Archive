---
title: "Guitar Pro doesn't work after upgrade to 12.10"
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xedi on 2012-10-13
I upgraded yesterday to 12.10 and now guitar pro 6 stopped working. Since I had/have the 64bit version I used [this]("http://askubuntu.com/questions/149951/how-do-i-install-a-32-bit-proprietary-deb-on-a-64-bit-system-without-causing-dep")to install it and guitar pro worked without problems in 12.04.

Now in 12.10 guitar pro will not launch. If I click on the the app through the dash nothing happens happens and if I execute launcher.sh in a terminal, the terminal immediately closes.

Do you have any idea what the cause might be or how to diagnose the problem?

Thanks in advance!

---

### Post by Frogs Hair on 2012-10-13
Did you check compatibility prior to upgrade ? Try opening the the application via the terminal by typing the name and post the output in code tags using # symbol on the reply tool bar. The application is not available in the 12.10 software center and it looks like it was not easy to get running on 12.04.

---

### Post by xedi on 2012-10-13
The app isn't officially compatible with 64bit systems in the first place and since 12.10 is not even out I doubt that there is any official compability with it (A quick google search does not bring any results concerning guitar pro and 12.10).

I tried to run it from the terminal and it just says command not found when I type in GuitarPro which I believe was the name. Also I think normally the program runs by executing the launcher.sh but if I try to execute in the terminal, the terminal immediately closes so I can't even inspect any potential error outputs.

---

### Post by Frogs Hair on 2012-10-13
You should be able to start almost any application from the terminal. Command not found usually indicates the name was not entered correctly. Try lower case. 

The correct package name will be displayed in the synaptic package manager if installed. 12.10 is based on Gnome 3.6 and 12.04 is based on 3.4 so there could be dependency problems.Program compatibility problems occurred during the switch from 3.2 to 3.4 also.

To check compatibility with Gnome 3.6 you would have had contact the developer prior to upgrade. The two main problems are the application is not an official Ubuntu package and not 64 bit compatible. Bug reports for non official applications don't normally get a response.

---

### Post by xedi on 2012-10-14
So I checked the dependencies and for some reason the program does complain:

```
/opt/GuitarPro6$ ldd GuitarPro | grep found./GuitarPro: /opt/GuitarPro6/./libz.so.1: version `ZLIB_1.2.3.3' not found (required by /usr/lib/i386-linux-gnu/libxml2.so.2)

```

Does anybody know what libz.so.1 is and where I can find it? It's not in synaptic...

Edit: Probably it's the other way around, I need zlib for libz.so.1 to work?

---

### Post by offgridguy on 2012-10-14
I haven't heard of Guitar Pro before but am interested to know the capabilities, and what
you like/dislike about it.  Thank's:guitar:

---

### Post by xedi on 2012-10-14
Another problem is, I would like to execute to see launcher.sh to see whether it gives some errors. If I double click in nautilus, then I get an option to run it in an terminal. When I do that, it instantly closes. If I use the terminal and go to the directory and type launcher.sh, then the terminal says command not found. How do I execute the script from the terminal?

Edit: Used sh launcher.sh and it complains about the missing library too: ```
./GuitarPro: /opt/GuitarPro6/./libz.so.1: version `ZLIB_1.2.3.3' not found (required by /usr/lib/i386-linux-gnu/libxml2.so.2)
```

---

### Post by xedi on 2012-10-14
> **offgridguy said:**
> I haven't heard of Guitar Pro before but am interested to know the capabilities, and what
you like/dislike about it.  Thank's:guitar:

It's a tablature software and most sheet music you will find for genres I like are written in guitar pro formats. There is TuxGuitar, a free and open source tablature program, which is compatible with them but not with the newest format .gpx and since tuxguitar doesn't seem to be in development anymore I bought guitar pro 6.

I like it a lot and it's much better than tuxguitar, it has better sounds and a more intuitive interface, basic things like changing tempo or muting selected instruments are obvious e.g.

The only issue I have with it is that it's a pain in the *** to install in a 64bit system. The demo in 64bit and 32bit and the .deb of the full version runs under 32bit fine but in 64bit you have to manually install it and also install some 32bit dependencies, which my guess somehow broke when upgrading from Ubuntu 12.04 to 12.10. It's not hard when you have the guide I linked earlier but it would be nice if they could make an official 64bit version. The company says that they can't because they use some third-party parts but obviously it did work with a workaround so I don't know what the issue is.

---

### Post by Frogs Hair on 2012-10-14
You can check these two sites.

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by mc4man on 2012-10-14
12.10 uses zlib 1.2.7 (if that's an issue), plus I guess you also need the 32 bit version?

You could try 
```
sudo apt-get  install zlib1g:i386
```

Or to see what it entails - (simulate the install
```
sudo apt-get -s install zlib1g:i386
```

---

### Post by xedi on 2012-10-14
It says:

```
zlib1g:i386 is already the newest version.
zlib1g:i386 set to manually installed.

```

Is it possible to downgrade to whatever version Ubuntu 12.04 was using in case that is the problem?

---

### Post by mc4man on 2012-10-14
> **xedi said:**
> It says:

```
zlib1g:i386 is already the newest version.
zlib1g:i386 set to manually installed.

```

Is it possible to downgrade to whatever version Ubuntu 12.04 was using in case that is the problem?

Well you can't have different versions of zlib1g so you'd need to downgrade zlib1g, zlib1g-dev also. Considering how many other packages dep on them that could prove to be problematic.
(if you aren't too attached to your 12.10 install or confident on recovering if things go amiss  then give it a go...

Edit - occasionally in such instances creating a symlink with the name of the .so your app is looking for to the .so that's installed can work

---

### Post by xedi on 2012-10-15
> **mc4man said:**
> 
(if you aren't too attached to your 12.10 install or confident on recovering if things go amiss  then give it a go...

I rather have a working install of Ubuntu 12.10 than getting GP6 to work. I have a second computer I can mess up or where I could install 12.04 again or alternatively I heard that the windows version is supposed to work well in wine.


> Edit - occasionally in such instances creating a symlink with the name of the .so your app is looking for to the .so that's installed can work

How would I do that in detail?

---

### Post by chris billington on 2012-10-16
> **xedi said:**
> I rather have a working install of Ubuntu 12.10 than getting GP6 to work. I have a second computer I can mess up or where I could install 12.04 again or alternatively I heard that the windows version is supposed to work well in wine.




How would I do that in detail?

You'd type:

```
sudo ln -s /lib/i386-linux-gnu/libz.so.1.2.7 /lib/i386-linux-gnu/libz.so.1.2.3.3
```

(Ie create a soft link called libz.so.1.2.3.3, which points to libz.so.1.2.7).

But I tried that and it doesn't work for me, guitar pro still complains with the same error message. I got a hold of the actual libz.so.1.2.3.3 ([https://dl.dropbox.com/u/83002646/libz.so.1.2.3.3](https://dl.dropbox.com/u/83002646/libz.so.1.2.3.3) if you want it, extracted from [http://archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-15ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-15ubuntu1_i386.deb), which won't install with dpkg: not co-installable yadda yadda), but putting that in /lib/i386-linux-gnu/ doesn't have the desired effect either.

I still get:
```
$ /opt/GuitarPro6/launcher.sh
./GuitarPro: /opt/GuitarPro6/./libz.so.1: version `ZLIB_1.2.3.3' not found (required by /usr/lib/i386-linux-gnu/libxml2.so.2)
```

Sigh.

Seriously, I'm pretty ignorant of packaging, but it can't be that hard to bundle it all in with the gp6 installer, keeping all the shared libraries in /opt/GuitarPro6 away from the rest of the system . Clearly they're doing a similar thing for Windows already, so how hard can it be?

---

### Post by chris billington on 2012-10-16
I've made a support question in launchpad answers about the versioning of libxml2 and zlib1g:

[https://answers.launchpad.net/ubuntu/+question/211383](https://answers.launchpad.net/ubuntu/+question/211383)

But I think for the time being I'll be running the Windows version of guitar pro in WINE. Seems to work fine so far.

---

### Post by xedi on 2012-10-17
The issue is not related to 64bit after all, since it doesn't work in Ubuntu Studio 12.10 either with the same error, but it does work in 12.04.

---

