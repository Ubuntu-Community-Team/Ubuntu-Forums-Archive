---
title: "ubuntu alternative disk"
date: 2010-07-16
forum: Security
---

### Post by Drenriza on 2010-07-16
I'm currently trying to install ubuntu from an alternative disk, on a test machine. To provide my install with an encryption, in the case that my (work) laptop gets stolen. Since i have "sensitive" data on the laptop.

Under the install im asked if i want to setup encrypted LVM up. And im wondering is this the encryption?
How secure is it? i did set it up with an 16 digit pass phrase, is this enough? And are their back-doors to get
around the pass phrase, thus making it useless?

Also ive been wondering. On an encrypted machine. Can i do all my normal stuff on that like,

ssh, youtube, gmail, wine, games, with more.

All that i would be able to do on my normal not encrypted work-pc? Or is their some restrictions since its encrypted.

Hopes it makes sense.

Thanks on advance.

---

### Post by rookcifer on 2010-07-16
> **Drenriza said:**
> Under the install im asked if i want to setup encrypted LVM up. And im wondering is this the encryption?

LVM is just a way to achieve logical volumes, which is used by the alternate disk for allowing all of the volumes to be treated as one.  That is, you can create various partitions and encrypt/decrypt them all at the same time without having to enter an pass phrase 4 different times at boot.

> How secure is it?

It's secure enough to stop major governments from getting your data.

>  i did set it up with an 16 digit pass phrase, is this enough?

It depends on the strength of the password -- that is, how much entropy the password possesses. A password like "abcdefghijklmno" will not be as strong as "#&^4fkeRTn&89R.}" even though they are the same length.


 > And are their back-doors to get
around the pass phrase, thus making it useless?

There's the [evil-maid attack]("http://theinvisiblethings.blogspot.com/2009/10/evil-maid-goes-after-truecrypt.html"), which requires someone to have access to the machine without your knowledge so they can plant at rootkit on it.  Later, when you use the machine like normal, the rootkit will sniff your pass phrase and send it to a remote machine.  There is no other defense against this other than to not leave your laptop unattended.  

A possible defense against these sorts of attacks (which we don't have with Linux right now) would be two-factor authentication (that is, use a pass phrase along with another method for unlocking the volume.  TPM provides something like this).

Bottom line:  Don't leave your laptop unattended around people you don't trust.  Most people would probably steal it rather than trying to put a keylogger or rootkit on it anyway.  If it's stolen, the encryption will protect it (assuming it was powered down when stolen).

> Also ive been wondering. On an encrypted machine. Can i do all my normal stuff on that like,

ssh, youtube, gmail, wine, games, with more.

Yes.  The encryption is completely transparent (except for a small performance overhead).  By the way, I suggest you use 128 bit encryption because it wont give as much of a performance hit as 192 or 256 bit will.  So, it would be best to use "aes-cbc-essiv:sha-256."

---

### Post by Drenriza on 2010-07-16
Thanks for the answer.

How do i define the bit strength 128 / 192 / 256 bits? that i want to use. I have not seen a option to select this, yet.

Question. Lets say i make a ridiculous strong pass phrase, then i go on vacation hit my head and forget it. I suspect i'm royally screwed then?

---

### Post by rookcifer on 2010-07-16
> **Drenriza said:**
> Thanks for the answer.

How do i define the bit strength 128 / 192 / 256 bits? that i want to use. I have not seen a option to select this, yet.

I found this on Google, which is from [this blog]("http://webcache.googleusercontent.com/search?q=cache:O3tAATWTSzYJ:learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/+ubuntu+alternate+cd+choose+algorithm&cd=5&hl=en&ct=clnk&gl=us") (in the comments):

*During installation you can configure the encryption options in the partitioner: it’s in the screen after you select the partition format to be “volume for encryption”.*

That sounds right from memory.

> Question. Lets say i make a ridiculous strong pass phrase, then i go on vacation hit my head and forget it. I suspect i'm royally screwed then?

Yes, you are royally screwed.  No chance to recover the data.

---

### Post by iponeverything on 2010-07-16
I used 10.04 alternate 64bit disk to setup LVM encryption on new Lenovo x200. To be honest I don't notice any performance hit like I did on my old Pentium M 1.7 Ghz machine -- it is totally transparent.  

I had originally set it up on second drive to use when I am on the road, but since I have had zero issues and no inconveniences having the encrypted disk -- I just made it my everyday disk. I use a very long pass phrase, but it is a line from an obscure Irish poem that I know, so it easy to remember. You can always do something like email a clue to the passphrase to your email account in case your forget it.

Encryption will keep data safe if the laptop is stolen. The time, effort and money it would take would be far disproportionate to value of data.  

Governments don't need to be able to crack the encryption as they have very compelling ways to get you to cooperate.

---

### Post by wacky_sung on 2010-07-16
Personally i find it kinda waste of effort running on an encrypted hard disk,unless you have real important documents to store.If those documents are so important then you shall never get it to the public or connected to the net.Not even to mention of losing it or stolen.

The simple way is to create a encrypted folder with a length of password with at least 20 characters including those very special characters **[COLOR="Red"]&#1574;&#1575;&#1576;&#1577;&#1578;[/COLOR]** in which went beyond crackable chance.

---

### Post by Drenriza on 2010-07-16
Thanks for all the help everybody.

Thinking about doing the encryption, 256bit with a pass phrase of 12-20 characters with special characters, letters, symbols, numbers.

under the install on a test system i had lieng around. I was under the install asked if i wanted to encrypt my home folder. If i do a 256bit encryption, is their then a need to do encryption on home folder also? does it give x-tra protection?

---

### Post by iponeverything on 2010-07-16
> **wacky_sung said:**
> Personally i find it kinda waste of effort running on an encrypted hard disk,unless you have real important documents to store.If those documents are so important then you shall never get it to the public or connected to the net.Not even to mention of losing it or stolen.

The simple way is to create a encrypted folder with a length of password with at least 20 characters including those very special characters **[COLOR="Red"]&#1574;&#1575;&#1576;&#1577;&#1578;[/COLOR]** in which went beyond crackable chance.

I travel a lot. Getting access to the my loptop would give someone access to banking, taxes, email that would make very easy for someone to steal my money - my identity and generally make my life a very difficult.

---

### Post by wacky_sung on 2010-07-16
> **iponeverything said:**
> I travel a lot. Getting access to the my loptop would give someone access to banking, taxes, email that would make very easy for someone to steal my money - my identity and generally make my life a very difficult.

What most vital things for you to do is just keep a encrypted thumb drive / get a paid service provided with an encrypted storage for you.

People will go for laptop than a cheap thumb drive if they really wanna steal.Beside that,thumb drive is handy.I will recommend you to get a titanium thumb drive.

---

### Post by iponeverything on 2010-07-16
> **wacky_sung said:**
> What most vital things for you to do is just keep a encrypted thumb drive / get a paid service provided with an encrypted storage for you.

People will go for laptop than a cheap thumb drive if they really wanna steal.Beside that,thumb drive is handy.I will recommend you to get a titanium thumb drive.

thanks, it is another way to do it. 

Encrypting my drive is easy, it works and I don't have to buy or sign up for anything.

---

### Post by Drenriza on 2010-07-17
when you encrypt your laptop hdd.

When happens if u copy some files to another disk?
I suspect they will be encrypted or?

---

### Post by cariboo on 2010-07-17
If you copy the files while you are logged in, they are unencrypted, so you are copying unencrypted files. If you try copying files while not logged in good luck.

---

