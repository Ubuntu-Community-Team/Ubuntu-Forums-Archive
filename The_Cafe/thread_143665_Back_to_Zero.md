---
title: "Back to Zero"
date: 2006-03-12
forum: The Cafe
---

### Post by OffHand on 2006-03-12
I just installed Dapper Flight 5.
The whole install process went smooth untill it needed to install the GRUB.
Didn't find my xp, gave me some errors.... it's all vague after that.
Well, here I am without my files (thank god my projects and work are on my mac) and only running Ubuntu Dapper. A brand new start. I'll miss my mp3's but they will be back soon enough  (thnx to some awesome folks I know). 
System seems to be running ok now. It's def fast. 
I wonder how I will manage without Windows. I didn't use it too much anyways.
Time to fill that 100 GB again  :)

---

### Post by mstlyevil on 2006-03-12
[QUOTE=subsonic_shadow]I just installed Dapper Flight 5.
The whole install process went smooth untill it needed to install the GRUB.
Didn't find my xp, gave me some errors.... it's all vague after that.
Well, here I am without my files (thank god my projects and work are on my mac) and only running Ubuntu Dapper. A brand new start. I'll miss my mp3's but they will be back soon enough  (thnx to some awesome folks I know). 
System seems to be running ok now. It's def fast. 
I wonder how I will manage without Windows. I didn't use it too much anyways.
Time to fill that 100 GB again  :)[/QUOTE]

You might want to see if there is a bug report filed on that. You might be able to recover your XP partition by editing your grub file.

---

### Post by sapo on 2006-03-12
Why dont you just edit the menu.lst?

Add this to the end of the file:

/boot/grub/menu.lst
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

I assume that your windows XP is installed on the first hard drive partition, this should solve your problem

---

### Post by OffHand on 2006-03-12
It broke the grub, made 20 GB of my disc disappear.
I'm too tired now. If I would have know more I probably could have solved it.
Maybe not. I'll fill in a report tomorrow.
Recovery isn't possible I'm affraid. On the other hand I got rid of tons of illegal stuff so that's good.

---

