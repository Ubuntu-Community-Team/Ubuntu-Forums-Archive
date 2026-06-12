---
title: "Help mounting a veracrypt partition"
date: 2021-06-23
forum: Security
---

### Post by birdbirdbird on 2021-06-23
Hi,
I have a veracrypt partition (which I can decrypt, from windows, using veracrypt). I used to use a script on my previous distro  (Opensuse) to decrypt & mount my partition, but it doesn't work on Kubuntu for some reason (despite both using KDE).

This is the code which used to work for decrypting, but here, now, it doesn't work anymore. Whether I use /dev/disk/by-partlabel/Te or /dev/sdb2 makes no difference. I can't get it to open.
```
sudo cryptsetup open --type tcrypt --veracrypt /dev/disk/by-partlabel/Te MyMappedPartition
```

In fact, when it asks for the passphrase, no matter what I enter (correct or wrong), it doesn't even give me an error...
Please help.

---

### Post by TheFu on 2021-06-23
try:
```
sudo cryptsetup open --type tcrypt --veracrypt "/dev/disk/by-partlabel/Te BRARAR"
```

Spaces are bad. Always. Anything with a space _needs to be quoted_.  Also, you should check in the dev/disk/by-partlabel/ directory and see that the label is there.

I don't use veracrypt, but with LUKS, we are required to provide the correct "name" for the LUKS device to be opened. If the wrong name is provided, it will not open.

---

### Post by birdbirdbird on 2021-06-23
> **TheFu said:**
> try:
```
sudo cryptsetup open --type tcrypt --veracrypt "/dev/disk/by-partlabel/Te BRARAR"
```

Spaces are bad. Always. Anything with a space _needs to be quoted_.  Also, you should check in the dev/disk/by-partlabel/ directory and see that the label is there.

I don't use veracrypt, but with LUKS, we are required to provide the correct "name" for the LUKS device to be opened. If the wrong name is provided, it will not open.

The code doesnt work.
the "BRARAR" (which I should just really have called "MyMappedPartition" or something - I'll edit the OP, it'll make things simpler) is because, you can't decrypt the partition without the argument to map it in /dev/mapper. In fact, I just tried and here's the result, which confirms it : 
```
[FONT=monospace][COLOR=#000000]Command requires device and mapped name as arguments.[/COLOR]
[/FONT]
``` 

I did check whether the label is here or not (and yes it is here). I have also tried by directly using the corresponding entry in /dev/ (which would be, /dev/sdb2).

---

### Post by TheFu on 2021-06-23
Ah, my mistake ... so BRARAR was the correct name for the encrypted volume previously. I've not used partlabel for mounting.

In my cryptsetup notes, I have this:
```
 sudo cryptsetup luksOpen /dev/sdf5        c720
 sudo mkdir /mnt/root /mnt/Stuff
 sudo vgchange -ay  # that's for LVM stuff which I suspect isn't being used.
 sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
```
It has been a few years, and luksOpen has been deprecated, but still works. There are number of similar aliases for other encryption methods.

The manpage says this:
```
       open <device> <name> --type <device_type>
```
So if we follow that order, it would be 
```
sudo cryptsetup open  /dev/disk/by-partlabel/Te   BRARAR    --type tcrypt --veracrypt  
```

Have you tried to gather more data using:
```
sudo cryptsetup   tcryptDump    /dev/disk/by-partlabel/Te 
```

The manpage has lots and lots of stuff about using TrueCrypt-compatible encryption, plus it lists the limitations.

---

### Post by birdbirdbird on 2021-06-24
```
sudo cryptsetup open /dev/disk/by-partlabel/Te BRARAR --type tcrypt --veracrypt
```

I tried it, and ... got no more response than before with my own code. Just "enter passphrase", which I did, a little pause, and nothing happened (no success confirmation nor error even if I put the wrong passphrase). I don't see any new device in /dev/mapper, /mnt/ or /media/ (or anywhere for that matter, I did a search).

```
sudo cryptsetup   tcryptDump    /dev/disk/by-partlabel/Te
```

Because it's a veracrypt partition, I don't think this code can work :
```
[FONT=monospace][COLOR=#000000]Enter passphrase for /dev/disk/by-partlabel/Te:  [/COLOR]
No device header detected with this passphrase.[/FONT]
```

this is incorrect because like I said, it works on Windows (and I did not make an error in the passphrase, I copy/paste it from my password manager and I even checked it manually after copy, in case it added an extra space at the end of the phrase or something).

---

