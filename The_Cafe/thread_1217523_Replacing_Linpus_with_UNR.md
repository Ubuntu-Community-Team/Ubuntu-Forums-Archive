---
title: "Replacing Linpus with UNR?"
date: 2009-07-19
forum: The Cafe
---

### Post by Jestersage on 2009-07-19
I have a friend that wants to get the cheap model of Acer Aspire One, and apprrently the one they choose comes with Linpus. after reading the quick blurb on Wikipedia, I am wondering: how is it, and should i replace it with either openSuSE (known to have no issues with wireless) or Ubuntu NR?

---

### Post by t0p on 2009-07-19
Being an Ubuntero, I'd say go with Ubuntu.  But I recommend full Gnome desktop rather than Netbook Remix.

---

### Post by heroidi on 2009-07-19
> **Jestersage said:**
> I have a friend that wants to get the cheap model of Acer Aspire One, and apprrently the one they choose comes with Linpus. after reading the quick blurb on Wikipedia, I am wondering: how is it, and should i replace it with either openSuSE (known to have no issues with wireless) or Ubuntu NR?

try the normal Ubuntu because a friend of mnie installed netbook remix and he had issues with the window manager

---

### Post by ddrichardson on 2009-07-19
> **heroidi said:**
> try the normal Ubuntu because a friend of mnie installed netbook remix and he had issues with the window manager
Don't bother with Moblin yet, its not very quick on the Aspire One and uses ext3 by default, which is not optimal for SSD.  I removed it recently.

UNR works fine and supports all the A110L's hardware but you might need to blacklist the acer_wmi module.  Some have it working, I don't on the last update.  As for the window manager, there are issues reported with desktop-switcher, which switches between the two interfaces not working but the UME interface is actually quite good.

Arch works very well too, if you're feeling adventurous there's a guide here [http://wiki.lynxworks.eu/aspireone/arch](http://wiki.lynxworks.eu/aspireone/arch)

---

### Post by Jestersage on 2009-07-19
Thanks for everyone's response. I will consider Ubuntu vanilla, then. (Though i see no one recommend openSuSE)

I guess my issue is not just that "it's a netbook", but the fact that it is for my friend (mostly computer illiterate) who will be using it for a mission trip for about one year in the middle of who-know-where in India (no IT support joke plz), so I assume they will have very minimum support.

I do not mind doing more stuff to set them up, but I need to know what stuff I need to get to ensure they will still be functioning. My main concerns are the wireless drivers and VoIP.

Personally, I would rather recommend them to WinXP, but if they do want to go to the cheaper option, that's their call, and I intend to support them with the best capability. Even then, since they will be over at India, I will have to be able to get it right on the get go.

P.S. So, no Arch.

---

### Post by ugm6hr on 2009-07-19
Details re: NBR on Aspire One: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

I'm sure the same is true of Vanilla 9.04

NBR is easier to install on Netbooks due to the files coming ready as USB img.

Easy to replace NBR and install ubuntu-desktop or xfce4 (as I have).

Skype is best for Voip; not sure about Aspire One, but it works flawlessly on Mini 9.  Ekiga may suffice.

I've never used Suse, so can't comment.

---

### Post by Jestersage on 2009-07-19
^Thanks. As I know that 8.04 vanilla works well with HP desktop's card readers, the issues could be very minimized.

---

### Post by themusicalduck on 2009-07-19
I have a cheap Aspire One. The linpus OS is pretty awful.. but Ubuntu and netbook remix work pretty well.
With Ubuntu I had to compile the wireless drivers (which need to be re-compiled after a kernel update), but with NBR it worked straight out of the box as the driver is included, everything else works great.

I can recommend UNR.

---

