---
title: "VMWare Player: can't boot into LiveCD for gParted"
date: 2015-05-17
forum: Virtualisation
---

### Post by stupidquestion on 2015-05-17
I ran out of disk space so I need to run gParted at boot up. I'm using VMWare Player, and according to the following link I need to hit F2 on boot up:
[http://askubuntu.com/questions/294889/how-to-expand-the-ext4-primary-partition-size-in-a-vmware-player-virtual-disk](http://askubuntu.com/questions/294889/how-to-expand-the-ext4-primary-partition-size-in-a-vmware-player-virtual-disk)

My problem is it doesn't seem to work, as it just boots up as usual. I did mount my Ubuntu Server .iso file for the CD/DVD drive. I also tried a Desktop version .iso with the same result. 

What am I doing wrong? (The Ubuntu installation disk is the Live CD right, or am I supposed to use a specialized disk?)

---

### Post by stupidquestion on 2015-05-17
The answer: 
> [COLOR=#111111][FONT=Ubuntu]the boot delay is just too short. What you can do to slow it down is go to your vm's .vmx file and type in something resonable like:[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]bios.bootDelay = &#8220;5000&#8221;
for 5 seconds of boot delay.

Also, I think only the Desktop iso had the Live CD.
[/FONT][/COLOR]

---

### Post by fidel5 on 2015-05-19
Did you select the Connect and Connect at power on checkboxes under the CD/DVD ROM settings (second picture from the top on this link: [http://goo.gl/SQ5Wcs](http://goo.gl/SQ5Wcs))

---

