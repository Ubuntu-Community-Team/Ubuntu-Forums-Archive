---
title: "Cocos2D-X: &quot;X Error of failed request: BadMatch&quot; runtime error"
date: 2016-04-16
forum: Ubuntu Application Development
---

### Post by givemeanthony on 2016-04-16
I'm trying to compile a Cocos2D-X project on Ubuntu running in Parallels 11. I'm getting a strange "X Error of failed request: BadMatch" error. By the look of the error, I thought maybe there was some issue with GLX; so I ran glxgears but that works just fine (as you can see in the screenshot). Also note, this project is over a virtual network share. /media/psf simply points to my user directory on my macbook pro.

[IMG]http://i.imgur.com/7o4Nk2Q.png[/IMG]

I was going to post this in the Cocos2D-X fora, but they're having issues with their registration form. Hopefully, someone here can help me. I've found this issue posted online in a few places, but no answers were given.

[B][SIZE=5]UPDATE 05/18/2015 1:17pm:[/SIZE]
[/B]
I did a bit of digging a found out some key information. The man page for glxmakecurrent(3) shows that a BadMatch error is created if *drawable* was not created with the same X screen and visual as *ctx*. It is also created if *drawable* is **None** and ctx is _not_ **NULL**.
[I]
drawable: a [/I][COLOR=#000000][FONT=arial]GLX drawable. An X window or GLX pixmap.
[/FONT][/COLOR]*[FONT=arial][COLOR=#000000]ctx: [/COLOR][/FONT]*[FONT=arial][COLOR=#000000]a GLX rendering context that is to be attached to [/COLOR][/FONT]*drawable*[FONT=arial][COLOR=#000000].

The end of my /var/log/Xorg.0.log file shows the following after compiling my program:[/COLOR][/FONT]
```
[  6542.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[  6542.351] (II) PRLCONTROL: GL PBuffer(this=0x7fa6acdab620, host_pbuf=57153A74, glxId=5000006, drawId=5000005, GLXDrawablePtr=0x7fa6a93a42e0, DrawablePtr=0x7fa6abd493a0, tex_fmt=20DA, tex_tgt=20DC) created
[  6542.357] (II) PRLCONTROL: GL PBuffer(this=0x7fa6acdab620, host_pbuf=57153A74 tex_tgt=20DC) destroyed
```

[B][SIZE=5]UPDATE 04/23/2015 10:30PM:
[/SIZE][/B]I've been posting in the Cocos2D-x forum regarding this issue. Another user from a few years ago had the issue on Ubuntu 12 and I grave-dug the post, relating it to Ubuntu 14. The issue most definitely has to do with Parallels' graphical incompatibility with Ubuntu. The solution is to abandon Parallels 11 for VMWare Fusion 8. DO NOT migrate your virtual machine, create a brand new one. Visit this topic on the [Cocos2D-X forum]("http://discuss.cocos2d-x.org/t/all-of-the-samples-in-ubuntu12-04-get-crash/8843").

---

