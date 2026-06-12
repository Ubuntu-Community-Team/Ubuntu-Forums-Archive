---
title: "Does Wine support Visual Basic 2005/2008"
date: 2009-04-11
forum: Wine
---

### Post by D@RKKIN6 on 2009-04-11
Hi

I want to know if Visual Basic 2008 is supported by Wine.
Because at school we are using Windows XP and as a programming language Visual Basic 2005/2008, 
at home I'm trying to get used to Ubuntu 8.10, 
so it would be easy for me to use VB2005/2008 on Ubuntu, so I don't need to restart my computer to use Ubuntu or Windows. 
And I want to ask if there is an "WINDOWS EMULATOR"(not WINE) for Ubuntu (like DOS emulator or similar)?

Thank you

---

### Post by hikaricore on 2009-04-11
Did you check the WINE AppDB per the sticky posted at the top of thie forum?

---

### Post by asdfoo on 2009-04-11
> **D@RKKIN6 said:**
> 
And I want to ask if there is an "WINDOWS EMULATOR"(not Wine) for Ubuntu (like DOS emulator or similar)?

Thank you

If you have a valid license for Windows, you can install it using VirtualBox which is an x86/x86-64 emulator.

---

### Post by sonicb00m on 2009-04-11
> **D@RKKIN6 said:**
> Hi

I want to know if Visual Basic 2008 is supported by Wine.
Because at school we are using Windows XP and as a programming language Visual Basic 2005/2008, 
at home I'm trying to get used to Ubuntu 8.10, 
so it would be easy for me to use VB2005/2008 on Ubuntu, so I don't need to restart my computer to use Ubuntu or Windows. 
And I want to ask if there is an "WINDOWS EMULATOR"(not WINE) for Ubuntu (like DOS emulator or similar)?

Thank you

NO and i wouldnt bother trying.

Í also use virtualbox with xp inside. windows seamless mode works a treat.

---

### Post by D@RKKIN6 on 2009-04-11
> **hikaricore said:**
> Did you check the WINE AppDB per the sticky posted at the top of thie forum?

Yes but the site is complicated
I don't know if it runs on 32 bit or 64bit version

My Ubuntu is 32bit version

---

### Post by chrisjsmith on 2009-04-11
Forget Wine - VS.Net is a huge beast.  I doubt it will ever work properly.

I'm using VMware server 2.0 (which is free incidentally and works nicely on 8.10/9.04) with XP on it and Visual Studio 2008.  I use tsclient to connect to the XP box as it's more responsive and works better than VirtualBox/VMware workstation.  Plus it doesn't get in the way on your desktop then either.

---

### Post by asdfoo on 2009-04-11
> **D@RKKIN6 said:**
> Yes but the site is complicated
I don't know if it runs on 32 bit or 64bit version

My Ubuntu is 32bit version

Wine is distributed for Ubuntu as 32bit only.

---

### Post by asdfoo on 2009-04-11
> **chrisjsmith said:**
> Forget Wine - VS.Net is a huge beast.  I doubt it will ever work properly.



why do you doubt it will work properly?  It's just a matter of time, give it a year.

---

### Post by chrisjsmith on 2009-04-11
> **asdfoo said:**
> why do you doubt it will work properly?  It's just a matter of time, give it a year.

VS2008 is full of nasty Pinvokes, is partly written in .Net and C++ and relies on lots of new functionality in MFC, bundles multi-platform debuggers and the like.  It will never work properly.  Believe me.  It doesn't even work properly on Windows.  If they do make it work, it'll be in 7 years by which time people will want VS11 working.

Rewrite the stuff in python and not be tied to the platform!

Sorry to by cynical but VS 2002 still doesn't work!

---

### Post by sonicb00m on 2009-04-11
> **asdfoo said:**
> why do you doubt it will work properly?  It's just a matter of time, give it a year.

It's been 7 years since VS2002 and that doesn't even work properly.

---

### Post by asdfoo on 2009-04-11
> **sonicb00m said:**
> It's been 7 years since VS2002 and that doesn't even work properly.

You're welcome to fix it.

---

### Post by jflaker on 2009-04-11
Nope,
Install VirtualBox and setup Windows XP with about 7-12GB of disk space
Share a folder under VirtualBox to save your stuff to your $HOME/SomeDir

Works great for me for the last year or so......

---

### Post by sonicb00m on 2009-04-12
> **asdfoo said:**
> You're welcome to fix it.

I don't know what your problem is over this but VS doesn't work in Wine and is unlikely to. The best solution right now for anyone seeking to be productive in VS within a Linux is environment is to install Virtual Box or another virtual machine and run it from inside an XP installation or something similar. It's the only way right now.

I've got very little interest in the Wine project as it is, never mind spending my time trying to get a complex program like visual studio working. Something which I lack any competence to try in the first place.

Your "give it a year statement" is not only unproductive it's total conjecture. It insinuates that all the person has to do to get it working is sit on his **** for a bit and hope for the best because, in your opinion, the applications will just work "in time".

---

### Post by hikaricore on 2009-04-12
> **sonicb00m said:**
> Your "give it a year statement" is not only unproductive it's total conjecture. It insinuates that all the person has to do to get it working is sit on his **** for a bit and hope for the best because, in your opinion, the applications will just work "in time".

Actually many programs run under WINE within or less than a year after release.
This is a common trend.  Perhaps there's just so little interest in fixing bugs relating to VB when Linux has so many other native options for scripting and programing.

---

### Post by TimothyLuke on 2009-04-14
If all you are looking at doing is working through your class examples on your linux box, You might be able to get away with MONO and Eclipse.  It really depends a lot on the elements of .NET that you are using with VB200x and if they are part of the MONO libraries.  If nothing else you will learn a lot about VB, .NET, Linux and MONO attempting this.

---

### Post by directhex on 2009-04-14
> **TimothyLuke said:**
> If all you are looking at doing is working through your class examples on your linux box, You might be able to get away with MONO and Eclipse.  It really depends a lot on the elements of .NET that you are using with VB200x and if they are part of the MONO libraries.  If nothing else you will learn a lot about VB, .NET, Linux and MONO attempting this.

Why Eclipse? Its Mono support is dreadful at best.

"mono-vbnc" is the package with a VB.NET compiler in it though, and "monodevelop" for an IDE

---

### Post by x001 on 2009-04-15
I use MonoDevelop for C#. I saw an option for VB.NET as well.

---

