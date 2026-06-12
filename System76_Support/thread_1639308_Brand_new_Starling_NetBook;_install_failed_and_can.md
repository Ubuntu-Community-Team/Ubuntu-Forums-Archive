---
title: "Brand new Starling NetBook; install failed and can't install from CD or USB"
date: 2010-12-06
forum: System76 Support
---

### Post by Sydius on 2010-12-06
Just got my brand new [Starling NetBook]("http://www.system76.com/product_info.php?cPath=28&products_id=105").  Booted it up and filled out my name etc.  When I was done configuring the setup, it gave me an error I regret not writing down saying that installation could not complete.  I clicked "retry" once, but got the same error, so I clicked "continue anyway" and it restarted.

After restarting, I am now getting the message "No init found.  Try passing init= bootarg."  I'm then given a "(initramfs)" shell and can navigate around the file system.

I wasn't sure what to do on that shell, so I decided to just install a fresh copy of Ubuntu, since I wanted 10.10 anyway (having used it in the past).  I first tried installing Ubuntu Desktop 10.10 x64 since the [Atom N550]("http://ark.intel.com/Product.aspx?id=50154") it came with is 64-bit.

My first attempt was with a CD ROM I already had and was known to work with a USB CD-ROM drive.  After reconfiguring the boot priority, it clearly tried to boot off of it and would display an Ubuntu purple screen momentarily but then hang with a blinking text cursor.

I thought maybe I was wrong about the netbook being 64-bit compatible or that the USB CD ROM drive was broken, so I then tried making a bootable USB memory stick with Ubuntu 10.10 NetBook (32-bit) from my Ubuntu desktop and I tried making a bootable memory stick with Ubuntu 10.10 Desktop x64 from a Windows Vista desktop by following the instructions on the Ubuntu web site.  Neither one worked--same problem as the CD.

Given I've never successfully installed off of USB, I gave the CD ROM one last try, this time with Ubuntu 10.10 (32-bit) NetBook edition on a freshly burned disc.  Still get nothing but the blinking cursor.

Halp?

**(EDIT) Solution:**

Reinstall using the **Ubuntu 10.04.1 x64 Alternate**; 10.10 did not work (all combinations of NetBook/Desktop/Alternate, x64/32-bit) and 10.04 x64 also did not work.

---

### Post by Sydius on 2010-12-06
I just tried booting it again and immediately got "Keyboard controller error" with a loud beeping.  I'm afraid this is looking more and more like a HW issue?

**Edit:** oddly, I was able to press F1 to continue, so the KB wasn't broken or anything

---

### Post by Sydius on 2010-12-06
Was able to get to the menu by pressing enter while the Ubuntu 10.10 x64 CD was booting (during the purple screen it gets to before hanging); currently doing a memory test for kicks.

**Edit:** the memory test passed.

---

### Post by isantop on 2010-12-06
It sounds to me like the CD you tried to use was bad. You might try checking it. To check it, press a key at the first screen you see when you boot from it (The purple one with the white symbols on the bottom). In the menu that appears, select a language, then select "Check CD for Defects" Let this run until it's finished, and it will check the entire CD for any errors. If there are any, consider re-downloading and re-burning at the slowest possible speed.

---

### Post by Sydius on 2010-12-06
> **isantop said:**
> It sounds to me like the CD you tried to use was bad. You might try checking it. To check it, press a key at the first screen you see when you boot from it (The purple one with the white symbols on the bottom). In the menu that appears, select a language, then select "Check CD for Defects" Let this run until it's finished, and it will check the entire CD for any errors. If there are any, consider re-downloading and re-burning at the slowest possible speed.

It would also hang at the cursor when I chose to check the CD from the menu.  This happened with both the Ubuntu 10.10 Desktop x64 CD as well as with the Ubuntu 10.10 NetBook CD.  I had used the Ubuntu 10.10 Desktop x64 CD before to install Ubuntu on my desktop and had no issues, but I popped it into my desktop anyway to check it and it passed without any problems.  As I mentioned in my original post, I also tried both versions of Ubuntu from a USB memory stick as well.

**Edit:** I also hang at the cursor if I choose the try-before-installing option, for what that's worth.

---

### Post by Sydius on 2010-12-06
I tried adding "xforcevesa noapic noapci nosplash irqpoll" in place of "quiet splash" per [this thread]("http://ubuntuforums.org/showthread.php?t=1474731").  A lot of text then scrolls past and it stops after "ata2: SATA link down (SStatus 0 SControl 300)", but I'm not sure if that's even an error or just more startup spam.  I didn't see anything else that jumped out as an error, but couldn't see most of it as it scrolled past too quickly.

---

### Post by Sydius on 2010-12-06
It seems to boot from the Ubuntu 10.04 Desktop CD.  So maybe it's something specific to 10.10 that it doesn't like?

Other things I tried (but didn't work):

[LIST]
[*]Reseated the hard drive
[*]Disabling the HD from BIOS then booting from 10.10 Live CD (both NetBook and Desktop)
[/LIST]

---

### Post by Sydius on 2010-12-06
While Ubuntu 10.04 Desktop x64 Live CD boots fine, installation stops at 93% with the status of "Configuring hardware..." ](*,)

**Edit:** The 10.10 x64 alternate image hangs (from USB memory stick) after choosing a keyboard layout and country.

**Edit 2:** I also tried the 10.10 x64 alternate image from a CD and it also hangs, though it doesn't seem to be a specific step--it just hangs after about a second or two of being on the language selection page.

---

### Post by Sydius on 2010-12-06
Success!  I was able to install using the **Ubuntu 10.04.1 x64 Alternate** CD.  Everything seems fine now, though I'm a little scared to upgrade now.

---

### Post by Sydius on 2010-12-07
It actually looks as if the HD is bad.  Running badblocks reports a number of bad blocks and smartmontools fails right away with a read error for both short and long tests.  I've sent an e-mail to support to ask about returning either the HD or the whole netbook for a replacement.

---

