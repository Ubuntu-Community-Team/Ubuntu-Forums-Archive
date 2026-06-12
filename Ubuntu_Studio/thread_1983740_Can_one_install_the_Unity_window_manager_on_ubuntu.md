---
title: "Can one install the Unity window manager on ubuntustudio??"
date: 2012-05-20
forum: Ubuntu Studio
---

### Post by n3mmr on 2012-05-20
I'm running Ubuntustudio 12.04 and I'm largely happy with it, but for various reasons i'd like to try the Unity shell, too.

How does one go about adding the Unity shell/lenses/scopes as an alternative w/o taking the ubuntu studio default wm and xfce choices away?

For some reason, whenever I try adding the Unity shell, things just stop working.

What is the proper way to add the unity shell environment w/o affecting the default shells of ubuntu studio?

---

### Post by jejeman on 2012-05-20
I don't think that is posible. Unity needs gnome, compiz.
If you need Unity, install Ubuntu, and than install (audio) programs that you need.

---

### Post by n3mmr on 2012-05-21
> **jejeman said:**
> I don't think that is posible. Unity needs gnome, compiz.
If you need Unity, install Ubuntu, and than install (audio) programs that you need.

Then it should be possible to do it by installing unity + ..... + compiz + gnome.

And what else??

I failed miserably installing the audio/video stuff on ubuntu standard 12.04.
All the advice I found was for older versions, and invariably lots of other stuff was missing.

I don't NEED unity, it would be nice, and if it works, I could forego installing a third OS on the same machine.

---

### Post by irv on 2012-05-22
> **n3mmr said:**
> Then it should be possible to do it by installing unity + ..... + compiz + gnome.

And what else??

I failed miserably installing the audio/video stuff on ubuntu standard 12.04.
All the advice I found was for older versions, and invariably lots of other stuff was missing.

I don't NEED unity, it would be nice, and if it works, I could forego installing a third OS on the same machine.

I wanted the best of both worlds, so I cleaned up some old OS' off my hard drive and Installed Ubuntu Studio 12.04 on it's own partition, and have Ubuntu 12.04 w/Unity on it's own partition. So now I have the best of both worlds. This works for me. Glad we have so many ways of doing things.
Here is a shot of my Hard Drives in gparted.
[ATTACH]218476[/ATTACH]
sda2 is Windows 7
sda5 is Ubuntu Studio 12.04
sda7 is Ubuntu 12.04 w/Unity.

---

### Post by n3mmr on 2012-05-22
> **irv said:**
> I wanted the best of both worlds, so I cleaned up some old OS' off my hard drive and Installed Ubuntu Studio 12.04 on it's own partition, and have Ubuntu 12.04 w/Unity on it's own partition. So now I have the best of both worlds. This works for me. Glad we have so many ways of doing things.
Here is a shot of my Hard Drives in gparted.
[ATTACH]218476[/ATTACH]
sda2 is Windows 7
sda5 is Ubuntu Studio 12.04
sda7 is Ubuntu 12.04 w/Unity.

I'd rather avoid that: I want to use Unity when doing media work, and that's what I'm looking to do, here.
I would have to duplicata about a 3rd or more of the tools in both environments.

---

### Post by n3mmr on 2012-05-22
> **n3mmr said:**
> I'm running Ubuntustudio 12.04 and I'm largely happy with it, but for various reasons i'd like to try the Unity shell, too.

How does one go about adding the Unity shell/lenses/scopes as an alternative w/o taking the ubuntu studio default wm and xfce choices away?

For some reason, whenever I try adding the Unity shell, things just stop working.

What is the proper way to add the unity shell environment w/o affecting the default shells of ubuntu studio?

I tried this, that I found in UbuntuStudioPreparation:
sudo apt-get uninstall ubuntustudio-lightdm-theme && sudo apt-get install unity unity-2D unity-greeter gnome-session ubuntu-artwork

It lost me my keyboard, when tried in 12.04, or at least it seemed so.
Should this be a good way, and why must one uninstall the ubuntustudio-lightdm-theme???

---

