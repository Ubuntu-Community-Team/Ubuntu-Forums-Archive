---
title: "Basic Requirements"
date: 2021-03-02
forum: Virtualisation
---

### Post by daniell59 on 2021-03-02
I would like to set up a virtual machine. Once set up, I want to install Windows XP. Do I have enough resources?

OS Ubuntu 20.04 64
CPU Intel Duo CPU E8400 @ 3.00 GHz
RAM 4 GIG
Motherboard P5Q-Pro

Thanks in advance

---

### Post by mIk3_08 on 2021-03-02
You have just reach the minimum hardware requirements of OS Ubuntu 20.04. Yes! It will still work if vm alone will run in your machine. But if you will run another more applications aside from the vm running in your machine and running more application inside the vm with your xp system maybe it will shorten the amount of your ram and maybe will slowdown your system and maybe the GUI applications will cause you more freezing state.

---

### Post by TheFu on 2021-03-02
I ran 15 VMs on a Core2Duo E8400 for a few years.  That machine had 16G of RAM.

WinXP should run fine in 1G, so give it 1.5G.  The real difficulties will be in setting up the VM with supported virtual hardware since hardware commonly used today was not supported under WinXP without specific drivers.

Of course, you shouldn't enable any networking for the WinXP VM. Unsupported is still unsupported.

You didn't say which hypervisor you planned to use.  That would be important, since some hypervisors have much more overhead than others. Also, the commercial hypervisors have probably dropped all testing of WinXP, so they may not work with it at all.

When you say how much RAM will be used for the VM, be certain to always leave at least 1G of RAM for the hostOS.

---

### Post by daniell59 on 2021-03-02
> **TheFu said:**
> You didn't say which hypervisor you planned to use.  That would be important, since some hypervisors have much more overhead than others. Also, the commercial hypervisors have probably dropped all testing of WinXP, so they may not work with it at all.What would you suggest? After installing XP, I want to install an old copy of Quickbooks. Am I being unrealistic. 
Thanks for the input.

> When you say how much RAM will be used for the VM, be certain to always leave at least 1G of RAM for the hostOS.

---

### Post by DuckHook on 2021-03-02
> **daniell59 said:**
> What would you suggest?
I run XP on Virtualbox in an old laptop with total 4GB of RAM, so it is doable. Rather slow, so don't expect good performance, but it doesn't crash either, so it's workable, but not enjoyable.
> After installing XP, I want to install an old copy of Quickbooks. Am I being unrealistic.
It's realistic, but you can explore other options that will be much more rewarding. When I switched from Windows to Linux, I bit the bullet and switched my accounting software over too. There are a number of accounting packages that are native to Linux, but they tend to fall into one of two camps: Mickey Mouse consumer ones that are flat files (basically glorified spreadsheets) or enterprise level behemoths that are overkill. The one package that met my needs at the time was GnuCash. It is double entry, uses a lightweight database and is easy to install because it is available in the repos.

I went through the initial pain of temporarily keeping two sets of books (for safety), but only that first year. After that, I've never looked back.

I've been using it for almost a decade. It's a powerful little beast, conforms to GAAP, makes proper redundant database images, and has all of the functionality that I need. It's not as "pretty" as QuickBooks; frankly, looks rather ugly, but I don't care&#8230; it's an accounting package&#8230; I spend all of four hours in front of it every month.

The saving grace about accounting is that it's pretty much the same the world over. Such standardization makes every accounting package easy to pick up. I doubt you will find the learning curve very challenging.

If you are not married to QuickBooks, I would suggest installing GnuCash from the repos and taking it for a spin. It comes with a test database that you can play with. If converting, you will still need QuickBooks/XP for legacy reasons, but once converted, your new books will be on an up&#8209;to&#8209;date package, running on a secure OS that continues to be updated and you won't need to rely on the complexity of a VM (and everything that can go wrong with so many layers). Note that if you are running QuickBooks, it will be almost impossible for you to properly isolate XP by disabling the NIC as TheFu recommends, since you will need to print. My experience was that making the jump to a native Linux acct app was the right choice.

As an aside, I found it impossible to get QuickBooks to run on WINE. Accounting is not a function that can be left to anything less than Platinum level compatibility.

---

### Post by ajgreeny on 2021-03-02
As an alternative to Quickbooks you may also find that kmymoney is something that works well.

It's a KDE application, though that does not stop it running in Ubuntu, it just means it will pull in a lot of KDE/qt libraries when installed.
I use it on my Xubuntu 20.04 very successfully and in terms of its layout and looks it is more like Quicken/Quickbooks than gnucash so far as I can recall quicken.

Using gnucash was something that I never managed to get under my belt; I found the double entry system that was needed for every entry just too much hassle so gave up on that and tried kmymoney which I found much easier with no double entry requirements.
That may not be something that is a problem to you (I do not know quickbooks at all and perhaps ituses the double entry system so you're used to that?)

PS:
For a long time I ran XP in VBox with Xubuntu as my host, having 4G RAM, so it can certainly be done as long as Ubuntu does not use hugely more RAM than Xubuntu.  I gave XP 1.5G of RAM and it ran extremely well and probably still does though I haven't booted it for several months, having no need for it any more.

---

### Post by DuckHook on 2021-03-02
Hi ajgreeny! ):P

kMyMoney is a lot easier to use and, frankly, a lot easier on the eyes than GnuCash. People looking for an alternative to Quicken usually find apps like kMyMoney to be the way to go. But the problem with consumer level financial management apps is that they don't conform to GAAP, of which double entry is an absolute requirement, so they aren't true accounting apps. Don't know about the OP, but my accountants told me that if I didn't use some double entry system, their notice to reader in my annual reviews would have to say that my statements were basically unreliable—which defeats the whole point in an annual review, to say nothing of the statements themselves.

@daniel59

If you don't need to conform to GAAP, then are a lot more alternatives. But if you need to conform to GAAP, then be careful about consumer&#8209;level apps. I should note that there are a lot of cloud hosted browser&#8209;based accounting services these days that comply with GAAP. These are another alternative—if you are okay with your financials floating around out there in the ether. They swear up and down on a stack of holy books that they are fully encrypted, only you have the key, blah&#8209;blah&#8209;blah, but who really knows?

---

### Post by daniell59 on 2021-03-03
Thanks to all for your kind and informative replies. Soon I will try it and sees what happens. In the near future, I will be building a new machine.

---

### Post by ajgreeny on 2021-03-03
> **DuckHook said:**
> Hi ajgreeny! ):P

kMyMoney is a lot easier to use and, frankly, a lot easier on the eyes than GnuCash. People looking for an alternative to Quicken usually find apps like kMyMoney to be the way to go. But the problem with consumer level financial management apps is that they don't conform to GAAP, of which double entry is an absolute requirement, so they aren't true accounting apps. Don't know about the OP, but my accountants told me that if I didn't use some double entry system, their notice to reader in my annual reviews would have to say that my statements were basically unreliable—which defeats the whole point in an annual review, to say nothing of the statements themselves.
Thanks DuckHook.
As I said abpve gnucash and its double entry system was beyond both my needs and my wish, or ability, to understand.
Having now read more about the many finance applications available to us I had already come to the conclusion you mention before I read your post.

I probably should have persevered further with GnuCash but as I didn't need it I could not be bothered.
For personal finances I stand by my recommendation for kmymoney; it's slick, quick, and very detailed, offering all that most users need for their home use.

---

### Post by TheFu on 2021-03-03
I used Quickbooks for a few years for a few small LLCs and C-corp, mainly because that was what our contractor CPA/accountant used.  Hated it. It was overkill for moving money around between the companies and for the paychecks of 6 people.  We didn't sell anything retail, so many of the extra features Quickbooks provides wasn't useful to us (all the different tax collection rules by locality). I'm not the CFO of 2 companies anymore (and never should have been).

Switched to Quicken Home & Business which does some stock market stuff that none of the Linux alternatives above handle.  It was always fine for my LLC.  For a few years, had it working under WINE after much effort, then something changed and it broke. When that happened, I simply moved into a Windows VM and still use that today. Even if I have to pay for a Windows license to keep using it, I would. My sanity vs $100 ... I'll pay the $100 every time, but I'll not allow it to contact any Microsoft servers - ever. Firewalls are good at blocking all sorts of unnecessary things. I have a whitelist for allowed network access by that system. The VM is locked down for internet access only to retrieve stock data and allow "pull" backups. Nothing else.

For that VM, 
* 2 vCPUs (this choice was forced by Windows installing different kernels based on the number of CPUs).
* 1512M of vRAM
* 100G virtio storage (loaded the Redhat drivers; I should switch back to SCSI or SATA vDisks to avoid hassles)
* Display SPICE to access it w/ QXL video drivers (WinXP doesn't support this)
* GigE NIC - e1000 - is a Intel PRO/1000 NIC. I used virtio for years, but the hassles ended that.

It isn't WinXP.  WinXP doesn't support PRO/1000 NIC drivers without a separate, manual, install. I think those drivers have been removed from the internet. They certainly aren't easy to find from reputable sources and I'd rather not use drivers from random places for my financial software VM.  

When Intuit switched to an annual subscription, I stopped updating.  In reality, wish I'd done that when it was *Quicken for MS-DOS* which was always very fast.

The VM host system hardware is a Ryzen 2600 with an SSD. Last summer it was a Core i5-750 from 2010 on a 7200 rpm HDD which worked fine.  Both setups were/are very stable, so is the VM. It used to run 24/7 as an OTA TV recording system until about a year ago. Since then, all the media capabilities were removed. It is only used for Quicken a few times a month now.

The hypervisor I use is KVM with libvirt. Because I'm _in the business_, I've tried all the hypervisors over the decades.  For most people running a desktop on a desktop, virtualbox is the least bad of the bad choices. KVM and libvirt is usually just a little too complex for normal users to figure out.  KVM is what Amazon and probably 90% of all cloud VPS providers use.  The rest of them split between Xen, MS-Hyper-V, and VMware ESXi.  None of those are easier than KVM and none are lighter/faster in my testing.  

Gnome-Boxes might be easy enough. It is based on KVM, but I've not touched it.  Virtualbox has a large following, so getting help for it will be the easiest, probably. Even with the limitations vbox has.

---

### Post by DuckHook on 2021-03-03
> **ajgreeny said:**
> For personal finances I stand by my recommendation for kmymoney; it's slick, quick, and very detailed, offering all that most users need for their home use.
> **TheFu said:**
> Hated it. It was overkill for moving money around between the companies and for the paychecks of 6 people.  We didn't sell anything retail, so many of the extra features Quickbooks provides wasn't useful to us (all the different tax collection rules by locality).
…Switched to Quicken Home & Business which does some stock market stuff that none of the Linux alternatives above handle.  It was always fine for my LLC.
I agree with all of the above. If you don't need to conform to GAAP, then neither QuickBooks nor GnuCash are necessary. I would definitely not recommend either for consumer use. They are both overkill. I only raised it because the OP stated he was using QuickBooks (instead of Quicken). Such use implies a need for GAAP, hence the Linux equivalent had to be beefier (and fussier).

Candid admission: at the risk of offending the accountants on this forum—I HATE accounting. Absolutely loathe it. I admire those who do it well, but it's just not my thing. I spend the bare minimal amount of time doing it that I can get away with and would drop GnuCash in a heartbeat if I didn't need double entry. So, ajgreeny, I'm glad you have no need to persevere with it. It means you have better and nicer things to do with your time.

<sigh> Sometimes, I think "accounting" needs to be added to that old adage about death and taxes.

---

### Post by ajgreeny on 2021-03-03
> **DuckHook said:**
> Candid admission: at the risk of offending the accountants on this forum—I HATE accounting. Absolutely loathe it. I admire those who do it well, but it's just not my thing. I spend the bare minimal amount of time doing it that I can get away with and would drop GnuCash in a heartbeat if I didn't need double entry. So, ajgreeny, I'm glad you have no need to persevere with it. It means you have better and nicer things to do with your time.

<sigh> Sometimes, I think "accounting" needs to be added to that old adage about death and taxes.
I agree totally; it must be something devised by accountants to make sure they are  more fully employed; as I say, it completely baffled me even after looking through the examples I found online.
In the days when I needed to declare income for UK taxes, having been self-employed in a very small, sole trader manner, I did everything online using the software provided by HMRC (Her Majesty's Revenue & Customs) which required only simple balance sheet accounting easily done with kmymoney or even with a simple spreadsheet.

As I now have more time (thanks Covid-19!) I might even have another look at GnuCash to see if it now makes more sense to me than it used to.

---

### Post by DuckHook on 2021-03-03
> **ajgreeny said:**
> …I might even have another look at GnuCash to see if it now makes more sense to me than it used to.
:shock:

Why on *earth* would you want to do that if you don't have to?

Well, I suppose it's a bit like…  ](*,)  ….feels so good when you stop. :-P

---

### Post by ajgreeny on 2021-03-03
> **DuckHook said:**
> :shock:

Why on *earth* would you want to do that if you don't have to?

Well, I suppose it's a bit like…  ](*,)  ….feels so good when you stop. :-P
:lolflag:
Yes, I think you're probably correct.
However, I have just installed it and tomorrow might see if I can make sense of it.

Watch this space!

---

### Post by daniell59 on 2021-03-04
I just realized something. I have an even older computer that has 2 x 2GIGs of DDR2 memory. probably at a slower speed. My motherboard has room for 2 more modules. Would this help make virtualisation more practical? Would mixing memory modules be OK? This would make it two pairs.

Thanks

---

### Post by TheFu on 2021-03-04
I don't know what you mean by "mixing memory modules." 

No way to know until you try.  

You can't mix DDR3 and DDR2. They don't work that way.  Mixing speeds of some RAM won't work. I vaguely remember DDR2 being very picky. Some systems wouldn't boot with mixed RAM.  With DDR3, they seem to boot, but used the slowest speed.  With DDR4, the motherboards perform some sort of test and if the RAM won't boot at the requested speed, mine drops back to the slowest speed possible.

Some workloads are very CPU or RAM specific. It isn't always clear which is which until you try. In general, virtualization likes having more RAM available. 4G really should be fine for 1 VM, running WindowsXP.  I've run KVM VMs on a 2GB Chromebook before. It was tight and I felt it, but it wasn't THAT bad. 4G was roomy enough.  6G and 1-2 other VMs were fine.  8G and I've had 4+ VMs running Ubuntu Server for months.  16G and let's load up plenty of Linux servers and 1 Windows VM.

---

### Post by daniell59 on 2021-03-04
> **TheFu said:**
> I don't know what you mean by "mixing memory modules." 

No way to know until you try.  

You can't mix DDR3 and DDR2. They don't work that way.  Mixing speeds of some RAM won't work. I vaguely remember DDR2 being very picky. Some systems wouldn't boot with mixed RAM.  With DDR3, they seem to boot, but used the slowest speed.  With DDR4, the motherboards perform some sort of test and if the RAM won't boot at the requested speed, mine drops back to the slowest speed possible.

Some workloads are very CPU or RAM specific. It isn't always clear which is which until you try. In general, virtualization like having more RAM available. 4G really should be fine for 1 VM, running WindowsXP.  I've run KVM VMs on a 2GB Chromebook before. It was tight and I felt it, but it wasn't THAT bad. 4G was roomy enough.  6G and 1-2 other VMs were find.  8G and I've had 4+ VMs running Ubuntu Server fine for months.  16G and let's load up plenty of Linux servers and 1 Windows VM.

I should have been more clear. I now have 2 pair. One pair has a speed of 800 the other less. They are both DDR2

---

### Post by SeijiSensei on 2021-03-04
If you give WinXP 1.5 G and leave the rest for the Ubuntu host you should have no problems running on the first machine you mentioned.

---

### Post by deadflowr on 2021-03-04
> **daniell59 said:**
> I should have been more clear. I now have 2 pair. One pair has a speed of 800 the other less. They are both DDR2

Your using the less.
Memory runs at the slowest modules speed.

---

### Post by daniell59 on 2021-03-04
I just thought of something. My current memory had to be set manually because the motherboard was unable to do it automatically. The extra memory is generic without any indications of its numbers. I don't know how to deal with it in the BIOS.

---

### Post by rsteinmetz70112 on 2021-03-04
Is the computer seeing the new ram? 
If so and it's working you may not need to do anything else.

---

### Post by daniell59 on 2021-03-05
I installed the two RAM modules. Booted up and something strange happened. I was only able to get to the to initial Ubuntu welcome. I could not even get to the password signup. I took it out and now it is as it was.

---

### Post by DuckHook on 2021-03-05
Not a good idea to mix speeds. Some MOBOs can handle it awkwardly; others go on strike. What's really frustrating are the oddities and subtle misbehaviours that plague you afterwards. It's actually better to experience what you have: a system that at least forthrightly refuses to work. It's more damaging to be misled by a semblance of operability only to experience odd app breakages later on.

---

### Post by lammert-nijhof on 2021-03-08
I use a Windows XP Virtualbox VM since 1-1-11. In 2011 I installed it on a Pentium 4 HT with 1.5GB DDR. My host OS was Ubuntu 10.04 LTS :) Probably both OSes did run in approx. 512MB each.

Running a modern version of Windows in a VM in Ubuntu 20.04 with in total 4 GB is difficult. I got Windows Vista installed on a first gen i5 laptop with 4 GB, but basically it is unworkable. I assigned 2 GB to Vista, but with XP using 1GB it will work. If you use Virtualbox, it will come with the drivers for XP. 

I'm not aware of any limitation that Virtualbox has and I use both Virtualbox and KVM. Virtualbox is more user friendly and more reliable. KVM disk IO was faster, so it booted faster too.

---

