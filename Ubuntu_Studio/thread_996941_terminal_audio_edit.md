---
title: "terminal audio edit?"
date: 2008-11-29
forum: Ubuntu Studio
---

### Post by rylleman on 2008-11-29
I'm looking for some tool that lets me do basic audio editing at the terminal for a bash-script I'm writing.
All I really need to do is cut a piece at the start and/or the end of the file.
I know ffmpeg can do this but it only seems to be able to work with seconds, I need some more accurate than that. Centesimal at least (have to match film frames).
So something like FFmpeg but for audio anyone?

---

### Post by nowardev on 2008-11-29
look a this 
[http://www.cli-apps.org/content/show.php/fual+(FuocoUbuntuAudioLooper)?content=88071](http://www.cli-apps.org/content/show.php/fual+(FuocoUbuntuAudioLooper)?content=88071)
we have created with bash and sox  :

sox libsox-fmt-all

---

### Post by rylleman on 2008-11-29
Thanks,

I guess Sox is hat I'm after.

---

### Post by Stochastic on 2008-11-30
ecasound is also a very handy (and more flexible) command line wave editor.

---

### Post by rylleman on 2008-11-30
> **Stochastic said:**
> ecasound is also a very handy (and more flexible) command line wave editor.
Thank you.
Ecasound seems more robust than Sox. I'll try them both out to see which one I like the best.

For Ecasound, reading through the man pages it seems that you can use 2 decimals for time, is this true?

For Sox, all examples use only one decimal for time. Is this as accurate as it goes?, I would need 2 decimals.

---

