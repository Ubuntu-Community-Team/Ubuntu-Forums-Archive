---
title: "Lubuntu doesn't detect my laptop microphone"
date: 2020-09-24
forum: Ubuntu/Debian BASED
---

### Post by victo83 on 2020-09-24
Hello,

I recently installed lubuntu on my laptop and also I installed Discord. Today I tried to call someone, but I discovered that my mic is not detected by the OS. What could I do?

Thanks in advance.

---

### Post by scorp123 on 2020-09-25
> **victo83 said:**
>  I discovered that my mic is not detected by the OS. What could I do?


I have the same problem with my office PC. Because I'm one of the local Linux admins I got permission to wipe Windows 10 and replace it with whatever I want... so I went with Ubuntu 20.04.  But surprise: The built-in microphone didn't work, no matter what I tried.  #-o

At first I blamed the Linux version of "Microsoft Teams" ... but I soon found out that it wasn't the culprit. There's some weird BS going on with that soundcard in that office PC and the microphone sound channel is not even detected. I wasted hours and hours trying to troubleshoot that thing, tried setting various boot parameters, blacklisting modules, forcing modules, recompiling things ... Nothing worked. ](*,)

Because fewer and fewer newly released Android phones come with a 3.5mm headphone jack I bought one of these USB-C-to-3.5mm adapters so I could re-use my old headsets and what not ...

[IMG]https://www.picclickimg.com/d/l400/pict/174149701556_/Type-C-to-35mm-Audio-Microphone-Adapter-For-Samsung.jpg[/IMG]

It works tip top on my Samsung phone.....

But aren't modern Android phones basically Linux devices too? :-k  Yes, they are! 
So .... if some USB-C thing works for Android it should also work for Ubuntu 20.04...?  Yes it does! :idea:

So I plugged in that USB-C adapter into the USB-C port on my office PC, I attached one of my headsets to the other end .... And voila, I have everything working now. Ubuntu 20.04 now is convinced there's a "USB Audio" device and the microphone channel on that device is working tip top. I also tested USB-C headphones, e.g. the one that shipped with my Android phone, and that one worked too, instantly.

So I still have no clue why the built-in soundcard refuses to work properly.... but the USB device workaround works well enough for me. 8-)

Since you did not give any details about your hardware it's impossible to say what might be wrong in your case ... But maybe you have one of those USB-C headphones too? Give it a try and plug it into your PC. Chances are it might just work...

---

### Post by guiverc on 2020-09-25
I don't know your issue, and may not be able to help, however the starting point would be your release of Lubuntu, and what software stack you are using.

eg. is it Lubuntu 20.04 LTS using the 5.4 kernel & LXQt desktop?
is it Lubuntu 18.04 LTS with the GA kernel (4.15) & stack & LXDE desktop?
is it Lubuntu 18.04 LTS with the HWE kernel (5.4) & stack & LXDE desktop?
or something else?

Release details at least give us a clue of what you're running.

---

