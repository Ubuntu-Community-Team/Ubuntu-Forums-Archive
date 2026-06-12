---
title: "Removing background hiss from MP4's audio track"
date: 2010-01-28
forum: Ubuntu Studio
---

### Post by haldrik on 2010-01-28
Hello everyone,
I am a professor who records his lectures with an inexpensive flip ultrahd video camera, which I love for its convenience. However, because I stand fairly far from the camera, and because the air conditioning is always running in the classroom, it's sometimes hard to hear what I'm saying on the video because of the background hiss. I use Audacity on sound files to take take of this nicely, but I haven't been able to find tools to do the same on the video. If this requires ripping the audio from the mp4, applying filters, and then pasting this back into the video, I'm fine with that. I just need to know, step-by-step, how to accomplish this.
Many thanks for suggestions.
Cheers!

System: Standard Ubuntu Karmic - 64 bit on Intel core-2-duo.

---

### Post by LuridCinema on 2010-01-28
I would do it in Audacity right click on the file and open w/ audacity.
you highlight a small 1 sec sample of just the fzz and then click on Effects then choose Noise removal then click "Get Noise Profile" , the hit "Ctrl + A " to select the entire track and go to effects > noise removal again and try mebbe 15db of noise removal and hit OK
You can go up to 20db of noise removal, the higher you go you risk making the voices sound like chipmonks. Play with several settings of noise removal first and see what the result is. . You might even select all and try "normalize" effect after you remove the fuzz, normalize will make the audio richer and bring it out more. when U R happy....... Export the audio as an ac3 file
Then drop it into the Timeline of either Openshot or Kdenlive along with the original video delete or turn off the sound of the noisy audio and line up the new improved audio and render

You can prolly find some tutorials on youtube

---

