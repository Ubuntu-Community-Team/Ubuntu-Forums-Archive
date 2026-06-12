---
title: "ALSA instead of Pulseaudio"
date: 2010-01-14
forum: Ubuntu Studio
---

### Post by marin123 on 2010-01-14
Hello,
i have a problem with LMMS: when i choose alsa output i cant get audio (no sound) and i have midi input, but when i choose pulseaudio as output i can get sound, but cant have midi input (m-audio o2 if its important)..
Is there any way to switch from pulse to alsa? i tried using Default Sound Card and it cant start...
I'm using 64-bit karmic..

---

### Post by thorgal on 2010-01-14
open a terminal and type
```

pulseaudio -k

```

to stop pulseaudio and try lmms with the ALSA backend again.

This is not a fix but a way to see whether this is the problem.

---

### Post by AutoStatic on 2010-01-15
Pulseaudio will respawn immediately again after killing it, unless you tell Pulse not to do so with a client.conf file.
Another option would be to use the **pasuspender** command. The steps would be then:
- Open LMMS and select ALSA as the Audio Interface (Edit - Settings - Speaker icon), don't close it yet
- Open a terminal and enter the command **aplay -l**, this will output info on your soundcards, we're interested in the part after 'card 0:', or 'card 1:' if you have one and want to use that specific card. If it's an onboard card it will probably say 'Intel'
- Go back to LMMS and enter 'hw:Intel' in the 'device' field instead of 'default'. If you leave it on 'default' LMMS still won't make a sound because the 'default' ALSA device is.... Pulseaudio and we're going to supend it with the **pasuspender** command
- Click OK and close LMMS
- Restart LMMS by going back to the terminal and enter **pasuspender -- lmms**. If you want to avoid the terminal you can enter the command also after pressing Alt+F2 or create a new shortcut for LMMS with this command
- Now Pulse gets suspended so LMMS can use ALSA as the backend
- LMMS starts with sound and MIDI

---

### Post by gradinaruvasile on 2010-01-15
Pasuspender doesnt really work in 9.10. And cannot set alsa as output device as long as pulseaudio is running. 
Only way is to kill pulseaudio at startup, set in the client.conf autospawn=no and edit alsa.conf to not load the pulseaudio modules. The last step is required because some alsa programs doesnt work if the pulseaudio module is loaded even if pulseaudio itself isnt.

---

### Post by JC Cheloven on 2010-01-15
> **gradinaruvasile said:**
> Pasuspender doesnt really work in 9.10. And cannot set alsa as output device as long as pulseaudio is running. 
Only way is to kill pulseaudio at startup, set in the client.conf autospawn=no and edit alsa.conf to not load the pulseaudio modules. The last step is required because some alsa programs doesnt work if the pulseaudio module is loaded even if pulseaudio itself isnt.

In my experience, it is the way to go.
Perhaps the OP needs a more detailed explanation on how to do this this:

- Create the file  ~/.pulse/client.conf
- Stuff it with a single line: ```
autospawn=no
```
- When you want to get rid of pulseaudio, execute ```
pulseaudio -k
```
- When you want again pulseaudio around, execute ```
pulseaudio -D
```

None of these require root privileges.

EDIT: If for some reason you want to completely uninstall pulseaudio and get things working with alsa only, follow post #4 here: [http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)  It's how I'm running my main UbuntuStudio (due to a pulse-problem with my hammerfall 9632 pci card).

---

### Post by marin123 on 2010-01-22
thanks guys, this works great :))

---

### Post by marin123 on 2010-02-08
does anyone know why i'm getting cracking sound when i play lmms... i dont know when it started happening but i know this wasnt happening before...
when i play something in lmms sound breaks (doesnt play) and i hear a crack instead of sound (cracking sound like in cassetes)...
this is very annoying and i cant work anything with this problem (not that the world is missing some great stuff from me :D :P)

---

### Post by JC Cheloven on 2010-02-10
> **marin123 said:**
> does anyone know why i'm getting cracking sound when i play lmms... i dont know when it started happening but i know this wasnt happening before...
when i play something in lmms sound breaks (doesnt play) and i hear a crack instead of sound (cracking sound like in cassetes)...
this is very annoying and i cant work anything with this problem (not that the world is missing some great stuff from me :D :P)

Have you the RT kernel, and rt permissions correctly configured? Nice value set to something suitable? Please see the rt section of:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by marin123 on 2010-02-11
i have rt kernel, and i'm using LMMS with alsa, everything works great, i can use vst's...
thanks for your help!

---

