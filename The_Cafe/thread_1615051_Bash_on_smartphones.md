---
title: "Bash on smartphones"
date: 2010-11-06
forum: The Cafe
---

### Post by geo909 on 2010-11-06
Hello everybody,

Do you know if there is any smartphone where I could use bash? I mean, having a terminal application that can run every command line program for linux?

Probably a naive question, but I now absolutely nothing about smartphones.

Thanks in advance.

---

### Post by amitabhishek on 2010-11-06
Yes. Nokia N900 or Android phones with Cyanogenmod ROMs.

---

### Post by geo909 on 2010-11-06
Thanks, that sounds good!

So, this has a perfectly working terminal emulator? Should I expect to have some issues or every terminal app that works for my computer should work there? 

Again, sorry if I ask something obvious.

---

### Post by Duncan J Murray on 2010-11-06
Well the N900 doesn't have the repositories of ubuntu - so, for example, I haven't got Mutt working properly on it yet (I can't send email on it!).

Duncan.

---

### Post by Sporkman on 2010-11-06
There are SSH clients for the iPhone that you can use to remotely log into other machines (& then use their bash sessions).

---

### Post by ve4cib on 2010-11-06
> **Duncan J Murray said:**
> Well the N900 doesn't have the repositories of ubuntu - so, for example, I haven't got Mutt working properly on it yet (I can't send email on it!).

Duncan.

I don't remember if Ubuntu has repositories for ARM-based systems (like the N900), but you should be able to add Debian's repositories and fetch whatever you need from there at the very least.


> So, this has a perfectly working terminal emulator? Should I expect to have some issues or every terminal app that works for my computer should work there?

Well, not every terminal app will necessarily work as you'd expect.  The N900, for example, uses an ARM processor, so you can't just copy over your i386 or amd64 binaries and expect them to work.  But provided you can find an ARM-compatible version, you should be able to run it.  Or if it's written in an interpreted language (like Python), or a bytecode-interpreted language (like Java) you should be able to run it without any problems.

If you've got the source code you can cross-compile for ARM as a last-resort, assuming you can't find it on any repositories.

---

### Post by NCLI on 2010-11-06
> **amitabhishek said:**
> Yes. Nokia N900 or Android phones with Cyanogenmod ROMs.
Any Android phone can run bash, you don't even need root.

---

### Post by geo909 on 2010-11-08
Thanks for your replies, guys! Good to know.

---

### Post by conundrumx on 2010-11-08
The N900 is the only "real" Linux phone you can get your hands on right now.  Android toes the line.

---

