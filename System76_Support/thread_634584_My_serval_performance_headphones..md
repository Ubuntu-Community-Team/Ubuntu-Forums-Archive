---
title: "My serval performance headphones."
date: 2007-12-07
forum: System76 Support
---

### Post by Royal_Pwner on 2007-12-07
When I plug in my headphones, the front speakers don't turn off. 
I can't figure out why, or how to fix it.
Help?

---

### Post by maddog39 on 2007-12-07
Did you try  checking off the headphones option  under "Switches" in the volume control dialog?

---

### Post by Royal_Pwner on 2007-12-08
There is no switches option in the volume control dialog.

---

### Post by thomasaaron on 2007-12-10
Double-click your speaker icon. In the resulting window go to Edit > Preferences and check all available checkboxes.

Now do you have a headphone slider?

You may need to mute "Front."

If you still need help, please post the details of your sound control settings.

---

### Post by Trevor Bramble on 2007-12-23
Should we not expect the hardware controls (Fn+F*#*) to manipulate sound settings?

Could the default non-working status be fixed by adding the appropriate keyboard shortcuts?  (I'm not sure how that works with Fn keys.)

---

### Post by thomasaaron on 2007-12-24
You can set what channels the function key combinations control by going to System > Prefs > Sound and then highlighting the channel you want to control at the VERY bottom of the GUI.

---

### Post by asmiller-ke6seh on 2007-12-24
Here is what I use as a sound setup on my SERP2 - and **my **headphones turn off the front speakers when plugged in - you might want to try my setup; if you have a different model of the Serval Performance you might get a different result.
> **asmiller-ke6seh said:**
> <CLIP>
So, I deduce that on the **serp2** that the following should be done to allow for full use of the sound system for analog mike input and good sound output through either the front speakers (I love the laptop sound) or with speaker disconnect when plugging in an analog headphone:

1) Open the Sound Preferences by selecting **SYSTEM** | **PREFERENCES** | **SOUND** from the menu.
- On the **DEVICES** tab, use the following selection:
  **Sound Events**
  - Sound playback: Autodetect
  **Music and Movies**
 - Sound playback: Autodetect
  **Audio Conferencing**
  - Sound playback: Autodetect
  - Sound capture: ALSA - Advanced Linux Sound Architecture
  **Default Mixer tracks**
  - **Device: HDA Intel (ALSA mixer)**
*device and tracks to control (from the list) use Control and the mouse click to select all of the following, only:*
  PCM
  Front
  Capture
Click **CLOSE** to continue

2A) Open the **Volume Control: HDA Intel (ALSA mixer)** dialog by double clicking on the speaker icon in the panel.
  a) Select **EDIT** | **PREFERENCES** and select these items (check boxes) only:
  -  Headphone
  -  PCM
  -  Front
  -  Microphone
  -  Capture
  -  Capture 1
  -  Digital
  -  Input Source
  -  Input Source
  b) Click **CLOSE** to close the Volume Control Preferences dialog to continue

2B) On the **PLAYBACK** tab, set the controls as follows:
  a) **Headphone** full down - muted
  b) **PCM** full up - unmuted
  c) **Front** full up - unmuted
  d) **Microphone** full down - muted

2C) On the **RECORDING** tab, set the controls as follows:
  a) **Capture** half way- unmuted
  b) **Capture 1** full down - unmuted
  c) **Digital** half way - unnmuted

2D) On the **OPTIONS** tab, leave the Input Source (both of them) set to **Mic** (the only setting available).

Close the **Volume Control: HDA INTEL (Alsa Mixer)** dialog to finish.



---

### Post by thomasaaron on 2007-12-26
If that doesn't work, you might try to mute the "Front" channel when you are using headphones.

---

### Post by Trevor Bramble on 2007-12-26
Perfect.  Thank you both.

After muting both Headphones and Front, I selected them for the controls.  Now they respond in sync to Fn volume manipulation and when plugging in the headphones, Front is muted while the beat goes on in the 'phones, and vice versa as appropriate.

Just what I was looking for.  It's one of those low-priority comforts I hadn't come around to solving yet, and I halfway expected that the Fn sound keys couldn't be used at all.

Thanks again!

---

### Post by asmiller-ke6seh on 2007-12-26
:)

Glad we could help - my posting is based on thomasaaron's help to me: I just posted my successful results.

By the way, if you appreciate the help, it is nice if you can recognize the poster by clicking on that little "hero's star" [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG] found in the bottom right of the post(s) that helped you.

---

### Post by Royal_Pwner on 2007-12-26
Oh, I didn't know that.
Thanks for the help!

---

### Post by asmiller-ke6seh on 2007-12-27
> **Royal_Pwner said:**
> Oh, I didn't know that.
Thanks for the help!

:) Just trying to be helpful :)

:lolflag:

---

