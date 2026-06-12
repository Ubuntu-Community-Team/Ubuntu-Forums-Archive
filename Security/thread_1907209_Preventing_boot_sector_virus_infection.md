---
title: "Preventing boot sector virus infection"
date: 2012-01-10
forum: Security
---

### Post by jsvidyad on 2012-01-10
Hello,

  I am not sure if this is the correct forum to post this. So, I am also posting in security discussions forum.

  I want to prevent getting a boot sector virus by booting from an infected storage device. Now, I have set the BIOS so that the computer will boot only from the hard drive and from nothing else. The hard drive is first in boot sequence and is the only one with a number in front(only devices preceded by a number are bootable). 

Will this prevent getting a boot sector virus from an infected medium inadvertently left plugged into the computer at bootup/shutdown?

---

### Post by CharlesA on 2012-01-10
I haven't run into any boot sector virii in a long time - not since floppy disks were the norm.

If you have it set to only boot from the internal drive, there would be little to no risk of getting that type of virus.

---

### Post by Bucky Ball on 2012-01-10
This is pretty much a duplicate post of your other one (with a slightly different title). I have asked moderators to merge them. Duplicate posting is against forum rules. ;)

---

### Post by jsvidyad on 2012-01-10
I am not sure if my post was clear enough. What I wanted to know is if the above BIOS setting is enough to prevent getting a boot sector virus from an infected USB storage device/DVD/floppy left in the computer and in place when the computer boots up or shuts down.

---

### Post by jsvidyad on 2012-01-10
I mentioned that I was not sure where to put the post. Please put it in the appropriate forum.

---

### Post by CharlesA on 2012-01-10
> **jsvidyad said:**
> I am not sure if my post was clear enough. What I wanted to know is if the above BIOS setting is enough to prevent getting a boot sector virus from an infected USB storage device/DVD/floppy left in the computer and in place when the computer boots up or shuts down.
In short: Yes.

Long answer: You don't really need to worry about boot sector viruses anymore, as they aren't that common anymore. I'd be more concerned with phishing attacks or XSS than a boot sector virus.

BTW: I closed your other thread, since there were no replies.

---

### Post by Dangertux on 2012-01-11
I have to disagree with Charles at least on one point. The bios control mechanism you have in place offers you no real protection against MBR tampering. Though I do concede that this is not a common avenue of approach for most malware these days (TDSS not withstanding). 

That being said you have to realize that your MBR is not really ever going to be protected in that it will almost always be writeable. The exception there is that some high end server raid controllers give You some measure of control. 

Really securing your operating environment should be your top priority. Sorry if this is convoluted.

---

### Post by jsvidyad on 2012-01-16
Hello,

  I know that I can get a boot sector virus infection over the internet when I'm browsing using a windows OS. My question was regarding avoiding boot sector infection from infected media left in the computer alone. I am not concerned about getting it from the internet as I don't use windows at all.

---

### Post by Ms. Daisy on 2012-01-16
Is there a reason that you're focused on this one particular kind of virus?

---

### Post by OpSecShellshock on 2012-01-16
In order for a drive to be booted from, there has to be a bootable image on it and it has to be selected in the BIOS as a boot device. Also it has to be physically present. Absent any of those factors you're pretty well in the clear. Obviously the easiest factor to control is whether it's connected or not.

---

### Post by jsvidyad on 2012-01-25
> **OpSecShellshock said:**
> In order for a drive to be booted from, there has to be a bootable image on it and it has to be selected in the BIOS as a boot device. Also it has to be physically present. Absent any of those factors you're pretty well in the clear. Obviously the easiest factor to control is whether it's connected or not.

In the BIOS, only the Onboard SATA Hard Drive is set as bootable. It is the first device in the BIOS boot sequence list, is the only one in that list with a number in front and only devices preceded by a number are bootable. So, I guess I am protected from getting a boot sector virus from an infected medium(floppy/CD/DVD/USB storage device) left in the computer while shutting down or booting up the computer, right?

---

### Post by jsvidyad on 2012-01-25
> **Ms. Daisy said:**
> Is there a reason that you're focused on this one particular kind of virus?

I got a possible boot sector virus infection earlier.

---

### Post by OpSecShellshock on 2012-01-25
> **jsvidyad said:**
> In the BIOS, only the Onboard SATA Hard Drive is set as bootable. It is the first device in the BIOS boot sequence list, is the only one in that list with a number in front and only devices preceded by a number are bootable. So, I guess I am protected from getting a boot sector virus from an infected medium(floppy/CD/DVD/USB storage device) left in the computer while shutting down or booting up the computer, right?

Yes, you should be fine. For the most part when a boot sector virus is detected it is on the boot sector of whatever disk it's found on and shouldn't be much of a problem if that disk isn't booted from. Also most of them are old enough to be detected quickly.

---

### Post by jefelex on 2012-01-26
If you did boot in the past from an infected medium (floppy, USB, etc) then you may have a boot sector virus - changing the boot sequence afterwards is too late.  once the virus is written to the boot sector, then cleaning the boot sector is the only way to get rid of it.  Once it is cleaned up, (by whatever tool you use) then you may have a bios option that prevents writing to the boot sector on your hard drive - that will affect your grub bootloader, so you'll have to enable boot sector protection after you have a new grub bootloader installed, and have determined that the OS will never need to write there - and determining that is beyond my knowledge!

Good luck!
John

---

