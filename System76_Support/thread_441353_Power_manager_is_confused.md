---
title: "Power manager is confused"
date: 2007-05-12
forum: System76 Support
---

### Post by AusIV4 on 2007-05-12
I've just recently started using Kubuntu Feisty on my Gazelle. Lately, the power manager has been reporting that the battery is not present, even when it's unplugged an running on battery. It's not necessarily consistent - sometimes it will detect the battery for a while, then it just say "The battery has been removed."

Any help?

---

### Post by gotcha5 on 2007-05-13
Same problem here!

---

### Post by AusIV4 on 2007-05-13
Actually, this problem seems to be better now. I think this may have happened between applying some hal updates and rebooting. The power manager seems to be behaving properly now. I'll post if that changes.

[EDIT]
Never mind. After suspending and resuming the problem is back.

---

### Post by AusIV4 on 2007-05-15
I'm  back to my edgy partition again. My Gazelle wouldn't resume if it had been in suspend for more than a few hours (hibernate worked fine), and if it did resume, it was reporting completely bogus data about the battery. It didn't seem to know whether it was present, whether AC was plugged in or not, how much life was left on the battery, etc. Power management is rather important on a laptop.

---

### Post by AusIV4 on 2007-05-17
I filed a bug report, for anyone who wants to follow it.

[https://bugs.launchpad.net/system76/+bug/114932]("https://bugs.launchpad.net/system76/+bug/114932")

---

### Post by thomasaaron on 2007-05-18
Thanks.

We will have a look at it early next week.
Incidentally, is there a way for you to verify whether the problem is related to Kubuntu?
Is it whacked out under Ubuntu as well?

Best,
Tom

---

### Post by AusIV4 on 2007-05-19
I installed from a Kubuntu CD, and don't have the Ubuntu-desktop package installed. I can install it if it will help, but I'd rather avoid it.

I think this post is having the same problem:

[http://ubuntuforums.org/showthread.php?t=436535]("http://ubuntuforums.org/showthread.php?t=436535")

The symptoms seem fairly similar.

---

### Post by thomasaaron on 2007-05-20
Installing Ubuntu would be helpful.
While our driver will run on Kubuntu, we only officially support Ubuntu and do no testing with KDE.
It would be useful for us (and you) to know if the problem is related to the Kubuntu installation.

Seeing as how both this post and the one you referenced involve Kubuntu, I'm a little suspicious...

Best,
Tom

---

### Post by newlinux on 2007-05-20
I recently started getting this problem too. After a HAL update, and run KDE... ):

---

### Post by AusIV4 on 2007-05-20
> Installing Ubuntu would be helpful.
While our driver will run on Kubuntu, we only officially support Ubuntu and do no testing with KDE.
It would be useful for us (and you) to know if the problem is related to the Kubuntu installation.

Seeing as how both this post and the one you referenced involve Kubuntu, I'm a little suspicious...

Best,
Tom

First, when I purchased the Gazelle, I had been under the impression that Kubuntu was supported. I guess I was misinformed.

Secondly, the post I referenced makes no mention of Kubuntu or KDE - you may know that the person uses it from other interactions, but it is not mentioned there.

Lastly, I just installed the ubuntu-desktop package. The power manager didn't show up, but initially it was responding to unplugging the power by dimming th screen, and brightening it when the power was plugged back in. When I suspended and returned from suspend, it was no longer responding to the change in AC power availability.

I'm not familiar with Gnome, and I have quite a bit to do today, so I can't spend too much time figuring out how to get the power manager to show up (network manager also didn't show up), but perhaps tomorrow I'll try and figure out whether this problem is exclusive to KDE - right now, it doesn't look like it.

---

### Post by newlinux on 2007-05-20
I should note my problem is intermittent. I do have gnome installed, so If it starts happening more often then I will use gnome a bit and see if it happens there. I can confirm that in KDE gnome-power-manager still gets confused too - just a bit more info.

---

### Post by AusIV4 on 2007-05-20
I got gnome-power-manager working properly in Gnome this evening. Before suspending, it knew when it was plugged in, it knew when the battery had been removed, etc. After suspending and resuming, it reported that it was on AC power and the battery was empty, no matter what the state of the machine was: AC + Battery, AC + No battery, Battery + No AC, etc. This is exactly what I'm experiencing with the power manager in KDE.

Unless you think there's any chance having installed from the Kubuntu CD then installing the ubuntu-desktop package could be throwing off the results, I think it's safe to say this is not a Kubuntu issue.

---

### Post by newlinux on 2007-05-20
I'm running kubuntu-desktop on top of a ubuntu install, as another data point.

---

### Post by thomasaaron on 2007-05-21
I'm not sure we can assume that installing the Ubuntu Desktop on top of a Kubuntu CD installation proves KDE is not the culprit.

While I admit that you may very well be correct, I can also say that the only problems we're currently having  with power management involve KDE.

---

### Post by AusIV4 on 2007-05-21
I can now be completely certain that KDE has absolutely nothing to do with it. As I've just gotten a CPU and RAM, I decided it would be a good time to put in a new (bigger) hard drive I have lying around.I formatted this drive and did a clean install of Ubuntu 7.04 and I am having the exact same experience as I had before. After resuming from suspend, the power manager arbitrarily chooses a power state and reports that no matter what is actually the state of the power system.

Again, I'm having this problem with a completely clean install. It has nothing to do with KDE. The problem is somewhere between Ubuntu and the Gazelle V3.

---

### Post by thomasaaron on 2007-05-22
Thanks for following up on that.
Well, at this point, filing a bug report is the way to go, as this one is going to take some research to unravel.

[https://launchpad.net/system76](https://launchpad.net/system76)

Best Regards,
Tom

---

### Post by AusIV4 on 2007-05-26
Looks like I should have been updating my bug report, as Carl rejected it. I've updated the bug report to clarify that this is an issue with the Gazelle and Ubuntu, and has nothing to do with KDE. Hopefully he'll reopen it soon.

Additionally, I've done a little more research. I've added this to the bug report, but I thought it might get a wider audience if posted here:
> I decided to see how battery information is managed. I assume both Gnome power manager and KDE's Guidance power manager collect their data from /proc/acpi.

I ran the following commands

cat /proc/acpi/ac_adapter/AC0/state
cat /proc/acpi/battery/BAT0/alarm
cat /proc/acpi/battery/BAT0/info
cat /proc/acpi/battery/BAT0/state

Prior to suspend, they gave outputs that matched the state of the system and what the power manager reported. After resuming from suspend, those commands gave outputs that resembled what was being reported by the power manager, but not the actual state of the system.

I assume there is some kernel module that is not being reloaded properly after suspend and hibernate. Is there any way to reload modules individually to help determine which one is not being reloaded? If this can be determined, perhaps there will be one line to add to the /etc/default/acpi-support in order to get things working properly.

---

