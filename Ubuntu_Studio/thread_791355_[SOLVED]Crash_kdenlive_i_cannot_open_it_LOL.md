---
title: "[SOLVED]Crash kdenlive i cannot open it LOL"
date: 2008-05-12
forum: Ubuntu Studio
---

### Post by Creative2 on 2008-05-12
It was so sad  yes i could not use kdenlive... but i solved as i written on my forum ..

[http://fuocotools.byethost13.com/index.php?topic=102.msg167#msg167](http://fuocotools.byethost13.com/index.php?topic=102.msg167#msg167)

edit well there are problems with byethost so i will write here the solution:

hello just installed kubuntu 8.04 (without compiz) and just installed kdenlive ?
damn your kdenlive crash? of couse 

your error in konqui is this?


 
 ```
Using host libthread_db library "/lib/libthread_db.so.1".
 [Thread debugging using libthread_db enabled]
 [New Thread 0xb66e26c0 (LWP 10242)]
 [New Thread 0xb32fdb90 (LWP 10250)]
 [New Thread 0xb3afdb90 (LWP 10249)]
 [New Thread 0xb4ed9b90 (LWP 1024]
 [New Thread 0xb46d9b90 (LWP 10247)]
 0xb75f3161 in read () from /lib/libpthread.so.0
 #0 0xb75f3161 in read () from /lib/libpthread.so.0
 #1 0xb683a1d3 in ?? () from /usr/lib/libxcb.so.1
 #2 0x00000003 in ?? ()
 #3 0x082c7bbc in ?? ()
 #4 0x00001000 in ?? ()
 #5 0xb68488bc in ?? () from /usr/lib/libxcb.so.1
 #6 0x082c7b28 in ?? ()
 #7 0x082c7b28 in ?? ()
 #8 0xbfba8158 in ?? ()
 #9 0x082c7bbc in ?? ()
 #10 0x082c7b34 in ?? ()
 #11 0x00000001 in ?? ()
 #12 0xb68488bc in ?? () from /usr/lib/libxcb.so.1
 #13 0xb683a14b in ?? () from /usr/lib/libxcb.so.1
 #14 0x082c8bec in ?? ()
 #15 0x082c7b34 in ?? ()
 #16 0xb66e26c0 in ?? ()
 #17 0xb68488bc in ?? () from /usr/lib/libxcb.so.1
 #18 0x00000000 in ?? ()
```

solution:

[B]1 :sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2: delete configuration files (~/.kde/share/config/kdenliverc)
3: try to disalble compiz (gnome user run this :     metacity --replace  ;  kde user      kwin --replace)[/B]

**ONLY FOR NVIDIA USER NEVER TESTED BECAUSE I HAVE AN INTEL ***

4 if you have nvidia graphid card i found this on this forum :

If you have a NVidia and Ubuntu Hardy Heron, the crash of Kdenlive is due a missconfiguration of the last Nvidia driver in Heron by default.
 
 The solution:
 
 Edit the xorg.conf
```
 sudo gedit /etc/X11/xorg.conf
```
 
 Add this line to the Device Section
```
 Option "UseCompositeWrapper" "True"
```
 
 Add this at the end of the file
```
 Section "Extensions"
 Option "Composite" "Enable"
 EndSection
```
 
 Reset the X server (Ctrl+Alt+Backspace)
 You can run the Kdenlive without it crashes&#8230; enjoy it!

---

### Post by theophiles on 2008-05-12
It helped me. Thank you. I will be referring to this thread from the ones were I was asking for help.

---

### Post by Creative2 on 2008-07-14
updated :) just see first post i have edited

---

### Post by koshari on 2008-08-25
you should edit this post to place the code lines in a code wrapper so as the correct asci letters are cut and pasted in the xorg file :-)

like this

The solution:

Edit the xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

Add this line to the Device Section
```
Option "UseCompositeWrapper" "True"
```

Add this at the end of the file
```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```

the way they were with the funny quote marks crashes the xsession.

---

### Post by Creative2 on 2008-08-25
Made :)

---

### Post by marer13 on 2011-10-21
It didn't work on mine....

What shall I do ? I still cannot start Kdenlive........

---

