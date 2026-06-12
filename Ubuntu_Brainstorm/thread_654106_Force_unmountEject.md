---
title: "Force unmount/Eject"
date: 2007-12-30
forum: Ubuntu Brainstorm
---

### Post by holihue on 2007-12-30
A function to force unmount/eject an drive or cd is one thing that is needed sometimes in Ubuntu.

For example when I installed a program in wine, and I had to insert cd nr2, I got an error massage saying that an application is preventing to unmount the drive.
And to "fix" (eject) it I had to take out my cd rom (while I my pc was running), and after I got the message displaying that it was unsafe to remove the drive, it put it back and eject it and put in the other disc.

I'm glad I used my ThinkPad, because it is easy to take off the cd-rom.


This is very necessary to have.

---

### Post by jken146 on 2007-12-30
Well, you can always kill the program that is using the cdrom, and then it will let you eject it.

**top** shows you the most active processes that are running.

**kill** and **pkill** can be used to kill processes.

**xkill** will kill a GUI window with the cursor.

---

### Post by IanW on 2007-12-31
To change CDs during a wine install, you need to open a terminal window and use the command "wine eject".

---

### Post by Sukarn on 2008-01-01
I do agree with the OP here.

I have faced situations where a cd would get stuck in the drive, pressing the eject button would tell me that the disc was in use, trying to **umount** or **eject** through terminal would give the same result, and **umount -f** gives a similar error, or else I don't know how to use **umount -f**. Isn't the purpose of **umount -f** to be able to force un-mount some partition, even if it is in use?

The only way I have been able to eject the CD in such a condition has been by rebooting the computer. Restarting X or killing random processes did not help me at all.

---

### Post by Linder on 2008-01-13
> **IanW said:**
> To change CDs during a wine install, you need to open a terminal window and use the command "wine eject".

I can confirm that this does work.

---

### Post by kli6891 on 2008-08-24
> **Linder said:**
> I can confirm that this does work.

same here

---

### Post by olskar on 2008-08-24
This problem sounds windowsish..not good :)

---

### Post by Merk42 on 2008-08-24
> **olskar said:**
> This problem sounds windowsish..not good :)

How so? I have NEVER come across such a thing when I've used Windows, but have when using Ubuntu.

---

### Post by snake444 on 2008-09-06
the normal user doesnt need to do commands in terminal, have u seen someone in windows opening dos and doing some commands? no because windows is user friendly, and solutions like open terminal and do wine eject are bad because normal users doesnt need to open terminals! ubuntu should be user friendly and until it wont be i dont think alot of people use it.

---

### Post by rossjman1 on 2008-09-06
> **snake444 said:**
> the normal user doesnt need to do commands in terminal, have u seen someone in windows opening dos and doing some commands? no because windows is user friendly, and solutions like open terminal and do wine eject are bad because normal users doesnt need to open terminals! ubuntu should be user friendly and until it wont be i dont think alot of people use it.
I agree. I have been using linux for 4 years and never heard of "wine eject". This would have saved me some headaches.

---

### Post by truffsekka on 2008-09-09
> **IanW said:**
> To change CDs during a wine install, you need to open a terminal window and use the command "wine eject".

Just what I needed.

---

### Post by SpaaTTeLi on 2009-02-14
Sorry for replying to this old thread but I just googled this up and I think it would help if it would even say in the "cant eject" window that you could try wine eject on terminal, or is this really only wine's problem?

---

### Post by Sukarn on 2009-02-14
> **SpaaTTeLi said:**
> Sorry for replying to this old thread but I just googled this up and I think it would help if it would even say in the "cant eject" window that you could try wine eject on terminal, or is this really only wine's problem?

If this is implemented, then there would have to be some sort of check to see whether wine is installed and running before suggesting this, or else it would only confuse normal users who do not have wine installed.

---

### Post by ajkenney on 2009-02-16
My problem has been not with the CD/DVD Drive but with external USB HDD's.  My desk is a busy place and my laptop gets shoved around a lot.  When I have a USB HDD connected to the laptop and the HDD is mounted on the desktop, the laptop might get pushed aside for a large diagram or some such thing.  During this process the connection with the USB HDD is momentarily lost and then returns (loose connector most likely).  This results in the HDD being mounted again leaving me the old and new icons on the desktop.  When I try to unmount the old icon, the computer does nothing.

If this happens 3-4 times in a morning without me looking at my laptop, I wind up having the same HDD mounted 3-4 times with an icon for each time...

How can I unmount the drives that don't function anymore?  And their associated icons on the desktop?  I already tried deleting the unused icons....  doesn't work.

Cheers,

Andy

---

### Post by smartboyathome on 2009-02-16
You can't unmount those extra ones. The only way to is to reboot the computer as far as I know. I get the same thing happening when I accidentally knock the cable out of the USB slot.

---

