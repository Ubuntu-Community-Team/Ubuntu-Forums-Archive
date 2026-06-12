---
title: "warcraft 3 TFT not working after patch"
date: 2009-11-12
forum: Wine
---

### Post by blackmajik2021 on 2009-11-12
I had warcarft 3 running perfectly fine with 

"wine "c:\\Program Files\\Warcraft III\\war3.exe" -opengl : exit"

it ran fast and worked great, then i patched it by updating via battle.net, and now i cant get it to run. I get this error 

~$ wine "c:\\Program Files\\Warcraft III\\war3.exe" -opengl : exit
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
err:module:map_image Could not map section .text, file probably truncated

It seems like a videocard problem, but that wouldnt make sense since it was running just fine before. 

I tried installing winetricks and that helpe a little bit because now I Don't get the allocate memory error i just get. 

 ~$ wine "c:\\Program Files\\Warcraft III\\war3.exe" -opengl : exit
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
err:module:map_image Could not map section .text, file probably truncated

help please!

---

### Post by beastrace91 on 2009-11-13
What Wine version are you running?

~Jeff

---

### Post by blackmajik2021 on 2009-11-13
sorry I thought I included this in the post. 

Wine 1.1.32 Released
ubuntu 9.10
Warcraft 3 TFT 1.24.1.6374
ATI HD4035 1GB video card

---

### Post by Anarci on 2009-11-13
War 3 should not require any additional software and should work with vanilla wine and that error output doesn't really point to any specific software winetricks should install so I'm left wondering what did you install?

You can try removing your ~/.wine folder and reinstalling wine and the game as a last resort.

---

### Post by blackmajik2021 on 2009-11-13
because I read this

[http://ubuntuforums.org/showthread.php?t=845750](http://ubuntuforums.org/showthread.php?t=845750)

I was having a .dll error so I thought I would at least try it.

I ran

sh winetricks vcrun2005sp1

---

