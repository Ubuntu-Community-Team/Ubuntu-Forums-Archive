---
title: "Computer won't turn off"
date: 2009-11-17
forum: The Cafe
---

### Post by cartisdm on 2009-11-17
Ok, I know this is the Community Cafe but this is a windows problem so I didn't know where to post help (and this is my favorite forum;))

I'm building a computer for my boss and I have all new components in the desktop but for some reason the machine doesn't turn off fully.  I've tried it with Vista and 7, both same result.  I go to Start > Shutdown then the computer will turn almost all the way off but the system fans and lights stay on and won't shutdown 100%.  Any of you ever experienced this before?

I tried booting into some of my Ubuntu liveCDs to see if they would give the same result but for some reason this system doesn't want to boot into any of them and I dont have the time to diagnose it since linux isn't my priority.

---

### Post by amingv on 2009-11-17
I have seen some vista computers (particularly laptops) in which the default behavior for the shutdown button (even in the start menu) is to suspend/sleep.
You may want to check into that. You can change it through power settings or start menu properties.

---

### Post by alphaniner on 2009-11-17
My best guess would be a setting in the BIOS: ACPI or Power Management or something along those lines.

---

### Post by doas777 on 2009-11-17
if it won;t boot off cd, check your boot order in your bios. move the optical drive to the top, save and exit.
if it still won't make sure your optical drive is fully functional, and that your motherboard was manufactured after 2002.

---

### Post by cartisdm on 2009-11-17
> 
I have seen some vista computers (particularly laptops) in which the default behavior for the shutdown button (even in the start menu) is to suspend/sleep.
You may want to check into that. You can change it through power settings or start menu properties.

Double checked all those settings, the computer is set to shutdown

> **alphaniner said:**
> My best guess would be a setting in the BIOS: ACPI or Power Management or something along those lines.

I tried disabling the ACPI stuff but it wouldn't allow me to boot into windows so I had to change it back to the settings shown in the attached picture.

P.S. I got the liveCD (ubuntu 8.10) to boot up and when I did shutdown the computer turned off 100% (after that screen where it says remove the CD from tray)

---

### Post by cariboo on 2009-11-17
I'm not close to anything running Windows at the moment, but there is a setting in power management in the control panel in XP that you have to enable in order for the computer to shut down completely. I'm sure you'll find the same thing in newer versions.

---

### Post by cartisdm on 2009-11-17
Ok I dug a little deeper and found some information from [this site]("http://www.pchardware.ro/Articles/article.php?id=127").  It is for Windows 2000 but I think some of the info is still relavent.  Apparently if you want to disable the ACPI settings in the BIOS you must do something to your Windows configuration as well or else it won't boot properly anymore.

Anyone have any clue what this change might entail? I am pretty sure that if I am able to disable the ACPI function in the bios I will be able to turn off my computer completely

---

### Post by SunnyRabbiera on 2009-11-17
Its possessed!
Always knew Microsoft was allied with Satan ;)

---

### Post by pwnst*r on 2009-11-17
> **cariboo907 said:**
> I'm not close to anything running Windows at the moment, but there is a setting in power management in the control panel in XP that you have to enable in order for the computer to shut down completely. I'm sure you'll find the same thing in newer versions.

lol i've NEVER had to do anything in power management in either XP, Vista, or 7.  

so, no.

---

### Post by alphaniner on 2009-11-17
> **cartisdm said:**
> Anyone have any clue what this change might entail? I am pretty sure that if I am able to disable the ACPI function in the bios I will be able to turn off my computer completely

Disabling would be a workaround, not a fix.  When I mentioned ACPI, it was to make sure things were enabled not disabled.  Did you do any Googling?  [This post]("http://windows7forums.com/windows-7-support/5028-windows-7-wont-shut-down-help.html") on the Win7 forum looks promising.

Alternately, just Google "[Windows 7 won't shutdown]("http://www.google.com/webhp?hl=en#hl=en&source=hp&q=windows+7+won%27t+shut+down&aq=2&aqi=g10&oq=windows+7+won&fp=1c443ffcb5a5cce1")"

---

### Post by cariboo on 2009-11-17
I'm sitting in front of a computer that was running XP Pro last week, It's about 5-6 years old, and it would shut down completely with out putting a check mark in the setting. See the screenshot.

---

### Post by doas777 on 2009-11-17
> **cariboo907 said:**
> I'm sitting in front of a computer that was running XP Pro last week, It's about 5-6 years old, and it would shut down completely with out putting a check mark in the setting. See the screenshot.

the efficacy of any given power management system varies widely from mobo to mobo.

---

### Post by cartisdm on 2009-11-17
> **alphaniner said:**
> Disabling would be a workaround, not a fix.  When I mentioned ACPI, it was to make sure things were enabled not disabled.  Did you do any Googling?  [This post]("http://windows7forums.com/windows-7-support/5028-windows-7-wont-shut-down-help.html") on the Win7 forum looks promising.

Alternately, just Google "[Windows 7 won't shutdown]("http://www.google.com/webhp?hl=en#hl=en&source=hp&q=windows+7+won%27t+shut+down&aq=2&aqi=g10&oq=windows+7+won&fp=1c443ffcb5a5cce1")"

All that info seemed so solid I wanted it to work so bad but unfortunately I am still unable to power down. Sucks.

All those people had problems with ASUS mobos and I'm running a MSI k9n2 diamond.  I just checked and it has the latest BIOS as well so I don't think flashing the BIOS would do anything either...

This is driving me crazy

---

### Post by FootySr on 2009-11-17
Did you connect the case fans to the motherboard? Try connecting the case fans directly to the PSU, you might have to tell the bios not to monitor the case fans. Not that this will be of any help but I've always just attached mine directly to the PSU and since you seemed to have exhausted all other options. As long as you know you have enough case cooling and check your case once a month or so to make sure your fans are working there's no need to have the attached to the motherboard just to be monitored.

---

### Post by alphaniner on 2009-11-17
> **FootySr said:**
> Did you connect the case fans to the motherboard? Try connecting the case fans directly to the PSU, you might have to tell the bios not to monitor the case fans. Not that this will be of any help but I've always just attached mine directly to the PSU and since you seemed to have exhausted all other options. As long as you know you have enough case cooling and check your case once a month or so to make sure your fans are working there's no need to have the attached to the motherboard just to be monitored.
[COLOR="White"].[/COLOR]
[QUOTE=Joe Dirt]Whaaaaaaaaat?[/QUOTE]

---

### Post by cartisdm on 2009-11-17
> **alphaniner said:**
> originally posted by joe dirt 
whaaaaaaaaat?

+1

---

### Post by MasterNetra on 2009-11-17
Curious just how far did you get into shutting down windows? I know Windows 7 takes painfully long to shutdown.

---

### Post by cartisdm on 2009-11-17
> **MasterNetra said:**
> Curious just how far did you get into shutting down windows? I know Windows 7 takes painfully long to shutdown.

The OS completely shuts down and the power to the screen gets cut.  The only thing left running is the CPU fan, GPU fan, case fan, and a few lights on the motherboard.  If I cut the power on the PSU then turn it back on and start up the machine everything boots up fine (as opposed to saying Windows Didn't Shutdown Properly)

I have this system 99.9% working except for this one stupid problem...grr....

---

### Post by Machnikowski on 2009-11-17
A Vista box I had at one point did this. The only way to turn it off completely after shutting down Windows was to flip the switch on the PSU off, then on again. The same box with Windows XP installed never had the issue. Weird.

---

### Post by cartisdm on 2009-11-17
> **Machnikowski said:**
> A Vista box I had at one point did this. The only way to turn it off completely after shutting down Windows was to flip the switch on the PSU off, then on again. The same box with Windows XP installed never had the issue. Weird.

That's how this is.  With Ubuntu I can shut it down just fine, but with Vista and 7 I am in this boat

---

### Post by alphaniner on 2009-11-17
I'm no hardware guru, but it seems that if Ubuntu shuts down properly, it must be some sort of communication failure between the OS and one of the components.  So remove every one of them you can (and disable unnecessary onboard devices like network and sound, as applicable) and see if the problem persists.  If it doesn't, add stuff one by one until it returns.  If it does, then the problem is with one of the components you couldn't remove.  Either way, you will have gathered important information even if you don't find a solution.

---

### Post by FootySr on 2009-11-18
Hey Joe Dirt!

Be nice I'm just trying to be helpful. ;)

I had issues recently with my processor fan cycling down to a stop, then spinning back up to a high rate. Turning off the CPU Smart FAN Control in my bios fixed it. 

I've built many XP boxes in recently years and have never had such an issue. I would suspect something with the motherboard, maybe and RMA is in order. Hook those case fans up to the PSU instead of the motherboard I bet they go off like they're supposed to. :)

---

### Post by cartisdm on 2009-11-18
Well, last resort is I have another motherboard on hand that I am going to try this afternoon.  It's not quite up to the same specs as the current one but I ran it by my boss and he said he doesn't want to have to deal with the shutdown issue at all so hopefully this new mobo will fix it.

Thanks again for everybody's help (especially w/ it being a Windows issue).  I will keep you updated after the motherboard swap.

---

### Post by cartisdm on 2009-11-19
Well after swapping out the motherboard I was able to solve the problem, weird that it worked out that way.  Thanks for everyone's help!

---

