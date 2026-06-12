---
title: "Recover Windows 10 Filesystem"
date: 2022-09-08
forum: Windows
---

### Post by vespertaria on 2022-09-08
My work computer no longer boots into windows 10. I first had some random blue screens, and then suddenly I could no longer boot windows.

I tried various windows tools, but no luck. I'm now on the ubuntu live cd. I tried boot-repair but that didn't work either. I also can't see my files in the file manager, which scares me.

I've copied the pastebin here: [https://paste.ubuntu.com/p/pv2Qw2g6HB/](https://paste.ubuntu.com/p/pv2Qw2g6HB/)

Is there anything I can try to save this without formatting and reinstalling?

---

### Post by vespertaria on 2022-09-08
Also, I should add, I have BitLocker on the Windows disk, so maybe that's why it's not showing up. I'm going to do some research to see if there's any way around this

---

### Post by TheFu on 2022-09-08
The general rules are these:
1. Use the OS that is native to the file system for all recovery efforts.
2. Whenever using any encryption, excellent backups are mandatory, since any physical or logical issue can block access to all files.
3. Never attempt data recovery onto the same storage with the issues.  Always use the recovery tool to read from physical device A and write to a different physical device B.  In short, don't trash the source.

Any good encryption will make the data appear as random bits, so don't expect data recovery tools from other OSes that don't natively understand the encryption to be much, if any help.  They could harm the source, which would be bad.

Even with all these warnings, if you still want to use Linux to attempt to recover random data, google "ubuntu data recovery" for a webpage just about that.

---

### Post by yancek on 2022-09-09
You will have much better luck going to a windows 10 forum or the support.microsoft site.  The links below have some suggestions.  Boot repair is designed to repair Linux bootloaders.  AFAIK, the only thing it will do with windows is create a chainload boot entry in Grub so you can boot windows.  If any windows boot files are corrupted or missing, it won't work.    Do you see any messages on screen when you try to boot?  There is generally an option for troubleshooting.

[https://www.windowscentral.com/how-troubleshoot-blue-screen-errors-windows-10](https://www.windowscentral.com/how-troubleshoot-blue-screen-errors-windows-10)

[https://www.makeuseof.com/tag/4-tips-fix-blue-screen-error/](https://www.makeuseof.com/tag/4-tips-fix-blue-screen-error/)

Boot repair doesn't show any information from windows only information on the drive, a 2TB SSD.  There is an entry for a windows 10 UEFI boot in the BIOS firmware.  If your windows files are not shown, boot repair may not be seeing them due to bitlocker or to having hibernation on in windows (this is the default).  Those are easy fixes if you can boot windows or some windows repair software.  You can not turn hibernation off from any Linux, not sure about bitlocker but I expect the same is true.  

The link below is to the microsoft support site dealing with BSOD, I'd try that first.

[https://support.microsoft.com/en-us/sbs/windows/troubleshoot-blue-screen-errors-5c62726c-6489-52da-a372-3f73142c14ad](https://support.microsoft.com/en-us/sbs/windows/troubleshoot-blue-screen-errors-5c62726c-6489-52da-a372-3f73142c14ad)

---

### Post by vespertaria on 2022-09-09
Thanks for the replies. I was hoping to avoid windows forums because in the past I’ve found them to be unhelpful, but I may give them a try as well. 


In case it helps anyone who finds this in the future, I was able to recover my file system by using TestDisk. This made the files visible in the file manager, which I could then unlock with the BitLocker password. TestDisk also fixed the boot loader problem, so I was able to reboot Windows, but the problem with Blue screens still persisted, so I’m doing a deeper check (virus scan, memory scan, etc) to figure out what’s going on. Interesting that the problems only seem to arise when using windows, so that gives me hope that they are software related and fixable (worst case by reinstalling windows).

---

### Post by mIk3_08 on 2022-09-10
> **vespertaria said:**
> My work computer no longer boots into  windows 10. I first had some random blue screens, and then suddenly I  could no longer boot windows.
I tried various windows tools, but no luck. I'm now on the ubuntu live  cd. I tried boot-repair but that didn't work either. I also can't see my  files in the file manager, which scares me.
I've copied the pastebin here: [https://paste.ubuntu.com/p/pv2Qw2g6HB/](https://paste.ubuntu.com/p/pv2Qw2g6HB/)
Is there anything I can try to save this without formatting and reinstalling?
In  my case, I've installed a new Linux Operating System to my second hdd  hard drive then I inserted my other hdd drive using enclosure where my  important files is stored so that I will never mistakenly erase  important files when I decide to install new Operating System. Regards  and cheers

---

