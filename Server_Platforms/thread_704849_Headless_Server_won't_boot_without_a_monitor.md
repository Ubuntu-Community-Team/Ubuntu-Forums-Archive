---
title: "Headless Server won't boot without a monitor"
date: 2008-02-22
forum: Server Platforms
---

### Post by acreman on 2008-02-22
I have a headless LAMP server that refuses to boot without a monitor being plugged into it.  I have checked the BIOS and don't see anything in there for detecting a monitor and failing if one is not present.  I have also checked the /etc/init.d and xserver isn't in there (a good thing).

Any suggestions on where this might be found in the forums or how to fix this?  The only way I want to log into this machine is via command-line and SSH (which works once the machine is actually at the login prompt.)

William

---

### Post by jflaker on 2008-02-22
Have you tried disabling the video?  Since there is no monitor, no need to keep it active, may be the solution too.

---

### Post by acreman on 2008-02-22
> **jflaker said:**
> Have you tried disabling the video?  Since there is no monitor, no need to keep it active, may be the solution too.

How would I go about doing that?  Would it be in /etc/init.d anywhere?

---

### Post by faulkes on 2008-02-22
> **acreman said:**
> How would I go about doing that?  Would it be in /etc/init.d anywhere?

If the server has an onboard video card (which most 1u/2u type servers do) then you 
can go into the bios, there should be an option to disable the onboard video.

[B]I however wouldn't suggest that because if you don't have another video card installed, 
you'd pretty much never be able to get back into the server via a monitor again.
[/B]
Instead, I would suggest you check the bios's POST check settings.  These usually amount
to several options such as "quick, minimal, full".  Setting it to quick or minimal would 
probably be the best option.

Faulkes

---

### Post by acreman on 2008-02-22
> **faulkes said:**
> If the server has an onboard video card (which most 1u/2u type servers do) then you 
can go into the bios, there should be an option to disable the onboard video.

[B]I however wouldn't suggest that because if you don't have another video card installed, 
you'd pretty much never be able to get back into the server via a monitor again.
[/B]
Instead, I would suggest you check the bios's POST check settings.  These usually amount
to several options such as "quick, minimal, full".  Setting it to quick or minimal would 
probably be the best option.

Faulkes

Unfortunately it isn't a 1u/2u rack mounted server.  This used to be an old desktop PC that I've turned into a CLI only server.  It is intended for home use only.  The BIOS is already set for a quick boot.  The OS is hanging somewhere before the network interface comes up so I know now that this isn't something found in the /etc/init.d directory but something to do with a configuration file or kernel setting.

---

### Post by faulkes on 2008-02-22
> **acreman said:**
> Unfortunately it isn't a 1u/2u rack mounted server.  This used to be an old desktop PC that I've turned into a CLI only server.  It is intended for home use only.  The BIOS is already set for a quick boot.  The OS is hanging somewhere before the network interface comes up so I know now that this isn't something found in the /etc/init.d directory but something to do with a configuration file or kernel setting.

IIRC, if you hit ESC (or was it alt-f1) as it boots at the splash screen you 
should be able to see the last point at which the kernel has executed 
something.

That should give you an indication of what exactly the problem is.

Faulkes

---

