---
title: "Installing Ubuntu via TTYA"
date: 2007-09-17
forum: Sun Sparc Users
---

### Post by megahurts on 2007-09-17
Hi,

I've got a (very) old Ultra One that up until recently was running GNU/Debian.  That is until I did a apt-upgrade and apparently bricked it,  no response to ping etc and unfortunately I don't have access to a sun monitor or keyboard (it was built with debian @ my old place of work when we were skipping a load of old kit and stupidly I never aquired the screen or keyboard...)

I'm ok with blowing Debian away and installing ubuntu as it was only a "spare" box, but now I've got a use for it.  

So my question,  is it possible to install Ubuntu without have a screen or keyboard attatched?  I'd rather spend a few quid on a nullmodem cable than have to trawl ebay for a screen n keyboard....

---

### Post by netztier on 2007-09-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/59889](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/59889) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **megahurts said:**
> So my question,  is it possible to install Ubuntu without have a screen or keyboard attatched?  I'd rather spend a few quid on a nullmodem cable than have to trawl ebay for a screen n keyboard....

Should be possible - I think I tried some of it once with my Ultras. But setup assumes that you *do have* a keyboard connected (see Launchpad Bug URL above), so you'll probably have to configure one - regardless if it is there or not.

If I remember correctly, some dialog boxes of the installer showed some strange reactions, depending on the terminal emulation you select - it might take some fiddling with the settings to get this right.

Using the alternate installation CD, you should be certain that you get a full text-mode-only instakller: 
[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

best regards

Marc

---

