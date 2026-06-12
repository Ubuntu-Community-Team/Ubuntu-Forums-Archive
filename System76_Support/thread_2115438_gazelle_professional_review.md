---
title: "gazelle professional review"
date: 2013-02-12
forum: System76 Support
---

### Post by metalanguage on 2013-02-12
I received mine on January 4th 2013. Since then I've had 2 minor problems:

1. Being forced into ubuntu (I do not like the recent trend of preinstalled amazon ads). When you do a little research, you find that if you don't run this machine with a modern linux kernel, you might get system crashes. Ever since I've been running ubuntu 12.10, though, I have experienced no crashes.

2. When placed on a flat surface, the laptop is uneven. One leg appears to be too short. I bring a few flashcards around. Oh well.

I carry this laptop around in my backpack all the time as I walk and bike. I tend to treat it well. As of this point I don't have any big complaints. It was a well priced machine which serves me as a portable workstation/desktop.



I want to respond to this guy's review:
[http://ubuntuforums.org/showthread.php?t=1991799&highlight=system76+gazelle+professional+review](http://ubuntuforums.org/showthread.php?t=1991799&highlight=system76+gazelle+professional+review)

**Body:** You can see the design on their website. I've never been hurt by holding this computer.
**Screen:** I agree: the screen casing is a bit flimsy.
**Touchpad, Cooling:** I've never felt that any region of the computer has been too warm to the point that it has become uncomfortable. It is true that that region does get warmer than the rest of the computer though. You should know that 1) I don't use this computer for gaming and 2) the laptop maintains a steady temperature of ~55 degrees if you're not doing anything too intense. I mainly browse, read, and program.
**Ubuntu:** I also wish that I was given the option to partition the hard drive during the first system set up.

**The Bad:** It is true that the battery life is around 3 hours.

---

### Post by cariboo on 2013-02-12
> **metalanguage said:**
> I received mine on January 4th 2013. Since then I've had 2 minor problems:

1. Being forced into ubuntu (I do not like the recent trend of preinstalled amazon ads). When you do a little research, you find that if you don't run this machine with a modern linux kernel, you might get system crashes. Ever since I've been running ubuntu 12.10, though, I have experienced no crashes.



With about 2 minutes of searching, you can find out how to turn off the shopping lens. System Settings->Privacy.

There aren't any ads, it just shows the results of your search if you search for any type of media, be it a book, video or music. There is no direct contact with Amazon, until you click on the link. Canonical anonymizes your request, before it is passed on to Amazon during a normal search.

---

### Post by metalanguage on 2013-02-12
> **cariboo907 said:**
> With about 2 minutes of searching, you can find out how to turn off the shopping lens. System Settings->Privacy.

There aren't any ads, it just shows the results of your search if you search for any type of media, be it a book, video or music. There is no direct contact with Amazon, until you click on the link. Canonical anonymizes your request, before it is passed on to Amazon during a normal search.

I already removed the relevant packages (unity-lens-shopping). I still don't want to support this kind of business though.

---

### Post by cbtengr on 2013-02-13
Why is running a "modern" linux kernel a problem?

You weren't forced into Ubuntu, another vendor offers a similar product with a choice of different Linux versions.  You can replace Ubuntu with another distro if you don't like it (Mint?).

---

### Post by metalanguage on 2013-02-13
> **cbtengr said:**
> Why is running a "modern" linux kernel a problem?

I switched to Debian, had the system crash and found that others were having similar problem. The recommendation from users and some representatives (iirc) was to update the kernel to above a certain version.

> You weren't forced into Ubuntu, another vendor offers a similar product with a choice of different Linux versions. You can replace Ubuntu with another distro if you don't like it (Mint?).

Yes: ubuntu or ubuntu derivatives. How many of those have reliable support? I either pick something which is supported (preferably even by the laptop manufacturer) or I put myself in a position where I have to debug the system every time something fails. I consider myself somewhat linux-savvy, but I still find that to be unpleasant.

---

### Post by cbtengr on 2013-02-13
> **metalanguage said:**
> I switched to Debian, had the system crash and found that others were having similar problem. The recommendation from users and some representatives (iirc) was to update the kernel to above a certain version.

But why is using an updated kernel a problem?


Yes: ubuntu or ubuntu derivatives. How many of those have reliable support? I either pick something which is supported (preferably even by the laptop manufacturer) or I put myself in a position where I have to debug the system every time something fails. I consider myself somewhat linux-savvy, but I still find that to be unpleasant.

These are issues common to all computers, whether Windows, Mac or Linux.  If you felt you were being being "forced" to use Ubuntu, why did you make the purchase?

---

### Post by metalanguage on 2013-02-13
> But why is using an updated kernel a problem?
Because it limits the distributions you can run, unless you have a desire to debug the operating system. 

> **cbtengr said:**
> These are issues common to all computers, whether Windows, Mac or Linux.  If you felt you were being being "forced" to use Ubuntu, why did you make the purchase?
What issues, in specific, are common to all computers and/or operating systems? You're being dishonest if you're trying to claim that the user has to deal with the same kind of problems on a Window or Mac.

I didn't realize the hardware would be so dependent on the kernel. How was I supposed to have known that ahead of time? If Ubuntu is the only operating system intended to be run on this machine, then yes, it's my fault. I had the impression that there was some general linux support.

---

### Post by lolwtfhax on 2013-02-14
All hardware support is either built into the kernel or compiled as a module for that kernel. That being said, the Gazelle Professional ships with Ubuntu 12.10 running kernel 3.5.0. Therefore, any distro that includes kernel 3.5.0 or newer should not have any problems.

These distros should work fine:
ubuntu (and derivatives), fedora, arch linux, mint, gentoo, and others...

That's not to say an older kernel wont work. It might. I haven't tried it.

---

### Post by cbtengr on 2013-02-14
Perhaps I misunderstood what you meant by support.
Simply trying to help with your problem - calling me "dishonest" is not productive.

---

### Post by Penguissimo on 2013-02-17
> **metalanguage said:**
> 
What issues, in specific, are common to all computers and/or operating systems? You're being dishonest if you're trying to claim that the user has to deal with the same kind of problems on a Window or Mac.

If someone tried to install Windows XP or Mac OS 9 on a modern computer, they would certainly have system crashes. This is because that software was written long before today's hardware was built. The same is true for Linux; it's impossible to write software that is *forward*-compatible.

> **metalanguage said:**
> I didn't realize the hardware would be so dependent on the kernel. How was I supposed to have known that ahead of time? If Ubuntu is the only operating system intended to be run on this machine, then yes, it's my fault. I had the impression that there was some general linux support.

The kernel is the piece of software that handles communication between the hardware and higher-level software. By definition, hardware support depends upon the kernel. 

And while S76 only offers active support for Ubuntu, many different distributions can be run on this machine. You just have to choose one that's modern enough to support your hardware. That rules out, say, Debian Potato, but you're hardly locked into Ubuntu; you'll just have to do the legwork to get anything else running on your own.

I'm also confused about the exact problem you're having. When people recommended updating your kernel in Debian...did you try that? If not, why not? Was there some other part of the distribution that wouldn't work with a newer kernel? Or do you have some other reason to not want to update your kernel? I promise that the requirement for a modern kernel isn't some kind of arbitrarily imposed evil, but a simple cause-and-effect scenario: kernel developers have no way of implementing support for hardware until that hardware exists. ;)

---

### Post by metalanguage on 2013-02-22
> **Penguissimo said:**
> I'm also confused about the exact problem you're having. When people recommended updating your kernel in Debian...did you try that? If not, why not? Was there some other part of the distribution that wouldn't work with a newer kernel? Or do you have some other reason to not want to update your kernel? I promise that the requirement for a modern kernel isn't some kind of arbitrarily imposed evil, but a simple cause-and-effect scenario: kernel developers have no way of implementing support for hardware until that hardware exists. ;)

I've tried upgrading a kernel on a VM in the past and I feel that it is a pain in the ass. I could be wrong and it could be very easy and maybe I had a bad experience, but I just picked the solution which would most likely lead to the best outcome. Again: I'm not interested in fixing operating system or package issues.

So fine: you're not forced into ubuntu, but you may experience problems if you run a kernel below a certain version. That was the intended message. I don't know why I wrote what I wrote before.

---

### Post by ElMaxito on 2013-02-22
Since we are on the topics of gazelles and whatnot.
I plan on starting masters program in CS in fall. Is this a good build for it? Any changes? If so, why? Thanks. 
Base System Price $875.00 (Gazelle Professional)
Ubuntu 12.10 64 bit
5 Free GB of Ubuntu One Online Storage and Sync
15.6" 1080p Full High Definition LED Backlit Display featuring 95% NTSC Color Gamut in Matte Finished Surface ( 1920 x 1080 ) +$79.00
Intel HD Graphics 4000
3rd Generation Intel Core i7-3740QM Processor ( 2.70GHz 6MB L3 Cache - 4 Cores plus Hyperthreading ) +$175.00
8 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 4GB +$45.00
120 GB Intel 520 Series SATA III 6 Gb/s Solid State Disk Drive +$109.00
United States Keyboard Layout
8X DVD±R/RW/4X +DL Super-Multi Drive
Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module

---

### Post by nerdcommander on 2013-09-25
Does anyone have comments on the most recent version of this laptop? Especially battery life and keyboard/trackpad performance? Thanks.

---

### Post by rorschachwalter on 2013-09-25
Keyboard is absolute rubbish. I posted videos for System76 and was told it was defective. Then Ian insisted it was just personal preference -- same thing they've been telling all the unhappy Galago users. The keyboard is simply horrid.

The touchpad is better, although admittedly I didn't use it for multigesture except for two-finger scrolling. The finish on the touchpad makes your fingers stick to it -- it's the same plastic the rest of the body is made of. The buttons sound hollow when you click. You can't use edge scrolling, since the touchpad doesn't actually register touching all the edge, which means you'd have to slide your finger up and down an invisible line slightly away from the edge to get it to scroll, and any deviation means it stops scrolling and moves the cursor. Highly irritating.

Battery life didn't seem to be affected terribly much by usage. It was I think 3-3.5 hours.

There were other issues -- wireless wasn't reliable, the volume buttons and others would "stick", resulting sometimes in making you go deaf with headphones on or waking the entire house up if speakers were plugged in, and it would render the keyboard unresponsive until you found out which key was sticking (it's a software issue, not a hardware issue).

The display actually doesn't seem to display colors accurately. Not sure whether that's just because of poor quality, or because the color profile they give you is off. But the entire display has a hue to it, and some of the colors are objectively wrong (you can see this using an online display test).

Speakers were garbage. Literally only as loud as my HTC EVO's speakers, and literally about the same poor, tinny quality.

The webcam and microphone are also rubbish.

The case scratches incredibly easily.

The machine runs hot, and presently it can't even handle a basic game like Team Fortress 2 (this *might* be fixed with the next Ubuntu release).

The microphone doesn't work until you plug in and unplug a device from the microphone port.

The BIOS on mine (which they assured me had been tested) didn't respect the low battery alarm setting, which meant I always got very loud, very annoying beeps when I passed the threshold.

---

### Post by nerdcommander on 2013-09-27
thanks very much for the detailed review.
if not the Gazelle, then what would you recommend? or, maybe better put, what is your reference machine that has the user experience and performance that you could recommend? I prefer a linux preload situation, but am not opposed to self install.
thanks.

---

### Post by rorschachwalter on 2013-09-27
It really depends what you're looking for. But something similar to the Gazelle (minus the IPS display, which is extremely rare on anything other than an ultrabook), the Dell Inspiron line works well with Linux (better than the Gazelle, from my experience). They've released an updated 17-inch version just recently with Haswell, and I imagine their 15-inch version will be updated shortly as well. Dells in general work well with Linux. You can wait for a "sale" on whatever machine you want or just call a representative and tell them you want the machine but it's too much and they'll help you get money off.

---

### Post by ddraper2 on 2013-09-30
I have had my Gazelle about 2 or 3 weeks. The configuration is as follows:

Base System
Ubuntu 13.04 64 bit     
15.6" 1080p Full High Definition ColorPro IPS Display with Matte Surface ( 1920 x 1080 )
Intel® HD Graphics 4600     
4th Generation Intel® Core™ i7-4800MQ Processor ( 2.7 GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )
16 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 8 GB
United States Keyboard Layout     
750 GB 7200 RPM SATA II
No Secondary Hard Drive     
8X DVD±R/RW/4X +DL Super-Multi Drive     
Intel Centrino Advanced-N 6235 - 802.11A/B/G/N Wireless LAN + Bluetooth Combo Module 

It has taken me a little bit of time to go through the machine however I believe I have touched on all the hardware etc. I have verified that all of the hardware is indeed functioning.

The biggest complaint is with the keyboard. It just seems to miss random keystrokes unless I pound on the keys. My a and w keys seems to be the most problematic however the problems are not limited to those keys.

I don't have much to say about the trackpad. I am not a big trackpad guy and use a mouse almost all of time except when I using my laptop on the subway. That said the trackpad is functional and certainly way better than the 4 year old HP laptop this one replaced.

I am going to open a support ticket on the keyboard. I really feel when you pay more than $1200 for a laptop you should not have problems with the keyboard. The only issue that prevents me from recommending the machine is the keyboard.

---

### Post by rorschachwalter on 2013-09-30
> **ddraper2 said:**
> 

I am going to open a support ticket on the keyboard. I really feel when you pay more than $1200 for a laptop you should not have problems with the keyboard. The only issue that prevents me from recommending the machine is the keyboard.

They *will not* fix the keyboard or acknowledge that it's a problem. Ian admitted from the videos I posted that the keyboards wasn't functioning well, but then decided to blame it on personal preference. And then the replacement they sent me was not only as dysfunctional as the original, but they it had a Windows key instead of an Ubuntu key. Small thing, but the point is, it's probably better for you *not* to try to get the keyboard "fixed".

---

### Post by nerdcommander on 2013-10-09
I'd like to support Linux/Ubuntu Laptop "manufacturers" and a friend has a Lemur that he likes, but the issues scare me. I've considered trying one and returning if it doesn't work for me, but at this point I'm holding out for the recently hinted at Dell XPS 13 with Haswell processor hoping they produce an Ubuntu loaded version. Supposed to be November for the machine, no official Ubuntu version yet... Thanks for the feedback.

---

### Post by 4CP8X4x on 2013-10-09
Well, for what its worth, I just recieved my Galago a couple days ago and its the best computer Ive ever had. Keyboard isnt great but it registers keys just fine. HDMI audio doesnt work but I suspect that its because Im using the 13.10 beta. No other problems and the screen is the most beautiful display Ive ever had the chance to see in person.

---

### Post by hendrik-0 on 2013-10-24
My experience with the gazelle was very similar to that of rorschachwalter. the keyboard is indeed very bad (mine was loose in the lower right corner). more annoyingly, when i first contacted them about the loose keyboard they did not tell me it was a common problem, they simply told me the way to take the keyboard off but no way to fix the problem. i later contacted them about it again and then they suggested to put notecards under the keyboard. while this worked, it is a somewhat ridiculous way of solving the problem.

what also annoyed me was that after one week i heard the first loose screw moving around inside the laptop. after opening the laptop, I noticed that 50% of the screws inside the laptop were not tightened properly. if you mind opening your laptop and your keyboard and fixing things, don't get this laptop.

i also had trouble with the microphone and skype only shows me a green screen on video calls. the lenovo of my wife with the same ubuntu version did not have that problem. i did not have time to fix this problem but given that on the same ubuntu version skype works fine on the lenovo and not fine on the system76 suggests that skype has trouble with some element of the system76 laptop.

further, if you plan to carry the laptop around you will notice that the edge between keyboard and trackpad starts touching the screen. that leaves a nice grey mark on the screen - great, that is exactly what you want with a glossy screen. i fixed it by attaching several 3M Bumpons along the top of the screen to keep the screen from touching the laptop. again, if you expect to buy a laptop, start running it and have no problems, don't bother with system76. 

the laptop indeed becomes very hot, especially in the area where you palm rests. i don't mind, but i can imagine that many people will find it annoying.

i tried some gaming on the laptop. uru (game from around 2006) worked fine on highest settings in wine. the ventilation went to full power for it though, so it seemed as if i was playing at an airport. i have not yet tried any steam games which may be the real test.

i noticed that the screen switch button (fn+f7) did not work. that was right at the moment i wanted to start a presentation, great!

to nerdcommander: i would recommend to get a lenovo and install ubuntu on it by yourself. the lenovo of my wife which came with win7 and still gave much less trouble running ubuntu 13.04 than the system76 laptop. sound, video, function keys, fingerprint reader, etc. worked without any problems and their laptops seem to be build out of much better material.

---

### Post by jaylittle on 2013-10-25
As a recent purchaser of the Gazelle Pro, I would like to provide my own review.

For starters the matte screen on the unit I purchased is beautiful.  The keyboard works pretty well despite a number of complaints indicating otherwise.  The idea that this might be a problem forced me to think long and hard about getting this laptop as I type for living (developer) and I'm glad I decided to move forward anyway.  The machine is quite powerful and can run multiple 4 gigabyte VM instances of Windows 7 Pro in VMWare without issue.  During compilations within Visual Studio the fans will spin up, but after that they will quiet down in short order.  Also these machines don't "force" you into running Ubuntu.  I'm running Arch Linux on mine right now with no issues at all (though I am using a cutting edge Intel video driver compiled out of git as Haswell support on Linux is still percolating it seems).

Now I've been in and out of the laptop quite a bit.  I installed my own SSDs and I've been switching between various wireless cards with different chipsets in an ongoing experiment to find what works best in Linux.  In that time I've found what appear to be several "extra" screws hidden away in the case and in some cases those screws come loose  and have to be removed.  I typically have noticed this after I close up the laptop, turn it over and hear a rattling.  I believe there have been four of these screws in total.  This was somewhat disturbing but the issue was easily rectified as getting in and out of the laptop is pretty easy as it only requires removing two screws on the bottom.

Also in terms of gaming, my experience has been good.  I already knew what I was in for with Intel integrated graphics and I'm pleased.  A lot of indie games that have been ported to Linux either via Humble Bundle or Steam work without issue.  Intel's support for their video hardware in Linux is improving day by day whereas their wireless hardware is terrible.  I highly recommend against purchasing any Intel wireless chipset for use in Linux or Windows due to massive driver related issues.  Atheros is the way to go.  Sadly System 76 doesn't offer that as a build to order option.

Overall my opinion of this laptop is very favorable.  I would recommend it to others without hesitation.  Of course as an experienced Linux user, I'm not afraid to get my hands dirty so a lot of the nit picks above are really non-issues for me.

---

### Post by scoodlebop on 2013-10-25
jaylittle, is it easy to put in a different wireless card? If I just purchase an atheros card from Amazon, can I just pull out the Intel card and put in the new card, or will it be more tedious than that?

---

### Post by hendrik-0 on 2013-10-25
@jaylittle: yes, tightening screws etc. is certainly nitpicking. what is certainly no nitpicking is the issue about having to plug in and plug out a microphone (headphone works, too) in order to get the internal microphone going. that is simply bad hardware/drivers and seems to be a problem that has been around for quite a while. also, having to put ugly bumpers on the laptop case so that the screen does not scratch on the keyboard edge below is simply bad construction. i have last had that problem with a laptop from around 2004. all laptops i have known since then had a smart enough design to avoid that problem.

i agree with you that it is an ok laptop, but i would not recommend it to others. especially since some of the problems have been known to system76 for a long time and have not been fixed over time. that suggests that also in the future one can expect their laptops to ship with bad keyboards and bad case construction. unfortunately i am over my 30 day return time, so since i did not immediately notice all of the problems I will have to keep it. but looking around and seeing that one can get a similarly-paced lenovo with a sturdy outside, nice keyboard and longer battery time makes me feel quite bad about having bought this laptop.

---

### Post by mbaee on 2013-10-25
@jaylittle, When I purchased my Gazelle Pro (gazp9) in June, I upgraded to the "Killer™ Wireless-N 1202 802.11 A/B/G/N Wireless LAN + Bluetooth 4.0 Combo Module" which is an Atheros based card.  I see it isn't offered anymore for new builds, but it's working great for me.  I'm sure you could find it online and add it yourself.

> 
# sudo lspci -v
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
    Subsystem: Bigfoot Networks, Inc. Device 2003
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7d00000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at f7d80000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k


---

### Post by jaylittle on 2013-10-25
> **scoodlebop said:**
> jaylittle, is it easy to put in a different wireless card? If I just purchase an atheros card from Amazon, can I just pull out the Intel card and put in the new card, or will it be more tedious than that?
Yes you'll have to remove two screws on the bottom of the laptop to remove the bottom panel.  Then you'll need to gently disconnect the two antenna wires from the wireless card (which is a mini-PCIe card) and remove a single screw so that you can remove it from it's slot.  Then put in the new card, screw it in and reconnect the antenna wires (gently).

---

### Post by jaylittle on 2013-10-25
> **hendrik-0 said:**
> @jaylittle: yes, tightening screws etc. is certainly nitpicking. what is certainly no nitpicking is the issue about having to plug in and plug out a microphone (headphone works, too) in order to get the internal microphone going. that is simply bad hardware/drivers and seems to be a problem that has been around for quite a while. also, having to put ugly bumpers on the laptop case so that the screen does not scratch on the keyboard edge below is simply bad construction. i have last had that problem with a laptop from around 2004. all laptops i have known since then had a smart enough design to avoid that problem.

i agree with you that it is an ok laptop, but i would not recommend it to others. especially since some of the problems have been known to system76 for a long time and have not been fixed over time. that suggests that also in the future one can expect their laptops to ship with bad keyboards and bad case construction. unfortunately i am over my 30 day return time, so since i did not immediately notice all of the problems I will have to keep it. but looking around and seeing that one can get a similarly-paced lenovo with a sturdy outside, nice keyboard and longer battery time makes me feel quite bad about having bought this laptop.
For what it's worth - I feel that System 76 is probably a bit too aggressive in moving to new Intel processors and chipsets.  The fact is that support for newer hardware lags in Linux, no matter how much you love it.  Up until kernel 3.11, Intel Haswell video support was less than great. Right now I'm using a pre-release xorg video driver for my Haswell video because kinks are still being ironed out.  But to be fair to System 76, they are competing in an aggressive market with razor thin margins.  Ubuntu generally seems to do an alright job with negating some of these issues but still - I think it could be handled better.

Yeah I agree the screw thing is annoying.  But I have had other laptops with similar issues ;)  Nobody is perfect.  As long as the screws don't short circuit the motherboard its a simple enough issue to resolve.  As for the keyboard and the screen issue, I can't attest to that one.  My laptop is relatively new though, so maybe that will become an issue over the next few months.  Maybe not.  We shall see.

---

### Post by jaylittle on 2013-10-25
> **mbaee said:**
> @jaylittle, When I purchased my Gazelle Pro (gazp9) in June, I upgraded to the "Killer™ Wireless-N 1202 802.11 A/B/G/N Wireless LAN + Bluetooth 4.0 Combo Module" which is an Atheros based card.  I see it isn't offered anymore for new builds, but it's working great for me.  I'm sure you could find it online and add it yourself.
My experience with combo wireless/bluetooth cards has been decidedly mixed whether the OS is Windows or Linux.  I find that on most of these cards, even if things are working great beforehand, once you connect a bluetooth device a number of problems tend to arise.  Not the least of which is the fact that once I connect my bluetooth headphones, network performance disintegrates.  At this point I've become resigned to using a straight out dual band wireless card and a USB dongle for bluetooth.  This seems to avoid all of the issues.

---

### Post by NoBugs! on 2013-10-30
Just curious, was this with the latest version (Gazelle Professional 9) ? [https://www.system76.com/laptops/model/gazp9](https://www.system76.com/laptops/model/gazp9)

Can you expand on "keyboard is absolute rubbish"? You mean the funny numpad with . at the top?

---

### Post by scoodlebop on 2013-10-31
@NoBugs!

People complaining about the keyboard are complaining that it doesn't register keystrokes. I'm too lazy to look them up, but there are multiple blogs and forum threads where people have hated the keyboards so much that they sent the machines back, even if they lose shipping costs and import fees. Most of the reviews are about the Galago, but the Gazelle seems to have the same complaints.

It's making me hold off on buying one. Although I keep thinking of getting one to see if I can handle the keyboard. There are videos somewhere on this forum that show how bad the keyboard is, with the guy hitting a key a lot and it doesn't register if you want to see what it's like. [This guy says]("http://blag.depotwarehouse.net/2013/09/system76-galago-ultrapro-galu1-review.html") "When I was initially typing this review, using this keyboard was an exercise in frustration, and I got really mad. **I returned the laptop because of the keyboard**" and "If you take only one thing away from this review, take away that the keyboard is *really* bad and give extra considerations to that before purchasing" and "I need one that when you press a key, the Operating System registers  that key as pressed and renders the appropriate ascii character on  screen. *The Galago k**eyboard does not do that*".

I'd love it if we could try the laptops for free so we could see if we liked them. That's a lot of money to spend on something that might have such a bad keyboard.

---

### Post by hawkmage on 2013-10-31
System76 is not forcing you into Ubuntu.  I have a friend with a Bonobo6 and he has run Mint, Arch, Debian and SolyDX on it with no issues.

---

### Post by NoBugs! on 2013-11-02
That's disappointing, since System76 seems to be the only place you can get a Matte good display, 1080p in something smaller than 17" that has a DVD drive and Ubuntu. :(

---

### Post by Sheepherd on 2013-12-03
hi all

just my experience with my galago ultra pro.

to sum up my attached printscreens: 

when closing the laptop lid, the screen touches the edge above to trackpad.
I reported this to the system76 support staff and they told me "it's not supposed to do that"
so I sent the unit in, willing to pay 600$ shipping to switzerland to get the screen replaced.
after getting the laptop back the issue was still present.
last answer from the staff: "the situation is treated  as not a part failure because of the design of the machine and how  close the screen resides to the keyboard.  This is not uncommon to  models of a thin nature.  "

soooo i payed 600$ for  something they could have told me to begin with, besides the point that  this behaviour being common is utter crap.

I am still absolutely  stunned by the performance of the galago and very happy with my gazelle  but a support that lies to you, and an obviously bad designed chassis is an  absolute killer.

Althought one of the reasons why I bought my laptop at system76 is to support the linux community I cant recommend them anymore.



[ATTACH=CONFIG]248323[/ATTACH]
[ATTACH=CONFIG]248319[/ATTACH]
[ATTACH=CONFIG]248320[/ATTACH]

---

### Post by metalanguage on 2014-01-02
I've had this computer for about a year now and it has no significant (crippling) issues. On one occasion I felt like I had to troubleshoot something (I think it turned out to be a non-issue), and so I posted a question on the system76 support site. They responded quickly.

There are minor things here and there though. I'll talk about them now:

1. rorschachwalter writes "the volume buttons and others would 'stick', resulting sometimes in making you go deaf with headphones on or waking the entire house up if speakers were plugged in, and it would render the keyboard unresponsive until you found out which key was sticking (it's a software issue, not a hardware issue)"

I get this problem a lot. The way you "fix" it is by using the volume button which stuck. If the "increase volume" button sticks, the volume will go to 100%. Then lower the volume and then hit "increase volume" again. Similarly with "decrease volume". This brings back the responsiveness of the keyboard for me. 

2. "The microphone doesn't work until you plug in and unplug a device from the microphone port."

Yes, this also happens to me. I'm really lazy though and there might be some way to fix it. 

3. I've had the computer suddenly just turn off maybe 3-5 times. No idea why. Too lazy to debug. I'm almost positive that it's not related to temperature.


There are a bunch of things I feel like people exaggerated (e.g. the keyboard). It depends on how high your standards are. The keyboard may feel cheap when compared to a macbook pro or something, but it is functional (at least in my case).


... and um, yeah, please read the series of responses I made in the beginning of the thread. You can run any operating system you like. The point is that there are greater risks if you don't run a kernel above a certain version. If you can figure it out, great. If you're not interested in debugging operating system level things like I am, then you don't have complete freedom in picking. (God forbid if a slightly casual user runs linux, right?)

---

