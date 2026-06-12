---
title: "Installed on old HP Pavilion N5415"
date: 2009-04-12
forum: Testimonials &amp; Experiences
---

### Post by SedaliaSteve on 2009-04-12
I've spent some hours today and now have a working xbuntu laptop.

These are the specs:
Hp Pavilion N5415, 900 MHz Duron CPU, 256 MB memory. 20 GB disk.

This was being neglected since it was awful with Windows. It's actually rather peppy now. I couldn't believe how easy it all went.I chose Xbuntu since this is an old slow machine. I made a ISO disk from 8.10.

I booted and it was off. I let it take the whole disk and run automatically and it can up with a reasonable set of file systems. I've only validated the display, mouse, keyboard, CD drive and network connection. As soon as I plugged in a network cable it was on the network.

I tried to get the sysinfo command and have failed with that but that is minor. Tomorrow I'll see how it plays and rips a CD.I'll also install a wifi card, I guess choosing an old computer meant there were no surprises.

I've installed Red Hat on some PC's and early Debian on others but this was flawless. I've had windows install much, much worse with this.

This makes me optimistic that ny next Ubuntu system will do well. I'm planning to do a small form factor system with a lot of RAID disk to hold lots of music and probably video. I was dreading it but now this sounds like fun,

Steve

---

### Post by overdrank on 2009-04-12
Welcome and moved to Testimonials & Experiences

---

### Post by armandh on 2009-04-12
wait tell you see how good it is at 512 meg mem

---

### Post by wgarider on 2009-04-12
> **SedaliaSteve said:**
> It's actually rather peppy now. I couldn't believe how easy it all went.

Steve

I've been doing quite a bit of this lately myself - it's great how 'older' hardware runs just fine with one of the Ubuntu flavors. Congrats!

---

### Post by torchy2000 on 2009-05-16
I have just installed Ubuntu 9.04 on a Hp Pavilion N5415, 900 MHz Duron CPU, 256 MB memory. 20 GB disk.

The only issue is the screen display: In the GUI, the screen occupies only about 80% of the screen's area. That is, there is about a 3 cm (1.25 inch) border all around. In fact, when I first installed Ubuntu, the blank border was about 6 cm (2 inches) all around but pressing the Fn-F5 key changes that. (The original Windows XP occupied the whole screen.)

I had the same effect when trying Xandros Presto and Knoppix. 

Does your installation occupy the whole screen area?

Any ideas for a solution?

Are there any BIOS settings changes required?

Some  other information:
   - the screen display application allows resolutions of (800 x 600), (640 x 480), (400 x 300), and (320 x 240). Changing resolution doesn't change the border size.

Any help or information would be appreciated.

--Jim

---

### Post by SedaliaSteve on 2009-05-16
torchy,

I had the black border also. It is irritating. If you do an *lspci* and get this for your video card:

Video card: Trident Cyberblade XP

The following thread should help: [http://ubuntuforums.org/showthread.php?t=1098092]("http://ubuntuforums.org/showthread.php?t=1098092")

If the link doesn't work it is titled **Video Driver on Toshiba Satellite Pro 4600 **. It's a simple edit on /etc/X11/xorg.conf to get full screen. I'm no Ubuntu expert. Dee, the author of the thread, had the solution.

Hope this helps.

Steve

---

### Post by torchy2000 on 2009-05-16
Steve: Thank you very much for the pointer. It did the trick.

--Jim


> **SedaliaSteve said:**
> torchy,

I had the black border also. It is irritating. If you do an *lspci* and get this for your video card:

Video card: Trident Cyberblade XP

The following thread should help: [http://ubuntuforums.org/showthread.php?t=1098092](http://ubuntuforums.org/showthread.php?t=1098092)

If the link doesn't work it is titled **Video Driver on Toshiba Satellite Pro 4600 **. It's a simple edit on /etc/X11/xorg.conf to get full screen. I'm no Ubuntu expert. Dee, the author of the thread, had the solution.

Hope this helps.

Steve

---

### Post by kyl416 on 2009-05-24
I'm using Ubuntu on an N5415 too, except it has a replacement 80 gig hard drive installed and I installed another 256 memory card to get a total of 512. Everything else is the same spec wise. My only problem so far is that I can't get TV out working.

I also had a problem with the volume and mute keys, but that's a known limitation with this model of Omnibook XE3's so I just remaped them to left shift + left ctrl + up/down/F7 instead.

---

### Post by rgwill on 2009-12-06
I've had Ubuntu 8.04 installed on an HP Pavilion N5415 and after some extensive Googling and forum searching I finally got the wireless card to work and graphics to display properly. I was very happy. Then I upgraded to Ubuntu 9.10. I got the wireless card to work as usual but the xorg.conf file configurations I used in 8.04 would not work in 9.10.
After some more internet searching I was coming up short with a solution to this problem. I did resolve this however by chance.

After a bad configuration in xorg.conf my laptop would not boot to the OS and would only sit in terminal mode. So in hopes I could fix the problem I ran Ubuntu from the CD stand alone and to my amazement my screen resolution was rightfully 1024x768. For some reason Ubuntu in CD mode was recognizing and running the proper driver for my laptop but was failing in the installed OS mode. I went to terminal and ran the following command;

**gksudo gedit /etc/X11/xorg.conf**

This brought up the current settings being run by the CD,
[B]
Section "Device"
             Identifier   "Configured Video Device"
             Driver        "vesa"
Endsection

Section "Monitor"
            Identifier    "Configured Monitor"
Endsection

Section "Screen"
            Identifier    "Default Screen"
            Monitor       "Configured Monitor"
            Device        "Configured Device"
Endsection[/B]

I took a digital photo of these settings because I did not want to make a mistake in writing these down. I then closed gedit without saving and then restarted Ubuntu and applied these settings to my xorg.conf file and low and behold I have full screen resolution again.

I hope this helps others with this problem.

---

