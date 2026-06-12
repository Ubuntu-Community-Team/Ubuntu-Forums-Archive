---
title: "Ubuntu Upgrade from v12.10 to 13.10 - First Timer"
date: 2014-03-09
forum: System76 Support
---

### Post by Cliff Bentley on 2014-03-09
My year old System76 Ratel Performance is running Ubuntu v12.10 and I wish to upgrade to Saucy Salamander (v13.10). I'm an Ubuntu sys-admin newbie and this is my first shot at an Upgrade, so there is FUD. I'd like to keep this simple and low-risk (KISS).
 

 I have a good back up of ~/Documents/allMyStuff on a flash drive. Since this is a 3 version jump, I was told I should load from a CD instead of from Software Updater. My book, &#8220;Ubuntu Unleashed, 2014 Edition&#8221;, came with a CD containing Ubuntu v13.10. If I must upgrade Ubuntu from CD, I'd like to upgrade from that.
 

 1) Is it indeed best to re-load Ubuntu from CD because this is a 3 version upgrade?

 2) If the answer to #1 is &#8220;yes&#8221;, how do I update Ubuntu from my CD? I keep reading about &#8220;the iso file&#8221;, but I don't see an *.iso file on the CD. I see dirs named, &#8220;isolinux&#8221;, &#8220;install&#8221;, et al. There is also a file named &#8220;wubi.exe&#8221;. When I put the CD in the drive a message box comes up and says:
 > Software Packages Volume Detected
 A volume with software packages has been detected. Would you like to open it with the package manager?

 3) &#8220;Ubuntu Unleashed&#8221; seems to say this install will re-write the entire hard disk and that it will require me to add myself as a new user at install. This sounds bad! Is there a way to upgrade Ubuntu from CD without blowing away my own user account and the privileges I set up via chmod? Or, will the install program allow me to re-load the OS while sustaining me as the user? I can re-load my data from my back up but don't want to lose all my permissions.

---

### Post by Jhongy on 2014-03-10
I've never had a problem using the upgrader. The CD isn't a more canonical source than canonical(!)s repositories.

Just upgrade using the software-updater. Just pay attention to any packages that require reconfiguration as part of the upgrade.

---

### Post by mörgæs on 2014-03-10
> **Cliff Bentley said:**
> I don't see an *.iso file on the CD. I see dirs named, “isolinux”, “install”, et al. There is also a file named “wubi.exe”.

What you have is the contents of the ISO file on the CD, as it should be. The ISO file is only a packaged archive which is used for creating a CD/USB stick with the installation files.

I wouldn't recommend an upgrade which goes through an unsupported release like 13.04. Fresh install of 13.10.

---

