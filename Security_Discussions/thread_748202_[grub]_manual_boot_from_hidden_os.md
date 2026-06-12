---
title: "[grub] manual boot from hidden os"
date: 2008-04-07
forum: Security Discussions
---

### Post by nightingale2k1 on 2008-04-07
Hi 
I have ubuntu and windows xp. at the moment i have no problem using dual boot. 

I ever look someone who hide windows xp partition and when he going to boot using windows, he type commands in grub and then he can login to windows. By default it went to Ubuntu but if he types 'long' commands he can enter to windows.

How to make it possible ... he is running ubuntu manually.

I did a testing today in grub
```

unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
chainloader +1
makeactive 
boot

```

I could enter Windows but after I restart, I found that my Grub destroyed (error no 22). So I tried to use Ubuntu Live Cd and I found that my ubuntu partition become Unknown (so I reinstall the ubuntu again). Now I know how to do "self suicide" using Grub :lolflag: 

Please tell me how to do that, I am very curious about that. 

Thanks !

---

### Post by cdenley on 2008-04-07
What are you asking exactly? In grub, hiding a parition marks it as hidden in the partition table, so it will still be hidden when you reboot. I don't think you need to use the hide and unhide commands in order to boot into windows xp.

---

### Post by nightingale2k1 on 2008-04-07
I mean, I want to delete one of my OS, let says Windows from my menu.lst so it won't appear on the Grub menu when I boot the OS.

but if I need to access into that OS, I just need to type command so that I can enter the windows.  What i need is the command it self. 

tx

---

### Post by cdenley on 2008-04-08
I think this would work.
```

root (hd0,0)
makeactive
chainloader +1

```

---

