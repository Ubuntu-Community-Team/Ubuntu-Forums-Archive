---
title: "[SOLVED] daru2 gutsy wireless/compiz"
date: 2007-10-20
forum: System76 Support
---

### Post by poetbeware on 2007-10-20
Upgraded to gutsy, which was a whole big ordeal in and of itself (shouldn't the Upgrade button do something Bittorrent-like so we don't have 8 bytes per second download rates? Oh never mind) and now nothing works.

1. Wireless is simply dead. It doesn't appear as an option on the taskbar. Pressing the wireless button has no effect.

2. Isn't a selling point of gutsy that it comes with 3d accelleration turned on by default? Because it's not, and going under System/Preferences/Desktop Effects yeilds a message "Desktop effects could not be enabled."

Can anyone help? #1 urgent, as I use this laptop at work and need to be mobile. I reactivated the system76 repository and installed the latest system76 driver like the wiki said.

-Paul

---

### Post by tedrampart on 2007-10-20
for the compiz issue.. here's a workaround: [http://ubuntuforums.org/showpost.php?p=3464235&postcount=33](http://ubuntuforums.org/showpost.php?p=3464235&postcount=33)

for wireless/networking..what happens when you try the commands:
"sudo killall NetworkManager" ..followed by..
"sudo NetworkManager"
?

---

### Post by poetbeware on 2007-10-20
Thanks for getting back to me... I tried the commands you listed, but nothing changed. The wireless options still don't appear in the drop-down. :(

Any other ideas?

---

### Post by poetbeware on 2007-10-21
The gutsy upgrade helpfully selected a random kernel to boot instead of the kernel it had just installed. I was using an old low-latency kernel I had attempted to see if some multimedia applications would run better. I stopped using the low-latency kernel because it interfered with wifi then forgot I had it installed. Luckily I did a uname to see if gutsy's kernel was compatible with the ipw3945 driver that the Darter's wireless chip seems to want.

I had to edit /boot/grub/menu.lst to make the gutsy kernel the default one, and now wireless is working properly again.

The upgrade seems to have erased all my wifi network passwords, which is annoying, but otherwise I'm happy. 

Oh! And thank you tedrampart, the link you provided got compiz working too.

-Paul

---

