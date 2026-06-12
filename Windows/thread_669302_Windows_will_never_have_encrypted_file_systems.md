---
title: "Windows will never have encrypted file systems"
date: 2008-01-16
forum: Windows
---

### Post by PetePete on 2008-01-16
ok, thats just my opinion, but recently i've been doing alot of personal research into this area and I was thinking that the chances of Windows supporting full disk encryption are minimal due to various reasons.. (full disk encryption being 99% encryption, similar to ubuntus method with alt install CD)

the main reason I think this is because  90% of Windows installations are from manufacturers and users just switch computer on and go, if the pcs were setup with encryption as default this would mean that eventually the vast majority of PCs would have disk encryption.... this is a good thing I hear you cry..... well yes, and no.. its good for people like you and me, but would be an absolute pain in the **** for governments and law enforcement agencies when it comes to forensic checks on the HDDs for gathering evidence. Because of this I believe MS would have some kinda agreement with governments and such not to implement this feature. 

anyway if you live in the UK the above doesn't make much difference, the government can force you to reveal an encryption key, failure to do so results in 2 years accommodation curtsy of her magistracy!

views and opinions?

ps... if anyone knows how to change the password on an encrypted volume, would you mind sharing?!

---

### Post by mozetti on 2008-01-16
Windows may not have it out of the box, but I'm currently working on a laptop with full disk encryption. IMO, Ubuntu doesn't offer it out of the box, either, since the way you obtain it is using the alternate CD -- you have to actively attempt to do it, just like you do with Windows.

---

### Post by ice60 on 2008-01-16
turecrypt will do it with the next release :lolflag:

---

### Post by 50words on 2008-01-16
Windows Vista has [Bitlocker](http://www.microsoft.com/windows/products/windowsvista/features/details/bitlocker.mspx), which is full-disk encryption. That is not good enough for you?

---

### Post by kevdog on 2008-01-16
I havent ugraded to Gutsy yet, probably never will, just wait for Hardy, but you are telling me the only way to do LUKS encryption for Gutsy is from the alternate CD and not the LiveCD??  ***Sarcastic***Who's bright idea was that?? Anyone know of any plans to include this with Hardy's LiveCD release??  I think its a great feature.

As far as TrueCrypt -- I dont really understand the difference between TrueCrypt and LUKS although on the truecrypt website they stated they were going to be introducing LUKS into the next release.

---

### Post by ~LoKe on 2008-01-16
Windows already has the ability to have an encrypted filesystem...just not by default.

---

### Post by PetePete on 2008-01-16
> **50words said:**
> Windows Vista has [Bitlocker](http://www.microsoft.com/windows/products/windowsvista/features/details/bitlocker.mspx), which is full-disk encryption. That is not good enough for you?

ah so it does...
well, its only really available for corporations, and as result avoids the forensic evidence problem i stated above..

---

### Post by popch on 2008-01-16
> **PetePete said:**
> ah so it does...
well, its only really available for corporations, and as result avoids the forensic evidence problem i stated above..

Directly taken from [Microsoft]("http://www.microsoft.com/windows/products/windowsvista/features/details/bitlocker.mspx")'s page:

> Windows BitLocker is for both business and personal users who need to help protect sensitive data on their PC.

---

### Post by PetePete on 2008-01-16
> **popch said:**
> Directly taken from [Microsoft]("http://www.microsoft.com/windows/products/windowsvista/features/details/bitlocker.mspx")'s page:

yeah but they are not directly aiming it at the personal market, its only available to top product lines, not vista home..

im saying that they wouldn't aim it at home users as it would potentially cause far too much upset within law enforcement agencies.... 
the way things are currently is when a person commits a crime their computer is taken away for inspection and evidence gathering, now imagine if every computer had encrypted file systems. it would be infeasible to brute force all these pcs... .

---

### Post by ~LoKe on 2008-01-16
> **PetePete said:**
> yeah but they are not directly aiming it at the personal market, its only available to top product lines, not vista home..

im saying that they wouldn't aim it at home users as it would potentially cause far too much upset within law enforcement agencies.... 
the way things are currently is when a person commits a crime their computer is taken away for inspection and evidence gathering, now imagine if every computer had encrypted file systems. it would be infeasible to brute force all these pcs... .

It's not illegal to encrypt your filesystem, like it's not illegal to lock your possessions in a safe.

---

### Post by edm1 on 2008-01-16
> **kevdog said:**
> Anyone know of any plans to include this with Hardy's LiveCD release??

Yes, i believe in Hardy it will be included on the live CD.

---

### Post by PetePete on 2008-01-16
> **~LoKe said:**
> It's not illegal to encrypt your filesystem, like it's not illegal to lock your possessions in a safe.

how does that relate to my post? im confused.

what I was saying was that it is not in the governments interest to have every PC with an encrypted file system. Evidence by PCs is used as a primary source of evidence these days and its relatively easy to extract for average users.... windows becoming encrpyted file system means that this wont be the case.

---

### Post by ~LoKe on 2008-01-16
> **PetePete said:**
> how does that relate to my post? im confused.

what I was saying was that it is not in the governments interest to have every PC with an encrypted file system. Evidence by PCs is used as a primary source of evidence these days and its relatively easy to extract for average users.... windows becoming encrpyted file system means that this wont be the case.

Why would Windows sacrifice filesystem encryption just because the government doesn't like it?  They're not bound by law.

Plus, they've probably created some kind of "bug" that would allow them to circumvent any kind of encryption.

---

### Post by 50words on 2008-01-17
I think the OP is implying the the government will stifle any attempts to implement large-scale encryption.

While that may be so, both Windows and OSX offer encryption (on OSX, just the /home partition) with the OS, and encryption is pretty easy to access in Linux.

If the government wanted to get in the way, I think they would have done it before now.

---

### Post by Linder on 2008-02-28
Since I work as a computer forensic I can say that encryption does not prevent us from extracting evidence. It does however prolong the process.

---

### Post by Pekkalainen on 2008-02-28
In Germany they forced Skype to implement a backdoor in their encryption system for the government to use. This will not be a one time occurance I'm affraid, it's best if we start writing our own encryption systems.

---

### Post by OffHand on 2008-02-28
> **Linder said:**
> Since I work as a computer forensic I can say that encryption does not prevent us from extracting evidence. It does however prolong the process.

not with the right encryption. if you use strong encryption you are not able to break it.

[http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

---

### Post by ice60 on 2008-02-28
> **Linder said:**
> Since I work as a computer forensic I can say that encryption does not prevent us from extracting evidence. It does however prolong the process.
??

---

### Post by hyper_ch on 2008-02-28
> **PetePete said:**
> anyway if you live in the UK the above doesn't make much difference, the government can force you to reveal an encryption key, failure to do so results in 2 years accommodation curtsy of her magistracy!
I still think that is a violation of international accepted law - at least that's the opinion of the ECHR to which the UK is also bound...

> **mozetti said:**
> IMO, Ubuntu doesn't offer it out of the box, either, since the way you obtain it is using the alternate CD
It offers it out of the box. The DesktopCD is not recommended for installation so you should use the alternate cd ;)

And with regard to Windows. It is commonly known that the NSA als has some parts of development done for XP and VISTA and nobody truly knows what they've done. If one might think they built in a backdoor, it migth be well possible.

---

### Post by ice60 on 2008-02-28
i just saw this posted on another forum. maybe this is what Linder uses lol
[http://www.msnbc.msn.com/id/23299150/](http://www.msnbc.msn.com/id/23299150/)

---

### Post by hyper_ch on 2008-02-28
But that still requires the attacked computer to be in a transparent state...

---

### Post by popch on 2008-02-28
> **Linder said:**
> Since I work as a computer forensic I can say that encryption does not prevent us from extracting evidence. It does however prolong the process.

What time frame are we talking here? Can you give an order of magnitude?

---

### Post by hyper_ch on 2008-02-28
I guess he can but is probably not allowed to.

---

### Post by awakatanka on 2008-02-28
> **hyper_ch said:**
> I still think that is a violation of international accepted law - at least that's the opinion of the ECHR to which the UK is also bound...


It offers it out of the box. The DesktopCD is not recommended for installation so you should use the alternate cd ;)

And with regard to Windows. It is commonly known that the NSA als has some parts of development done for XP and VISTA and nobody truly knows what they've done. If one might think they built in a backdoor, it migth be well possible.

NSA does it also for Linux. And OP didn't do alot of research because else he had known that MS can encrypted with vista to.

---

### Post by hyper_ch on 2008-02-28
but on linux you can actually look what the NSA code does ;)

---

### Post by K.Mandla on 2008-02-28
Moved to Windows Discussions.

---

### Post by sayakb on 2008-02-28
I really don't understand the merits of encryption. On a bitlocker encrypted drive, I could access through the LiveCD and on the Network Share.. So whats the use of encryption?

---

### Post by hyper_ch on 2008-02-28
well, if the system is not made transparent (upon boot entering the passphrase or loading a keyfile from an unencrypted device) all data is fully encrypted...

so during normal operation you don't notice anything. As soon as it is turned off, everything's encrypted again - until it is made transparent again.

---

### Post by sayakb on 2008-02-28
> **hyper_ch said:**
> well, if the system is not made transparent (upon boot entering the passphrase or loading a keyfile from an unencrypted device) all data is fully encrypted...

so during normal operation you don't notice anything. As soon as it is turned off, everything's encrypted again - until it is made transparent again.

But how did I access it through the LiveCD then?

---

### Post by ice60 on 2008-02-28
> **hyper_ch said:**
> But that still requires the attacked computer to be in a transparent state...
i read it quickly so i'm probably wrong, but i thought they captched the password from a volatile memory.

> But how did I access it through the LiveCD then? you'd need the password and the encryption system used on the livecd, i think.

---

### Post by andrewjoy on 2008-02-28
> **Linder said:**
> Since I work as a computer forensic I can say that encryption does not prevent us from extracting evidence. It does however prolong the process.

I am sure it would with advanced encryption nowadays you best have a few 100 years free.

---

### Post by hyper_ch on 2008-02-29
> **ice60 said:**
> you'd need the password and the encryption system used on the livecd, i think.

dm_crypt/LUKS is built into the kernel meanwhile so with the live cd you can make the harddisk transparent.

```

sudo cryptsetup luksOpen /dev/PARTITION DEVICENAME
sudo mount /dev/mapper/DEVICENAME /path/to/mountpoint

```

e.g. sdb2 is encrypted and you want to mount it as /media/music

```

sudo mkdir /media/music
sudo cryptsetup luksOpen /dev/sdb2 sdb2_music
sudo mount /dev/mapper/sdb2_music /media/music

```

or if you have a keyfile added to the encrypted partition, you could also use that one to make it transparent

```

sudo mkdir /media/music
sudo cryptsetup luksOpen /dev/sdb2 sdb2_music --key-file /path/to/your/keyfile
sudo mount /dev/mapper/sdb2_music /media/music

```

---

### Post by Linder on 2008-03-04
> **andrewjoy said:**
> I am sure it would with advanced encryption nowadays you best have a few 100 years free.

If the encryption key cannot be found, and no password is availible, then yes :P

---

