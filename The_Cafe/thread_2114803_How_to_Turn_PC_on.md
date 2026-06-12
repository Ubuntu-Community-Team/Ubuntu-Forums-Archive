---
title: "How to Turn PC on?"
date: 2013-02-11
forum: The Cafe
---

### Post by Quarkrad on 2013-02-11
Apologies if this is the wrong part of the forum to post this question.  Issue:  Elderly father-in-law (FIL) to have pc across room connected to TV for display. Want him to be able to switch pc on/off without having to get up/leave chair.  I have a thing about leaving the pc on in standby mode for long periods – I would prefer it to be switched off completely.   I am considering a remote control mains socket so he can turn the power on/off to the pc and looking at setting the bios Power Features to PWRON after PWR-Fail.  So I'm thinking …... he presses the remote and powers the mains socket – this should power-up the pc to his Ubuntu Desktop.  If he presses the remote to turn-off the power socket the PC will turn off/crash.  This PC will be used mostly once a day – it doesn't feel a  good solution 'crashing' the pc to turn it off but Ubuntu seems robust in the few occasions I have had to crash my set up.   If he turns 'off' (crashes) only when he has finished with the pc and is  back to his Desktop is this a practical solution?

---

### Post by pqwoerituytrueiwoq on 2013-02-11
you may be able to use wakeonlan from a smart phone that is connected to your wifi
wakeonlan does not work after a power failure
you can use the gui on the computer for shutdown

---

### Post by mJayk on 2013-02-11
All it takes to turn your pc on / off is a short between two motherboard pins.

You can get IR control / receiver sets that are literally switches and cost ~ 10 quid.  Get one of them and wire it up to the pins.  Otherwise the wake on lan stuff from a smartphone sounds good.

---

### Post by Paqman on 2013-02-11
What software is he running on the machine? If it's used for streaming video to the TV then XBMC is really easy to use, and as pqwoerituytrueiwoq mentions it can be controlled by a smartphone (including power on and off).

However, if your FIL doesn't use a smartphone then your power switch option will work well enough. It's not great to pull the plug without shutting down completely, it could cause loss of any data that is being written to disk (or waiting to be written).

Most of the TV power saving switches that talk to the remote don't have a long enough delay to allow the PC to sleep before cutting the power. What about a compromise where he allows the PC to sleep after a short period, then a timer switch cuts the power to everything (TV, PC, etc) overnight. That way you'll have at least eight hours of zero power, and also with zero input required from him.

---

### Post by Quarkrad on 2013-02-11
Thank you for the replies.  FIL has deteriorating eye sight so basic phone is a challenge let alone a smart phone!   He uses pc/ Ubuntu in it's most simplest form really &#8211; checking his email and a bit of surfing to look/check his bank account.  He is currently running 12.04 in classic mode &#8211; I have put a number of icons on his desktop that are basically web links to the pages he checks daily.  I like the idea of the IR control/receiver kits that will plug inti the motherboard and am looking for such devices at the moment.  If I find one I will come back to confirm.  Thanks.

---

### Post by Paqman on 2013-02-11
If he's using it for desktop stuff he's presumably using a keyboard and mouse/trackpad? Is there some reason he can't just shut it down the normal way and then the plug for the TV can switch it off at the wall? 

I use [this plug]("https://www.eonshop.co.uk/ProductDetails.aspx?ProductCode=1100024&Category=PowerSavingAppliances") btw, works really well. Power companies were offering them heavily subsidised (or free) here in the UK recently.

---

### Post by Quarkrad on 2013-02-11
I too live in the UK - FIL is with EDF but they do not seem to be offering the sort of plug you describe.  If I were to use this sort of plug and remotely power it up - I still need to turn the pc on.  Logically I could use the PWRON feature of the bios (I've got to check the pc motherboard can do this) to boot up as it now has power.  If he shuts down the normal way, via the Desktop, will he not be in a loop because when the pc shuts down it is going to sense power and the bios will re boot again?  He will have to shut down the pc in the normal way and towards the end of the power down remotely turn off the power plug.  Or have I got this all wrong?

---

### Post by pqwoerituytrueiwoq on 2013-02-11
does your bios have a boot key?
my desktop has a feature that lets my use the spacebar as a power button, but ot only works for  PS/2 keyboard, but the system i built my neighbor (newer hardware; uefi bios) has that but for USB
[[img]http://www.zimagez.com/miniature/screenshot-02112013-071938am.php[/img]](http://www.zimagez.com/zimage/screenshot-02112013-071938am.php)
[[IMG]http://www.zimagez.com/miniature/screenshot-02112013-071728am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-02112013-071728am.php")

---

### Post by Paqman on 2013-02-11
> **Quarkrad said:**
> I too live in the UK - FIL is with EDF but they do not seem to be offering the sort of plug you describe.

You don't have to be with EON to buy the plug from them. A few other people are selling it too, just Google "PowerDown Plug"

What I suggest:

To switch off:
[LIST=1]
[*]He suspends the PC
[*]He presses off on the TV remote
[*]The PowerDown plug turns off the TV and PC
[/LIST]

To switch on:
[LIST=1]
[*]He presses the on button on the TV remote
[*]The PowerDOwn plug turns on the power to TV and PC
[*]The PC BIOS detects power being restored and boots the PC
[*]He presses the on button on the TV remote to turn the TV on
[/LIST]

Killing the power from a state of suspend isn't risky, because AFAIK all pending writes to disk are done before the drive is spun down during suspend. All the contents of the RAM would be lost, but that's not a biggy IMO.

---

### Post by grahammechanical on 2013-02-11
We can choose Shutdown from the Power/cog menu and that shuts down not only Ubuntu but also the base unit. On my machine at least. I need to press the power button to reboot.

I agree with paqman about the use of that TV powerDown socket. Note this:

> Permanent On Socket - The dedicated socket is designed specifically for any box that requires permanent power such as Sky.

Do not use that one. Look in the BIOS under Power>APM configuration. This is where it exists in my BIOS. The options are

Restore on AC Power Loss

When set to Power Off the system goes into the off state after an AC power loss.
When set to Power On the system goes on after an AC power loss.
When set to Last State the system goes into either off or on state, whatever the system state was before the AC power loss.

Regards.

---

### Post by Paqman on 2013-02-11
> **grahammechanical said:**
> We can choose Shutdown from the Power/cog menu and that shuts down not only Ubuntu but also the base unit. On my machine at least. I need to press the power button to reboot.


That won't actually kill it completely though. Computers when shut down are really just in a standby mode, and generally use only slightly less power than when hey are suspended (typically about 6-10W for a desktop). To cut power use to zero you need to switch them off at the wall or at the PSU.

---

### Post by Quarkrad on 2013-02-11
Great suggestions - thanks.  I can suspend via the Ubuntu menu and there is a bios setting so that the pc goes into sleep mode.  Unfortunately there is not a power up option.  I'm changing over to another 'archived' base unit to see if that has a more modern bios.

---

### Post by Grenage on 2013-02-11
I bought an old TV card from ebay, one with a power cable pass-through, for IR control.  It cost me about £4, and effortlessly tied in to my harmony remote.

Alternatives include products such as [this]("http://www.simerec.com/PCS-1a.html"), which are better.

---

### Post by CharlesA on 2013-02-11
> **Grenage said:**
> I bought an old TV card from ebay, one with a power cable pass-through, for IR control.  It cost me about £4, and effortlessly tied in to my harmony remote.

Alternatives include products such as [this]("http://www.simerec.com/PCS-1a.html"), which are better.

Nice! I never knew about that sort of thing. I might have to include one of those in my next HTPC build.

---

### Post by pqwoerituytrueiwoq on 2013-02-11
you could rig parts from a wireless doorbell into a power button, you just have to connect it to the power button wires in the system
all the power button does it touch 2 wires together when pressed anything able to complete a circuit will work

---

### Post by Quarkrad on 2013-02-12
OK, sorry for the delay - I had some trouble loading 12.04 onto my other pc - turned out to be faulty memory card/bank so managed to get that sorted.  I think I do not understand the pwron command in bios.  I have enabled **PWRON after PWR-Fail** in my bios and was expecting that after shutting down Ubuntu in the normal way, I could turn off the mains (simulating the remote control power switch/plug) and then, switching the mains plug on the pc would power up.  Did this and nothing happened - the pc sat there doing nothing.  However, if I select Suspend, rather than Shut Down in Ubuntu drop down menu the pc seems to shut down completely - no lights on or noise/movement inside.   I switch off the mains and then after a few minutes back on again. Instantly the pc boots to Ubuntu. I guess my problem is sorted.  As an aside - is there a way I can edit/change the drop down menue so that I delete the Shut Down text and replace Suspend with Shut Down?  (I'm running 12.04 with the gnome classic desktop).

---

### Post by CharlesA on 2013-02-12
The setting will only power the machine on if it lost power - aka AC power was cut and a normal shutdown wasn't done.

---

