---
title: "Cannot install Latest Tbird/Firefox on Ubuntu 10.04 due to tar.xz in .DEB"
date: 2014-09-22
forum: Ubuntuzilla
---

### Post by dalmolin on 2014-09-22
Hello,

I am unable to install the latest couple of versions because the version of .dpkg on Ubuntu 10.04 LTS does not support unzipping tar.xz .  Is there a work around or is there no option but to upgrade my version of Ubuntu :-( (unfortunately there would be lots of work involved to do this).

Thanks!!

---

### Post by slickymaster on 2014-09-22
We highly recommend you upgrade to a supported release.
Upgrade to 12.04: [https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS")
Install 14.04: [https://help.ubuntu.com/14.04/instal...ide/index.html]("https://help.ubuntu.com/14.04/installation-guide/index.html")

For old computers with lower specifications, you may:
[LIST]
[*]Read this link: [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
[*]Try Lubuntu or Xubuntu 14.04 LTS (supported until April 2017)
[*]Try Xubuntu 12.04 LTS (supported until April 2015)
[*]Alternative to Unity on 12.04 LTS: [Gnome Classic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")
[/LIST]

We will not provide any additional support to EOL releases, and in particular to the 10.04 desktop edition.

---

### Post by nanotube on 2014-09-26
Hi dalmolin,

slickymaster is right, ubuntu lucid is no longer supported on the desktop, and you should upgrade to a supported release. I highly recommend xubuntu, myself :)

However, since i have received several inquiries about this, i have changed the compression format in the ubuntuzilla repository to gzip, and it should now work for you on lucid.

Cheers,
nanotube

---

