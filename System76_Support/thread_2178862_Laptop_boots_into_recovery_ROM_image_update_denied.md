---
title: "Laptop boots into recovery: ROM image update denied"
date: 2013-10-05
forum: System76 Support
---

### Post by GatoViejo on 2013-10-05
Greetings:

My laptop is booting into the recovery section of BIOS setup. It says:

ROM image update denied
EFI_NOT_FOUND: Rom image is not loaded

If I escape out of the BIOS setup, it proceeds to boot normally (or nearly normally - I no longer get sound on YouTube but sound works otherwise; this may be an unrelated issue).

What should I do to clear up the boot issue?

Machine info:
system76driver version 13.04.10
Ubuntu 13.04
kernel: 3.8.0-31-generic #46-Ubuntu SMP
model: lemu4

Thanks,
-- Mark

---

### Post by jbwyatt4 on 2013-10-19
Same issue as you-just happened today. Same OS and lemur4.

How do you escape out of bios? I choose exit without saving but it keeps booting into bios.

---

### Post by GatoViejo on 2013-10-19
I just hit escape and exit without saving and it proceeds to boot normally.

I entered a support ticket on this and they said that the EFI shell option can be disabled in the BIOS, but they were not specific about how and I have not yet found that option.

Can you boot to a dvd or a usb device?

---

### Post by clvx on 2014-06-02
> **GatoViejo said:**
> I just hit escape and exit without saving and it proceeds to boot normally.

I entered a support ticket on this and they said that the EFI shell option can be disabled in the BIOS, but they were not specific about how and I have not yet found that option.



Did you figure out how to solve it?

I'm having this same issue, and it happened after installing qemu-kvm and restarting. After that, I prompt everytime to BIOS with the error message:

"ROM image update denied EFI_NOT_FOUND ROM image is not loaded "

So far, I haven't found a workaround.

---

### Post by jamiekrug on 2014-06-05
I just ran into this same issue, yesterday. I've reviewed every single detail I could find in the BIOS setup, and I have not found a fix. There's a boot override option that allows me to select my SSD drive and boot normally, but I get bounced to that recovery error message in the BIOS setup every time I reboot.

System76 Model: lemu4
OS Version: Ubuntu, 14.04, trusty
Kernel Version: 3.13.0-27-generic

---

### Post by jamiekrug on 2014-06-05
I was finally able to resolve this merely by fully powering off my laptop! System76 support suggested I reset BIOS to default settings and fully power off. I had already tried default settings (and just about everything else), but I was always using either the Save Changes and Reset or Discard Changes and Reset option (or the Boot Override). I never fully powered down. Once I did so, everything is back to normal. I have no idea what caused this issue to begin with, and System76 has never been able to reproduce it.

---

### Post by rayx2 on 2015-04-15
> **jamiekrug said:**
> I was finally able to resolve this merely by fully powering off my laptop! System76 support suggested I reset BIOS to default settings and fully power off. I had already tried default settings (and just about everything else), but I was always using either the Save Changes and Reset or Discard Changes and Reset option (or the Boot Override). I never fully powered down. Once I did so, everything is back to normal. I have no idea what caused this issue to begin with, and System76 has never been able to reproduce it.

Hi, How to solve this problem, Just power off fully?

---

### Post by jamiekrug on 2015-04-16
> **rayx2 said:**
> Hi, How to solve this problem, Just power off fully?

Yes, simply power off fully, then power on--not just reboot without power off.

---

### Post by Skaperen on 2015-04-18
since hackers can't do a BIOS update with a manual power cycle then this is safe for EFI to allow.  keep this in mind for other EFI machines when windows 8 needs to go away.

---

