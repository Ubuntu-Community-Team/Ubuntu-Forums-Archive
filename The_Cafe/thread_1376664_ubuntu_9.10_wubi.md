---
title: "ubuntu 9.10 wubi"
date: 2010-01-09
forum: The Cafe
---

### Post by wirate on 2010-01-09
I posted a video on facebook showing all my compiz eyecandy. A friend got impressed and invited me to his home to install Ubuntu. I thought to avoid partitioning and stuff like that, wubi would be the best option. After spending an hour with the wubi installer (he has a slow computer), the desktop came live. I restarted the computer and booted into ubuntu to discover that wubi had placed something like a live cd into my hard drive. My friend was like what the f***! I have to go through a one-hour installation everytime I run Ubuntu. He was so pissed off he asked me to uninstall and go away :(

The Wubi with Jaunty didnt do this. It installed the system completely. Now whats up with Karmic. Thats not what wubi is supposed to do. After so much effort I convinced one friend and now he is gone thanks to this ****

---

### Post by pwnst*r on 2010-01-09
whoops.

---

### Post by starcannon on 2010-01-09
I have noticed that wubi and 9.10 aren't behaving correctly for me either. I test that particular feature for each new release that I am considering recommending. It is better to find the faults before recommending than to find them after. VirtualBox is a very handy tool for checking things out. 

GL in the future, try to put this one behind you and learn what you can from it.

---

### Post by wirate on 2010-01-10
yeah I learned and sorry for the bad language. I was just pissed off.

---

### Post by The Toxic Mite on 2010-01-10
Ouch!
 
I find 9.10 to be incredibly unstable too; the installer crashed while preparing to re-partition the hard drive.
 
I think I'll just go with LTS releases from now on.

---

### Post by sdowney717 on 2010-01-10
He told you to go away, well not much of a friend, he was just using you to try and get some 'eye candy' When he could not get out of you what he wanted, he threw you away.

---

### Post by wirate on 2010-01-10
> **sdowney717 said:**
> He told you to go away, well not much of a friend, he was just using you to try and get some 'eye candy' When he could not get out of you what he wanted, he threw you away.
 
He didnt want me to mess his computer up :). An archaelogical antique it is with the keyboard locked in a drawer. You know the type. The computer is worth nothing but they act as if it is the most precious thing on earth.

---

### Post by Pasdar on 2010-01-10
Maybe rewrite your post in proper English because I have no idea what happened to your friend's PC.

You installed Ubuntu on a friend's PC with the help of wubi, and it seems that through an error in wubi it had installed the LiveCD version of Ubuntu on his computer? Is that what you're trying to say?

That is in fact the correct functioning of the wubi installed. It downloads and places an image on your harddisk from which it will load Ubuntu each time you select it in Grub. Its faster than running LiveCD from CD, but not that much faster.

Its a great tool for those who have no experience installing OS'.

---

### Post by wirate on 2010-01-10
> **Pasdar said:**
> 
You installed Ubuntu on a friend's PC with the help of wubi, and it seems that through an error in wubi it had installed the LiveCD version of Ubuntu on his computer? Is that what you're trying to say?


It goes like this. I select Ubuntu from ntldr menu (I dont think its grub). Ubuntu boots and starts the setup. "getting time from a network time server", "starting the partitioner", "copying files", "configuring apt" and all that happens and finally when I see the desktop with panels etc, there is an icon on the desktop saying "Install Ubuntu 9.10". So what was all that it was doing for an hour? and when I restart, the same happens again.

---

### Post by The Toxic Mite on 2010-01-10
> **Pasdar said:**
> Maybe rewrite your post in proper English because I have no idea what happened to your friend's PC.
 
You installed Ubuntu on a friend's PC with the help of wubi, and it seems that through an error in wubi it had installed the LiveCD version of Ubuntu on his computer? Is that what you're trying to say?
 
That is in fact the correct functioning of the wubi installed. It downloads and places an image on your harddisk from which it will load Ubuntu each time you select it in Grub. Its faster than running LiveCD from CD, but not that much faster.
 
Its a great tool for those who have no experience installing OS'.
 
English is not her first language, which explains why it's slightly garbled. ;)

---

### Post by wirate on 2010-01-10
English is not HIS first language :D

---

### Post by The Toxic Mite on 2010-01-10
> **wirate said:**
> English is not HIS first language :D
 
Sorry, your avatar depicted a lady :oops: I think that's what confused me :/ lol

---

### Post by Elfy on 2010-01-10
> **The Toxic Mite said:**
> Sorry, your avatar depicted a lady :oops: I think that's what confused me :/ lol

we are all really our avatars, you're a train and I am a PHP :)

---

### Post by The Toxic Mite on 2010-01-10
> **forestpiskie said:**
> we are all really our avatars, you're a train and I am a PHP :)
 
Ah, the power of logic :>

---

### Post by pwnst*r on 2010-01-10
> **sdowney717 said:**
> He told you to go away, well not much of a friend, he was just using you to try and get some 'eye candy' When he could not get out of you what he wanted, he threw you away.

You watch too much television.

---

### Post by garvinrick4 on 2010-01-10
You take a Live CD do not boot from it just put in tray and run. Will come straight to WUBI install say yes. Installs Wubi and attaches its boot to Windows dos4grub, can check in Windows by running "bcdedit" without quotes, will be menu entry in that has a Wubi in it. 
 It is a folder in C: drive of Windows right next to Users folder. Old versions were installed differently before 9.04 I believe. After you hightlight Ubuntu in boot menu, hit escape will
give you Ubuntu boots such as multiple kernels and such. Of course just select Ubuntu in
boot and will boot UBuntu. 
 If you uninstall ubuntu, use the uninstall in windows folder, do not use add and remove programs in Windows. Sometimes the Wubi is left in boot manager of windows or the bcd as it is called.

When you install should ask you size you want of space and your password and click install that is it.

---

