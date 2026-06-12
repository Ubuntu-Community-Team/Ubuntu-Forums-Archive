---
title: "HOWTO: Installing NMap 5.20 in x64"
date: 2010-01-22
forum: Security
---

### Post by EJeanmaire on 2010-01-22
If you have been trying to compile & install the new NMAP 5.20 scanning utility as a 64 bit user, you may have run into some issues as I did...

The compiler will halt when you attempt to 'make', saying that you need to recompile using -fPIC.

The fix:  "./configure CXXFLAGS=-fPIC CFLAGS=-fPIC LPFLAGS=-fPIC"

then rerun "make".

I hope this helps someone, as it took me way longer than it should have to get this going.  Enjoy the new versions as it is supposed to have 10,000 updated OS detection signatures and new scripts!

---

### Post by user1397 on 2010-01-23
> **EJeanmaire said:**
> If you have been trying to compile & install the new NMAP 5.20 scanning utility as a 64 bit user, you may have run into some issues as I did...

The compiler will halt when you attempt to 'make', saying that you need to recompile using -fPIC.

The fix:  "./configure CXXFLAGS=-fPIC CFLAGS=-fPIC LPFLAGS=-fPIC"

then rerun "make".

I hope this helps someone, as it took me way longer than it should have to get this going.  Enjoy the new versions as it is supposed to have 10,000 updated OS detection signatures and new scripts!what is it for exactly?

---

### Post by user1397 on 2010-01-23
ah nevermind.

---

