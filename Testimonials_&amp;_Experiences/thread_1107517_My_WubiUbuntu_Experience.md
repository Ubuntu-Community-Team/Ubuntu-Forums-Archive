---
title: "My Wubi/Ubuntu Experience"
date: 2009-03-26
forum: Testimonials &amp; Experiences
---

### Post by simpfeld on 2009-03-26
Before I say a thing, let me give you a quick bit of background. A friend of mine was sick of Vista and it's increasing sluggishness, so I suggested trying Wubi, as it wouldn't touch his Windows install and Ubuntu is supposed to be a very friendly Linux distro. My background is I'm an experienced Linux sysadmin but on all RPM based systems (RHEL, Centos, Fedora), the last time I saw a Debian based distro was about 12 years ago in the days of dselect. So I thought I could give a pretty good perspective of how things seem to a layman and a distro jumper. 

Firstly the the Windows installer is just fantastic, so so easy to use. WOW!

My first problem came when the machine (a Dell Inspiron 530) first booted into Ubuntu. It tried to go into X but the monitor flickered a few times then just went into power save. So I went to a virtual console (we have now crossed the line where my friend would have been lost), and saw his video card was an ATI Radeon 2400 HD. All my attempts to get the xorg autoconfigured with the comments at the top of /etc/X11/xorg.conf. These didn't do anything. So I manually tried to hack the file to get vesa, but I typo'd somewhere but fortunately this caused the startup to notice and drop into a fail safe vesa driver. I could then google and found a post with a method (on the command line, way beyond my friend) to get the proprietary ATI driver running with this card. OK, all Linux distros have issues with video cards, but seemed strange it didn't dump me straight to VESA at first boot.

OK sorted the video, then I noticed the update icon had appeared on the desktop. So I hit this to update. There were 288 packages available, so I let them go. Then the updater started and bombed after about 20 packages. The error was non specific to my lazy eyes, so I ran it again. But it then recommended a command line I needed to run (I can't remember exactly)  to clean up the previous thing (my friend was now giving me that I'll never be able to do any of this look). It was only then from the command line command that I saw it was actually out of disk in the '/' partition. Darn. I'm pretty sure it said in the install somewhere that 8GB was enough. I thought my 15GB was generous, but no. I've seen from the FAQ that I can resize the root disk in Wubi, but I'm not sure I have the disk space to install the resizer without more fiddling around. This could do with a GUI installed by default program for this. The resize command line trick will just frighten an ex-Windows user.

Oh another slight thing was, Wubi was installed on the d: driver, so it mounted /host as the d: but there didn't seem to be the machines c: drive anywhere mounted. Not sure how I can remedy this without hacking fstab. And also an icon al la Knoppix style on the desktop to show a newbie where their Windows files are would help I'd have thought. They wouldn't know where to start.

Not sure how much of these issue are upstream issues, rather than Wubi or even Ubuntu. But I think it still highlights how much work we the Linux community need to do to bring Linux (well at least non-preinstalls) to the masses. Basically too much command line hacking to get stuff going if things go south.

But thanks for a great job so far on Wubi, it is the way things need to go.

---

### Post by etnlIcarus on 2009-03-26
There's no way ubuntu should require that much diskspace. It was only a couple of years ago that I was running Ubuntu on a 5gb Maxtor drive.

---

### Post by bapoumba on 2009-03-27
Moved to Ubuntu Testimonials & Experiences.

---

### Post by BuffaloX on 2009-03-27
I think it should be able to run even on 4 GB, the 8GB is for extra stuff selected by users, and the users own data.

It's obvious that 95% probably never would have made it through that installation. It should have defaulted to VESA as you say,
But on a modern system, VESA isn't very cool.

It's sad that ATI and NVidia still cause problems on Linux.
ATI will probably become better with the open source drivers, but that doesn't change how things are right now.

---

### Post by wolfen69 on 2009-03-27
wubi is garbage. do a real install if you want real ubuntu.

---

### Post by armandh on 2009-03-27
I reduced the vista partition on my wifes lap top by 10Gb with the vista partition utility. 
[nothing else worked]
I then installed 8.04 to the unpartitioned space
grub worked as expected
vista is rarely used.

I had to explain to my wife that to see more of the e-mail than the preview pane double click. but she loves that ubuntu does NOT interupt her shopping or e-mailing with its own house keeping crapolla.

---

### Post by Baylee on 2009-03-28
Offcourse i see many e mails when i want to shopping and ubuntu does not interupt for me

---

