---
title: "SEQ24 Problem"
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by dawiba on 2009-04-24
I upgraded to Jaunty yesterday and decided the time was right to try making music on Ubuntu after reading various comments about the real time kernel working properly in 9.04 as opposed to 8.10.

So, I downloaded and installed the rt kernel, Jack Control then Ardour for audio and Seq24 for midi. I also downloaded a couple of others like Jack Rack, Jack EQ, Jamin and Hydrogen, all from the repositories.

I normally work by playing what I want on my keyboard and recording this into the computer as midi. Then I'll play this back and use the keyboard to generate the sounds that I want. This suits me because it's an easy way to fix mistakes and also to change sounds if I want. After a bit of looking around, it seemed that Seq24 would be the right tool for the job.

However, when I load Seq24 then right click in one of the containers and select 'New', the program simply vanishes. I don't get any messages, it just disappears.

Has anyone else experienced this or got any ideas? I'd really like this to work as I managed to make sense of and actually use the other apps and even though I'm pretty poor at playing the keyboard, it's pretty important to the way I do things.

---

### Post by thorgal on 2009-04-25
not a big user of seq24 but nope, did not experience this problem. Try qtractor for the MIDI sequencing. I would not say rosegarden as it can be a bit complex for a beginner (but that's what I use and it works pretty good if you can go over some little irritating automatic reconfiguration).

---

### Post by dawiba on 2009-04-25
Thanks for the reply Thorgal.

I've downloaded Qtractor and so far I'm able to record midi but not able to use that midi to trigger sounds from my keyboard yet. I'll plug away at it tonight though to see if I can get anywhere.

---

### Post by rinishak on 2009-04-25
I'm experiencing this problem, too, now that I've upgraded to Jaunty. I can't seem to get Jack Server running, either, but that might be a problem with my settings, so nevermind that.

I tried running Seq24 in the terminal to see the debug messages. After I clicked "new" it crashed and dumped heaps of junk data into the terminal. Scrolling up, I found a line saying:

*** buffer overflow detected ***: seq24 terminated

I think this maybe a clue to why it's crashing?

---

### Post by dawiba on 2009-04-25
To be honest, I uninstalled Seq24 after Thorgal's post and downloaded and installed Qtractor, so I haven't tried Seq24 again, but thanks for your input.

On the plus side, I can now trigger sounds in my keyboard from midi events in Qtractor after a bit of messing around with connections in jack. I've also managed to get Ardour and Qtractor to be controlled from the transport in jack, so it looks like I'm all set.

I'm pretty happy now and thanks again to Thorgal for the suggestion.

---

### Post by rinishak on 2009-04-27
Well, good to know you've found a replacement. Just to let you know, though, I replaced Seq24 with the newer version, 0.9, which is available from the Seq24 Launchpad development page, and it worked perfectly. It must be manually compiled, though.

Cheers! ( ' &#8704; ' )

---

### Post by dawiba on 2009-04-27
Well, I downloaded the 0.9 version but when I type ./configure, I end up with this:


configure: error: Essential library libgtkmm-2.4 not found
dawiba@dawiba-laptop:~/seq24-0.9.0$ 

Can anyone help?

---

### Post by thorgal on 2009-04-28
if your apt repos list contain the deb-src as well, you can just do this:

```

sudo apt-get build-dep seq24

```


This will install all files that seq24 needs for a proper compilation. Then you can try to recompile it.

if the version of seq24 you're trying to compile is requiring newer dependencies, then you will have to add them "manually":

open synaptic, make a search on the lib it complains about, see that you find the -dev package as well, and install it. The library is usually just a bunch of binary objets that are needed at runtime. The -dev package contains all the necessary files that are needed for a program to compile against it.

---

### Post by dawiba on 2009-04-28
Thanks thorgal, I tried both of those suggestions but neither worked.

I'll leave it for now.

---

### Post by dawiba on 2009-05-12
Well I tried installing 0.9.0 again, but without success.

I get this message after 'make install'

dawiba@dawiba-laptop:~/seq24-0.9.0$ make install
Making install in man
make[1]: Entering directory `/home/dawiba/seq24-0.9.0/man'
make[2]: Entering directory `/home/dawiba/seq24-0.9.0/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
/bin/mkdir: cannot create directory `/usr/local/share/man/man1': Permission denied
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/dawiba/seq24-0.9.0/man'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dawiba/seq24-0.9.0/man'
make: *** [install-recursive] Error 1
dawiba@dawiba-laptop:~/seq24-0.9.0$ 

I admit I don't know what to do next to move forward. Can anyone help?

I did try Qtractor and it was fine. I also installed Rosegarden and quite liked the way I could set up the midi to map to different instruments on my keyboard (I actually found it pretty easy for a beginner!), but I can't help feeling that these programs are overkill for my needs because of their audio capabilities. I want to use Ardour for this, as it does everything I want for audio and I like the way it works. In the middle of this I even managed to set up my Saffire LE, so I'd really like to get seq24 to run to give me separate midi capability.

Thanks

---

### Post by thorgal on 2009-05-12
to install stuff in any place except /home/your-user-name or places you created as your-user-name, you need root priviledges. Try
```

make
sudo make install

```

---

### Post by dawiba on 2009-05-12
Thorgal

Success!

Many thanks!

---

### Post by curran on 2009-05-19
Hello,

Thanks everyone for sharing your experiences.

It seems impossible for me to get seq24 to work in a fresh install of Ubuntu Studio 9.04 - the packaged version crashes, and the source doesn't build. Here are details:

The first bug is that in the latest Ubuntu seq24 package (the one included in Ubuntu Studio 9.04 - yup, seq24 is broken out of the box), seq24 crashes when I click on "New" in the right-click menu (JACK was running if that makes a difference here). The following is output in the terminal (the second bug is described below this output) :

curran@nebula:~/seq24/seq24-0.8.7$ sudo apt-get install seq24
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following NEW packages will be installed:
  seq24
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/238kB of archives.
After this operation, 782kB of additional disk space will be used.
Selecting previously deselected package seq24.
(Reading database ... 154195 files and directories currently installed.)
Unpacking seq24 (from .../seq24_0.8.7-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up seq24 (0.8.7-2ubuntu1) ...

curran@nebula:~/seq24/seq24-0.8.7$ seq24
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Reading [/home/curran/.seq24rc]
Reading [/home/curran/.seq24usr]
Error Reading [/home/curran/.seq24usr]

----here's when I click "New"----

*** buffer overflow detected ***: seq24 terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb70ffda8]
/lib/tls/i686/cmov/libc.so.6[0xb70fdeb0]
/lib/tls/i686/cmov/libc.so.6[0xb70fd5a8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb706fbb8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x6f3)[0xb7041f23]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb70fd654]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb70fd59d]
seq24[0x8055c98]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class16realize_callbackEP10_GtkWidget+0x69)[0xb7f1e9f9]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb74733a4]
/usr/lib/libgobject-2.0.so.0[0xb74643d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7465c7b]
/usr/lib/libgobject-2.0.so.0[0xb747b6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb747d4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb747d936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xb1)[0xb7a781d1]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0xf0)[0xb7a78a50]
/usr/lib/libgtk-x11-2.0.so.0[0xb79dc059]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk15Container_Class21forall_vfunc_callbackEP13_GtkContaineriPFvP10_GtkWidgetPvES5_+0xd2)[0xb7e65302]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb78c5336]
/usr/lib/libgtk-x11-2.0.so.0[0xb78c77fb]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class12map_callbackEP10_GtkWidget+0xa2)[0xb7f1eb92]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb74733a4]
/usr/lib/libgobject-2.0.so.0[0xb74643d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb7465ba8]
/usr/lib/libgobject-2.0.so.0[0xb747b6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb747d4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb747d936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0x9c)[0xb7a789fc]
/usr/lib/libgtk-x11-2.0.so.0[0xb7891976]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk15Container_Class21forall_vfunc_callbackEP13_GtkContaineriPFvP10_GtkWidgetPvES5_+0xd2)[0xb7e65302]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb78c5336]
/usr/lib/libgtk-x11-2.0.so.0[0xb78c77fb]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class12map_callbackEP10_GtkWidget+0xa2)[0xb7f1eb92]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb74733a4]
/usr/lib/libgobject-2.0.so.0[0xb74643d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb7465ba8]
/usr/lib/libgobject-2.0.so.0[0xb747b6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb747d4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb747d936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0x9c)[0xb7a789fc]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a8a2d5]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk6Widget6on_mapEv+0x46)[0xb7f15556]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class12map_callbackEP10_GtkWidget+0x69)[0xb7f1eb59]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb74733a4]
/usr/lib/libgobject-2.0.so.0[0xb74643d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7465c7b]
/usr/lib/libgobject-2.0.so.0[0xb747b6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb747d4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb747d936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0x9c)[0xb7a789fc]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a8a3de]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk6Widget7on_showEv+0x46)[0xb7f155f6]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class13show_callbackEP10_GtkWidget+0x69)[0xb7f1ecb9]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb74733a4]
/usr/lib/libgobject-2.0.so.0[0xb74643d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7465c7b]
/usr/lib/libgobject-2.0.so.0[0xb747b6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb747d4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb747d936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_show+0x9c)[0xb7a791cc]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk6Widget14show_all_vfuncEv+0x46)[0xb7f13e06]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class23show_all_vfunc_callbackEP10_GtkWidget+0x6c)[0xb7f1ee2c]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 08:01 1588349    /usr/bin/seq24
080e5000-080e6000 r--p 0009d000 08:01 1588349    /usr/bin/seq24
080e6000-080e8000 rw-p 0009e000 08:01 1588349    /usr/bin/seq24
080e8000-080f3000 rw-p 080e8000 00:00 0
09802000-09a00000 rw-p 09802000 00:00 0          [heap]
b5570000-b5573000 r-xp 00000000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5573000-b5574000 r--p 00002000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5574000-b5575000 rw-p 00003000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5575000-b55d5000 rw-s 00000000 00:09 2654229    /SYSV00000000 (deleted)
b55d5000-b5635000 rw-s 00000000 00:09 2621460    /SYSV00000000 (deleted)
b5635000-b56cd000 r--p 00000000 08:01 1638950    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b56cd000-b56cf000 r-xp 00000000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b56cf000-b56d0000 r--p 00001000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b56d0000-b56d1000 rw-p 00002000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b56d1000-b56d7000 r--s 00000000 08:01 2065316    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b56d7000-b56da000 r--s 00000000 08:01 2065332    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b56da000-b56db000 r--s 00000000 08:01 2065331    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b56db000-b56de000 r--s 00000000 08:01 2065330    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b56de000-b56e5000 r--s 00000000 08:01 2065329    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b56e5000-b56e8000 r--s 00000000 08:01 2065328    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b56e8000-b56f0000 r--s 00000000 08:01 2065327    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b56f0000-b56fb000 r--s 00000000 08:01 2065326    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b56fb000-b56fd000 r--s 00000000 08:01 2065325    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b56fd000-b56ff000 r--s 00000000 08:01 2066090    /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b56ff000-b5706000 r--s 00000000 08:01 2065324    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5706000-b5707000 r--s 00000000 08:01 2065323    /var/cache/fontconfig/ec648e9a1aea82bddd4bd6050028158d-x86.cache-2
b5707000-b570d000 r--s 00000000 08:01 2066708    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b570d000-b571b000 r--s 00000000 08:01 2065313    /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b571b000-b571c000 ---p b571b000 00:00 0
b571c000-b5f1c000 rw-p b571c000 00:00 0
b5f1c000-b5f1d000 ---p b5f1c000 00:00 0
b5f1d000-b691f000 rw-p b5f1d000 00:00 0
b691f000-b6947000 r-xp 00000000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6947000-b6948000 r--p 00027000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6948000-b6949000 rw-p 00028000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6949000-b6969000 r-xp 00000000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6969000-b696a000 r--p 00020000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b696a000-b696b000 rw-p 00021000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b696b000-b6972000 r-xp 00000000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6972000-b6973000 r--p 00006000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6973000-b6974000 rw-p 00007000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6974000-b6980000 r-xp 00000000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6980000-b6981000 r--p 0000b000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6981000-b6982000 rw-p 0000c000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6982000-b6986000 r-xp 00000000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6986000-b6987000 r--p 00003000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6987000-b6988000 rw-p 00004000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6988000-b69a3000 r-xp 00000000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b69a3000-b69a4000 r--p 0001a000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b69a4000-b69b2000 rw-p 0001b000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b69b2000-b69b9000 r-xp 00000000 08:01 1585664    /usr/lib/libvorbisfile.so.3.2.0
b69b9000-b69ba000 r--p 00006000 08:01 1585664    /usr/lib/libvorbisfile.so.3.2.0
b69ba000-b69bb000 rw-p 00007000 08:01 1585664    /usr/lib/libvorbisfile.so.3.2.0
b69bb000-b69c8000 r-xp 00000000 08:01 1585666    /usr/lib/libcanberra.so.0.1.4
b69c8000-b69c9000 r--p 0000d000 08:01 1585666    /usr/lib/libcanberra.so.0.1.4
b69c9000-b69ca000 rw-p 0000e000 08:01 1585666    /usr/lib/libcanberra.so.0.1.4
b69cd000-b69d5000 r--s 00000000 08:01 2066406    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b69d5000-b69db000 r-xp 00000000 08:01 1639460    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b69db000-b69dc000 r--p 00005000 08:01 1639460    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b69dc000-b69dd000 rw-p 00006000 08:01 1639460    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b69dd000-b69e6000 r-xp 00000000 08:01 1777836    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69e6000-b69e7000 r--p 00008000 08:01 1777836    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69e7000-b69e8000 rw-p 00009000 08:01 1777836    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69e8000-b69fd000 r-xp 00000000 08:01 1777830    /lib/tls/i686/cmov/libnsl-2.9.so
b69fd000-b69fe000 r--p 00014000 08:01 1777830    /lib/tls/i686/cmov/libnsl-2.9.so
b69fe000-b69ff000 rw-p 00015000 08:01 1777830    /lib/tls/i686/cmov/libnsl-2.9.so
b69ff000-b6a01000 rw-p b69ff000 00:00 0
b6a01000-b6a08000 r-xp 00000000 08:01 1777831    /lib/tls/i686/cmov/libnss_compat-2.9.so
b6a08000-b6a09000 r--p 00006000 08:01 1777831    /lib/tls/i686/cmov/libnss_compat-2.9.so
b6a09000-b6a0a000 rw-p 00007000 08:01 1777831    /lib/tls/i686/cmov/libnss_compat-2.9.so
b6a0a000-b6a0c000 r--s 00000000 08:01 2066091    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b6a0c000-b6a10000 r-xp 00000000 08:01 1584873    /usr/lib/libgthread-2.0.so.0.2000.1
b6a10000-b6a11000 r--p 00003000 08:01 1584873    /usr/lib/libgthread-2.0.so.0.2000.1
b6a11000-b6a12000 rw-p 00004000 08:01 1584873    /usr/lib/libgthread-2.0.so.0.2000.1
b6a12000-b6a15000 r-xp 00000000 08:01 1585668    /usr/lib/libcanberra-gtk.so.0.0.4
b6a15000-b6a16000 r--p 00002000 08:01 1585668    /usr/lib/libcanberra-gtk.so.0.0.4
b6a16000-b6a17000 rw-p 00003000 08:01 1585668    /usr/lib/libcanberra-gtk.so.0.0.4
b6a17000-b6a1b000 r-xp 00000000 08:01 1641166    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a1b000-b6a1c000 r--p 00003000 08:01 1641166    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a1c000-b6a1d000 rw-p 00004000 08:01 1641166    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a1d000-b6a5c000 r--p 00000000 08:01 1607217    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6a5c000-b6b47000 r--p 00000000 08:01 1607220    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6b47000-b6b51000 r-xp 00000000 08:01 1777834    Aborted



The second bug is that when I attempt to compile from the "latest" download ([http://www.filter24.org/seq24/seq24-0.8.7.tar.gz](http://www.filter24.org/seq24/seq24-0.8.7.tar.gz)), I get the following error:

curran@nebula:~/seq24/seq24-0.8.7$ sudo apt-get build-dep seq24
Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

curran@nebula:~/seq24/seq24-0.8.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for main in -lrt... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for select... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS_CFLAGS... -D_REENTRANT -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/atk-1.0 
checking for DEPS_LIBS... -lgtkmm-2.4 -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 
checking for JACK_CFLAGS... 
checking for JACK_LIBS... -ljack -lpthread -lrt 
checking for LASH_CFLAGS... -I/usr/include/lash-1.0 -I/usr/include/alsa 
checking for LASH_LIBS... -llash -ljack -lpthread -lrt -lasound 
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands

curran@nebula:~/seq24/seq24-0.8.7$ make
Making all in .
make[1]: Entering directory `/home/curran/seq24/seq24-0.8.7'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/curran/seq24/seq24-0.8.7'
Making all in src
make[1]: Entering directory `/home/curran/seq24/seq24-0.8.7/src'
make  all-am
make[2]: Entering directory `/home/curran/seq24/seq24-0.8.7/src'
source='event.cpp' object='event.o' libtool=no \
    depfile='.deps/event.Po' tmpdepfile='.deps/event.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I. -I.    -D_REENTRANT -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/atk-1.0     -I/usr/include/lash-1.0 -I/usr/include/alsa   -Wall -g -O2 -c -o event.o `test -f 'event.cpp' || echo './'`event.cpp
event.cpp: In member function ‘bool event::append_sysex(unsigned char*, long int)’:
event.cpp:152: error: ‘memcpy’ was not declared in this scope
make[2]: *** [event.o] Error 1
make[2]: Leaving directory `/home/curran/seq24/seq24-0.8.7/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/curran/seq24/seq24-0.8.7/src'
make: *** [all-recursive] Error 1

Is seq24 an abandoned project? If not, could someone please provide an understandable fix that works in Ubuntu 9.04?

Thanks again everyone for contributing. Please let me know if I should include any other output files or information about my setup.

I think this kind of failure indicates the need for a more thorough test suite for Ubuntu Studio - maybe something driven by mouse and keyboard automation that just checks whether there is sound output at given checkpoints. Has anyone done something like that before? I imagine it must exist for UI testing.

Best,
Curran

---

### Post by curran on 2009-05-19
Aha! I found the latest source (which is NOT the "latest" on the official download page at [http://www.filter24.org/seq24/download.html](http://www.filter24.org/seq24/download.html) - come on seq24 guys - that should be changed for sure from 0.8.7 to 0.9.0)

Here are the commands I used to FINALLY get seq24 "working":

sudo apt-get remove seq24
mkdir seq24
cd seq24
wget [http://code.launchpad.net/seq24/trunk/0.9.0/+download/seq24-0.9.0.tar.gz](http://code.launchpad.net/seq24/trunk/0.9.0/+download/seq24-0.9.0.tar.gz)
tar xvfz seq24-0.9.0.tar.gz 
cd seq24-0.9.0/
./configure 
make
sudo make install
seq24

...well, at least it's not crashing when I breathe on it. JACK can't see it, why is this? Shouldn't I be able to connect seq24's midi out to some midi in via the JACK routing gui? Might I need some extra build option or something?

Now it's crashing when I click on "tools" in the piano roll view. Here is the output:

*** buffer overflow detected ***: seq24 terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb71d8da8]
/lib/tls/i686/cmov/libc.so.6[0xb71d6eb0]
/lib/tls/i686/cmov/libc.so.6[0xb71d65a8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb7148bb8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x6f3)[0xb711af23]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb71d6654]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb71d659d]
seq24[0x808dbaf]
/usr/lib/libglibmm-2.4.so.1(_ZN4Glib17SignalProxyNormal19slot0_void_callbackEP8_GObjectPv+0x52)[0xb787a7e2]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb754c3a4]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb753ec7b]
/usr/lib/libgobject-2.0.so.0[0xb75553d2]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb75564b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7556936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xb795cbda]
/usr/lib/libgtk-x11-2.0.so.0[0xb795e1f8]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Button_Class17released_callbackEP10_GtkButton+0xad)[0xb7f0cacd]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb754c3a4]
/usr/lib/libgobject-2.0.so.0[0xb753d3d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb753ec7b]
/usr/lib/libgobject-2.0.so.0[0xb75546c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb75564b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7556936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xb795cc7a]
/usr/lib/libgtk-x11-2.0.so.0[0xb795ccb3]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk12Widget_Class29button_release_event_callbackEP10_GtkWidgetP15_GdkEventButton+0xac)[0xb7fe103c]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a17526]
/usr/lib/libgobject-2.0.so.0[0xb753d3d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb753ec7b]
/usr/lib/libgobject-2.0.so.0[0xb7554aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb755634f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7556936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b322ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xec)[0xb7a0ff7c]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e7)[0xb7a11327]
/usr/lib/libgdk-x11-2.0.so.0[0xb77f734a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb74b0b88]
/usr/lib/libglib-2.0.so.0[0xb74b40eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb74b45ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7a117d9]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk4Main8run_implEv+0x17)[0xb7f563d7]
/usr/lib/libgtkmm-2.4.so.1(_ZN3Gtk4Main3runERNS_6WindowE+0x11e)[0xb7f564fe]
seq24[0x8083608]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb70f1775]
seq24[0x8053931]
======= Memory map: ========
08048000-080d7000 r-xp 00000000 08:01 1599962    /usr/local/bin/seq24
080d7000-080d8000 r--p 0008e000 08:01 1599962    /usr/local/bin/seq24
080d8000-080da000 rw-p 0008f000 08:01 1599962    /usr/local/bin/seq24
080da000-080e5000 rw-p 080da000 00:00 0 
086a2000-088aa000 rw-p 086a2000 00:00 0          [heap]
b5633000-b5636000 r-xp 00000000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5636000-b5637000 r--p 00002000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5637000-b5638000 rw-p 00003000 08:01 1655039    /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5638000-b5698000 rw-s 00000000 00:09 3440664    /SYSV00000000 (deleted)
b5698000-b56f8000 rw-s 00000000 00:09 3407895    /SYSV00000000 (deleted)
b56f8000-b5790000 r--p 00000000 08:01 1638950    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5790000-b5792000 r-xp 00000000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5792000-b5793000 r--p 00001000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5793000-b5794000 rw-p 00002000 08:01 1639408    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5794000-b579a000 r--s 00000000 08:01 2065316    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b579a000-b579d000 r--s 00000000 08:01 2065332    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b579d000-b579e000 r--s 00000000 08:01 2065331    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b579e000-b57a1000 r--s 00000000 08:01 2065330    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b57a1000-b57a8000 r--s 00000000 08:01 2065329    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b57a8000-b57ab000 r--s 00000000 08:01 2065328    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b57ab000-b57b3000 r--s 00000000 08:01 2065327    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b57b3000-b57be000 r--s 00000000 08:01 2065326    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b57be000-b57c0000 r--s 00000000 08:01 2065325    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b57c0000-b57c2000 r--s 00000000 08:01 2066090    /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b57c2000-b57c9000 r--s 00000000 08:01 2065324    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b57c9000-b57ca000 r--s 00000000 08:01 2065323    /var/cache/fontconfig/ec648e9a1aea82bddd4bd6050028158d-x86.cache-2
b57ca000-b57d0000 r--s 00000000 08:01 2066708    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b57d0000-b57de000 r--s 00000000 08:01 2065313    /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b57de000-b57df000 ---p b57de000 00:00 0 
b57df000-b5fdf000 rw-p b57df000 00:00 0 
b5fdf000-b5fe0000 ---p b5fdf000 00:00 0 
b5fe0000-b69e2000 rw-p b5fe0000 00:00 0 
b69e2000-b6a0a000 r-xp 00000000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6a0a000-b6a0b000 r--p 00027000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6a0b000-b6a0c000 rw-p 00028000 08:01 1658369    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6a0c000-b6a2c000 r-xp 00000000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6a2c000-b6a2d000 r--p 00020000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6a2d000-b6a2e000 rw-p 00021000 08:01 1658388    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6a2e000-b6a35000 r-xp 00000000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6a35000-b6a36000 r--p 00006000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6a36000-b6a37000 rw-p 00007000 08:01 1585656    /usr/lib/libltdl.so.7.2.0
b6a37000-b6a43000 r-xp 00000000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6a43000-b6a44000 r--p 0000b000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6a44000-b6a45000 rw-p 0000c000 08:01 1585660    /usr/lib/libtdb.so.1.1.3
b6a45000-b6a49000 r-xp 00000000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6a49000-b6a4a000 r--p 00003000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6a4a000-b6a4b000 rw-p 00004000 08:01 1585658    /usr/lib/libogg.so.0.5.3
b6a4b000-b6a66000 r-xp 00000000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b6a66000-b6a67000 r--p 0001a000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b6a67000-b6a75000 rw-p 0001b000 08:01 1585662    /usr/lib/libvorbis.so.0.4.0
b6a75000-b6a7c000 r-xp 00000000 08:01 1585664    /usr/lib/libvorbisfile.so.3.2.0
b6a7c000-b6a7d000 r--p 00006000 08:01 1585664    /usr/lib/libvorbisfileAborted

This is really lame. It's a shame seq24 is so impossible, from what I've read it is a really cool tool when it does work. I hope I can get it working eventually so I can use it, and maybe contribute something back to the community so people don't think it's just some buggy abandoned piece of garbage that gives Linux a bad name (which, from all appearances so far, if only superficially, it is).

Thanks in advance for any replies

Best,
Curran

---

### Post by dawiba on 2009-05-20
Curran:

I had experienced the same problems as you, namely, crashing when clicking on tools and not working with Jack.

In the end, I abandoned SEQ24 and have gone with Rosegarden for now, which works just fine so far with Ardour and Jack.

---

### Post by curran on 2009-05-20
Thanks dawiba, I have also tried Rosegarden and it works well as a sequencer.

Maybe seq24 should be taken out of the Ubuntu repositories until it works without a hitch, and not pre-installed in Ubuntu Studio. Experiences like this (you or I trying to get seq24 working for days and failing in the end) really do give Linux and the open source community as a whole a bad name.

I'd be curious to hear if anyone has had luck in getting seq24 to work in Ubuntu 9.04.

Thanks for the posts!

---

### Post by david.konsumer on 2009-06-23
I got it working well, in 9.04 (amd64 xubuntu, and i386 ubuntu.)

Here's what I did (in a script)

```

#!/bin/bash
wget http://code.launchpad.net/seq24/trunk/0.9.0/+download/seq24-0.9.0.tar.gz
tar xvfz seq24-0.9.0.tar.gz

mv seq24-0.9.0.tar.gz seq24-0.9.0/seq24_0.9.0-2ubuntu1.tar.gz

sudo apt-get install fakeroot
sudo apt-get build-dep seq24
apt-get source seq24

cp -R seq24-0.8.7/debian/ seq24-0.9.0

cd seq24-0.9.0

sed -i s/0.8.7/0.9.0/g debian/rules

echo 'seq24 (0.9.0-2ubuntu1) jaunty; urgency=low' > tmp
echo '' >> tmp
echo '  * Fixed crashing on "New"' >> tmp
echo '' >> tmp
echo ' -- David Konsumer <david.konsumer@gmail.com>  '`date "+%a, %d %b %Y %T %z"` >> tmp
echo '' >> tmp

cat debian/changelog >> tmp
mv tmp debian/changelog


rm debian/patches/*
dpkg-buildpackage -rfakeroot

```

That creates working debs in parent dir.

```

sudo dpkg -i seq24_0.9.0-2ubuntu1*.deb

```

---

### Post by raboofje on 2009-06-23
> **curran said:**
> I found the latest source (which is NOT the "latest" on the official download page at [http://www.filter24.org/seq24/download.html](http://www.filter24.org/seq24/download.html) - come on seq24 guys - that should be changed for sure from 0.8.7 to 0.9.0)

You can bitch about it, but you can hardly expect the seq24 guys to follow all seq42 threads on all distribution forums...

Added a bug report at [https://bugs.launchpad.net/seq24/+bug/391198](https://bugs.launchpad.net/seq24/+bug/391198)

---

### Post by raboofje on 2009-06-23
> **curran said:**
> Is seq24 an abandoned project

There seems to be some activity (also development, though not a whole lot) at the seq24-users-list: [https://sourceforge.net/mailarchive/forum.php?forum_name=seq24-users](https://sourceforge.net/mailarchive/forum.php?forum_name=seq24-users)

> If not, could someone please provide an understandable fix that works in Ubuntu 9.04?

Ubuntu should, of course, package a working version. David's post suggests this might just be a matter of upgrading the package to the latest version. Indeed, karmic (which will come after jaunty) already carries 0.9.0: [http://packages.ubuntu.com/search?keywords=seq24](http://packages.ubuntu.com/search?keywords=seq24) . Perhaps we could request this package to be included in the jaunty-backports? Anyone know how to submit such a request, or (better yet) do it?

---

