---
title: "Lost 2 of 3 HD's over night"
date: 2007-10-04
forum: Windows
---

### Post by Perpetual on 2007-10-04
All,

I know this is a Linux community but I also know the knowledge runs deep here.

We have a distant branch which woke this morning to a Dell Windows 2000 Server displaying a message:

Container Config Utility
SCSI Select
Disc Utilities

It will not boot into regular or safe mode.  We had a computer shop their go in and check it out.  The tech says that 2 of the 3 drives (1 containing the OS) went out.  All 3 are displaying green lights but they are 'dead'.

Questions, does any of this mean anything to you all?  How would you lose 2 drives over night?

---

### Post by dca on 2007-10-04
Are you sure it's the drives themselves or is it maybe just the SCSI-RAID controller card gone?

---

### Post by Perpetual on 2007-10-04
> **dca said:**
> Are you sure it's the drives themselves or is it maybe just the SCSI-RAID controller card gone?

Honestly, I don't know much more than what I gave at this point.  We are going to get the server down here tomorrow to see what is up.  For what it is worth, the gentleman that look at it is HP Certified...he said the drives were 'dead'.

Thanks for the thought though, will have a look in to that.

---

### Post by dca on 2007-10-04
Good luck, I hope it wasn't a mission critical server.  The only bit to cheer you up I had a NAS appliance w/ four IDE drives in it.  Ran fine for a few years all the time actually.  One day, one of the 160GB drives fails, install a new one, it rebuilds the RAID.  Not one week later another one fails.  That's about the worst I've seen...  Needless to say, the NAS left us and we just put the data on an IBM server....

---

### Post by Perpetual on 2007-10-04
Ouch.  Nah, not a real big deal.  Data back-up every night and it's a small branch.  Just a pain in the ***.

---

### Post by tgalati4 on 2007-10-04
Any evidence of a power outage?  Microwave clocks are good indicators for this.

Sometimes when a machine has been running a long time, any event that causes spindown and respin of the drives can cause issues.

Typically the platter bearings work while spinning, but when hot they require too much torque during startup  causing a SMART error condition and subsequent appearance of a drive failure.

If the machine cools for a couple of hours, try again.  If the machine boots then it's time to replace the drives.  How old were the drives?

---

### Post by Perpetual on 2007-10-04
Nothing else in the branch indicates a power outage or problem.  As for age, I am guessing 5 years.  Not positive.

Hoping to get it down here soon so we can have a look at it.

---

