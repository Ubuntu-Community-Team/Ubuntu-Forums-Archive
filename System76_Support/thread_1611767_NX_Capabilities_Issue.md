---
title: "NX Capabilities Issue"
date: 2010-11-02
forum: System76 Support
---

### Post by dave7802 on 2010-11-02
Hi All

Long time user, First Time Poster.

I know my way around Linux, but am far from advanced.

I have used Ubuntu on my VMware machine for a long time,
I upgraded to 10.10 about a month or 2 ago, And everything has been working fine.

Today i booted up my machine to find i can no longer run it.. 
I keep getting the following error:

"Your CPU appears to be lacking expected security protections. Please check you BIOS Settings, Or for more information, run:
/usr/bin/check-bios-nx --verbose

So i run that command:
and this is what i get:

"This CPU is Family 6, Model 23, and has NX Capabilities but is unable to use these protective features because the BIOS is configures to disable the capability.
Please enable this in your BIOS
For more details see:
https://wiki.ubuntu.com/Security/CPUFeatures"

Whats happened to my version of Linux lol 

I attempted everything i know, i even backed up my Vmware, Uninstalled reinstalled and installed a Freshly downloaded copy of 10.10

I restarted my machine (Windows XP) and booted into BIOS
No where do i see in my BIOS Anything to do with NX Capabilities. (Also i done the same on the Vmware BIOS still there is no option for NX Capabilities

It worked fine yesterday, at 6 oclock i shut down VMWare (Even left my machine on overnight)
Loaded it up this morning and i got this error.

No windows Updates. No Changes to the BIOS i have no idea.......

How is it possible for it to be working for so long with no issues and now this.
I have googled and looked at every other issue related to it on here, and its all the same, enable the feature in BIOS

I dont have it...... So what i can no longer run it on my Machine.. why now after its been running fine for so long...

Is there any way to overcome this issue... any command or alteration i can do to get my back into my OS

Any help or advise you can can offer i much appreciate

---

### Post by isantop on 2010-11-02
What model is your computer? It will probably be something like PanP7 or DarU3.

---

### Post by endotherm on 2010-11-02
in your bios, NoeXecute (NX) may be refered to as Data Execution Prevention (DEP). just a thought.

---

### Post by dave7802 on 2010-11-03
Thanks very much
It was DEP 

I Clearly missed it. 
Thanks, I enabled this option loaded into XP and started VMWare. 

As Ubuntu starts it now asks me to login in Terminal (It has not loaded the Desktop Environment yet)

"Figured it out, I attempted every command i know to start the desktop Enviroment, and i could not get it right)

Like Xstart, Full commands to load KDE etc

Anyway after 10 minutes of Guessing it was startx  lol  not xstart 

Anyway all booted up and working again, 
Strange the way it just stopped without anything happening..

Thanks again for your help guys

---

### Post by Ramy89 on 2010-12-17
Hi,I have the same problem,I just installed a new driver,and I got the same error.
Anyway how did you fix it?

---

### Post by narcisgarcia on 2010-12-26
I see the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

