---
title: "nwn dont work in hardy (yet)"
date: 2008-01-13
forum: Ubuntu Gamers Arena
---

### Post by zenrox on 2008-01-13
i followed a howto on biowares site for the diamond editon casue i thought the install had gone bad from going feisty -gutsy then hardy
nope so heres the error 
 Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb704c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb704c8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb719429d]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d8353d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d7e78c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d80457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d75f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d587de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d588dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c13450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)
 know any ideas as to whats going on

---

### Post by PurpleFool on 2008-02-04
I really hope you found the other threads that reference the problem, but just in case, if you take out the "./lib:" from the LD_LIBRARY_PATH assignment in nwn, the script that starts the client, then you may have better luck.  At least that's what worked for me.

One of the other threads opined that it looked like the SDL installed with NWN has a problem.

---

### Post by Perfect Storm on 2008-02-05
Most be something to do with the old version of SDL which follow with NWN which have trouble working with a much newer systems perhaps.

---

### Post by zenrox on 2008-02-11
the removal of ./lib caused it to todaly segfault
so still no fix seen a patch for gutsy bine thinking of trying it

---

### Post by bowsercake on 2008-02-15
removing the ./lib worked for me too. Thanks!

---

### Post by PurpleFool on 2008-02-16
Must admit I´m trying to get a second install going, also on Hardy, and it drops core too.  This system has an ATI graphics adapter and the 2.6.24-8 kernel image/restricted modules.

I think the working version is using -7, I know it&#347; an nVidia adapter.

---

### Post by surdin on 2008-02-27
Removing ./lib: worked for me as well, thanks!

---

### Post by bloodandsoil on 2008-03-10
I'm on Hardy alpha 6, and I get the same exact error as the OP.

When I remove the ./lib, I get "Segmentation fault (core dumped)".

---

### Post by quizzelsnatch on 2008-04-08
I'm on the beta of Hardy and I get the same error as the person above me. Anybody have any success with getting nwn to work on hardy?

---

### Post by Druke on 2008-04-11
It works great for me but I just removed the libSDL not the whole lib folder

---

### Post by Quikee on 2008-04-13
I had a similar problem with java applications. The fix was to set the following env. variable:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
```
and after this start the application. I hope this will help.

---

### Post by quizzelsnatch on 2008-04-22
I tried changing line ten to export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH and when i run ./nwn it gives me a segmentation fault with no message explaining anything else. Any tips?

---

### Post by Non Plus Ultra on 2008-04-26
> **quizzelsnatch said:**
> I tried changing line ten to export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH and when i run ./nwn it gives me a segmentation fault with no message explaining anything else. Any tips?

By removing the /lib entry, the new entry will be:
```

export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

```

Thus without the colon :)

---

### Post by quizzelsnatch on 2008-04-27
Makes sense, tried that, and I got this:
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Segmentation fault

---

### Post by hidinginthemountains on 2008-04-30
I just spent a few hours wrestling with NWN. Among the issues I had was a "Segmentation Fault". I'm not enough of a guru to tell you exactly what to type, but your answer likely lies in permissions (or, according to some of my reading file names with mixed cases).

All I can say beyond this is that I have done a successful fresh install of NWN on a fresh install of Hardy. I'm using v1.68 right now, but will go to the v1.69Beta6 when the DL is done.

(other things I did involved removing the ./lib reference...oh, and I use compiz-switch to quickly turn off desktop effects before playing...oh, AND I'm running the game as sudo, but I'm not sure that's needed)

Good luck!

---

### Post by Perfect Storm on 2008-04-30
Some say that removing the .ini file help them (good idea to back the file up first).

---

### Post by Geezle on 2008-05-01
I'm having the same problem as well...I've tried all the suggestions in this thread with no luck so far.

---

### Post by smah77 on 2008-05-07
Same issue here.  If I disable sound, I don't get the message about ALSA, just a segmentation fault.  I've got nVidia, 64-bit, etc., etc.

---

### Post by jfbilodeau on 2008-05-11
Same problem here. It seems to be related to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311](https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311)

---

### Post by Tinker Dragoon on 2008-06-08
I'm running Kubuntu Hardy 32-bit (though I doubt that makes a difference), and NWN works perfectly for me after disabling the included SDL libraries, as above, and enabling the restricted nvidia driver (I use an nVidia GeForce 6200 LE card, for what it's worth). 

Once before, when I was using 64-bit Gutsy, I too received segmentation faults when I tried to run the nwn script. In that case it turned out to be a simple permissions issue, as I had mistakenly used sudo when extracting some of the files to my hard disk. It might help to take a look here: [http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72)

---

### Post by Stunts on 2008-06-20
Those of you who are running on x64 Hardy, you need 32bit libs.
You can download them from the repros, just can't recall the exact command...
If you have toruble I'll try and provide it.
=-)

---

### Post by Saboteur777 on 2008-07-03
Hi!

I have a problem with nwn: after i start it by ./nwn, it starts, but at the point i click on the 'Join internet game', or after creating the character, on the 'Play' button, the game quits. By running it from terminal it 'answers': 'Segmentation fault'. I can't change the video, or sound, etc options thanks to this bug, too. Running nwn-win with wine everything is OK. I have changed the contents of the nwn file (I deleted the './lib' from the export... line). I tried to install a new driver for my nvidia geforce fx 5700ultra, but i haven't succeed... :( Please help, I don't know, what can i do with it. Thanks for your help! :D

---

