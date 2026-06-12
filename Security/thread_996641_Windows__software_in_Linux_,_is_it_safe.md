---
title: "Windows  software in Linux , is it safe ?"
date: 2008-11-29
forum: Security
---

### Post by radu1984 on 2008-11-29
If i were to install windows dedicated software on linux ( ubuntu and all other free O.S. from linux ) can i get viruses , trojans , spywre , etc ? 
Is it real that no viruses or other such things dont exist for lets say xubuntu , can i be ""infected"" ?
I am new so help me a litle please !
Thank you allot !
Radu !

---

### Post by doas777 on 2008-11-29
I once read an amusing story from a guy who purposly installed several malwares in wine. none of them acheived anything (most would not execute at all).

theoretically, yes a piece of malware could run through wine, but the likely hood of it actually being able to do anything dangerous is minimal. 

if you want a high sec box, you shouldn't install wine, but you really shouldn't install anything fun on a high sec box anyway. minimalism is the order of the day.

---

### Post by brainac0cult on 2008-11-29
no. you'll be fine. because wine creates a virtual c:\ drive in which all your apps are installed if you get a "wine virus" then the most it can do is destroy wine and then all you have to do is reinstall wine.

---

### Post by hyper_ch on 2008-11-29
why do you want to install windows software in linux? why not use linux software?

---

### Post by Dave_Connor on 2008-11-30
Yeah there is alot of good alts to windows software in linux.
Utorrent would be Deluge in torrenting.
Photoshop would be GIMP in image editing.
etc, etc.

---

### Post by markharding557 on 2008-11-30
I have used odd win programs in wine for several years with no problems.
so i think you have nothing to worry about

---

### Post by markharding557 on 2008-11-30
> **hyper_ch said:**
> why do you want to install windows software in linux? why not use linux software?

I use wine to run the exellent proxomitron web filter and for some older games like half life which run perfectly on wine

---

### Post by PocketDog on 2008-12-01
Read about running viruses in Wine [ here ](http://ubuntuforums.org/showthread.php?t=72598) . Classic post, that. Very funny

---

### Post by andr100 on 2008-12-02
I listen that Windows viruses don't live for Linux. Is it true?

---

### Post by Archmage on 2008-12-02
It deepends on how you configurate your system. A virus can easy delete everything that is in your C:\-Drive under WINE. So if you have all your datas there, everything will be gone. Viruses that send spam-mail, might do this and so on.

So you are not 100% safe.

---

### Post by doas777 on 2008-12-02
> **andr100 said:**
> I listen that Windows viruses don't live for Linux. Is it true?

it's true if you don't install wine.

---

### Post by Jammanuser on 2008-12-03
> **Archmage said:**
> It depends on how you configure your system. A virus can easy delete everything that is in your C:\-Drive under WINE. So if you have all your data there, everything will be gone. Viruses that send spam-mail, might do this and so on.

So you are not 100% safe.

hmm...i'm interested in using Wine too, Archmage...so where would u suggest putting all my important data, then, if not in the C:\-Drive under Wine???

Looking forward to ur reply... ):P

---

### Post by Archmage on 2008-12-03
> **Jammanuser said:**
> hmm...i'm interested in using Wine too, Archmage...so where would u suggest putting all my important data, then, if not in the C:\-Drive under Wine???

Looking forward to ur reply... ):P

Let's start on the other end. You should WINE point on an sub-folder where you put all your Windows-stuff. This sub-folder should than be your C:\-Drive. If you have important data there, you should copy it out on a safe place in your Linux-system. This way if a virus delete everything in "C:\", you are still safe.

---

