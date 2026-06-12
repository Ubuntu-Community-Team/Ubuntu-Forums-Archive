---
title: "DFU Mode??"
date: 2009-06-23
forum: Wine
---

### Post by JerichoDefeated on 2009-06-23
I'm running Ubuntu 8.10 LTS. And I'm trying to jailbreak my iPod, but it is not being recognized in DFU Mode.

I tried doing it in virtualbox but it's not recognizing the iPod in DFU mode.

Does anyone have a solution??

---

### Post by reyasuk on 2009-06-23
You need to jail break on a 'real' Windows machine unfortunately.  I keep a laptop with Windows installed just for this purpose.
Jen

---

### Post by JerichoDefeated on 2009-06-23
OK Thanks, I just did it using my dads computer.

---

### Post by DPic on 2009-10-31
> **reyasuk said:**
> You need to jail break on a 'real' Windows machine unfortunately.  I keep a laptop with Windows installed just for this purpose.
Jen

Really? Doesn't running virtualbox as root work just fine...

---

### Post by jmap82 on 2011-07-29
> **DPic said:**
> Really? Doesn't running virtualbox as root work just fine...

Well done. 
```
gksudo virtualbox
```
Worked like a champ! 

(For newer users, you will have to setup a 'new' virtual machine if this is your first time running VirtualBox as root. but its quick and easy if you tell it to use and existing 'hard drive', typically found at $HOME/.VirtualBox/HardDisks/Windows.vdi)

---

