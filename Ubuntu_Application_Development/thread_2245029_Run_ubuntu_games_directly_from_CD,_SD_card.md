---
title: "Run ubuntu games directly from CD, SD card?"
date: 2014-09-20
forum: Ubuntu Application Development
---

### Post by han5 on 2014-09-20
I have created a UBUNTU game "fps6.desktop" [https://www.sendspace.com/file/pbddio](https://www.sendspace.com/file/pbddio) <----download link to file
As you see the file runs great on UBUNTU desktop, just as good as windows.
[IMG]https://imagizer.imageshack.us/v2/951x560q90/902/sfDWlG.png[/IMG]

By default in  in the property menu > permission of the game the option: "allow executing the file as program"  is activated
[IMG]https://imagizer.imageshack.us/v2/804x506q90/912/q3DeJc.png[/IMG]



The problem starts when I put the file in another directory UBUNTU prevents it from running from other folders then desktop and shouts: "Untrusted application launcher" and refuse to run. 
[IMG]https://imagizer.imageshack.us/v2/936x608q90/674/p7p08F.png[/IMG]

Also note how Ubuntu disables in the property menu > permission of the game the option: "allow executing the file as program", once the game is placed in another directory
[IMG]https://imagizer.imageshack.us/v2/1120x601q90/540/M7GANy.png[/IMG]



Once I put that file back to desktop Ubuntu allows it to run again.
Do I need to convert the game with some program or something to make run from all directories.
My purpose is to run it from SD card or CD directly without installation or use of terminal. Please help to make this click and directly run from CD and SD card.

Thanks in advance

---

### Post by adrian89 on 2014-09-22
The partition "win8" might be mounted as "noexec"(which from what I know it disables applications to be executed from that partition), try editing /etc/fstab to mount with option "exec".

---

