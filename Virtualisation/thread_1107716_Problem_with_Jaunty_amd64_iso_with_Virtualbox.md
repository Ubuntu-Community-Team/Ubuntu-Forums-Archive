---
title: "Problem with Jaunty amd64 iso with Virtualbox"
date: 2009-03-27
forum: Virtualisation
---

### Post by roastpotato on 2009-03-27
Hello there, although this is my first post I have used ubuntu for more than a year. That's proof that ubuntu is that good :)

Tonight, I decided to take the plunge and downloaded the 9.04 beta amd64 iso for my Virtualbox(version 2.0.4) on my core 2 quad desktop.

It worked perfectly until it said "This kernel requires a x86-64 CPU, but only detected an i686 CPU" This can't be right as my 8.10 is amd64.

Is this a problem with Virtualbox or Jaunty.

Thanks

---

### Post by tienhn on 2009-03-29
Yes, I got the same error message. Installed x86 Ubuntu fine but not AMD64.

---

### Post by xebian on 2009-03-29
> **roastpotato said:**
> Hello there, although this is my first post I have used ubuntu for more than a year. That's proof that ubuntu is that good :)

Tonight, I decided to take the plunge and downloaded the 9.04 beta amd64 iso for my Virtualbox(version 2.0.4) on my core 2 quad desktop.

It worked perfectly until it said "This kernel requires a x86-64 CPU, but only detected an i686 CPU" This can't be right as my 8.10 is amd64.

Is this a problem with Virtualbox or Jaunty.

Thanks

Your version of Vbox is way outdated and does not support 64-bit guest OS.  Upgrade to the latest which 2.1.4.

---

### Post by tienhn on 2009-03-29
Actually I am using Vbox 2.1.4 and I already turn VM option on in my BIOS.

:)

---

### Post by roastpotato on 2009-03-29
It now works perfectly now. Thank you so much

> **tienhn said:**
> Yes, I got the same error message. Installed x86 Ubuntu fine but not AMD64.

In the settings menu for your guest OS, have you selected your OS type as ubuntu (64 bit)?

---

### Post by jonny.dee on 2009-03-30
I am experiencing exactly the same problem. I am using VB 2.1.4 and my host OS is Intrepid Ibex amd64. As guest OS I selected Ubuntu (64 bit).

EDIT: Also works now. tienhn's post gave me the right hint. I had to turn virtualization on in BIOS. Thanks :)

---

