---
title: "Dropbox off the Synaptic install failure with Ubuntu Gnome 13.04 daily"
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by FiremanEd on 2013-04-13
Seems that the Dropbox option to install Synaptic seems to hang upon install.  It downloads the dropbox app in terminal and just hangs.  I found going to the dropbox website and following the script seems to be the ticket.

Ed

BUT..

Install Dropbox via command line, ref: [https://www.dropbox.com/install](https://www.dropbox.com/install)

The Dropbox daemon works fine on all 32-bit and 64-bit Linux servers. To install, run the following command in your Linux terminal.

32-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -

64-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -

Next, run the Dropbox daemon from the newly created .dropbox-dist folder.

~/.dropbox-dist/dropboxd

Gold.

---

### Post by cariboo on 2013-04-13
I know you marked this solved, but did you figure out why installing using synaptic fails?

---

### Post by FiremanEd on 2013-04-13
Seems to stall at downloading dropbox usually at 100%.  At that point everything locks up without resolution and installation.

---

