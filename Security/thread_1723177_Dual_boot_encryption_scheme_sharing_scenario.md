---
title: "Dual boot encryption scheme sharing scenario"
date: 2011-04-06
forum: Security
---

### Post by Marcus Aurelius on 2011-04-06
Hello,

Here is my situation.  I have a dual boot x64 OS running win7 pro on one side, and Ubuntu 10.10 on the other side.  Win7 is on NTFS and Ubuntu is ext4.  Then I have another partition which is Fat32 which I use only for my desktop for the two dual booted machines.  So If I download a file in win7 to the desktop, the win 7 desktop is actually linked to the separate Fat32 partition.  So the file is in that Fat32 partition.  Then when I reboot, That same file pops up on the Ubuntu desktop, because the ubuntu desktop is also linked to the FAT32 partition.  

Now here is my question.  In windows I encrypt files using the method -> right click file -> properties -> advanced -> advanced attributes -> encrypt data checkbox.  The file turns green as its supposed to, no problems.  

Now I can not do this to any of the files in the FAT32 partition.... obviously. 

I have not yet decided how I want to encrypt files in Ubuntu 10.10.  I'd also be willing to encrypt files in win7 differently if it helped me with the following..

I would like to encrypt the FAT32 partition data.  The problem is that I need to have the ability for windows 7 to decrypt the desktop data for use.  THEN when I go into Ubuntu 10.10, Ubuntu also needs to be able to enter a password to decrypt that data.

What encryption program would be the best to use in a unique scenario such as this one?

Thank you.

---

### Post by bodhi.zazen on 2011-04-06
I would use LUKS or Truecrypt.

You can mount a LUKS partition in Windows:

[http://www.freeotfe.org/](http://www.freeotfe.org/)

Truecrypt works on both linux and windows.

---

