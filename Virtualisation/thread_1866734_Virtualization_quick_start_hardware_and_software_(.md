---
title: "Virtualization quick start hardware and software (Windows under Ubuntu)"
date: 2011-10-21
forum: Virtualisation
---

### Post by 5circles on 2011-10-21
My apologies if there are some standard places to find answers to my questions. With a couple of closed sticky threads that don't seem to help and 402 pages of threads I'm overwhelmed, and don't even know the right questions to ask.

Background: My Ubuntu box is a couple of years old, and doesn't have hardware virtualization (E2200 CPU). It's reliable for my internal webserver, but I don't know how long it will go on. My backup desktop box running Windows XP is a little older, and died a while back.  I've been having problems with my main laptop (Win7) and needed to move to a temporary desktop.  Now I'm considering options.

What I think I'd like is a reliable Ubuntu box that's capable of hardware virtualization.  I'd run Ubuntu all the time as the host OS, and run Windows virtually (probably Win7).  The Windows environment would be used to run occasional programs that make more sense to leave in the office - perhaps even older programs that run under XP, so I might want that too.  But when I have issues with the laptop, or maybe want more horsepower, I would want to run Office 2010, and other complex programs.

What should I be looking for in hardware?  I'm guessing I7 for future proofing, with lots of memory (how much), and good size hard drive.  I don't need screaming video, but does virtualization place higher demands?

I'm more confused about virtualization software, and don't really know where to start.  Help!

As for Windows, how does that work? I have a full copy of XP that should install, but what about Windows 7?  If I bought a machine with Windows7 installed, would I be able to install that inside the virtual environment?  (I'm guessing not).  Is there any benefit to the Professional edition over Home Premium when running under Ubuntu?  And what about using an upgrade version rather than the full copy?

Thanks for any ideas (and for hopefully being tolerant of my ignorance)
Mike

---

### Post by 2F4U on 2011-10-22
Virtualization is covered in the server documentation:

[https://help.ubuntu.com/11.10/serverguide/C/virtualization.html](https://help.ubuntu.com/11.10/serverguide/C/virtualization.html)

Another popular solution is VirtualBox:

[https://www.virtualbox.org/](https://www.virtualbox.org/)

You need a license to install Windows inside any virtualization solution and it usually requires install media, so most likely you will need a full version and can't get away with an upgrade version. As far as I know, there are solutions to convert an existing installation into a virtual machine, but I haven't done this.

---

### Post by 5circles on 2011-10-22
Thanks for the kickstart.  I've been experimenting with VirtualBox on my old box to get an idea of what I'll need in a new server

---

