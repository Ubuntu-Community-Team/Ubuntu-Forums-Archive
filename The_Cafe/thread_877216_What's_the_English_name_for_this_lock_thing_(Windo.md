---
title: "What's the English name for this lock thing (Windows OEM on laptops)"
date: 2008-08-01
forum: The Cafe
---

### Post by Ishimaru Chiaki on 2008-08-01
Hello.

I am seeking your help because there's an English name I just can't find for something I would like to mention when I talk about M$'s nasty deals with PC builders, so everytime I try to post something related to this on an English board (Forumotion support forum, for example), I delete my post before I even send it.  For information, English isn't my mother tongue, I'm French from Québec.

On the French Ubuntu community, there is something that is very documented and that we froggies call "tatouage".  But I just can't find the equivalent English name, whatever I type these keywords on Google : Windows, OEM, Ubuntu, Packard Bell, lock, issue, watermark, watermarking, watermarked
I just can't find relevent English articles about this issue.  It doesn't seem as much documented than on the French side.

What I talk about is a kind of forced sale technique which has been dealt between M$ and a few builders (Packard Bell, HP, Médio, Gericom, Dell...).
This technique is a kind of lock which is used with OEM versions of Windows with a restore partition, and it consists on watermarking the Windows' MBR or locking the BIOS.  If someone installs Ubuntu (or another Linux distro) and decides to install GRUB on the MBR, Windows won't boot, or worse, the machine won't boot since Windows detects that something is missing, and this technique told it to refuse booting if this happens.  This issue is more frequent on laptops from builders I mentioned above.

Some tips have been found to install Ubuntu without affecting the MBR : install with the Alternate CD and install GRUB on Linux's root partition.

For those who understand French, here is the documentation about this issue, so you will understand better what I mean : [http://doc.ubuntu-fr.org/windows/pc_tatoue](http://doc.ubuntu-fr.org/windows/pc_tatoue)

Thanks in advance.

Ishimaru

---

### Post by cardinals_fan on 2008-08-01
Dang, my French needs work.  Back to school next month ;)

---

### Post by dca on 2008-08-01
You may need translation & it doesn't really reference it by name but certain users that try to dual-boot with new Vista SP1 will run into a problem:
 
[http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm](http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm)

---

### Post by mikewhatever on 2008-08-01
the term you are looking for may be vendor lock-in.
[http://en.wikipedia.org/wiki/Vendor_lock-in#Microsoft](http://en.wikipedia.org/wiki/Vendor_lock-in#Microsoft)

Edit: Read your post again and got the idea this time.I've never head of anything like this on OEM machines or not.

---

### Post by dca on 2008-08-01
Hey!  On that note call IBM, one of their (possibly more) Think Pad laptops would only operate with the same exact Fujitsu HDD if the orig crashed.  The BIOS would indicate that it's not an auth replacement OEM part and yadda yadda yadda and not work, flat-out stall.  I'm sure Apple's BIOS screams if ANY part is replaced by a non-OEM part.

---

### Post by dca on 2008-08-01
> **mikewhatever said:**
> the term you are looking for may be vendor lock-in.
[http://en.wikipedia.org/wiki/Vendor_lock-in#Microsoft](http://en.wikipedia.org/wiki/Vendor_lock-in#Microsoft)

That's on the OS/Office (software) suite side, though...  Forcing you to upgrade those when newer vers come out and incompatibilities exist between old & new?

---

### Post by the8thstar on 2008-08-01
Although tatouage translates as tattooing, I would rather say that the PC are TAGGED in this instance, because it's the MBR that's marked.

---

### Post by the8thstar on 2008-08-01
> **dca said:**
> That's on the OS/Office (software) suite side, though...  Forcing you to upgrade those when newer vers come out and incompatibilities exist between old & new?

This hasn't happened to me when I upgraded to SP1. My guess is that it only affects Vista versions with BitLocker.

---

### Post by jayemcee on 2008-08-01
Dual boot rather suggests that one might want to load up MS Windows again after trying Ubuntu. Doesn't really sound likely ;)

---

### Post by gn2 on 2008-08-01
I've seen this vile phenomenon referred to as "BIOS Locked" in English.

---

### Post by the8thstar on 2008-08-02
Maybe **Dirty Hustling** could apply too.

---

### Post by mips on 2008-08-02
> **dca said:**
> Hey!  On that note call IBM, one of their (possibly more) Think Pad laptops would only operate with the same exact Fujitsu HDD if the orig crashed.  The BIOS would indicate that it's not an auth replacement OEM part and yadda yadda yadda and not work, flat-out stall.  I'm sure Apple's BIOS screams if ANY part is replaced by a non-OEM part.

HP & IBM also do that with wireless cards on their laptops. Don't know if this is still the case though. Inserting a genuine Intel card into the machine will not work, inserting the exact same HP branded card into the machine does work. I found this out with my hp nx6110. I resorted to a firmware hack on the wlan card, was not to comfortable hacking my bios.

---

