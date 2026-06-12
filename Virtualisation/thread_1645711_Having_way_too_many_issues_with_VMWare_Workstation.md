---
title: "Having way too many issues with VMWare Workstation 7.1.3"
date: 2010-12-14
forum: Virtualisation
---

### Post by LinuxFingers on 2010-12-14
Hi all.  My name's Jenny and I'm new here, so I'm hoping to find some help, and hopefully some long-term people to talk with about Linux!  I just started using Ubuntu 10.10 yesterday, having switched from Mint 10.  I like it very much, however it does not like me.  At least not VMWare.  Every time, and literally *every* time, I install a Windows OS as a VM, it errors out.  I've tried CD/DVDs, USB, network...every thing I can think of.  Every OS BSODs within 5 minutes of installation.  I get the same message of *[I]irql_not*_less_or_equal.[/I]  It's highly frustrating.  I use it to do the labs for school, and I am taking SQL, Windows Server, User Support, and Win7 in a few weeks, and I really need this to cooperate.  I've tried installing Vista Business, Vista Ultimate, XP Professional SP3, XP Pro SP1, Windows 7 Pro x64, and even Win95 to just test!  Nothing ever worked.  I feel like I'm running out of options.  This is a fresh install, and I have only updated what Ubuntu has recommended.  The OSs I downloaded we all supplied by my school, and worked perfectly on Mint.  

Does anyone have an idea of what this could be?

---

### Post by Jense on 2010-12-15
I have no experience with running/installing Windows-Client on VM-Ware hosts. But I have made good experiences with VirtualBox for this purpose. It is also possible to convert VM-Ware Images for VirtualBox.

I don't know what you need this for. Though VM-Ware is more powerfull as far as I know, if all you need to do is running the occasional app that just needs some Win-version, VirtualBox works just fine.

---

### Post by stevebond001 on 2010-12-16
Not sure if this relevant but does your PC meet the minimum requirements for VMware?

Do you have the latest version of VMware?  Also, is it the correct version (32 bit / 64 bit)?

I am running VMware Workstation and player (7.1.2 build-301548 ) 64bit on Ubuntu 10.10 64 bit (fully updated) with absolutely no errors.  I have a mixture of MS and Linux based VMs running without issue.

I am being prompted by VMware to upgrade it to the latest version at the moment but haven't yet.  Maybe you could try installing a previous release of the product (these are available on the VMware website once you have logged in) to see if you get the same issue?  Failing that do you have another PC you can install onto?  Maybe VMware doesn't like a particular piece of hardware you have.

Have you tried installing a linux guest (looks like you have only tried MS O/Ses so far).  If you try it and it fails then there is something wrong with your VMware installation, rather than the O/S you're trying to install.

Another thing you could try is when installing an O/S let the VMware setup wizard detect the installation disk - it will then set the recommended configuration for that OS.

Hope the above provides you with some pointers - please let us know how you get on.

---

### Post by LinuxFingers on 2010-12-16
Hello.  Thank you both for your replies.  I do need VMWare, as it's required for my courses.

The VMWare is up to date, as well as Ubuntu.  Thing is, on the 64-bit version of Mint 10, it worked perfect.  However, on the 32-bit Ubuntu, it does not work at all.  My computer definitely meets the specifications, and I have used it with success on it before.  After I deleted the Mint and Windows partition, reformatted, and did a clean install with *just* Ubuntu 10.10 is when I started having problems.  I'm sorry I didn't get back to everyone sooner, but my laptop charger broke, and I had been offline for a while.  Just a string of bad luck with this thing!  When I get the charger in the mail (hopefully) today, I'll post a screenshot of what I'm talking about.  The UNIX and A+ instructors at my school had no idea about the errors either...  I wish I could just get it figured out.  :(

---

### Post by stevebond001 on 2010-12-17
Have you tried installing a Linux guest?  If so, does this fail as well as the MS installations.  If it does it would point to a faulty VMware install.

I don't know how much time you've invested in your PC build, but is it worth re-installing your host O/S again?  I this was my PC I'd definitely consider rebuilding from scratch.  In my opinion VMware is the best virtualisation software out there so I would say it's worth trying a rebuild once you've tested everything I mentioned in my previous post  

Hope this helps

---

### Post by newbeeman on 2010-12-17
You say it worked on a 64 bit Mint but not on a 32 bit Ubuntu?
Why not try a 64 bit Ubuntu? Might fix the problem from a different direction!

---

### Post by LinuxFingers on 2010-12-21
Newbeeman,

Your suggestion worked.  It's amazing how something like that can affect virtualization. I noticed in my BIOS that I don't have an option to turn virtualization on or off, so that may have been the reason why.  The system runs better with a 64-bit OS anyway.  So much for testing!  :P

Thanks everyone for your help.  It's been a long, frustrating few days working this out, but I'm all set now.  If it wasn't for everyone, I'd probably still be getting frustrated.   :)

---

