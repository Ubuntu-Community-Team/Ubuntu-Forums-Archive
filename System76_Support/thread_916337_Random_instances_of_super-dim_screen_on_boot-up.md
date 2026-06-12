---
title: "Random instances of super-dim screen on boot-up"
date: 2008-09-10
forum: System76 Support
---

### Post by Caeliferum on 2008-09-10
Hi there! 

I've got previous model of Pangolin Performance, the one with the 8600M GT. I haven't made any altercations to the system aside creating a Windows partition for a dual-boot setup. Usually, everything's dandy. However, sometimes when the laptop boots up the screen is incredibly dim, almost black. =( It'll light back up either once Ubuntu has loaded (or a few mins after) or after a few immediate restarts. 

Moreso, this situation is almost guaranteed if I had been just gaming on the laptop not too long before (using the Windows partition). 

I should also note that even the initial BIOS screen is dim when this phenomenon occurs.

At any rate, thanks in advance for looking into this. =3 I'm eager to solve this as its proven to be a bit of an annoyance.

---

### Post by swegner on 2008-09-10
If you mention that it happens most often after gaming on Windows, then it may be due to a setting for Windows or some power management software running on Windows.  Check to make sure the screen isn't dimming automatically when you shut it down.

It may also be worth checking for a setting in your BIOS?

---

### Post by Caeliferum on 2008-09-10
Well, I haven't seen anything in the BIOS for that. Also, this also happens inbetween Ubuntu sessions without Windows activity, and seeing as the GRUB/Ubuntu section is dominant/boot I would think that any settings in Windows would have minimal effect on the overall system.

That said I'll do a thorough check of the Windows partition for any such power management features asap. =)

---

### Post by swegner on 2008-09-10
I wouldn't normally blame Windows, but I have heard of Windows drivers messing with other hardware settings across sessions (particularly, WakeOnLan settings).

Aside from that, I'm not really sure what the problem might be.  :-/

---

### Post by Caeliferum on 2008-09-11
Well, its not on the Windows side. Now the dim screen problem is occuring more often though. Every other boot up at the least.

---

### Post by thomasaaron on 2008-09-11
If you are certain it is happening in the pre-boot BIOS or posting screens, then the problem most likely is hardware related. Can you use your Fn-F? keys to change the brightness prior to booting?

You may need to contact me via email so I can check the status of your warranty.

---

### Post by Caeliferum on 2008-09-11
Oh I've tried that maaaaany times. Doesn't seem to do a thing. =/ I'm guessing it is a hardware problem then. Using ATITool my GPU temp comps up as 68 degrees when idle. (It doesn't feel all that hot to me though, but I did buy an external cooling pad anyways) I'm wondering if that is having an effect.

Anyways I bought the laptop this summer, but I'm using it for school so I probably wouldn't send it in until December unless the problem becomes permanent or the GPU fails on me.

---

### Post by glacialfury on 2008-09-30
I've just started having this problem as well, in the last week.  It occurred several times before I added a Windows partition, so it can't be Windows-based, but it certainly has increased in frequency lately.  Basically, when we say dim, the screen is so dim that at first I thought the screen was completely broken.  It was only after peering at it for a few minutes once I was able to make out the shadow of the login box, and I knew I was actually at the login screen.

When you log in to Ubuntu from the blackened screen, the brightness is restored.  When you force-power down the laptop from the login screen, and reboot it that way, sometimes it's better, sometimes it isn't.  

The easy short-term fix is to press control-alt-backspace from the login screen - this always restarts it with the brightness at normal.

The real annoyance though, is that while I can wait until GRUB puts me at the Ubuntu login screen, if I want to boot into Windows I can't see the GRUB screen and thus I literally have to guess when I'm at the GRUB screen to change to the other OS.

It is occurring roughly 1/4 to 1/3 of the times I boot the computer, and seems to be gradually increasing in frequency.

---

### Post by thomasaaron on 2008-09-30
This was a bug with Hardy. I knew of it happening on *some* of the DarU1 laptops.

Glacialfury, what are your system specs?
Also, are you running a variant of Ubuntu?

---

### Post by glacialfury on 2008-09-30
I'm on the SERP4.  I dual-boot Ubuntu 8.04 and Windows XP SP2. I'll update my post in this thread as it happens.  

Last occurrence: I was in Windows; the screen turned off from being idle for too long.  I couldn't bring the image back; the computer was running, and I could execute commands (those I knew from keyboard shortcuts), but the picture wouldn't come back.  I pressed the power button, which initiated the Windows shutdown sequence.  I left the laptop for about half an hour, came back to turn it on again, and the screen was dark.

Since my GRUB only has two entries on it, I can select which one I want without seeing the screen (it's either up=linux or down=windows); I started Windows, but the screen brightness was not reset in loading.  I rebooted to load Ubuntu, it was dark, and I did the control-alt-backspace trick which gave me my screen back.

Could this have something to do with the *hardware* or BIOS - not Hardy's kernel - having problems with suspend or hardware triggered screen restoration?  If it continues at this rate, it will essentially cripple the computer.  It's only a few months old.

Model is an FL92.

---

### Post by thomasaaron on 2008-10-01
OK, thanks.

Does this occur in the BIOS, or prior to Grub?
And how often is it happening?

---

### Post by glacialfury on 2008-10-01
It occurs prior to GRUB.  When it happens, it's basically:

1) Turn on computer
2) Hear the fans doing their whizzy thing
3) Check to see if screen is dead

There's literally no picture; if you've got the perfect angle, you *might* see the shadow of the screen behind it, so it *is* working, but brightness is at phenomenally low levels.  The screen just looks black.

The last time it happened was after a normal, uneventful shutdown of Ubuntu.  The screensaver had not run at all and there was no activation of power-saving features during that session. 

I tried pressing Function F5 (increase brightness) during the GRUB/pre-login screen loading; no change during that; however, the brightness was normal *at* the login screen once it loaded.

Summary so far:
 - darkness is random but frequent; probably 1/3 of all boots
 - it occurs immediately on system power, before you see the Phoenix BIOS logo, and persists until X is restarted (on Ubuntu).
 - occurs after both clean Ubuntu and clean Windows shutdowns
 - does not seem to be tied to the (separate) incident of the screen not coming back after suspend/hibernate/etc
 - can be immediately remedied from any point at login screen and after by restarting X with control-alt-backspace
 - can be delayed-remedied by using Function-F5 to increase (change?) brightness, but it won't actually take effect until the Ubuntu login screen, regardless of when you press it during system boot.

EDIT: Occurred again, tried a different experiment regarding Fun-F5.
 - Previously I had pressed Fun-F5 while it was booting, before reaching the login screen.  This time I tried pressing it after it had reached the login screen (well, I assume I was there, I couldn't see anything :p).  No effect.  Had to correct it with control-alt-backspace.

---

### Post by thomasaaron on 2008-10-02
OK, thanks for the great summary.

So, this item...
> - it occurs immediately on system power, before you see the Phoenix BIOS logo, and persists until X is restarted (on Ubuntu).
...is really the most important symptom.

It sounds like a hardware issue to me - like the graphics chip isn't firing up until its warm (although it could be something else entirely).

Let's try a two more things before blaming the graphics card or the LCD backlight or something like that. (Does wiggling your LCD make any difference?)

First, if you feel comfortable doing it, you should re-seat all of your components, but especially the memory cards and the hard drive.

Second, I'd like for you to run memtest86 overnight - six or seven passes minimum. You said earlier that you only had two entries in grub. If memtest86 isn't there, you can run it from a live cd.

If those don't fix/explain it, I think it's time to call it in.

---

### Post by glacialfury on 2008-10-02
If you can wait a few days, I might be able to try some of that over the weekend; I have a test tomorrow ;-)

I do have memtest available, I just commented out all the stuff I don't use in GRUB; easy enough to comment back in.

Just so I'm clear what I'm doing though, what is memtest supposed to do?  Does it leave output you need me to collect for you?  I don't know what it normally does so I won't be able to tell if it does something different.

---

### Post by thomasaaron on 2008-10-02
Memtest86 tests your memory cards. If it throws errors, you probably have bad cards, or some other bad memory-related hardware: card slots, etc...

It is pretty self-explanatory once you fire it up. It runs a number of different tests on your memory cards and has a column that will turn red if there are errors.

It really doesn't matter WHAT errors it throws. If it throws ANY errors, that will tell us the problem is memory related.

But try re-seating components before running memtest86. That way we know that nothing has gotten jarred loose or something.

---

### Post by glacialfury on 2008-10-06
OK: weekend's results.

1) I did not adjust the seating of the hardware; I simply forgot to do it before running memtest.

2) I ran memtest overnight, for a total of about 8 1/2 hours.  I think it ran about 9-12 iterations/tests.  No errors.

3) It has not occurred over the weekend; probably been through about 6-7 boot cycles.

---

### Post by AlchemyMan on 2008-11-13
Just want to say, I think I have the same issue, though I didn't realize it was a dim screen...I thought it was just a dead screen and have just posted about it [here]("http://ubuntuforums.org/showthread.php?t=980608") as well. I guess that makes three of us thus far...this can't be just something jarring loose then, can it?

---

### Post by AlchemyMan on 2008-11-13
I also ran memtest for a couple of passes (I think three). I wasn't too comfortable reseating the hardware, however. In any case, no errors were returned.

---

### Post by thomasaaron on 2008-11-13
This thread is getting a bit difficult to follow. I'm not sure what all models I'm dealing with and if all of the symptoms are the same.

Some general rules:

1. If the screen is dark at the manufacturer splash page, or you have a flashing cursor prior to the manufacturer splash page, it's *probably* a hardware problem. Re-seating things: particularly the memory and hard drive are a good first step. Re-setting the cmos is another good thing to try. If those steps don't work, we probably need t bring it in for repair.

2. If you end up with a blinking cursor after the splash screen, you're probably not finding grub. This can be intermittent. In my experience, about the only thing that has fixed this for me is a clean re-install.

3. If your screen is un-adjustably dim in the OS, boot from a live CD. If it's un-adjustably dim there too, it's *probably* hardware.

4. There was a bug in hardy that causes some computers to be dim in the OS, but it's adjustable. 

If you fall into category 1 or 3, consider emailing me at support.
If you fall into category 2 or 4, try re-installing or upgrading to Intrepid.

If you fall into none of those categories, create a new one! :lolflag:

---

### Post by glacialfury on 2008-11-13
For whatever reason, this error stopped occurring to me around when I last posted about it.  I didn't change anything, at least nothing that I recall - it just stopped happening.  Regardless, I'm grateful.

---

### Post by thomasaaron on 2008-11-13
I forgot to mention -- jiggle your lcd and see if you can make the problem recur. If you can, it's a hardware issue.

---

