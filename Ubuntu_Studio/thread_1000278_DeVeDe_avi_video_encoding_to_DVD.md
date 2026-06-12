---
title: "DeVeDe avi video encoding to DVD"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by groovomata on 2008-12-02
Hello All,
I am trying to use the program DeVeDe to convert an avi file to a playable DVD video. The video part looks fine, however the audio track is out of sync.

Are there any options that I should choose using DeVeDe to resolve this? Or is there a better program that I should use?

Thank you in advance for your help,
Erik.

---

### Post by axel206 on 2008-12-03
According to this guide [How to create a custom DVD using DeVeDe](http://www.my-guides.net/en/content/view/75/26/) you can manually add a delay in the audio.

Just test the final DVD before burning it to a disk. ;P

---

### Post by stinger30au on 2008-12-03
handy, thanks

---

### Post by groovomata on 2008-12-03
Thanks, I'll check it out, however the sync timing seemed to fluctuate. Sometimes virtually right on, sometimes quite noticably off.
Thanks,
Erik.

---

### Post by groovomata on 2008-12-27
I discovered that I had selected the wrong option between PAL and NTSC. I changed my selection and it worked fine.
Thanks for the help,
Erik.

---

### Post by sleepingdragon on 2008-12-28
I've had similar problems with DeVeDe. The only thing I found that was foolproof (for me) was to change the audio conversion to *MP2 (TwoLAME)* and to export the audio as an MP2 track (*Audio -> Save*). This should only take a few minutes.

When done, import the track back in as the main audio track (*Audio -> Main Track) *and change the *Audio Source* to "External MP3". Now you should be able to navigate to the MP2 track you created earlier.

I have no idea why converting the audio separately seems to help... but the MP2 track should now stay nicely in sync with whatever video conversion you throw at Avidemux.

Hope some of that helps.

---

