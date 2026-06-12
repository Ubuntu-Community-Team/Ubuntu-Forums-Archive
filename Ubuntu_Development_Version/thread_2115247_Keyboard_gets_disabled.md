---
title: "Keyboard gets disabled"
date: 2013-02-12
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2013-02-12
If I'm playing Warcraft 3 with Wine after some minutes/hours my keyboard gets disabled but the mouse still works. Normally I would assume this is a Wine bug but even after closing the application the keyboard is still disabled. The only solution is to reboot the system. Has somebody an idea what is causing this or how I can check this?

---

### Post by grahammechanical on 2013-02-12
Are you using Raring Ringtail? Do you have a 12.04 or a 12.10 install? Does this happen in either of those versions?

Is the keyboard a USB keyboard? Try unplugging it and plugging it back in, either to the same USB port or a different one.

To report this as a bug you need to identify the package that is causing the problem. Use Synaptic Package Manager to identify what packages control USB in each version of Ubuntu and make a note of the version numbers. 

Regards.

---

### Post by Sworddragon on 2013-02-12
> **grahammechanical said:**
> Are you using Raring Ringtail?

Sure, otherwise I wouldn't post here :P


> **grahammechanical said:**
> Is the keyboard a USB keyboard? Try unplugging it and plugging it back in, either to the same USB port or a different one.

Yes, it is an USB keyboard. I will plug it to another port and look if this happens again (this can need 1-2 days because the bug appears randomly on playing (maybe it is some special combination that I'm pressing in the game. Commonly I'm using Alt+F1 for Iconify from Openbox and shift + mouseclick for fast creating buildings)).

---

### Post by GrouchyGaijin on 2013-02-12
> **Sworddragon said:**
> If I'm playing Warcraft 3 with Wine after some minutes/hours my keyboard gets disabled but the mouse still works. Normally I would assume this is a Wine bug but even after closing the application the keyboard is still disabled. The only solution is to reboot the system. Has somebody an idea what is causing this or how I can check this?

Odd because starting a few days ago, I began having the same problem.  My keyboard would lock up.  The track pad still works, but the keyboard is unresponsive.  I have to hard reboot to get it back.  I am not using WINE or playing any games.  The only thing that is different is that I had installed, [Terra is a Python / GTK3 drop-down terminal emulator similar to Guake or Yakuake]("http://www.webupd8.org/2013/02/terra-drop-down-terminal-emulator-with.html").

I uninstalled it today and so far haven't a lock up.  It could be totally unrelated to Terra, but so far it ***seems*** to be related.  Although I wonder, because even prior to installing Terra, I had been suffering from somewhat frequent compwiz crashes.

I'm running 12.04.

---

### Post by Sworddragon on 2013-02-12
I'm not using Terra but I'm thinking that one of these conditions maybe matches:

[list][*]We are pressing any special combination of keys due to the behavior of the applications that is triggering this bug.
[*]The applications itself are doing something that is causing this bug.[/list]

---

### Post by GrouchyGaijin on 2013-02-12
> **Sworddragon said:**
> I'm not using Terra but I'm thinking that one of these conditions maybe matches:

[list][*]We are pressing any special combination of keys due to the behavior of the applications that is triggering this bug.
[*]The applications itself are doing something that is causing this bug.[/list]
I was thinking that it had to do with using the function keys.  f12 in my case.

---

### Post by Sworddragon on 2013-02-12
In my case it could be F1 because I have configured Openbox to use Iconify (minimizing) if Alt+F1 is pressed. But what speaks against it is that it never happened on other applications before on pressing Alt+F1.

I will just play a little more and make a few tests. Maybe this helps to isolate the problem.

---

### Post by Sworddragon on 2013-02-12
The problem appeared again even on another USB port. But I have figured out that the keyboard gets not disabled but the input is delayed for a few seconds. This means that I have to press a key for a few seconds until it responds. I'm assuming I have hit some key combination which activates this behavior. At least replugging the keyboard on the USB port does work as a workaround without rebooting the system.

---

### Post by grahammechanical on 2013-02-13
> Sure, otherwise I wouldn't post here 

I am learning not to assume anything. The other day in another section of the forum I assumed that because the person had recently registered on the forum that they were using either 12.04 or 12.10. So, I gave two sets of detailed instructions. And the OP posted back that he was on 10.04!

I am glad that unplugging and plugging back in the keyboard kind of fixes things. That is what I had to do the other year when I had a similar keyboard problem. That keyboard later became faulty to the point that some keys did not work.

Do not disregard the possibility that there could be a fault with the keyboard. Certain keys could be starting to become unresponsive or not breaking the connection and acting like the key is being held down.

Regards.

---

### Post by Sworddragon on 2013-02-24
The problem also appears if I'm plugging my USB-keyboard with an adapter into my PS2-port. I think I should now open a bug report but does anybody know which package could be affected?

Edit: Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1137481](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1137481)

---

