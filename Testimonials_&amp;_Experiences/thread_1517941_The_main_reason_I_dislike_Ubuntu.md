---
title: "The main reason I dislike Ubuntu"
date: 2010-06-25
forum: Testimonials &amp; Experiences
---

### Post by ComradeNF on 2010-06-25
Hey guys. This is a mini rant I am making about why I dislike Ubuntu 10.04. Please bare with me as English is my 3rd language :).

Around 12 hours ago, my friend told me about this "awesome" new OS called Ubuntu. I googled it, and it downloaded in a couple minutes. Then I followed the instructions and burned it onto a disk. Then I installed Ubuntu. I installed the x86 version, as dual-boot with Windows 7. I played around with the OS for an hour before I got bored, and I decided to remove it.

Now is when things started to get annoying. I wanted the OS off of my system so I looked up some guides on how to remove it. I read a thread on this forum which said to delete the partition for Ubuntu, and a lot of people said it worked for them. I did that. And thats when things started to go VERY wrong.

This is when I noticed that when installing Ubuntu, it deleted my old BIOS and installed GRUB instead, which is a TERRIBLE BIOS. I despise it. It kept giving me an error saying something like "partition does not exist". So I insterted my Windows 7 PC and stupidly enough system restored, but I got the same error. Then I fully reinstalled Windows 7 and got the same error. My patience was wearing thin. I called ASUS support but they didn't know anything either. At last, I reinstalled Ubuntu, and Windows 7 seemed to work again. SEEMED to work. But it didn't. I got an error in big red letters saying RECOVERY.DAT NOT FOUND. Then I spent 6 hours finding the solution to that. Apparently I had to start my Windows 7 disk and run something like "bootsect /nt60 ALL /mbr" and it worked.

Anyway, I got my Windows 7 to work again, and that annoying Dual Boot screen is gone for some reason now. At least it works. but I'm stuck with that annoying BIOS. I only ever used the BIOS once before installing Ubuntu and that was for overclocking my CPU.

Anyway, Ubuntu 10.04 is a very nice and user friendly OS, but the BIOS that comes with it is horrible.

Finally, I get to my question: Is there anyway to get my old computer BIOS back? Hopefully I don't have to call ASUS support again because it charges me a lot of money since I live in Sweden.

Thanks for reading this thread guys :).

---

### Post by WorMzy on 2010-06-25
Ubuntu doesn't do anything to your BIOS, that's built into your PC's motherboard. Can you describe exactly what this "BIOS" screen says?

---

### Post by ComradeNF on 2010-06-25
> **WorMzy said:**
> Ubuntu doesn't do anything to your BIOS, that's built into your PC's motherboard. Can you describe exactly what this "BIOS" screen says?

I don't remember exactly what it said. It said something along the lines of "Unable to find partition". Now I can't even open the bios anymore when I restart my computer. All I know is that my bios was changed to GRUB as soon as I installed Ubuntu. I haven't installed anything else for the past few weeks.

---

### Post by EdiblePlastique on 2010-06-25
The "BIOS" isn't a BIOS - it's a bootloader. Basically, it's for dual booting and changing linux kernels and stuff like that. 

Also, don't dislike Ubuntu because of one silly installation that you got bored of. It's not its fault that the partitions were left over from the removal of it, it was yours for not deleting the Ubuntu ones and resizing your Windows one. 

Somebody here will help you remove GRUB and get your old "BIOS" back.

---

### Post by wilee-nilee on 2010-06-25
Phishing are we.

---

### Post by ComradeNF on 2010-06-25
> **EdiblePlastique said:**
> The "BIOS" isn't a BIOS - it's a bootloader. Basically, it's for dual booting and changing linux kernels and stuff like that. 

Also, don't dislike Ubuntu because of one silly installation that you got bored of. It's not its fault that the partitions were left over from the removal of it, it was yours for not deleting the Ubuntu ones and resizing your Windows one. 

Somebody here will help you remove GRUB and get your old "BIOS" back.

Actually, I took the advice of the person above me and restarted my PC just now, and pressed F5. It then gave me an option which said something like "Select BIOS" and there were 3 different options. I clicked the first option which said something like "HDD BOOT". Then it came up with my original boot. I'm really confused right now. I'm not that great with computers, and I had no idea you can have more than 1 BIOS o_O. Anyway, things are running smoothly now, so its all good. I'm getting a desktop soon anyway so I can finally sell this piece of junk.

And I don't hate Ubuntu as an OS. It was actually an okay OS. Its very basic, and great for people who are new to computers. It actually reminds me a bit of Mac OS X Snow Leapord. So I don't hate Ubuntu, I just find the GRUB thing to be really annoying and a waste of my time. As for Ubuntu, I might install it again someday on my "Trash" computer which is like 10 years old and play around with it some more.

Just a question, but do any of you know if Steam works on Ubuntu? I'm a hardcore PC gamer and I'd really like to know this. If it does work, I will try it out again.

---

### Post by bodhi.zazen on 2010-06-25
> **ComradeNF said:**
> Hey guys. This is a mini rant I am making about why I dislike Ubuntu 10.04. Please bare with me as English is my 3rd language :).

Around 12 hours ago, my friend told me about this "awesome" new OS called Ubuntu. I googled it, and it downloaded in a couple minutes. Then I followed the instructions and burned it onto a disk. Then I installed Ubuntu. I installed the x86 version, as dual-boot with Windows 7. I played around with the OS for an hour before I got bored, and I decided to remove it.

Now is when things started to get annoying. I wanted the OS off of my system so I looked up some guides on how to remove it. I read a thread on this forum which said to delete the partition for Ubuntu, and a lot of people said it worked for them. I did that. And thats when things started to go VERY wrong.

This is when I noticed that when installing Ubuntu, it deleted my old BIOS and installed GRUB instead, which is a TERRIBLE BIOS. I despise it. It kept giving me an error saying something like "partition does not exist". So I insterted my Windows 7 PC and stupidly enough system restored, but I got the same error. Then I fully reinstalled Windows 7 and got the same error. My patience was wearing thin. I called ASUS support but they didn't know anything either. At last, I reinstalled Ubuntu, and Windows 7 seemed to work again. SEEMED to work. But it didn't. I got an error in big red letters saying RECOVERY.DAT NOT FOUND. Then I spent 6 hours finding the solution to that. Apparently I had to start my Windows 7 disk and run something like "bootsect /nt60 ALL /mbr" and it worked.

Anyway, I got my Windows 7 to work again, and that annoying Dual Boot screen is gone for some reason now. At least it works. but I'm stuck with that annoying BIOS. I only ever used the BIOS once before installing Ubuntu and that was for overclocking my CPU.

Anyway, Ubuntu 10.04 is a very nice and user friendly OS, but the BIOS that comes with it is horrible.

Finally, I get to my question: Is there anyway to get my old computer BIOS back? Hopefully I don't have to call ASUS support again because it charges me a lot of money since I live in Sweden.

Thanks for reading this thread guys :).

I am sorry you are having problems, but fortunately for you Microsoft / Windows is easier to use.

In fact,Microsoft maintains a detailed page with step-by-step instructions:

[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

We have a similar page on Ubuntu if you prefer:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Best of luck to you.

In the future you might have better luck with virtualization.

If you ever decide to install an OS again, windows, Linux, or BSD, you may find you have less problems if you read the relevant documentation first or ask questions if you are not sure how to proceed. Failure to do so can result in irreversible data loss, so I also advise you learn to back up your data (if you do not already do this).

---

