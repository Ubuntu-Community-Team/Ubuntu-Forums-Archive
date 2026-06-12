---
title: "W00t doggies"
date: 2008-04-24
forum: Testimonials &amp; Experiences
---

### Post by imbjr on 2008-04-24
Ahem. This is an account of my first taste of heron ...

First of all, I banged together a script to occasionally poll for the torrent file of the ISO and then have deluge download it. Just before midday (UK time), the file was found and by the time I got home from work, a new ISO was waiting for me. Someone at work suggested I should had the script email me too!

I give the ISO a quick tickle under VirtualBox and everything checked out nice - no checksum problems. So I installed the ISO on my USB stick, to save on CDROMs and fired it all up.

There was some trouble with Gnome daemon settings (if I recall the dialog correctly), but considering this was a LiveCD environment I didn't worry too much. However, far more importantly, the screen resolution was correct and I did not have to correct my xorg.conf like I had to do everytime I booted up the Gutsy disk.

One thing about the LiveCD: I was hoping to see if Compiz was going to work straight off, but it did not and I seemed to have problems following on-line advice - I couldn't install the XGL server; it wasn't in the respositories(!?). However, again, I surmised this was the LiveCD environment and so was not truly representative of running the distro.

Firefox ran nicely. I was slightly taken aback by the new feature of it remembering at restart what page one was on when the session was closed. I think I will turn that off.

The fonts look good. I'm not sure if anything has changed in this respect, but under Gutsy I had fiddle with the fonts to get them extra crispy.

So I decided to install. I had set aside a little bit of HD for the installation, so if this was going to be a big mistake, I could still very easily fall back on teh Gut. I don't intend to upgrade, I intend to clean install since I'm not convinced upgrade will work; the system is surely too flexible and I can't imagine the upgrade scripts being able to cope with every possible tweak one may have made.

A combination of using a USB stick and the smallness of the partition meant that the installation was very quick. Two things of note: 1) selection of the time zone when I ran the ISO under VirtualBox was very tricky due to overscrolling, but fortunately there was an alternative way to make the selection; 2) the partition editor made it much clearer what would have happened if I had chosen the guided re-partitioning - that was good, but as I said, I already had a place to decant the install.

So back to the question of the display and Compiz. Again, off the bat screen resolution was correct - though the refresh rate was slightly off, but easily corrected. This is the first time EVAR that the display was configured at the right resolution. 

Again, screen effects did not work straight off. I tried the XGL server again and included the Compiz settings editor. Voila ... it worked. However, everything was laggy. Dragging a window about felt like stirring toffee. I then realised I had gone off in the wrong direction.

I took XGL off and installed the restricted ATI (ack! I know) driver. BINGO. This time effects worked without lag, though I must admit some of the transitions do seem a little more hesitant than they were in Gutsy. I note that whilst in LiveCD mode the restricted driver was not available, but since installing it would have required a reboot, it would have been pointless to include (though Gutsy does).

I begain testing my attached devices. I attached the USB stick and it automounted. Recently, I decided I did not care for automount so I went to switch it off. However, the option to do so was now gone from the removable media widget. Google then revealed that gconf-editor would allow one to access a Nautilus setting ... hahaha. I just looked at Nautilus' settings dialog and saw a new tab. Bugger. I did not need to gconf after all!

Next I attached the laser printer. It's HP, chosen because historically Linux and HP have had a good relationship. Sure enough it just worked. I will need to test if colour-to-greyscale has been improved, but even if not, that's not what the printer's really for.

I then powered up the Epson scanner. Oddly, xsane kept insisting on selecting my TV card as input device. Under Gutsy it would give me a choice of the card or the scanner. But this time  - not. I was in the middle of installing some CLI software to query the scanner devices to determine their device names when I realised ... I had not attached the scanner's USB to the PC. ACK ACK ACK!

I tested the Wacom tablet. under Gutsy I had to tweak xorg.conf to get basic operations working smoothly. As yet, pressure sensitivity still does not appear to work - but I never really cared for that feature.

Something I just realised: whenever I had to re-install Windows (oh so many times), the mouse senstivity settings were always off. Under Ubuntu, the mouse has always felt right.

Whilst typing this, I decided to listen to some music. I started to mount the main Linux partition and the new policykit feature clicked in. I must admit it gave me the impression I was allowing anyone the future right to mount the volume, but further digging seems to have dispelled that. I need to investigate further - especially since I would still like to be asked for a password when I do things like that.

So far I am very pleasantly pleased with this release. I shall be putting it through various other hoops before I decide to go ahead with the full installation, but I think I could easily recommend this distro.

W00t doggies, indeed.

---

