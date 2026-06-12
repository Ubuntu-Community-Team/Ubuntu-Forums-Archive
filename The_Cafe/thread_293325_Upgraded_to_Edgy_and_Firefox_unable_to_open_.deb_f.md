---
title: "Upgraded to Edgy and Firefox unable to open .deb files with gdebi-gtk"
date: 2006-11-05
forum: The Cafe
---

### Post by dernwine on 2006-11-05
Going nutz trying to figure out this problem. In 6.06 Firefox v1.5x would ask to open .deb files with gdebi-gtk. Edgy has Firefox v2.0 and never prompts to install.deb files when you click on a .deb download link.

Application gdebi-gtk is installed in the same place in both 6.06 and 6.10,
/usr/bin/gdebi-gtk.

It's not in the "View and Edit options" of the Firefox "Download" tab.

Any ideas?


TIA,
David

---

### Post by JustinClift on 2008-04-22
Hi, did you solve this?

I'm having the same thing with Firefox 2.x on Hardy Heron.

Have already used it once to install a package (Salasaga), then came back later after rebooting the system (a virtual machine) and now... packages don't have the option to install with GDebi.. just save to disk.

Even went back to the exact same Salasaga download on SourceForge and that also just "Save to disk" option.  :(

---

### Post by JustinClift on 2008-04-22
Hmmmm, am now suspecting it's something to do with the mime headers (content type) being sent by the web server.

Different SourceForge mirrors are sending different mime header content type info for the exact same file.

This one from Internap works fine, GDebi is presented, etc:

[http://internap.dl.sourceforge.net/sourceforge/salasaga/ubuntu_8.04-salasaga_0.8.0.alpha1-0ubuntu1_i386.deb](http://internap.dl.sourceforge.net/sourceforge/salasaga/ubuntu_8.04-salasaga_0.8.0.alpha1-0ubuntu1_i386.deb)

Content type sent by the Internap web server is "Content-Type: text/plain".

This one from Switch (exact same file) only gives the "Save a file" option:

[http://switch.dl.sourceforge.net/sourceforge/salasaga/ubuntu_8.04-salasaga_0.8.0.alpha1-0ubuntu1_i386.deb](http://switch.dl.sourceforge.net/sourceforge/salasaga/ubuntu_8.04-salasaga_0.8.0.alpha1-0ubuntu1_i386.deb)

Content type sent by the Switch web server is "Content-Type: application/octet-stream".

How strange.

---

### Post by Lostincyberspace on 2008-04-22
hey if is that old and unanswered then leave it be please.

---

