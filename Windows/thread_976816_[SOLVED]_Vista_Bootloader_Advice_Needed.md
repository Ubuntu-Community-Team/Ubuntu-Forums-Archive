---
title: "[SOLVED] Vista Bootloader Advice Needed"
date: 2008-11-09
forum: Windows
---

### Post by Vince4Amy on 2008-11-09
I already had Vista on this computer but I installed another copy of Vista on another hard drive on the same computer after because I needed it to test some applications.

I have now removed the other copy of Windows, however when I boot Windows the Bootloader still shows a choice of:

Earlier Operating Systems (There are none and never have been)
Windows Vista.. etc

It no longer shows the other Windows Vista which I have removed, and I've ran the commands

fixboot
fixmbr

From the Vista DVD but it still gives me the choice of earlier OS's and my Vista install. I have set it to boot from my Vista install by default but I can't set the timeout to 0 (minimum is 3 seconds) so this displays for 3 seconds. Before I installed the other Vista on the other drive the boot loader would just boot this copy of Windows with nothing else previous to this.

---

### Post by RoyalShrubber on 2008-11-09
> **Vince4Amy said:**
> I already had Vista on this computer but I installed another copy of Vista on another hard drive on the same computer after because I needed it to test some applications.

I have now removed the other copy of Windows, however when I boot Windows the Bootloader still shows a choice of:

Earlier Operating Systems (There are none and never have been)
Windows Vista.. etc

It no longer shows the other Windows Vista which I have removed, and I've ran the commands

fixboot
fixmbr

From the Vista DVD but it still gives me the choice of earlier OS's and my Vista install. I have set it to boot from my Vista install by default but I can't set the timeout to 0 (minimum is 3 seconds) so this displays for 3 seconds. Before I installed the other Vista on the other drive the boot loader would just boot this copy of Windows with nothing else previous to this.

Try Control Panel -> Advanced tab -> Settings button at the bottom under Startup and Recovery and uncheck 'Time to display list of operating systems'.

If this doesn't suffice you can use freeware tool with which you can edit vista's bootloader configuration: [http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1") :)

---

### Post by Vince4Amy on 2008-11-10
Thanks for that I'll try it when I get home, though I'm amazed I overlooked this. 

Thanks it's solved now.

---

