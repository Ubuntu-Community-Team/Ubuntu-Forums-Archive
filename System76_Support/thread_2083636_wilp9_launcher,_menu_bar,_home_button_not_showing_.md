---
title: "wilp9: launcher, menu bar, home button not showing after upgrade to 3.5.0.18"
date: 2012-11-13
forum: System76 Support
---

### Post by jaezcurra on 2012-11-13
[FONT="Arial"]Hi, My Wild Dog Performance (wilp9) came with 12.10 and 3.5.0.17 kernel.  Everything was 100% OK until I upgraded to 3.5.0.18.  Since then I have to boot from 3.5.0.17, as launcher, menu bar, home button have disappeared from desktop.
Any suggestion?[/FONT]

---

### Post by isantop on 2012-11-13
> **jaezcurra said:**
> [FONT="Arial"]Hi, My Wild Dog Performance (wilp9) came with 12.10 and 3.5.0.17 kernel.  Everything was 100% OK until I upgraded to 3.5.0.18.  Since then I have to boot from 3.5.0.17, as launcher, menu bar, home button have disappeared from desktop.
Any suggestion?[/FONT]

Go ahead press Ctrl+Alt+T to open a terminal window, then run these commands:

```
sudo apt-get clean
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall nvidia-current-updates
sudo reboot
```

Your system should now reboot. Once it's finished, you should be all set. Let me know if you have any otehr problems.

---

### Post by jaezcurra on 2012-11-14
It worked!

Thanks a lot!

P.S.: I had to change the last command. It should be:
[INDENT]sudo reboot[/INDENT]

---

### Post by isantop on 2012-11-14
> **jaezcurra said:**
> It worked!

Thanks a lot!

P.S.: I had to change the last command. It should be:
[INDENT]sudo reboot[/INDENT]

::facepalm:: I can't believe I typed that. I guess once you get "apt-get" programmed into your fingertips, you just can't shake it.

---

### Post by LuisGMarine on 2012-11-14
Hello,

I have a quick question:

When I get my wilp9 should I run the system updates and then run the commands above, or vice versa?  Haven't been on Linux in quite a bit, and last thing I need to do is break my first Ubuntu computer.

Thanks,

-Luis

---

### Post by isantop on 2012-11-14
> **LuisGMarine said:**
> Hello,

I have a quick question:

When I get my wilp9 should I run the system updates and then run the commands above, or vice versa?  Haven't been on Linux in quite a bit, and last thing I need to do is break my first Ubuntu computer.

Thanks,

-Luis

You would only need to run this one:

```
sudo apt-get install linux-headers-generic
```

That said, we're working on a new System76 Driver which will do this for you.

---

### Post by LuisGMarine on 2012-11-17
thanks ... works like a charm now.

---

### Post by TheBigLaskowski on 2013-02-10
Worked great for me as well, appreciate the tip

---

