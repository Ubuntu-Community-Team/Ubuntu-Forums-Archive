---
title: "My Laptop hates every other distro.... How do I tame my computer?"
date: 2006-02-20
forum: The Cafe
---

### Post by byen on 2006-02-20
Hey fellas,
First of all... I feel awkward posting this issue here but I have tried asking a similar question in various forums and I just cant seem to work this out. Here is my question...
Ive used Fedora for a while and after finding Ubuntu... my search for an awesome distro came to an end. Ive been a happy Ubunut for over 9 months now and Ubuntu seemed to have scratched every single itch that came up along the way.
Now, after reading great reviews about other distributions such as Suse,PCLinuxOS, Mandriva,DSL  etc and trying it out on my roomie's desktop I decided to install one of these distros on my other drive to have it run along with Ubuntu and XP. But for some reason... no other distro except Ubuntu and fedora seem to be able to run on my laptop without crashing. And by crashing I mean one of the following:
- CD boots but shuts off randomly during initial boot (even before reaching the setup)
- CD setup starts but shuts off at any random point
- If I do manage to install... the random-shutoff issue still persists either while booting the installed OS or after the entire OS has booted.

I have tried LiveCds as well as Install Cds but the problem persists. I have no idea what is going on and would like to see what you guys have to say on this issue.

I thank you for your support and time.

~byen

---

### Post by byen on 2006-02-20
To add to the above:
-I have tried acpi off feature
-I have also tried disabling legacy USB support
-I have noticed one thing though.. even though the computer doesnt get HOT.. after crashing I see a message similar to 
Warning: System Critical temperature reached during last boot

But I know for sure that the critical temperature has not been reached. Infact.. the livecd/install process seems to boot only if I manage to keep the temp below 40C (crazy..I know)

Well..thats it from me. Here are my system specs:
Compaq Presario 2100 Laptop
AMD athlon XP 2800+
704mb Ram
AtI Radeon 320M graphics card
Broadcom HP  54G Wireless card

---

### Post by dickohead on 2006-02-21
so when you put in the installation cd you typed this:
```
linux acpi=off noapic nolapic
```
and added this to your kernel when booting:
```
acpi=off noapic nolapic
```

Might also be worth a try to check your BIOS settings and make sure that the temperature isn't set to something stupid like 40 degrees, make it around 70.

---

### Post by byen on 2006-02-21
dickohead.thank you for the reply.
The first thing that came to my mind when this started happening was using the>  linux acpi=off noapic nolapic but this does not seem to help. I have also searched my bios to see if I could change any temperature settings but have not found anything as yet.
Now adding "acpi=off noapic nolapic" to the kernel is something I have to look further into. But the problem is that once the cd starts booting... it just shuts off at any random point. I only had success a couple of times where I finished the installation by placing the laptop near the AC blower (thus keeping it under 40C). I think I have to do that again and then look into tweaking my kernel.
thank you for the suggestion. Will try searching more on setting these kernel options and will report back later.

---

### Post by BoyOfDestiny on 2006-02-21
[QUOTE=byen]dickohead.thank you for the reply.
The first thing that came to my mind when this started happening was using the but this does not seem to help. I have also searched my bios to see if I could change any temperature settings but have not found anything as yet.
Now adding "acpi=off noapic nolapic" to the kernel is something I have to look further into. But the problem is that once the cd starts booting... it just shuts off at any random point. I only had success a couple of times where I finished the installation by placing the laptop near the AC blower (thus keeping it under 40C). I think I have to do that again and then look into tweaking my kernel.
thank you for the suggestion. Will try searching more on setting these kernel options and will report back later.[/QUOTE]

I would suggest trying to update the BIOS of your laptop. That has solved every 'mysterious' problem I've had. :)

If your laptop like mine (doesn't come with a floppy), it is pretty easy to mount a dos bootdisk image, and burn an iso and do the update. I've done it sucessfully 3 out of 3 times for my dell inspiron 6000. :)

Good luck to you!

---

