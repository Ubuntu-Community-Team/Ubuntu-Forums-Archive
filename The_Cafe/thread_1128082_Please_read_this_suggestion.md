---
title: "Please read this suggestion"
date: 2009-04-17
forum: The Cafe
---

### Post by ssdt on 2009-04-17
Linux, mostly Ubuntu users like me who is a complete newbie at this has faced a lot of problems with the installation of Ubuntu softwares. There is a reason to that too. The most important reason for that is the file type. Because of the file type, a person like me would say that .deb file is the best one around but there is not much applications that uses .deb file.
Due to my brother and also me, I have to install Sopcast in the Ubuntu computer but I faced problem with the .deb because there is no official .deb package for Ubuntu's Sopcast. There's .tar, .tar.gz and many other formats. These formats does not only cause kind of catastrophic problems but many more than that.
I could not compile the file and I couldn't make it worth using. I wondered if I could actually see the cricket games through this but I couldn't.
At last I found a .deb package that actually works and it was gsopcast. gsopcast got installed in my computer but it had problems too. It's major problem was that it couldn't play anything from the site I watch it from, myp2p.eu where there is a list of channels where you can watch all different types of sports, news and entertainment channels.
My main reason for writing this is that if there was only one type of package that is in Windows, then there would be much easier tips to this because then everyone would concentrate on only one kind of package and then they would not later mess it up which is happening now with small, useful programs like Sopcast. 
[I]
I was not sure on where to post this. If it is needed to be moved, please do so.[/I]

---

### Post by xir_ on 2009-04-17
hey i feel you deb hunting pain, but there are multiple packaging options in windows exe self extracting rar, msi. Not to mention compiling from source is quite often done in windows.

Im not quite familiar with exactly what you are trying to achieve but ZOHO (i think), is a tv streaming app and i think has debs and may even be in the repositories. Maybe it will help?

---

### Post by 3rdalbum on 2009-04-17
You don't understand.

Windows only has to target one CPU architecture: x86.

Ubuntu supports a number of CPU architectures directly: Sparc, x86, x86_64, and ARM; and unofficially supports PPC, ia64 (Itanium) and probably a few others.

You can't run an x86-compiled program or an x86 Debian package on another CPU architecture - they don't understand eachother's instructions. In fact this is why 64-bit Windows is more problematic than 64-bit Linux. With Linux, you can just compile the source code of the program for 64-bit. With Windows, all developers have been making 32-bit only binaries and not distributing source code, so on 64-bit Windows you end off running mostly 32-bit programs that might not be fully safe for 64-bit operation.

So, Linux users need the source code. Besides which, it's an open-source operating system - if the source code wasn't available, it wouldn't be open-source!

As for the different package formats, that's more a case of social inertia. It's very easy to agree to adopt a single package format, but it's impossible to agree on which one to adopt. Many have tried, many have failed. Windows doesn't have a single package format. People speak of ".exe installers" but those are all binary installers that could come from a variety of different vendors, and work in different ways. There's nothing "standard" about them. The nearest thing on Linux is just what we call a binary installer, and that's got the problems I said above. Native packages (.deb, .rpm etc) can be converted amongst eachother so there's no problem for ISVs. You can use an RPM if nothing else can be found.

The solution as I see it is a universal compiler - a program that can easily compile any software (that is in compilable state) for your architecture, automatically resolve dependencies, and register the end result with the native package manager.

---

### Post by Johnsie on 2009-04-17
I'm pretty sure most of the people who broadcast to Sopcast aren't doing so legally... So I don't have much sympathy there. There are plenty of legal television watching applications for Linux that are easy to install.

---

### Post by ssdt on 2009-04-17
But I'm not sure if Zoho will play the tv that I want to play. Im trying to see cricket the sport if you know what I mean.

> **Johnsie said:**
> I'm pretty sure most of the people who broadcast to Sopcast aren't doing so legally... So I don't have much sympathy there. There are plenty of legal television watching applications for Linux that are easy to install.

Could you tell me if there is cricket in that. I didn't see any of them that has that.

---

### Post by Johnsie on 2009-04-17
You can watch cricket legally on satellite or cable. The people who are broadcasting on the Internet are doing so without permission from the ICB or the broadcasters who paid alot of money for broadcasting rights.

---

### Post by balaknair on 2009-04-17
> if there was only one type of package that is in Windows, then there would be much easier tips to this because then everyone would concentrate on only one kind of package and then they would not later mess it up

Windows 'exe' files cannot be used in Linux(except maybe through Wine). It's rather like suggesting that a diesel engine be able to run on petrol- won't happen, because the basic design is too different. Linux and Windows are two different OSes and are designed differently. A package compiled for Windows won't work in Linux(without an additional layer like Wine) and vice versa.
Besides, why would you want to expose Ubuntu to the thousands of malware written for Windows? Not to mention Microsoft's lawyers(remember the FAT LFN patent and TomTom). More trouble than it's worth.

As the Linux ecosystem grows, more and more applications will get ported to Linux, and as Ubuntu's marketshare increases, you will find deb files for more of the applications you want. 

If the program you want has rpm files available, you might be able to convert them with 'alien'. You can find instructions on how to do that here in the Ubuntuforums.
Installing from source- Go through the readme file for the tar.gz package carefully before attempting to compile. 'make, make install' does not apply for all tarball packages, some might use different steps. You will also have to get the dependencies for the program to work properly(again, read the readme file).

---

### Post by xir_ on 2009-04-17
> **ssdt said:**
> But I'm not sure if Zoho will play the tv that I want to play. Im trying to see cricket the sport if you know what I mean.



Could you tell me if there is cricket in that. I didn't see any of them that has that.

zoho support dozens of channels from different countries, but it would be illegal for them to broadcast pay to view programming. If its solely add supported its fair game. 

is it sky cricket you are trying to watch?

---

### Post by leandromartinez98 on 2009-04-17
Lets be realistic. The problem there, ssdt, is not the "type of file". Linux (and Ubuntu as well), is still a work in progress relative to Windows in terms of multimedia. There is a lot of people trying to work that things out so that you and many other people can have sopcast, webcams, skype, etc... working flawesly on Linux, but we are not there yet, although these things do work for a lot of people.

---

### Post by bapoumba on 2009-04-17
We do not support illegal activities on this forum. Closing the thread.

---

