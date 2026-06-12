---
title: "[SOLVED] CD/DVD drive stopped working."
date: 2009-01-07
forum: System76 Support
---

### Post by Lee_Machine on 2009-01-07
So I'm seeing other posts about peoples optical drives stop working. Well now has mine. 

It worked about 12 hours ago at work when I was watching a movie...its my turn to stay the night and babysit the servers :)

Tonight I popped in a copy of Shoot em Up and it didn't read the disc. I thought it might be the disc. So i tried another movie, same thing.

I tried all media types I had around the office DVD/CD -+R, RW, and DL

Both blank and with data on it. Nothing is readable. 

I checked to see if my drive was being detected with a scsiadd -s command and the drive is there.

Just no media is reading. 

I also tried sudo cdparanoia -vsQ with a metallica CD and its seeing the tracks but its not showing up within gnome.

I checked bug reports on LP, but so far nothing new about this.

Any ideas?

BTW I've dont nothing new or install new programs, just system updates. I also pulled down the newest backport-modules.


Thanks again,

---

### Post by Lee_Machine on 2009-01-07
I read on a post on LP that using the drive virtually in windows XP will work. Sure enough I mounted the host drive in XP and bam it works. LOL WTF is that?

---

### Post by thomasaaron on 2009-01-07
What's the output of...
> 
uname -r

Are you using proposed? or Backports?
I'll try to duplicate the problem here in the shop.
Can you try a previous kernel?

---

### Post by Lee_Machine on 2009-01-07
wow thanks for the quick reply

2.6.27-11-generic 

Another thing I just did is when I have the drive mounted in XP and play it, then I can go into Mplayer and hit play DVD and it works just fine....still not shown up in nautilus.

Backports.

---

### Post by thomasaaron on 2009-01-07
I'm imaging now.

What about proposed and backports? Are they activated in your Software Sources?

Does it do this in a previous kernel?

---

### Post by Lee_Machine on 2009-01-07
I have both Proposed and backports checked off.

I dunno about an older kernel, Ill reboot into one and see.

---

### Post by Lee_Machine on 2009-01-07
So im booted up in 2.6.27-7-generic and i dont get the same errors. I then reboot back into 2.6.27-11-generic and it now works just fine...huh.

Thanks for the help, i rebooted first before I started a thread. I then installed the newest backports. without the reboot. So maybe that fixed it.

Any ideas what the issue could have been?

Thanks again for the help.

---

### Post by thomasaaron on 2009-01-07
OK.

I've got my shop panp4 fully updated with both proposed and backports. On xxx-11, I'm not seeing it. But I rebooted after every set of updates and retested.

I'm guessing it was a glitch in support for the SATA DVD drive that was quickly fixed.

Let me know if anything else happens, and I'll pursue it further.

Best,
Tom

---

