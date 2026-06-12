---
title: "Virtualbox 3.0.10 update: DO NOT INSTALL"
date: 2009-10-29
forum: Virtualisation
---

### Post by niteshifter on 2009-10-29
An update for the PUEL version of Virtualbox is available as an update. Version of this update: 3.0.10

DO NOT INSTALL THIS UPDATE

It kills your VMs. They will start booting then crash and present an Vbox error dialog.

See this [thread in the virtualbox forums]("http://forums.virtualbox.org/viewtopic.php?f=7&t=23898").



If you did install and every VM you have is not working:

Remove 3.0.10 via Synaptic - Mark for removal, then click Apply. DO NOT mark for complete removal, you'll lose your VMs.

Download the previous version (3.0.8) .deb file from virtualbox.org [Linux downloads link]("http://www.virtualbox.org/wiki/Linux_Downloads").

Install the 3.0.8 .deb via GDebi or dpkg.

Log out and log back in.

Your VMs should now work.


Consider locking your current version in Synaptic Package Manager.

---

### Post by joewski on 2009-10-29
This explains my problem with Virtualbox. I just upgraded from jaunty to Karmic and am experiencing the same issues.

Yes I just did a downgrade to 3.0.8 and my VM's now all work again.

---

### Post by Findarato on 2009-10-29
I am having no problems here... and I did just install the new VB.

---

### Post by b00ka on 2009-10-29
Well, that explains my issues also.  Updated this arfternoon and my XP VM's crashed on boot.  Will revert to earlier version now - thanx

---

### Post by HotShotDJ on 2009-10-29
Good catch.  Fortunately, I was sleeping when this new update hit the Sun repository, so I missed it.  They must have pulled it, because Update Manager does not offer me any upgrades this morning and 3.0.10 is not found on VirtualBox.org.

---

### Post by ianc on 2009-10-29
Rather than uninstalling & then manually downloading 3.0.8 from the Virtualbox site you could try downgrading in Synaptic.

Select Virtualbox per #1 above but rather than remove it do (menu) <Package> - <Force Version> to 3.0.8.

You can then lock the version as suggested until a clean release is available.

It worked for me anyway...

---

