---
title: "Detection, auto-detection and manual settings"
date: 2004-12-08
forum: The Cafe
---

### Post by Sorin Paliga on 2004-12-08
If allowed, a comment on the existing problems in Ubuntu (intel, mainly, but the ppc version also used):
1. Hardware/periphereal detection. This is a major problem with many distros, Ubuntu included, though not critical (as in other cases, especially when the monitor does not display anything usable). Mouse non-detection (incorrect port) and monitor bad resolution (even though non-critical) are the most frequent. Also, less important, printer auto-detection . Mouse being 'dead' is quite frequent, even with 'great' distros like SuSE, just that there is the immediate possibility to set (and test) it upon installation. Monitor incorrect settings (with the ultimate situation to being unusable) is also frequent. CONCLUSION: forthcoming Ubuntu should have the possibility to make manual settings and tests during the last stage of installation, before launching X. (Thanks to those who illuminated me in this forum, other section, on how to manually set mouse port).
As often with Gnome, the floppy unit is not detected ( have not solved this, perhaps tomorrow).
2. Network problems. I have not yet discovered how I share my printer (there is an iMac aside the intel pc), how I share a folder, and how I can easily connect to my neighbouring iMac (other windows-based pc's are OK, but samba should be indeed installed by default, not addable after the basic installation). Adding the apple talk protocol via apt-get would not be a bad idea (if there is hfs and hfs+, among others, this one should be too). Note: in fact I know how to share iMac from within iMac by adding a small utility, but this is another story.
3. Font installation. There should be a simple and friendly way to add fonts. Yes, I know, there is the .font folder method (this works in Fedora, have not tested yet in Ubuntu) or asking Nautilus to detect 'fonts'. There should be something more obvious than these possibilities.
4. Gnome dependency. I have no particular bias for either KDE or Gnome, but I have just noted that KDE has lately moved quite far ahead, while Gnome has become a little bit retarded. None of them has got the Aqua height, yet currentKDE is - by far - much better done than current Gnome. Sorry to say this, do not wish to hurt anyone.


Conclusion, at last: the Hedgehog should have a simpler way to handle all these, including manual settings and testing if mouse, monitor etc. really work. Curious enough, the live cd detects hardware better than the installed version. Knoppix influence?

---

### Post by TravisNewman on 2004-12-08
1. The installation is made to be as easy as possible, and require the least amount of user interaction that they can. This would be a good option to add to the expert installation though.

2. Should samba be installed by default? How many people really need to share across a network? I'm personally the only person I know who does. Everyone has their ideas of what "should" be included in Ubuntu by default, and if everyone was satisfied, it would be a 3 or 4 cd distribution like Fedora or SuSE. They are committed to a 1 cd distro.

3. This is a Linux suggestion and not an Ubuntu suggestion it seems. But it's about as easy as figuring out how to do it in Windows.

4. And I think the opposite. I think KDE used to be the best thing ever back in it's 2.x days, but I think it keeps getting worse and worse, and Gnome keeps getting better and better. Fact of the matter is, Ubuntu is a Gnome based distro. There are plenty of KDE based distros out there if you want KDE.

Edit: Also, I don't think this is in the right place, but I don't have power here, can a mod who has power here move this?

Edit again: when did I get power in this section *LOL*

---

### Post by adbak on 2004-12-08
1.  As far as printer detection is concerned, enable the Universe repos and install cupsys-gimpprint-driver.  After installation, get rid of any existing configuration you may have and cilck Add Printer.  Go through the steps.  If this still fails to set up your printer, try checking to see if you have the printer utility set to look in the right port (e.g. parallel, usb).

3.  Point Nautilus to "fonts:///" without the quotation marks.  I believe it's just drag-and-drop to add new fonts.  Also, try installing the package "msttcorefonts" which is a package containing a lot of fonts that Windows uses.

4.  Gnome is fine by me, but I'm sure there's room for improvements in both KDE and Gnome.

---

### Post by randy on 2004-12-08
1.  Installation should be kept extremely simple.  If X doesn't start correctly a manual configuration program should be launched.  

2. There's currently a new file sharing solution that is being worked on by Gnome.  I'm not sure of the specifics but I'm pretty sure that it involves a Web Dav server.  You'll be able to share things easily from nautilus and other operating systems will be able to connect to them as long as they support webdav.  This is much easier than samba and your not pulling in as big of a security risk.

3.  You've got me on the font thing, except for the Nautilus view that makes it easy to drag and drop fonts.

4.  Gnome is much more responsive and uses a lot less system resources than KDE so you don't need as beefy of a system to start running it.  It also has fewer configurable options than KDE so it's easier for most new users to start using.

---

