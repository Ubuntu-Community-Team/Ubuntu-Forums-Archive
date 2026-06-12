---
title: "Can only run VMWare Server as sudo after upgrade to Hardy"
date: 2008-05-01
forum: Virtualisation
---

### Post by dlobo on 2008-05-01
Greetings all y'all,

I just upgraded to Ubuntu 8.04 from 7.10 and ever since I have been having issues running VMWare Server.
I have read the multiple threads existing on this forum about the issues of running VMWare on Hardy, but I haven't seen this one yet.
So I ran runme.pl applied the any-to-any116 update and I am finally to start the VMWare Console but only when I do it from the command line like this: sudo vmware.
If I try to run it without sudo I get the following error:
****
terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
/usr/share/themes/ClearlooksClassic/gtk-2.0/gtkrc:34: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6fb58b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7e341bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xb7d24969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xb7d24f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b6a180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b6ad2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b3ac14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b4724f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b3ac14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b46b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4b298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4b586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4d77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c60459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c483a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c48076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c5f6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xb7c5ed46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xb7c5f0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6fb581e]
#2 /usr/lib/libX11.so.6 [0xb7e33518]
#3 /usr/lib/libX11.so.6(XAddExtension+0x2c) [0xb7e16c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xb7d1ced7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d1b8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d1bd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xb7d1bec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b689b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b6ad75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b3ac14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b4724f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b3ac14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b46b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4b298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4b586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a4d77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c60459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c483a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c48076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
****
Note how it complains about Clearlooks theme, but it doesn matter what theme I am using at the time I want to launch vmware, I will get the same error, it will just change the name of the theme.
Any thoughts about how to fix this? I am not happy to run vmware as sudo. :-(

Thanks a lot

dmlobo

---

### Post by Kokopelli on 2008-05-02
This is a shot in the dark but try

```
sudo chown -R `whoami`:`whoami` ~/.vmware
```

---

### Post by dlobo on 2008-05-06
Kokopelli,

I tried your suggestion but it didn't have any effect. Still no luck.

Thanks anyway

dmlobo

---

### Post by tombrus on 2008-05-15
I have exactly the same problem. Any ideas, anyone?

---

### Post by fjgaude on 2008-05-15
Did everybody add these two lines:

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

after installing?

---

### Post by tombrus on 2008-05-15
Yes, I did.

---

### Post by fjgaude on 2008-05-15
> **tombrus said:**
> Yes, I did.

If you installed vmware VMs in /var/lib/vmware/Virtual Machines then you might try this:

```
sudo chmod -R <login>:<login>/var/lib/vmware/Virtual Machines
```

If you can't remember where, go to /var/lib/vmware and see what's there. Check permissions to make sure it isn't "root".

I've never had to do this but it might work.

Let us know what happens.

---

### Post by tombrus on 2008-05-15
I guess you mean [COLOR="DarkRed"]chown[/COLOR] not [COLOR="DarkRed"]chmod[/COLOR]...

I checked, they are all tom:tom...

-Tom

Thanks for helping out by the way, I appreciate it :)

---

### Post by fjgaude on 2008-05-15
Yes, I did mean chown... one more to check permissions on: /etc/vmware. See if that isn't "root".

Also do you have a icon in Applications/System Tools or /Other menus?

---

### Post by tombrus on 2008-05-15
On /etc/vmware:```
$ ls -laR /etc/vmware
/etc/vmware:
total 364
drwxr-xr-x   6 root root   4096 2008-05-15 14:09 .
drwxr-xr-x 144 root root  12288 2008-05-15 22:22 ..
-rw-r--r--   1 root root    824 2008-05-15 14:09 config
-r-xr-xr-x   1 root root  16606 2008-05-15 11:30 installer.sh
-rw-r--r--   1 root root    375 2008-05-15 11:40 license.vs.1.0-00
-rw-r--r--   1 root root 289040 2008-05-15 12:48 locations
-rw-r--r--   1 root root     86 2008-05-15 11:43 netmap.conf
drwxr-xr-x   2 root root   4096 2008-05-15 11:30 pam.d
-r--r--r--   1 root root    182 2008-05-15 11:30 signing-key.pub
drwxr-xr-x   2 root root   4096 2008-05-15 11:37 ssl
-rw-r--r--   1 root root    139 2008-05-15 11:43 vm-list
-rw-r--r--   1 root root     87 2008-05-15 11:43 vm-list-private
drwxr-xr-x   3 root root   4096 2008-05-15 11:37 vmnet1
drwxr-xr-x   4 root root   4096 2008-05-15 11:36 vmnet8

/etc/vmware/pam.d:
total 12
drwxr-xr-x 2 root root 4096 2008-05-15 11:30 .
drwxr-xr-x 6 root root 4096 2008-05-15 14:09 ..
-rw-r--r-- 1 root root  246 2008-05-15 11:30 vmware-authd

/etc/vmware/ssl:
total 16
drwxr-xr-x 2 root root 4096 2008-05-15 11:37 .
drwxr-xr-x 6 root root 4096 2008-05-15 14:09 ..
-r--r--r-- 1 root root 1204 2008-05-15 11:37 rui.crt
-r-------- 1 root root  887 2008-05-15 11:37 rui.key

/etc/vmware/vmnet1:
total 12
drwxr-xr-x 3 root root 4096 2008-05-15 11:37 .
drwxr-xr-x 6 root root 4096 2008-05-15 14:09 ..
drwxr-xr-x 2 root root 4096 2008-05-15 11:40 dhcpd

/etc/vmware/vmnet1/dhcpd:
total 16
drwxr-xr-x 2 root root 4096 2008-05-15 11:40 .
drwxr-xr-x 3 root root 4096 2008-05-15 11:37 ..
-r--r--r-- 1 root root  748 2008-05-15 11:37 dhcpd.conf
-rw-r--r-- 1 root root  417 2008-05-15 11:40 dhcpd.leases
-rw-r--r-- 1 root root    0 2008-05-15 11:37 dhcpd.leases~

/etc/vmware/vmnet8:
total 16
drwxr-xr-x 4 root root 4096 2008-05-15 11:36 .
drwxr-xr-x 6 root root 4096 2008-05-15 14:09 ..
drwxr-xr-x 2 root root 4096 2008-05-15 11:40 dhcpd
drwxr-xr-x 2 root root 4096 2008-05-15 11:36 nat

/etc/vmware/vmnet8/dhcpd:
total 16
drwxr-xr-x 2 root root 4096 2008-05-15 11:40 .
drwxr-xr-x 4 root root 4096 2008-05-15 11:36 ..
-r--r--r-- 1 root root  765 2008-05-15 11:36 dhcpd.conf
-rw-r--r-- 1 root root  417 2008-05-15 11:40 dhcpd.leases
-rw-r--r-- 1 root root    0 2008-05-15 11:36 dhcpd.leases~

/etc/vmware/vmnet8/nat:
total 12
drwxr-xr-x 2 root root 4096 2008-05-15 11:36 .
drwxr-xr-x 4 root root 4096 2008-05-15 11:36 ..
-r--r--r-- 1 root root 1245 2008-05-15 11:36 nat.conf

```Nothing wrong with that as far as I can see, or am I missing something?

Yes I have an icon in Application/Other but I get the error output mentioned above when I start vmware from the command line as well and (as above) when I do 'sudo vmware' it works just fine. I am not too happy running the whole thing as root, it just does not feel right.

-Tom

---

### Post by fjgaude on 2008-05-15
Looks good to me... but what do I know?

Do you get the same error message that poster "dlobo" gets when you go non-sudo?

---

### Post by tombrus on 2008-05-16
Not exactly, but close enough I think:```
$ vmware
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6fd6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6fd68b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e551bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d45969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d45f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8b180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8bd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b5bc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b6824f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b5bc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b67b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6c298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6c586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6e77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c81459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c693a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c69076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c806eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c7fd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c800b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6fd6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6fd681e]
#2 /usr/lib32/libX11.so.6 [0xf7e54518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e37c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d3ded7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d3c8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d3cd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d3cec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b899b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8bd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b5bc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b6824f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b5bc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b67b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6c298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6c586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6e77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c81459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c693a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c69076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```
only some adresses diff and lib v.s. lib32 and he gets some more messages first.

-Tom

---

### Post by fjgaude on 2008-05-16
Are you running 64- or 32-bit Ubuntu?

You did follow every step in the Sticky, eh?

---

### Post by tombrus on 2008-05-16
I am running 64 bit. Eh, yes I followed every step of   the page [http://ubuntuforums.org/showthread.php?t=770873]("http://ubuntuforums.org/showthread.php?t=770873")...

---

### Post by fjgaude on 2008-05-16
Gosh, I'm at a loss... except to re-install vmware, of course leaving the vm you created intack.

---

### Post by altonbr on 2008-05-18
A gentlemen named 'p388l3s' over on my VMware script thread has possibly found a fix: [http://ubuntuforums.org/showthread.php?p=4986139](http://ubuntuforums.org/showthread.php?p=4986139)

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loader
```

The difference between that and my code:

```
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

Is the **l3232**. If you can test that fix and tell me if it works that would be greatly appreciated!

---

### Post by fjgaude on 2008-05-18
I can't test the code but it has worked for many folks here on the forums... I can't see what you have to lose... try it and if it doesn't solve the problem re-run the old one.

That 3232 is not good for Hardy 8.04, this we know. If one installs Hardy and then installs vmware and uses the Sticky to do it, then I believe all would be okay. It's the upgrading that gets us all into trouble. Just too complicated to get everything right.

Let us know what happens.

---

### Post by tombrus on 2008-05-18
I do not see this point of this editing. The libgtl2.0-0.loaders file on my machine only contains references to '/usr/lib32/' (no other '/usr/' refs in there). So the l3232 script above would not do anything. Furthermore the second sed command you mention would change these refs into '/usr/l3232' refs, but the only /usr/l* dirs on my machine are: /usr/lib  /usr/lib32  /usr/lib64  /usr/local. No /usr/l32 or /usr/l3232 around. 

Imho the scripts are pretty senseless. Please explain what you try to accomplish.

-Tom

---

### Post by fjgaude on 2008-05-18
> **tombrus said:**
> I do not see this point of this editing. The libgtl2.0-0.loaders file on my machine only contains references to '/usr/lib32/' (no other '/usr/' refs in there). So the l3232 script above would not do anything. Furthermore the second sed command you mention would change these refs into '/usr/l3232' refs, but the only /usr/l* dirs on my machine are: /usr/lib  /usr/lib32  /usr/lib64  /usr/local. No /usr/l32 or /usr/l3232 around. 

Imho the scripts are pretty senseless. Please explain what you try to accomplish.

-Tom

Well, those commands were used before Hardy was released. They were for beta users to assist in getting a 64-bit OS to recognize a 32-bit library file of vmware. Here's what the original recommend was:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

Let me you I'm about as confused as anyone... the beta and alpha usage by regular users starts a wave of bug fixes that sooner or later may not be needed in the final release. This is one of them.

---

