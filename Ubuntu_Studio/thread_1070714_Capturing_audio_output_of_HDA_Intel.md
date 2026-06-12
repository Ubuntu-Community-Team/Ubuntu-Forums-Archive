---
title: "Capturing audio output of HDA Intel"
date: 2009-02-15
forum: Ubuntu Studio
---

### Post by riksweeney on 2009-02-15
Hi,

I've been trying to capture the audio output of a game that I'm writing using Audacity but I can only capture the sound coming from the microphone. Has anyone had any luck capturing the sound coming out of the soundcard?

HDA Intel

Thanks

Richard

---

### Post by Malacoda103 on 2009-04-09
i'd like to know as well please!

---

### Post by thorgal on 2009-04-09
I guess you can always feed the output to the physical input :lol:

seriously, I think there used to be an ALSA module called snd-aloop, for just that purpose. Maybe you can look in this direction.

---

### Post by TheBuzzSaw on 2009-04-09
Personally, I just set the **Sound capture** field (System > Preferences > Sound) to the same thing as the sound output devices listed everywhere else.

---

### Post by Malacoda103 on 2009-04-11
> **TheBuzzSaw said:**
> Personally, I just set the **Sound capture** field (System > Preferences > Sound) to the same thing as the sound output devices listed everywhere else.


Hmmm it all seems to be on auto detect and when i use other settings it wont playback or it still wont capture....

---

### Post by Abu_Dayya on 2009-04-12
You can try jack_capture. Its a small software that works on JACK and captures whatever is playeing through the speakers. read the README file for more information 

[http://old.notam02.no/arkiv/src/?M=D](http://old.notam02.no/arkiv/src/?M=D)

---

### Post by Ascenti0n on 2009-04-12
I did read a post that gave a howto on exactly that. Do a search for something like: 'sound capture speakers'.

---

### Post by markbuntu on 2009-04-12
Since you are using Intrepid, you can now do that by running audacity with pulseaudio according to this

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

### Post by Malacoda103 on 2009-04-13
> **markbuntu said:**
> Since you are using Intrepid, you can now do that by running audacity with pulseaudio according to this

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

works perfect! thanks!

---

