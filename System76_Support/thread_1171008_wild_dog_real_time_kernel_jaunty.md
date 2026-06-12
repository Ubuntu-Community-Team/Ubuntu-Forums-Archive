---
title: "wild dog real time kernel jaunty"
date: 2009-05-26
forum: System76 Support
---

### Post by corey.abshire on 2009-05-26
Hi system76. 

I am trying to get a nice sound studio set up with my new Wild Dog and have ran into a slight issue. I have jack running, and it runs ok, but I tend to get a lot of xruns. I've tried a variety of settings as recommended by various support forums, but still receive an unacceptable amount in my opinion to really do some reliable recording. 

Most of the threads I've read recommend using a realtime kernel for audio tasks like this. I tried installing linux-rt using apt-get and tried starting it up, but I run into an issue. It shows the boot screen, starts loading, shows the Ubuntu progress bar, but then, just about the time it would normally show the login screen, the screen gets all garbled and the system apparently hangs. If I reboot into the generic kernel, it seems to work fine.

I also tried running the realtime kernel in recovery mode, and using the xfix option. This wrote out a new xorg.conf file, but when I tried booting with that I got the same result - garbled screen about the time it should show the login screen. Then, when I tried changing back to the generic kernel, this time I got the same result - garbled screen. Then, I tried changing over to the xorg.conf.failsafe to see if that worked. I did a diff before I did it and the main difference I could see is it was changing back to the vesa driver. I tried both the realtime kernel and generic kernel and both of those had the same result - garbled screen around the time it should show the login screen. I changed back to the original backup that the xfix option wrote out and I am now able to get back into the generic kernel.

I'm thinking the best option is for me to figure out how to get the realtime kernel working in jaunty, as that's what most of the threads seem to recommend to get decent jackd throughput (no xruns!), so that's the main issue I'm asking for help on. However, if you have other recommendations for eliminating xruns I'd certainly be open to that as well.

I'm basically running a new (less than 1 month old Wild Dog with dual Samsung 2333's on an ATI 4850. I've tried disconnecting one of the monitors from the video card before restarting to see if it had something to do with dual headed display detection and again got the same result, so I don't think it had anything to do with that. The system is fairly pristine, other than installing jack and various other supporting audio utilities like Ardour, Rosegarden, jackd, etc...

I checked various forums regarding jaunty realtime kernel issues, and can see many others having issues, but no real solutions. A few recommended custom building the kernel, but I read separately it can be very difficult to get support using this approach, and so am trying to stick to the provided packages and see if anyone else has a better option before trying something drastic like that. I've compiled kernels for other systems I've had in the past, but I'd rather be trying to record some nice tunes!

BTW - Thanks a lot for great machines - I'm really diggin' my Wild Dog other than this!

Thanks!
- corey

---

### Post by thomasaaron on 2009-05-27
I think the -rt kernel produced the garbled screen because it was trying to use the vesa video driver on the ATI cards -- which doesn't work well.

When you created a new xorg.conf, you basically removed the version of the xorg.conf that had the fglrx driver specified.

Try booting into a recovery mode root command prompt and running...

sudo nano /etc/X11/xorg.conf

In the resulting text editor, place this line...

Driver "fglrx"

...into the Device section. Then run...

sudo reboot -h now

Did that get you back into the generic kernel? If not, I'll send you the xorg.conf from my shop Wild Dog and we'll replace it that way.

---

### Post by corey.abshire on 2009-05-27
Hi Tom. I think I may have miscommunicated. 

I was already back in the generic kernel with fglrx when I wrote that.

Let me try to summarize a little better. Here's what I've tried so far:

1: -rt kernel w/fglrx (no change) (garbled screen)
2: -rt kernel w/vesa? (xfix) (garbled screen)
3: -rt kernel w/vesa (xorg.conf.failsafe) (garbled screen)
4: -generic kernel w/fglrx (no change) (works fine except audio issues)
5: -generic kernel w/vesa? (xfix) (garbled screen)
 6: -generic kernel w/vesa (xorg.conf.failsafe) (garbled screen)

Basically I did try it with the same xorg.conf I used with -generic first, and then tried a few different xorg.conf's after that didn't work. But I did manage to restore the -generic to working order.

I still have the xorg.conf's I tried if that helps. Or if you have another one you know works with -rt you want me to try I can certainly do that. 

It just sounded like you thought maybe I hadn't already tried the fglrx with the -rt, and that it wasn't even working in -generic.

---

### Post by thomasaaron on 2009-05-27
Yeah, I misunderstood. Sorry.

First, you're not going to get any kind of good results with the vesa driver on the ATI card. I'm 99% sure that's exactly what causes the garbling.

You might want to try a *previous* -rt kernel. It sounds like the video drivers won't compile against the -rt kernel. But maybe they compiled against a previous one. It's worth a shot.

We don't test with the -rt kernels, so I don't really track what works with them.

---

### Post by corey.abshire on 2009-05-28
Ok - I get you on the vesa drivers. 

I searched for a long time tonight trying to figure out how to properly install a previous kernel as you mentioned but wasn't able to figure it out. Can you please provide some additional guidance on that?

Also, I tried various other amalgamations but none worked well enough. I did get the real-time kernel working in a gnome session at one point with the non-ATI provided drivers, and it worked somewhat. The good news is, I tried out my sound studio software in it and sure enough it all works beautifully with no xruns under that kernel. The bad news - no 3d support, so definitely not a long term solution for me. It really whetted my apetite to have the overall solution working - real ATI drivers + RT kernel.

Have you guys ever thought of using the realtime kernel by default, or at least providing it as an option and including it in your testing? I know I would certainly appreciate it, and I'm sure other folks looking at system76 as a solution for multimedia processing needs would appreciate it also. Sound apps under the generic kernel are pretty bad.

Thanks for your help on this. I really do appreciate it.

---

### Post by thomasaaron on 2009-05-28
Actually, after further investigation, it will not work with a previous -rt kernel either...

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=EE2&q=jaunty+rt+kernel+and+ati+graphics&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=EE2&q=jaunty+rt+kernel+and+ati+graphics&btnG=Search)

A quick review of those links indicates there may be ongoing issues with ATI graphics under the -rt kernel.

Eventually, ATI will gain support as Ubuntu Studio (which uses an -rt kernel) becomes more popular. I'm not really sure what you can do in the meantime, though, other than going with a different graphics card.

---

### Post by juaniretro on 2009-06-24
Hi corey.abshire! 
My name is Juani and I'm from Argentina. I'm a sound engineering student and I'm really struggling to use Ubuntu for any kind of sound work. My situation is a bit complicated since I've tried many ways to get a good recording quality and no Xruns: I have exactly the same problem you explain at the thread "wild dog real time kernel jaunty".
I'm using a Presonus FP10 for recording right now and I have an ATI Readeon Mobility video card which I'm not willing to use at all. You wrote, at some point of the thread:

"I did get the real-time kernel working in a gnome session at one point with the non-ATI provided drivers, and it worked somewhat. The good news is, I tried out my sound studio software in it and sure enough it all works beautifully with no xruns under that kernel."

Could you give me an explanation on how to get to that point? I really don't mind about the graphics, I don't really need them. All I need is a real good recording quality/functioning and I'm not an Ubuntu expert at all.

Thanks in advance!


Juani

---

