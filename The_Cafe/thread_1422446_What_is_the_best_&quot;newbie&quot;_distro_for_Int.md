---
title: "What is the best &quot;newbie&quot; distro for Intel graphics?"
date: 2010-03-05
forum: The Cafe
---

### Post by Dreakon on 2010-03-05
It seems Ubuntu has rather poor Intel graphics support at the moment (I have a Intel GMA 4500MHD).  YouTube videos are crazy choppy and there's noticable sluggish-ness in the GUI, using GNOME.  Even with desktop effects off.  Windows don't pop up right away, minimizing and maximizing them is noticably slow.

Anyways, I don't want to whine too much... but is there any easy-to-install-and-get-into distro out there with proper Intel graphics support?  Like, relatively on par to the snappy-ness of the GUI of Windows?

I really wish I could get Ubuntu working well though...

---

### Post by RiceMonster on 2010-03-05
Intel drivers are pretty bad in general. I don't know how much you're going to get out of switching distros, however, you could always try Fedora, OpenSUSE, or Mandriva.

---

### Post by NightwishFan on 2010-03-05
What version are you using, perhaps try the 10.04 Lucid Alpha. As for distros, if you want to shop around.. I recommend (in this order).

Debian (Stable/Testing/Unstable, any will do)
OpenSUSE
Puppy
Fedora

---

### Post by Dreakon on 2010-03-05
> **NightwishFan said:**
> What version are you using, perhaps try the 10.04 Lucid Alpha. As for distros, if you want to shop around.. I recommend (in this order).

Debian (Stable/Testing/Unstable, any will do)
OpenSUSE
Puppy
Fedora
Well, if I weren't back on Windows, I would be using 9.10 32-bit.  I'm tempted to wait until Lucid comes around and give it another try, but I really have to wonder if it'll be any better by then lol...

---

### Post by NightwishFan on 2010-03-05
The new Ubuntu is excellent, though oddly it caused me to switch to Debian. My machine is older and I need to use a lighter setup to get rid of some of the memory pressure. I also can use rolling release, which I have never tried before.

Some people also swear by Arch, though I never tried it, so I cannot confirm.

Perhaps try Debian Unstable in a Virtual Machine on your current OS. You need to install Debian testing and manually update, it should not be hard. If you have any questions about it, just ask.

---

### Post by Dreakon on 2010-03-05
Well, for the sake of community (Ubuntu having one of the biggest), I don't really want to stray too far unless I have to... the most important thing I'm looking for is better Intel support.  I looked into Arch Linux but that looks a bit more complicated to set up then I'm looking for lol.

Does Debian or Ubuntu 10.04 boast, specifically, improvements on Intel graphics?  I'm sure otherwise they're great. ;)

---

### Post by NightwishFan on 2010-03-05
Such drivers are upstream in Xorg and the Kernel. I am actually using a 2.6.33 Zen kernel, but I believe stock Debian Unstable has 2.6.32.

Ubuntu does not develop the drivers itself, sometimes it just has a X.org that does not agree with them. (It can happen to anyone)

Ubuntu 10.04 is *based* on Debian testing, and it has already reached feature freeze. Debian Unstable is more up to date than that by now. Testing has moved on as well I am sure.

(Note testing and unstable really are not "unstable" they just perhaps can be.) Generally if something works be careful when you upgrade it is all.

---

### Post by Dreakon on 2010-03-05
> **NightwishFan said:**
> Ubuntu 10.04 is *based* on Debian testing, and it has already reached feature freeze. Debian Unstable is more up to date than that by now. Testing has moved on as well I am sure.
Are you suggesting I try Ubuntu 10.04 Alpha or Debian Unstable?  Like I said, if I can keep going with Ubuntu, I'd prefer it given it's ease-of-use and community.

And let me see if I got this right.  Ubuntu 10.04 has reached feature freeze?  I'm guessing that means that new features are done being added and they're just preparing it for release, right?  If I were to install the Alpha now, would I have basically was will be released later in April?

If so... would I have to download/burn/upgrade to 10.04 when it comes out, if I decide to go with the Alpha for now?  Or will it just update as normal and go from there?

---

### Post by NightwishFan on 2010-03-05
You could update right now if you wished. I have some issues with the boot splash, but it still works. It is very stable and fast so far and it is based on Debian Testing instead of Unstable.

I am saying if you want, go with Debian. I was stressing that it is not much harder to use. Except for installing Nvidia drivers. ;)

---

### Post by Dreakon on 2010-03-05
Hmm... interesting.  If I had to choose I would go with Ubuntu.  Debian seems fine but I think Ubuntu is designed to be a little more for novices like me.  Especially if I am urged to start traveling into the "Unstable" releases.

1. How would I go about making a CD to install Ubuntu 10.04 Alpha?  Assuming I wouldn't have to install the real 10.04 when it's released...  Note, I don't currently have Ubuntu installed lol. ;)

2. I dunno if this was actually answered, but does 10.04 actually boast significant improvements in the Intel graphic drivers, at least as compared to the default ones in 9.10?  I'm sure the rest of 10.04 is really nice, but the deal breaker for me is the graphics.  Will I actually be able to watch YouTube videos? :P

Thanks for all the help so far, by the way!  It's very appreciated. :)

---

### Post by NightwishFan on 2010-03-05
To get Ubuntu Alpha 3:
[http://www.ubuntu.com/testing/lucid/alpha3#Download%20Alpha%203](http://www.ubuntu.com/testing/lucid/alpha3#Download%20Alpha%203)

Alpha 3 Info:
[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)

New Ubuntu Branding:
[https://wiki.ubuntu.com/Brand](https://wiki.ubuntu.com/Brand)

Enjoy!


New stuff in Linux 2.6.32 used in Ubuntu 10.04
[http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

> Intel driver:

    *

      GPU reset on i965. The GPU is reset when the driver detects that the GPU has hanged (commit), (commit)
    *

      Framebuffer compression (about 0.5W power savings when idle) (commit) and pre-GM45 (commit)
    *

      Add dynamic clock frequency control: When the graphics are idle, the LVDS refresh rate and the GPU clock is reduced, and memory self refresh is enabled to go into a lower power state. All of these things are reenabled between frames when GPU activity is triggered (commit)
    *

      Improve behaviour under memory pressure. Now when the system is running out of memory, the driver can free used buffers (commit), (commit), (commit)
    *

      8xx works again, since the regression with GEM's introduction back in .27 

---

### Post by Dreakon on 2010-03-05
Thanks for all the links and info!

Perhaps anyone around here using the Lucid Alpha and an Intel graphics chipset want to give me an idea if there are any significant improvements?  Enough to warrant taking the plunge? :P  All the technical jargon goes right over my head lol.

---

### Post by cariboo on 2010-03-05
I'm no really sure we should be recommending Lucid to a newbie. I have Karmic running on my atom powered media center pc, with the 945 chipset, it auto detects monitors, quite well, and will run full affects. The only problem I have is running HD flash full screen, but that may be due to lack of CPU power more than anything else.

I'm actually running XBMC Live on it, which is based on Karmic, and I'm very happy with the performance.

---

### Post by NightwishFan on 2010-03-06
Dreakon,

I just purchased a laptop today and decided to go with an Intel chip. Firstly I completely removed Windows 7 and installed the new Ubuntu Alpha. I found that Ubuntu 10.04 had very poor performance in games like Urban Terror (Around 7 fps). I am unsure of the reason, though I am assuming that it is not a permanent issue. Because of that and a few other problems, I decided to install Debian Testing.

Urban Terror worked with 50fps and the issue with my laptop unable to change brightness was solved, probably due to newer vesions of drivers and X.org. Ubuntu is not that far behind Debian, so changes may hit there as well.

I am not pestering you to try Debian, I just wanted to inform you that I am now in a similar boat. That is how I solved it. If you are willing to give it a try, it is not harder than Ubuntu, just more manual with what packages to install.

For reference, this is the laptop I am using:
[http://hu.asus.com/product.aspx?P_ID=ZWrNVPXEbNNTjJZg](http://hu.asus.com/product.aspx?P_ID=ZWrNVPXEbNNTjJZg)

---

### Post by Dreakon on 2010-03-06
Hmm... I seriously can't decide what O/S to go with at the moment, so I guess I can give Debian Testing a try.  I tried 10.04 Alpha actually and was impressed with the fact that I could actually watch a YouTube video fullscreen without serious stuttering and slowdown.  So if that's what 10.04 Alpha can do while still having graphic troubles (according to your post), Debian should be right up my alley.

I guess my question is, is there any way to use the Debian Testing video drivers, but keep everything else as Debian Stable?  I'm a little uncomfortable using an entire operating system where things haven't been very thoroughly tested.  Which is why I'm iffy about staying on the 10.04 Alpha...

And if I'm running 32-bit, should I download the i386?

I'm a little confused with the download section since it seems it has a list of ISO's (debian-testing-i386-CD-1.iso to debian-testing-i386-CD-43.iso).  Do I just download one of them...?

EDIT: While I'm in the process of asking too many questions in one post, will I have to install GNOME myself?  Or does it come with it?

---

### Post by ssam on 2010-03-06
the intel driver went through some big transitions last year (kernel mode setting, uxa). see [http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/](http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/)

it had not fully stabilised by the time 9.10 karmic came out. i recommend that you have a play with a lucid alpha or daily live cd ( [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) ). you probably should wait until at least the beta before installing, but you can still see the progress that has been made with the live cd.

---

### Post by MasterNetra on 2010-03-06
> **NightwishFan said:**
> The new Ubuntu is excellent, though oddly it caused me to switch to Debian. My machine is older and I need to use a lighter setup to get rid of some of the memory pressure. I also can use rolling release, which I have never tried before.

**Some people also swear by Arch, though I never tried it, so I cannot confirm.**

Perhaps try Debian Unstable in a Virtual Machine on your current OS. You need to install Debian testing and manually update, it should not be hard. If you have any questions about it, just ask.

Its a pain in the Arch to get setup initially. I suppose though once you do, you could use Clonezilla to create a re-installation CD/DVD. Arch is diffidently not for newbies.

---

### Post by cap10Ibraim on 2010-03-06
I have the same graphics card using Ubuntu 9.10 karmic koala
Intel® Graphics Media Accelerator 4500MHD with 128MB-1759MB
dynamically allocated shared graphics memory
It works great with extensive graphics effects !

---

### Post by doorknob60 on 2010-03-06
I haven't tried Ubuntu on this laptop (it has Arch), but I've had some significant graphics performance boosts ever since it got Xorg 1.7 and Kernel 2.6.32 (both which I assume Ubuntu 10.04 has), that driver has progressed a lot over the last few months.

---

### Post by NightwishFan on 2010-03-06
I am using Debian Unstable and it is bug free for me, but that is just me. Debian Testing should be more up to date and perhaps even more bug free than Ubuntu, not far behind unstable. No critical bug packages can get into debian testing. Debian stable may not be up to date enough with kernel and xorg to see improvements but you can try it. I would say go with testing.

I think you can install a specific package group for unstable or testing like this, but I think you will need testing in your sources.list. You can 'configure sources.list in Synaptic, under Settings -> Respositories and add testing as shown in the screenshot. Then reload the packages, and update: xserver-xorg-video-intel. **Make sure you input "testing" where it says "unstable"**.

After than just remove the testing entry and reload again, and you have stable with testing intel drivers.

I really advise just adding only testing, and updating to it. Just change every "stable" or "lenny" to testing and running this in root terminal. **This will update you to testing**, which I think you will like.
```
aptitude full-upgrade
```

After updating it should work fantastically, and its kernel is more desktop enabled, with preemption added.

---

### Post by Simon17 on 2010-03-06
Gosalia.

---

### Post by Simon17 on 2010-03-06
> **simon17 said:**
> gosalia.

+1

---

### Post by swoll1980 on 2010-03-06
> **Simon17 said:**
> +1

lol

---

### Post by MasterNetra on 2010-03-06
> **Simon17 said:**
> Gosalia.

Odd its not at Distrowatch, found its site none the less. DLing now.

---

### Post by juky on 2010-11-06
> **MasterNetra said:**
> Odd its not at Distrowatch, found its site none the less. DLing now.

Hi,

are you saying that Gosalia does not have issues with intel graphics as in 10.04 and 10.10 (Lucid and Maverick)?

---

