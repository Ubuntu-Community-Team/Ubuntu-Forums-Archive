---
title: "Scroll stutter browsers fullscreen Ubuntu 20.04.3 LTS VMWare"
date: 2021-12-23
forum: Virtualisation
---

### Post by antonwas1 on 2021-12-23
Hello everyone,

I'm encountering a strange problem in Ubuntu 20.0.4. When I have a browser open in full screen mode (doesn't matter which one: Google Chrome, Firefox or Edge) the scrollbar is heavily stuttering.
Every so many lines the scroll bar stops for around 1-1.5 seconds and then continues. For clarity: this is only when taking the scrollbar with the mouse and dragging it. Using the scroll wheel the problem isn't recognizable.

When I make the browser window a little bit smaller (nearly full screen) the problem doesn't appear. Other programs of Ubuntu doesn't suffer this problem, e.g. text over multiple pages in LibreOffice.

I am running Ubuntu in a VMWare Workstation Pro 16 VM with the specs below:

4 GB RAM
1 fysical CPU with 8 cores
SSD 60 GB

Of course I installed the most recent version of open vm tools in the VM.

The specs of the host machine (laptop) are:

Intel i7-4700MQ CPU @ 2.40GHz, 2401 MHz, 4 core('s), 8 logical processors
8 GB RAM
GPU: Intel HD Graphics 4600 (1GB VRAM) and NVIDIA GeForce GT 740M (2GB VRAM)

When I run Ubuntu in the tryout mode (without installing) directly on the hosts' hardware the problem above doesn't appear.
So I assume that the problem lays somewhere in the virtualization software and not in Ubuntu, nor the browser. However I have no idea where to look.

On another, more powerful host machine the exact same situation as above occurs.
Does someone have an explanation for this problem? Could not find a 'real' solution for it.

Thanks in advance for all reactions!!

---

### Post by MAFoElffen on 2021-12-28
What is your graphics and video setting of the VM Guest Machine?

What is the Desktop Environment (DE) of the Guest?

---

### Post by antonwas1 on 2022-01-06
See te settings below for the video settings for the VM:

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=289747&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289748&stc=1[/IMG]

Desktop environment: GNOME

---

### Post by MAFoElffen on 2022-01-06
Just an initial observation, and I've not used VMware Workstation for years, so I am going off old experience with this...

You didn't mention what OS the host system is, and what resolution and the aspect ratio of the host system...

I see to things... In what you previously said, you have 8GB RAM on your host, 4GB assigned to your VM Guest... But in your VM Guest Settings for Display > Graphics Memory, you 8GB assigned to video... That number is greater than what would be physically possibly available, right? What happens if your lower that number? For example, if you lower the VM RAM assigned to GB and the Graphics Memory to 2GB.

The other thoughts I have was if you test changing the Display Scaling from 'Keep Aspect Ratio" to "Stretch". The reason I say that is you said if it is just under "full-screen" mode versus an actual full-screen mode... That there may be a difference in translation of that aspect ratio and the host's resolution and aspect ratio settings, in trying to keep "that". a

Another idea might be to keep that setting as "keep aspect ratio", but to lower the setting above that, for the max resolution of one monitor... To match that resolution and aspect ration to what it is being viewed on. It is possible to config a resolution that is more than what it is being viewed on... It just is not a smart thing to do, and is a pain to view.

---

