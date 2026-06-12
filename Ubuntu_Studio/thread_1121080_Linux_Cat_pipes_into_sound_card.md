---
title: "Linux Cat pipes into sound card"
date: 2009-04-09
forum: Ubuntu Studio
---

### Post by passonno on 2009-04-09
Hello,

So I have been thinking, I would love to use Ubuntu live in performance as a noise generating tool, and to do this, I used to be able to cat the mouse into /dev/audio to make it do make crazy noise, however I cannot figure out how to do this now.

At this point, I can do this:  sudo cat /dev/urandom > /dev/audio, which is great, except for when I want a little more control over the sound. 

Any other noise weirdos running Ubuntu?

---

### Post by Stochastic on 2009-04-09
I find it's funner to cat a file like a jpg or pdf etc... (even an entire harddrive) to the /dev/audio rather than /dev/urandom (that just gives random white noise instead of a data pattern).

I'm sure there's ways of inserting effects into that chain.  Infact there's toolkits out there that I'm sure are perfect for this task - I'll go searching and try to find some later.

In the meantime, I'd recommend you play with PD or ChucK or SuperCollider for your noise manipulation needs.  The learning curve is steeper than bash but your sonic flexibility is greatly enhanced.

---

### Post by passonno on 2009-04-09
While those sound like pretty damn cool options, and believe me I do appreciate the suggestion, I am still at this point just trying to figure out what Canonical did to change the Ubuntu sees usb devices, as in the past I was simply able to cat /dev/mouse into /dev/dsp and got some pretty cool sound, but as of 8.10 I am simply unable to figure it out.

---

### Post by unutbu on 2009-04-09
Intrepid uses pulseaudio. Perhaps you need something like this

```
padsp cat /dev/urandom > /dev/dsp 
```
?

I don't have a /dev/mouse. Do you?

---

### Post by passonno on 2009-04-10
that does work, both with /dev/dsp and /dev/audio, and I meant to say /dev/input/mouse(*)

I have 3 listings for mice, mouse0, mouse1, and mouse2, yet only have two mice, the logitech cordless, and the mouse attached to my very old IBM keyboard(the nub/eraser thing).

how can I narrow it down?

---

### Post by Stochastic on 2009-04-10
> **passonno said:**
> I have 3 listings for mice, mouse0, mouse1, and mouse2

I have 4 listings for mice within /dev/input/
mice
mouse0
mouse1
mouse2
but none of the four made any sound when I cat'ed them to audio on my Jaunty box with sudo.

I find a nicely indented block of source code or XML is an interesting sound (try a hydrogen .h2song file).

One interesting thing to try would be copy/pasting/saving live into a text file while catting that file over & over in a scripted bash loop.
It'd be almost like Live Coding [http://www.toplap.org](http://www.toplap.org) but by brute force.
Or for those who prefer elegance rather than brute force, here's a little of Andrew Sorensen live coding a song: [http://homepage.mac.com/digego/study_in_keith.mov](http://homepage.mac.com/digego/study_in_keith.mov) (sorry, that's off topic, but only vaguely).

---

### Post by passonno on 2009-04-10
So I guess my next question, and since I am nowhere near being a programmer, it is a good one, how would I go about doing that sort of thing live with a text file?

I would probably have an instance of gedit open, so would it be as simple as it sounds to me?

---

### Post by Stochastic on 2009-04-11
Well the hardest thing would be creating the bash script that repeatedly cats the text file to /dev/audio

I don't know anything about bash programming but from looking at a google help file I'll try to write one
```
#!/bin/bash
while [ "foo" = "foo" ]; do
    cat /path/to/textfile > /dev/audio
done

```
Save that to a file (let's call it loopSkript), change the file's permissions to be executable (easiest would be to do 'chmod 777 loopSkript'), then run that file with 'sudo ./loopSkript'

Then, while that's running head into your gedit and edit the text file.

---

### Post by passonno on 2009-04-11
Super mega kickass!!

Thank you!

What I figured out as well was this:  


touch noise.txt

THEN:  two terminal tabs, one with the script running, the other for the text file, like this

cat >> noise.txt

It's as near to a perfect live text noise synth that I could ever find, so thank you very much!!

---

### Post by mkarnicki on 2009-04-11
That was an interesting thread to follow :)

---

### Post by Stochastic on 2009-04-11
> **mkarnicki said:**
> That was an interesting thread to follow :)

Who says it's over yet ;)

---

### Post by FrankT-Qc on 2009-04-11
Where else can you cat your stuff ??? (Not to be confused with "stuff your cat" ...) 

interesting thread indeed...

---

### Post by passonno on 2010-02-09
It's not over yet,  not by a long shot,  because though I am happy with Windows 7 on my main box,  and even on the notebook,  I did install a wubi 9.10 on the notebook,  and am back to square one on this problem.  

The main thing is I am having a hard time figuring out where the sound card lives in the system,  assuming that Pulse is the culprit.

---

### Post by robeast on 2010-02-10
roger@ultramegamek:~/Pictures$ cat tongue_monkey.jpg > /dev/audio
bash: /dev/audio: Device or resource busy


NOOOOOOOOOOOOO!!!!

---

### Post by AutoStatic on 2010-02-10
Ha ha, you probably have JACK running ;)
With PulseAudio it works fine:
```
cat setup2x24-1.jpg > /dev/audio
```

SCCCHHHHHGGGRGRGGRGGGRGGRGRGGR!!

Hehe, nice :)

---

### Post by robeast on 2010-02-10
No JACK, I'm on my comp at work. 9.1, sound card not being used to my knowledge. :(

---

### Post by robeast on 2010-02-10
How about a little "I am sitting in a room..." as a sound generating an image, then cat that image into audio, record and turn into an image, then cat that image into audio, etc.

---

### Post by AutoStatic on 2010-02-10
> **robeast said:**
> No JACK, I'm on my comp at work. 9.1, sound card not being used to my knowledge. :(Yeah, I'm being a dumbass, generating sound like this has got nothing to do with PulseAudio because you're directly addressing a device node 8-[

And what would be a good way to convert sound to an image?

---

### Post by robeast on 2010-02-10
Spectral map? You could write something to generate image data from sound in all sorts of ways :)

This isn't a good example because it was generated from raw frequency data over time, but it's a cool visualization of sound: [http://rogerwakeman.net/rogerwakeman.net/virtual/interVil/bfaSaves/19.gif](http://rogerwakeman.net/rogerwakeman.net/virtual/interVil/bfaSaves/19.gif)

---

