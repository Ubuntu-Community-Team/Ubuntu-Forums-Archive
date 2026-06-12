---
title: "Battery is &quot;estimating&quot; forever, even after S76 driver install"
date: 2011-08-24
forum: System76 Support
---

### Post by CaptSaltyJack on 2011-08-24
I've run the System76 app and done "restore system" as well as "install drivers" (still not sure what the difference is). I thought I saw somewhere in the changelog that the driver update fixed the battery estimation issue. I've got a Bonobo P5.

---

### Post by CaptSaltyJack on 2011-08-24
Haha.. oh, this is sad, when the laptop can't figure out its own battery percentage, but it knows exactly where my iPhone stands. :lol:

[IMG]http://i.imgur.com/fyQKC.png[/IMG]

---

### Post by birdsarah on 2011-08-27
I have the same issue. If I click on Laptop Battery and it goes into the detailed information it knows how much battery life is left - just won't display it in the status bar....did you solve this?

---

### Post by CaptSaltyJack on 2011-08-27
No, but I did talk to System76 support, they said it's a known issue that is fixed in Ubuntu 11.10.

EDIT: If you're a programmer type, you can access the battery's charge level in /proc/acpi/battery/BAT0/state and its max capacity in /proc/acpi/battery/BAT0/info. I put together a little shell script that tells me the battery percentage. It'll do for now. :)

---

