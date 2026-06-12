---
title: "virus scanner question"
date: 2008-06-25
forum: Security
---

### Post by Falc7 on 2008-06-25
Which virus scanner is the best for linux?
I want to scan files for viruses before i pass the files onto windows computers, and also if possible scan my windows partition for windows viruses from my ubuntu partition, what should i use to do this?
I have had problems with avg in the past (always said i didn't have permission to update database), and i was never sure how to update with clamav.

---

### Post by nowshining on 2008-06-25
clamav install the auto-updater in synaptic it should auto-update or install the clamav gui avscan, the package for updating is - clamav - freshclam or something - in synaptic do a search for clamav and in the gui u should find a tab or something for manual updating, etc..

---

### Post by Falc7 on 2008-06-25
I see, that sounds useful, will clam let me scan my windows partition when using ubuntu?

---

### Post by nowshining on 2008-06-25
as long as they are mounted - yes :) it doesn't depend on whether it's fat, ntfs, etc.. or shouldn't care of the filesystem basically.

---

### Post by Alldan on 2008-06-29
i use avast! for linux.
It's free but you need to register (for free) in order to receive a licence key.
Easy to use / graphic interface (called with avastgui in console or after ALT+F2)

---

### Post by Falc7 on 2008-06-29
i'll have a look at avast, i have installed clamav, but when i try to manually update virus definitions, it tells me i have to log in as root, how do i do that?

i have just told clam to scan my windows partition, which is like 30gb, and it finished it in 3 seconds, how is is possible for it to scan this fast and do a good job? Also, even though i told it to scan the entire partition, it says it only scanned 9 files, i am confused.

---

### Post by lisati on 2008-06-29
I use the Linux version of AVG free. One thing, however, that caught me out at first(and other people too, judging by some comments on the AVG forums) is that you have to add your Linux user name to the "avg" user group on your system before the GUI-based update will work properly. (I should have RTFM!)

---

### Post by Falc7 on 2008-06-29
I have downloaded avg for linux, and i thought i had added in the right groups but it still isen't working, perhaps i have done something wrong?

I went to user and groups, unlock, login name: avg, manage groups, users, properties, ticked 'jamie', then ok and closed.

Still isen't updating, saying i don't have permission

---

### Post by lisati on 2008-06-29
> **Falc7 said:**
> I have downloaded avg for linux, and i thought i had added in the right groups but it still isen't working, perhaps i have done something wrong?

I went to user and groups, unlock, login name: avg, manage groups, users, properties, ticked 'jamie', then ok and closed.

Still isen't updating, saying i don't have permission
You might have to log out and then log in again.

---

### Post by Falc7 on 2008-06-29
> **lisati said:**
> You might have to log out and then log in again.

ah yes that worked, thanks
Does avg work equally as well (by that i mean detection levels) as clamav?

---

