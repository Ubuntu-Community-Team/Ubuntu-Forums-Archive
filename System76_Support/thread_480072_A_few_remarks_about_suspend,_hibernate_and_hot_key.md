---
title: "A few remarks about suspend, hibernate and hot keys on Darter"
date: 2007-06-21
forum: System76 Support
---

### Post by perce on 2007-06-21
Only minor remarks: suspend and hibernate both work, even if with some oddities, and all useful function keys now work.

Suspend: it is fast and reliable, but on AC it doesn't restore the brightness of the screen until I press Fn-F6. When I press that key once, it restores the brightness at it's full value; it doesn't go from zero to full brightness step by step as it does whee I press the key after turning off the brightness with Fn-F5. (I'm sorry if it's not clear, English is not my mother tongue). If I'm on the battery the screen comes back to life after a few seconds without any external input.

Hibernate: it is roughly as slow as a boot, so I almost never use it and I don't know how reliable it is. I don't now if it waits for something in the process, or if it's just the time needed to copy 1.5 GB to and from the disk. After resuming from hibernation power management is confused: it always thinks it is on he battery, but if it actually is on the battery, the battery applet doesn't show the charge correctly. Strangely enough, suspending and resuming brings power management back to life.

Fn-F9: it used to work (it is supposed to switch of the touchpad), but it doesn't work anymore.
The output on /var/log/acpid when I press Fn-F9 is the following:

[Thu Jun 21 00:48:10 2007] received event "hotkey ATKD 0000006b 00000002"
[Thu Jun 21 00:48:10 2007] notifying client 4776[107:114]
[Thu Jun 21 00:48:10 2007] notifying client 4935[0:0]
[Thu Jun 21 00:48:10 2007] executing action "/etc/acpi/asus-touchpad.sh"
[Thu Jun 21 00:48:10 2007] BEGIN HANDLER MESSAGES
Can't access shared memory area. SHMConfig disabled?
[Thu Jun 21 00:48:10 2007] END HANDLER MESSAGES
[Thu Jun 21 00:48:10 2007] action exited with status 1
[Thu Jun 21 00:48:10 2007] completed event "hotkey ATKD 0000006b 00000002"
[Thu Jun 21 00:48:10 2007] received event "hotkey ATKD 0000006b 00000002"
[Thu Jun 21 00:48:10 2007] notifying client 4776[107:114]
[Thu Jun 21 00:48:10 2007] notifying client 4935[0:0]
[Thu Jun 21 00:48:10 2007] executing action "/etc/acpi/asus-touchpad.sh"
[Thu Jun 21 00:48:10 2007] BEGIN HANDLER MESSAGES
Can't access shared memory area. SHMConfig disabled?
[Thu Jun 21 00:48:10 2007] END HANDLER MESSAGES
[Thu Jun 21 00:48:10 2007] action exited with status 1
[Thu Jun 21 00:48:10 2007] completed event "hotkey ATKD 0000006b 00000002"

Fn-F2 has a symbol on it, but apparently it does nothing, and gives no message on  /var/log/acpid.

---

### Post by thomasaaron on 2007-06-21
For the Fn-F9 key. I can confirm that.
However, I can also fix it! :)

in /etc/X11/xorg.conf, if you add an SHMconfig line to your touch-pad block to make it look
like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"

Then the Fn-F9 will enable and disable the touchpad.



The others might be best worked out in a bug report.


____________________________-

Edit:
As it turns out, running the system 76 driver will already fix the Fn-F9 key. 
But only if you run 'Restore.' This actually dumps in the proper xorg.conf file.

---

### Post by perce on 2007-06-21
> **thomasaaron said:**
> 

Then the Fn-F9 will enable and disable the touchpad.



Thank you, now it works again :)

> 

The others might be best worked out in a bug report.


 
There is already a bug report on suspend/hibernate on Darter, I'll add my remarks there.

> 
Edit:
As it turns out, running the system 76 driver will already fix the Fn-F9 key. 
But only if you run 'Restore.' This actually dumps in the proper xorg.conf file.

Restoring the _proper_ xorg.conf file? no way, after I've spent one day ti make the projector going to the corect resolution! 

I just remembered I had another observation about power management: the computer 
on the battery is cooler and less noisy than on AC. I's probably some power management feature which is activated only on the battery. Since I haven't noticed any decrease of performance for what I do, I'd like to have them always enabled if possible. 

A side remark: I'm glad to see that almost all main issues have been solved, and I'm looking forward to a fix for the CDrom problem. Only the rustle remains unaddressed, as it seems that I'm the only on experiencing it, or being bothered by it. It's a pity because it's the only thinks that prevents me to claim that my Darter is better than my friends' macbooks.

---

### Post by thomasaaron on 2007-06-21
> Only the rustle remains unaddressed

The rustle? I don't understand.

---

### Post by perce on 2007-06-21
> **thomasaaron said:**
> The rustle? I don't understand.

I mean the soft background noise I was complaining about the first day I received the computer.

---

### Post by thomasaaron on 2007-06-21
I just had an idea. It probably won't work, but I'd like for you to humor me and give it a try anyway.:D

I tried it on my shop Darter, and I can't hear any difference, but your ears are obviously more sensitive than mine.

In the BIOS menu, under the Power tab, there is a setting for LCD power saving when the battery is off. It essentially dims the monitor when the A/C is unplugged. By default, I think this setting is enabled.

We know that you can do that from Ubuntu's power management settings. But what if the BIOS is still allowing some sort of power draw that is making your fan run more/faster when the A/C is plugged in than the battery. (You did say it's noisier under A/C than with the battery...).

Try disabling that setting.

Of course, it could have the unwanted side-effect of not distinguishing at all between lcd brightness under A/C or Battery. Then it might just be noisy all the time. But at least we'll know where the problem is.

Best,
Tom

(I'll be amazed if that made any sense...)

---

### Post by perce on 2007-06-21
> **thomasaaron said:**
> 

I tried it on my shop Darter, and I can't hear any difference, but your ears are obviously more sensitive than mine.



Probably not, it's because I live alone. I will try your suggestion for sake of experiment, but it is really not  a big issue. It is also hard to quantify noise and heat because their perception is subjective and heavily influenced by the environment. 

> 
But what if the BIOS is still allowing some sort of power draw that is making your fan run more/faster when the A/C is plugged in than the battery. (You did say it's noisier under A/C than with the battery...).


I think something like that is really happening: if I can trust the sensors applet, when on the AC 
the fan starts when the computer goes above 46 degrees, while on he battery it starts after around 50. There was no difference in the two cases before the BIOS upgrade, so it definitely depends on the BIOS. However I saw no option to control the fan in the BIOS, so I think there is nothing we can do.

---

