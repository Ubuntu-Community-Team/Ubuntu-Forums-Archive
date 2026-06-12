---
title: "[Kernel Choice] ubuntu studio vs. ubuntu general"
date: 2008-05-28
forum: Ubuntu Studio
---

### Post by kakyoism on 2008-05-28
I had thought that ubuntu studio was just a collection of software
until I realized that it requires linux-rt.

I have a desktop that works as my SVN server and some Matlab work.
Now I wonder if I'd like to have some audio production work done
with it. Is the ubuntu studio+linux-rt stable enough to secure
my regular tasks? Is it worth a change from the general?

Thanks.

---

### Post by Samhain13 on 2008-05-28
Why don't you just install the RT kernel from the repos. That's what I've been doing since Feisty as I play with audio (MIDI) too some times. Upon installation, your GRUB menu will be edited and you'll be given a choice on what kernel to boot. When doing your regular work, maybe just boot the Generic kernel; and when editing audio, boot the RT. :)

---

### Post by atomkarinca on 2008-05-28
The major difference between the regular kernel and rt kernel I have noticed is their Jack support. rt kernel can handle Jack very well, whereas it's hard to get it working with regular kernel. Other than that Ubustu is just a meta package with great production applications and very cool artwork.

---

### Post by angelsguitar on 2008-05-28
> **Samhain13 said:**
> Why don't you just install the RT kernel from the repos. That's what I've been doing since Feisty as I play with audio (MIDI) too some times. Upon installation, your GRUB menu will be edited and you'll be given a choice on what kernel to boot. When doing your regular work, maybe just boot the Generic kernel; and when editing audio, boot the RT. :)

May I just add to the excellent suggestion:  You can just install the ubuntu-studio packages (all the ones that start with the name ubuntu-studio - like ubuntu-studio-desktop, ubuntu-studio-audio, and so on...) available from synaptic.  That way you can have all the packages and rt kernel from the Ubuntu Studio distro along with your current setup. You can choose which kernel to boot at the GRUB menu on startup.

---

### Post by Stochastic on 2008-05-28
> **kakyoism said:**
> I had thought that ubuntu studio was just a collection of software
until I realized that it requires linux-rt.

It's still is a collection of software, the kernel is just a special piece of software.

> **kakyoism said:**
> Is the ubuntu studio+linux-rt stable enough to secure my regular tasks?

Yes, it's stable enough.  If you happen to find it otherwise, please file a bug report.

---

