---
title: "Ubuntu studio, Djplay crashed."
date: 2008-09-17
forum: Ubuntu Studio
---

### Post by rick3878894 on 2008-09-17
So finally got jack up and running now I have one last thing to over come. Djplay is crashing on me. For the first time it is going belly up. 

It loads fine but once you try to select a folder that holds music in it with the built in file manager then it eats dirt. i.e:

/home/xess/Music/empty folder or one with out mp3's | [ok]
/home/xess/Music/Rip of cd or other music files | [fail] it just crashes.

Here is the out put from running it out of a command line:
```
xess@numbersix:~$ djplay
No Hercules DJ Console found
Port system:capture_1
Port system:playback_1
Port alsa_pcm:monitor_1
Port system:playback_2
Port alsa_pcm:monitor_2
cannot lock down memory for RT thread (Cannot allocate memory)
Audio player cannot su to root
Audio player cannot su to root
Port 0: Semitone Shift
Port 1: Rate Shift [%]
Port 2: Dry Level [dB]
Port 3: Wet Level [dB]
Port 4: latency
Port 5: Input
Port 6: Output
LadspaEffect instance created
LadspaEffect instance created
Port 0: Semitone Shift
Port 1: Rate Shift [%]
Port 2: Dry Level [dB]
Port 3: Wet Level [dB]
Port 4: latency
Port 5: Input
Port 6: Output
LadspaEffect instance created
LadspaEffect instance created
Port 0: Lo gain (dB)
Port 1: Mid gain (dB)
Port 2: Hi gain (dB)
Port 3: Input L
Port 4: Input R
Port 5: Output L
Port 6: Output R
Port 7: latency
LadspaEffect instance created
Port 0: Lo gain (dB)
Port 1: Mid gain (dB)
Port 2: Hi gain (dB)
Port 3: Input L
Port 4: Input R
Port 5: Output L
Port 6: Output R
Port 7: latency
LadspaEffect instance created
Port 0: Lo gain (dB)
Port 1: Mid gain (dB)
Port 2: Hi gain (dB)
Port 3: Input L
Port 4: Input R
Port 5: Output L
Port 6: Output R
Port 7: latency
LadspaEffect instance created
Port 0: Lo gain (dB)
Port 1: Mid gain (dB)
Port 2: Hi gain (dB)
Port 3: Input L
Port 4: Input R
Port 5: Output L
Port 6: Output R
Port 7: latency
LadspaEffect instance created
Scan /home/xess/Music/Mathias Klingner - Songs And Wrongs -- Jamendo/01 - Arktis.mp3
Segmentation fault

```

I am not sure what a segmentation fault is but I would love for it to stop doing that. 

Thanks for reading.

---

### Post by rick3878894 on 2008-09-17
It still crashes in my music folder but not when I route it to my mp3 player.

Though some songs that I play are very distorted. I don't know if this is an issue with djplay or jack. Is there a way to fix this?

---

