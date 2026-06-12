---
title: "Jack, pulse, pavucontrol &amp; pulseaudio problems"
date: 2014-03-20
forum: Ubuntu Studio
---

### Post by thomasmorey72-9 on 2014-03-20
So I upgraded to KXstudio from 12.04 LTS Studio......Great, but I just cannot stand "Jack" never have. Too time consuming and hit or miss at best. I was strolling through Ubuntu Software Center and installed a package for desktop add-ons and S**t!.  Now there is some message:

~$ pavucontrol

(pavucontrol:21960): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed


Then if you try to run pulseaudio this:

~$ pulseaudio
E: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
E: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_Oxygen_25-00-O25" card_name="alsa_card.usb-M-Audio_Oxygen_25-00-O25" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
W: [pulseaudio] module.c: module-combine is deprecated: Please use module-combine-sink instead of module-combine!
W: [pulseaudio] module-combine.c: We will now load module-combine-sink. Please make sure to remove module-combine from your configuration.


I am in trauma mode! I have uninstalled the offending package, but NOTHING, NOTHING will stop the onslaught! I need pavucontrol!! It is a Nessessity!! I just got a mssg from Update-Manager i could upgrade from 12.04 LTS "Precise Pangdolin" to 12.10 Studio "Quanta Quetzal". I want it to overwright this star configuration with the Blocking of "Pulseaudio", but most likely it will upgrade with the SAME issue.....

Truly Jackd-HELP

Thomas Morey

---

### Post by su:bhatta on 2014-03-20
What package did you install and other details that you can furnish will help.

I guess, it would be better to post the issue in KXStudio forums here : [http://www.linuxmusicians.com/viewforum.php?f=47](http://www.linuxmusicians.com/viewforum.php?f=47)

---

