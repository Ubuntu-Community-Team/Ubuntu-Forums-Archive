---
title: "killall pulseaudio - am I the only one?"
date: 2008-11-29
forum: The Cafe
---

### Post by Hellcom on 2008-11-29
I've grown so tired of compensating for pulseaudio (due to its lousy support for things like OSS and openal) that I've now got my sessions manager set to 'killall pulseaudio', and thus have defaulted to ALSA. I'm thinking about just removing the packages altogether as the additional features it provides seem pointless to me and I'm happy with just ALSA.

Does anyone else hate pulseaudio as much as I do?

---

### Post by screaminj3sus on 2008-11-29
I haven't had any problems with it...

---

### Post by k@e on 2008-11-29
I have installed PulseAudio 0.9.13 in Intrepid. It works much better than the official version from the repos. It was a pain in Hardy.

Sadly, PA still works horrible with Wine. Unless it does not get fixed, I have to refuse using PA.

---

### Post by Tom--d on 2008-11-29
Just remove pulseaudio in synpatic Package Manager. After, it will default to ALSA.

---

### Post by ssam on 2008-11-29
works fine for me on several machines.

i look forward to having some more advanced GUI tools for things like pushing the streams around a network.

---

### Post by Pekkalainen on 2008-11-29
Pulseaudio made the old sound issues from Hoary (or Warty) come back for me. :(

---

### Post by Exsecrabilus on 2008-11-29
Wonderful work has been going on for PulseAudio in Intrepid. I have no issues now after upgrading to 8.10.

---

### Post by SunnyRabbiera on 2008-11-29
Pulse has some way to go, but who knows what it can bring to the table in the future.

---

### Post by binbash on 2008-11-29
It sucks at some games, you have to kill pulse audio before starting some applications.I am gonna remove it soon.

---

### Post by mrgnash on 2008-11-29
> **Hellcom said:**
> I've grown so tired of compensating for pulseaudio (due to its lousy support for things like OSS and openal) that I've now got my sessions manager set to 'killall pulseaudio', and thus have defaulted to ALSA. I'm thinking about just removing the packages altogether as the additional features it provides seem pointless to me and I'm happy with just ALSA.

Does anyone else hate pulseaudio as much as I do?

Yes, I purged it from my system and switched to Open Sound V4.

---

### Post by rajeev1204 on 2008-12-01
I love it. I can finally fire up more than one application with sound playing for each one of them.So now i play my favourite games with rhythmbox in the background.

---

### Post by Rick Deckard on 2008-12-06
> **Hellcom said:**
> Does anyone else hate pulseaudio as much as I do?

I'm using pulseaudio 9.10 with Intrepid and the only real issue I have is when using Audacity - but it is an easy compromise; just use the **pasuspender** command to put the pulseaudio server to sleep allowing Audacity to have exclusive use of **/dev/dsp** - when the application has ended, the Pulseaudio Server automatically wakes up again and continues to function as before. Magic.

So, in Gnome for example, edit the menu entry for Audacity and set the command field to:

```
pasuspender -- audacity
```

The two hyphens are important!

Do the same for other 'troublesome' applications - after all, it's not Pulseaudio that's at fault, it's the way that some applications are written.

I think Pulseaudio is a step forward - most of my applications work perfectly with it and eventually, newer versions of the 'problem' apps will come along and fix the **/dev/dsp** issues...

---

