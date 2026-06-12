---
title: "Booting into Ubuntu on a dual-boot Ubuntu/Windows machine with an infected USB stick"
date: 2017-03-04
forum: Security
---

### Post by John_Patrick_Mason on 2017-03-04
Is it safe to plug in an infected USB flash drive on a dual-boot Ubuntu/Windows machine if I only boot into Ubuntu?

---

### Post by T.J. on 2017-03-04
Probably, although I would not recommend it, simply because some of the new forms of USB tampering can overload and damage the PC as soon as you plug in the drive.  If you are certain that it is just a garden variety virus or malware, then it will probably do no harm.  Most are designed for Windows, and will not work in Linux.

---

### Post by John_Patrick_Mason on 2017-03-04
So if I understand you correctly, unless a cracker specifically took into account Linux systems when writing the malicious software, if I plug in the USB flash drive with its firmware tampered with, you're saying I should be fine?

---

### Post by DuckHook on 2017-03-05
> **John_Patrick_Mason said:**
> So if I understand you correctly, unless a cracker specifically took into account Linux systems when writing the malicious software, if I plug in the USB flash drive with its firmware tampered with, you're saying I should be fine?You are drawing the wrong conclusions from T.J.'s comments. Moreover, the question you are asking is actually a very complicated one.

The USB subsystem is a known major vulnerability in modern computers:

[LIST=1]
[*]It has direct access to system memory (not sandboxed). This is what makes connecting USB storage so easy.
[*]So many peripherals use USB that it is easy to exploit it.
[*]
[/LIST]
For example, your mouse and keyboard connect through USB. The simplest of thought experiments can envision a scenario wherein a rogue USB stick emulates a keyboard and executes a series of dead-simple keystrokes that deletes your /home directory. Since it is your /home directory, elevated privileges are unnecessary to access it. Yet, for most people, all of our really important data is in /home anyway. The usual concern about defending against root escalation is academic when all of your photos, music, email and documents are erased.

Despite this theoretical exposure, I routinely plug in USB sticks without a second thought. Why? Because:

[LIST]
[*]I make sure that such sticks are from trusted sources. I will not plug in something that I found off the street or laying on a coffee shop counter.
[*]There is a limit to the amount of suspicion and paranoia that one can sustain without becoming dysfunctional in the real world.
[/LIST]
You appear to desire black and white reassurances in an arena that, by its very nature, exists only in shades of grey. Computer malware is the equivalent of booby traps and land mines in the real world. That's what malware is designed to do. And just like with booby traps, there is no such thing as a slam-dunk when it comes to assessing them or disarming them. There's always that risk that they will detonate in your face. Even if you found someone on these forums silly enough to give you the absolute reassurance that you want, you'd be a fool to believe them.

---

### Post by John_Patrick_Mason on 2017-03-05
I made a mistake in the previous post. I meant to say, "So if I understand you correctly, unless a cracker specifically  took into account Linux systems when writing the malicious software, if I  plug in the USB flash drive **WITHOUT** its firmware tampered with, you're  saying I should be fine?" My question was specifically meant to address USB thumb drives that had their firmware tampered with that would overload a Linux **or **Windows computer. I hope that makes more sense. Sorry for the mistake.

[QUOTE=DuckHook]For example, your mouse and keyboard connect through USB. The simplest  of thought experiments can envision a scenario wherein a rogue USB stick  emulates a keyboard and executes a series of dead-simple keystrokes  that deletes your /home directory.[/QUOTE]

I would like reassurances, but right now, I'm only trying to understand the risks. Some things *are* nearly hack-proof, like putting tape over the integrated webcam on your laptop, disconnecting the USB Wi-Fi adapter on your desktop, turning off your computer at night, or using two-factor authentication with a FIDO security key. I'm not sure what you mean by a USB stick *emulating* a keyboard. Are you saying that if a keyboard with a USB connection gets plugged into an infected Windows computer and then gets plugged into an Ubuntu computer, that keyboard could be sending back every keystroke ever typed on the Ubuntu machine to some remote server?

---

### Post by DuckHook on 2017-03-05
> **John_Patrick_Mason said:**
> …Some things *are* nearly hack-proof, like putting tape over the integrated webcam on your laptop, disconnecting the USB Wi-Fi adapter on your desktop, turning off your computer at night, or using two-factor authentication with a FIDO security key.True enough. But few people do any of these things. If you do, then it makes you a very small minority that takes security seriously.> I'm not sure what you mean by a USB stick *emulating* a keyboard. Are you saying that if a keyboard with a USB connection gets plugged into an infected Windows computer and then gets plugged into an Ubuntu computer, that keyboard could be sending back every keystroke ever typed on the Ubuntu machine to some remote server?Keyboards tend to be simple devices. I'm not aware of any keyboards that have sufficiently complex circuitry to allow tampering with their firmware. There may be hardware devices that can be installed in keyboards to capture strokes, but that seems more in the realm of spy movies than the real world, though I suppose that those who work in highly sensitive professions must worry about even such devices.

I'm talking about actual USB flash sticks. They have sufficiently complex firmware that such firmware can be modified to make the USB stick emulate a keyboard instead of a memory device. This is not just theoretical. At least one brand of micro-controller has been hacked in just such a way. When you plug in such a USB stick, your computer will not see a memory device. It will see instead a HID (a Human Interface Device like a mouse or keyboard). And since HIDs are considered fundamental to computer functionality, they communicate at the most basic level of the OS. Even malware detectors will find it tough to identify—much less intercept—such hacks.

Although the process of changing USB stick firmware in this way is not trivial, it is well within the ability of most crackers. There are tutorials on-line that teach scumbags how to do it. If, instead of deleting your files (as in my example above), the hacked firmware is programmed to install a keylogger, or to encrypt your files as part of a ransomware attack, then the consequences would be profitable to the cracker. With respect to your question (Windows malware migrating to Linux), writing malware that modifies USB sticks without the knowledge or acquiescence of the computer owner is yet another level a difficulty. But I seriously doubt that a sufficiently capable cracker would find that problem much of a hurdle for too long.

It bears noting that such a crack would *not* be disarmed by a simple format of the USB stick. And since it works by way of emulated keystrokes, it is also OS agnostic, though it would presumably have to be sophisticated enough to first detect the nature of the OS.

---

### Post by HermanAB on 2017-03-05
If you only consider actual USB memory sticks that have not been tampered with, beyond the act of loading malware on it, then you have little to fear, since there is almost no Linux malware and even the malware that does exist, usually only run on a specific version of Linux and which therefore likely won't run on your version of Linux.  For all practical purposes, there are no Linux viruses and I have never encountered a Linux virus, despite having used it in thousands of computers since about 1995.

However, it is possible to make a device that looks like a USB memory stick, but which isn't a memory stick and it is very hard to defend against something like that. These type of specialized devices do exist and can be purchased online.  

For example, keyboard emulators are used by sysadmins to configure computers - to load a new BIOS or whatever cannot be done easily the usual way and which gets tiring really quickly if you have to do it on hundreds of machines.  Full size examples are Gamer Keyboards - keyboards with macro abilities - your local computer game shop sells them.  You cannot easily defend against a small keyboard emulator, since it emulates someone typing on a keyboard.

---

### Post by John_Patrick_Mason on 2017-03-05
[QUOTE=T.J.]Probably, although I would not recommend it, simply because some of the  new forms of USB tampering can overload and damage the PC as soon as you  plug in the drive.[/QUOTE]

What do you mean by damage? Damage as in you can't turn on the PC anymore, or damage as in the CPU is being used at a 100% -- with practically no applications open -- which eventually causes it to fail, but can be fixed doing a full reformatting of the partition and doing a clean install of Windows 7? I'd like to know what you mean by overload too. What would PC overload look like?

---

### Post by DuckHook on 2017-03-05
> **John_Patrick_Mason said:**
> What do you mean by damage? Damage as in you can't turn on the PC anymore, or damage as in the CPU is being used at a 100% -- with practically no applications open -- which eventually causes it to fail, but can be fixed doing a full reformatting of the partition and doing a clean install of Windows 7? I'd like to know what you mean by overload too. What would PC overload look like?[https://arstechnica.com/security/2015/10/usb-killer-flash-drive-can-fry-your-computers-innards-in-seconds/](https://arstechnica.com/security/2015/10/usb-killer-flash-drive-can-fry-your-computers-innards-in-seconds/)

To be clear, it's a hardware hack. This cannot be done with software, so you are not at risk from a "virus". However, plugging in "found" USB sticks is not a good idea except on equipment that you don't care about.

---

### Post by John_Patrick_Mason on 2017-03-05
[QUOTE=DuckHook]To be clear, it's a hardware hack. This cannot be done with software, so  you are not at risk from a "virus".[/QUOTE]

Interesting. I think I remember reading the same article a while back in the link you provided. Do we know by now whether such an attack would render the data on the hard drive unrecoverable?

---

### Post by DuckHook on 2017-03-06
The technique is essentially an induced power spike. Various components will have varying resistance to damage. Purely electronic components are most at risk, including USB controller, other MOBO components, RAM, CPU & GPU. It is known that HDDs can be crippled by power spikes because their firmware is electronic. However, the underlying substrate may survive intact and physical recovery may be possible. You would need the facilities of recovery experts though. All bets are off when it comes to SSDs.

---

