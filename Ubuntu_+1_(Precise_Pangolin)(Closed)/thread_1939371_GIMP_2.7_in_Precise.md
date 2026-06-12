---
title: "GIMP 2.7 in Precise?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
Is there a way to install GIMP 2.7 (preferably 2.7.5) in Precise? If yes, how? I just can't get around dependencies problem.

---

### Post by VinDSL on 2012-03-11
> **&#1058 said:**
> Is there a way to install GIMP 2.7 (preferably 2.7.5) in Precise? If yes, how? I just can't get around dependencies problem.
I've been running Gimp 2.7.5 (unstable) for quit a while.

And, I love the changes!  Day n' night difference...

Personally, I'm using the matthaeus123/mrw-gimp-svn repo.

LINKAGE:  [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

Which one are you using?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
I tried using the same repository, but it seems that there's no support for Precise 12.04 in it. And indeed, if you go to

[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/)

you will see four Ubuntu distros folders, but not Precise among them.

With this repository enabled, if I try to install GIMP from Synaptic, I get an error:
```
Could not apply changes!
Fix broken packages first.
```
And when I try to fix broken packages, I get:
```
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```
How did you manage to install GIMP 2.7 on your Ubuntu Precise 12.04?

---

### Post by sgage on 2012-03-11
Just edit the repo entry to oneiric instead of precise. It's easy to do in Synaptic. I use a couple of ppa's that require the edit.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
I did that too, but it didn't help. I still get the same error.

But now that you mentioned it, I went and checked the repository, and it seems that now Precise is among the supported distros. So I changed my repo from Oneiric to Precise. Unfortunately, now I get a different error:
```
gimp:
  Depends: libgimp2.0 (<=2.6.12-z) but 2.7.5-2012020901~oo is to be installed
  Depends: gimp-data (<=2.6.12-z) but 2.7.5-2012020901~oo is to be installed
```

---

### Post by ajgreeny on 2012-03-11
I presume you have refreshed your repos?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
Yes I did. But I forgot to try to fix my broken packages again. So after changing my repo to Precise, I fixed the packages and that way I finally managed to install GIMP 2.7.5. However, now I simply can't run it. When I type GIMP in Dash, the GIMP icon shows, but when I click on it, nothing happens. In the System Monitor GIMP process doesn't even show. What gives? :(

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
And now I've noticed a strange thing. Although I have Matthaeuss's repository enabled, in Synaptic version of GIMP shows as 2.6.12. And a few moments (and a reboot) ago I'm sure it was 2.7.5.

---

### Post by ajgreeny on 2012-03-11
You probably need to edit the shortcut command to gimp in your menu from **gimp-2.6 %U** to **gimp-2.7 %U** but I am not sure how you manage to do that in unity; is the menu-editor still available?  If so that will do it.

---

### Post by VinDSL on 2012-03-11
> **ajgreeny said:**
> You probably need to edit the shortcut command to gimp in your menu from **gimp-2.6 %U** to **gimp-2.7 %U** but I am not sure how you manage to do that in unity; is the menu-editor still available?  If so that will do it.
Type *Main Menu* into the Dash.  ;)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
Well, I actually tried re-installing GIMP (uninstalling and then installing again), but after some more hassle with version numbers, I can't install 2.7 again. When I mark it for installation, I get this error:
```
gimp:
 Depends: libgimp2.0 but it is not going to be installed
 Depends: libgimp2.0 but it is not going to be installed
 Depends: libpoppler-glib6 (>=0.16) but it is not installable
```
When I try to install libgimp2.0, I get a message saying I should fix broken packages. When I try to do it, I get this:
```
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```
And libpoppler-glib6 is not even available for me to install. Although I have libpoppler-glib8 installed.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
> **VinDSL said:**
> Type *Main Menu* into the Dash.  ;)

I don't get any results if I type 'Main Menu'. Although, as I mentioned, that wouldn't help me now.

---

### Post by VinDSL on 2012-03-11
> **&#1058 said:**
> I can't install 2.7 again. When I mark it for installation, I get this error:
```
gimp:
 Depends: libgimp2.0 but it is not going to be installed
 Depends: libgimp2.0 but it is not going to be installed
 Depends: libpoppler-glib6 (>=0.16) but it is not installable
```
Aha!  That rang a bell...  :)

My Gimp 2.7.5 install is using libgimp2.0 version 2.7.5-2012020901~oo

The most recent version is 2.7.5-2012020902~oo but it refuses to upgrade.

So, I leave it unchanged (waiting for a fix) since Gimp is running just fine.

Don't know what the workaround would be, off the top of my head.

---

### Post by mc4man on 2012-03-11
You're goig to see 2 issues with that ppa - 
First - libpoppler-glib6  is now libpoppler-glib8
2nd - libgimp2.0 depends on libglib2.0 but it is now named libglib2.0-0

Unlees you want to build the gimp source you may wish to wait till the ppa does a 12.04 build which I'm sure it will

---

### Post by VinDSL on 2012-03-11
Ahoy!  There she blows...  LoL!

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+build/3199880](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+build/3199880)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
> **mc4man said:**
> Unlees you want to build the gimp source you may wish to wait till the ppa does a 12.04 build which I'm sure it will

I'm not sure if I'd be able to "build the gimp source" (don't even know what that means :( ). I know the repo will get Precise support (sooner or later), I just hoped I shouldn't wait any longer. And since VinDSL said he managed to install GIMP 2.7.5 on Precise using that same repository, I hoped I could do it too.

Well, thanks anyway, I guess this problem goes to my mile-long "wait for a possible solution" problems liset. :-?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-11
> **VinDSL said:**
> Ahoy!  There she blows...  LoL!

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+build/3199880](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+build/3199880)

Oh yeah, and on top of everything, I'm also having some problems with my stupid ISP - I can't access Launchpad for the whole day! Morons...

---

### Post by mc4man on 2012-03-12
> **VinDSL said:**
> Aha!  That rang a bell...  :)

My Gimp 2.7.5 install is using libgimp2.0 version 2.7.5-2012020901~oo

The most recent version is 2.7.5-2012020902~oo but it refuses to upgrade.

So, I leave it unchanged (waiting for a fix) since Gimp is running just fine.

Don't know what the workaround would be, off the top of my head.

Whether the ppa could be now used is still debatable but what happened was the latest build ended up having a double dep for libgimp2, that obviously can't be satisfied 

libglib2.0-0 (>= 2.30.2), libglib2.0 (>= 2.30.2)

There's still the question of the libpoppler-glib version, anyway I'm sure Matt will do a new build at some point not to distant

*rebuilt his source here for 12.04 & all seems fine, the 'all in one window' is very nice on unity

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-12
Well, um... That still isn't telling me how to install it. Can you please give any more information?

---

### Post by VinDSL on 2012-03-12
> **mc4man said:**
> *rebuilt his source here for 12.04 & all seems fine, the 'all in one window' is very nice on unity
I L-O-V-E Gimp 2.7.5!

It was perfectly usable before, but...

I've always left claustrophobic, in a multi-window Gimp workspace.

Single-Window Mode with Hidden Docks (and tabs) RAWKS!  :D

---

### Post by VinDSL on 2012-03-12
> **&#1058 said:**
> Well, um... That still isn't telling me how to install it. Can you please give any more information?
I don't know exactly what *your* workaround would be.

Here's a screenie of the Gimp 2.7.5 install... from Synaptic... inside a Gimp window.  LoL!


[INDENT][[IMG]http://vindsl.com/images/vindsl-gimp2.7.5-11-mar-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-gimp2.7.5-11-mar-2012-2.png")[/INDENT]


However you can get to that collection... or, compile from source, like mc4man said...  ;)

---

### Post by jampe on 2012-03-14
Install Gimp from source.

This should work for any Gimp and Linux version: [http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)

Just follow every step carefully and remember to replace gimp 2.7.2 with 2.7.5 and gegl 0.1.6 with 0.1.8. Worked beautifully for me, it even loads quicker than gimp 2.6 :D

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-14
jampe thank you so much for answering my question at last. I'll give it a try.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-15
I finally got 2.7.5 working on my 12.04b1! Thank you jampe once again! I've learned a lot from the instructions you referred me to. I'll just add that in the compilation instruction I had to change the very last command from:
```
make install -j5
```
to:
```
sudo make install
```
Now, if I run GIMP from /opt/gimp-2.7.5/bin/gimp-2.7 it runs fine. But it's not showing if I want to run it from Dash. How do I get GIMP in my dash?

Thanks again.

---

### Post by zika on 2012-03-15
I'm using Gimp from [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn) in Precise...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-15
> **zika said:**
> I'm using Gimp from [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn) in Precise...
&#1046;&#1080;&#1082;&#1086; &#1078;&#1080;&#1074;&#1086;&#1090;&#1072; &#1090;&#1080; how did you manage to do it? I've been getting the errors mentioned earlier in this thread.

---

### Post by zika on 2012-03-15
> **&#1058 said:**
> &#1046;&#1080;&#1082;&#1086; &#1078;&#1080;&#1074;&#1086;&#1090;&#1072; &#1090;&#1080; how did you manage to do it? I've been getting the errors mentioned earlier in this thread.It was some time ago. Before this libgimp2.0 arrived. I think it will be solved in a day or so, judging from one other thread (as I recall)...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-15
Either way, now it doesn't matter to me any more. I've got it working thanks to jampe's assistance.

---

### Post by jampe on 2012-03-18
@&#1058;&#1086;&#1084;&#1080;&#1094;&#1072;: To get it in your dash, create the file gimp-2.7.desktop in your /usr/share/applications directory

```

sudo gedit /usr/share/applications/gimp-2.7.desktop

```

..paste this into the file..

```

[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP Image Editor (2.7)
GenericName=Image Editor
Comment=Create images and edit photographs
Comment=GIMP
Exec=/opt/gimp-2.7/bin/gimp-2.7
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
StartupNotify=true

```

..and save the changes.

The launcher should show up in the dash from now on.

---

### Post by jampe on 2012-03-18
By the way, if anyone reading this thread in the future is having trouble compiling babl, check out this site: [http://www.linuxfromscratch.org/blfs/view/svn/general/babl.html](http://www.linuxfromscratch.org/blfs/view/svn/general/babl.html).
And this one for gegl: [http://www.linuxfromscratch.org/blfs/view/svn/general/gegl.html](http://www.linuxfromscratch.org/blfs/view/svn/general/gegl.html)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-18
jampe, you're a wizzard! :-({|=

---

### Post by jampe on 2012-03-18
Heh, thank you :)

---

