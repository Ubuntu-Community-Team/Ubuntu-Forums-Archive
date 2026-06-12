---
title: "WARNING to new users"
date: 2008-08-03
forum: Testimonials &amp; Experiences
---

### Post by ingeva on 2008-08-03
I was having trouble with my local websites. After I set them up with Apache they worked perfectly.

When testing one of the pages today FireFox crashed. This was repeated every time, so I decided to restart the system (Ubuntu 8.04).

The system started FireFox after I logged in, and the system crashed immediately. That is, it went into terminal mode for a moment, and then presented me with the graphic login. After I logged in the same thing happened.

I realized that I had made a minor change in the /etc/hosts file earlier today, so I booted Knoppix LiveCD (I had no Ubuntu live CD), managed to mount the disk drive in RW mode and edited the hosts file from there. I was very anxious when I rebooted Ubuntu.

The hosts file must have been the problem. For the computer itself I had written
 127.0.0.1  <computername>
instead of 
 127.0.1.1  <computername>

This is sufficient to make the system go bananananas as soon as you start a browser.

Just a warning. **Careful with your hosts file!**

Before I start testing those pages again I'll make a FULL backup of my system disk! :)

---

### Post by bodhi.zazen on 2008-08-03
Moved to Testimonials and Experiences as it is not really a support thread.

You should take care with any and all system files , make backups first.

---

### Post by NovaAesa on 2008-08-03
I doubt new users would touch these kind of files anyway.

---

### Post by ingeva on 2008-08-03
> **NovaAesa said:**
> I doubt new users would touch these kind of files anyway.

Well, I am a new user. Had Ubuntu for just over a week. :)

---

### Post by wolfen69 on 2008-08-03
> **ingeva said:**
> Well, I am a new user. Had Ubuntu for just over a week. :)

you are an exception.

---

### Post by ingeva on 2008-08-04
> **wolfen69 said:**
> you are an exception.

A reminder can be in its place anyway. :)

---

