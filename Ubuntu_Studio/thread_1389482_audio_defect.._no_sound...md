---
title: "audio defect.. no sound.."
date: 2010-01-24
forum: Ubuntu Studio
---

### Post by esash on 2010-01-24
Hi all,

I am a new user of ubuntu.. I tried playing a song file after installing all the necessary softwares.. But the song is playing without any sound.. I tried playing songs in windows xp to check if the sound card is damaged, but it played well in xp. I'm experiencing this only in ubuntu.. Please help.. 

Thanks in advance
Esash

---

### Post by ajgreeny on 2010-01-24
Deleted as double post appeared.  Sorry!

---

### Post by ajgreeny on 2010-01-24
Use the command ```
alsamixer
``` in terminal.  In the window that appears navigate with the cursor keys to move from slider to slider and to raise and lower the sliders, and the "M" key to mute and unmute sliders.  Tab will move from Playback to Capture to All.  Check that nothing is muted, or too low, and you may get your sound back.

---

