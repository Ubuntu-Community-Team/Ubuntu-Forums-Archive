---
title: "Ubuntu 9.10 on PanP5 -- Does HDMI work?"
date: 2009-10-15
forum: System76 Support
---

### Post by samalex on 2009-10-15
Hi,

I'm just curious if anyone has tried Ubuntu 9.10 on a PanP5, and if so does HDMI out work with audio and video?

And if you have ran 9.10 on a PanP5 but haven't tested HDMI, any thoughts in general?  Just curious --

Thanks,

Sam

---

### Post by HotShotDJ on 2009-10-15
I'm using 9.10 -- I'm not sure how to check HDMI video, but based on the attached screenshot, my guess is that HDMI audio should work.  I've got a friend with an HD TV that has HDMI inputs.. perhaps I should visit him and try it with my PanP5 and see what happens. :)

---

### Post by samalex on 2009-10-16
Nice!  Yes please do test this if you can because this might be the singular reason for me to move up to 9.10 sooner then later.

Thanks --

Sam

---

### Post by betrunkenaffe on 2009-10-16
I'm taking my PanP4 to work tonight to test just this feature. From what I understand, the issue was Ubuntu based, not hardware. If works for PanP4, should work for 5.

I'll let you know.

---

### Post by Lee_Machine on 2009-10-16
I have been messing around with audio over HDMI for quite some time on my PanP4n. I was only able to get it working once with 8.10.

I looked to see if it worked with 9.10 Alpha...3 I think, and it did not.

the output of aplay -l should show NVIDIA HDMI.

and now with Ubuntu 9.10 I get

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]

Which is very good, that is what is supposed to show up.

I connected the laptop to the TV, but for the life of me I could not get it too work. I tried multiple video players, and many audio settings.

I'm positive now its just a settings issue, once that's settled we should have audio over HDMI for now on! :guitar:



So please post if any of you get it to work.:P

---

### Post by Lee_Machine on 2009-10-16
I just though I would go back to the basics, and make sure nothing was muted....and well *cough* it was.

I ran alsamixer, and IEC958 1 was muted :P

So audio over HDMI works wonderfully :popcorn:

Ubuntu 9.10 64bit

---

### Post by samalex on 2009-10-16
> **Lee_Machine said:**
> I just though I would go back to the basics, and make sure nothing was muted....and well *cough* it was.

I ran alsamixer, and IEC958 1 was muted :P

So audio over HDMI works wonderfully :popcorn:

Ubuntu 9.10 64bit

Awesome!!!  And this was with it installed and not just from the bootable CD?  

I had originally planned on installing 9.10 after my online class was done in December, but I might have to jump the gun and install it when it's released on Oct 29th because it would be nice to have this working. 

Sam

---

### Post by Lee_Machine on 2009-10-16
Yes, this was with it installed on the hard drive.

---

### Post by betrunkenaffe on 2009-10-17
I couldn't even get it to recognize the HDMI tv as a display, is there anything I should be doing other than simply hooking it up and auto detecting inside nvidia settings?

I can't test further until Wed cause off work.

---

### Post by Lee_Machine on 2009-10-17
No, you just plug it in and click "Detect Displays" in the NVIDIA Settings.

---

