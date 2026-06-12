---
title: "wake on lan: how to use it?"
date: 2011-01-28
forum: Security
---

### Post by magowiz82 on 2011-01-28
I installed on my android phone an app that should use wake on lan functionality to power on my pc, but I have a doubt : the application asks me the MAC (which is ok) and also the IP, but how can a turned off machine have an IP ? I know this issue is not relative to ubuntu but it's a general networking/hardware issue...

---

### Post by artie_effim on 2011-01-28
pretty self explanitory in the wiki [http://en.wikipedia.org/wiki/Wake_on_lan]("http://en.wikipedia.org/wiki/Wake_on_lan"), read also [http://ubuntuforums.org/showthread.php?t=234588]("http://ubuntuforums.org/showthread.php?t=234588").

---

### Post by uRock on 2011-01-28
The network interface card, hardwired not wireless, is listening even when the PC is turned off. It will need to be set statically, so that it always has the same IP.

You will most likely have to make some adjustments in BIOS for that app to work.

---

### Post by Jive Turkey on 2011-01-30
In my case the IP address for that command from the terminal is the Bcast address as reported by the ifconfig command on your computer.  I don't have an android phone to test it but maybe try that.  

If sending from outside your LAN you might need to forward port 9 to that machine and use your router's actual IP address.

---

