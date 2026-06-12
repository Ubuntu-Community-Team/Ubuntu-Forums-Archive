---
title: "Arduino Software"
date: 2009-10-19
forum: The Cafe
---

### Post by lukeiamyourfather on 2009-10-19
I've been messing around with an Arduino lately (open source hardware and software microcontroller). Last night I was thinking it would be cool if the software for the Arduino was available in the repositories for Ubuntu. Where and/or how can I make suggestions about packages for Ubuntu? I've done some searching but can't find an appropriate place to do so. Also are there any other Arduino users using Ubuntu? Cheers!

---

### Post by kpholmes on 2009-10-19
you might be able to create a launchpad account and make a ppa, then add the ppa address to your respiratory list. i dont know the full details on how you would go about doing that but i know you can add other software lists from launchpad to your respiratorys, i had to do that when trying to install drivers on a macbook

---

### Post by 23meg on 2009-10-19
[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by lukeiamyourfather on 2009-10-20
> **23meg said:**
> [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

Thanks for the information! Looks like someone else had the same idea and already submitted the package request. 

[https://bugs.launchpad.net/ubuntu/+bug/230387](https://bugs.launchpad.net/ubuntu/+bug/230387)

Hopefully we'll see it in the next version of Ubuntu, or the version after that. :guitar:

---

### Post by Steveway on 2009-10-20
Well, we allready have avr-gcc and all it's doodads.
That works perfectly together with avrdude for my own ATmega32-Board.
It should also work for the Arduino.

---

### Post by lukeiamyourfather on 2009-10-20
> **Steveway said:**
> Well, we allready have avr-gcc and all it's doodads.
That works perfectly together with avrdude for my own ATmega32-Board.
It should also work for the Arduino.

Its more of a convenience thing really. That way new users don't have to install half a dozen packages manually (that could be handled with dependencies) and modify the IDE to run with Ubuntu (which could already be done in the package). I never said it wasn't possible to use avr-gcc and avrdude but why not take it one step further? I could see this being very handy for many Edubuntu users in computer labs where Arduino is used for classes in addition to the new users like myself. Cheers!

---

