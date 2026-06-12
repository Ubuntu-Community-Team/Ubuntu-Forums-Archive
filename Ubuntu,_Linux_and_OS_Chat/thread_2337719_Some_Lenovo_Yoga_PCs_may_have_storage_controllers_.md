---
title: "Some Lenovo Yoga PCs may have storage controllers unsupported by Linux"
date: 2016-09-21
forum: Ubuntu, Linux and OS Chat
---

### Post by baronhk on 2016-09-21
I got a reply from Lenovo on my Best Buy review about why the BIOS on my Yoga 900 ISK2 UltraBook has been set to stop people from using Linux.

---
Lenovo Product Expert
September 20, 2016
This system has a Signature Edition of Windows 10 Home installed. It is locked per our agreement with Microsoft.
---

This is related to the discussion going on Lenovo's forum's about why the SSD is locked in a proprietary RAID mode that Linux doesn't understand.

[https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206)

I've attached a screenshot of my review and Lenovo's reply.

[http://imgur.com/a/niewu](http://imgur.com/a/niewu)

So they admitted that this is now a requirement for Signature PCs. 

So be warned that if you buy a "Microsoft Signature PC", it may not be allowed to run Linux, per Microsoft.

The Yoga 900 ISK2 at Best Buy is not labeled as a Signature Edition PC, but apparently it is one, and Lenovo's agreement with Microsoft includes making sure Linux can't be installed.

---

### Post by him610 on 2016-09-21
Not sure if this is where this should be posted.

I came across these two articles at Slashdot.org
[https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports?sdsrc=rel]("https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports?sdsrc=rel")

[https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs]("https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs")

Should unsuspecting buyers be warned before purchasing *Lenovo Yoga 900 ISK2 UltraBook*?

---

### Post by vasa1 on 2016-09-21
[http://www.theregister.co.uk/2016/09/21/lenovo_denies_plot_with_microsoft_to_block_linux_installs/](http://www.theregister.co.uk/2016/09/21/lenovo_denies_plot_with_microsoft_to_block_linux_installs/)> 

"Unsupported models will rely on Linux operating system vendors releasing new kernel and drivers to support features such as RAID on SSD," he added. "Unfortunately, I cannot confirm our relationship to the person at Best Buy."

Basically, if you want to install Linux, you need a kernel with the required SSD driver.

And this is what one of the Linux kernel authorities is [reported to have said]("http://www.cio.com/article/3122945/linux/no-microsoft-is-not-locking-users-out-of-lenovo-laptops.html"):> We reached out to Greg Kroah-Hartman, one of the leading kernel developers, and he said, “We support more raid controllers than any other operating system, and we support software raid as well (recommended over hardware raid as it doesn't lock you into any one host controller vendor.)”

Commenting on the whole saga, Kroah-Hartman said “It's just a ‘look, another odd storage controller that Linux might not support, but no one really knows as they don't have the hardware to test it with…’ issue." 

---

### Post by 6975 on 2016-09-24
So is this the thread source of the rumor before spread it wildfire became an article many sites & facebook?

---

### Post by speedwell68 on 2016-09-27
I have seen all the fuss about this on Google+.  Is it any surprise that a Microsoft branded product will only support a Microsoft branded OS?

---

### Post by mörgæs on 2016-09-27
It is indeed surprising. 

When a company has a near-total monopoly normal legislation would prevent it from advancing their monopoly even further. In most other kinds of business this would have been brought to court. Remember that Microsoft has been suing Google for abusing their search engine dominance.

---

### Post by mastablasta on 2016-09-27
on the other hand it seems this is the same as for all new hardware with proprietary drivers. at first it only supports MS (or Apple), Linux support is provided (if ever) only a few months (if not a year) afterwards.

---

### Post by speedwell68 on 2016-09-27
> **mörgæs said:**
> It is indeed surprising. 

When a company has a near-total monopoly normal legislation would prevent it from advancing their monopoly even further. In most other kinds of business this would have been brought to court. Remember that Microsoft has been suing Google for abusing their search engine dominance.

I don't really see how this is advancing Microsoft's monopoly.

---

### Post by Halbarad on 2016-10-02
> I don't really see how this is advancing Microsoft's monopoly.

Maybe in this way: that people cannot install Linux on certain machines? I carefully check in advance before buying a new machine. However, it is no longer a matter of a Bluetooth not working -- and the worst thing is that practically nobody cares about that any more.

---

### Post by RichardET on 2016-10-02
> **mörgæs said:**
> It is indeed surprising. 

When a company has a near-total monopoly normal legislation would prevent it from advancing their monopoly even further. In most other kinds of business this would have been brought to court. Remember that Microsoft has been suing Google for abusing their search engine dominance.


There are hardware options out there - Dell equipment usually runs fine with Ubuntu.  I suggest that people use common sense when making computer purchases, if their real plan is to run it with Linux and not its Windows branded default OS.

---

### Post by farrinux on 2016-10-02
The big questions come when the SSD needs replaced. From whom are you going to have to get it?  Locked into a specific manufacturer, type or brand?  While I would recommend that you always plan your hardware purchase. This type of tactic if true steps on the very fabric of freedom.  You purchase a computer (not a license to use it mind you.) you should be  able to put any OS on you want. So long as it is legal.  The other thing is that if and that's a big if, this is going on then it needs to be communicated to the purchaser.  It really smacks of consumer fraud.  It's like buying a car and later on you are required to buy everything, oil, gas, tires, etc from the dealer or manufacturer.

---

### Post by mc4man on 2016-10-02
This thread was a mistake/misinterpretation & of no value. Should be closed.

---

### Post by jeremy31 on 2016-10-02
> **mc4man said:**
> This thread was a mistake/misinterpretation & of no value. Should be closed.
If you really think that, press the report post button

---

### Post by speedwell68 on 2016-10-03
I still don't see what the fuss is all about.  If you don't want to run Windows don't buy one of these, simple.  There is such a big choice of compatible hardware available, from a huge number of suppliers, why is this even an issue.

---

### Post by mastablasta on 2016-10-03
> **speedwell68 said:**
> I still don't see what the fuss is all about.  If you don't want to run Windows don't buy one of these, simple.  There is such a big choice of compatible hardware available, from a huge number of suppliers, why is this even an issue.


because their actuons are not according to PC standards.
because MS was exposed (or so it was thought) as abusing it's near monopoly in desktop computer market.
because if this was true it could mean the distruction of competition. - say it suddenly appeared on all motherboards as it would be required for manufacturer to support such windows only feature.

---

### Post by farrinux on 2016-10-04
> **speedwell68 said:**
> I still don't see what the fuss is all about.  If you don't want to run Windows don't buy one of these, simple.  There is such a big choice of compatible hardware available, from a huge number of suppliers, why is this even an issue.

It's not so hard to see.  You go buy a new laptop say dell.  "Always worked with linux in the past!" You take it home decide to through some linux on it and presto it will not install.  Has it sit's now the manufacturers are not telling "joe customer" that this is going on. Now there maybe a ton of hardware available, but the question is how much you can afford to buy until you find one that works.  Guaranteed at least here in the states that you the consumer would be stuck with what ever piece or piece's of hardware you bought period.  Did you buy a windows machine? Does it run and work? If so you bought it.

---

### Post by speedwell68 on 2016-10-05
> **mastablasta said:**
> because their actuons are not according to PC standards.
because MS was exposed (or so it was thought) as abusing it's near monopoly in desktop computer market.
because if this was true it could mean the distruction of competition. - say it suddenly appeared on all motherboards as it would be required for manufacturer to support such windows only feature.

It is a Microsoft branded product, it only has to conform to their standards.  Much the same as with Apple with iPads or iPhones.  It hasn't and won't appear on all motherboards.

> **farrinux said:**
> It's not so hard to see.  You go buy a new laptop say dell.  "Always worked with linux in the past!" You take it home decide to through some linux on it and presto it will not install.  Has it sit's now the manufacturers are not telling "joe customer" that this is going on. Now there maybe a ton of hardware available, but the question is how much you can afford to buy until you find one that works.  Guaranteed at least here in the states that you the consumer would be stuck with what ever piece or piece's of hardware you bought period.  Did you buy a windows machine? Does it run and work? If so you bought it.

Again it is a Microsoft branded product, so to complain after the point would be silly.  As a Linux user I would steer clear of any Microsoft branded product as you are pretty certain they aren't going to work well with a Linux based OS.  If you buy a system with Windows and you decline the Microsoft EULA you will be able to return it as not fit for purpose, as I am prepared to say that the sales documentation does not confirm it works with Linux.

---

### Post by T2uiYKb7 on 2016-10-05
That makes me angry. (Microsoft locking computers to Windows.)

To be honest Google is doing something similar with Chromebooks, they won't release the source code for there drivers specifically so x86 **Chromebooks can't be used with Windows. **(Unless your OK with no sound, GPU acceleration etc.)

---

### Post by colmax on 2016-10-06
Appygeek showed/suggested Lenovo has introduced raid software that seems incompatible with linux
Also reported microsoft is also introducing software to ignore other bootloaders
Seems wrong since microsoft was bragging so much about building limited bash into win10
Cheers

---

### Post by buzzingrobot on 2016-10-06
> **mastablasta said:**
> because their actuons are not according to PC standards.


"PC standards" are whatever PC vendors decide they are. 

There's more profit in closed throw-away devices like phones and tablets than in PC's. Whatever Microsoft's faults, it's the continued presence of Windows that keeps the traditional PC hardware market alive. That (shrinking) market will continue to serve business and professional needs. The rest of us use our toys primarily for entertainment. (Netflix, Facebook, etc.) The days of  user-modifiable commodity PC boxes targeting consumers are numbered. The industry will replace traditional consumer desktop/laptops with locked-down devices with limited support cycles, just like phones and tablets.  Most of us will be quite happy with that as long as the screen is big enough to comfortably watch Game of Thrones.

---

### Post by colmax on 2016-10-06
Just wondering where democracy may play a part in os suppliers audacity
For an os to mess with my bios/efi (as win anniversary stopped f2 bios call on boot) is just wrong
Thinking maybe do a linux server install on my laptop cos i think it partitions auto
Uses the whole volume :)
Really like linux

---

### Post by colmax on 2016-10-06
Yeh it will be the internet of things where most devices will be sealed and aware (gps motion cam mic etc)
Smart tvs have apparently been sending data back to the manufacturers
Amazing world tho
Cheers

---

### Post by mastablasta on 2016-10-07
> **colmax said:**
> 
For an os to mess with my bios/efi (as win anniversary stopped f2 bios call on boot) is just wrong
and it all started with those silly signatures and MS claiming they won't mess with BIOS.

> 
Thinking maybe do a linux server install on my laptop cos i think it partitions auto


might not be a good idea. there are issues with server installer on UEFI. : [SIZE=2]https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1552365
[/SIZE]

---

### Post by colmax on 2016-10-07
Hey thanks Mastablasta
Maybe best i stick to desktop install
Cheers
ps. i found 1 of my posts was picked up by a site that firefox warned on (insecure & not built properly - whatever that means)
So i didn't go any further
Cheers again

---

### Post by kurt18947 on 2016-10-07
> **speedwell68 said:**
> It is a Microsoft branded product, it only has to conform to their standards.  Much the same as with Apple with iPads or iPhones.  It hasn't and won't appear on all motherboards.



Again it is a Microsoft branded product, so to complain after the point would be silly.  As a Linux user I would steer clear of any Microsoft branded product as you are pretty certain they aren't going to work well with a Linux based OS.  If you buy a system with Windows and you decline the Microsoft EULA you will be able to return it as not fit for purpose, as I am prepared to say that the sales documentation does not confirm it works with Linux.

Unless I'm misreading the original post, the device in question is a Lenovo product, not a Microsoft product e.g. Surface convertible/whatever it's called. Lenovo products, particularly the Thinkpad line are well known to be Linux friendly. So yeah, this could provide an unpleasant surprise to someone who relied on Lenovo's Linux friendly reputation when making a purchase.

---

### Post by macbreak on 2016-10-07
> **kurt18947 said:**
> Unless I'm misreading the original post, the device in question is a Lenovo product, not a Microsoft product e.g. Surface convertible/whatever it's called. Lenovo products, particularly the Thinkpad line are well known to be Linux friendly. So yeah, this could provide an unpleasant surprise to someone who relied on Lenovo's Linux friendly reputation when making a purchase.

Lenovo BIOSes have lots of nasty surprises in them, of late - ask Steve Gibson. (Twitter: @Sg_grc)

---

### Post by buzzingrobot on 2016-10-08
> **macbreak said:**
> Lenovo BIOSes have lots of nasty surprises in them, of late - ask Steve Gibson. (Twitter: @Sg_grc)

Yes, it's a Lenovo product.  Yes, Linux is installable.  The original reporting that prompted all this was inaccurate and then hyped by kneejerk Microsoft bashing.

The standard PC architecture, include the BIOS, was established about 30 years ago specifically to run Windows.  It's a market-determined standard.  It's pointless to get upset when a vendor changes something that inconveniences Linux.  Until something new replaces the entire PC hardware standard we've all been using for years and obsoletes every PC operating system, Linux will be responding to vendor hardware changes.

---

### Post by kurt18947 on 2016-10-08
> **buzzingrobot said:**
> Yes, it's a Lenovo product.  Yes, Linux is installable.  The original reporting that prompted all this was inaccurate and then hyped by kneejerk Microsoft bashing.

The standard PC architecture, include the BIOS, was established about 30 years ago specifically to run Windows.  It's a market-determined standard.  It's pointless to get upset when a vendor changes something that inconveniences Linux.  Until something new replaces the entire PC hardware standard we've all been using for years and obsoletes every PC operating system, Linux will be responding to vendor hardware changes.

But hardware vendors often dance to Microsoft's tune - see Secure Boot. Secure boot in itself is not a bad thing as long as it can be disabled. Windows 8.x machines require the ability to disable Secure Boot. Windows 10 machines don't.

---

### Post by kurt18947 on 2016-10-08
> **macbreak said:**
> Lenovo BIOSes have lots of nasty surprises in them, of late - ask Steve Gibson. (Twitter: @Sg_grc)

I've read that elsewhere as well. Build quality of the Thinkpad line is declining, the Superfish(?) fiasco. I've recently purchased two refurbished Thinkpads but those might be my last if this trend continues.

---

### Post by buzzingrobot on 2016-10-08
> **kurt18947 said:**
> But hardware vendors often dance to Microsoft's tune...

That's essentially a condensed version of my comment.

Why would a hardware vendor deliberately make PC's that can't run Windows?  That's suicidal.  Vendors will have every reason to continue making PC's per Microsoft's wishes until something comes along to supplant not just Windows but the entire PC market. I think that will be an extension of the phone/tablet platform with more local storage and and separate, large, and attachable displays. Shuttleworth's notion of a phone that can be connected to a large display and keyboard and used like a PC will happen.  Probably won't be Ubuntu or any other Linux,  though.

(There was a short time at the beginning of the PC era when multiple not-necessarily-compatible vendor-specific PC's ran vendor-specific versions of DOS.  Was a real drag on the hardware and software market.)

 For example, right now I'm using an Intel NUC box, which is about 4 inches square and 1 and 1/2 inches tall. Inside is an i5 CPU, 16 gigs of RAM and 768gigs of fast SSD storage.  And it's mostly empty space inside the box. As temperature and energy management improves, that space won't be need for fan cooling.  If  I could buy a phone with those specs that I could slot into a large desktop display and use a keyboard and mouse to run apps equivalent to those I now use, I'd buy it today and not look back.

Microsoft knows this.  Apple certainly does. So does Google. They all know the PC platform as a consumer product will not last forever.

I could certainly be wrong. I often am wrong.  But it seems clear that phones and tablets currently deliver the computing tools most consumers use most of the time.

---

### Post by kurt18947 on 2016-10-08
I think you're right about some sort of convergence. I just hate to see Microsoft do to the hardware business what they've done to the OS/software business -- force subtle but effective incompatibilities to screw any possible competitors. Oh but it'll be all in the name of keeping us safe.

---

### Post by buzzingrobot on 2016-10-09
> **kurt18947 said:**
> I think you're right about some sort of convergence. I just hate to see Microsoft do to the hardware business what they've done to the OS/software business -- force subtle but effective incompatibilities to screw any possible competitors. Oh but it'll be all in the name of keeping us safe.

The changes are happening because hardware capabilities enable them, not because of anything Microsoft has done or will do, or, in fact, to any software changes at all.  We have phones and tablets only because hardware production capabilities allow them to be produced at marketable prices. They aren't using the PC architecture, which, in any case, is wedded to a single specific Intel CPU-based hardware design that dates to the 1980's. 

You don't need Intel chips or that 30-year-old architecture to run software. Phones and tablets don't use Intel chips.  Add a large display and a keyboard to one of those and you've delivered all the computing capability most people want.  As it is, many, many people will never buy another PC, or even buy one in the first place.

These changes threaten any vendor that's dependent on the Intel PC architecture, and that specifically means Microsoft. Microsoft has essentially abandoned phones and is still trying to contort Win10 to support both traditional desktops and tablets.

Microsoft's business practices are typical of any business with a dominant market position. Frankly, it's naive to think any business will not do what it thinks is in its best interests.  The consumer OS and software market will always be dominated by one or two hardware/software platforms and their vendors because consumers will not tolerate the confusion and cost of a wide mix of platforms.

---

### Post by macbreak on 2016-10-10
> **buzzingrobot said:**
> Yes, it's a Lenovo product.  Yes, Linux is installable.  The original reporting that prompted all this was inaccurate and then hyped by kneejerk Microsoft bashing.

The standard PC architecture, include the BIOS, was established about 30 years ago specifically to run Windows.  It's a market-determined standard.  It's pointless to get upset when a vendor changes something that inconveniences Linux.  Until something new replaces the entire PC hardware standard we've all been using for years and obsoletes every PC operating system, Linux will be responding to vendor hardware changes.

I think you'll find Steve Gibson to be one of the most well informed, ***excruciatingly ***accurate and intelligent security people on the face of the planet, a fact which can and will be backed up by any amount of people in the same business as him, and he also happens to be incredibly humble - if he had his facts wrong (sometimes he does) he will then come back a week or two later, apologise graciously and correct himself. Steve Gibson doesn't come across as one of the whimsical copy/paste "journalists" who simply jumps on a news story bandwagon and rides it, just because the rest of the silly "journalists" in the industry can't be bothered to invest time and energy into proper research (most are 20/30-something upstarts, with the only goal being getting a "story" published, regardless of credibility.)

Yes, we all make errors of judgement, but I have listened to "Security Now" most weeks for the last 2 years, and I've yet to get even the slightest notion of a feeling that Mr Gibson doesn't know his stuff - he VERY MUCH does.

---

### Post by mc4man on 2016-10-10
> **jeremy31 said:**
> If you really think that, press the report post button

done

---

### Post by wildmanne39 on 2016-10-10
The title has been changed to reflect that this is an issue right now with a certain kind of lenovo computers so please stay on topic and remember this is not really a lot different from what has always been going on with vendors supporting the OS that keeps them in business and linux is always finding work arounds.

---

### Post by vasa1 on 2016-10-27
[Lenovo Issues Yoga Laptop BIOS Update To Fix Linux Woes]("https://phoronix.com/scan.php?page=news_item&px=Lenovo-Yoga-Linux-BIOS")

---

### Post by mörgæs on 2016-10-27
Good news :-) Thanks for posting.

It does help to raise media attention. Without people doing so this series of Yogas would have remained Windows-only.

---

