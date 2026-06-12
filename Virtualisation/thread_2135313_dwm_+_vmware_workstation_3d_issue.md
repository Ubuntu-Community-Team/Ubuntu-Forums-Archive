---
title: "dwm + vmware workstation 3d issue"
date: 2013-04-13
forum: Virtualisation
---

### Post by moostapha on 2013-04-13
Greetings. 

New to the Ubuntu community and recently back on linux. Long term gentoo user before that. 

I have access to a site license of vmware workstation for work, as well as a few VMs I need to use from it. I've been using them on VMWare Fusion on my MBP without issues. However, with my new laptop (thinkpad x230, hd400 graphics) and ubuntu with dwm, I keep getting 3d acceleration issues on the VMs. They work, but it keeps complaining that it can't use graphics acceleration or 3d. 

I've been reading about it for a while, and I'm confused. I suppose I could always just install dwm on the guests as well, but the acceleration thing is really bugging me. 

Is this just an HD4000 graphics issue, or is there something else at work?

---

### Post by dcstar on 2013-04-18
Most VM platforms do not fully support 3D video, some do partial support depending on the underlying hardware. This is a known limitation of VM environments.

---

