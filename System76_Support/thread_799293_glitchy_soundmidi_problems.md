---
title: "glitchy sound/midi problems"
date: 2008-05-18
forum: System76 Support
---

### Post by eyecreate on 2008-05-18
I have a serp4 laptop I just bought. I have to say I love my purchase, but there is one minor problem I'd like to have fixed. I use many programs to do audio editing on my laptop. I have used LMMS, Hydrogen drum machine, Renoise, and Rosegarden. In general, when I use ALSA driver, I usually get glitchy sound. This happens in renoise and hydrogen especially.(I do not notice it really much in the others) After switching hydrogen's driver to OSS, the glitchy sound stops. I can not test Renoise because there is only ALSA, but I am surprised when LMMS does not seem to have difficulty with the ALSA driver. The CPU is not very high, so there is enough resources, but the sound still glitches. The other problem is I can not get the MIDI to function properlly. I have tried playing and editing MIDI in many software to little success. IDK if this is a problem to just my laptop because my desktop with hardy has the (almost)same problem.(i can sometimes get my soundblaster live to play midi on my desktop, but not all software, rosegarden plays MIDI nicely on my desktop but not any other audio player/editor) 

Would love to get at least smooth sound on my serp4 and maybe even better support on the MIDI.

---

### Post by Bakon Jarser on 2008-05-18
This guide worked for me.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Looks like some other people found this guide helpful

[http://ubuntuforums.org/showthread.php?p=4991126#post4991126](http://ubuntuforums.org/showthread.php?p=4991126#post4991126)

---

### Post by eyecreate on 2008-05-20
while not perfect, the first tut help things out a bit, that is, changing the kernel.(still some blips, but i'll check the other tut later) I noticed some other odd occurrences too now. I am making a small test game in pygame, and I cannot get it(the sound) to play. It plays for 1 sec or less and then stops the sound. Also, any pygame program I make, when calling sys.exit(), will stop the game(as if you paused it), but has to be forced closed, even at the python interpreter(terminal-enter basic code line by line) it does it. I only noticed some of this recently, and I hope its a quick fix and not due to something I did trying to get the sound to work.


EDIT: here is a quick flash anim I put together to show you what I was talking about. 
[http://img362.imageshack.us/img362/645/pygamemd4.swf]("http://img362.imageshack.us/img362/645/pygamemd4.swf")

EDIT2:I partially fixed this by reading another post that seemed unrelated. I added this to my ~/.profile file "export SDL_AUDIODRIVER=pulse". Now the sound plays and the game doesn't stall on quit. It seems that ALSA(or whatever pygame defaults) does not like my computer. The sound still seems to have the same problem of glitchy sound, but at least it plays. I'm getting closer to a solution.

---

