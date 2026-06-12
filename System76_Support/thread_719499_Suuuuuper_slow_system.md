---
title: "Suuuuuper slow system"
date: 2008-03-09
forum: System76 Support
---

### Post by EmilyRose on 2008-03-09
So, I don't know whats up with my Gazelle (bought last oct... not sure which vs...). I've been trying to get a usb-serial cable working (without success...), so that I can get online again (my usb modem broke, and I'm trying to be cheap, though atm that means I'm freezing in the basement...), and now the whole system is running SUPER slow. From the time I boot up to opening just one program takes at least 8 or 9 minutes. 

It first hangs on CUPS system during bootup for 1-3 minutes-ish then proceedes to the bootup menu at normal speed. I type my username/pw in and then I sit for upwards of 5+ minutes while it slowly loads my desktop - nothing at first but a cursor, then background then icons, then menus, etc. Between each of these things loading there is nothing going on, during 1-3 minutes. Its ridiculous. Once everythings loaded, it will take another minute to load every single program, minimum. If I close the program (terminal for example) and then try to open it again, I have to sit and wait a minute again. 

I've stuck system monitor on my panel to see if somethings working super hard, but its not. CPUs stay at 4-15% working the whole time. Its bizzare. I've tried rebooting several times without succes. Log out works fine, but login takes another 5+ minutes. 

Does anybody have any idea as to wtf is going on to make it run SOO god damn slow?

---

### Post by Bölvaður on 2008-03-09
I am sorry that I am not sure on what is wrong, but my best guess is that it has something to do with USB. I've noticed when I have USB cable plugged in (perhaps with digital camera on the other end, but that is not turned on) it makes the bootup a lot slower.

If you are able to turn the USB ports off, you might want to check if that would help. But don't expect too much of a newbie like me :)
You still have your 1 year warranty haven't you?


> **EmilyRose said:**
> I've tried rebooting several times without succes

If you make no changes between the restarts, you should not expect any improvement.

---

### Post by thomasaaron on 2008-03-10
Well, the two places to start are:

1. After a slow boot-up, email the output of: cat /var/log/syslog
Maybe that will revewl something.

2. While you have the computer on, go to Applications > Accessories > Terminal
and run this command: top
Now, open an application, which should open very slowly (right?). Watch the terminal and see what is hogging the cpu time when the program is opening.

It definitely sounds like something is hogging your memory pretty badly.

---

