---
title: "DOD Wipe"
date: 2008-06-17
forum: Security
---

### Post by DGortze380 on 2008-06-17
Pardon the newbie question. I've been searching for a few hours now and I'm more confused than when I started...

I told I friend I'd figure out how to DOD wipe his Hard Drive for him. I was under the impression that it involved two formats writing zeros to every bit, three writing randoms, and two more writing zeros, and running a checksum between each step.

I assumed I'd be able to do this using a live cd, probably knoppix. Can someone point me to a howto, or give me some pointers on how I might do this? I assumed I could use fdisk. I'm not quite sure how to run a checksum, or really what it would even tell me.

Any help would be greatly appreciated.

---

### Post by WorldTripping on 2008-06-18
It would be a lot easier to just use [http://dban.sourceforge.net/]("http://dban.sourceforge.net/").

Download the iso burn up a CD and boot from it.

It pretty much has all of the HDD wiping methods that you need.

---

### Post by hyper_ch on 2008-06-18
basically you can use this:

```

sudo dd if=/dev/urandom of=/dev/sdX

```
I think "sudo" won't be necessary on Knoppix live cd and of (output file) will be the harddisk he wants to have wiped. This operation will take a looong time but IMHO securely deletes eveything... just make sure that /dev/sdX is the actual drive/partition and that it's not mounted.

---

### Post by DGortze380 on 2008-06-18
Ok. I need to look into what urandom is, because the way I understand that, it would be copying urandom to the hard disk (I'm obviously off on something, because I know it actually rights random numbers to every bit)... also, will this cause any problems as far as mounting the drive after this completes in order to format ntfs for a windows install?? Do I need to clear the first part of the drive for the partition table?

---

### Post by hyper_ch on 2008-06-18
it will just overwrite the whole thing with randon data.... however generating them takes long.... once it's done, you'll just need to format it to whatever filesystem you want... or rather you first need to create a partition and then format it...

---

### Post by DGortze380 on 2008-06-18
alright, thanks for the help, I'm going to give it a try on an old drive I have laying around first.

---

### Post by hyper_ch on 2008-06-18
just make sure you select the rigth drive/partition with of=/dev/sdX...

---

### Post by tr333 on 2008-06-18
> **WorldTripping said:**
> It would be a lot easier to just use [http://dban.sourceforge.net/]("http://dban.sourceforge.net/").

Download the iso burn up a CD and boot from it.

It pretty much has all of the HDD wiping methods that you need.

I second this.  dban is incredibly simple to use for clearing HDDs, and it's a lot faster if you have multiple drives to clear.

---

### Post by tact on 2008-06-18
I support the dban option too.  download it, burn to CD, boot  and say bye bye to whatever you want wiped

---

### Post by HermanAB on 2008-06-18
Here is the right way to erase a disk drive: 
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Any other method will leave some data behind.

---

