---
title: "Fix Windows boot problem within Ubuntu"
date: 2008-11-17
forum: Windows
---

### Post by Fueled on 2008-11-17
Greetings everyone!
I've been having some troubles with my Windows XP setup lately. I decided to come to this forum for advice because, first I had a great response on my first query about dual-booting, and second because I have Ubuntu installed on the same drive as my Windows setup and I thought it could be useful in solving this problem.

I'll try to be brief.
About a month ago, I formatted and installed a fresh Windows XP setup on my 4-year old computer (I also installed the latest Ubuntu release in unpartitioned space on the same drive).
One of the reason I decided to format and reinstall Windows, is that CHKDSK often ran when I rebooted my PC because some files were considered corrupt. I figured a fresh install could solve things.
But since my new installation, I've had again some problems.
Not two weeks ago, I had a corrupt registry problem, which I could solve within Ubuntu, with this [_guide_]("http://www.arsgeek.com/2008/02/27/use-your-ubuntu-partition-to-fix-a-corrupt-registry-on-a-windows-xp-partition/").
Last night, while everything was working seemingly fine, Word and Excel 2007 documents could not be edited anymore. So, after doodling a bit, I decided to reboot, as this is sometimes an easy solution. But, after I chose Windows XP at Grub prompt, I saw the Windows progress bar, and then a glimpse of the blue login screen, but immediately the computer reboots. Every attempt to reboot had the same behavior.

With "Disable automatic reboot on error", I was able to see the blue screen error, which was "STOP: c000021a. The Windows Logon Process system...".
I've tried:
- the registry fix that solved my other booting problem, because it seems the editing problem of Office 2007 documents could be due to AutoUpdates and registry;
- using "Last good configutation" from F8 menu;
- Safe Mode, but it still reboots after loading the Safe Mode needed files;
- CHKDSK from the Recovery Console (but without /r parameter, I will do that tonight, but I don't think this will solve it).

I have this unpleasant feeling that my hard drive is possibly physically damaged. But then again, Ubuntu is working fine.

Anyone has suggestions on how to solve this one, knowing that I have a working Ubuntu setup at my disposition?
Thanks in advance!

---

### Post by caljohnsmith on 2008-11-17
> **Fueled said:**
> 
I have this unpleasant feeling that my hard drive is possibly physically damaged. But then again, Ubuntu is working fine.

Based on your computer's symptoms, I would have to agree, it sounds like you could be experiencing a hardware problem, most likely your HDD. How about testing your HDD's health while you are in Ubuntu by opening a terminal (Applications > Accessories > Terminal), and doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please attach the two files from your desktop so I can look at them, and hopefully help you determine whether your HDD is the cause of your problems. :)

---

### Post by Fueled on 2008-11-17
Hi and thanks for your answer!

I've done as you suggested. I've attached both "before" and "after" files to this post.
Please note that in my case, the drive in question is **sdb**.

At first glance, nothings grabs my attention in the "after" file which could indicate a problem. But then again, what do I know ;)

Thanks!

---

### Post by caljohnsmith on 2008-11-17
I agree, it looks like from the results that your HDD is OK. Just to confirm though, how about also running:
```
sudo badblocks -sv /dev/sdb
```
And let me know if that finds any bad sectors. Also, what does the Windows "chkdsk /r" report when you run it? If it finds any errors, be sure to run chkdsk as many times as it takes until it reports no errors. It's definitely sounding more like you have a Windows problem, and the fact that Ubuntu is still working just fine would support that idea. Let me know how it goes. :)

---

### Post by Fueled on 2008-11-18
Seems in perfect condition:

```
sudo badblocks -sv /dev/sdb
Checking blocks 0 to 117220823
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

```

I did not have the time to try chkdsk /r yesterday, so I'll do it tonight and come back here with the results.

Thanks!

---

### Post by Fueled on 2008-11-18
Ok, I've done a CHKDSK. There were "one or more errors" the first round, but the secound round looked good: _[http://i33.tinypic.com/25g8mqh.jpg]("http://i33.tinypic.com/25g8mqh.jpg")_.

I tried booting into Windows, but it's exactly the same as before.
Any ideas?

---

### Post by caljohnsmith on 2008-11-18
Were you using good antivirus/anti-malware software in Windows? I'm wondering if some malware might be the cause of your Windows problem. I think if you want to salvage your Windows without reinstalling, then doing a "Windows Repair" from the Windows Install CD is your best bet at this point. Let me know how it goes.

---

### Post by Fueled on 2008-11-18
Yes, I was using Antivir, and it was up-to-date. 
I can't recall if I had installed SpyBot S&D or not. I usually do, but I don't remember if I did since reinstalling Windows.

I tried finding the "Windows Repair" option when booting with the Windows CD, but I could not see it right away and I did not want to choose the wrong option and reinstall Windows! Why couldn't they make it simple *sigh*.
I'll have another look now.

---

### Post by Fueled on 2008-11-19
Ok, so with the Windows installation CD, I choose the partition where Windows is currently installed, and as expected it finds an existing /WINDOWS directory. But the only options I'm presented with are:
1) "L" to delete existing Windows installation
2) "ESC" to choose a different installation folder
3) "F3" to exit setup

No repair option whatsoever. I don't know what I'm doing wrong now...

Another thing is that I got a "routine check" of drive /dev/sdb6 during startup of Ubuntu. It's the first time this happens, or at least the first time I notice it.

---

### Post by caljohnsmith on 2008-11-19
Is your Windows Install CD a true Microsoft install CD or just an OEM (Original Equipment Manufacturer) CD? If you have a true install CD, then choose the option "install Windows" from the first main menu, and that actually leads to an option to repair windows in addition to the option to install it. If you don't have the Windows Repair option, you might be stuck with a reinstall. Let me know how it goes.

---

### Post by Fueled on 2008-11-19
Nah, it's an OEM. Oh well! At least I can easily access my files from within Ubuntu!

I'm just pissed that I installed Windows not one month ago, and that the only symptom that preceded the booting problem is Office 2007 documents being non-editable. Not very helpful to diagnose...

So in your mind, you see no other culprit than spy/malware?
And, is it OK for me to assume that my hard drive is still in good condition, and should not be the cause of my recent troubles?

Thanks again!

---

### Post by caljohnsmith on 2008-11-19
> **Fueled said:**
> 
So in your mind, you see no other culprit than spy/malware?
And, is it OK for me to assume that my hard drive is still in good condition, and should not be the cause of my recent troubles?

Thanks again!
I can only guess it is maybe a virus/malware problem based on Windows' strange symptoms, but we don't know for sure if that's the case. The fact that Ubuntu is still OK and the HDD diagnostic test said your HDD is healthy means your HDD is probably just fine. 

If you decide to reinstall Windows with your OEM CD, make sure you backup everything important you have in Ubuntu, because I think it's highly likely that the OEM disk will simply erase the entire drive and reinstall Windows to the entire drive, not reinstall Windows to its current partition. That's usually the way those OEM CDs work. Anyway, good luck and keep me posted on how it goes. :)

---

### Post by Fueled on 2008-11-19
Fiouf! It turned out to be pretty easy! The installation only installed back the system folders. All programs are still found in "Program Files" and most run on the first try. Funny thing is it created a copy of the contents of "Documents & Settings", i.e. I now have "All Users" and "All Users.WINDOWS" folders... Another thing is that the Windows installation is now on the D:\ drive letter. I'll have to get used to that I guess.

This is a bit off-topic, but is there a way to make a ghost of the WINDOWS volume (/dev/sdb1) from within Ubuntu, and to restore it also from Ubuntu, if ever the need arises?

Thanks!

---

### Post by caljohnsmith on 2008-11-19
> **Fueled said:**
> Fiouf! It turned out to be pretty easy! The installation only installed back the system folders. All programs are still found in "Program Files" and most run on the first try. Funny thing is it created a copy of the contents of "Documents & Settings", i.e. I now have "All Users" and "All Users.WINDOWS" folders... Another thing is that the Windows installation is now on the D:\ drive letter. I'll have to get used to that I guess.

This is a bit off-topic, but is there a way to make a ghost of the WINDOWS volume (/dev/sdb1) from within Ubuntu, and to restore it also from Ubuntu, if ever the need arises?

Thanks!
That's great news the reinstallation went so smoothly. About ghosting/cloning the Windows partition, you could look at maybe "partimage" which is in the repositories, or even [Clonezilla]("http://www.clonezilla.org"). Or if you want to be a little geeky about it and use the command line, you can use: 
```
sudo dd if=/dev/[COLOR="Blue"]sdb1[/COLOR] bs=10M conv=notrunc,noerror | bzip2 -c > ~/Desktop/[COLOR="Blue"]sdb1[/COLOR].bz2
```
And then to restore the sdb1 image:
```
bzcat ~/Desktop/[COLOR="Blue"]sdb1[/COLOR].bz2 | dd of=/dev/[COLOR="Blue"]sdb1[/COLOR] bs=10M conv=notrunc,noerror
```
Anyway, cheers and have fun. :)

---

