---
title: "Track Pad Freezing On First Boot Issue still exists in Alpha 2!"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-02-02
Track Pad Freezing On First Boot Issue still exists in Alpha 2!

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> Track Pad Freezing On First Boot Issue still exists in Alpha 2!

Have you reported this bug?

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> Have you reported this bug?

I don't know how to, Launch Pad has a block on the Website preventing just plain anyone from filing a Bug Report where a Crash has NOT occurred or if you have NOT read the Release Notes! Just FYI!

---

### Post by xyzzyman on 2012-02-02
What is the model of touchpad? Then you'll be able to file a report using apport to the relevant xorg package. If you need help reporting a bug that's what the forum is for, but actual reporting of bugs isn't done here as it won't be seen and taken care of. Most likely if it's affecting others you'll be able to just add yourself to the list. The issue with the kernel panics has been finally fixed in 3.3 and is going to be in the next kernel release of 3.2 in PP. At least what seems to be the most common one that I've seen affecting people.

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> What is the model of touchpad? Then you'll be able to file a report using apport to the relevant xorg package. If you need help reporting a bug that's what the forum is for, but actual reporting of bugs isn't done here as it won't be seen and taken care of. Most likely if it's affecting others you'll be able to just add yourself to the list. The issue with the kernel panics has been finally fixed in 3.3 and is going to be in the next kernel release of 3.2 in PP. At least what seems to be the most common one that I've seen affecting people.

I don't know what type of Touch Pad I have. I was also very surprised that you said that the Kernel Panic Affects Realtek Storage Devices, as far as I am aware, the only Realtek Hardware that I have is My Realtek Integrated Ethernet Port, and My Realtek Integrated Sound Card. Just FYI!

---

### Post by xyzzyman on 2012-02-02
Did you read the bug report that you posted in today claiming it wasn't a change in the kernel that started it?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962)

If you had read it, you would see the patch is [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=b3ef051db763b640d1ff724b616ffba940896b44](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=b3ef051db763b640d1ff724b616ffba940896b44) which changes a single line in drivers/usb/storage/realtek_cr.c which is the driver for Realtek RTS51xx USB card readers...

**[SIZE="4"]Also FYI[/SIZE]** you do have a realtek RTS5159 card reader in that system:  [http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf](http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf)

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> Did you read the bug report that you posted in today claiming it wasn't a change in the kernel that started it?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962)

If you had read it, you would see the patch is [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=b3ef051db763b640d1ff724b616ffba940896b44](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=b3ef051db763b640d1ff724b616ffba940896b44) which changes a single line in drivers/usb/storage/realtek_cr.c which is the driver for Realtek RTS51xx USB card readers...

**[SIZE="4"]Also FYI[/SIZE]** you do have a realtek RTS5159 card reader in that system:  [http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf](http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf)

Thanks for sharing that info.

---

### Post by xyzzyman on 2012-02-02
I looked up on google and did your homework for you. You've been asked before to check what kind of trackpad you have and you ignored the request and the information of how to find out:

[http://ubuntuforums.org/showthread.php?t=1897259](http://ubuntuforums.org/showthread.php?t=1897259)

JUST FYI you have a synaptic trackpad, so check for an existing bug report on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bugs](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bugs). If there isn't one then read the sticky and submit a bug to that package. You may want to stick with 11.10 until 12.04 is released if you don't want to take the time to work out your issues. I personally am in 11.10 more often than 12.04 because I haven't had the time as I had during the 11.10 alpha's & beta's.

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> I looked up on google and did your homework for you. You've been asked before to check what kind of trackpad you have and you ignored the request and the information of how to find out:

[http://ubuntuforums.org/showthread.php?t=1897259](http://ubuntuforums.org/showthread.php?t=1897259)

JUST FYI you have a synaptic trackpad, so check for an existing bug report on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bugs](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bugs). If there isn't one then read the sticky and submit a bug to that package. You may want to stick with 11.10 until 12.04 is released if you don't want to take the time to work out your issues. I personally am in 11.10 more often than 12.04 because I haven't had the time as I had during the 11.10 alpha's & beta's.

Will you please try to go a little bit easier on me from now on? This is my first time back here (Alpha/Beta Testing Ubuntu) in a while just to let you know, and I am using different PC Hardware than I previously used here.

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> Will you please try to go a little bit easier on me from now on? This is my first time back here (Alpha/Beta Testing Ubuntu) in a while just to let you know, and I am using different PC Hardware than I previously used here.

[QUOTE=kevpan815 from back in the day]On my Dell Inspiron 1012 Mini Net Book PC I have a problem where my Mouse Track Pad is not working with Yesterday's Nightly Build Of Ubuntu 12.04. Sorry, but I don't know if it is Made by Dell or a Third Party.[/QUOTE]

Just to let you know, it's the same hardware.

---

### Post by effenberg0x0 on 2012-02-02
> **kevpan815 said:**
> I don't know how to, Launch Pad has a block on the Website preventing just plain anyone from filing a Bug Report where a Crash has NOT occurred or if you have NOT read the Release Notes! Just FYI!

Kevpan815, you can create a bug report using this link:
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

Regards,
EFfenberg

---

### Post by kevpan815 on 2012-02-02
> **effenberg0x0 said:**
> Kevpan815, you can create a bug report using this link:
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

Regards,
EFfenberg

Thanks for the link.

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> Just to let you know, it's the same hardware.

That's still 12.04, what I am saying is that I was virtually absent from here during 11.04 and 11.10 and maybe even 10.10 while I had no alternate way to hook this PC up the Internet other than my Dad's Comcast Connection (and he does NOT like Linux like I do).

---

### Post by xyzzyman on 2012-02-02
You said that you were using different hardware then with 12.04. All I did was quote you from before and you said you were using the same Dell netbook, contrary to what you are now claiming, and Effenberg tried to help you then but you just started a new thread about it instead of continuing the previous.

---

### Post by kevpan815 on 2012-02-02
> **kevpan815 said:**
> That's still 12.04, what I am saying is that I was virtually absent from here during 11.04 and 11.10 and maybe even 10.10 while I had no alternate way to hook this PC up the Internet other than my Dad's Comcast Connection (and he does NOT like Linux like I do).

P.S. Back during the 7.10, 8.04 LTS, and 8.10 days I was using both a Dell XPS 630I Desktop PC and a Dell Inspiron 530N Desktop PC. Most of the 3 computers and 1 Mac that I now own were NOT bought until the year 2010.

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> P.S. Back during the 7.10, 8.04 LTS, and 8.10 days I was using both a Dell XPS 630I Desktop PC and a Dell Inspiron 530N Desktop PC. Most of the 3 computers and 1 Mac that I now own were NOT bought until the year 2010.

So? Why are you bringing that up. You said you were using a different hardware than when earlier in the alpha for 12.04. Now you're changing your story. Whatever.

---

