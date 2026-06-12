---
title: "Ubuntu 9.04 on an HP dv4"
date: 2009-04-27
forum: Ubuntu Studio
---

### Post by systemOAD on 2009-04-27
[-o< hello everyone. i need some help with my ubuntu installation. i have used ubuntu gutsy on my old lenovo before and everything worked out flawless. now i installed jaunty on my new hp-dv4 laptop and there are several problems. **first of all** the sound doesnt work. i tried SEVERAL options such as editing the /etc/modprobe.d/alsa-base file and even installing alsa 1.0.19. the sound still doesnt work. **second problem is** that my 'quick touch' buttons do not correspond to the actual control. for example, when i press the mute button, the display comes with the the 'X' across the speaker but the speaker icon in the panel is still at full volume. (not the the sound is working mind you). **third of all**, my funciton keys arent working. i cant increase the brightness using fn+f8. **also**, when i put my machine in standby, and i open my laptop lid, my entire computer freezes and there is no response until the press and hold the power button to shut down. so **please please please** someone try to help me out before i lose faith. i have spend several hours upon hours trying to fix the problems (especially sound) but its just not working. so **someone PLEASE HELP ME. **

---

### Post by systemOAD on 2009-04-28
anyone? please...

---

### Post by markbuntu on 2009-04-28
Did you try

enable_msi=1

that's what dv4 users have reported to work with these machines

dv4-1120us
dv4-1124nr
dv4-1124cl
dv4-1150
dv4-1000ea
dv7

don't forget to reboot....

You need to set the controls for your buttons by selecting the proper device in System/Preferences/Sound/default Mixer Tracks. 

You can go here once your sound is sort of working to get it all dialed in

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

The other stuff i can't help you with.

---

### Post by systemOAD on 2009-04-29
thanks for the help markbuntu. i ll try it out.

---

