---
title: "computer does not respond to single left-click of mouse"
date: 2010-09-01
forum: System76 Support
---

### Post by eljayski on 2010-09-01
hey, everybody (or anybody)!

for no obvious reason, my starling has stopped responding to single mouse clicks (left) to get things done.

i've swapped mouse units (both gigaware, from radio shack) and no effect.

i confess to enabling horizontal scrolling the other day--i just disabled it before posting here.

went to about:config without success.

life used to be better; can anyone suggest a fix?

this is so basic; i feel ignorant.

many thanks

---

### Post by isantop on 2010-09-01
What model is your computer. If you need to check, you can use the System76 Driver. 

If you can't get to the driver since your mouse isn't responding, you can press Alt+F1 to open the menu, then use the arrow keys to navigate through them. You should also be able to launch it by pressing Alt+F2 and entering ```
system76-driver
``` and pressing enter.

I'll also need to know how you tried to enable the horizontal scrolling.

---

### Post by eljayski on 2010-09-01
hi, isantop, and thank you for replying!

computer is a Starling, purchased about 1 year ago.  running 10.04.

the mouse still works, but left-clicking is an uncertain proposition.  sometimes a double-click makes the computer go, sometimes it takes more than 2 clicks.

right clicking seems to be OK.  i changed from one "Gigaware" cordless mouse to another unit we had in the house.  problem remains.

i had thought that perhaps the left-click button is simply wearing out, physically.  the fact that the problem did not go away with a change of mouses makes me think it is software, not hardware.

i enabled then disabled horizontal scrolling using the "mouse" button with the preferences selection within "System" at the top of the screen.  it "seems" like the problem began coincident with my enabling horizontal scrolling.

thank you kindly for your help, eljayski

---

### Post by jcphil on 2010-09-01
I'm having a similar issue. No mouse clicks seem to work. I can move the cursor just fine and no apps are frozen. I can type commands at the command line. The logs seem to indicate a USB issue and it is plugged in to a USB port. The same mouse works fine when I'm running Windows.

---

### Post by 73ckn797 on 2010-09-01
Try using a USB to the round connector adapter. The one next to the round keyboard plug. I have a MS keyboard which does not always work on a reboot when connected with USB unless I use the adapter.

---

### Post by eljayski on 2010-09-02
apparently, i've been able to solve the problem by disabling H scrolling and then rebooting.  reboot seems to be key.

thanks for comments!

---

### Post by 73ckn797 on 2010-09-03
> **eljayski said:**
> apparently, i've been able to solve the problem by disabling H scrolling and then rebooting.  reboot seems to be key.

thanks for comments!

Since Ubuntu does not require a reboot for most changes, I find weird problems pop up sometimes if I do not reboot.

---

