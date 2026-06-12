---
title: "Support for GMA500 cards ?"
date: 2009-09-24
forum: Ubuntu Moblin Remix
---

### Post by bodhi.zazen on 2009-09-24
Does Moblin have support for the Intel GMA 500 (common video card in netbooks) ?

---

### Post by sexyclient on 2009-09-24
I'm pretty sure that there's no support there - only the 950.  I read the info on a comment on the moblin announcement of the 2.0 release, though, so it wouldn't hurt to verify.

---

### Post by NormanFLinux on 2009-09-24
The poulsbo drivers are available in the respositories. But they don't work on Ubuntu Moblin Remix.

---

### Post by bodhi.zazen on 2009-09-24
> **NormanFLinux said:**
> The poulsbo drivers are available in the respositories. But they don't work on Ubuntu Moblin Remix.

Thank you, I was hoping the moblin remix included a newer driver for the GMA 500, which is actually fairly common in netbooks, that is working with the newer kernels. I believe Dell released the drivers that were incorporated into the poulsbo driver, and so was hoping with moblin they were willing to work on and release an updated driver for use on netbooks.

Alas, everyone is moving forward with the Intel 950 driver, but the 950 card is not yet as prevalent as the 500 in netbooks (moblin is targeting netbooks and the 950 is more prevalent in laptops).

---

### Post by PeteBuntu on 2009-10-11
> **NormanFLinux said:**
> The poulsbo drivers are available in the respositories. But they don't work on Ubuntu Moblin Remix.

Why not?

---

### Post by michael37 on 2009-10-13
> **bodhi.zazen said:**
> Does Moblin have support for the Intel GMA 500 (common video card in netbooks) ?

The worst news is that GMA 500 is not only not supported, but is also not planned to be supported.

Look at [http://moblin.org/downloads](http://moblin.org/downloads), no support for both current release and developer-only 2.1 release.

> 
System Requirements:

    * CPU: Intel(r) Atom(tm) or Intel(r) Core(tm) 2 CPU (support for SSSE3)
      Note: Moblin will not work on non-SSSE3 CPUs
    * Platforms with the GMA-500 Graphics chipset are not supported.


---

### Post by bodhi.zazen on 2009-10-13
> **michael37 said:**
> The worst news is that GMA 500 is not only not supported, but is also not planned to be supported.

+1  I understand their reasoning for this decision, but I think it is unfortunate.

---

### Post by StaRetji on 2009-10-19
> **sexyclient said:**
> I'm pretty sure that there's no support there - only the 950.


Well, not sure if supports this GPU, but I have two Atom motherboards, one with N270 and one with N330 Atom.
Both have GMA950 and both works unbelievably slow.
For example, browser will open about a minute while system is not responsive, after finaly launching the browser it will become responsive.
Then, if you visit youtube you'll wait another minute to load and to become responsive, after that if you play a video, the system is unresponsive till the video finishes
(actually video is static, you can hear sound).

Just my two cents...

---

### Post by Jackyboy86 on 2009-10-27
I've got it working!
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1253406](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1253406)
Gives a step by step guide.
Good luck!
 
I'm having problems with the UMR GUI, but i'm pretty sure it's something to do with compiz, not the PSB drivers...

EDIT: cancel my last - it's a conflict between PSB and the moblin shell. No-go. However, gnome works a treat. I'll defo be switching to Karmic on my mini 10

---

### Post by StaRetji on 2009-10-29
> **Jackyboy86 said:**
> I've got it working!

When you say working, can you be more specific please.

How is browsing experience?
Can you watch Youtube videos decently?

Thx...

---

### Post by mikewhatever on 2009-10-31
> **StaRetji said:**
> When you say working, can you be more specific please.

How is browsing experience?
Can you watch Youtube videos decently?

Thx...

My experience is based on Jaunty only (couldn't get Karmic working with gma500 crap), but yes, both browsing and youtube videos are ok. Contrary to the understanding folks here, I think it simply outrageous, that Intel wouldn't provide drivers for its chipsets.

---

### Post by Jackyboy86 on 2009-10-31
Now, under karmic desktop - and moblin with Gnome running - everything is working as it should.
Youtube is fine - I see no need for improvement.
It's the same as it was in Jaunty - the guide uses backports to jaunty instead of new drivers.
Give it a try in a new partition.
I'm running the two side by side at the moment, and i'm quite happy, i'll be removing Jaunty within the next week or so.

However, in the Moblin shell theres a conflict with the PSB drivers, so it's Gnome or KDE only, methinks...
The syslog output is:
moblin-panel-me[1420]: segfault at e ip 04009131 sp bf8bf620 error 4 in psb_dri.so[3fde000+2b2000]

If anyone can shed any light on this - i'd be greatful!

---

### Post by mikewhatever on 2009-10-31
> **Jackyboy86 said:**
> Now, under karmic desktop - and moblin with Gnome running - everything is working as it should.
...........

I found the instructions you followed incomplete to say the least. For example, the following code should be preceded by a wget url line, but there is none.

```
# Install downloaded psb-kernel-* packages
dpkg -i psb-kernel-*
```

I tried it nevertheless, and had errors while building the kernel module. Apparently, the psb-kernel-source package version was wrong, but there was no indication which one should install successfully.
In addition, both ppa keys were not found.

---

### Post by Jackyboy86 on 2009-10-31
Did you download the kernel modules that were linked in the post?
I ignored that line and just ran the .deb files - it worked fine.
it doesn't need wget - you download the .deb's manually.

It's on there as the 1st step (i think it's the 1st)
Download the modules [link]
click the link, it takes you to a post which has the modules attached!

At that stage, run the .debs and then continue as per the guide.

As for the ppa keys - I didn't need them :S
I've ignored that part of the post, as well!

---

### Post by mikewhatever on 2009-10-31
Are these the packages you used?
[http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13)
If so, did you download and locally installed all three or just the psb-kernel-source_4.41.2?

I'll probably try again sometime next week, with more means to test and backup.

---

### Post by Jackyboy86 on 2009-11-01
Aye, those are the ones. You need all 3 .debs
Install headers, modules and then the source and you'll be laughing.

---

### Post by bodhi.zazen on 2009-11-01
> **Jackyboy86 said:**
> I've got it working!
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1253406](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1253406)
Gives a step by step guide.
Good luck!
 
I'm having problems with the UMR GUI, but i'm pretty sure it's something to do with compiz, not the PSB drivers...

EDIT: cancel my last - it's a conflict between PSB and the moblin shell. No-go. However, gnome works a treat. I'll defo be switching to Karmic on my mini 10

Thank you for posting that, and yes I can confirm that it is working.

I had to change my dpi from135 to 96.

---

### Post by NormanFLinux on 2009-11-02
Is there a fix for dropping to the TTY shell upon reboot?

---

### Post by bodhi.zazen on 2009-11-02
> **NormanFLinux said:**
> Is there a fix for dropping to the TTY shell upon reboot?

If X is working you can do it from X, simply remove then re-install the psb-kernel-source any way you wish (synaptic).

If X fails (as is often the case), then no.

---

### Post by Jackyboy86 on 2009-11-03
Just to say, that after a little hiccup (involving gParted and a kernel panic) I've just reinstalled Karmic UNR - and followed this guide again.
20 minutes work, and everythings running smoothly.
When the kernel updates come along is a different matter - maybe uninstalling and reinstalling the psb kernel source file will work (as it did in 9.04) but until then, I can't tell.
Glad the link was of help to people!

---

### Post by StaRetji on 2009-11-06
Glad to read it works for you guys.
I prefer waiting for release that will have everything fixed,
so that I just install and start using the system right away ;)

Cheers...

---

### Post by Jackyboy86 on 2009-11-06
You'll be waiting a long time!
Maybe, just maybe, as 10.04 will be a LTS release, Dell/Intel might pull their fingers out and sort it, but thats only a hope...

---

