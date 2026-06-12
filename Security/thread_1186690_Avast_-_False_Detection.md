---
title: "Avast - False Detection?"
date: 2009-06-13
forum: Security
---

### Post by mharrison on 2009-06-13
I was running a virus scan on /home/ and when Avast was scanning my VirtualBox hard drives it was saying the VDI Hard drive file was infected with a Win32:Small-HUF [TRJ].

Now, I think this is just a false reading, as I also have Avast running on the actual virtual machine (Win2000) and it came back clean.

Just wondering if anyone else here who runs Avast has had the same reading on a VirtualBox file.

---

### Post by pietjanjaap on 2009-06-14
[http://www.virustotal.com/](http://www.virustotal.com/)
Check with this site. I do not know if you windows for this.

---

### Post by mharrison on 2009-06-14
> **pietjanjaap said:**
> [http://www.virustotal.com/](http://www.virustotal.com/)
Check with this site. I do not know if you windows for this.

I'm positive that this file is not infected as my VirtualBox hard drive for my Debian 5 virtual machine shows up with the same result....I was asking if anyone else has confirmed the same result.

---

### Post by bobince on 2009-06-16
Names like ‘Small’, ‘Delf’ or ‘Agent’ means “some kind of small loader trojan thing probably, we don't really know what it is because we can't possibly analyse every EXE thoroughly any more given today's quantity of malware”.

Clearly that doesn't apply to your VDI file. Google sez your particular detection was also found in a Windows coredump, so it looks like the kind of thing that is more likely to trigger at random from large quantities of data, and less likely to be meaningful.

AV gets less and less effective, and more prone to false positives, by the month. :-(

---

