---
title: "Help With MRB/Grub. Want Vista Back."
date: 2007-09-04
forum: Windows
---

### Post by ScreamingShadow on 2007-09-04
Well i feel alittle ill-advised to come into a ubuntu forum and ask for ...essentially windows vista help but i hope someone out there has a heart and helps. :P Like walking into a bears den. But here goes, my situation is this. Ive recently installed Ubuntu on my computer. I did a dual-boot partition. Split my hard drive right down the center. Now my only problem with not using Ubuntu is the massively confusing command line/setups. I havent been able to get my hardware to work with it. So for now ive given up. Ill keep my LiveCD for future use with a soon to come pc. Anyways i want to remove linux and get my machine back to automatically loading Vista always free-n-clear. Now i know just inserting the LiveCD and removing the Linux partition will remove it but also leave my MBR broken and no where to go. How do i fix my MBR to boot back to Vista once linux is gone? I ordered this pc online so no authentic vista discs or anything. =( Just my recovery discs and hardware registry disc. So..i was just wondering if theres anything for me to do. How can i get Linux uninstalled and Vista back up.

---

### Post by ashz on 2007-09-04
1.	Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.	Press a key when you are prompted.
3.	Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.	Click Repair your computer.
5.	Click the operating system that you want to repair, and then click Next.
6.	In the System Recovery Options dialog box, click Command Prompt.
7.      Type Fixmbr Press Enter
8.      Type Fixboot Press Enter


All done

Laters
ash

---

### Post by K.Mandla on 2007-09-04
> **ScreamingShadow said:**
> Well i feel alittle ill-advised to come into a ubuntu forum and ask for ...essentially windows vista help but i hope someone out there has a heart and helps. :P Like walking into a bears den. 
Don't worry: You can ask anything you like here. There are plenty of experienced Vista users around and they'll help if they can.

I'm going to shift your thread to the Windows discussion area, where more people who can help might see it. :)

---

### Post by LaRoza on 2007-09-05
Or use the super grub disk to restore the MBR of Windows (works with Vista).

---

### Post by Foxblood on 2007-09-05
I've got the same problem. (one of many). I was looking around for a solution and came across this:

1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

Source: [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html")

Very similar to what's listed above. Do both of these methods work? Do they do the same thing? Is one better than the other or is there anything anyone can add to this?

I have just used this method successfully. It even left my XP install intact and functional.

---

### Post by digital_exhaust on 2007-09-06
The methods outlined above may or may not work..sometimes it does and sometimes it doesn't... 

One easy and free way to fix a borked Vista bootloader is [VistaBootPro]("http://www.vistabootpro.org/").. Not as rewarding as actually fixing it yourself, but it works... or you could always just re-install and start over;)

---

### Post by ScreamingShadow on 2007-09-07
Well i removed the linux parition. Idk how to get the 130gigs of my hard drive back to ntsf or w/e so windows can use it. Ill figure that out later. I also installed and loaded the winboot pro thing before i uninstalled my linux partition. It only saw Vista(1 os) and nothing else. Said everything was fine. So....i removed linx and now my computer is nothing. Grub error 22 and wont boot from a linux livecd to try running winboot pro. So if i use HP System recovery to reformat my hard drive, like it came from the factory, will Vista still be on there? I had made the 2 DVDs for Vista Recovery. I DO NOT have installation discs. I bought it online and they used their distribution copy to load it on there before shipping it to me. So thats my question, if i reformat will vista still be on there or will my recovery discs put it back on there? Or am i s.o.l and just gota go buy some actual hard-copy, authentic discs for myself?

---

