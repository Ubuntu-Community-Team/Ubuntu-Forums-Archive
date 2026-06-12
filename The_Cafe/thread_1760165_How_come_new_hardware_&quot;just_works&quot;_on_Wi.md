---
title: "How come new hardware &quot;just works&quot; on Windows but not ubuntu?"
date: 2011-05-16
forum: The Cafe
---

### Post by nrundy on 2011-05-16
let me use sandy bridge as an example. Win7 came out in 2009. ubuntu 10.04 came out in 2010. yet the sandy bridge processor from intel didn't work on 10.04 until the kernel was updated, but Win7 didn't need to update its kernel for Sandy bridge to work. or stated another way, sandy bridge just worked on 2009 Windows but not on 2010 ubuntu. how come?

---

### Post by Morbius1 on 2011-05-16
Well let's think about this situation for a minute. 

I'm Mr Intel and I've got a new product I want to roll out. I've tested it and ... oops ... Windows 7 won't run on it. Gosh, my product won't run on an operation system from a company that controls 90+% of the market! Back to the development lab it goes until it does run on Win7.

So now everything is good to go and one of the younger testers tests it on Linux and ... oops ... bummer. Ship it anyway, Earl.

---

### Post by el_koraco on 2011-05-16
cuz windows has better midgets

---

### Post by sjhstorm on 2011-05-16
Just might be that Intel shared their architecture with MS long before releasing sandy bridge and the Linux kernel maintainers had a later start, I just don't know. Mind you how come I have to install drivers on MS Vista for a Microsoft Lifecam but it just works on Linux!!

---

### Post by speedwell68 on 2011-05-16
What I'd like to know is why does XP, Vista and W7 not support my Microsoft Comfort Curve 2000 USB keyboard or my Microsoft wireless mouse without additional drivers, yet Ubuntu 10.04, 10.10 and 11.04 support it just by plugging it in?  Also why does my Hewlett Packard Photosmart Printer/Scanner require an 83mb download to work in XP & W7, as I have lost the disc, yet in Ubuntu I just plug it in and 30 seconds later I have a working printer and scanner?

---

### Post by Dustin2128 on 2011-05-16
> **speedwell68 said:**
> What I'd like to know is why does XP, Vista and W7 not support my Microsoft Comfort Curve 2000 USB keyboard or my Microsoft wireless mouse without additional drivers, yet Ubuntu 10.04, 10.10 and 11.04 support it just by plugging it in?  Also why does my Hewlett Packard Photosmart Printer/Scanner require an 83mb download to work in XP & W7, as I have lost the disc, yet in Ubuntu I just plug it in and 30 seconds later I have a working printer and scanner?
Thank you! Hardware support for me is much more plug & play in ubuntu than in windows.

---

### Post by aphatak on 2011-05-16
When new hardware is marketed, the maker wants to sell it.  One surefire way of selling it is to make sure Windows (which happens to have a very large share of the desktop market) has no problems with it.  If I were making such a device, the first thing I would do is get together with Microsoft, get all the specs I need to interface the hardware piece with Windows, then write (or pay someone to write) the device driver, test it will all versions of Windows in large-scale use, put the driver on a CD and include the CD in the hardware box.  If I had the muscle that Intel has, for example, I could get Microsoft to help me.  The market size makes it worth the trouble and expense for me.

The desktop market share of Linux being what it is, do you see any major hardware manufacturer taking this kind of trouble to make a Linux driver available?  The cost structure being what it is, I don't think so.  The only way Linux drivers are going to be available is when some Linux user (or a group of users) gets the hardware details from the manufacturer, and writes the device driver.  Again, they are not going to have the incentive - or the resources - to test the driver in a variety of hardware / software environments to make sure it will work whatever anyone cares to throw at it.  There is an exception, of course - if a manufacturer wants to, the company will publish a binary-only driver, but at a second priority.  Naturally.  They exist to make money, not to promote open-source software.  And I can't blame them - they have their stockholders to answer to.

If the hardware is truly ground-breaking, or if the manufacturer thinks there are some features competitors might copy, the manufacturer is going to be pretty leery about disclosing the details or putting them in the public domain for all (specifically folks who might write a Linux driver) to see.  The result is that Linux drivers are not going to be available - not unless the manufacturers themselves write one.  You can see it happening again and again - NVidia and ATI video cards are cases in point.

Ultimately it boils down to economics, and the fact that the consumer who uses the driver (in this case, Linux users) and the customer who pays for the driver development (in this case the manufacturer) are different economic entities.  They share some objectives but don't share all of them, so friction is inevitable.

You will see this friction whenever consumer and payer are different - exactly as it happens with auto insurance (the car owner wants repairs but the insurance company pays for them) and health insurance (the patient wants treatment but the health insurance provider pays for it).  I, for one, don't have a solution; I have merely decided to live with it!

All this said, I keep getting pleasantly surprised that by the time I have scraped together the money to buy hardware, a Linux driver is available nine times out of ten!

---

### Post by Joe of loath on 2011-05-16
For every piece of hardware that needs a driver disk, or a download from some dodgy website somewhere, there are half a dozen or so bits that 'just work' in Linux.

Installs are a lot more fun when you don't have to root around for scratched or, worse, lost driver disks.

---

### Post by NormanFLinux on 2011-05-16
Almost every new device is USB and runs according to a common input standard. So introducing new peripherals to Linux is greatly simplified today.

---

### Post by nrundy on 2011-05-16
So the bottom line is that Intel designed Sandy Bridge to work for Windows and didn't give Linux much thought. Or in other words, Windows "just works" with sandy bridge because Intel designed its product with this goal in mind.

BUT

if Intel wanted, they could have designed sandy bridge to "just work" with existing Linux kernels. They just didn't concern themselves with whether it "just worked" on Linux when they made the product. 

I understand this right?

---

### Post by gsmanners on 2011-05-16
The bottom line is that Microsoft probably drove a truckload of money to Intel's door and said you WILL design it with Windows 7 in mind (and if it doesn't work on Linux, that would be a nice plus).

---

### Post by murderslastcrow on 2011-05-16
Microsoft has been pretty rude to Intel in the past, if you read up on some computer history. But Intel's kinda' giving them the cold shoulder, lately. The issues with SandyBridge in particular have a different root than most 'just works' problems that are most common. Ubuntu is, of course, not on the bleeding edge so far as kernels go (after a few months out of an Ubuntu release, you'll be waiting three more months for a new kernel that just came out), but it is feasible to install newer kernel versions in Ubuntu through PPAs, as well.

Bottom line is, if you're out to buy new hardware, you might as well buy one with official Linux support from a vendor that supports Linux. Just like how people don't buy Macs just to put Windows on them- although Linux is much more flexible than OS X or Windows in the hardware it supports, it's always best to aim a year back in time if you're not buying from a Linux vendor, just to be safe.

---

### Post by d3v1150m471c on 2011-05-16
> **speedwell68 said:**
> What I'd like to know is why does XP, Vista and W7 not support my Microsoft Comfort Curve 2000 USB keyboard or my Microsoft wireless mouse without additional drivers, yet Ubuntu 10.04, 10.10 and 11.04 support it just by plugging it in?  Also why does my Hewlett Packard Photosmart Printer/Scanner require an 83mb download to work in XP & W7, as I have lost the disc, yet in Ubuntu I just plug it in and 30 seconds later I have a working printer and scanner?

lmmfao

---

### Post by 3Miro on 2011-05-16
What was it that didn't work on the Sandy Bridge? Was it something like the power savings, thermal sensors or it just didn't boot at all.

I know on Phenom II X6, the Linux kernel had a small issue with the driver for turbo mode (i.e. disable three of the cores and let the other three work on higher frequency). Was it something like that?

---

### Post by murderslastcrow on 2011-05-16
[Some details on what went wrong with Sandybridge]("http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1"). The issues are still being sorted out a bit, but Intel is dedicated to the open source community and contributes in many ways. This is very much a corner case for them, and usually hardware support comes down to a closed graphics driver for today's Linux users, and some extra features that aren't supported by a closed driver and will take a couple years to come to the open drivers.

Graphics drivers really are the final frontier for out-of-the-box stuff to work gracefully on every Linux system and for us to stop worrying so much about providing 2D fallbacks (there are software-based 3D shaders in the works, too, so that even non-accelerated cards can support Kwin/Clutter/Compiz to a poor extent until better drivers are available).

In general, stick to Intel graphics beyond 2005 if you want a decent, supported experience. Always do a little research before assuming stuff will work, even if it's pretty easy to count on it working these days.

---

### Post by JustinR on 2011-05-16
I've rarely had hardware "just work" Windows, especially things like printers and other things. Ubuntu has been more successfull for me.

---

### Post by 3Miro on 2011-05-16
> **murderslastcrow said:**
> [Some details on what went wrong with Sandybridge]("http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1"). The issues are still being sorted out a bit, but Intel is dedicated to the open source community and contributes in many ways. This is very much a corner case for them, and usually hardware support comes down to a closed graphics driver for today's Linux users, and some extra features that aren't supported by a closed driver and will take a couple years to come to the open drivers.

Graphics drivers really are the final frontier for out-of-the-box stuff to work gracefully on every Linux system and for us to stop worrying so much about providing 2D fallbacks (there are software-based 3D shaders in the works, too, so that even non-accelerated cards can support Kwin/Clutter/Compiz to a poor extent until better drivers are available).

In general, stick to Intel graphics beyond 2005 if you want a decent, supported experience. Always do a little research before assuming stuff will work, even if it's pretty easy to count on it working these days.

Oh, this is a graphics not a CPU issue. I was a bit confused.

Graphics manufacturers don't make drivers for Linux and usually don't give out specifications that the community would need to make drivers for Linux. Even if they do, they sure take their time. Overall Nvidia has the best proprietary drivers, Intel has the best Open ones and the AMD Open drivers are improving with tremendous speed. However, all companies are also guilty of neglect, Nvidia (Optimus), AMD/ATI (Evergreen support came months after the release), Intel (Sandy Bridge and what was the graphics issue on the Netbooks).

No company would neglect Windows as it is their primary target.

---

### Post by timZZ on 2011-05-16
Because Microsoft pays for the privileges and exclusivity to use state of the art technology where Linux needs to wait or create alternatives.

---

### Post by weasel fierce on 2011-05-16
If its any consolation, I've had a windows XP install fail to recognize that wired internet was available and the ethernet cable was plugged in

---

### Post by IWantFroyo on 2011-05-16
I'd bet that it isn't that easy with pre-installed Windows (on those computers with the green, yellow, red and blue stickers). They probably have to mess around with Windows for a while before it works, and then just back it up and install it on all the computers being produced. I could be wrong, though.

As for desktops and boxed Windows, I'm pretty sure manufacturers usually try to use "Windows-approved" hardware in the desktops.

---

### Post by Bandit on 2011-05-16
> How come new hardware "just works" on Windows but not ubuntu?
Other then the Sandy Bridge processor you mentioned. Honestly I see more hardware working out of the box on linux more then windows. But guess thats me.

---

### Post by themarker0 on 2011-05-16
lol. I bet it was just the kernal guys taking their time, as they always do. Linux wouldn't be stable if they rushed out the patches that fast. You do know that Intel has Kernal workers, right?

---

### Post by 3rdalbum on 2011-05-16
My understanding is that the CPU works fine on Linux, it's just that the driver that Intel supplies for the embedded GPU was a bit faulty.

The GPU wouldn't "just work" on Windows 7, a driver would need to be downloaded and installed.

---

### Post by murderslastcrow on 2011-05-16
[Intel's OSS site]("http://software.intel.com/sites/oss/"). A lot of relevant things have come straight from Intel over the years- they're one company that does right by their users, and recognizes the amount of open source users they have more than any other technology company out there (unless they're a Linux company, obviously). IBM might be another big contributor, as well, but probably less important to desktop-using consumers.

nVIDIA and ATi are awesome in that they support Linux in the first place, and update their offerings so often, but they have been known to be a little bit behind due to the way they're released and maintained (separately). They have their reasons to stay closed.

I don't really know of any big name devices that don't work with Linux at all. The iTouch devices and Broadcom adapters work well without installing drivers or doing weird stuff to the device itself. The only issues I've had are with very rare hardware, and even then there's usually a driver on the manufacturer's website you can install yourself. And if you take PowerPC, ARM, MIPS, and smartphone hardware into account, Linux itself supports an outrageous amount of hardware out of the box.

---

### Post by 3Miro on 2011-05-17
> **themarker0 said:**
> lol. I bet it was just the kernal guys taking their time, as they always do. Linux wouldn't be stable if they rushed out the patches that fast. You do know that Intel has Kernal workers, right?

There is the issue of lag in the kernel releases. If a new driver/patch is made for the kernel, then it doesn't become available right away. All distributions take their time to test something before they put it in their releases. This can cause some issues.

---

### Post by murderslastcrow on 2011-05-17
I've got to agree. Even Arch only includes stable packages, and for those with expected complications like the kernel, they usually keep it in testing for about a week before releasing it to core. Of course, every distribution has simple ways of installing the latest kernel, but I don't suspect that's part of this discussion.

---

