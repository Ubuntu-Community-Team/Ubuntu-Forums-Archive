---
title: "Some fixes for Meerkat Ion running Karmic."
date: 2009-11-23
forum: System76 Support
---

### Post by Makurosu on 2009-11-23
I recently bought a Meerkat Ion.  I have found solutions to three problems that were hard for me to find, so here are the solutions:

1.  **Unable to play video at 1080p out of the box.**  Specifically, Matroska files with h.264 video compression.  Here's how to fix that.

Add "ppa:nvidia-vdpau/ppa" to your repositories in Software Sources.  It will poof up to "http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main" after you add it.  Reload when it asks.

Add the package "nvidia-190-modaliases".  This will make it possible for Karmic to detect the Nvidia 9400M architecture.

Go into Hardware Drivers and activate the 190 driver.

Install mplayer, smplayer, x264, xine-ui, etc.  Then go into the Preferences of each player and select VDPAU as the output driver.

For more information, read [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)  Make sure you check out the hdr-wallpapers package.  There are some really beautiful images.


2.  **No HDMI audio output.**

I experienced this problem when the Meerkat Ion first arrived.  Then I reinstalled Karmic and the problem occurred again.  I think this is an issue with Karmic muting the IEC958 channels.

Run "alsamixer" from the terminal.  Scroll to the right until you see the three IEC958 channels.  Press "m" to unmute them.  Sound should work immediately.


3.  **Problems with SDLMAME/GMAMEUI.**

I've had a very annoying problem with SDLMAME having crappy audio and then crashing my system when I exit by pressing the ESC key.

Install the package libsdl1.2debian-pulseaudio.  This will uninstall the package libsdl1.2debian-alsa, but it completely fixed the problem.


The System76 driver did not work out of the box, but that may be because the BIOS is not properly installed.  System76 support is helping me with that.

I bought the Meerkat Ion originally to be an HTPC.  It has the Nvidia Ion (9400M) chipset with HDMI output and 7.1 audio, so there was no reason why it couldn't be.  Since I got the video working correctly, I've been able to play all my 1080p files quite well with one of the CPU's running at only about 20%.  I'm not sure why they put a fan in there.  The Atom 330 processor should not need a fan and the Nvidia Ion contains the 9400M chipset which is designed to only need a heatsink.  But the computer is built like a tank, it's small, and looks good with the rest of my black TV components.

I added an Adesso Wireless Mini Trackball Keyboard which I highly recommend.  I have the TV in my bedroom and I sit on the bed with the keyboard in my lap, and I can watch movies, surf the web, etc.  I also have two 1TB hard drives attached to it via USB with my movies and music.  So far it's doing what I want.

I hope this helps.

---

### Post by eddietours on 2010-01-25
cool am thinking of buy one wht the max resolution ?

---

