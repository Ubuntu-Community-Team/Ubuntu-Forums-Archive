---
title: "ubuntu installs in UEFI ok on Windows xp rollover"
date: 2015-01-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-01-22
I was just experimenting with  Windows XP Rollover (Windows 10) in UEFI mode and there is no problem detecting Windows Booloader for GRuB.

Regards..

---

### Post by sudodus on 2015-01-23
Yes, I have made such a dual boot system too. Ubuntu managed to do it well.

But after some time (and Windows updates) Ubuntu was locked out - it was a Windows only boot. It happened twice, so I don't think it was 'by chance' but 'by intention'. It will be interesting to see if you experience something similar. I was running Ubuntu 14.04.1 LTS, and I guess you are running Vivid.

---

### Post by kansasnoob on 2015-01-23
> **sudodus said:**
> Yes, I have made such a dual boot system too. Ubuntu managed to do it well.

But after some time (and Windows updates) Ubuntu was locked out - it was a Windows only boot. It happened twice, so I don't think it was 'by chance' but 'by intention'. It will be interesting to see if you experience something similar. I was running Ubuntu 14.04.1 LTS, and I guess you are running Vivid.

Was Boot Repair able to fix that?

I really wish I had some UEFI hardware to test on ;)

---

### Post by ventrical on 2015-01-23
> **sudodus said:**
> Yes, I have made such a dual boot system too. Ubuntu managed to do it well.

But after some time (and Windows updates) Ubuntu was locked out - it was a Windows only boot. It happened twice, so I don't think it was 'by chance' but 'by intention'. It will be interesting to see if you experience something similar. I was running Ubuntu 14.04.1 LTS, and I guess you are running Vivid.


No . I installed the 14.04.1  daily trusty iso.

What build of enterprise are you using? I had a  rather buggy install experience. It uses the same installer as W8...

Regards..

edit:

I am using Evaluation Copy : Build 9841

---

### Post by ventrical on 2015-01-23
Also the W10 install will not shut-down. It goes into a suspend and wakes on mouse. That of ocurse is beyond the scope of this topic but I am just highlighting a possible bug with both the W8 and W10 builds that can affect accutae results during UEFI install of Ubuntu 14.04.1 or 15.04.

Regards..

---

### Post by sudodus on 2015-01-23
> **ventrical said:**
> No . I installed the 14.04.1  daily trusty iso.

What build of enterprise are you using? I had a  rather buggy install experience. It uses the same installer as W8...

Regards..

edit:

I am using Evaluation Copy : Build 9841

I used Windows Technical Preview (to become Windows 10) with md5sum:
```

9005dce26734bcde7f912c2c51ab1127  WindowsTechnicalPreview-x64-EN-US.iso
```

---

### Post by ventrical on 2015-01-23
> **sudodus said:**
> I used Windows Technical Preview (to become Windows 10) with md5sum:
```

9005dce26734bcde7f912c2c51ab1127  WindowsTechnicalPreview-x64-EN-US.iso
```

I am using

9841.0.140912-1613.FBL_RELEASE_CLIENTENTERPRISE_VOL_X64FRE_EN-US.ISO

Do you have a link to your DL.

Thanks..

Windows 10 valuation Copy Link:
[http://onhax.net/windows-10-download-links/](http://onhax.net/windows-10-download-links/)

---

### Post by sudodus on 2015-01-23
I have forgotten how I downloaded it. I'll plug in the drive and start the computer and check for the build statement:

Evaluation copy, Build 9841

So it should be the same version of Windows.

---

### Post by sudodus on 2015-01-23
> **kansasnoob said:**
> Was Boot Repair able to fix that?

I really wish I had some UEFI hardware to test on ;)

It would have been possible, it works in this computer ([my Toshiba]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/") and its UEFI system) to use Boot Repair. I  noticed it, but did not spend time looking at what happened in detail  or how to prevent it. I was running Windows Technical Preview and I  suppose it will change several times until it will be released.

---

### Post by ventrical on 2015-01-23
> **sudodus said:**
> I have forgotten how I downloaded it. I'll plug in the drive and start the computer and check for the build statement:

Evaluation copy, Build 9841

So it should be the same version of Windows.


Sounds good.

So belay my last request for link.

Regards..

---

