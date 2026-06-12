---
title: "Graphical environment for Ubuntu Server 14.04 on Dell Power Edge T110 2"
date: 2014-05-19
forum: Server Platforms
---

### Post by smbit on 2014-05-19
Hi, all!
I just installed a Ubuntu Server 14.04 on the Dell Power Edge T110 2 server machine.
After installing a gnome-desktop environment I'm experiencing a very slow graphic performance. The system has all updates installed.
Please suggest how can I troubleshoot the issue?

---

### Post by spynappels on 2014-05-19
Apart from the obvious question of why you are running a DE on a server, what do you mean by slow? Are there lags between keyboard presses and what you see on the screen? What graphics are included on the MoBo?

---

### Post by ibjsb4 on 2014-05-19
> After installing a gnome-desktop environment
Which one?  There are several these days :)

If you want to add a minimal gnome desktop to a server install, here is one way:
```
sudo apt-get install --no-install-recommends gnome-session-flashback && sudo apt-get install gnome-terminal
```
I am not sure if xorg is part of the server install or not, may also have to add it.  And you must also add 'xinit' if you wish to use the startx command.

---

### Post by smbit on 2014-05-20
Hey, take it easy, that is my first cup of Ubuntu. ](*,) I decided to install DE because I want to test some vm's on it. Lags between keyboard presses and what I see on the screen that is exactly my issue!!! Also the graphical response is very slow.

Regarding motherboard, that is the output of the lspci for the 'VGA compatible controller'

 04:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04de
    Flags: bus master, medium devsel, latency 0, IRQ 6
    Memory at c0000000 (32-bit, prefetchable) [size=8M]
    Memory at c1000000 (32-bit, non-prefetchable) [size=16K]
    Memory at c0800000 (32-bit, non-prefetchable) [size=8M]
    Expansion ROM at c1010000 [disabled] [size=64K]
    Capabilities: [dc] Power Management version 1

Furthermore, I already installed a Ubuntu Desktop 14.04 on the same machine. And I'm experiencing the same perfomance issues.
If the driver is the issue, how can I find an appropriate driver ?! please advice..

---

### Post by ibjsb4 on 2014-05-20
Ok :) lets back up a bit.

I would still like to verify your DE.
```
echo "$XDG_CURRENT_DESKTOP"
```And you should have a look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by spynappels on 2014-05-20
I wasn't having a go, getting used to a server is (for some) a legitimate use of a DE :)

I'm not sure what the issue actually is, but I suspect that the VGA controller is just struggling with the Unity interface, as you're having the same with a vanilla Desktop install.

Could you try another DE like LXDE or XFCE and see if they work any better? LXDE is the more lightwieght of the two I mentioned.

---

### Post by sandyd on 2014-05-20
Most server graphics cards are not very powerful, it would be better off running a lighter desktop. Openbox is a nice choice when you need a desktop on a server as it has a low memory footprint and is not very graphics hungry

---

### Post by smbit on 2014-05-21
Thank you all! It was really not good idea to install GUI on the server[-X and I found else machine for my purposes.
Thank you all for your suggestions once again, I'm sure I'll try one of them in future.

---

