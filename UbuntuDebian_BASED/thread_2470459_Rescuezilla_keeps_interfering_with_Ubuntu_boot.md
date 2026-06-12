---
title: "Rescuezilla keeps interfering with Ubuntu boot"
date: 2021-12-30
forum: Ubuntu/Debian BASED
---

### Post by Seafarer999 on 2021-12-30
Made the mistake of loading Rescuzilla into my Ubuntu 21. distro and now it prevents Ubuntu from loading. Have researched Google with many terms and combinations but nowhere can I find how to uninstall it, only how to load  Rescuezilla. Tried reinstalling Ubuntu, loading Debian over the top, flashing BIOS and everything/anything else I can think of. (I'm a noobi and followed recommendation of loading Rescuzilla as opposed to Timeshift to save all personal documents as opposed to just system.)

Allowed Rescuezilla to run for 24 hours with no indication of what it was doing or what it expected of me to do. Now, I just want to get rid of it!

Any assistance appreciated. Can provide computer specs from a BelArc report but please be specific on the request, using exact wording if possible as I am not a tech person.

Thank You,
Sonny

---

### Post by QIII on 2021-12-30
Did you try using a Live Session to re-partition the storage device to clean it up?

---

### Post by ajgreeny on 2021-12-30
In do not understand what you mean by your question. How did you install  Rescuezilla in your Ubuntu OS?

As far as I'm aware it is not an application that you install but an OS of its own, based on Ubuntu that is burned to a USB/CD/DVD and then that is used to boot the computer and rescue a broken installed OS.

---

### Post by rescuezilla on 2021-12-31
Hi Seafarer999,

I am the developer of Rescuezilla.

What steps did you run to get into this situation? Typically you would write the Rescuezilla ISO file onto a USB stick using a tool like belenaEtcher. Then you would restart your computer (pressing a key like F12) to boot into the USB stick, and therefore into the Rescuezilla live environment. This "live environment" makes no permanent changes to your computer at all. [B]Simply removing the USB stick (or DVD) and restarting will bring your computer back to the original state.
[/B]
But if removing the USB stick (or DVD) isn't enough, by any chance:

1. Did you use Rescuezilla to "restore" the Rescuezilla ISO file to your existing hard drive?
2. Or did you follow some advanced instructions page involving installing the Rescuezilla ISO file in your GRUB bootloader menu?

These two options would have "installed" the Rescuezilla tool onto your hard drive, which is an approach that is not recommended.

Please provide further information on the steps you have taken to get into this situation and I am happy to continue to provide assistance until the issue is resolved. Please let me know how you go!

---

