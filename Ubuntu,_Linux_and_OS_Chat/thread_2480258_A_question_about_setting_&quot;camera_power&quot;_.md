---
title: "A question about setting &quot;camera_power&quot; for IdeaPad users"
date: 2022-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by ecuner on 2022-10-23
Hi everyone, i'm new in here :)

I'm using IdeaPad 520-15ikb (2017). Recently I wanted to toggle camera power via ideapad-laptop driver's camera_power sysfs node, but I noticed that it doesn't work. Moreover, I also noticed that reading it always gives me 1. Then I asked my friend to try this on his laptop(who is using some 2016 Legion laptop) and he got the same result.

So nowadays I'm preparing a patch to submit to mainline kernel, to hide camera_power node for whom it doesn't work on. (Patches will include more changes, but this isn't the place to explain them :P)

I've investigated ~10 ACPI tables (DSDTs) to see how I can understand whether the device supports toggling camera power via camera_power node, and I think I found a pattern. I think it should be working on laptops made before 2013-2014, and not on the ones made after that. However, I don't know if G500, G570, Y570 and U510 IdeaPads(2011-2013), which share similar DSDT structures, have working camera_power setting.

So, my question to 2013+ IdeaPad users is:
- Is changing camera_power setting works on you? I'll assume on most people it won't work, so if you have working camera_power on 2013+ IdeaPad and leave a reply here, I'll appreciate it.

And my question to G500, G570, Y570 and U510 IdeaPad owners are:
- Can you check if you can set camera_power, and then check the camera, and leave a reply here no matter it's working or not? I'll highly appreciate it.

Location of the camera_power setting is: [B]/sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/camera_power
[/B]You can set it via:
> echo _**0 or 1 here**_ | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004\:00/camera_power

Thank you very much! :)

---

### Post by ecuner on 2022-10-26
Looks like this forum isn't for this kind of things.

I found that camera_power should indeed work on G500, G570, Y570 and U510, and submitted the patches to mainline kernel: [https://lore.kernel.org/platform-driver-x86/20221026190106.28441-1-erayorcunus@gmail.com/T/#t](https://lore.kernel.org/platform-driver-x86/20221026190106.28441-1-erayorcunus@gmail.com/T/#t) Now waiting them to be reviewed.

So no further investigation is needed.

---

