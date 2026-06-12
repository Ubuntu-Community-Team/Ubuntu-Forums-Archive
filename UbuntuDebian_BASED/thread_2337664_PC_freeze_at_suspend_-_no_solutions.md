---
title: "PC freeze at suspend - no solutions"
date: 2016-09-20
forum: Ubuntu/Debian BASED
---

### Post by tachionx on 2016-09-20
Dear all,

I have an AUSUS NF55 laptop with Nvidia GT555M graphic card.
I have installed peppermint OS 7  - 64 BIT  (=Ubunto 16.04 with LXDE environment).
In all my other laptops everything is working fine.

In this one I cannot suspend the pc at all! 
No matter If I close the lid or press on the suspend button in the menu or after ctrl+alt+del.
Everything goes off (disk, keyboard, monitor) but after 30 seconds the fan starts to run crazy and the temperature increase a  lot.

The only way to stop the hung is to press the power button for 5 second. Everything get off, fan included. The white led on the power button blinks.
If I press the power button again it seems that something is waking up, the disk starts but then after 1 second everything is staked again, no monitor,no disk,no keyboard, nothing.
So I have to press the power button again for 5 second and everything shut down again but this time no white led blinking on the powerbutton
If I press the power button again the system boot normally.

I tried to put initcall_debug no_console_suspend ignore_level log_buf_len=16M as booting option.
But then when I call dmesg after booting, it seems I only have information on the actual booting session and not on the previous problematic suspend!
In the dmseg there are some warning regarding ACPI. So I also tried to set acpi=off as booting option in grub and reboot.But i cannot test suspend because it is diable. So I removed acpi=off.

I tried also sudo PM_DEBUG=true pm-suspend. After the problematic suspend and the reboot, I have the log in /var/log/pm-suspend.log. 
But I am new in linus so I don't know how to read it


I have read many forums in these days and I have tried many suggestion without any result:

- Kernel from 4.4.0-36 to 4.7.4 do not solve the problem
- all the graphic drivers give the same error (Nuveaux or Nvidia 361 propretary, tested)
- using nomodeset and disabling the i915  module does not work
- acpi=off doesn't work
- setting a hook in /etc/pm/sleep.d like 20_custom_ehci_hcd (suggested in thecodecentral.com website)
- I don't have the possibility to set XHCI enable in my BIOS so also this solution cannot be used

I am really frustrated and too newbi to be able to solve this problem alone.

Could you please help me finding solution?

thanks in advance

---

### Post by DuckHook on 2016-09-20
*Thread moved to **Ubuntu/Debian BASED** as the more appropriate forum.*

We frequently get posters who believe that, because another distro is "based" on one of the 'buntus, that they can get answers on Ubuntu forums. This is not true any more than Ubuntu users can get proper answers posting on the Debian forums.

Each distro customizes many things from its DE to its configuration files to the kernel itself. Unless forum members also run that distro, we don't know what those differences are. Without such knowledge, not only is it difficult to help, but we may actually end up misguiding you.

I recommend that you try the Peppermint forums for the help you seek.

---

### Post by tachionx on 2016-09-22
I have tried again. Suspend dos not work at all.
Hibernate works perfectly.

Does this can point out a more specific problem?

---

### Post by tachionx on 2016-09-22
moreover I have to add that during the freeze of suspend the CAPSLOCK turns on, fix until I manually force-reboot the sytem

---

