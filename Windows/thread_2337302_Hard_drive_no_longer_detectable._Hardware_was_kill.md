---
title: "Hard drive no longer detectable. Hardware was killed?"
date: 2016-09-16
forum: Windows
---

### Post by stepnjump1 on 2016-09-16
Hi guys,

Something really weird happened to me last week. I wanted to make some room on my gf's Windows Vista computer in order to install ubuntu (dual boot) using the live CD
As her computer was full at 98% I started  backing up her computer first. The interface told me it would take something like 2 hours to back it up only (by copying files from one drive to the other). When I woke up 6 hours later, the screen was all black and the computer was totally unresponsive so I had to shut it down by cutting the power (yes I'm aware I shouldn't have but it was the only thing I could do).
When I started the system again, it booted in Vista with no problem so I felt really fiuh! about this.
Later that night, she shut it down the normal way (controlled shutdown). The next morning, as I tried to boot it up, I got an error message
[h=1]File: \boot\BCD Status: 0xc000014c Windows Vista[/h]Then I unplugged the serial ATA hard drive and connected the drive as slave in my main computer. Lo and behold, even gparted cannot even see this drive!
Is it possible that just by cutting the power, I would have killed a hard drive so bad. Goodness, I was just reading her drive. Besides, it rebooted after that event. It only crashed hours later.
It's not even a crash, it's a total kill !!!

I don't know what to think.


Step.

---

### Post by howefield on 2016-09-16
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2016-09-16
I'm surprised you could even boot a computer that was 98% full.  The BCD in your error message is in reference to the windows boot files which appear to be corrupted.  Copying from that drive should not have any impact on boot files.  Your best bet for help with this is at the microsoft or some other windows forum.  The link below discusses possible solutions to the problem.  Good luck.

[http://answers.microsoft.com/en-us/windows/forum/windows_vista-update/file-bootbcd-status-0xc000014c-windows-vista/fd4a7978-c356-4771-a253-6216c3a6e0e2?auth=1](http://answers.microsoft.com/en-us/windows/forum/windows_vista-update/file-bootbcd-status-0xc000014c-windows-vista/fd4a7978-c356-4771-a253-6216c3a6e0e2?auth=1)

---

### Post by stepnjump1 on 2016-09-16
Thank you for the link yancek but what is really bizare is that I cannot even mount this drive in linux and can't even see it when doing a fdisk -l. All I see is my sda
All I could think is that something hardware happened?

---

