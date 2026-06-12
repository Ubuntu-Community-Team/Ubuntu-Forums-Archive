---
title: "Is there an encrypted filesystem to meet my needs?"
date: 2006-06-26
forum: Server Platforms
---

### Post by gushy on 2006-06-26
I need to setup a couple of encrypted filesystems on some servers; having looked around at a few sites and on the forums I'm still not sure as to whether I will be able to achieve what I want.

1. I need to be able to have an encrypted filesystem that will be quick and will handle upto a couple of hundred gigs of data without much performance impact.

2. I need to be able to convert a currently active partition to be encrypted - a lot of the guides I've seen all seem to start with creating a new blank encrypted partitions

3. I would like the partition to be secured via two keys - 1 on a usb drive and 1 on a network share.

Can anyone with experience of encrypted filesystems shed light on the feasability of my aims?

Thanks

---

### Post by Randomskk on 2006-06-26
As far as the keys go, that's easy: in any public/private key based system you could just copy the private key onto your USB drive and onto the network share; typically you encrypt it with a passphrase so that all you need is a copy of the key and the passphrase. 

Handling lots of data shouldn't be much of an issue, I believe most of the crypto FSs do this.

I think your best bet with the current data is to encrypt that someplace else, make the new partition then copy it back.

---

### Post by gushy on 2006-06-26
Certainly copying a key off is easy, idially I'd like to have a system that will require two different keys, or maybe two halves of one key

Good to hear that the data / access won't be an issue I was concerned that the impact the extra overhead might cause would be noticable.

I figured I might have to move my data off the servers, create the partitions and then bring it back; trying to avoid that if I can, but all I've read seems to indicate that I won't have a a choice.

---

### Post by gushy on 2006-06-26
Also - and I'm not sure I'm reading this right - is it a case of, the key is read in during mount of the filesystem, and then it's always decrypted?  Or is there a regular / constant check for the key?

My ideal scenario is that if the network cable or usb drive/key is pulled, the filesystem becomes encrypted again.  Clearly in this instance it would need to buffer and finish any writes in progress, but even if that's not possible, it's an acceptable loss.

---

### Post by Randomskk on 2006-06-26
What do you need that level of security for?
I doubt much software exists to do what you need; the easiest way would probably be to write your own small program that will lock the file system if you pull the USB key.

Two halves of one key isn't really practical under PGP (unless you literally divide the keyfile in two and join it via a script), but you could encrypt everything twice, once using each key.
The performance overheads doing that may not be desirable, depending on your need a better solution may exist (perhaps a secure file store that can only be accessed via a serial link?) - it depends what you need the security for.

---

### Post by gushy on 2006-06-27
To be honest having one key on the usb drive and one on the network is overkill, having one on a network share would be sufficient.  I just liked the idea of having a usb key to pull that would encrypt the system. :)

I don't want to rely solely on a key on a usb drive because if someone stole the box they'd take the usb drive with it.

I freelance and this server is in my garage and contains all customer data and my financial data etc. I live in a pretty pikey area of town so I'm a little paranoid. :p  I pgp key on a nas drive that's in my house would be sufficient to stop the data being read once the box is stolen.

My thought's about the drive encrypting again once the pgp key had been removed was really me just thinking about encrypted filesystems to another level - ie, my laptop - when on a customer site, pull the key and take it with me and the drive encrypts. I mentioned it here in the same context as my server as I figured if I could do it for one then I would do it for all.

---

### Post by Randomskk on 2006-06-27
> Location: Reading, UK
Missed that XD
Is reading really pikey? I went to the uni there once and it seemed OK :/

I see your need for the seperate key thing, although the best bet for the home server would probably be a key stored in the house securely, although one thing to bear in mind - if you kept the key on a USB drive, and someone stole that and the drive, it's STILL useless as you also need the passphrase.
Just shutting down or suspending the laptop and have it decrypt at boot with the USB key is probably easiest, having a filesystem that suddenly encrypts itself would mess up all sorts of things.

An option might be if you have two hard disks, and encrypt one of them to hold data, but just have the base system on the second disk - that way the system could stay running while the second drive was encrypted.

For the server, I think the best idea would be to simply keep the key on the network share, and it needs a passphrase to decrypt, then if the server is stolen the drive is still no use (as, after all, you can't steal it and keep it powered up unless it's being stolen by someone who knows what they are after - in which case, not much is going to help anyway)

For the laptop, requiring a key that's on the USB and a passphrase would work, and while it would remain decrypted the whole time it's on, you could always just lock the desktop, and to get out of that someone would need to reboot anyway - thus needing the key again.

---

### Post by gushy on 2006-06-27
[QUOTE=Randomskk]Is reading really pikey? I went to the uni there once and it seemed OK :/[/QUOTE] Parts of it, the part I've moved to is more pikey than I'd like (trade off between size of house / quality of the area)!  Around the Uni ain't too bad though.

> An option might be if you have two hard disks, and encrypt one of them to hold data, but just have the base system on the second disk - that way the system could stay running while the second drive was encrypted. That's exactly what I was thinking of, well two partitions anyway.
> For the laptop, requiring a key that's on the USB and a passphrase would work, and while it would remain decrypted the whole time it's on, you could always just lock the desktop, and to get out of that someone would need to reboot anyway - thus needing the key again.Yeah that's true, like I said before I'm probably being overly paranoid.  99.9% of the people I meet wouldn't have a clue what to do when faced with my desktop anyway! :p

> For the server, I think the best idea would be to simply keep the key on the network share, and it needs a passphrase to decrypt, then if the server is stolen the drive is still no use I think I just want to use a pgp key and not a passphrase as well; although the server is mine and in my house/garage, other chaps I sub-contract access it as do some of my customers, so if there's a power-cut and I'm away, I need it to come back up decrypted when it finds the key.

---

