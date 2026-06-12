---
title: "best way to wipe a drive"
date: 2013-03-12
forum: Security
---

### Post by roten on 2013-03-12
Hi!

I would like get advice how wipe my old drive completely. I have read about hdparm, DBAN, HDDErase, wipe, dd, shred, bleach-bit, sfill,... I'm sure there are many more to be found.

Which method is up to date and will work with most pc computers now?

What about speed versus security (quality of wiping)?

And how should it be used? Please show with command lines (if a CLI method)!

TIA

---

### Post by Cheesemill on 2013-03-12
I would use hdparm, as it will wipe parts of the drive which other methods simply can't reach.

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by tubbygweilo on 2013-03-12
"Danger, Will Robinson!"

---

### Post by sudodus on 2013-03-12
> **Cheesemill said:**
> I would use hdparm, as it will wipe parts of the drive which other methods simply can't reach.

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

Thanks,

The link has a lot of details :-)

---

### Post by Soul-Sing on 2013-03-12
use a ubuntu live-cd
:```
 shred -n 5 -vz /dev/sda
```

or use [COLOR="#FF0000"]dban[/COLOR], the new released one.

hdparm is rocket science imho.

---

### Post by pinballwizard on 2013-03-12
Bugger DBAN, I'd use a frikkin large magnet.

---

### Post by roten on 2013-03-12
> **Cheesemill said:**
> I would use hdparm, as it will wipe parts of the drive which other methods simply can't reach.

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

Thanks 

This looks a little complicated, but there are several small steps and good explanations. So I'll try it. My drive seems to have the necessary properties, and I have an eSATA adapter, that can be switched on after boot, so that the BIOS won't freeze the drive.

I'll be back and report my results...

---

### Post by roten on 2013-03-12
> **Soul-Sing said:**
> use a ubuntu live-cd
:```
 shred -n 5 -vz /dev/sda
```

or use [COLOR=#FF0000]dban[/COLOR], the new released one.

hdparm is rocket science imho. Thanks for the tips,

The current version of DBAN booted but exited with errors for me. I tried in two computers with the drive to be wiped in an eSATA box. If hdparm turns out to be too hard I might try shred. But is it worth the wear and time to run 5 random writes?

---

### Post by Cheesemill on 2013-03-12
> **roten said:**
> Thanks 

This looks a little complicated, but there are several small steps and good explanations. So I'll try it. My drive seems to have the necessary properties, and I have an eSATA adapter, that can be switched on after boot, so that the BIOS won't freeze the drive.

I'll be back and report my results...

I've done it a few times and it's easy enough to follow the instructions, there's only a few commands you have to execute.

Just make sure you get the right drive before you start :)

---

### Post by roten on 2013-03-12
Thanks for the warning tubbygweilo. And the manual **man hdparm **is pretty scary.

Thanks for the tip pinballwizard. You are right about DBAN, but I don't want to brick the drive with a strong magnet, I'll try hdparm first.

---

### Post by duke.tim on 2013-03-12
hmm i'll add another vote for DBAN. Burn a cd, boot click enter* YAY!

(well almost)

---

### Post by roten on 2013-03-13
I think it worked, but would like some feedback, particularly about the minor pagefaults. See my edited dump from the terminal window :-)

As you can see, I also checked the result but that lasted more than 10 times longer than the wipe, so I don't think I will run that check again, at least not let it finish.

*Edit*: The drive was a Toshiba laptop 250 GB 5400 rpm sata HDD

```
&#65279;[COLOR=#008000]roten@my-precise:~$ sudo hdparm -I /dev/sdb[/COLOR]
...
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
    88min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50000391f340058c
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 1f340058c
Checksum: correct
[COLOR=#008000]roten@my-precise:~$ sudo hdparm --user-master u --security-set-pass Eins /dev/sdb security_password="Eins"[/COLOR]

/dev/sdb:
 Issuing SECURITY_SET_PASS command, password="Eins", user=user, mode=high
[COLOR=#008000]roten@my-precise:~$ sudo hdparm -I /dev/sdb[/COLOR]
...
Security: 
    Master password revision code = 65534
        supported
        enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
    Security level high
    88min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50000391f340058c
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 1f340058c
Checksum: correct
[COLOR=#008000]roten@my-precise:~$ sudo time hdparm --user-master u --security-erase Eins /dev/sdb security_password="Eins"[/COLOR]

/dev/sdb:
 Issuing SECURITY_ERASE command, password="Eins", user=user
0.00user 0.00system [COLOR=#800080]1:11:03elapsed 0%CPU[/COLOR] (0avgtext+0avgdata 2432maxresident)k
0inputs+0outputs (0major+200minor)pagefaults 0swaps
...
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
    88min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50000391f340058c
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 1f340058c
Checksum: correct
[COLOR=#008000]roten@my-precise:~$ sudo time xxd -a /dev/sdb[/COLOR]
[sudo] password for roten: 
0000000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
1000000000000 0000 0000 0000 0000 0000 0000 0000  ................
2000000000000 0000 0000 0000 0000 0000 0000 0000  ................
3000000000000 0000 0000 0000 0000 0000 0000 0000  ................
54272.57user 343.93system [COLOR=#800080]15:10:36elapsed 99%CPU[/COLOR] (0avgtext+0avgdata 2096maxresident)k
488398400inputs+0outputs (0major+179minor)pagefaults 0swaps
[COLOR=#008000]roten@my-precise:~$[/COLOR] 
```

---

### Post by a2j on 2013-03-26
DBAN, if I can't or don't want to take the drive out. Shred, if I have a drive out and in my sata docking station. Both work great.

---

### Post by ChristianWiles on 2013-03-26
Try using 'Dban' link: [http://dban.org/](http://dban.org/) . It is probably the best thing for Hard Drive Wiping I have ever used. I also recommend after using Dban to destroy the Hard Drive. (Just for security) ;)

---

### Post by Stonecold1995 on 2013-03-29
I second hdparm, however if you are paranoid, or don't trust the closed source hard drive firmware to actually do its job well enough, you could use DBAN, as others have said.  You won't need the full Gutmann 35-pass wipe, usually the 7-pass or 3-pass should be sufficient.

EDIT: Didn't see this thread was solved.  Sorry.

---

