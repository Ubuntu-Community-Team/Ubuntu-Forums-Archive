---
title: "BIOS rootkit, targeted attack"
date: 2012-07-12
forum: Security
---

### Post by Vidar30 on 2012-07-12
Sony VAIO E series (SVE14A1S1EB) - American Megatrends R0260V4

The laptop was new with Win7 preinstalled. Shortly after the purchase, the system was compromised (I assume through web/javascript) and someone managed to modify my BIOS and install a persistent rootkit which survives a HD-wipe.

How do I know? 

Because the perp is communicating to me and has revealed it. Beside from some initial pranks, the hacker doesn't seem to have ill intentions but my system is compromised and it's inhibiting my usage. I've done a fresh install of both Windows and Ubuntu several times, without desired result - system is still compromised. I don't know the exact software used in the attack except that the perp has hinted that Python was used, MEBROMI perhaps? I don't know. 

Question - reliable detection

According to my understanding these kind of attack isn't generic, but need some customizing in accordance to the target specs. It's understandable that antivirus software currently can't remove this kind of malware, but why can't it be detected? It's a piece of code residing in BIOS, should have a signature, yes? 

Question 2 - removal

Flash BIOS, immediately boot a Live CD and do a clean install. Can it fail? Will it work? 

Is it realistic to expect such kits to also reside in some firmware? 
Should I expect a BIOS rootkit to be able to copy itself to RAM during the flash process and insert itself immediately afterwards, or is this fiction for now?

Links/information about BIOS rootkits would be very welcome, thank you.

---

### Post by Hungry Man on 2012-07-12
It's unlikely that they attacked your BIOS. If it's surviving a reformat it's likely just infected your boot manager, which isn't always removed in a Windows reinstall.

If it is a BIOS infection you can go to Sony's website and use the esupport website to the driver/ downloads. Flash the latest BIOS and it should fix that part of the infection. Booting into a LiveCD is a good idea as well.

As for copying itself to RAM and installing itself after I find that unlikely. Not impossible just... unlikely. 

There isn't much information to give. There's only been two BIOS infections in the wild that I know of (widespread that is, direct attacks would have higher numbers) and the best defense is one of those MoBo's with two BIOS.

---

### Post by Soul-Sing on 2012-07-12
Ubuntu comes with [COLOR="Red"]rkhunter[/COLOR]: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)
And [COLOR="Red"]chkrootkit[/COLOR]. You could "run" these rootkithunter progs via Ubuntu.
Please post the outcome of these two progs. These are not "reliable" tools though. There known for their false positives.

A bios flash is very tricky. I would not recommend using it. You could be left with a dead computer. (No cure....)

---

### Post by Hungry Man on 2012-07-12
Flashing the BIOS is basically a 100% automated process nowadays. You use the tool provided by the manufacturer to do it.

---

### Post by |{urse on 2012-07-12
Bios flash from manufacturer's site, this is necessary as no linux-based rootkit tool is going to help you with that.

---

### Post by Vidar30 on 2012-07-12
> **Hungry Man said:**
> It's unlikely that they attacked your BIOS. If it's surviving a reformat it's likely just infected your boot manager, which isn't always removed in a Windows reinstall.

Positive it has a BIOS component. Installed Ubuntu using whole HD, also - system is compromised when booting from USB. It's a targeted intrusion for which complete reinstall using a clean LiveCD is no fix.  

> **Hungry Man said:**
>  There isn't much information to give. There's only been two BIOS infections in the wild that I know of (widespread that is, direct attacks would have higher numbers) and the best defense is one of those MoBo's with two BIOS.

Two BIOS infections in the wild? First Mebromi, secondly?

I'll post the output from rkhunter and chkrootkit shortly. If my understanding is correct the BIOS modification is mainly about providing persistence in case of HD-wipe and an intruder still to install a conventional rootkit for exercising control on the infected system.

Since BIOS is accessible for software to read, what is the reason for anti-virus software not being able to detect this type of malware? The malware should have a signature, right?

---

### Post by Hungry Man on 2012-07-12
> Two BIOS infections in the wild? First Mebromi, secondly?

Can't remember their names. The other was in China or something.

No idea about detection for the BIOS.

---

### Post by wirelessmonkey on 2012-07-13
You seem very certain of a hack, which is fine, but you don't provide much in the way of detail.

How does this 'hacker' communicate with you?
How does this 'hack' become apparent, i.e. messaging, popups, alteration of an application, outgoing traffic, incoming traffic, etc...

Are symptoms only visible when on a network? When you are physically disconnected from the network, does it persist?

What BIOS version do you use? Is it up to date? What manufacturer?

Do you run additional software on your installs, or just default?
i.e. vnc, rdp, sshd, etc...

---

