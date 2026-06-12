---
title: "GRUB Stage 1.5 Error 22"
date: 2007-09-03
forum: Windows
---

### Post by cdjoya on 2007-09-03
Hey everyone. I am a newbie to Linux, and decided to play around with it. I created a partition on my laptop using Vista's Disk Management. I then installed Ubuntu... I disliked it, and then I decided to boot into Vista and delete the partition with Ubuntu on it. Now, I get a GRUB Stage 1.5 Loading... Error 22. And I can't get back into Vista... Please help!

---

### Post by ScreamingShadow on 2007-09-04
I know what caused this but im in your exact same position! I havent deleted my ubuntu partition yet because thats exactly what'll happen. What you did was you deleted the....main boot command for windows. Well atleast where the GRUB will find those little bytes of code telling it to go into the Vista partion of your hard drive to boot up vista. 

Someone told me.
1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Fixmbr Press Enter
8. Type Fixboot Press Enter

But sadly i dont have a Windows Vista Installation Disc. All i have is recoverys. Can anyone tell me if those are the same or can i "repair" the mbr/boot thru vista while its running?

---

### Post by Dr. C on 2007-09-04
> **ScreamingShadow said:**
> I know what caused this but im in your exact same position! I havent deleted my ubuntu partition yet because thats exactly what'll happen. What you did was you deleted the....main boot command for windows. Well atleast where the GRUB will find those little bytes of code telling it to go into the Vista partion of your hard drive to boot up vista. 

Someone told me.
1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Fixmbr Press Enter
8. Type Fixboot Press Enter

But sadly i dont have a Windows Vista Installation Disc. All i have is recoverys. Can anyone tell me if those are the same or can i "repair" the mbr/boot thru vista while its running?

If you can boot DOS the command FDISK /mbr will do the trick and this works with XP. I do not know about Vista

---

### Post by ScreamingShadow on 2007-09-04
Yeah idk. Command prompt isnt the same as MS-DOS lol. Idk the commands or how to go about this. Sucks :mad: Why did Vista have to go and screw everything up. lol. The only good thing i like about it and have noticed, i have yet to have my pc freeze/blue-screen-error on me. My step dads does it countless times and so does my cousins. Thats the only thing i like about Vista. Rest of it is just a pain.

---

