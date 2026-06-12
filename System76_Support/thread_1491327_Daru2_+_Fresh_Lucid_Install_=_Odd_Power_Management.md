---
title: "Daru2 + Fresh Lucid Install = Odd Power Management"
date: 2010-05-23
forum: System76 Support
---

### Post by werewolves on 2010-05-23
I have a Daru2.  I've just done a fresh install of Lucid 32bit.  Everything seems to be working fine except power management.

Power readings are fine until I unplug the power cord.  When I unplug the cord, it will pop up a warning that says I have 2 minutes of battery life (even though it will show the correct battery fill ie. 93%) and the machine will hibernate, even if I click "cancel" on the popup dialog.

Any suggestions?

---

### Post by Flyers2391 on 2010-05-23
> **werewolves said:**
> I have a Daru2.  I've just done a fresh install of Lucid 32bit.  Everything seems to be working fine except power management.

Power readings are fine until I unplug the power cord.  When I unplug the cord, it will pop up a warning that says I have 2 minutes of battery life (even though it will show the correct battery fill ie. 93%) and the machine will hibernate, even if I click "cancel" on the popup dialog.

Any suggestions?

I've seen this happen on a Windows laptop before ... do you know if your battery is still in good shape?  I'm not sure the best way to test (there is probably a utility around) but if you change your power settings to not hibernate on low battery, does it last more than 2 minutes?  Do you see the % life remaining plummet?

---

### Post by werewolves on 2010-05-23
> **Flyers2391 said:**
> I've seen this happen on a Windows laptop before ... do you know if your battery is still in good shape?  I'm not sure the best way to test (there is probably a utility around) but if you change your power settings to not hibernate on low battery, does it last more than 2 minutes?  Do you see the % life remaining plummet?

No, the battery is not in great shape, but it's also not bad enough that I only have 2 minutes once it's unplugged.  I usually get about an hour.  No, the percentage does not plummet.

This behavior only started with Lucid.  I was on Linux Mint 8 before.  I also had this behavior on Mint 9, so I assume it is a Lucid issue, maybe the kernel?

Unfortunately, I can't set it not to do anything when the battery is critically low.  The only options in the power settings are "Suspend", "Hibernate" and "Shut Down".

---

### Post by jdb on 2010-05-24
> **Flyers2391 said:**
> I've seen this happen on a Windows laptop before ... do you know if your battery is still in good shape?  I'm not sure the best way to test (there is probably a utility around) but if you change your power settings to not hibernate on low battery, does it last more than 2 minutes?  Do you see the % life remaining plummet?

I just loaded Lucid on my Daru2 & it acts the same way it did on Kola.

When I unplug the power is says 98% charged, 4 minutes remaining.
A box pops up & says it's critically low & will hibernate if I don't plug it in.
I click cancel & the box goes away.
I click on the battery icon & it says I have around 4 hours left.

Power reporting has always been flakey on the Daru2.

jdb

---

### Post by werewolves on 2010-05-24
> **jdb said:**
> I just loaded Lucid on my Daru2 & it acts the same way it did on Kola.

When I unplug the power is says 98% charged, 4 minutes remaining.
A box pops up & says it's critically low & will hibernate if I don't plug it in.
I click cancel & the box goes away.
I click on the battery icon & it says I have around 4 hours left.

Power reporting has always been flakey on the Daru2.

jdb

Well, I wish that would work for me.  When I click on cancel, it still hibernates.  My power management was fine on Mint 8 (so it's not *only* the Daru2), but I really would like to use the features in Lucid...

---

### Post by jdb on 2010-05-24
> **werewolves said:**
> Well, I wish that would work for me.  When I click on cancel, it still hibernates.  My power management was fine on Mint 8 (so it's not *only* the Daru2), but I really would like to use the features in Lucid...

Open a terminal & type:

gconf-editor

open the apps menu

open the gnome-power-manager

click on actions

You can change the value of critical-battery from hibernate to nothing.

That will at least keep it from hibernating as soon as you unplug the power.

Hopefully it will at least intermittently report the correct battery level so you'll know when you're getting low.

If I learn anything more I'll post.

jdb

---

### Post by werewolves on 2010-05-24
> **jdb said:**
> Open a terminal & type:

gconf-editor

open the apps menu

open the gnome-power-manager

click on actions

You can change the value of critical-battery from hibernate to nothing.

That will at least keep it from hibernating as soon as you unplug the power.

Hopefully it will at least intermittently report the correct battery level so you'll know when you're getting low.

If I learn anything more I'll post.

jdb

Ahh, perfect, I figured there must be a way to do that.  That should work for now.

Actually, that's what's odd, the battery indicator displays the correct power.  The little fill indicator shows full (or less as time goes by).  If I click on it, it gives a reasonable approximation of time left.  But if I unplug the power, it will tell me there are two minutes left (even though it says 98% full).

Oh well, your fix will get me by for the moment, but if anyone has a suggestion for any logs or output I can send, I'd be happy to help.

---

### Post by werewolves on 2010-05-25
Is there a chance that 64 bit would work better, or am I just grasping?

---

### Post by thomasaaron on 2010-05-25
The only time power management worked well on the DarU2 was under Gutsy 64-bit, so it's worth a try. But it didn't work well in Hardy, Intrepid, Jaunty, or Karmic 64-bit.

---

### Post by werewolves on 2010-05-25
> **thomasaaron said:**
> The only time power management worked well on the DarU2 was under Gutsy 64-bit, so it's worth a try. But it didn't work well in Hardy, Intrepid, Jaunty, or Karmic 64-bit.

Yeah, I am still baffled as to what made it magically work under Mint 8, but it did.

I'll try 64 bit and report back.

---

### Post by williumbillium on 2010-06-11
> **werewolves said:**
> Is there a chance that 64 bit would work better, or am I just grasping?

I just booted into a 64-bit Lucid live USB and have the exact same problem.  On unplugging the power, it reported 2 minutes remaining/98% charged and immediately hibernated.

This is a regression as power management was perfect out of the box in Karmic.

There are several similar bugs listed in launchpad with mostly MSI machines affected:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541)

Here is a workaround mentioned in the tickets which is working for me so far.  In a terminal type:

gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false

(Alternatively run gconf-editor -> apps -> gnome-power-manager -> general -> uncheck use_time_for_policy

This will make gnome-power-manager use the battery charged percentage instead of time remaining for policy actions ([source]("http://live.gnome.org/GnomePowerManager/FAQ#My_time_to_discharge_is_always_incorrect_due_to_a_faulty_battery.2C_what_can_I_do.3F")).

I suggest subscribing to the first bug above and hopefully someone will find a real fix.

---

### Post by jdb on 2010-06-11
> **williumbillium said:**
> I just booted into a 64-bit Lucid live USB and have the exact same problem.  On unplugging the power, it reported 2 minutes remaining/98% charged and immediately hibernated.

This is a regression as power management was perfect out of the box in Karmic.

There are several similar bugs listed in launchpad with mostly MSI machines affected:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541)

Here is a workaround mentioned in the tickets which is working for me so far.  In a terminal type:

gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false

(Alternatively run gconf-editor -> apps -> gnome-power-manager -> general -> uncheck use_time_for_policy

This will make gnome-power-manager use the battery charged percentage instead of time remaining for policy actions ([source]("http://live.gnome.org/GnomePowerManager/FAQ#My_time_to_discharge_is_always_incorrect_due_to_a_faulty_battery.2C_what_can_I_do.3F")).

I suggest subscribing to the first bug above and hopefully someone will find a real fix.

Thanks,

jdb

---

### Post by MatthewPlanchard on 2010-07-01
I just wanted to confirm the workaround mentioned above.  Going into the gconf-editor -> apps -> gnome-power-manager -> general and unchecking use_time_policy stops both the warning and automatic hibernation.

---

### Post by isantop on 2010-07-02
It should. It will cause the power manager to use the battery percentage instead of the time left to decide when to hibernate, etc.

---

