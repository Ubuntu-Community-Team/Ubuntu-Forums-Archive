---
title: "i am a newbie and happy to be here"
date: 2010-08-15
forum: Security
---

### Post by PSioNiC STRaNGLeR on 2010-08-15
I am a Newbie,

I installed nubutu on an old non functioning ibm centrino that i am using right now! I cant believe the computer is even working-and fast-I am amazed! I am test-driving everything on this computer first.

My question is; When i installed Ubuntu, i pressed use entire disk. I _**don't**_ want to retrieve anything. I just want to know if any old information is still there somewhere. Do I need to wipe/shred the hard drive first and then re-format the drive for Ubuntu and then install to make sure there is no private information on it, or does the install disk I made do this already.

The reason I am asking is if Ubuntu can make this old piece of %$#@ work great and all previous private information has been wiped, then I will install them on my families old computers (6) and donate them to my father's school in Africa.

Thanking everyone in advance for any advice. :popcorn:

---

### Post by PSioNiC STRaNGLeR on 2010-08-15
I am a Newbie,

I installed nubutu on an old non functioning ibm centrino that I am  using right now! I cant believe the computer is even working-and fast-I  am amazed! I am test-driving everything on this computer first.

My question is; When I installed Ubuntu, I pressed use entire disk. I _**don't**_  want to retrieve anything. I just want to know if any old information  is still there somewhere. Do I need to wipe/shred the hard drive first  and then re-format the drive for Ubuntu and then install to make sure  there is no private information on it, or does the install disk I made  do this already.

The reason I am asking is if Ubuntu can make this old piece of %$#@ work  great and all previous private information has been wiped, then I will  install them on my families old computers (6) and donate them to my  father's school in Uganda, Africa.

Thanking everyone in advance for any advice:popcorn:

---

### Post by cariboo on 2010-08-15
The complete disk is formatted when you choose **use the whole disk**, it is debatable if you actually need to wipe the whole disk first. For your peace of mind I would suggest using [dban]("http://www.dban.org/"), before installing an os on the other computers.

---

### Post by NovaAesa on 2010-08-15
I'm fairly sure that the previous data could still be on the disk (although it would be hard to access - the person trying to get the data would need a professional).

If you are extremely concerned about privacy, the best bet would be to shred the disk using a livecd, then do a reinstall.

---

### Post by corrytonapple on 2010-08-15
Boot from the live CD and go to **System>Administration>Disc Utility**.  Choose the Hard Drive you want to wipe and click format. ext4 is recommended. Then you can do it over and over to make sure the data is erased. Also, keep your posts in one forum. One thread may be locked due to cross posting.

---

### Post by fatality_uk on 2010-08-15
In most common use, the data won't be able to be read. There may be *some* data in there, most likely on the outside of the disk, but it would take more than a quick scan of the disk to get at it.

---

### Post by PSioNiC STRaNGLeR on 2010-08-15
Thank you for the advice. I think I will wipe the drives first as they are going to Africa. Should have done all this years ago ;)

---

### Post by cariboo on 2010-08-15
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by PSioNiC STRaNGLeR on 2010-08-15
sorry, thought first one was in wrong forum, this is first time i ever even posted a post on the web :)

---

### Post by PSioNiC STRaNGLeR on 2010-08-15
thanx, I will do that, i can't take any chances-cheers

---

### Post by FuturePilot on 2010-08-15
> **corrytonapple said:**
> Boot from the live CD and go to **System>Administration>Disc Utility**.  Choose the Hard Drive you want to wipe and click format. ext4 is recommended. Then you can do it over and over to make sure the data is erased. Also, keep your posts in one forum. One thread may be locked due to cross posting.

Format != secure wipe.

---

### Post by shoppertrip on 2010-08-16
same situation happened to me a few months ago..and after trying many means in vain, i took it to a PC workshop where most of my data was restored. ..but unfortunately..my previous attempts had destroyed some of it.

---

### Post by JustChris21 on 2010-08-16
> **corrytonapple said:**
> Boot from the live CD and go to **System>Administration>Disc Utility**.Then you can do it over and over to make sure the data is erased. .

Yeah this is the best way. Takes about 15 reformats the fully 'lose' all the data iirc.

---

### Post by cdenley on 2010-08-16
> 
Yeah this is the best way. Takes about 15 reformats the fully 'lose' all the data iirc.

As already said, formatting is not erasing. Formatting simply writes enough to make it a usable filesystem. It overwrites only a small portion of existing data. I believe doing the same reformat over-and-over would only overwrite the same locations over-and-over, leaving the remaining data untouched. If you need to protect your unencrypted data from being read, you must overwrite all of it. If you're in a hurry, just copy /dev/zero and overwrite it with nulls. If you're really paranoid, you can use multiple passes with random data and/or patterns (shred or dban).

---

### Post by bodhi.zazen on 2010-08-16
As has been pointed out, formatting alone does not affect all the data (you may loose some data of course).

I would add the gutmann theory has been debunked, one pass is sufficient (save on HD wear and tear).

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough-part-2-this-time-with-screenshots](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough-part-2-this-time-with-screenshots)

---

### Post by mailc on 2010-08-16
As already said several times, the old files are still on the disc despite all the formatting.

You should do the "shredding" . 

To shred, start with a live cd,  enter in terminal :  sudo shred -vfz -n 1 /dev/sdx       (replace x  with the drive -probably a )  and let it shred.                                              You will need to reinstall Ubuntu.
If you have time , you can replace the '1'  with another number and it will shred several more times .

But it is not necessary to shred 38 times as previously recommended by Gutmann .

---

### Post by corrytonapple on 2010-08-16
> **mailc said:**
> As already said several times, the old files are still on the disc despite all the formatting.

You should do the "shredding" . 

To shred, start with a live cd,  enter in terminal :  sudo shred -vfz -n 1 /dev/sdx       (replace x  with the drive -probably a )  and let it shred.                                              You will need to reinstall Ubuntu.
If you have time , you can replace the '1'  with another number and it will shred several more times .

But it is not necessary to shred 38 times as previously recommended by Gutmann .
Yes, do this.;)

---

