---
title: "So... encrypting my drives was pointless?"
date: 2010-04-14
forum: Security
---

### Post by Sin@Sin-Sacrifice on 2010-04-14
[Passware Recovery Kit Forensics]("http://www.lostpassword.com/kit-forensic.htm") claims to decrypt truecrypt and bitlocker encryptions in minutes. I downloaded the trial but I assume it won't be as functional as the full version. About to reboot into winblows in a min and try it out. Anyone have any thoughts?

---

### Post by Bachstelze on 2010-04-14
> **Sin@Sin-Sacrifice said:**
> [Passware Recovery Kit Forensics]("http://www.lostpassword.com/kit-forensic.htm") claims to decrypt truecrypt and bitlocker encryptions in minutes. I downloaded the trial but I assume it won't be as functional as the full version. About to reboot into winblows in a min and try it out. Anyone have any thoughts?

Read more carefully. All it does is get the key from memory, you could just as well do it yourself with a hex editor and a memory dump.

---

### Post by 2hot6ft2 on 2010-04-14
The trial will only work on a truecrypt file 64MB or smaller.
Guess you're only safe from those that don't have the $800 for the program.

---

### Post by Sin@Sin-Sacrifice on 2010-04-14
> **Bachstelze said:**
> Read more carefully. All it does is get the key from memory, you could just as well do it yourself with a hex editor and a memory dump.

So then unless I'm logged in and the drive is mounted I'm safe? I have to be honest... I just use encryption... I don't really understand it.

---

### Post by Bachstelze on 2010-04-14
> **Sin@Sin-Sacrifice said:**
> So then unless I'm logged in and the drive is mounted I'm safe? I have to be honest... I just use encryption... I don't really understand it.

Quite the opposite. ;) When you mount a TrueCrypt drive, TrueCrypt does not decrypt all the data at once, it just loads the decryption key into memory and then decrypts data on-the-fly when you want to access it. This is what this program attacks: you give it a memory dump and it looks for the key in it. This means that as long as the key is present in memory, it can potentially be read from it. As you probably know, data in memory disappears when the computers is powered off (not instantly, though!), so if your computer has been posered off for, say, 10 minutes, there's nothing this program can do, and that's when you're safe. This is why leaving a computer unattended while powered on is a bad idea if you have sensitive data, even with those "screensaver lock" things.

---

### Post by Sin@Sin-Sacrifice on 2010-04-14
Right on... thanks for the info. I don't really have anything that important to protect. It's just that if someone is an *** and wants to steal my stuff then I don't want them to have the satisfaction. Thanks again.

---

### Post by fargle on 2010-04-14
This is more of an issue on Windows than on Linux - I have demonstrated using a Linux laptop to hook up to a Windows XP laptop via Firewire and dumping the entire memory image even though the screen was locked.  The tool I used can also make it so that any password is accepted when you go to unlock the screen.

On Linux, it's my understanding that if you blacklist the OHCI (I think!) Firewire module, this won't work.  On Windows, you can't stop it.

Still, good advice - never leave a machine with highly sensitive data on it unattended while powered up.

---

### Post by OpSecShellshock on 2010-04-14
You could also pull your 1394 card or, if it's not a card, physically break it (warning: may void the warranty?) at the connection. Who uses those in this day and age anyway?

---

### Post by HermanAB on 2010-04-15
Howdy,

The purpose of Bitlocker and Truecrypt is to protect data *at rest*.  In other words: Your data is protected when the machine is switched off only.

When the system is in use, the data is not protected.

---

### Post by uRock on 2010-04-15
There is a reason gov agencies and banks do not use Windows on machines that need a security rating. Go ITSEC E3 or higher.

---

### Post by PocketDog on 2010-04-17
[QUOTE=uRock]There is a reason gov agencies and banks do not use Windows on machines that need a security rating[/QUOTE]
The cashpoint nearest my house runs XP. I saw a McAfee update error warning looking at me when I went to use it the other day

---

### Post by uRock on 2010-04-17
> **PocketDog said:**
> The cashpoint nearest my house runs XP. I saw a McAfee update error warning looking at me when I went to use it the other day

Your money is in good hands with that bank.

---

