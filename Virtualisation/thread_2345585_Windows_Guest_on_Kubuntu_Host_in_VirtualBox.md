---
title: "Windows Guest on Kubuntu Host in VirtualBox"
date: 2016-12-05
forum: Virtualisation
---

### Post by oygle on 2016-12-05
Have been running Kubuntu on a laptop as the only OS. The laptop was pre-loaded with Windows 8, however as I had no use for Windows at all, I wiped it clean and put the Kubuntu on it.

Now I do have a need for Windows, just to download data from an inverter. They only supply the software in Windows.  :(

I didn't receive any media with the laptop, just Win 8 preloaded. So, I later purchased from Dell - "Windows 8.1 OEM - Deployment Solution Media Kit - OM Kit-DVD".

Do I use dual boot or VM, something like KVM ?

I have used dual boot before, seperate hard drives. From memory Windows insisted it be the primary OS (XP Pro) and I had Ubuntu as the OS on the secondary drive. This laptop only has one hard drive, and I want to keep Kubuntu as the primary OS. I have seen posts about the need to determine if it will be UEFI or not. Can I do the VM with a USB ?

---

### Post by DuckHook on 2016-12-05
A few thoughts:

If it were me, I would definitely VM. You state that you hardly ever use Windows. Therefore, it seems a complete waste of system resources and HDD space to dual boot. Moreover, this forum is filled with dual boot issues. It doesn't seem worthwhile wrestling with all those alligators to install an OS that you use very infrequently. Your intended use doesn't sound like a resource-heavy one. If you were gaming, I would say a VM won't cut the muster, but downloading data is not resource-intensive and should be fine in a VM. A big consideration is your HW. If it is relatively new and powerful, a VM works fine. If old or light-duty, then a VM may choke. Last but not least, a VM is extremely versatile. The ability to take snapshots and revert to known good snapshot is very useful, especially dealing with Windows.

---

### Post by QIII on 2016-12-05
If you are going to use virtualization, you can use the main drive for the Virtual Drive.  In most respects, it is just another file.

I would recommend against a dual boot at the moment for this reason:  The success rate of dual boot with Linux installed first is low.  It is usually best to install Windows first and Linux second.

If you are not worried about gaming graphics performance, a VM makes good sense for occasional use.

If you want easy setup and a free virtualization package, VirtualBox may be the ticket.

---

### Post by DuckHook on 2016-12-05
And as if you needed any further confirmation, QIII's advice and mine are practically identical...

Is it great minds thinking alike or partners in crime? :lolflag:

---

### Post by QIII on 2016-12-05
We should both be arrested!

:)

---

### Post by #&amp;thj^% on 2016-12-05
> **qiii said:**
> we should both be arrested!

:)
+100:p

---

### Post by Keith_Helms on 2016-12-05
Same situation for me.  I need Windows 7 to do a few minor things - run tax software once a year, download updates to my GPS, run some OCR software once in a while.  I also went with a VM.

One advantage not mentioned above is that a VM is much more portable.  You can easily copy it to a new computer and run it there.

---

### Post by vasa1 on 2016-12-06
> **oygle said:**
> ...
Do I use dual boot or VM, something like KVM ?
...
Why is KVM less popular?

---

### Post by oygle on 2016-12-06
> **DuckHook said:**
> 
If it were me, I would definitely VM. You state that you hardly ever use Windows. Therefore, it seems a complete waste of system resources and HDD space to dual boot. Moreover, this forum is filled with dual boot issues. It doesn't seem worthwhile wrestling with all those alligators to install an OS that you use very infrequently. Your intended use doesn't sound like a resource-heavy one.

Okay, thanks, so dual boot would be a waste of time. The software is not resource hungry at all, and as the inverter keeps data for 12 months, I really only need to dump the data to a laptop about every 11 months. That said, there have been issues lately where we need the data 'now'. Here is the software that just hooks up to a usb to dump the data - [SP LINK Software, now supporting AS4777.2:2015 ]("http://www.selectronic.com.au/sppro/splink.htm")

> **DuckHook said:**
> A big consideration is your HW. If it is relatively new and powerful, a VM works fine. If old or light-duty, then a VM may choke. Last but not least, a VM is extremely versatile. The ability to take snapshots and revert to known good snapshot is very useful, especially dealing with Windows.

Got the laptop about 12 months ago as new - 4th Generation Intel Core i5 cpu, 4 Gb ram, 1 Tb HDD, 2 Gb video card.

> **QIII said:**
> If you are going to use virtualization, you can use the main drive for the Virtual Drive.  In most respects, it is just another file.

So, is the VM basically a logical drive ?

> **QIII said:**
> 
I would recommend against a dual boot at the moment for this reason:  The success rate of dual boot with Linux installed first is low.  It is usually best to install Windows first and Linux second.

Okay, no dual boot then.  :)

> **QIII said:**
> If you are not worried about gaming graphics performance, a VM makes good sense for occasional use.

If you want easy setup and a free virtualization package, VirtualBox may be the ticket.

I don't use gaming. I can see a 64 bit package here for Ubuntu 16.04 - [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Thanks everyone.  :D

---

### Post by DuckHook on 2016-12-06
> **oygle said:**
> &#8230;there have been issues lately where we need the data 'now'.&#8230;hooks up to a usb to dump the dataA VM can be spun up in seconds. The only thing you may have to pay a bit of attention to is assigning the right USB port to your Windows virtual machine.> Got the laptop about 12 months ago as new - 4th Generation Intel Core i5 cpu, 4 Gb ram, 1 Tb HDD, 2 Gb video card.That's a powerful little beastie. Easily powerful enough to run a Windows VM.> So, is the VM basically a logical drive ?Not even that. It's basically an app. The app creates a little pretend-computer running within Ubuntu. You then install Windows into this little pretend-computer. Windows doesn't know any difference and thinks it's running in a real machine. The app is smart enough to map some physical functions (mouse, keyboard, NIC, designated USB port, etc) to Windows, so Windows thinks things are just peachy. Since the VM is really just an app, it resides on your HDD as just a big file&#8213;not even a logical drive.> I don't use gaming. I can see a 64 bit package here for Ubuntu 16.04 - [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)That's the link. Set it up as an additional repo/PPA as per the instructions in that wiki and you're good to go.

Post again if you run into any issues.

Good luck and Happy Ubuntuing.

---

### Post by oygle on 2016-12-07
Thanks for your explanations and tips on using VM.

> **DuckHook said:**
> Post again if you run into any issues.

The only thing I need to clarify now is whether I can legally use the Windows 8.1 in a VM environment. I now remember being informed in [this post]("https://ubuntuforums.org/showthread.php?t=2341803&p=13566480#post13566480") that "A copy of Windows sold with a computer is normally OEM licensed, and can't be used for virtualization without breach of contract".

I actually wiped the copy that came with the laptop, and later on purchased a DVD from Dell with Windows 8.1 OEM on it.

Would appreciate some clarification please.  :)

---

### Post by DuckHook on 2016-12-07
I'm afraid I'm of no help on that. Haven't used Windows since Vista came out.

I do know that every version of Windows has had different license terms and even different terms within the same version depending on the flavour. You will have to read the license on your copy. It should be readily available. One of the things that MS does very well is broadcast their license terms loudly and clearly. It could be on the MS site if nowhere else. Or ask Dell about their specific terms on their OEM licenses.

Unless a knowledgeable Windows user hops in here, I have no other info.

---

### Post by wildmanne39 on 2016-12-07
I believe that giving out legal advice is not within the scope of support we can provide here.

---

### Post by Keith_Helms on 2016-12-07
> **oygle said:**
> Thanks for your explanations and tips on using VM.



The only thing I need to clarify now is whether I can legally use the Windows 8.1 in a VM environment. I now remember being informed in [this post]("https://ubuntuforums.org/showthread.php?t=2341803&p=13566480#post13566480") that "A copy of Windows sold with a computer is normally OEM licensed, and can't be used for virtualization without breach of contract".

I actually wiped the copy that came with the laptop, and later on purchased a DVD from Dell with Windows 8.1 OEM on it.

Would appreciate some clarification please.  :)

You bought a copy of Windows and you can install that copy in whatever physical or virtual machine you want.  Where you might be crossing the line is if you installed it in a VM and then were to run multiple instances of that VM at once.  Giving copies of the VM to other people would definitely be a no-no.

---

### Post by oygle on 2016-12-07
> **DuckHook said:**
> One of the things that MS does very well is broadcast their license terms loudly and clearly. It could be on the MS site if nowhere else. Or ask Dell about their specific terms on their OEM licenses.

Thanks, I have dropped a post on a Dell forum, a Windows sub forum.

> **wildmanne39 said:**
> I believe that giving out legal advice is not within the scope of support we can provide here.

Yes, fair enough.  :)

> **Keith_Helms said:**
> You bought a copy of Windows and you can install that copy in whatever physical or virtual machine you want.  Where you might be crossing the line is if you installed it in a VM and then were to run multiple instances of that VM at once.  Giving copies of the VM to other people would definitely be a no-no.

Installing it on the laptop would definitely be the **ONLY** computer/VM that it will be installed on.

---

### Post by DuckHook on 2016-12-07
> **Keith_Helms said:**
> You bought a copy of Windows and you can install that copy in whatever physical or virtual machine you want.I'm not at all sure that this is correct. To my knowledge, there are licensing restrictions especially on OEM copies: that they can only be installed on bare metal, and further restrictions even then depending on version/flavour/vendor.> **wildmanne39 said:**
> I believe that giving out legal advice is not within the scope of support we can provide here.In the final analysis, this is the most accurate and wisest position we can permit ourselves.

---

### Post by oygle on 2016-12-07
> **DuckHook said:**
> In the final analysis, this is the most accurate and wisest position we can permit ourselves.

I like that reply.  :)

---

### Post by Keith_Helms on 2016-12-07
This is from Microsoft's website:

**Q.** Can I install OEM software on a virtual machine (VMware)?
 **A.**  You can install OEM software in a virtual environment as long as you  have a separate license for each instance of the software. It is fine to  use the OEM version as long as it is properly licensed. To be clear, a  separate version of the software must be installed for both the  &#8220;standard&#8221; and &#8220;virtual&#8221; installations.

[https://www.microsoft.com/OEM/en/Pages/support-faq.aspx](https://www.microsoft.com/OEM/en/Pages/support-faq.aspx)

There's also this page which says you need a full retail version starting with Windows 8.1:

[https://www.microsoft.com/OEM/en/licensing/sblicensing/Pages/windows-licensing-for-personal-use.aspx](https://www.microsoft.com/OEM/en/licensing/sblicensing/Pages/windows-licensing-for-personal-use.aspx)

So I guess it boils down to what exactly the software you bought from Dell is.  Will they sue you over something you paid them money for and are only using on a single system.  Not a chance.

---

### Post by oygle on 2016-12-07
> **Keith_Helms said:**
> This is from Microsoft's website:

**Q.** Can I install OEM software on a virtual machine (VMware)?
 **A.**  You can install OEM software in a virtual environment as long as you  have a separate license for each instance of the software. It is fine to  use the OEM version as long as it is properly licensed. To be clear, a  separate version of the software must be installed for both the  “standard” and “virtual” installations.

[https://www.microsoft.com/OEM/en/Pages/support-faq.aspx](https://www.microsoft.com/OEM/en/Pages/support-faq.aspx)

Great, thank you for finding that. As I would only be using **_one_** Windows 8.1 in this scenario, then I'm only required to have a lisense for that.

> **Keith_Helms said:**
> 
There's also this page which says you need a full retail version starting with Windows 8.1:

[https://www.microsoft.com/OEM/en/licensing/sblicensing/Pages/windows-licensing-for-personal-use.aspx](https://www.microsoft.com/OEM/en/licensing/sblicensing/Pages/windows-licensing-for-personal-use.aspx)

So I guess it boils down to what exactly the software you bought from Dell is.  Will they sue you over something you paid them money for and are only using on a single system.  Not a chance.

In Jan 2015, as I wanted to purchase Windows 8.1 media (Not OEM), I enquired about purchasing a '**FULL**' Windows 8.1. The reply from Dell support was "OEM, FULL and RETAIL are the same product". So that was the product I purchased.

---

### Post by oygle on 2016-12-07
I have been informed in a Microsoft forum that to use Windows 8.1 in a VM, I will need to add [Dell SLIC 3.0]("http://arstechnica.com/civis/viewtopic.php?p=26623195") to the laptop BIOS.

Does anyone know about this please ? I do feel that this is now at a stage where I can backup the laptop, and install the VM software. ( [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) )

---

### Post by 1clue on 2016-12-07
Speaking from prior experience (not in the last few years though) most OEM Windows installations won't work in a VM because they're keyed to a serial number on the motherboard. We ordered some OEM CDs awhile back, turned out there was a different Windows installer for every 50 machines. I've heard that some manufacturers have keyed to 20-machine batches.

That said, I have more recent (not Win10) experience using Microsoft-distributed Windows on VMs. Here's my advice:
[LIST=1]
[*]Don't use any image that doesn't come directly from Microsoft.
[*]Each image has several EULAs (end-user license agreements) which apply to that image.  They could be:
[LIST=1]
[*]education
[*]commercial
[*]developer
[*]testing
[*]enterprise
[*]personal
[*]this list changes constantly, you need to find out which ones exist and which most applies to your scenario.
[/LIST]

[*]Each EULA is designed for a different scenario. Some are more friendly for VMs than others.
[*]Call the 800 number on Microsoft's website and tell them exactly what your scenario is. They will tell you which of the current licenses makes most sense for you.
[*]The 800 number people can't sell you a license, but they can give you some names/websites where you can get a valid license.
[/LIST]

Another thing:  Don't be afraid of the guys on the 800 number. If you're calling that number they know you're trying to be legal. Tell them what you have in mind and they'll give advice as to the best fitting license, and answer questions about it. These guys know about KVM, QEMU, and every other virtualization/dual-boot scenario that you can think of. They know about testing scenarios where you may have an image that gets reset to a known starting point every time you use it. They know about scenarios where you need to reinstall over and over. They know about backing up an image. Be straight with them and you'll get good answers.


Finally, read the license agreement. It's not really that hard to understand.

---

### Post by DuckHook on 2016-12-08
Since this thread has morphed into a *Virtualisation* support issue, I have moved it into that subforum and changed the title to more accurately reflect the new topic.

---

### Post by oygle on 2016-12-08
> **1clue said:**
> Speaking from prior experience (not in the last few years though) most OEM Windows installations won't work in a VM because they're keyed to a serial number on the motherboard. We ordered some OEM CDs awhile back, turned out there was a different Windows installer for every 50 machines. I've heard that some manufacturers have keyed to 20-machine batches.


I have seen posts where the key is in the BIOS, and yet have seen posts where it is stated that the key is not in the BIOS ?  So, I'm not sure.

> **1clue said:**
> 
That said, I have more recent (not Win10) experience using Microsoft-distributed Windows on VMs. Here's my advice:
[LIST=1]
[*]Don't use any image that doesn't come directly from Microsoft.
[*]Each image has several EULAs (end-user license agreements) which apply to that image.  They could be:
[LIST=1]
[*]education
[*]commercial
[*]developer
[*]testing
[*]enterprise
[*]personal
[*]this list changes constantly, you need to find out which ones exist and which most applies to your scenario.
[/LIST]


I have purchased the Windows 8.1 media CD. Dell have stated that the product I purchased is retail/full/OEM.

> **1clue said:**
> [list]
[*]Call the 800 number on Microsoft's website and tell them exactly what your scenario is. They will tell you which of the current licenses makes most sense for you.
[*]The 800 number people can't sell you a license, but they can give you some names/websites where you can get a valid license.
[/LIST]

Thanks, I will consider calling the number. It is overseas call and waiting, waiting in a queue, costs. However, the link shown in a previous posts, from the MS site, in reference to the use of VM's, has settled the matter. 

> **DuckHook said:**
> Since this thread has morphed into a *Virtualisation* support issue, I have moved it into that subforum and changed the title to more accurately reflect the new topic.

Thanks. I was actually going to start a new thread, and wondered if there was a 'Virtualisation' sub forum.  lol

---

### Post by oygle on 2016-12-08
Have installed the Oracle Virtual Box Version 5.1.10 r112026 (Qt5.5.1)

Followed the guide at [http://download.virtualbox.org/virtualbox/5.1.10/UserManual.pdf](http://download.virtualbox.org/virtualbox/5.1.10/UserManual.pdf) . Went through the instructions up to page 21. At 1.8.1 the guide mentions a “First Start Wizard”. This didn't appear. When I now 'Start' the VM, a msg "FATAL: No bootable medium found! System halted." (See VM_Page21.png )

I have rechecked that the DVD/CD is specified. The Windows 8.1 CD is in the drive, and I can browse it with Dolphin. The settings are all greyed out, except the main settings display.

---

### Post by oygle on 2016-12-08
Arrgh, I just saw a post about getting rid of the "saved state", tried that, and now the CD/DVD drive is active.  :)

So, it seems ok now.

Later: The Win 8.1 install wanted 10 Gb, and I only had 8 Gb setup, so it didn't proceed. This is despite the fact that I made the storage dynamic. Can't see how to change the VM storage from 8Gb to 10 Gb. Does this look safe - [https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks](https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks)

---

### Post by &amp;KyT$0P# on 2016-12-08
> **oygle said:**
> Can't see how to change the VM storage from 8Gb to 10 Gb. Does this look safe -
Why bother with all that for a blank virtual disk?  Just delete the storage medium and create a new, larger one.

---

### Post by 1clue on 2016-12-08
> **oygle said:**
> I have seen posts where the key is in the BIOS, and yet have seen posts where it is stated that the key is not in the BIOS ?  So, I'm not sure.

Me either. I always thought it was burned into some ROM chip on the motherboard.

> 
I have purchased the Windows 8.1 media CD. Dell have stated that the product I purchased is retail/full/OEM.

Just to clarify, OEM Windows is generally held to be a Windows installation which has been modified by a hardware manufacturer (not Microsoft) and resold. In that case I believe that the licensing is through Dell, not through Microsoft. These OEM versions are not only often keyed to the hardware, but also full of random software that most people either don't use at all or won't use most of. My advice from the above post doesn't apply here.

> 
Thanks, I will consider calling the number. It is overseas call and waiting, waiting in a queue, costs. However, the link shown in a previous posts, from the MS site, in reference to the use of VM's, has settled the matter. 

Microsoft (or Dell in this case) should have a number in your country.

> 
Thanks. I was actually going to start a new thread, and wondered if there was a 'Virtualisation' sub forum.  lol

Yup. :)

---

### Post by oygle on 2016-12-08
> **halogen2 said:**
> Why bother with all that for a blank virtual disk?  Just delete the storage medium and create a new, larger one.

Yes, good point, thanks.

> **1clue said:**
> Just to clarify, OEM Windows is generally held to be a Windows installation which has been modified by a hardware manufacturer (not Microsoft) and resold. In that case I believe that the licensing is through Dell, not through Microsoft. These OEM versions are not only often keyed to the hardware, but also full of random software that most people either don't use at all or won't use most of. My advice from the above post doesn't apply here.


Okay, thanks for the clarification.  :)

---

### Post by oygle on 2016-12-08
I chatted to Microsoft today. In short, Microsoft have given me permission to install Windows 8.1 in the VM  :)

---

### Post by oygle on 2016-12-09
Thanks to everyone for all your help. Have to pinch myself that I actually have Windows 8.1 running as a guest.  :D

---

### Post by 1clue on 2016-12-09
There are a whole lot of businesses running windows of every variety on virtual machines. Many of them use QEMU and/or KVM, many use VirtualBox, whatever.  There are a lot of Enterprise-grade virtualization engines out there.

---

### Post by DuckHook on 2016-12-09
> **oygle said:**
> Thanks to everyone for all your help. Have to pinch myself that I actually have Windows 8.1 running as a guest.  :DVery happy that it worked out for you, oygle. You are now a virtual person and deserve a cookie! :KS

Please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

### Post by oygle on 2016-12-13
Now that the VM is setup, and I have Windows 8.1 running as a guest, there is a problem with sharing ? I have been following the instructions on sharing as per [http://download.virtualbox.org/virtualbox/5.1.10/UserManual.pdf](http://download.virtualbox.org/virtualbox/5.1.10/UserManual.pdf)

Have created a folder on the host, yet every time I attempt to add a 'shared folder' under the guest as 'Machine Folders', the share is added under 'Transient Folders'. That aside, I can't see the folder/files on the host, from within the guest ?

---

### Post by &amp;KyT$0P# on 2016-12-13
1) Shutdown the VM before adding/removing shared folders.

2) When setting up the shared folder, be sure to select the "Auto-mount" option.

---

### Post by oygle on 2016-12-13
> **halogen2 said:**
> 1) Shutdown the VM before adding/removing shared folders.

2) When setting up the shared folder, be sure to select the "Auto-mount" option.

Thanks. Do you mean shutdown the VM guest (Windows) ? I usually exit the guest which causes a small window to appear, and I select the default, to 'save'.

Regarding sharing - does anything need to be done on the host, like setup Samba, etc ? Or , additional on the guest, like a Windows share ?

---

### Post by &amp;KyT$0P# on 2016-12-13
> **oygle said:**
> Do you mean shutdown the VM guest (Windows) ? 
Yep.

> Regarding sharing - does anything need to be done on the host,
I don't think so.  If it still doesn't work even with the above advices, make sure your user account on the host is added to the [FONT=Courier New]vboxusers[/FONT] group.  Run [FONT=Courier New]id[/FONT] in a Terminal to check what groups you're in.

> Or , additional on the guest, 
You need to install VirtualBox Guest Additions.  Devices > Insert Guest Additions CD Image

---

### Post by oygle on 2016-12-16
> **halogen2 said:**
> If it still doesn't work even with the above advices, make sure your user account on the host is added to the [FONT=Courier New]vboxusers[/FONT] group.

Now that I have user management again (kuser), have added the group vboxusers

> **halogen2 said:**
> You need to install VirtualBox Guest Additions.  Devices > Insert Guest Additions CD Image

In synaptic package manager there is *virtualbox-guest-additions-iso* . When I selected 'Mark for installation' , synaptic gave a msg about removing the virtualbox-5.1 ; screen dump ...

[ATTACH=CONFIG]272727[/ATTACH]

---

### Post by oygle on 2016-12-16
Downloaded   this file - [http://download.virtualbox.org/virtualbox/5.1.10/VBoxGuestAdditions_5.1.10.iso](http://download.virtualbox.org/virtualbox/5.1.10/VBoxGuestAdditions_5.1.10.iso)

Then after a while the guest recognised the ISO and di theinstallation. Rebooted, etc, and I can now see the shared folder. :)

---

### Post by &amp;KyT$0P# on 2016-12-16
Glad you got it working, but, er, "Devices > Insert Guest Additions CD Image" is the faster way to do it.  Right above the running VM's display, you should see a menu bar.  "Devices" is one of the menus there, click it and you'll see that option on the bottom of the menu. :)

---

### Post by oygle on 2016-12-16
> **halogen2 said:**
> Glad you got it working, but, er, "Devices > Insert Guest Additions CD Image" is the faster way to do it.  Right above the running VM's display, you should see a menu bar.  "Devices" is one of the menus there, click it and you'll see that option on the bottom of the menu. :)

Yes, that is what eventually worked. Because of what synaptic was reporting, I downloaded the ISO, but found that it took Win quite a while to work out where the ISO was. Hmm, just remembered that the ISO isn't in that shared folder, but in a folder (supposedly) inaccessible to Windows. How did Windows access that when it is in a folder **NOT** shared ?

---

### Post by oygle on 2016-12-16
Just further on the sharing and trying to understand how Windows knows where the ISO is, and is able to access it. Screen dump of windows explorer ..

[ATTACH=CONFIG]272732[/ATTACH]

1. Drive C: is where Windows 8.1 is installed. It is reporting only 21 Mb free, and there was a warning msg about disk nearly full. I alloated 10 Gb for Windows as guest, but have the settings as dynamic though, so I assume there is no cause for alarm. Is that correct ?

2.  Drive D: is the file VBoxGuestAdditions_5.1.10.iso , which is on the Downloads folder. How can Windows access/view that when that folder is not shared ?

3.  Drive E: is the shared folder. That seems okay, yet Windows is able to determine the total drive space ?  Is that okay ?

---

### Post by &amp;KyT$0P# on 2016-12-16
1) "Dynamically allocated" only refers to the size of the .vdi file.  Not the virtual hard disk size, which is constant at 10 GB.  I'd say your lack of disk space in the guest could be cause for alarm.

2) That's because you inserted it in the VM's CD drive.

3) Yep, that's all normal.

---

### Post by oygle on 2016-12-16
> **halogen2 said:**
> 
1) "Dynamically allocated" only refers to the size of the .vdi file.  Not the virtual hard disk size, which is constant at 10 GB.  I'd say your lack of disk space in the guest could be cause for alarm.

Hmm, there as a link a few posts back of how to increase the size. Not going to just delete that file and make it bigger, as I'd have to reinstall Windows again.

> **halogen2 said:**
> 
2) That's because you inserted it in the VM's CD drive.


I don't use the CD drive. The ISO is on the hard drive.

> **halogen2 said:**
> 
3) Yep, that's all normal.


How is Windows able to determine how much of the HDD is used, and how big it is ?  My understanding is that Windows is not able to access *nix file systems, unless permissions are given.

---

### Post by ian-weisser on 2016-12-16
> **oygle said:**
> I don't use the CD drive. The ISO is on the hard drive.
halogen2 is correct. You pointed the VM to the ISO. It's a setting for a *virtual* CD drive.

> **oygle said:**
> How is Windows able to determine how much of the HDD is used, and how big it is ?
To the Guest OS, the VM Host pretends to be an ordinary, expected HDD, and responds like one. That's one reason VM hosts are big applications - they have lots of features like that.

---

### Post by &amp;KyT$0P# on 2016-12-16
> **oygle said:**
> Hmm, there as a link a few posts back of how to increase the size. Not going to just delete that file and make it bigger, as I'd have to reinstall Windows again.
Yep, follow those instructions this time.  But instead of using Gparted to resize the Windows partition, see if you can resize it from Windows.  I've heard it's safer that way, but I don't remember the reasoning.

> I don't use the CD drive. The ISO is on the hard drive.
The VM's CD drive is not your physical CD drive.  It can take an ISO image file just as well as your host's CD drive.

> My understanding is that Windows is not able to access *nix file systems, unless permissions are given.
And you **did** give permissions, by setting up the shared folder.  Nothing to be concerned about.

---

### Post by oygle on 2016-12-16
> **halogen2 said:**
> Yep, follow those instructions this time.  But instead of using Gparted to resize the Windows partition, see if you can resize it from Windows.  I've heard it's safer that way, but I don't remember the reasoning.

Thanks - I guess who can fathom these mysteries.  :)

> **halogen2 said:**
> 
The VM's CD drive is not your physical CD drive.  It can take an ISO image file just as well as your host's CD drive.


Yes, it's a logical drive. But the only sharing enabled was one folder, definitely not the 'Downloads' folder. I can view the ISO and all it's files/folders within Windows.

> **halogen2 said:**
> 
And you **did** give permissions, by setting up the shared folder.  Nothing to be concerned about.

Okay thanks. Something for me to be aware of. If I share evn just one folder on the host, Windows can see total size/used space.

---

### Post by &amp;KyT$0P# on 2016-12-18
> **oygle said:**
>  the only sharing enabled was one folder, definitely not the 'Downloads' folder. I can view the ISO and all it's files/folders within Windows.
That's not a share.  You literally inserted the ISO in the VM's virtual CD drive.

You've done the virtual equivalent of inserting a disk in your physical CD drive and forgetting to remove it.

---

### Post by oygle on 2016-12-23
> **halogen2 said:**
> That's not a share.  You literally inserted the ISO in the VM's virtual CD drive.

You've done the virtual equivalent of inserting a disk in your physical CD drive and forgetting to remove it.

Yes, I didn't realise the Guest Additions ISO was actually in a folder ..

[ATTACH=CONFIG]272818[/ATTACH]

---

