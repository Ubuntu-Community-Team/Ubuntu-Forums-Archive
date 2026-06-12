---
title: "Acer Aspire One Cloudbook FN+Brightness doesn't work, mouse freezes sometimes"
date: 2016-04-14
forum: Ubuntu Development Version
---

### Post by Holy_Chuck on 2016-04-14
Hey Guys,
As stated in the title, I am running Ubuntu "Xenial Xerus" 16.04 LTS on my Acer Aspire One Cloudbook 11 AO1-131-C58K. However, while I can use FN+Hotkeys to change the volume, the hotkeys for Brightness settings, in my case F1 and F2 do not seem to work with the FN key. I am currently using xbacklight to change brightness via Terminal but I would love to be able to use my FN Hotkeys again.
I appreciate every help I can get.

Oh, I have tried those various combinations of stuff to edit in grub, that people with similar problems tried, and I also tried a lot of other ways, whatever I could find... Nothing seemed to work so far..



Also I am using the touchpad mouse, which seems to freeze out of reason sometimes. It happens after 2 minutes of work or even 2 hours. The only fix for me is to restart the pc. I am unable to reproduce the error for troubleshooting so far.

Thanks for your efforts.

---

### Post by justen_m on 2016-04-15
Well, I've got Acers running 16.04. One is a newer Aspire v5, the other an Ancient Aspire One.
For the former...
GRUB_CMDLINE_LINUX_DEFAULT=“acpi_osi=Linux acpi_backlight=vendor”
For the latter...
I didn't have to change anything. Sorry that doesn't help.

I've got a new ASUS laptop, and haven't found anyway to get the keyboard screen brightness keys to work, but the keyboard backlight brightness keys DO work. I tried the above, and also
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=intel"
but neither helped on the ASUS. Maybe one would work for you. I also manually change the brightness via terminal or settings menu.

---

### Post by Holy_Chuck on 2016-04-21
Thanks for your effort, justen_m.
Sadly none of the above was helpful to me, but I did not give up yet, even though I am starting to run out of ideas.
I was thinking that there may be a driver problem, or rather an additional driver that would help me and I just haven't found it yet..
Sadly I am not really experienced in this area.
Hopefully someone can help.

---

### Post by morngrar2 on 2016-07-01
> **Holy_Chuck said:**
> Hey Guys,
As stated in the title, I am running Ubuntu "Xenial Xerus" 16.04 LTS on my Acer Aspire One Cloudbook 11 AO1-131-C58K. However, while I can use FN+Hotkeys to change the volume, the hotkeys for Brightness settings, in my case F1 and F2 do not seem to work with the FN key. I am currently using xbacklight to change brightness via Terminal but I would love to be able to use my FN Hotkeys again.
I appreciate every help I can get.

Oh, I have tried those various combinations of stuff to edit in grub, that people with similar problems tried, and I also tried a lot of other ways, whatever I could find... Nothing seemed to work so far..



Also I am using the touchpad mouse, which seems to freeze out of reason sometimes. It happens after 2 minutes of work or even 2 hours. The only fix for me is to restart the pc. I am unable to reproduce the error for troubleshooting so far.

Thanks for your efforts.

I've just today got my cloudbook 11 (AO1-131-C39W), and I have the same problems as you. The most irritating thing, for me, is the touchpad. The enable/disable Fn-key doesn't work for this either. I've tried toggling it on and off from the terminal with xinput set-prop and it works nicely. However, when the touchpad has randomly frozen the xinput command does not work.

One idea I got was to go into BIOS and change the touchpad from "advanced" to "basic" (It might've been something other than "basic", but there should only be two choices). I'm currently testing this now to see if it gets rid of the random freezes. I'll post back here if it does!

---

### Post by morngrar2 on 2016-07-01
> **morngrar2 said:**
> 
One idea I got was to go into BIOS and change the touchpad from "advanced" to "basic" (It might've been something other than "basic", but there should only be two choices). I'm currently testing this now to see if it gets rid of the random freezes. I'll post back here if it does!

This seems to have fixed the random touchpad freezes. But only time will tell. The Fn-key for enabling and disabling the touchpad now works.

---

