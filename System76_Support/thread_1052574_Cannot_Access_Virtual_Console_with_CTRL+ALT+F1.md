---
title: "Cannot Access Virtual Console with CTRL+ALT+F1"
date: 2009-01-27
forum: System76 Support
---

### Post by KRopa on 2009-01-27
Hiya, it's my very first post, although I have been reading these forums, and this topic in particular, for about the last six months.  I have experience with computers dating back to the Timex-Sinclair 1000, Commodore 64, mainframes, Mac and Windows, but am brand new to Linux.

My new Serval has been sitting in its box since early December, and tonight I finally turned it on.  After applying all of the updates using GNOME Update Manager, the first thing I did was to try to access a virtual console with CTRL+ALT+F1.  This blanked the screen but produced no login prompt.  I was able to get back to X with CTRL+ALT+F7.

This seems to be similar to a problem reported in this thread:
[http://ubuntuforums.org/showthread.php?t=1015624](http://ubuntuforums.org/showthread.php?t=1015624)

I attempted the "telinit 1" command suggested there, which brought up an "Ubuntu" splash screen and a progress bar which stalled at 90%.  Upon pushing CTRL+ALT+F1 again, the splash screen became distorted and the machine was completely unresponsive, except to the power switch.

Since I am new to Linux and learning as I go, right beside the Serval is an older Mac G4 Cube, on which I installed Debian "Etch" so that I'd have a place to try out commands and become familiar with another related distro.  Bringing up the virtual consoles was no trouble there.

The other forum thread remains unresolved, but indicated it could possibly be a hardware issue, so I'm checking with the System76 experts.

I'm liking the new machine so far, though, very speedy.  Also I am looking forward to becoming a more active participant in all of these forums.  Thanks for a more healthy alternative to Microsoft and Apple!

---

### Post by thomasaaron on 2009-01-28
> I have experience with computers dating back to the Timex-Sinclair 1000, Commodore 64

Those were my first two computers. We must be about the same age.

> the first thing I did was to try to access a virtual console with CTRL+ALT+F1

I seem to remember a previous forum post dealing with this on a newer Serval, but I can't seem to locate it. If memory serves, it turned out to be some sort of a bug with the nVidia driver.

I'll try to find it (and do some testing when my shop serval gets back from review). But in the meantime, you can always use Applications > Accessories > Terminal or boot into recovery mode and drop into a root prompt.

---

### Post by MorphWVUtuba on 2009-01-28
I had that problem on my Serval and you're right, Tom.  It is NVIDIA, the goobers.  I've learned to make do without.

But hey, maybe they fixed it with the new drivers they just released.  You catch word of that one?  Any idea if/when they'll be officially supported by Ubuntu/System76?

---

### Post by thomasaaron on 2009-01-28
I've not tested it with the new driver yet, but I will as soon as my Serval comes back from review.

Thanks for posting. I knew I'd seen this before!

---

### Post by KRopa on 2009-01-28
Thanks for investigating, y'all.  In spite of this little oddity, I was able to use the NVidia configuration tool, along with careful sudo-editing of Xorg.conf to successfully try out several dual-monitor setups... not bad for being brand new to it all, I thought.  I await the challenge of my first driver upgrade.

---

### Post by Lee_Machine on 2009-01-29
[HERE]("http://http://www.nvidia.com/object/linux_display_amd64_180.22.html") is the new driver. It's really easy to install. just a simple command line copy and paste, then a reboot. I found my Pangoline Performace to work a little better as far as playing Elder Scrolls Oblivion goes (better FPS and less lag)

---

