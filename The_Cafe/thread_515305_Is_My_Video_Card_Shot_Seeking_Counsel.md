---
title: "Is My Video Card Shot? Seeking Counsel"
date: 2007-08-01
forum: The Cafe
---

### Post by Chickencha on 2007-08-01
I have a strong suspicion that my video card may be shot.  I'm basically just seeking a second (or third, or fourth, or whatever) opinion.  I'm posting this here, rather than, say Multimedia & Video, since this isn't, strictly speaking, an Ubuntu problem.

Here's the story: the other day I went to use my computer and woke it up from sleep when I noticed that it had some annoying graphical glitches going on.  I figured it was some obscure Linux video problem and didn't think too much of it and turned off the computer.  The next day, I booted up and noticed similar issues with a few boot up screens.  So I decided to boot into Windows to see how things looked there (yeah, I dual boot).  Same deal.  I tested all my video connections and no dice.

The nature of the display glitches can be seen in the attached screenshot.  It's basically green and magenta lines down the screen, but it only happens in certain areas and seems kind of "banded."  (As in, it'll happen consistently in several certain vertical sections of the screen and never happen in other sections.)

The fact that I'm able to take a screenshot tells me that it's probably not a monitor problem.  I am a little worried that it could be a motherboard problem, though.  I do get a strange error when I'm booting up that I've never seen before.  (I can't remember it offhand, but I'll try to write it down next time I boot.)

Here's some further information about my system:
ATI Radeon 9800XT (with fglrx driver in Kubuntu)
MSI K8T800 NeoMotherboard

My case does have a tendency to run sort of hot, but still not terrible.  Further information can be provided upon request.

Anyway, is my video card shot?  Does anyone have any suggestions on what to do to try to fix the problem?  If this is probably an unfixable video card problem, does anyone have a good suggestion for a new one?

---

### Post by bread eyes on 2007-08-01
Well, it's most probably a hardware issue. I'd guess it's the motherboard.

---

### Post by Turboaaa2001 on 2007-08-01
Most likely its NOT the Motherboard, I say that of course until I can see that error you get. 

If possible try another video card. It can be a PCI, AGP, PCIx, or PCIx16 card. Preferably use the same interface in the same slot if you can.  If you get the same problem then it's the Motherboard, if not then it's the card.

EDIT:

The only video problems you should get from your Motherboard are if you use integrated video. You are using a video card.

---

### Post by Chickencha on 2007-08-01
I went ahead and rebooted to see what the error was.  It's:

Serial_Ch1 Master: No Device

That worries me, since it doesn't seem like that would be related to my video card.  And I'm *fairly* sure it wasn't there before, but maybe I'm just now noticing it because I'm having problems.

Edit: I'll try another video card when I get the chance, but that may not be for a while since it's a fair amount of work to be digging around that deep inside the case.  And I'd need to scrounge up another card to try.

---

### Post by bread eyes on 2007-08-01
> **Turboaaa2001 said:**
> Most likely its NOT the Motherboard, I say that of course until I can see that error you get.

If possible try another video card. It can be a PCI, AGP, PCIx, or PCIx16 card. Preferably use the same interface in the same slot if you can. If you get the same problem then it's the Motherboard, if not then it's the card.

EDIT:

The only video problems you should get from your Motherboard are if you use integrated video. You are using a video card. 

That's not true.

> **Turboaaa2001 said:**
> Most likely its NOT the Motherboard, I say that of course until I can see that error you get.

If possible try another video card. It can be a PCI, AGP, PCIx, or PCIx16 card. Preferably use the same interface in the same slot if you can. If you get the same problem then it's the Motherboard, if not then it's the card.


Remember it was sleeping before making it unlikely that the video card got shot. Besides, broken video cards usually make it look funkier than that.

---

### Post by Turboaaa2001 on 2007-08-01
I'm not going to debate with you, but I see that you have no idea what is happening to his computer because you have offered no help.

Back to the problem:

The error message is saying that there is no devices attached to the Channel 1 Serial Interface.  So it's not a problem if all your drives are working.

I still think the problem is your video card. If it was the motherboard you would be having more problems than this.

Try these:

1. Shutdown the computer.
2. Unplug power from both the Monitor and Computer.
3. Unplug the video cable from both the monitor and computer if possible.
4. Take out the video card and place it back in (this is re-sitting)
5. Plug everything back in and boot-up.

If this does not work then:

1. Install the latest BIOS. Get it from [http://www.msicomputer.com/support/bios_result.asp](http://www.msicomputer.com/support/bios_result.asp)  If you need help let me know.

and if that does not work:

1. Reset the BIOS by either unplugging it and removing the battery on the motherboard or using the jumper.

Hopefully this will give you something to try before buying a new card (save some cash hopefully)

I will say that I have 8 - 10 years experience in PC repair and have attended college for it. It's up to you to decide who to listen too.

---

### Post by Chickencha on 2007-08-01
> **bread eyes said:**
> Remember it was sleeping before making it unlikely that the video card got shot. Besides, broken video cards usually make it look funkier than that.

That's true, but the screensaver was on before it went to sleep and it wasn't as if I was actively watching what happened the whole time.  It could have happened at any point before sleep.  I do appreciate your thoughts, though.

I'll try the suggestions, although I've already checked most of the connections to make sure they're okay.

---

### Post by handy on 2007-08-02
Definitely hardware.

I have seen multiple graphics cards go down that displayed fine lines  across the screen, all  those that I can remember had the lines horizontal not vertical?  In some of these older cards I could replace the video ram & it fixed them, it was caused by a failed video ram chip on the graphics card.  These days everything is soldered on, so you won't be able to swap out the ram.

Easiest diag' is to borrow another graphics card & install it, that will tell you a great deal.  If it is on board, hopefully you have a graphics slot as well.  You will have to turn the on board chip off in the BIOS under those circumstances.

Out of interest, does windows show the same lines in the same location?

---

