---
title: "Hard drive Encryption, how possible?"
date: 2009-12-17
forum: Security
---

### Post by Btheone on 2009-12-17
How possible is it to encrypt part of my hard drive, such as personal data etc. Anyone have any ideas on good programs to use?

Thanks.

---

### Post by User3k on 2009-12-17
Truecrypt is my favorite

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by Cheesemill on 2009-12-17
The easiest way to set up full-disk encryption is to do it when first installing your system.

This can be done by using the Alternate CD instead of the Live CD and selecting 'Install with encrypted LVM' at the partitioning stage.

---

### Post by EJeanmaire on 2009-12-17
> **Btheone said:**
> How possible is it to encrypt part of my hard drive, such as personal data etc. Anyone have any ideas on good programs to use?

Thanks.

Read the sticky at the top of this forum for all the encryption details you need and more.

---

### Post by BkkBonanza on 2009-12-17
If you want to encrypt a user home directory it can be done easily with, 

adduser --encrypt-home username

If you already have a user then probably create a new one and copy data over and get rid of the old one.

---

### Post by FuturePilot on 2009-12-17
> **BkkBonaza said:**
> If you want to encrypt a user home directory it can be done easily with, 

adduser --encrypt-home username

If you already have a user then probably create a new one and copy data over and get rid of the old one.

You can convert your existing user to an encrypted /home 

See [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

---

### Post by daenoid on 2009-12-17
Here is another possible solution that works on a per directory basis: [https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by RedSingularity on 2009-12-17
+ 1 for truecrypt

---

### Post by jollyjollyroger on 2009-12-17
what if i want uber-epic encryption that a bootable USB OS cannot read?
entire ubuntu partition... non-existant to anything other than an OS with my pw...?

---

### Post by daenoid on 2009-12-17
> **B.G.plzDeye said:**
> 
entire ubuntu partition... non-existant to anything other than an OS with my pw...?

I believe the very nature of encryption solves this problem.

---

### Post by jollyjollyroger on 2009-12-17
> **daenoid said:**
> I believe the very nature of encryption solves this problem.
thank you kind sir.

---

### Post by Cheesemill on 2009-12-18
> **B.G.plzDeye said:**
> what if i want uber-epic encryption that a bootable USB OS cannot read?
entire ubuntu partition... non-existant to anything other than an OS with my pw...?

Then just install with full-disk encryption like I mentioned above.

---

### Post by BkkBonanza on 2009-12-18
I just wanted to add a comment for others. I followed the tutorial above for converting your home to ecryptfs - encrypted home. It worked well. I came across a little trick too that may be handy for others.

I had a large amount of data in my home that I really didn't want to have encrypted. It is my .VirtualBox directory and contains multiple virtual hard drives. They already go through a virtual filesystem driver and I didn't want the files to also be encrypted.

I used symlinks to work this out and it does work well. Instead of copying .VirtualBox into my encrypted home I moved it into /home/.ecryptfs/$USER/ so it sits there next to .Private. Then I symlinked it into my home so it would work just the same as before.

ln -s /home/.ecryptfs/$USER/.VirtualBox /home/$USER/.VirtualBox

VirtualBox still works with the symlink. So this is a method for creating excluded portions of your home that are not encrypted. In this case I have 34G of stuff that I wanted the freedom to move easily around without being encrypted.

Hope that helps someone else needing to do this type of thing.

---

### Post by Btheone on 2009-12-18
Thanks All, I decided to use; Truecrypt.

---

### Post by paradigm2 on 2009-12-18
> **BkkBonaza said:**
> I just wanted to add a comment for others. I followed the tutorial above for converting your home to ecryptfs - encrypted home. It worked well. I came across a little trick too that may be handy for others.

I had a large amount of data in my home that I really didn't want to have encrypted. It is my .VirtualBox directory and contains multiple virtual hard drives. They already go through a virtual filesystem driver and I didn't want the files to also be encrypted.

I used symlinks to work this out and it does work well. Instead of copying .VirtualBox into my encrypted home I moved it into /home/.ecryptfs/$USER/ so it sits there next to .Private. Then I symlinked it into my home so it would work just the same as before.

ln -s /home/.ecryptfs/$USER/.VirtualBox /home/$USER/.VirtualBox

VirtualBox still works with the symlink. So this is a method for creating excluded portions of your home that are not encrypted. In this case I have 34G of stuff that I wanted the freedom to move easily around without being encrypted.

Hope that helps someone else needing to do this type of thing.

Just wanted to say thanks for the tip.  I suppose this could solve things like key based ssh authentication issues or possibly issues with having to use a cron script in a user directory without being logged in.

---

