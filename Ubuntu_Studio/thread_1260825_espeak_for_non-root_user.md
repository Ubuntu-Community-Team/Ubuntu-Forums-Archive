---
title: "espeak for non-root user"
date: 2009-09-08
forum: Ubuntu Studio
---

### Post by xxhon on 2009-09-08
Hi

Please help.

I can't run the espeak command. When I type

espeak hello
espeak "hello"
espeak "hello how are you"

give no sound or sometimes just give a small "beep" sound.

But then if I login as root then the espeak no problem.

I using ubuntu 9.04. all packages updated and upgraded to date.

---

### Post by xxhon on 2009-09-09
Is that something to do with the user permission for espeak?

I can play sound in console for both root and non-rootuser.

---

### Post by scott.alan.kline on 2009-10-02
Add the user to the audio group:

```
sudo usermod -a -G audio *<yourusername>*
```

And try running it as sudo:

```
sudo *espeak "hello."*
```

Does that work?

---

### Post by xxhon on 2009-10-13
I didnt add the user to the "audio" group (and double confirm with id command)

even thought that but I can run "espeak hello -w output.wav" successfully and generated the wav file then play with sox with no problem.

thanks anyway for giving suggestion.

---

### Post by scott.alan.kline on 2009-10-14
Try these, they may work for you...

First try with a longer output, like "hello, this is a test of the espeak system. Hello again, this is a test of the espeak system"

Instead of just "Hello".

Only because sometimes the settings shoot the sound out super fast and I have noticed some systems the first few words never come out of the speaker, so I add spaces in front of them which works sometimes. Trying a long sentence like above you will here the trailing end of the sentence if that is the case. If you hear the last part of the sentence normal then you know you need to just 'pad' your output text, if it comes out super fast then adjust the output with the espeak options (do an espeak --help to see them all, there are two speed settings one for the space between words, and one for how quickly the words are output)

You can also try removing PulseAudio altogether (if you are using that) it seems to cause some problems with a lot of audio output issues.

---

