---
title: "Encrypt a raid 10 array"
date: 2015-05-24
forum: Server Platforms
---

### Post by Jaman42 on 2015-05-24
Hi,
On my machine I have a separate OS disk with full disk encryption and I am atm building a raid 10 array of my storage disks with webmin. After the resyncing has finished, how do I go about encrypting the raid array?

I was thinking full disk encryption off course and somehow setup a autounlock feature with a keyfile on the OS disk (since that is full disk encrypted as well)

Is there anything in particular I have to worry about when encrypting a raid array? As I said I don't boot of the array.

Thank you for reading!

*Edit: I'm fairly inexperienced with Ubuntu but I found out that encrypting with the disk manager was a breeze. I also decided not to use any keyfiles on this machine, it should always be on so I will manually mount the encrypted array if I for some reason need to reboot.

---

### Post by DuckHook on 2015-05-27
I don't know how to advise what you want to do, but would note that even if you achieve it, your end result could be extremely brittle. Any breakage in your raid may very well render the whole array unreadable (depending on how you set it up). You might also wish to have one of the mods move your thread to the servers subforum where the specialized expertise resides.

---

### Post by cariboo on 2015-05-27
Not a beginners question, moved to server platforms.

---

### Post by darkod on 2015-05-28
If I'm not mistaken you need to do this before you start putting data on the array because it is formatting during the encryption setup. So make sure you finish that first.

Otherwise there is nothing special about it especially if you don't want it to automount at boot. But be careful if any applications or services are using this array. When booting you might not be there to always enter a password quickly so the services that will start running will not have the array available. Until it is unlocked it does not exist...

Apart from the main password you will create on encryption setup I do suggest you add one key too and use autounlock and automount at boot. But the choice is yours...

---

