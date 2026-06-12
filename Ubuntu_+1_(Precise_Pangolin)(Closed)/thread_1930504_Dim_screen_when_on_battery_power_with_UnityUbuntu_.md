---
title: "Dim screen when on battery power with Unity/Ubuntu 12.04"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by WebDrake on 2012-02-23
I've just installed Ubuntu 12.04 on a new laptop.  This is the first time I've seriously used the new Unity interface, as I've been mostly a Kubuntu user for the last few years.

I have not been able to find a way to ensure that the screen brightness is reduced automatically when the laptop is running on battery power.  If I go to System Settings > Brightness and Lock, the "Dim screen to save power" box is ticked.  I can also alter the screen brightness manually here.  However, unless I do alter it manually, the laptop continues to operate at 100% brightness when the power cable is unplugged.

Conversely, if I've manually dimmed the display and then plug the power cable back in, it stays dim until I manually brighten it.

Is there any way within the Unity UI to determine screen brightness for different power statuses?  And if not, is there another way to configure it?

(Unrelated issue: the "Hibernate" option seems to be disabled, both manual hibernation and automatic.  Any advice on what might be the issue?  I have 8GB of RAM in this machine, and 9GB of swap, which I was assuming would be enough for hibernation purposes.)

---

### Post by LinuxFan999 on 2012-02-23
Ubuntu 12.04 is still alpha, so it is expected to have plenty of bugs.

I don't believe there is a way to configure screen brightness for different power statuses.

Also, you need at least twice as much swap as RAM in order to Hibernate.

---

### Post by matt_symes on 2012-02-23
Hi

> **WebDrake said:**
> I've just installed Ubuntu 12.04 on a new laptop.  This is the first time I've seriously used the new Unity interface, as I've been mostly a Kubuntu user for the last few years.

I have not been able to find a way to ensure that the screen brightness is reduced automatically when the laptop is running on battery power.  If I go to System Settings > Brightness and Lock, the "Dim screen to save power" box is ticked.  I can also alter the screen brightness manually here.  However, unless I do alter it manually, the laptop continues to operate at 100% brightness when the power cable is unplugged.

Conversely, if I've manually dimmed the display and then plug the power cable back in, it stays dim until I manually brighten it.


Are you getting an acpi power event when the power cord is plugged in and taken out ?

You can check this with

```
acpi_listen
```

> 
Is there any way within the Unity UI to determine screen brightness for different power statuses?  And if not, is there another way to configure it?

Not quite sure what you mean here. Are you talking about when the power adaptor is plugged in and taken out ? If you are then yes. It should be dimming if you set that option in system setting.

If that is not what you meant then can you elucidate ?

> 
(Unrelated issue: the "Hibernate" option seems to be disabled, both manual hibernation and automatic.  Any advice on what might be the issue?  I have 8GB of RAM in this machine, and 9GB of swap, which I was assuming would be enough for hibernation purposes.)

can you suspend by open a terminal and typing

```
sudo pm-hibernate
```

Do you get any error messages on the screen ? If so then post them back. If it does attempt to hibernate (or even if it doesn't) cehck for the file

```
/var/log/pm-suspend.log
```

If it exists then post it back here.

Kind regards

---

### Post by lisati on 2012-02-24
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by WebDrake on 2012-02-24
> **LinuxFan999 said:**
> Ubuntu 12.04 is still alpha, so it is expected to have plenty of bugs.It wasn't clear to me if this was a bug or the lack of a feature, hence the query.  Your response makes it seem likely it's the latter.  Slightly difficult to believe, as it's so standard ... :-(


> **LinuxFan999 said:**
> Also, you need at least twice as much swap as RAM in order to Hibernate.Ack.  I'd followed the guidelines at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) : *"The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size."*

---

### Post by WebDrake on 2012-02-24
> **matt_symes said:**
> Are you getting an acpi power event when the power cord is plugged in and taken out ?

You can check this with

```
acpi_listen
```
Yes, I'm getting the acpi events.  As power cable is unplugged:
```
ac_adapter AC 00000080 00000000
ibm/hotkey HKEY 00000080 00006040
ibm/hotkey HKEY 00000080 00006030
thermal_zone THM0 00000081 00000000
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001
``` and as it is plugged back in again:
```
ac_adapter AC 00000080 00000001
ibm/hotkey HKEY 00000080 00006040
ibm/hotkey HKEY 00000080 00006030
thermal_zone THM0 00000081 00000000
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001
```

> Not quite sure what you mean here. Are you talking about when the power adaptor is plugged in and taken out ? If you are then yes. It should be dimming if you set that option in system setting.

If that is not what you meant then can you elucidate ?  What I mean is that I can't find any way in the Ubuntu/Unity System Settings to set different default screen brightnesses for different power statuses.

As I said, I'm coming from KDE where I'm used to having a well-defined set of different power settings (Performance, Powersave, Aggressive Powersave, Xtreme Powersave, ...), all individually configurable.  I don't need to have quite that level of configurability, but what I want is to be able to set the default brightness level for when the power cable is unplugged.  If I could set different brightness levels for different battery remaining statuses, even better.

Thanks for all the advice!

---

### Post by matt_symes on 2012-02-24
Hi

You're getting ACPI event from the kernel, and that is good, so the problems is higher up.

Your scripts are set up correctly ?

```
ls -l /etc/acpi/events/battery 
```

```
ls -l /etc/acpi/power.sh
```

```
ls -l /usr/share/acpi-support/policy-funcs
```

upowerd is running ?

```
ps aux | grep [u]powerd
```

I'm not sure if it is possible to configure for different power management settings for brightness control though the GUI. You could always write your own scripts for it, of course.

LinuxFan99 is correct when he says that 12.04 is a development version so you must expect bugs, things not to work and for breakage to happen.

I would not recommend not using 12.04 until 12.04.1 unless you are prepared to fix any breakage that may happen.

That being said, i upgraded to 12.04 under a week after 11.10 came out and i have had a pretty good ride with it.

As for hibernate, can you hibernate with

```
sudo /usr/sbin/pm-hibernate
```

Can you post the log of the hibernation events.

```
cat /var/log/pm-suspend.log
```

Kind regards

---

### Post by WebDrake on 2012-02-24
Matt, thanks so much for all the detailed advice.

> **matt_symes said:**
> Hi

You're getting ACPI event from the kernel, and that is good, so the problems is higher up.

Your scripts are set up correctly ?

upowerd is running ?
Yes, all present.

> I'm not sure if it is possible to configure for different power management settings for brightness control though the GUI. You could always write your own scripts for it, of course.I was hoping that, if not GUI-configurable, I might be able to tweak an appropriate config file -- can you advise?

> LinuxFan99 is correct when he says that 12.04 is a development version so you must expect bugs, things not to work and for breakage to happen.I know; but I don't think this is a bug, rather a lack of configuration options in the GUI.

> As for hibernate, can you hibernate with

```
sudo /usr/sbin/pm-hibernate
```

Can you post the log of the hibernation events.

```
cat /var/log/pm-suspend.log
```Attached. :-)  The hibernate seemed to work fine using the command line as you describe, but it's greyed out as an option in the Power Settings (e.g. for "When power is critically low", "When lid is closed").

It's not a major issue, as this machine has quite a lot of battery life, but I would like to be able to set it to hibernate when remaining battery is too low.

---

### Post by WebDrake on 2012-02-24
> **lisati said:**
> *Thread moved to **Ubuntu +1 (Precise Pangolin)**.*Just to note: I deliberately avoided posting in the Ubuntu +1 forum as I assumed that these issues must be germane to all Unity-based Ubuntu versions.  Apologies if that isn't the case.

---

### Post by mc4man on 2012-02-24
Maybe give this a try - Starting  on **Ac** go to the "Brightness and Lock " screen

Uncheck the "dim screen to save power" option, leave it disabled for good

Make sure your screen is as bright as desired on **AC**, if not and the slider is all the way to the right then adjust with your keyboard controls

Now unplug the AC  -  going to battery power
Adjust the slider to the desired setting for when on battery

Check if plugging in AC returns brightness & unplugging dims

---

### Post by WebDrake on 2012-02-25
> **mc4man said:**
> Maybe give this a try - Starting  on **Ac** go to the "Brightness and Lock " screen

Uncheck the "dim screen to save power" option, leave it disabled for good

Make sure your screen is as bright as desired on **AC**, if not and the slider is all the way to the right then adjust with your keyboard controls

Now unplug the AC  -  going to battery power
Adjust the slider to the desired setting for when on battery

Check if plugging in AC returns brightness & unplugging dimsNope, doesn't work.  Screen just keeps whatever the current set brightness level is. :-(  Thanks for the thought though!

---

### Post by mc4man on 2012-02-25
> **WebDrake said:**
> Nope, doesn't work.  Screen just keeps whatever the current set brightness level is. :-(  Thanks for the thought though!

Maybe something related to your hardware/drivers, don't know

Can say that starting in 11.10, maybe also 11.04, have seen exactly the same on a few installs out of a couple of hundred. Usually it does work correctly without any need to adjust in System Settings

In the case of when there was no change in levels fooling around as I described would get it going.

Currently I can individualize the AC & battery levels by  simply setting the level on each. This can also be done on the Desktop by just using the FN & brightness up/down buttons, the settings are stored somewhere (?),  & hold.

This could be also done to the exact opposite of what's expected, set brightness to dim on AC, very bright on battery - so at least here the settings are user defined, not based on some static, normal expected parameters

---

### Post by WebDrake on 2012-03-10
> **mc4man said:**
> Maybe something related to your hardware/drivers, don't know

A small and belated follow-up, if nothing else just to thank you for your careful input.

I realized I should clarify one thing, to make sure we're not talking at cross-purposes.

The screen DOES dim on battery power, but only with inactivity -- the screen brightness reduces considerably if I don't do anything to the computer for more than about 15-20 seconds.  If I'm active, the screen returns to and remains at full brightness.

This contrasts with the behaviour I'm used to on KDE where there are different default (active) brightness levels depending on power status.

Is this a behavioural difference of Ubuntu/Unity rather than a bug?

---

### Post by matt_symes on 2012-03-10
Hi

> **WebDrake said:**
> A small and belated follow-up, if nothing else just to thank you for your careful input.

I realized I should clarify one thing, to make sure we're not talking at cross-purposes.

The screen DOES dim on battery power, but only with inactivity -- the screen brightness reduces considerably if I don't do anything to the computer for more than about 15-20 seconds.  If I'm active, the screen returns to and remains at full brightness.

This contrasts with the behaviour I'm used to on KDE where there are different default (active) brightness levels depending on power status.

Is this a behavioural difference of Ubuntu/Unity rather than a bug?

I think that is a behavioural difference because 12.04 on my laptop behaves in exactly the same way.

You could probably write your own scripts do do what you require though.

You can get the currently running governor from

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

and 

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq 
```

will give you the current operating frequency of cpu0. For a multicore system, there will be other cpu's as well (cpu1, cpu2, ...)

You can set the brightness based on this by setting this value

```
echo 9 | sudo tee /sys/class/backlight/*/brightness
``` 

On my laptop you can set value between 0 and 9. The script would need root privileges.

You can find the max brightness with

```
cat /sys/class/backlight/*/max_brightness
```

My sysfs name for my acpi video apadtor is acpi_video0. Yours may be different. This is for my machine.

```
matthew@matthew-Aspire-7540:~$ ls -l /sys/class/backlight/acpi_video0/
total 0
-r--r--r-- 1 root root 4096 Mar 10 13:15 actual_brightness
-rw-r--r-- 1 root root 4096 Mar 10 13:15 bl_power
-rw-r--r-- 1 root root 4096 Mar 10 12:53 brightness
lrwxrwxrwx 1 root root    0 Mar 10 13:15 device -> ../../../0000:01:05.0
-r--r--r-- 1 root root 4096 Mar  9 18:50 max_brightness
drwxr-xr-x 2 root root    0 Mar 10 13:15 power
lrwxrwxrwx 1 root root    0 Mar  9 16:38 subsystem -> ../../../../../../class/backlight
-r--r--r-- 1 root root 4096 Mar  9 18:50 type
-rw-r--r-- 1 root root 4096 Mar  9 16:38 uevent
matthew@matthew-Aspire-7540:~$
```

If your setup is similar to mine then this may give some inspiration.

Kind regards

---

### Post by mc4man on 2012-03-10
> Is this a behavioural difference of Ubuntu/Unity rather than a bug?
I don't think so  - just did a fresh install here where as usual the default has the level the same for both AC & battery (full on

And again here it's simply a matter of setting the  level while on either for either, slightly dimmed for battery, full on AC.

Maybe there is some hardware diff that doesn't allow you do do that?

---

### Post by matt_symes on 2012-03-10
Hi

> **mc4man said:**
> I don't think so  - just did a fresh install here where as usual the default has the level the same for both AC & battery

That is interesting. 

On my 12.04 64 bit install which was a fresh install from a daily build (unlike my 12.04 32 bit install which is an upgrade from Natty) i also get dimming on battery power.

It's not the type of things i would set myself so is lightly to be set from the initial install.

Maybe hardware related as you state.

Kind regards

---

### Post by kelpdip on 2012-03-10
If I'm not mistaken, this was one of the gnome3 regressions. This is possible in gnome2. I was hoping the gui system settings would be finished by the LTS, but it is unlikely.

---

### Post by mc4man on 2012-03-10
> **matt_symes said:**
> Hi



That is interesting. 

On my 12.04 64 bit install which was a fresh install from a daily build (unlike my 12.04 32 bit install which is an upgrade from Natty) i also get dimming on battery power.

It's not the type of things i would set myself so is lightly to be set from the initial install.

Maybe hardware related as you state.

Kind regards

Again - maybe hardware related - 
Here I don't have to even use System Settings > ..  to set per power source (though I do turn of the "Dim screen to save power option"

Anyway, just using the keyboard works fine on the machine - (FN+ up/down
So whatever is set while on battery is maintained for battery, same for AC

---

