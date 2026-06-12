---
title: "New Panv3 No Sound  (newbie woes)"
date: 2007-11-29
forum: System76 Support
---

### Post by kegreenough on 2007-11-29
Bought a Pangolin mid-October this year.  Set it up, but didn't start using it until Thanksgiving.  Little gun shy.

Beautiful machine.  Upgraded to Gutsy Gibbon.  Connected the restricted repositories.  Installed RealPlayer.  (Tried to install RealPlayer and Helix at same time.  System gave an 'overlap' file use error (didn't save a copy.  So I removed the Helix and got a smooth install of RealPlayer.)

But, no sound.

I connected, as a test, to a site with RealPlayer streams, which I access often on my Dell/WinXP.  (Spiritual-Happiness.com)

The RealPlayer seemed to be getting the stream.  But no sound.

Went to the forums.  Tried many 'no sound' thread possible solutions.  None worked.

Did not keep a formal list of what I tried, but, this is close.

Checked mute. 

Checked alsamixer in the terminal.  Set levels at 80 %.  Not muted.

Tried each of the sound apps.  None worked.  Amarok had a  12sec. sample.  Amarok indicated, via emulator bars, that sample was playing, though no sound through speakers  or  headphones.

Tried speaker and headphones as separate tests for each of above.

Put in another Linux (PCLinuxOS) live CD and booted from that disk.  The PCLinuxOs detected the sound card but had same problem.  Amarok sample used as test.  Emulator bars undulate but no sound through speakers or headphones.

Rebooted to Ubuntu.  Tried system restore to factory settings.  Each test, no sound.  Upgraded again to Gutsy.  No sound. 

I balked at replacing the sound kernel alone - since this, evidently would have lopped off the desktop too, and I was too timid to worked through that.

I love the machine.  Very elegant and quiet.  Ubuntu is so obviously superior to Windows, that I want to find a way to get this working properly.

Finally,  tried inserting a movie, to see if it would play with sound or not.  Couldn't seem to get the machine to recognize movie in DVD drive.  (I'm a newby, so probably some simple mistake of mine here, too.)

Two days later.

I've gone through all the steps on the knowledge76 guide to sound problems page, including (just now)  replacing the sound kernel.

Here's what the terminal indicates:

greenough@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
greenough@ubuntu:~$


Again.  I have checked the mutes and set the sound levels at 80%.  But I get nothing.  (I am mainly using the Sound Preferences Autodetect Test to check).

I also, continue to try sliding a movie dvd into the machine.  Supposedly, the computer should detect this, but it does not.  It does not seem to detect the existence of this drive.  Don't know if this is related. Yet I have booted from this drive into a PCLinuxOS live CD, and it worked fine.  Although no sound.



What do you suggest?

---

### Post by thomasaaron on 2007-11-29
Did you try the steps in the two emails I sent you?

Best,
Tom

---

### Post by kegreenough on 2007-11-29
Only email I received from you was a notification of reply on this forum.

In the intermediary time,  I was playing around.  Added some pulseaudio devices.  Then did a system restore, and had sound at the log-in.  And the test sound autodetect was working.  

So.  The sound card is up and running.

However, The realplayer 10 can receive a test stream, but does not register sound.  And a sample vid on youtube will display the video, but without sound.

Also.  When a Cd or DVD is put in the 'whateveryoucallit'.  The computer gives me this:

mount: special device /dev/scd0 does not exist

Alas.

Still, I am happy to get any sound at all.  

Don't know why the other emails did not show.

---

### Post by thomasaaron on 2007-11-29
I'm re-sending the email now.

---

### Post by thomasaaron on 2007-11-29
Did you get it?

---

### Post by octathlon on 2007-11-29
> **New Panv3 No Sound**

I love the machine. Very elegant and quiet.


Sorry, I just had to laugh at that. :D

Good luck, I have a Panv3 and love it too. :)

---

