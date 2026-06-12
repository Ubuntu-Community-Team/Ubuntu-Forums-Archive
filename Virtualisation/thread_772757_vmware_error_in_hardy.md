---
title: "vmware error in hardy"
date: 2008-04-28
forum: Virtualisation
---

### Post by tlacuache on 2008-04-28
I just upgraded from Gutsy to Hardy. I'm using VMWare Workstation. Running vmware-config.pl, I first got an error about vmmon not compiling, so I googled around and found vmware-any-any-update-116.tgz and was then able to build and install the modules just fine.

However, when running vmware, I got these errors:

```

$ vmware
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

After googling around some more, and after finding [this thread]("http://ubuntuforums.org/showthread.php?t=770873"), I did the following:

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

However, now I get these errors:
```
$ vmware
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fe8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6fe88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7e661bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xb7d56969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xb7d56f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9c180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9cd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b7924f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b78b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7f77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c92459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c7a3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c7a076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c916eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xb7c90d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xb7c910b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fe8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6fe881e]
#2 /usr/lib/libX11.so.6 [0xb7e65518]
#3 /usr/lib/libX11.so.6(XAddExtension+0x2c) [0xb7e48c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xb7d4eed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d4d8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d4dd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xb7d4dec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9a9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9cd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b7924f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b78b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7f77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c92459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c7a3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c7a076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Anyway, I'm quite stuck. I don't want to have to go back to 7.10. Please help!

-Thanks,

Seth

---

### Post by tlacuache on 2008-04-28
Well, after messing around with the gtkrc file in question I got rid of that error, but the other error (about the assertion failure and whatnot) is still there.

Interestingly enough, I can run vmware-console-server and connect to remote VMs fine.

Any help on this would still be much appreciated!

-sg

---

### Post by vsritual on 2008-04-28
This command fixed my problem... I read it somewhere else.  



vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

---

### Post by tlacuache on 2008-04-28
Thanks, but I already did something to this effect as you can see in my original post. That got me past the first set of errors, but I've still got the others.

In the meantime I'm using VMWare Server until I can hopefully figure this out.

---

### Post by strakarpickup on 2008-04-29
> **vsritual said:**
> This command fixed my problem... I read it somewhere else.  



vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1


Thank you!

That solved my problem also.

:guitar:

---

### Post by RWT711 on 2008-04-29
This one worked for me too. Thanks!:guitar:

---

### Post by deltakilo on 2008-04-29
I also ran into problems getting VMWare Server to start after upgrading to 8.04

I was able to resolve the issue by first using vmware-any-any-update-116 update found here [http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)

And then running these commands:
```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

---

### Post by raigorodski on 2008-04-29
Jesus Man! I was stuck with this mess about a month.(liar!!!:lolflag:)


Really THANK You!!!

---

### Post by sonnywise on 2008-05-03
> **strakarpickup said:**
> Thank you!

That solved my problem also.

:guitar:

I had the same problem and it has been solved using these 2 copy lines you wrote.

Thak you.

---

### Post by HFC01 on 2008-05-07
This worked for me after a bit of searching on Google.  It´s mostly in Japanese but you can figure it out (unless you are Japanese of course when it will make perfect sense).

[http://forum.ubuntu.org.cn/viewtopic.php?p=672855&sid=268311fd879245582a40d28af7de53d8](http://forum.ubuntu.org.cn/viewtopic.php?p=672855&sid=268311fd879245582a40d28af7de53d8)

My vmware tools now work perfectly.

---

### Post by Dubbayoo on 2008-05-10
> **vsritual said:**
> This command fixed my problem... I read it somewhere else.  



vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

This command works for me using vmware server. Apparently it does not work for vmware workstation.

---

### Post by dlobo on 2008-05-12
tlacuache,

Can you explain what you did to the gtkrc file? I posted about this problem about two weeks ago. The only difference for me is that I can only run vmware as sudo, I don't even get an error when I do so. I even uninstalled the previous vmware version I had (1.4.0) and installed 1.5.0, but the problem is still there.

Thanks a lot

dmlobo

---

### Post by tlacuache on 2008-05-12
IIRC, I went through the gtkrc file and replaced variables for colors (@fg_color, etc.) with their actual values instead. 

But, like I said, I still had the assertion error. I've tried the things mentioned by the other posters in this thread (thank you, by the way) but it didn't fix my problem.

I got fed up with it and just installed VMWare Server instead, and it's been working fine for me. The only thing I feel slightly bad about is that the VMWare Workstation my company bought for me a few years ago is now completely unused. That and the lack of multiple snapshots.

-sg

---

### Post by greenthumbtacks on 2008-05-12
> **tlacuache said:**
> I just upgraded from Gutsy to Hardy. I'm using VMWare Workstation. Running vmware-config.pl, I first got an error about vmmon not compiling, so I googled around and found vmware-any-any-update-116.tgz and was then able to build and install the modules just fine.

However, when running vmware, I got these errors:

```

$ vmware
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

After googling around some more, and after finding [this thread]("http://ubuntuforums.org/showthread.php?t=770873"), I did the following:

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

However, now I get these errors:
```
$ vmware
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fe8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6fe88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7e661bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xb7d56969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xb7d56f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9c180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9cd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b7924f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b78b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7f77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c92459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c7a3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c7a076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c916eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xb7c90d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xb7c910b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fe8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6fe881e]
#2 /usr/lib/libX11.so.6 [0xb7e65518]
#3 /usr/lib/libX11.so.6(XAddExtension+0x2c) [0xb7e48c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xb7d4eed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d4d8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d4dd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xb7d4dec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9a9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b9cd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b7924f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b6cc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b78b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7d586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7f77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c92459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c7a3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c7a076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Anyway, I'm quite stuck. I don't want to have to go back to 7.10. Please help!

-Thanks,

Seth

Looks like you pointed the libraries used by your system to the libraries used by vmware.  It's not a good idea to link libs in /lib or /usr/lib to app specific sub folders like that unless you really know what you are doing.  I suggest reinstalling those libs that you sym-linked, libgcc and libpng, with apt or whatever.

As for the vmware issue this fix worked for me

[http://www.cryptolife.org/2008/04/26/vmware-server-and-ubuntu-hardy-heron/]("http://www.cryptolife.org/2008/04/26/vmware-server-and-ubuntu-hardy-heron/")

---

### Post by Twigman on 2008-05-13
> **tlacuache said:**
> I just upgraded from Gutsy to Hardy. I'm using VMWare Workstation. Running vmware-config.pl, I first got an error about vmmon not compiling, so I googled around and found vmware-any-any-update-116.tgz and was then able to build and install the modules just fine.

However, when running vmware, I got these errors:

I had exactly the same problem... try this:

sudo rm -Rf /usr/lib/vmware/lib/libgcc_s.so.1

Daniel..

---

### Post by nssone on 2008-07-21
I know I'm bumping up an old thread but this is relevant to my attempts here. I was getting those same header file errors so I tried those file overwrite/delete commands but I keep getting this afterward:

process 14779: Attempt to remove filter function 0xb6a93cd0 user data 0x88bdbb0, but no such filter has been added

Any ideas?

---

### Post by lizman on 2008-08-26
I got the same error.
Solved the problem by just deleting the file "/usr/lib/vmware/lib/libgcc_s.so.1"

---

### Post by hofa on 2008-09-20
Thank you for the two cp-lines. It worked perfectly for me!

---

### Post by bitlink on 2008-09-27
> **vsritual said:**
> This command fixed my problem... I read it somewhere else.  

vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1


This "fix" is also applicable, with a slight variation, for vmware-server-console, if you are installing that independantly. Just adjust the path in each of the commands to replace vmware with vmware-server-console. This worked for me in Ubuntu 8.0.4 installing vmware-server-console 1.0.7-108231.

Thanks.

---

### Post by erny on 2008-10-07
> **bitlink said:**
> This "fix" is also applicable, with a slight variation, for vmware-server-console, if you are installing that independantly. Just adjust the path in each of the commands to replace vmware with vmware-server-console. This worked for me in Ubuntu 8.0.4 installing vmware-server-console 1.0.7-108231.

Thanks.
I had the same problem with vmware-server 1.0.7.
I just removed the two files:
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

The explanation may be the following:
VMware is redistributed with most of the libraries, but not with libcairo2. But when using xgl or a vectorial X backend, libcairo is needed.
libcairo2 is linked to whatever it was compiled with, which does not match the libraries in /usr/lib/vmware/lib. Removing or renaming the files should be enough so that the dynamic load gets the default versions of the libs.

---

### Post by fistcar on 2008-10-24
> **vsritual said:**
> This command fixed my problem... I read it somewhere else.  



vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

This worked for me. I am using VMware Server 1.0.6 build-91891 on:
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

### Post by vakili on 2008-12-19
> **vsritual said:**
> This command fixed my problem... I read it somewhere else.  



vsr@localhost:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

vsr@localhost:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1


Thanks alot Man, It solved my problem too! 
Vakili

---

### Post by spiderwort on 2008-12-28
Thanks to everyone who contributed to this thread! This solution worked great for me as well.

Further note that someone might find of interest:
1. VMWare Server 1.0.8 build 126538
2. 64-bit Hardy, so some of my paths were slightly different
3. I linked the files instead of copying. *shrug* Time will tell which method is better.

........Spiderwort

---

