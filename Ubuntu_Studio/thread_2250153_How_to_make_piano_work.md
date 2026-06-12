---
title: "How to make piano work?"
date: 2014-10-27
forum: Ubuntu Studio
---

### Post by andreas30 on 2014-10-27
Hello, 
Sorry for the "very newbie" question. But I have been searching in the forum and didn't find any of the basics...
I have a sound card, Scarlett Focusrite 2i2. It works fine.
I have a USB midi keyboard. M-Audio Prokeys Sono 61.
When I connect it, I see it in the "Input Devices", and when I press i see signal.
Now, my problem is, I cannot figure out how to make sound with that signal! 
I just want to mess around with my piano... Not to record. (Of course, if i get it to make sound, I think i can figure out how to record).

So, if you have the kindness and the time, please share this information, or give me a link so I can read how to do it.
Thanks a lot! :)

---

### Post by richierich1986 on 2014-10-27
Your piano is actually a MIDI keyboard, which doesn't produce sound on it's own. You'll need to use VSTi plugins or something like that if you want to play sound. You should install a software synthesizer or organ for example.

edit: Sorry for my uninformed conclusion. I was thinking of another m-audio keyboard which is purely MIDI.

Still, you'll have to connect the stereo outputs to the inputs of the focusrite sapphire so the soundcard can then output the audio to your speakers

---

### Post by andreas30 on 2014-10-27
The piano is connected via usb directly to the pc.
So i just open a standalone vst and it will work? 
I tried a few and it doesnt. Ubuntu studio has some built in vsts.
does my problem have to do anything with jack?

---

### Post by jejeman on 2014-10-28
Connect everything.
Give
```
cat /proc/asound/cards 
amidi -l
```

---

### Post by andreas30 on 2014-12-13
OK i found how to do it.
I just opened patchage, and connected the keyboard to hexter.
Thank you :)

---

