---
title: "need help enable usb boot in Raspberry pi running Ubuntu 20.04"
date: 2020-07-16
forum: Server Platforms
---

### Post by raspberry-noobi on 2020-07-16
Hi all,
I am reying to enable boot from usb on my raspberry pi. it is currently using ubuntu 20.04 os.

but while doing so, i am getting stick in installing pri-eeprom package to change the bootloader. 
i am running =[U][B] "sudo apt install rpi-eeprom"
[/B][/U]
and getting this error

_**E: Unable to locate package rpi-eeprom**_

please find the attached image.

[ATTACH=CONFIG]286476[/ATTACH]

is there a work around it? or is it possible only thorugh Raspbian os?

Thank you.

---

### Post by TheFu on 2020-07-16
raspberry pi questions will probably get much better answers on a pi-specific forum I'm sad to say. [https://www.raspberrypi.org/forums/viewforum.php?f=63](https://www.raspberrypi.org/forums/viewforum.php?f=63)  Folks here are typically desktop Ubuntu users and r-pi devices haven't been good at running those.

Since I know nothing about this package or booting Ubuntu on a PI or booting a Pi using USB storage, I can only say that the error is pretty clear.  Either the wrong package name is used or the PPA with that package isn't configured on the system or it isn't configured correctly.

Have you run **sudo apt update** to refresh the package lists?  People forget to do that after modifying the repos.

---

### Post by raspberry-noobi on 2020-07-16
thank you. appreciate the help.

yes, i did do apt update. but still it is not working. I will post the question over rpi forum.

thanks.:)

---

