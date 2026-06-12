---
title: "Installing Software Package from Flash Drive"
date: 2007-11-16
forum: Repositories &amp; Backports
---

### Post by Michl on 2007-11-16
I want to install a debian package from a flashdrive because
I don§t want to get onto the internet.  My windows
partion had some bots and I just want to make sure they're 
gone via ubuntu as well before I connect.  So I
downloaded all the packages on another machine  to a flashdrive, get
Debiinstaller or whatever it is called to install
it (after the warning) and then it starts to download
and nothing happens.

Michl

---

### Post by timcredible on 2007-11-16
to install a .deb file, just double-click on it, it'll bring up the installer.  if it says there's a dependency, you have to install that first.  but, there's no reason not to get on the internet, the bots and viruses are on your windows software, not your ubuntu software.  so, just get on the internet and use synaptic to install packages.

---

### Post by Michl on 2007-11-16
I guess that's true.  Still, when I double click and use the
GDebi installer, it sits there downloading and then it says
I should check my internet connection.  But I downloaded
it from the ubuntu site and the download has all
the files.

---

### Post by IanW on 2007-11-17
What is happening to you is that sometimes, the file you want to install needs  something else present for it to work, and asks the installer for the other files.

This is where your install is hanging.

You need to search for the package you are trying to install at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and also download ALL files marked with a red circle.
The file you originally wanted to install won't work without those files.
The bad news is that each of those "dependencies" may have dependencies of their own, so you'd have to do the above again for each one!
This is why having a net connection is helpful, because the package installer (GDebi / Synaptic / apt-get / aptitude) takes care of all this for you.

---

