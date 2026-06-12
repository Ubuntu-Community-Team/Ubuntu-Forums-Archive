---
title: "keystroke randomly repeatiiiiiiiiiiing"
date: 2009-12-04
forum: System76 Support
---

### Post by EmilyRose on 2009-12-04
Hi there, I'm running Ubuntu 9.10 and have been having this problem for several months now, I've searched through the forums and it sounds like some people have had similar problems with a particular problem, but this happens completely randomly in all programs - Opera, Tomboy, Firefox, OpenOffice, absolutely anytime I type. I push a key down and it randomly repeats for a second or two, and then goes on with the rest of the words (left it inplace in the title, usually I go back and delete all buto ne instance) It doesn't seem to happen with any specific letter more than others. I've tried messing with keyboard settings, without luck unless I just turn off 'key presses repeat when key is held down' entirely, but then it makes scrolling annoying... Sometimes it happens a lot and then won't happen for a while. 

I'm on a gazp5. Any thoughts on how to fix this??

---

### Post by drewbenn on 2009-12-04
This might not be the same cause, but just in case: when I upgraded to 9.04, I noticed a behavior change where keyboard input would pause for a fraction of a second when I used the touchpad after the touchpad had been idle for a little while.  If a key was depressed when this happened, then when keyboard input resumed I would see several keystrokes of that key: as if it had been held down for the entire length of the delay and then released when the delay period ended.  I was able to replicate this by opening up a gedit window, waiting a few seconds, typing nonsense characters as quickly as I could (gaeawgeawge), and then moving the touchpad.  About one in every 5 or 6 attempts would show the repeating keystrokes.

I never found a fix, but did find a workaround: in System | Preferences | Keyboard | General, I increased the "repeat keys" delay so the slider control is right-aligned with the end of the word "is".  I think that added enough of a delay so that whenever the touchpad induced a delay in the keyboard, the delay period would end before the key repeat threshold was reached.

I tried replicating it right now, but was unable to: it's possible that my 9.10 upgrade finally fixed it for me.  Also, I've been using the "proto=imps" option for the psmouse (touchpad) module to get my preferred scrolling method, so that could be having an effect.

[http://ubuntuforums.org/showthread.php?t=1146227](http://ubuntuforums.org/showthread.php?t=1146227)  was the previous thread.

You could be brushing the touchpad accidentally while you're typing.  If you're using an external mouse, or have one that you can use, you can disable the touchpad temporarily to try to verify that: in a terminal, type
```
sudo modprobe -r psmouse
```
To get it back, do:
```
sudo modprobe psmouse
```

Of course you could be having a completely different problem!

---

### Post by EmilyRose on 2009-12-04
You know what, that sounds like exactly what my problem was... and having done as you suggested seems to have fixed it! Thanks!!

---

### Post by jeamer on 2009-12-05
Thanks. I had this issue as well, and just became complacent about it. It was only ever other people using my computer that commented on it. Now she works like a chaaaaaaaaaaaaaaaaaaaaarm..... oh no!



Just kidding. Ha!

Jordan

---

