---
title: "No Sound after Install"
date: 2012-01-11
forum: Ubuntu Studio
---

### Post by decibeldesign on 2012-01-11
Hi;

Just installed Studio and I get no sound.

I followed some of the advice on the forums and the system does seem to see the sound card, not that I have confirmed the drivers loaded and all is well.

If I run JACK I see nothing listed.

I am new to Linux although I have run older versions of Studio and didn't have this problem.

Can somebody help walk me through the things to check and make sure the sound device is installed etc and where I go from there within the GUI to make sure it is setup properly.  For one thing a lot of the advice said check the volume is not muted, click on the volume icon in the upper bar.  Well in this Studio version there is no volume control on the desktop anywhere, what's up with that?

Thanks

---

### Post by jejeman on 2012-01-11
Which version of ubuntu studio?
give us otuput from
```
aplay -l
```

---

### Post by decibeldesign on 2012-01-11
I am running Ubuntu Studio 11.10.

The reply to the above command is:
==================================================================
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
=====================================================================

I tried several of the suggestions in the forums about inserting lines like:

editting:
sudo nano /etc/modprobe.d/alsa-base.conf

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=HP

sudo alsa force-reload
================================================================

This had no effect.
So it looks like the system sees the device but I still got no sound.
I went looking for the volumn icon on the desktop toolbar to check it was unmutted and there is no volumn icon in this Ubuntu Studio.  So I used the application finder and found 'Pulse Audio Volumn Control'  and as I could find any other way to adjust the volumn in the the Applications Menu, I ran the Pulse Audio, I moved a few sliders and looked in a few drop down menus, but changed nothing.

I tried one last time and I had sound !?!, not sure how or why and I had undo all the changes I did at the terminal level, and in Pulse all I did was click on stuff but changed nothing and now I get sound.  Best I can figure something in Pulse got it working.  However, all is not right with the world as I don't see anything in JACK.  I get Jack squat under the audio tab.

That isn't right is it?

Any thoughts?

Thanks
Dave

---

### Post by sgx on 2012-01-11
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Hi, read links 4 and 8 at the above page to learn connextions.
As you launch software like hydrogen, zynaddsubfx, phasex etc, their items will appear in in the alsa and audio tabs. 

The midi tab will use items only if a2jmidid is installed,
a jackd-->alsa midi connector. Yoshimi will use that, as well as many
others. After installing a2jmidid, start jackd, then this command

a2jmidid -j default

Now, a midi port will be available in qjackctl midi tab.

Your soundcards and motherboard chips will be in the
setup page, middle right,

Input device  >
Output Device  >

click  >  to see a dropdown list of your system audio devices,
and select as needed.

Cheers

---

### Post by decibeldesign on 2012-01-12
Thanks for the help.  Still not sure what made the sound work, but all is well now.  I didn't realize I had to hit Play in QJack first before it would initialize and see the System Sound card.

Thanks

---

