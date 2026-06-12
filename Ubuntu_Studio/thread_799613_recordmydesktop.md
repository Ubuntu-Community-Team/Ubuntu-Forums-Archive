---
title: "recordmydesktop"
date: 2008-05-19
forum: Ubuntu Studio
---

### Post by Dai777 on 2008-05-19
here is terminal error message: 
 
Locking assertion failure. Backtrace: 
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a53767] 
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a538b1] 
#2 /usr/lib/libX11.so.6 [0xb7eac421] 
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e94734] 
#4 recordmydesktop [0x8051776] 
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d724fb] 
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b2be5e] 
Broken pipe: Underrun occurred. 
Broken pipe: Underrun occurred. 
Broken pipe: Underrun occurred. 
 
Do you know how I can fix this? 
I have asked in the rmd forum but no one has answered this query

Thanks in advance  
Dai

---

### Post by Dai777 on 2008-05-19
dai@dai-desktop:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
recordmydesktop: ../../src/xcb_io.c:285: _XAllocID: Assertion `!(dpy->flags & (1L << 3))' failed.
Aborted
dai@dai-desktop:~$ 

After doing a complete re-install of hardy I'm still getting the above error when trying to record cinelerra full screen.

---

### Post by tamoneya on 2008-05-19
make sure you have all the modules necessary by trying this:```
sudo apt-get install libx11-6 libxcb-xlib0

``` Then record my desktop again.  Does this problem happen in any program besides cinelerra or is it program specific.

---

### Post by Dai777 on 2008-05-19
yes I have those installed thanks. Not sure what the solution is, if you think of anything else let me know.

---

### Post by tamoneya on 2008-05-19
is this cinelerra specific or does it occur with any program?

---

### Post by Dai777 on 2008-05-19
no it's occurring in all programs. at the moment it's not recording at all.

---

### Post by Dai777 on 2008-05-19
This the error after a brand new install:

dai@dai-desktop:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eb4734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7ecd200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6 [0xb7ecccb2]
#4 /usr/lib/libX11.so.6 [0xb7eccfcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eb474b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eb4734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7ecd200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6 [0xb7ecccb2]
#4 /usr/lib/libX11.so.6 [0xb7eccfcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eb474b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eb4734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6 [0xb7ecccb2]
#4 /usr/lib/libX11.so.6 [0xb7eccfcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eb474b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eb4734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6 [0xb7ecccb2]
#4 /usr/lib/libX11.so.6 [0xb7eccfcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eb474b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a738b1]
#2 /usr/lib/libX11.so.6 [0xb7ecc421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eb4734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a73767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7381e]
#2 /usr/lib/libX11.so.6 [0xb7ecc518]
#3 /usr/lib/libX11.so.6 [0xb7ecccb2]
#4 /usr/lib/libX11.so.6 [0xb7eccfcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eb474b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d924fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b4be5e]
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.

---

### Post by tamoneya on 2008-05-19
you say this is a new install.  Did you switch to metacity already.  record my desktop appears to think that it is:> Your window manager appears to be MetacityBy default in Ubuntu the window manager is compiz.

---

### Post by Dai777 on 2008-05-20
not sure all I've done is re-installed ubuntu put my mac theme in and chosen clear looks as far as metacity is concerned not sure can you give me more info on this so I can check things out.

---

### Post by benquick on 2008-05-20
try to use istanbul
```

sudo apt-get install istanbul

```
I'am using Istanbul Desktop Session Recorder to recording my desktop

---

### Post by Dai777 on 2008-05-20
all video programms seem to be playing up in hardy why.
this is a brand new install done yesterday

---

### Post by cayhorstmann on 2008-06-07
> **Dai777 said:**
> here is terminal error message: 
 
Locking assertion failure. Backtrace: 
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a53767] 
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a538b1] 
#2 /usr/lib/libX11.so.6 [0xb7eac421] 
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e94734] 
#4 recordmydesktop [0x8051776] 
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d724fb] 
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b2be5e] 
Broken pipe: Underrun occurred. 
Broken pipe: Underrun occurred. 
Broken pipe: Underrun occurred. 
 
Do you know how I can fix this? 
I have asked in the rmd forum but no one has answered this query

Thanks in advance  
Dai

I did what was recommended at 
[https://sourceforge.net/forum/forum.php?thread_id=1804915&forum_id=590957](https://sourceforge.net/forum/forum.php?thread_id=1804915&forum_id=590957)

and added position_fix=1 to options snd-hda-intel in /etc/modprobe.d/alsa-base 

No, I have no idea what that means, but it did take care of the  underrun problem.

Cheers,

Cay

---

### Post by sigint on 2008-06-18
I never managed to get gtk-recordMyDesktop to work on my amd64 Ubuntu box but it worked OK first time on my Celeron i686 running Edgy But after upgrading to 8.04 even that failed.

In the crash log in my home directory it shows the parameters passed to recordmydesktop and when I removed the no-shared (or something similar - I cannot remember) parameter and pasted the remainder into console then it worked - so after some more blind poking around I found a config file, also in my home directory for gtk-recordMyDesktop and I changed the memory sharing parameter to True (i.e. 0 in this case because they are back to front) and saved the file and now

gtk-recordMyDesktop 

works on an i686 running the latest Ubuntu ( linux-image-2.6.24.19 appeared yesterday) with sound (it was the sound that is/was the problem).

the config file is called
.gtk-recordmydesktop

and the parameter currently is set to

#Shared memory,1 disabled 0 enabled
0

---

