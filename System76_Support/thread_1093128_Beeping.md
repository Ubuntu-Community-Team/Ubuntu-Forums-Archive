---
title: "Beeping"
date: 2009-03-11
forum: System76 Support
---

### Post by flukeairwalker on 2009-03-11
Sometimes my Pangolin makes annoying beeping sounds. I think they're called system beeps. For example, when I shut down or a key gets stuck. Anyway, it's kind of annoying and I'd rather be rid of it. What can I do?

I think I should mention it only started after I reinstalled the BIOS.

---

### Post by jolx on 2009-03-11
[this thing right here]("http://ubuntuforums.org/showthread.php?t=531781&p=3231687") should work :)

---

### Post by thomasaaron on 2009-03-11
It is a known, latest-greatest feature. Everybody wanted it in previous versions of Ubuntu, so devs put it in. However, there was no way to disable it.

I've not seen that before, but Jolx's suggestion just might work. However, you might want to make sure it doesn't hose sound elsewhere.

---

### Post by flukeairwalker on 2009-03-15
The beeping hasn't stopped with the suggestion from jolx. Whenever I backspace or shut down the computer the beeping happens, and it even happened for about 10 seconds straight yesterday. Is there really no way to disable this? There are times when I need to keep my laptop quiet, and having it beep like that is really not helpful.

---

### Post by 3Miro on 2009-03-15
> **flukeairwalker said:**
> The beeping hasn't stopped with the suggestion from jolx. Whenever I backspace or shut down the computer the beeping happens, and it even happened for about 10 seconds straight yesterday. Is there really no way to disable this? There are times when I need to keep my laptop quiet, and having it beep like that is really not helpful.

Are you sure this was the system beep? Without realizing it, I had the microphone on on my laptop and when I close the lid, there was horrible effect between the mic and the speakers resulting in 5 - 1 second beep that can be mistaken for system beep.

---

### Post by flukeairwalker on 2009-03-16
I've had that one happen before! :D At first I thought it was some type of alarm but I figured it out pretty quick. No, I'm certain it's not the mic. I went into the system utilities at startup and disabled a setting there, but it doesn't seem to help. If nothing works then I guess I'll just have to apologize for having a noisy computer.

---

### Post by thomasaaron on 2009-03-16
Check the sound controls in System > Preferences > Sound.
Also, open a terminal and go to Edit > Profiles. See if your Terminal beep is enabled there.

---

### Post by flukeairwalker on 2009-03-17
So I looked through those options as you suggested and deselected anything that seemed like it might have to do with the system beep. While it seems to have taken care of most beeping circumstances, the computer still beeps when I shut it down. I guess I can live with that one instance, though I'd rather not have to. Thanks for your help so far, you've been very understanding.

---

### Post by dje on 2009-03-17
try the [tutorial here]("http://www.debuntu.org/how-to-turn-off-virtual-console-beep"), make sure you follow it all (ie. not just the first command)

dje

---

### Post by bubba_169 on 2009-03-17
Have you tried "sudo rmmod pcspkr" in a terminal to unload the module that controls the internal speaker? Also make sure in the last tab of System->Preferences->Sound that the alert checkbox is not ticked. It worked for me...

---

### Post by flukeairwalker on 2009-03-17
I tried the code, and I got a "command not found" on the second piece. Hopefully that I wasn't able to complete the instructions won't screw things up?

---

### Post by dje on 2009-03-17
> **flukeairwalker said:**
> I tried the code, and I got a "command not found" on the second piece. Hopefully that I wasn't able to complete the instructions won't screw things up?

it won't screw things up but i means that once you reboot the beep will be back. Read the tutorial again, what looks like a second command isn't a command, if you read the paragraph above it says to add it to the mentioned file ;)

you can edit the file with the following command:
```
gksu gedit /etc/modprobe.d/blacklist
```
then add this line to the bottom:
```
blacklist pcspkr
```
then save and close the file, done!

dje

---

### Post by betrunkenaffe on 2009-03-17
Best answer I've seen to this issue was a command someone on these forums gave which allows you to change duration, volume and I believe pitch of the system beeps.. So you can keep the beeps and not have them piss you off

---

### Post by flukeairwalker on 2009-03-18
dje, thanks for clearing that up. I don't know why I didn't read that part. My Ubuntu-fu is still white belt ^_^

---

### Post by thomasaaron on 2009-03-18
> So I looked through those options as you suggested and deselected anything that seemed like it might have to do with the system beep. While it seems to have taken care of most beeping circumstances, the computer still beeps when I shut it down.

I'm not finding a way to stop that one. It may be at the BIOS level.

---

### Post by flukeairwalker on 2009-03-19
dje, using your code seems to have fixed all the beeping. Thanks!

---

### Post by silvertuna on 2009-06-24
dje #12 did not stop the low battery beeping for me. It did stop the backspace beep. I've tried everything in this and other threads and have been unable to stop the low battery beep. I saw a post that this feature was fixed in Intrepid but it doesnt look fixed to me.  I'd love to get rid of it.  Pan4 64-bit Jaunty.

---

### Post by silvertuna on 2009-06-25
Possible solutions appear in this bug thread - 

EXCERPTS - 
[https://bugs.launchpad.net/ayatana/+bug/77010](https://bugs.launchpad.net/ayatana/+bug/77010)

xset - 
To change the volume / pitch, use `xset b 30 500`. The first number is the volume, in percentage, and the second is the frequency in hertz. See `man xset` for more info.

gconf -
There is another bug, #290204
He wrote:
"An upgrade to Intrepid has re-enabled the 'bell' or 'beep' when clicking 'Shutdown' or at the login screen. There is no way in the GUI or standard Gnome settings to reset this (none that work, anyway). The only way to disable it again is:

run gconf-editor from terminal and set
/desktop/gnome/peripherals/keyboard/bell_mode
to 'off' rather than 'on'

Not exactly easy to find for your experienced users, impossible for the average user. At the very least this should setting should be migrated during an upgrade, but should really be editable from the Sound properties tab."
([https://bugs.launchpad.net/hundredpapercuts/+bug/290204/comments/12](https://bugs.launchpad.net/hundredpapercuts/+bug/290204/comments/12))

This setting should be made in Audio-configurations! I am sure this can be fixed in 100 paper cuts!
END EXCERPTS

It looks like xset be used to disable the beep?
[http://www.linuxmanpages.com/man1/xset.1x.php](http://www.linuxmanpages.com/man1/xset.1x.php)

I will try these later today.

---

### Post by silvertuna on 2009-06-25
None of the fixes i just posted worked.

---

