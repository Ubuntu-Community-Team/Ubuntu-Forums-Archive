---
title: "I get more and more surprised at how good Ubuntu is every day."
date: 2009-03-17
forum: Testimonials &amp; Experiences
---

### Post by stchman on 2009-03-17
Hello all, just wanting to share something with you.

A friend of mine who is very anal sold a laptop to someone else.  He wanted to wipe the OS completely and reinstall XP.

He said he had lots of data on that PC and he did not want anyone possibly retrieving data by data recovery methods.  I gather he may have had credit card or other personal information.

He did not have a file shredder on his laptop and they usually cost money.

He did not want to go the delete partition route either.

I fired up the LiveCD and noticed there was a CLI app called wipe in the repos.  I apt installed wipe.

I used the following command after mounting the NTFS disk.

```
wipe -rf /media/disk
```

After about 20 minutes the disk where Windows resided was wiped clean.  Apparently wipe is sufficient to stop good file recovery people but the NSA still might be able to get something.

Again, I am surprised at all the free tools that Ubuntu has.

---

### Post by wolfen69 on 2009-03-17
i'm not surprised at all. after 2 years of linux full time, i expect things to work well. i guess i'm just spoiled.

---

### Post by damis648 on 2009-03-17
> **wolfen69 said:**
> i'm not surprised at all. after 2 years of linux full time, i expect things to work well. i guess i'm just spoiled.

Haha, same. :popcorn:

What you should have done for *permanent* deletion would be to take out the drive, plug it in and unmount it, and then:
```
sudo dd if=/dev/zero of=/dev/sdx
```
where sdx is the drive. This would write zeros to the whole drive, which would make it impossible for any data recovery.

---

### Post by stchman on 2009-03-17
> **wolfen69 said:**
> i'm not surprised at all. after 2 years of linux full time, i expect things to work well. i guess i'm just spoiled.

The repos are vast, I love it.

---

