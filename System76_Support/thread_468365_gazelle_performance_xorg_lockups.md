---
title: "gazelle performance xorg lockups"
date: 2007-06-08
forum: System76 Support
---

### Post by tedrampart on 2007-06-08
hey all,

I've been working with the tech support on this for over a week now, but can't seem to get it resolved so I thought I would open it up to the forum for any suggestions.

on my gazelle performance (brand spankin new model too, purchased late in may of this year.. its the new version with bluetooth) my system locks up randomly for about 30sec - 1 min, where only the mouse is movable.  When I run top, I can see that xorg is jumping up to 100% causing the screen to lock up.  its been doing this since I first turned the machine on.

we thought at first it was the dvd drive causing errors, which it was, but after doing some tests, it became clear that this was a seperate issue.

I've tried reinstalling and doing the restore, but that didn't help.  the only thing that did help was disabling the accelerated nvidia driver in the restricted manager.

but this isn't good enough, because whats the point of paying that little extra for beefy accelerated video, when you can't use it right?  

from what Tom said in tech support, this is a very rare thing, so I don't expect to find too many fixes here, but more suggestions on what I could look into.  I've also looked in the other ubuntu sub forums here, as well as google, and the nvidia forum.. but no help.

---

### Post by tedrampart on 2007-06-10
here's some attachments that might help with this issue..

nvidia bug log, xorg.conf, and a screenshot of top

please, someone must have some insight.. its really turning my experience with this machine into a sour one, and I know this is a special case....

---

### Post by tedrampart on 2007-06-10
after talking to someone at nvidia's bug report, they told me this:

>  [I]In your bug report I see several ACPI exceptions, which are symptoms of
a BIOS bug.  Its not clear from your email whether you've verified that
you're using the latest BIOS.

Also, does disabling the Composite extension in xorg.conf have any
impact on this problem?[/I] 

I tried disabling composite, and it locked up right after I restarted.

the ACPI/BIOS bug they mentioned got me thinking.  when I got my gazelle performance, CPU stepping wasn't working, and I got messages from the cpu frequency monitor saying cpu stepping wasn't supported.  

I had to add "acpi-cpufreq" manually to get cpu stepping. 

looking in the bios it says its version 203, and on the asustek website for model Z62jm (the model of the gazelle), it has version 205 as the latest, but doesn't say how to flash the bios in linux without a floppy drive.

would this be causing it?

---

### Post by thomasaaron on 2007-06-11
It's definitely worth a try.
I've got a bootable USB image and instructions.
Send me an email at support[at]system76[dot]com, and I'll reply with the necessary files.

---

### Post by tedrampart on 2007-06-13
well flashing the bios to version 205 seemed to fix the problem.  its been over 6 hours since my last reboot, and has been going with no lockups since yesterday after I flashed it..

---

### Post by thomasaaron on 2007-06-13
OK. Let's run it for a while longer just to be sure.
Sounds promising, though.

---

### Post by voidmage on 2007-06-13
I received my Gazelle today. While X did lock up in gnome, I wasn't able to replicate this in KDE.

---

### Post by tedrampart on 2007-06-14
did it lock up the same way?  like xorg spiked the cpu, but the mouse could move?

could you tell me what the bios version is on your gazelle?

---

### Post by voidmage on 2007-06-14
Yes it did, and I just saw it happen in KDE this morning.

---

### Post by tedrampart on 2007-06-14
if its the same as my issue, try flashing it to bios version 205, it seemed to work for me.  email tom at tech support for the files and instructions.

also curious as to if you had issues with cpu-stepping?

---

### Post by voidmage on 2007-06-14
Just flashed the bios from 203 to 205. I'll keep you all posted on improvements.

---

### Post by thomasaaron on 2007-06-15
I just flashed a GazP3 here at the shop. So far, no more lockups.

---

### Post by tedrampart on 2007-06-15
wow, so there's a few of them out there now creeping to the surface.  

hopefully we nipped this frustrating problem in the bud for good..

---

### Post by thomasaaron on 2007-06-15
There are probably less than a dozen out there.
My count is that five of them are now cured.

(The BIOS of the others might be current though.  It's impossible to tell.)

I appreciate all the help, though, on sorting it all out.

---

### Post by paulkingnz on 2008-02-22
I had this problem with xorg 100% cpu nvidia and KDE and I fixed it by running nvidia-xconfig and then restarting X with ctrl-alt-backspace.

---

