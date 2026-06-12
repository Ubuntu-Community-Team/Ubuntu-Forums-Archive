---
title: "Migrate installed instance of Win XP to virtual machine"
date: 2010-11-05
forum: The Cafe
---

### Post by samalex on 2010-11-05
Hey Guys --

I just moved from Win XP to Win 7 at work, and given many of the apps I used under Win XP don't work all that well under Win 7 I started researching ways to image my Win XP system and run it virtually on Win 7.

Well after some trial and error I finally have my old instance of Win Xp that was installed on my workstation running virtually on VirtualBox, and it runs quite well.  I can't help but think something like this would be great for people looking to migrate from Windows XP or even 7 (should work the same there) to Linux in that they can still have their old PC to boot from anytime they need.  Granted some games and other graphic-intensive applications may not run stellar on a virtual machine, but how many times have you moved from one system to another and thought aftewords "Crap!  I forgot to copy/backup something".  And I guess this could work when upgrading from one instance of Ubuntu to another as well.  

I won't post the crazy details unless someone asks, but just wanted to note this is something that's possible.  

Sam

---

### Post by Schrute Farms on 2010-11-05
I, for one, would be interested in how you did it.  I dual boot XP/Lucid.  I have XP on a separate internal drive from Ubuntu.  I do have a fully updated XP virutualbox installation, but it would be cool to access my full original windows install without rebooting.  
As long as it didn't mess up the ability to actually boot into XP if need be.

---

### Post by sydbat on 2010-11-05
Yes, a straight forward How To would be nice!

---

### Post by CharlesA on 2010-11-05
Keep licensing issues in mind.

---

### Post by sydbat on 2010-11-05
> **CharlesA said:**
> Keep licensing issues in mind.Can you clarify? 

If I have an XP install on my box, and I can figure out how to run that install in a VirtualBox, how would that have any impact on "licensing"? I haven't installed it more than once, just accessing it in a different manner, right? Or am I mistaken?

---

### Post by CharlesA on 2010-11-05
> **sydbat said:**
> Can you clarify? 

If I have an XP install on my box, and I can figure out how to run that install in a VirtualBox, how would that have any impact on "licensing"? I haven't installed it more than once, just accessing it in a different manner, right? Or am I mistaken?

If it's an OEM copy I do not believe it is allowed to be run inside a VM.

That's what I have seen at least.

---

### Post by Schrute Farms on 2010-11-05
> **CharlesA said:**
> If it's an OEM copy I do not believe it is allowed to be run inside a VM.

That's what I have seen at least.

Ok, what if it's a store bought copy, or what if I have 2 store bought copies?

---

### Post by CharlesA on 2010-11-05
> **Schrute Farms said:**
> Ok, what if it's a store bought copy, or what if I have 2 store bought copies?

If they are retail copies, they can be installed on one machine (physical or virtual, I believe).

You'd have to read the EULA to be 100% sure tho.

---

### Post by earthpigg on 2010-11-05
> **CharlesA said:**
> If they are retail copies, they can be installed on one machine (physical or virtual, I believe).

You'd have to read the EULA to be 100% sure tho.

as you understand it:

he can still uninstall it on one, and then reinstall on another... right?

similar to what happens if he upgraded his motherboard. he would probably need to reinstall windows on the 'new' computer, but he wouldn't be breaking any laws.

---

### Post by Dr. C on 2010-11-06
> **CharlesA said:**
> If it's an OEM copy I do not believe it is allowed to be run inside a VM.

That's what I have seen at least.

I will preface this by the I am not a lawyer (IANAL) disclaimer. 

My understanding is that the Windows XP OEM versions can be installed on a virtual machine that is running on the OEM hardware. The XP EULA is silent on the subject of virtual machines. 

There is also a well established principle in contact law that when a contract is entered between two parties and one of the parties drafts the contract any ambiguities in the contract are resolved in favor of the party that did **not** draft the contact. This is especially true of a Microsoft EULA where any ambiguities would be resolved in favor of the user and not Microsoft. 

By the way later versions of Microsoft Windows such as Windows 7  explicitly allows the installation of the OEM copy in a virtual machine running on the OEM hardware, that would further serve to resolve any possible ambiguity in the XP case.

Here is a link to the Microsoft ELUAs. Very interesting reading: [Microsoft License Terms]("http://www.microsoft.com/About/Legal/EN/US/IntellectualProperty/UseTerms/Default.aspx")

---

### Post by HermanAB on 2010-11-06
Howdy,

VMware has a little tool for moving Windoze to a VM and back to physical HW.

BTW, the MS licences are mostly BS.  It depends on your state's Sale of Goods Act.  Every state/country has one and in most cases - everyone I looked at - the EULA is moot.

---

### Post by P4man on 2010-11-06
TO make a VM from an existing windows install for either Virtualbox or VMware have a look at this great little free tool:
[http://www.paragon-software.com/home/go-virtual/scenarios.html](http://www.paragon-software.com/home/go-virtual/scenarios.html)

---

### Post by CharlesA on 2010-11-06
> **HermanAB said:**
> 
BTW, the MS licences are mostly BS.  It depends on your state's Sale of Goods Act.  Every state/country has one and in most cases - everyone I looked at - the EULA is moot.

Agreed, but if you want to use their software you must abide by the licensing agreement, otherwise don't use the software.

It's a bit of a "grey-area" tbh.

---

### Post by HermanAB on 2010-11-06
It is not grey at all.

State law trumps contract law.
Federal law trumps state law.
The constitution trumps Federal law.

---

### Post by samalex on 2010-11-06
From a licensing standpoint I believe an OEM copy can only reside on the system it came on, but I don't know if it's addressed whether or not it matters if it's installed Virtually or not.  In my situation under our MSDN subscription there's no licensing problem in what I did, and for home users as long as they don't boot from their original drive for non-OEM copies of Windows I think it's legit.

But technically it was pretty simple.  Microsoft offers a tool called Disk2VHD - [http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx](http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx) - which lets you create a Micrsoft Virtual Hard Disk (VHD) image from a physical drive.  The theory is it could be booted from Microsoft VirtualPC, but due to VPC only being able to boot partitions at or less than 127 Gigs it's VERY limited since most modern computers have drives much bigger then this.  

For me I had two drives in my computer, so I swapped them making my bootable Win XP drive the secondary and my backup drive primary, then I installed Windows 7 (at work so Linux isn't an option).  Then I used the Disk2VHD tool to image my second drive into a VHD file.  From there I installed Oracle VirtualBox and setup a new Virtual Machine using the VHD file as the drive.  It picked it up and booted fine, though Windows took some time to find new drivers. 

Doing this is essentially like pulling a Windows drive from one system and booting it from another, and often times Windows can choke doing this, but I think VBox has generic enough drivers that at least Win XP was bootable.

The biggest caveat is if you were on a system with multiple processor support you'll need to change HAL in Windows to only utlize a single core -- unless you have a system robust enough to match the number of cores on the system the Windows image was created on.  In my case my Win XP system had 2 cores but I only wanted to use one core with VirtualBox.  windows though still was configured to use two cores, which isn't something that's easily changeable.

So if your VHD image boots to just a black screen go into the Virtual Machine settings and under System check 'Enable IO APIC' which should enable APIC support an allow the box to boot -- but it'll be WAY slow until you change HAL in Win XP to only use one processor.

When Windows comes up let it find whatever drivers it can and reboot, then check Device Manager and Computer to see if it's using a Multi Core APIC.  Here are some sites to give more info about this;
[http://support.microsoft.com/?scid=kb%3Ben-us%3B309283&x=10&y=9](http://support.microsoft.com/?scid=kb%3Ben-us%3B309283&x=10&y=9)
[http://tecbites.blogspot.com/2009/09/single-to-dualmulti-core-with-windows.html](http://tecbites.blogspot.com/2009/09/single-to-dualmulti-core-with-windows.html)
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

You can use Microsoft's Devcon utility - [http://support.microsoft.com/kb/311272](http://support.microsoft.com/kb/311272) - to change this, or hit Google and look or HALu.zip which is a frontend to devcon that'll look at your current HAL settings, just select APIC PC from HALu.exe.

Also before doing all this make sure and go into System Properties and uncheck the option to reboot on system failure.   After I got HAL reconfigured to use ACPI PC it gave a BSOD and just rebooted.  I had to boot into safe mode to disable the auto-restart which showed it was hosing on a specific Sys file, which i found this post on the VirtualBox - [http://www.virtualbox.org/ticket/420](http://www.virtualbox.org/ticket/420) - with info on fixing it (post by xok was fix for me).  

Also note after changing to ACIP PC support uncheck the 'Enable IO APIC' option in the Virtual Machine settings.

After all this and my network admin  got my new instance of Win Xp on the domain I was set -- I could boot into my old Win XP instance.

The purpose in posting all this is to show Windows users can migrate to Linux and still keep their current system virtually if need be.  Also though I used the Microsoft tool Disk2VHD you can also do this on Linux when upgrading from one Linux instance to another by using just dd and converting the raw image to something VirtualBox can use. 

Take care --

Sam

---

### Post by samalex on 2010-11-06
> **P4man said:**
> TO make a VM from an existing windows install for either Virtualbox or VMware have a look at this great little free tool:
[http://www.paragon-software.com/home/go-virtual/scenarios.html](http://www.paragon-software.com/home/go-virtual/scenarios.html)

I hadn't heard of this tool, but how ever you create the image Windows will probably still need HAL reconfigured.

---

### Post by juancarlospaco on 2010-11-06
Theres a P2V LiveCD, LiGNUx based...

---

### Post by P4man on 2010-11-06
> **samalex said:**
> I hadn't heard of this tool, but how ever you create the image Windows will probably still need HAL reconfigured.

Nope, it just works. Probably changes the registry settings for you. Havent tested with XP but it works in 7 which has the same issue as XP in that regard AFAIK.

---

### Post by earthpigg on 2010-11-07
> **HermanAB said:**
> It is not grey at all.

State law trumps contract law.
Federal law trumps state law.
The constitution trumps Federal law.

Don't signed and ratified international treaties fit in there between constitution and federal law?

State law trumps contract law.
Federal law trumps state law.
Ratified treaties trump federal law.
Constitution trumps treaties.

Nitpicky and slightly off topic, but it jumped out at me :P

---

### Post by Johnsie on 2010-11-08
People actually abide by Microsoft licensing??? I business yes, but in the real world no. Microsoft aren't going to chase after Joe Bloggs who used the same Windows cd on two different machines.

---

### Post by CharlesA on 2010-11-08
> **Johnsie said:**
> People actually abide by Microsoft licensing??? I business yes, but in the real world no. Microsoft aren't going to chase after Joe Bloggs who used the same Windows cd on two different machines.

Perhaps, but we do not condone piracy on these forums.

Microsoft's policy is one key per computer (outside of volume licenses) and if someone wants to reuse that key while the software is still on a machine, they are breaking the license agreement.

---

