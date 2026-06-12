---
title: "JLAB b-flex C-Media USB speaker finally working on Intrepid 8.10"
date: 2009-11-21
forum: System76 Support
---

### Post by elphaba on 2009-11-21
Wanted to report because I received so much help from various posts, many in this forum though no individual post precisely helped but all together (including several major sound tutorials on the web), they were invaluable.

This effort has definitely decreased my enthusiasm for ubuntu.  Shouldn't have been this hard.  Oh well, I guess I should be grateful I was successful at all.

These are all the apps and places I "touched" in getting my JLAB b-flex C-media USB speaker working, Not sure this is the right order but the end result of this for my system was successful - may be some reboots necessary between steps..

1. confirm that Pulseaudio volume control and Pulseaudio meter control is installed - (go to pull down menu for Applications, then add/remove, then search for pavumeter and pavucontrol - if not installed, then install)
2. double click on "master applet" (mine looks like a microphone in upper right corner- single click will get you only volume increase or decrease- need to double click)
3. select "c-media usb audio device (alsa mixer) from the list in the pull down at the top of the box 
  FYI - I know that my speaker was "C-Media" by entering following command from a terminal session:
  $ cat /proc/asound/cards
 returned info below:
----------------------------------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4600000 irq 22
 1 [default        ]: USB-Audio - C-Media USB Audio Device   
                      C-Media USB Audio Device    at usb-0000:00:1d.0-1, full speed
----------------------------------------------------
4. start pulse audio device chooser in pulldown under Applications 
5. select preferences in chooser and then check box for "start applet on session login"
6. (this is most important step to do!)  modify /etc/modprobe.d/alsa-base by commenting out "options usb snd audio index=-2 i.e. insert "#" at beginning of line (this line was preventing the usb speaker from becoming the default)
7. click on system pull down menu, then preferences/sound and click on devices tab, then set or confirm that:
  a. "Sound events - sound playback  - says "c-media..."
  b. "Music and movies - sound playback - says "c-media..."
  c. confirm both fields under Audio Conferencing say "pulseaudio server"
  d. confirm that "Default Mixer Tracks"  says "c-media..."
8. Note: need to reboot (now is good time if not rebooted yet) at some point after the file in modprobe.d directory changed and before you can increase volume on usb speakers in next steps
9. click on pulseaudio applet (mine is in a tray at the top of my screen)
10. select volume control
11. select playback
12. then adjust volume by sliding bar - this was point that my speaker(s) began working properly

They're not the greatest speakers, I know, but they sure beat the sound from the PC speakers.  I think I may spring for the Logitech Z5 (or maybe something even better) since I've now got (some of) this stuff figured out. 

FYI - Here is an Amazon link where I purchased them at:
[http://www.amazon.com/USB-Laptop-Speakers-Portable-Notebook/dp/B001I7IVEG/ref=sr_1_2?ie=UTF8&s=electronics&qid=1258812868&sr=8-2](http://www.amazon.com/USB-Laptop-Speakers-Portable-Notebook/dp/B001I7IVEG/ref=sr_1_2?ie=UTF8&s=electronics&qid=1258812868&sr=8-2)

---

