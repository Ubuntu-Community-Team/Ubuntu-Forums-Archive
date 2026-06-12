---
title: "Securely delete file in TrueCrypt volume"
date: 2011-01-04
forum: Security
---

### Post by SilenceW on 2011-01-04
Good afternoon.

First things first: I am a relatively casual computer user; quite competent as a *user*, I hope, but I am not a coder, hacker, IT specialist, or any other such luminary.  As Edmund Blackadder once said:

"I am one of those people who are quite happy to wear cotton, but have absolutely no idea how it works."

So I am with operating systems, especially this one.

'This one' being Ubuntu 9.10 (yes, I know I really should upgrade).  I keep a number of confidential files in a TrueCrypt container which is a standalone file in my Documents folder.  I'd like to delete some of these, but I want to do it as securely as I can, but I believe if I simply hit 'Delete' with the file selected it'll move the file to the Deleted Items folder.  This, I assume, means that the file is taken out of the encrypted volume and stored unencrypted in the Deleted folder.

I've been reading a little about the Shred command, and there seems to be some question about whether it works effectively with a journalled file system; and since I have no idea whether I'm using a journalled file system, or how to find out, I'm treating Shred and other over-writing secure deletion tools as ineffective for now.

With this in mind, can anyone advise me how I can protect the file stored in the TrueCrypt volume, and delete it in place, without taking it out of the encrypted area?  And, further to that, can anyone tell me whether in fact the file is actually secured while it's in the encrypted volume?  For all I know, just opening the volume may result in copies being made somewhere (apart from RAM).

The obvious first response would be to tell me that with such a lamentable lack of knowledge I've no place trying to use Linux or encryption in the first place.  I'll take that one as read, but since I'm here, if anyone has any other suggestions I'd appreciate it. :D

---

### Post by Grenage on 2011-01-04
Unless otherwise specified, you'll be using EXT3 or EKT4 (journalled).

I believe that while there is data in the journal, that will only be the case if it has just been written - it gets overwritten very quickly.

---

### Post by endotherm on 2011-01-04
the ubuntu defaults for ext3 do NOT use journaling, so you should be fine there, but if you are really concerned, use ext2. ext4 does use journalling by default, but can be switched to ordered mode if you wish.

as for wiping the interior of a truecrypt volume, that is not really needed, for most intents and purposes. if you want to do it, wipe/shred/sfill will do alright, but is largely unneeded. 

from the truecrypt FAQ:
> 

          **Do I have to "wipe" free space and/or files on a TrueCrypt volume?**
       Remark: to "wipe" = to securely erase; to overwrite sensitive data in order to render them unrecoverable. 
        
      If you believe that an adversary will be able to decrypt the  volume (for example that he will make you reveal the password), then the  answer is yes. Otherwise, it is not necessary, because the volume is  entirely encrypted.

[http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)

read teh faq, it answers several of your questions about leakage as well.

---

### Post by rookcifer on 2011-01-04
OP, just use the shred command to remove the file.  If you are paranoid, then use sfill (in the secure-delete package) to wipe the free space of your non-encrypted partitions.  That will probably be the only way to ensure that the file hasn't "leaked" out of the encrypted container.

This is why I prefer full disk encryption.

---

### Post by SilenceW on 2011-01-06
> **endotherm said:**
> the ubuntu defaults for ext3 do NOT use journaling, so you should be fine there, but if you are really concerned, use ext2. ext4 does use journalling by default, but can be switched to ordered mode if you wish.

as for wiping the interior of a truecrypt volume, that is not really needed, for most intents and purposes. if you want to do it, wipe/shred/sfill will do alright, but is largely unneeded. 

from the truecrypt FAQ:
[http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)

read teh faq, it answers several of your questions about leakage as well.
Thanks for that.  With regard to file deletion, I was just concerned that using the standard delete command in the Ubuntu GUI would copy the file to a non-encrypted area (presumably 'Deleted Items' is in an unsecured section of the drive) before 'deleting' it.  I may have this completely wrong and 'Deleted Items' may read from wherever the file is to construct its contents list, but I wanted to rule out any potential issues there.

[quote=rookcifer] If you are paranoid, then use sfill (in the secure-delete package) to  wipe the free space of your non-encrypted partitions.  That will  probably be the only way to ensure that the file hasn't "leaked" out of  the encrypted container.

This is why I prefer full disk encryption.[/quote]
I admit: I hadn't taken the option to encrypt the home drive on  installation, although to be honest the risk level even on my  confidential files is fairly low..  Compromise would be pretty  irritating but nothing catastrophic.  I think as long as Shred (which  I've now added to the context menu) removes the file in place without moving it out of the Truecrypt container volume I'm fairly happy.

Thanks also to Grenage for taking the time to reply.

Have many good days. :)

---

### Post by rookcifer on 2011-01-07
> **derekKinny said:**
> [www.tooLongPath.com](www.tooLongPath.com) saved me lot of time for solving this

^ Spam.  He's posting Windows bloatware on a Linux forum.

---

