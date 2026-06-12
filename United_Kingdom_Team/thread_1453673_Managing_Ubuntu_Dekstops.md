---
title: "Managing Ubuntu Dekstops"
date: 2010-04-13
forum: United Kingdom Team
---

### Post by monkeyx.net on 2010-04-13
I am looking at implementing a project at work to install and manage Ubuntu desktops running the latest 10.04 LTS version(when it is released) on 110 Pentium 4 machines. The latest Beta version starts up in 30 seconds (even on old hardware Smile ). These machines were destined for computer heaven until we rescued them, so we have done our bit for the environment Smile

We currently run and support half a dozen Ubuntu servers at work so we are not total noobs Smile I have also used Ubuntu as my primary desktop on my laptop for around 5 years now.

The machines will run Gnome, OpenOffice, Firefox, Scribus and GIMP.

Some ideas on how we are thinking of managing and/or implementing the project.

Initital base build Clonezilla/FOG/ One supplier mentioned using Debian installer. Would appear d-i gives more control over hardware and software packages. Does d-i work with latest version of Ubuntu is there a Ubuntu spefic version of preseed etc?

Managing the desktop shortcuts, security, configuration and remote application installation. Some examples of how we want to configure the system are that we want add a wow factor by ensuring compiz is enabled for each user profile, integration with ActiveDirectory, provide consistent set of applications short cuts etc, lockdown security via gconf etc. Does ubuntu/gnome have a specfic management tool. Or would looking at cfengine/puppy be better?

Maybe there is something we are missing and there are other tools out there ?

Also consider commercial assistance to help implement this solution. I have already asked for commercial quote from a UK company.

All the best,

Tim

---

### Post by dwarfolo on 2010-04-13
Have you aldready taken in consideration LTSP as a possible solution?

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by monkeyx.net on 2010-04-13
I have looked at LTSP, and to do it properly we would need at least one well specced server(Ideally 2). Which we do not really have the budget for. The PCs are fast enough to run and process the workload required from them, so we may as well put the local machine to good use. We do have some much older hardware that could benefit from LTSP though, so hope to also do a project that uses LTSP at some point. Does 10.04 have spcefic improvements for LTSP version that may help with memory requirements?

Thanks,

Tim

PS anyone using likewise for managing Ubuntu ?

---

