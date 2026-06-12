---
title: "Final fantasy viii cursor always moves up"
date: 2009-05-26
forum: Wine
---

### Post by themusicalduck on 2009-05-26
I'm having a couple of problems running FF8 on wine. Firstly when I get to the first menu, the cursor will continuously move up, as if I'm holding onto the up key. Secondly, I can't seem to make it work in fullscreen. I can set it as fullscreen in the ff8 config program, and set it to use a virtualdesktop but it still only appears as a small box in the top left.

The cursor selection problem also happens in game Alex the Alligator 4 which is native to linux and in the repository.. but it hasn't happened in any other native or wine program.

Most reports on this game seem to be that it works fine, so seems like something weird is up for me here.

I'm using Jaunty 9.04 and wine 1.1.22.

---

### Post by doas777 on 2009-05-26
FFVIII was released on PC? 
I usually get my FF fix via emulators myself, but just like wine, there are often unfixable annoyances. just pray they're not showstoppers.

---

### Post by themusicalduck on 2009-05-26
It was released on PC, FFVII was too. Not the best of ports but still better than an emulator.

Then again if I can't fix this cursor problem then an emulator might be the next best option.

---

### Post by themusicalduck on 2009-05-27
bump

---

### Post by themusicalduck on 2009-05-28
final bump :(

---

### Post by mikezila on 2009-05-28
Are you playing with a gamepad?

Can you control the pointer with the mouse?  Not are you trying to, do you have the option?

Are you using compiz?

---

### Post by themusicalduck on 2009-05-28
I'm not playing with a gamepad, only the keyboard, though the option is there. I was hoping to disable or change the bindings for the gamepad incase it was misreading something but the option doesn't seem to be there.

Pretty sure it can't be controlled by the mouse. There aren't any options about it anyway. Then again it does seem to take control of the mouse when I run it..

Having compiz on or off makes no difference.

---

### Post by mikezila on 2009-05-28
Go to the wine config and see if changing "allow the window manager to control the windows" fixes things.  Also, turn "allow the window manager to decorate the windows" off if it's on.

This has fixed many game-related problems for me in the past.

---

### Post by themusicalduck on 2009-05-28
Doesn't seem to have helped :(

---

### Post by mikezila on 2009-05-28
I'll download the demo and see if I can reproduce this problem and find a way to fix it.

Stand by...

---

### Post by mikezila on 2009-05-28
I've installed the demo, but I can't reproduce your problem.  I've tried all of the options at various values, but nothing seems to cause your trouble.

What settings are you using using FF8Config?

---

### Post by themusicalduck on 2009-05-29
Well I seem to have found the problem..

Basically I recently tried another called yofrankie, but I couldn't control it at all. Looking at the options it listed the controls as 'joystick' and they couldn't be changed.

I did a bit of search about joysticks on ubuntu, downloaded a program called joystick calibrator from the repos and sure enough it lists me as having a joystick. The joystick is listed as /dev/input/js0, Microsoft Digital Media Pro Keyboard.. as in my keyboard.. which you can probably guess.

So it seems like my imaginary joystick had taken over all games with a joystick input as an option.

I'm not actually sure what I did to fix it.. I fiddled with some controls on my keyboard and also fiddled with some stuff on the calibrator program. This definitely seems to be a bug though. Ideally I'd like to disable joystick support so as to not cause problems with any other programs. Is there a good way to do this?

---

### Post by mikezila on 2009-05-29
Now that I'm not sure about.

---

