---
title: "What problems are people having with Jaunty?"
date: 2009-06-01
forum: Testimonials &amp; Experiences
---

### Post by UncleMonty on 2009-06-01
I updated today and am still regretting this as I've encountered the following problems:

1) The graphics card appears to be no longer configured
2) My C64 Emulator won't load anymore
3) Control-alt-backspace doesn't do anything

---

### Post by p388l3s on 2009-06-01
so far i've been very un-impressed with Jaunty, Intrepid was super slick no slow-downs and everything worked, but Jaunty is slow in my games, has un-explained high processor usage every so often, and has generally not been a fun experience, I may go back to my Intrepid install.

CONS:
Slow in 3d gaming.
VNC into desktop not working with nvidia gfx card.
Strange processor usage. (x seems to be the culprit)

---

### Post by UncleMonty on 2009-06-01
> **p388l3s said:**
> so far i've been very un-impressed with Jaunty, Intrepid was super slick no slow-downs and everything worked, but Jaunty is slow in my games, has un-explained high processor usage every so often, and has generally not been a fun experience, I may go back to my Intrepid install.

CONS:
Slow in 3d gaming.
VNC into desktop not working with nvidia gfx card.
Strange processor usage. (x seems to be the culprit)


Is it possible to downgrade to Intrepid?

---

### Post by p388l3s on 2009-06-01
downgrade no, but I ALWAYS use 2 partitions on my main machine, 1 for my current desktop and 1 for either a test desktop or a new Ubuntu version, if I like then I delete the old and do the same again but in this case I may just kill Jaunty and go back to intrepid.

---

### Post by Lunx on 2009-06-01
> **UncleMonty said:**
> 

3) Control-alt-backspace doesn't do anything

Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1176040&highlight=control+alt+backspace](http://ubuntuforums.org/showthread.php?t=1176040&highlight=control+alt+backspace)

---

### Post by UncleMonty on 2009-06-02
> **Lunx said:**
> Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1176040&highlight=control+alt+backspace](http://ubuntuforums.org/showthread.php?t=1176040&highlight=control+alt+backspace)


Woot thank you, oh well that's one problem sorted. :) 

Next stop: Graphics card configuring...

---

### Post by TheNosh on 2009-06-02
flash seems worse, but i'm not gonna go back to intrepid and sacrifice EXT4 compatibility for that. it'll probably be fixed eventually, and usually if i'm using flash it's just for hulu and i'm not doing much else so i just boot the win7 RC (takes like 20 seconds)

also the 3D drivers for my intel graphics were blacklisted. but having installed them i seem to run compiz and everything else without trouble

(also on a purely superficial level, i think the new notification system is just to slick to lose)

---

### Post by UncleMonty on 2009-06-02
> **TheNosh said:**
> flash seems worse, but i'm not gonna go back to intrepid and sacrifice EXT4 compatibility for that. it'll probably be fixed eventually, and usually if i'm using flash it's just for hulu and i'm not doing much else so i just boot the win7 RC (takes like 20 seconds)

also the 3D drivers for my intel graphics were blacklisted. but having installed them i seem to run compiz and everything else without trouble

(also on a purely superficial level, i think the new notification system is just to slick to lose)


What does EXT4 compatibility consist of?

---

### Post by MichaelSammels on 2009-06-02
Wow... I've had none. :P

---

### Post by TheNosh on 2009-06-02
> **UncleMonty said:**
> What does EXT4 compatibility consist of?

i just mean that jaunty supports installation on the EXT4 filesystem, which is much faster than EXT3. intrepid will not allow EXT4 as an option during instalation and won't recognize EXT4 partitions (i'm sure theres some way to make intrepid read them without much hassle, but i'm not using intrepid anymore so i don't much care)

---

### Post by adament45 on 2009-06-02
Hi,
so i have been running 8.10 for a while and i love it. Not to long ago i tried out the jaunty beta and it worked fine, then not so fine. I couldnt install programs and things were crashing left and right. I then reinstalled 8.10, its been a month or 2 since then, an i thought 9.04 may be stable by now. I upgraded and once i restarted my computer, it went to the whole" Failed to start the X server. It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem" so i ran sudo dpkg-reconfigure xserver-xorg, and nothing happened, i then tried the recovery branch from the grub, i can access ubuntu but internet wont work, and i tried to reinstall desktop effects, so once i restarted, my computer repeated the "Failed to start xserver", i repeated this process 5 times,same results. So far i am not much of a fan of 9.04, is there any way i can fix this or do i have to reinstall?

---

### Post by p388l3s on 2009-06-02
you would need to tell us what your gfx card is first then we may be able to help.

---

### Post by UncleMonty on 2009-06-02
> **p388l3s said:**
> you would need to tell us what your gfx card is first then we may be able to help.

How do you find out what graphics card you are using? What info is relevant?

---

### Post by p388l3s on 2009-06-02
one easy way is to type into a terminal:

```
dmesg | grep nvdia
```

replace nvidia with intel ati or evan matrox, although if you search on the forums there's probably much better ways to do this.

---

### Post by UncleMonty on 2009-06-02
> **p388l3s said:**
> one easy way is to type into a terminal:

```
dmesg | grep nvdia
```

replace nvidia with intel ati or evan matrox, although if you search on the forums there's probably much better ways to do this.

Thanks, it's Intel.

---

### Post by HappyFeet on 2009-06-02
No problems here.

---

### Post by 3rdalbum on 2009-06-02
No problems on my desktop. My netbook has Intel graphics and that seemed to cause problems with my h.264 videos. After trying some HOWTOs on increasing the performance of the Intel graphics, the performance actually decreased by three quarters. I tried to roll back my changes and I borked the system.

It's running Intrepid again now, partly because of the video playback issue and partly because I don't have a 32-bit Jaunty CD! My home server runs 8.10 (because I don't have a 32-bit Jaunty CD to match the 32-bit Atom!) and my father's desktop runs 8.04. But my desktop runs 9.04 and it's going beautifully.

---

### Post by Gausian on 2009-06-03
Disconnecting wireless connection (Intel 4965 agn)

and cant use Skype because you need a hearing aid to hear sounds recorded from my mic.

other than that im happy.

---

