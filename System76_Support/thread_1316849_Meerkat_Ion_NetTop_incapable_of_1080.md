---
title: "Meerkat Ion NetTop incapable of 1080?"
date: 2009-11-06
forum: System76 Support
---

### Post by slimteufel on 2009-11-06
Did I just buy a computer that cannot display 1080? Seriously?

---

### Post by Lee_Machine on 2009-11-06
Yep, I looked into getting one. 720p is it's max and it will struggle with that....actually the review said that 720p was unwatchable, 

[http://www.tweaktown.com/reviews/2898/gigabyte_ga_gc330ud_mini_itx_dual_core_atom_tested/index9.html](http://www.tweaktown.com/reviews/2898/gigabyte_ga_gc330ud_mini_itx_dual_core_atom_tested/index9.html)

According to this you can overclock it, and 720p plays just fine...at > 90% CPU usage. :D

[http://www.anandtech.com/weblog/showpost.aspx?i=602](http://www.anandtech.com/weblog/showpost.aspx?i=602)



But to be fair though, my computers with new Core2Duo's hate life when I play 1080 video. 

The Meerkat is still a good buy, it will play downloaded content just fine, just not the HD stuff.

---

### Post by echo314 on 2009-11-06
What specifications led you to believe the computer you bought would be capable of 1080? Maybe are unaware that the Meerkat does not have the processing power of a traditional desktop, itself being a *NetTop*

Sys76 has a nice return policy. Assuming you have everything, good condition, etc, you may be able to return it, just eat the shipping charges, and get a different comp from them.

---

### Post by snowpine on 2009-11-06
The Atom is the weakest processor available on the market today, lol! It's like using a Celeron or old Pentium 4. :)

---

### Post by thomasaaron on 2009-11-06
> The Atom is the weakest processor available on the market today, lol! It's like using a Celeron or old Pentium 4.

It's not really meant to be a powerhouse production machine. It is meant to be a good, inexpensive system for Internet-related activity. 

Of course, it can do a lot more than that. But that is the intended usage.

---

### Post by snowpine on 2009-11-06
> **thomasaaron said:**
> It's not really meant to be a powerhouse production machine. It is meant to be a good, inexpensive system for Internet-related activity. 

Of course, it can do a lot more than that. But that is the intended usage.

I am in fact typing this from an Atom 330 desktop. I agree it is an excellent platform for energy efficient, general purpose computer use. It's just powerful enough that I can even run Windows XP in VirtualBox! I kind of wish, however, I'd spent a little extra and gone for the Ion platform (like the Meerkat) instead of the integrated Intel... maybe next time!

---

### Post by slimteufel on 2009-11-06
> **echo314 said:**
> What specifications led you to believe the computer you bought would be capable of 1080? Maybe are unaware that the Meerkat does not have the processing power of a traditional desktop, itself being a *NetTop*

1. nVidia GeForce 9400M
2. HDMI plug

> **echo314 said:**
> Sys76 has a nice return policy. Assuming you have everything, good condition, etc, you may be able to return it, just eat the shipping charges, and get a different comp from them.

My first idea was to frisbee the worthless hunk of ****. After I calm down, this *NetTop* will be given to my daughter. Or I can enjoy the fact that I assume too much and just frisbee this brick. **** fuckity **** **** ****.

---

### Post by jbelmonte on 2009-11-06
I wonder if this limitation is a Linux/Ubuntu limitation as the [hardware]("http://www.nvidia.com/object/sff_ion.html") should support 1080p. Other Ion Nettops claim support for full 1080p HD and they seem to have the same basic hardware (e.g. [AspireRevo 1600]("http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68974&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=750687650") or the [EeeTop PC ET2002T]("http://www.asus.com/product.aspx?P_ID=DPWRF5hdLVP5bqsQ")) but they use various flavors of Windows for the OS.

---

### Post by Lee_Machine on 2009-11-06
There is a huge difference between 1080p to a monitor, and 1080p video playback.


Plus as a rule you should never take what computer companies say at face value.

Go by independent reviews, and benchmarks.

If there is ever any hardware limitations it's not coming from the OS, but the drivers. In this case that does not apply.

---

### Post by HotShotDJ on 2009-11-06
> **slimteufel said:**
> My first idea was to frisbee the worthless hunk of ****. After I calm down, this *NetTop* will be given to my daughter. Or I can enjoy the fact that I assume too much and just frisbee this brick.Let's calm down a bit.  System76 doesn't market this machine as anything more than a low-power machine for basic networked applications such as web browsing, email, etc.  You looked at the hardware and made some assumptions about it.
> **jbelmonte said:**
> I wonder if this limitation is a Linux/Ubuntu limitation as the [hardware]("http://www.nvidia.com/object/sff_ion.html") should support 1080p.I believe the problem here is that, while the hardware and the NVidia drivers both will support what slimteufel is trying to do, the software he is using probably doesn't.  NVidia only recently released the decoding algorithms (VDPAU) that allow video decoding by the GPU rather than the CPU.  ATI has not released theirs at all.  However, none of the default players in Karmic have VDPAU support yet, so, what is happening is that the CPU is trying to get the decoding done, which it just can't handle.

[HERE]("http://newyork.ubuntuforums.org/showthread.php?t=1037625") is a thread that I've found that deals with the issue of installing VDPAU enabled video players... it is a LONG thread and page one talks about Jaunty... but you'll find information and suggestions for Karmic later in the thread.  The good news is that VDPAU is being integrated into the players that are available for Ubuntu... the bad news is that it is not done yet.  But if you don't mind doing some research and tweaking your system, you might be able to get it now.

---

### Post by jjacobs2 on 2009-11-07
I was able to enable it in Jaunty by adding the avenard repos.
[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)
And installing vdpau, the nvidia drivers, and an updated mplayer.  The video output in  mplayer must be set to vdpau.  This only works for files though, if you wish to play bluray discs you'll need to try something else.  I didn't try this on a computer with the system 76 drivers though so it may have other issues.  Another option is to simply compile the software you need and install the version of nvidia drivers you want manually.  You may need to make a special launcher with the correct mplayer commands to activate vdpau for the file type you use.

EDIT: The mplayer version in Karmic does come with the vdpau output option in preferences.  There's also a driver in the repository for vdpau support.  It's called nvidia-185-libvdpau.

---

### Post by Rob_H on 2011-03-26
Reviving this old thread. Have any of you had any luck getting smooth Flash video on this system? Supposedly, the latest NVIDIA driver in combination with Flash 10.2 on Maverick will enable hardware accelerated video, but Hulu is still choppy for me. Others having the same experience?

---

