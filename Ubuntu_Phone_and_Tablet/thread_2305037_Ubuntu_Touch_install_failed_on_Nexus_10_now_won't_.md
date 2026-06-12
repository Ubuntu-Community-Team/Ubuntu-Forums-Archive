---
title: "Ubuntu Touch install failed on Nexus 10 now won't boot"
date: 2015-12-02
forum: Ubuntu Phone and Tablet
---

### Post by ahounsome on 2015-12-02
Hi,
I have followed the instructions for installing Ubuntu Touch here -
[http://www.pcadvisor.co.uk/how-to/linux/how-install-ubuntu-touch-image-3531970/](http://www.pcadvisor.co.uk/how-to/linux/how-install-ubuntu-touch-image-3531970/)
Unfortunately I got as far as step 7 and then the Nexus device is now stuck on the loop boot animation (swirly coloured balls). I left it like this for 4 or 5 hours but no joy.
I have powered off and then held down power and volume to get to the screen with the android on it's back and tried recovery, but again, no joy.
I am completely new to Android, so any help would be extremely helpful.
Thanks,
Andy

---

### Post by grahammechanical on 2015-12-02
How does that guide compare with this one?

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

You may need to do this

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/reinstalling-android/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/reinstalling-android/)

Regards.

---

### Post by ahounsome on 2015-12-04
Thanks very much for your help on this. I have successfully completed the flashing of my Nexus 10 to Phablet.
I did this by first restoring the android device with a factory reset. I found the instructions online.
I then followed the documentation you suggested I look at :-

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

However, there is an error in the line of part 3 Install Ubuntu. The line -

ubuntu-device-flash touch --channel=ubuntu-touch/stable/ubuntu --bootstrap

Should actually be -

ubuntu-touch/devel/ubuntu

rather than being in the "stable" directory, the build is in the manta sub directory in the "devel" directory.
I hope this helps anyone else who wants to try Touch on Manta.

---

