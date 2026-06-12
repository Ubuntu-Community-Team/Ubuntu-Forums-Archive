---
title: "Hang on boot that doesn't tell me much"
date: 2021-09-01
forum: Server Platforms
---

### Post by nondisclosure on 2021-09-01
So I've been running ubuntu server edition for a couple of years now and today I upgraded my hardware, everything but the hard disks changed. My processor still remains an AM4 socket and the motherboard is just an identical but upgraded version of the old one. Now, for some reason I can't boot, and it doesn't tell me much. I get this output:

[https://imgur.com/a/q3lVNq8](https://imgur.com/a/q3lVNq8)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289096&stc=1[/IMG]
The strange thing is that if I go into recovery mode via the GRUB menu and then just click "resume", everything works as expected. It's only when I let it auto-select or click the default GRUB menu option that this happens, so I have no idea what to do and any/all help would be greatly appreciated.

Also I have never installed nouveau and it is not found when I drop in to a root shell to try and remove it, so idk why it says it here, unless it means something different.

P.s. apologies for the bad picture, had to use my phone to snap a pic of the screen.

Update: in the time it took me to write this post and upload a pic, the machine eventually booted. It still hangs on this output at every boot, though :(

---

### Post by Bashing-om on 2021-09-01
nondisclosure; Hummm ...

does the kernel see the hardware:
```

lspci -k | grep -iEA5 'vga|3d'

```

Are we indeed working with the nouveau driver:
```

dpkg -l | grep -i nouveau

```

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by mastablasta on 2021-09-02
do you have nvidia card ? nouveau is driver for nvidia GPU. it could be on motherboard.

---

### Post by nondisclosure on 2021-09-05
No, I had an AMD card and no integrated graphics. Googling for hours showed me that a bunch of people had similar problems with the Ryzen 7 5800x and Ubuntu Server 20.04, so I returned the chip/mobo and just went back to intel, problem is now solved =)

---

### Post by Bashing-om on 2021-09-05
nondisclosure; Well !

That is one solution :D

As this is now at an end >>
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

