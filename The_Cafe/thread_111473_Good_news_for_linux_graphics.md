---
title: "Good news for linux graphics?"
date: 2006-01-02
forum: The Cafe
---

### Post by NoTiG on 2006-01-02
[http://www.osnews.com/comment.php?news_id=13154](http://www.osnews.com/comment.php?news_id=13154)

I hope all this is ready in time for dapper. And I hope it works on ATI cards! specifically mobility 9600.




"Xcompmgr can currently be run under XGL with full acceleration provided that the proprietary ATI or Nvidia drivers are used. An OpenGL based compositing manager, 'Compiz' is currently in the works and a release is expected in February."

---

### Post by jc87 on 2006-01-02
> Xgl is an X server architecture, started by David Reveman, layered on top of OpenGL via glitz. It is seen as the future of the X.Org Server.

As of February 2005, it is at an early stage in development and a number of important pieces are still missing. X servers using Xgl include Xglx and Xegl. [Wikipedia](http://en.wikipedia.org/wiki/Xgl)

By the way , besides desktop graphics , this could also help to improve proprietary drivers suport?

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=NoTiG][http://www.osnews.com/comment.php?news_id=13154](http://www.osnews.com/comment.php?news_id=13154)

I hope all this is ready in time for dapper. And I hope it works on ATI cards! specifically mobility 9600.
[/QUOTE]

This is great news because people like me can compile it an play with it, but don't get too excited.

Xgl WILL be in the Dapper repos (it is now I think). But it will be like Xcompmgr is today- you use it if you want to play with it and you don't mind crashing.

This stuff won't be the default for at least two or three years. Its hard not to get too excited, but we have to have a level head about it.

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=jc87]
By the way , besides desktop graphics , this could also help to improve proprietary drivers suport?[/QUOTE]

Not really. Xorg 7 cutting up the Xserver code and making the drivers seperate will do the most for making the closed drivers better.

---

### Post by poofyhairguy on 2006-01-03
Expect a guide to play with it as soon as I can.

---

### Post by exclipy on 2006-01-03
For the newbies in this forum, can someone please explain how this fits into [the current scheme of things]("http://ubuntuforums.org/showthread.php?t=75527") and why it's an improvement?  What's the hierarchy between Xgl, Xcompmgr, OpenGL, video drivers and the X server?

---

### Post by GeneralZod on 2006-01-03
[QUOTE=exclipy]For the newbies in this forum, can someone please explain how this fits into [the current scheme of things]("http://ubuntuforums.org/showthread.php?t=75527") and why it's an improvement?  What's the hierarchy between Xgl, Xcompmgr, OpenGL, video drivers and the X server?[/QUOTE]

It's all rather complex, unfortunately - your best bet to grok all of this is to read this:

[http://www.freedesktop.org/~jonsmirl/graphics.html](http://www.freedesktop.org/~jonsmirl/graphics.html)

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=exclipy]For the newbies in this forum, can someone please explain how this fits into [the current scheme of things]("http://ubuntuforums.org/showthread.php?t=75527") and why it's an improvement?  What's the hierarchy between Xgl, Xcompmgr, OpenGL, video drivers and the X server?[/QUOTE]

This helps

[http://www.gnome.org/~seth/blog/relations](http://www.gnome.org/~seth/blog/relations)

Man...I can't get this to install...I will keep trying.

---

### Post by zAo on 2006-01-03
Tried to compile it, but I get
```
checking for XGLSERVER... configure: error: Package requirements (glitz >= 0.5.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XGLSERVER_CFLAGS and XGLSERVER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```
Ubuntu has 4.4
EDIT: 5.2 is in CVS, will try it on my testmachine.

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=zAo]Tried to compile it, but I get
```
checking for XGLSERVER... configure: error: Package requirements (glitz >= 0.5.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XGLSERVER_CFLAGS and XGLSERVER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```
Ubuntu has 4.4
EDIT: 5.2 is in CVS, will try it on my testmachine.[/QUOTE]

Here is info on that 

[http://www.freedesktop.org/wiki/Software_2fXgl](http://www.freedesktop.org/wiki/Software_2fXgl)

---

### Post by One Quick Question on 2006-01-03
I've been trying to compile this beast all day.  After hours wrestling with tracking down dependencies that ./configure didn't bother telling me about, I've hit a wall I can't get past by simple apt-getting and symlinking...

Any of you guys able to compile past hw/xgl/glx/xglxinit.c without getting something like "error: too many arguments to function &#8216;xglxInitXXX&#8217;" ..?

(Edit: Oh, and that was with a *./configure --prefix=/usr --enable-xglserver --enable-xglxserver --enable-glx --enable-xkb*.)

---

### Post by lolocaust on 2006-01-03
[QUOTE=One Quick Question] Well, it started out as one quick question anyway...[/QUOTE]

off topic, but your username and sig made me lol out pretty loud :)

---

### Post by lolocaust on 2006-01-03
[QUOTE=One Quick Question] Well, it started out as one quick question anyway...[/QUOTE]

off topic, but your username and sig made me lol out pretty loud :)

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=One Quick Question]I've been trying to compile this beast all day.  After hours wrestling with tracking down dependencies that ./configure didn't bother telling me about, I've hit a wall I can't get past by simple apt-getting and symlinking...

Any of you guys able to compile past hw/xgl/glx/xglxinit.c without getting something like "error: too many arguments to function ‘xglxInitXXX’" ..?

(Edit: Oh, and that was with a *./configure --prefix=/usr --enable-xglserver --enable-xglxserver --enable-glx --enable-xkb*.)[/QUOTE]

Nope. I hit the same wall.

Looking into it, it seems the only distro that has all the dependancies is Gentoo. Later today I will add an old harddrive to my rig and install Gentoo so I can try it out and get some screenshots.

The odds of my making a guide to install this thing in Breezy is very low as of now...its just too hard.

---

### Post by One Quick Question on 2006-01-03
[QUOTE=lolocaust]off topic, but your username and sig made me lol out pretty loud :)[/QUOTE]
:) Thanks, that made my day.

Well, 3++ hours of C++ hacking and tomfoolery, and I am no closer to getting this thing compiled. (Not that I'm a wizard at this stuff or anything.)  I've managed to change the error message several times, getting a few more chunks of delicious gcc output with each attempt, but there are too many loose ends that are whipping the motivation out of me.  I wanted this thing to just make.

What it does make is me pretty suspicious of the thing, to be honest.  I'm thinking the point of the source code was to make people excited who were once upset about the "closed doors" thing.   That is, the xgl-svn_100.tar.bz2 file was a show of open-source freedom and happiness, not a show of an awesome XGL exhibition.

Or at least that's how I'm feeling about it right now.  (i.e., a little grumpy and frustrated.)

---

### Post by poofyhairguy on 2006-01-03
[QUOTE=One Quick Question]:) Thanks, that made my day.

Well, 3++ hours of C++ hacking and tomfoolery, and I am no closer to getting this thing compiled. (Not that I'm a wizard at this stuff or anything.)  I've managed to change the error message several times, getting a few more chunks of delicious gcc output with each attempt, but there are too many loose ends that are whipping the motivation out of me.  I wanted this thing to just make.

What it does make is me pretty suspicious of the thing, to be honest.  I'm thinking the point of the source code was to make people excited who were once upset about the "closed doors" thing.   That is, the xgl-svn_100.tar.bz2 file was a show of open-source freedom and happiness, not a show of an awesome XGL exhibition.

Or at least that's how I'm feeling about it right now.  (i.e., a little grumpy and frustrated.)[/QUOTE]

Don't worry about it too much. I can almost promise that if the code makes it into teh cvs soon it will enter dapper's universe.

I might wait till its in CVS myself.

---

