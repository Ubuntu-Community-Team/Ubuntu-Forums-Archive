---
title: "can I run ubuntu studio components without installing ubuntu studio?"
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by extendedping on 2009-10-31
I ask because I installed ubuntu studio 9.10 on a free pc the other day and was not crazy bout the first impressions on the desktop such as the wallpaper and the fact that open apps just "disappeared" (had to add something to the panel but common that should work off the bat). but I do want to try using ubuntu with the various recording softwares as opposed to upgrading my old cubase at quite an expense. so I now have the "regular" ubuntu installed (9.10) and want the real time kernel, jack and all applications that I heard about that a home recording studio might find helpful. I am sure I could search out apps and necessary stuff (the kernel the jack server etc) individually but I would love it if one of the ubuntu experts could point me to the necessary stuff. basically I guess you could say I want the studio edition without the studio desktop if that is possible. thank you in advance, and no disrespect to the studio edition which I am sure works great under the hood, I just really like the look/feel of the regular old ubuntu better...again thank you for any help. this ubuntu thing looks sweet, even my wife says it looks better then xp...

---

### Post by 73ckn797 on 2009-10-31
Yes you can.

Go to System/Administration/Synaptic Package Manager and look for "ununtustudio" packages. You can install audio, video and other studio packages without having to have the complete Studio OS. You will not have the real time kernel but any apps or other features are available.

---

### Post by candyiz4kidz on 2009-10-31
actually... if i remember correctly, you can install ubuntu 9.xx and then go into the package manager and select "ubuntu studio extra" or something like that. which sets up your low latency kernel settings (for producing music without lag), then you can install all the same programs from ubuntu studio using the same package manager. you'll need almost everything labeled "jack" with a few exceptions. I've done this once or twice on a couple of different computers. However, in my opinion Ubuntu Studio looks pretty awesome. Sure you might have to change the default wallpaper, but that only takes a few seconds. So, to sum up....


Go into the package manager, select and install "ubuntu studio extras" and ALMOST everything labeled "JACK", then find the audio production software that you want to use...

I recommend Ardour and LMMS. Ardour is kind of like cubase and LMMS is a lot like FL Studio.

---

### Post by candyiz4kidz on 2009-10-31
i feel like i should clarify. [73ckn797]("http://ubuntuforums.org/member.php?u=641480") is correct, you will not have a real time kernel, instead you will have your same old kernel, but it will be optimized as far as possible to get very low latency.

---

### Post by extendedping on 2009-10-31
thanks guys I searched using apt (first time) and found this...are these packages that I need? and is this what will be installed if I take the packages that have been mentioned? also of the ubuntustudio packages which ones would I leave out? remember I want the functionality without the look/desktop changing, and many of the packages under ubuntustudio seemed to be bout artwork, desktop, wallpaper, theme etc...

apt-cache search linux-rt
linux-image-2.6.31-9-rt - Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch
linux-rt-headers-2.6.31-9 - Header files related to Linux kernel version 2.6.31
linux-rt - Complete rt Linux kernel

---

### Post by 73ckn797 on 2009-10-31
> **extendedping said:**
> thanks guys I searched using apt (first time) and found this...are these packages that I need? and is this what will be installed if I take the packages that have been mentioned? also of the ubuntustudio packages which ones would I leave out? remember I want the functionality without the look/desktop changing, and many of the packages under ubuntustudio seemed to be bout artwork, desktop, wallpaper, theme etc...

apt-cache search linux-rt
linux-image-2.6.31-9-rt - Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch
linux-rt-headers-2.6.31-9 - Header files related to Linux kernel version 2.6.31
linux-rt - Complete rt Linux kernel

I assume you are not using Synaptic? You will easily see what is available and what will meet your desires. What you want can be accomplished without all the glitz that comes with the Studio full installation.

---

