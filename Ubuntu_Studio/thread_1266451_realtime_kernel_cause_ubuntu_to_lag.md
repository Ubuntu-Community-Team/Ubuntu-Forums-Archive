---
title: "realtime kernel cause ubuntu to lag"
date: 2009-09-14
forum: Ubuntu Studio
---

### Post by junglejuice on 2009-09-14
hi
i'm trying to get the realtime kernel to work in ubuntu studio 9.04 i am using kernel version 2.6.28-3-rt. i need a realtime kernel because i am using midi in rosegarden and there is really bad latency with the generic kernel.
basically i've installed ubuntu studio and when i try to boot into the realtime kernel using grub ubuntu loads fine all the way to the log in screen, there are no problems. i enter my user name and password hit enter and then the ubuntu studio desktop loads, at this point the start up sound gets stuck in a loop and just keeps on looping half way through playing (the loop is about 2 seconds long), my mouse then becomes really slow to update on screen and disappears and reappears at the location i've moved it to. it's as if my computer is 'refreshing' every 30 seconds or so and just lagging in between.
i'm using an intel core 2 duo, with a nvidia geforce 7 graphics card, a sata drive that's only about half full and a sound blaster audigy, and 2GB of ram. i'm pretty sure it's not my hardware as i've run ubuntu studio with the realtime kernel perfectly before on this exact same computer, this was ubuntu studio 8.04.
if anyone can offer me any assistance i'd really appreciate it, as working with midi is virtually useless without realtime performance and i've tried searching the forums for help but have not come up with anything that resembles my problem.
your help is greatly appreciated.
many thanks
jj

---

### Post by kvk on 2009-09-14
This has been a widespread problem with the rt kernel in 9.04, if I understand correctly. I am having difficulties with it, although mine are different from yours. I haven't decided if the best thing is to dual boot with 8.04, rollback the rt kernel to the 8.04 version, or try the newer Karmic rt kernel.

---

### Post by junglejuice on 2009-09-14
hi kvk
i've considered rolling back to 8.04, but i recall having problems setting up my modem in that version of ubuntu :(
i have read various threads about patches for some ubuntu kernels, but have not found a patch that matches my kernels version. how do other people using 9.04 work with midi in realtime, i'd be really interested to find out?
thanks for the response
jj

---

### Post by tgalati4 on 2009-09-14
Run htop and see what's happening.

sudo apt-get install htop

Are you running pulseaudio?  If so, try turning it off.

---

### Post by trulan on 2009-09-14
The Jaunty realtime kernel is known to cause some systems to randomly freeze up, I'm not sure if it is causing your problems or not.  My laptop has the freezing issue, my desktop does not.

As far as other versions of the kernel, Hardy's rt kernel (8.04) is very stable.  Karmic, well, it's still alpha.  I have been running a version of it for several weeks now (2.6.31-2-rt), but the two latest releases (2.6.31-3-rt and 4-rt) will not boot at all for me.  I have high expectations for it but I can't recommend it just yet - unless you enjoy the challenge of trying to fix your system when it breaks;)

---

### Post by kvk on 2009-09-15
I'm trying to install the Hardy rt-kernel but apparently, I am not doing it correctly.

I enabled the Hardy repos in /etc/sources.list by adding four lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

then in the terminal ran

sudo apt-get update

and then

sudo apt-get install linux-image-2.6.29-rt

but the return was that it could not find the package.

Am I missing the correct kernel version number? Or am I simply out in left field somewhere?

---

### Post by junglejuice on 2009-09-15
hi tgalati4
thanks for the suggestions, i am using alsa as my main sound source (does that make sense?) how would i go about disabling pulse audio? i have installed htop, when you say 'Run htop and see what's happening.' do you mean run htop through a terminal and post the output here? sorry for the simple questions i'm still quite new to linux eventhough i've been using it for almost two years.
thanks again for your help
jj

---

