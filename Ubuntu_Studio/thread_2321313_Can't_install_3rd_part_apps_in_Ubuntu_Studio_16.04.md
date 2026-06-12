---
title: "Can't install 3rd part apps in Ubuntu Studio 16.04 Xenial Xerus LTS"
date: 2016-04-21
forum: Ubuntu Studio
---

### Post by likapaul on 2016-04-21
It returns "non-free" , and then stop installing.
How to solve this problem ?

---

### Post by Bucky Ball on 2016-04-22
Welcome. With that little info there's not a lot to say. What says 'non-free' and what release/flavour of Ubuntu are you using?

You need the 'Canonical Partners' repository enabled perhaps? Again, just guessing at this point ... :-k

You might like to check the pink link in my signature for future reference. ;)

---

### Post by likapaul on 2016-04-22
I download the GrandOrgue, vrtual pipe organ software, deb. while I double click the file, it goes to the page for software installation. There's two block showing {non-free}{3rd party}. Underline is this: {This software comes from a 3rd party and may contain non-free components}. While I click the Install button, it installs a bit and then stop. It is the same situation for LinuxSampler's deb, etc...downloaded from kxstudio. It didn't happen in previous versions of Unbuntu Studio. This version of Unbuntu Studio just launch yesterday, so, not much people had come to this problem yet.

---

### Post by shaun57661 on 2016-04-23
I'm having the same issue, but now the Software App is just showing a spinning wheel when I try to install Ubuntu Tweak. Also, the damn Software app is not updating at all, even to show a single app in the repository. I cannot search for bleachbit, synaptic, nothing. It just goes blank with a spinning wheel that goes on forever every time i try to search for an app. Also, when browsing, there is no refreshing of the app. It just stays blank. It's absolutely useless, and without Synaptic in this new version, I'm really pissed.

---

### Post by kc1di on 2016-04-23
Try installing Gdebi and try through that instead.  If there is a dependency problem it will reveal it .
you can install gdebi by typing in a terminal
```
sudo apt-get install gdebi
```

Also this thread is similar 
[http://ubuntuforums.org/showthread.php?t=2321483&p=13475017#post13475017]("http://ubuntuforums.org/showthread.php?t=2321483&p=13475017#post13475017")

---

### Post by shaun57661 on 2016-04-23
Had to reboot. Software App running properly now. Was able to d/l Synaptic.

---

### Post by shaun57661 on 2016-04-23
OMG, this new 16.04 OS is HORRIBLE. The Software app is now showing "No Application Data Found". A moment ago prior to that, I had tried to install Chromium from the Software app, and it just did nothing.

I'm going to wipe my drive and reinstall 14.04 LTS and wait 6 months before upgrading to 16.04. Hopefully all the bugs will be worked out by then. This new upgrade is a FAIL.

---

### Post by Manny_Aeneas on 2016-04-24
I have this issue, too.

The best package installer is GDebi. 
Install it by running:

```
sudo apt-get install gdebi
```

After that, download .deb packages and install them by right-clicking the file and opening with GDebi Package Installer. 
I've never had any issues with GDebi.

And right now, it's the only option.

---

### Post by yoshii on 2016-04-25
If you need to do an offline install of a .DEB download, you can also do ...

$ dpkg -i theFile.deb

Or if there are a bunch of .DEB files, put them all into an empty folder, and then run the terminal from that folder:   

$ dpkg -i *.deb

This will install all of the .DEB archives in that folder at the same time, so that if they depend upon each other, it will possibly work out.

I also miss Synaptic Package Manager.  

I'm sticking with Ubuntu Studio v14.04.x LTS until more of the bugs get fixed.  16 is not real bad, but I need the whisker menu to work better and more AMD graphics support.

---

