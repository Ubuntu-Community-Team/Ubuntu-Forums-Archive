---
title: "Laptop does not shutdown on critical battery"
date: 2007-06-28
forum: System76 Support
---

### Post by klato on 2007-06-28
Well, the subject pretty much explains my problem.

My power management preferences say to shutdown the laptop when the battery is critically low, but instead it just powers the system off in the blink of an eye.  No shutdown sequence, no nothing.  It's just as if I popped the battery out of my laptop.

This is a Gazelle Performance (gazp2) running Feisty.

Any ideas?  I know this worked before in Edgy

---

### Post by thomasaaron on 2007-06-29
Can any other Gazelle Performance (GazP4) users confirm this one?
I'm running the battery down on mine to test, but I've got two hours to go :-\"

I'll report back when she dies.

________ I meant GazP3_____________

---

### Post by tedrampart on 2007-06-29
there's a gazp4?  strange..

on my gazelle performance, it shuts down when the battery is low, I get  a warning (the one you're supposed to get), then it jumps into the shutdown screen.

---

### Post by nmtsunami on 2008-01-27
I have the exact same problem. My computer is a Lenovo T61 and the computer simply goes down when the battery is critical.

---

### Post by thomasaaron on 2008-01-28
Check your settings in System > Preferences > Power Management (Battery Tab).

---

### Post by conceptrat on 2008-02-06
I too had this problem but found that my acpi implementation seemed to be causing problems with the "time remaining" features.  So I made some changes the the gnome configuration using gconf-editor and that seems to have fixed not only the shutdown on critical problem but also the problem with the gnome-power-manager tooltip giving the incorrect "time remaining" figures.

What I changed via gconf-editor was:

Unchecked /apps/gnome-power-manager/general/use_profile_time
Unchecked /apps/gnome-power-manager/general/use_time_for_policy

I also changed:

Checked /apps/gnome-power-manager/general/network_sleep

in an attempt to fix a problem with my laptop not restarting the Network connection correctly at resume.  Seems to fix my little niggle.

I had to use gconf-editor because there doesn't appear to be any other way to change these settings via a GUI tool or the "gnome-power-manager" preferences.

Cheers
Julz

---

### Post by hihihi on 2008-06-21
I think you should go for laptop-mode tool instead of the solution above.
laptop-mode tools are not started by default but are very very handy for laptop users.

I am having the same problem with my new laptop (sony vaio fz31m).
gpm gives out battery-critical-low warning, so it is working correctly.
hibernation is working correctly, too, but nevertheless it wont hibernate on critical level.
so we need to change the laptop-mode settings.

1.) first of all make sure laptop-mode is enabled on battery (not default)

$ sudo gedit /etc/default/acpi-support

set line &#8220;ENABLE_LAPTOP_MODE&#8221; to &#8220;true&#8221;


from now on this will work automatically after restarting system, once you're on battery, laptop mode is activated.

to activate without restart on the fly:

$ sudo laptop_mode start

2.) now you need to edit laptop-mode-tools:

$ sudo gedit /etc/laptop-mode/laptop-mode.conf

set the
"Disable all data loss sensitive features"-option when the battery level to 1%:

MINIMUM_BATTERY_CHARGE_PERCENT=1

to enable auto-hibernation (hibernate on battery critical-low):

ENABLE_AUTO_HIBERNATION=1

HIBERNATE_COMMAND=/etc/acpi/hibernate.sh (this is my working hibernation script, point it to the script that works for you)

AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=3 (this value has to be higher than the "MINIMUM_BATTERY_CHARGE_PERCENT"-value and has to give your battery enough time to hibernate)

I hope this helps anybody searching for the answer.
cheers

---

### Post by tiger015 on 2008-06-24
NO. It does not help. I followed hihihi's instructions and was not able to even boot up my laptop.

---

### Post by hihihi on 2008-06-25
if u follow my instructions, nothing should ever break your bootup.
UNless you tryed to boot up after hibernating, but this requires a working hibernation script on your laptop, as mentioned above.
what kind of laptop do you have?

---

