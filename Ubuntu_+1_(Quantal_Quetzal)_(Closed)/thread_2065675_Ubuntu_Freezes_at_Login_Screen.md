---
title: "Ubuntu Freezes at Login Screen"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mmasroorali on 2012-10-02
Dear All,
I have already made a post ([http://ubuntuforums.org/showthread.php?t=2065511](http://ubuntuforums.org/showthread.php?t=2065511)) and got some excellent suggestions. However, the issues have become a bit scattered and not everybody will have the patience to read thoroughly among all the posts (no offense intended). But I need an answer.

Today, after a partial upgrade (hard reboot at midpoint) to 12.10 from 12.04 the machine freezes at login screen. The machine boots fine, the login screen appears, it says that there is not wired network and I am disconnected and then there is no keyboard and mouse. 

My steps so far,
[LIST=1]
[*]While booting with an old version CD, I made grub to appear (hold shift). At the Grub menu I selected the kernel that I wished to boot and pressed the letter 'e' that let me edit the Grub script for loading that kernel. I found the line that has "ro quiet splash" towards the end of the line and replaced "quiet splash" with "nomodeset" without the quotation marks. The machine then booted to login screen and froze. Nothing happened when I pressed Ctrl-Alt-F1. The machine can not be called to have hanged since the CD eject button works.
[*]Same as the previous one but tried "text" in place of "nomodeset". The text login screen appeared, and again, no keyboard, no mouse.
[*]At the login screen, detached the USB mouse and keyboard and plugged them back in, no improvement.
[*]Tried the recovery mode from grub, the second (text look) menu appeared with a number of options. Then the keyboard froze. Nothing happened with up-down arrow key or Enter. I have tried *each and every* key plus those two/three key combinations in keyboard.
[*]Anything to do with that disconnected LAN message? But that is weired. Tried booting the machine with the network cable disconnected. No change. 
(I see that in 12.10 the network icon is appearing *before* login, previously, it has appeared *after* login. )

(A disconnected LAN message may appear for my connection when the MAC address does not match with the one approved from ISP.)

[/LIST]



So, as you can see, I could try those many suggestions with the commands which I can Google. But for all these you need to login or at least get a terminal prompt.

I want to wait half a day more before I go through the painful (and lossy) process of fresh installation from CD.

Any suggestion will be more than appreciated.

---

