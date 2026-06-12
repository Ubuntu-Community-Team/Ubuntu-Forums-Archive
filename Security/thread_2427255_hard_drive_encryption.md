---
title: "hard drive encryption"
date: 2019-09-19
forum: Security
---

### Post by sniper8752 on 2019-09-19
If I encrypt a hard drive, and I am using it, and it is in a decrypted state, and someone were to come by, and unplug it, would the contents remain encrypted, or would everything be unencrypted? Or does it depend on the encryption used?

---

### Post by uRock on 2019-09-19
Taken from the link below.
> Full disk encryption ensures that data is never present on the drive in an unencrypted state, so sudden power loss does not result in any unencrypted data remaining on the drive. When your computer has to access data, it will read the encrypted data, then use the key you provided (also in RAM) so the data that gets stored in RAM is decrypted. This ensures that decrypted data is only ever present in RAM.

Hard disks and solid state drives are non-volatile, meaning the data they store is permanent. After a power loss, the data is still there. RAM on the other hand is volatile. The type used in modern computers, called DRAM, is composed of a transistor connected to a capacitor. A charge in the capacitor signals a binary 1, and no charge signals a binary 0. Every 64ms, the capacitor is refreshed so it does not leak electricity and loose its bit. When a computer loses power, the capacitors are no longer refreshed, and they begin to lose their charge. DDR2 DRAM will lose power in less than a minute, and DDR3/DDR4 DRAM will lose power in a couple seconds. Compare this with magnetic media, which can retain their polarity for half a century or more, or solid state flash media, which can retain their charge for around a decade without power.

You may have heard of cold boot attacks. It's a type of attack that exploits the fact that RAM does not lose its power instantly, but takes a couple seconds to lose power. If RAM is put in an extremely cold medium, this process can be slowed down to several hours. So unless someone freezes your RAM modules within a second of you powering off your computer, there will be no trace of the key or any unencrypted data on your system.
[https://security.stackexchange.com/questions/146279/how-does-full-disk-encryption-protect-against-unexpected-power-loss](https://security.stackexchange.com/questions/146279/how-does-full-disk-encryption-protect-against-unexpected-power-loss)

---

### Post by Skaperen on 2019-09-19
it stays encrypted.  each time a buffer is read it is decrypted.  decrypting the whole drive could take hours.

---

### Post by Skaperen on 2019-09-19
if i wanted to steal your data, when i come by, what i would do is unplug your UPS from the wall but *not* unplug your computer from the UPS.  then i just take your computer while it is running and while you are still logged in with an unlocked screen.

if the screen is locked, i could get in by booting a Live CD or DVD or memory stick.  but that would lose the passphrase you type in each time you boot it up.  so, all i'd get is the OS.  but i have one of those, already.

if you want my data, you will need to guess my 35 character passphrase.  and, yes, i really can remember it.  i really did type it in about half an hour ago.

---

