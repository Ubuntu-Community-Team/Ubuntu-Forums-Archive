---
title: "quadrouple boot (win 7, win 8, ubuntu and android)"
date: 2013-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by ads2996 on 2013-11-16
Hi,

Hopefully for Christmas i am getting a 1tb drive for my laptop which will quench my needs for all my games. I would also like to set up a quadrople boot, with windows 7,8.1, Ubuntu and android. And a seperate drive for data formatted to ntfs.

1. Windows 7 (100gb)
2. Windows 8 (60gb)
3. Ubuntu (20gb)
4. Android (20gb)
5. Swap (8gb)
6. Data (790gb)

---

### Post by oldfred on 2013-11-16
Do not know anything about Android, but Windows is best in primary partitions if your system is BIOS based not UEFI.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Also with Window8 you have to make sure fast boot is off, even if just dual booting two versions of Windows.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Then from grub you can easily boot both versions of Windows.

---

### Post by david98 on 2013-11-16
Old fred is spot on. Am just curious why you would want win 7 and 8 ? In my opinion it would be 1 or the other.

---

### Post by ads2996 on 2013-11-16
i want win 7 cause it works perfectly with my laptop and its hybrid graphics, i want win 8 to rey it out as my laptop has a touch screen, i did use to triple boot ubuntu win 7 and win 8 then i ran out of space so got rid of win 8. so i know to porcess behind isntalling a tripl boot. my main problem is android.

---

### Post by Copper Bezel on 2013-11-17
Why Android, though? Android on x86 is still barely usable for lack of apps, isn't it? And a lot of desktop-type hardware acts funny under Android. It's really not the same experience on a non-ARM device.

---

### Post by ads2996 on 2013-11-17
I hadnt done much research into to how well android ran on x86, the only reason i wanted to get it was because i dont have the money atm to buy a 10" tablet

---

### Post by Copper Bezel on 2013-11-17
Gotcha. Yeah, best stick with Windows 8 for tablet-type apps, even if the selection is poorer than on ARM Android. You could run Chromebook OS, but it doesn't give you anything Chrome under Ubuntu doesn't.

---

### Post by ads2996 on 2013-11-23
I love Ubuntu, so I will definitely be using it, I have tried bother distros but in prefer Ubuntu, I just have a graphics card problem with both Ubuntu and windows 8, so I'll have to find the workaround I had for Ubuntu and install that, Windows 8 however will be more of a problem.

---

