---
title: "Petition to Canonical &amp; AMD re ATI madness on Jaunty"
date: 2009-05-03
forum: The Cafe
---

### Post by blackSP on 2009-05-03
As many of you, I also suffer from the annoying lack of ATI card support.

What I find most disturbing is the lack of any sort of 'official' communication from either Canonical or AMD. Although I have to say that AMD at least notified us that they moved some of their product development on the back burner.


Maybe we can use this thread to vent our frustration (not to complain about our individual card/driver problems).

To start:

Hey Canonical and AMD, please make 1,5 year old Asus F8P/Radeon HD2400 work with proper 2/3D support!


[COLOR="Lime"](Please only reply if you want to say something to Canonical or AMD)[/COLOR]

---

### Post by TomB19 on 2009-05-03
I used to run the proprietary ATI driver because the open source driver had some bugs.  Now, the open source driver is working well so, while there is no binary driver available, I'm sufficiently happy.

Personally, I don't think it's a big deal but then I don't play games or do much 3d work.

---

### Post by chudak on 2009-05-03
I sent them email from their support form to complain. I'd suggest that others do the same. My 2 year old T60 with a Mobility Radeon X1400 had support dropped in the new driver. This is inexcusable.

If they fail to respond to this situation I'd suggest that people rethink the purchases of ATI video cards or laptops containing them. It really pisses me off that a two year old laptop that cost upwards of $2k is now unsupported by the manufacturer of one of the primary components.

---

### Post by scorpia1275 on 2009-05-03
> It really pisses me off that a two year old laptop that cost upwards of $2k is now unsupported by the manufacturer of one of the primary components.


Here, here.  My laptop is only 18 months old (A Dell Inspiron 1521) and now X1250 mobility radeon is unsupported.

Forgive me if this is a silly assumption, but I thought Linux was an ideal OS that works on older hardware, able to bring an old machine back from the grave, one that has been left in the dirt by Windows?

Is is not possible for the people who make XServer -Xorg (or whatever it is) backward compatible so the old driver can continue to be used with the new version?  Or at least downgrade the Xserver from 9.04 to use the old one from 8.10 so that it still works?

I love ubuntu (well perhaps love is too strong a word) and Linux, but it just seems that Ubuntu with every new release takes two steps forward and one step back.

Scorpia

---

### Post by Jackelope King on 2009-05-03
I'd really like to see a fresh driver come out that would let me give Jaunty a shot right now with my Radeon Mobility x700, but at this point, it almost seems like it'll just be quicker to buy myself a new laptop this summer and make sure I avoid ATI graphics cards.

---

### Post by jaxpiron on 2009-05-04
I agree

still if this is their line ([http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y))...

This is really not acceptable, they think 26 months are enough to let u throw your machine in the garbage. No no no.
My laptop is 3ys old and alive, and I do intensive processing on it, should I dump it just because they think it is way too old??

I think they will not care about us complaining, but we'll see how many of us will go for an nvidia next time they buy a laptop.

I will for sure.

---

### Post by udippel on 2009-05-04
> **jaxpiron said:**
> 
I think they will not care about us complaining, but we'll see how many of us will go for an nvidia next time they buy a laptop.

I will for sure.

Careful, careful. Though this is very bad, the situation with NVIDIA-drivers has gone south as well; just read their forum! Many, many have problems with stability and functionality. :(

I for one might do the 'unthinkable', after sitting on AMD CPUs for the last 20 years, I might move to Intel. I have an old Dell Latitude D400 of 5 years of age, and 9.04 and compiz work well on it, and so does the Acer Aspire A4930 that I installed yesterday. No, I don't like Intel. But their graphic chips (IGP) are well supported, because they have opened the specs and documentation. 
I might be willing to reward this with money (the machines above have been bought by someone else).

Uwe

---

### Post by Ubuntist on 2009-05-10
My card, a Radeon 9800 Pro, being quite old, my complaint that it's no longer supported will be of limited weight.  Can I legitimately complain to AMD that the limitations of the open-source driver result from AMD's lack of openness?  Is either nVidia or Intel better in this regard?

---

### Post by Wartender on 2009-05-10
i really shouldn't have bought my laptop with an ATI card a few weeks ago. it has an ATI Radeon HD 3200 and it's been giving me nothing but problems. i had to toil endlessly and downlaod like 5 drivers to get Spring (my favoritest game ever) to work on 8.10, and even my normal desktop used to flicker a lot. Why do i say USED to? because now i upgraded to jaunty, and nothing works. see [this]("http://ubuntuforums.org/showthread.php?t=1154915"). My desktop with an nvidia geforce 8400 works perfeclty, i have never had any issues with it. ever.
i really should have bought a laptop with nvidia, but the thing is not much nvidia is seen on laptops... *sigh*

---

### Post by ssri on 2009-05-10
My 6910p business laptop from HP came with vista pre-installed, aero and the whole works, 18 months ago (Mobility Radeon x2300, M64).  AMD/ATI even says my card is supported in their Catalyst 9.4 (8.602) release notes.  Tested it in Intrepid and neither aticonfig nor fglrxinfo worked! ](*,)  This alone made me hesitant to upgrade to Jaunty.  The latest opensource drivers (Jaunty livecd, ppa) has windows compositing barely working, even with different xorg.conf tweaks after the default config threw up some glitches.  Testing it out with the Jaunty livecd and my current Intrepid setup yielded the same results.  Thankfully, I easily rolled back my drivers to 9.3 in intrepid.  I can't imagine grandma enduring all of this hardware hacking.  With respect to us ATI sufferers, I think Canonical and ATI seriously dropped the ball with the rollout of Jaunty.

---

### Post by Mark Phelps on 2009-05-11
Agree with the claim of ATI dropping the ball ... I'm using open source now for the first time since 7.04 only because AMD/ATI has stopped supporting my card.  But ... they did the same with Vista drivers, and with Windows 7 drivers.  So, I really doubt that any "petition" is going to change their minds.

But Canonical might step up development of their open source driver if they see enough interest in the Ubuntu community.

As I said, I'm using the open source, and am able to get compiz working OK (first time on open source) and full 1920x1200 resolution.  So, for me, the open source drivers are working fine.  But I've heard that they don't handle hardware acceleration for gaming.

---

### Post by sgosnell on 2009-05-11
This is an ATI problem, not a Ubuntu problem.  The hardware manufacturer has the responsibility of making the drivers available, or at least the necessary information for open-source developers to make a driver.  The long-term solution is to stop buying anything with an ATI card.

---

### Post by lvleph on 2009-05-11
AMD doesn't care. When I complained they said tough. Well, I am not buying AMD any more. That is a customer of 16yrs they just lost. I have only bought 2 Intels in that whole time, if I recall correctly. 

Their reasoning for telling me tough was that although my computer was only 8 months old the card in it was released almost two years ago. They state that it is reasonable to stop supporting such cards. My thinking is that you stop supporting it once computers have stopped being produced with them for over a year.

---

### Post by Ubuntist on 2009-05-12
> **lvleph said:**
> AMD doesn't care.

If enough of us complain, perhaps AMD will start to care.  It's so easy, let's all give it a try.

---

### Post by eldragon on 2009-05-12
flipping to nvidia based stuff might give you joy today, but on the long run you will be probably facing the same problem (or even worse) since their OS drivers are even worse than ati's. on the other hand, this will definately spurr innovation and development on the open source ati drivers, for which apparently ati releases specs (or this i heard).

im stuck with a x600 on my desktop, but havent gotten around upgrading. but i decided to go with intel on my laptop in  my last purchase. just for opensourceness of their drivers. 

im not picking OS drivers because i belive in RMS's crusade against binary. but drivers which interact with your kernel should be open for other reasons...

so there you go. i think if you care about the longetivity of your hardware, you should use the OS drivers anyway, and report bugs, test and share your experience with devs so that a better driver can be produced.

---

### Post by gocek on 2009-05-12
I have a rather new card which is HD4870 and it still works really crappy on Jaunty. I would expect that at least if I'm the lucky one to have a card which is supported (in some way, because none linux drivers by ATI are officially supported) it should work. But it does 2 times out of 3, which certainly is a joke.

And seriously, how is the situation with nvidia? If I switch to let's say geforce 260 will it work in Jaunty with desktop effects, no flickering in movies and well ... generally WORK ?

---

### Post by nealklomp on 2009-05-12
The thing is ATI is so darn popular too. This should be addressed with some alacrity.

---

### Post by nealklomp on 2009-05-12
.

---

### Post by d_fiant_1 on 2009-05-16
as an ATI customer for the last 7 years I too am pissed off with their approach to Linux and the inexcusable rejection of the customers that pay the wages of those who develop the drivers.

I highly doubt a petition would do anything the the arrogant pompous arsehole at AMD that has made the atrocious mistake.

So I went out and bought and Nvidia card...hurting AMD bottom line owuld be more effecient and cause a greater impact than a petition that they will probably never read

---

### Post by Sxeptomaniac on 2009-05-19
Same issues here.  I have an ATI HD 3200 on my **brand new** laptop.  They don't have the excuse that it's an old card in my case.  In addition, the ATI Sound chipset on that same laptop has been a complete pain, too.

At this point, my plan is to never buy ATI again.  I've had issues with an ancient NVIDIA card on my old desktop, but they weren't so completely frustrating.  The somewhat newer NVIDIA card on my new desktop has been a breeze, though.

---

### Post by shrndegruv on 2009-05-20
> **sgosnell said:**
> This is an ATI problem, not a Ubuntu problem.  The hardware manufacturer has the responsibility of making the drivers available, or at least the necessary information for open-source developers to make a driver.  The long-term solution is to stop buying anything with an ATI card.

It is Ubuntu's problem in that there was no visible warning not to upgrade for ATI users.  I think canonical really dropped the ball on this one. There is no way Jaunty is usable for the majority of ATI users.

---

### Post by Cyb3rD0n Architectus on 2009-05-22
It is an absolute outrage that a product merely 2 years old gets kicked off the support by the manufacturer! I have a Dell Inspiron 9400 with an ATI Mobility Radeon X1400 and sometimes runs better than the newest mid-range videocards! And especially with laptop users who cannot change their videocard with a new one, as with desktop compters, it is very unacceptable to drop, not even support, but the entire functioning of a product alltogether...

ATI, you have lost my confidence. Unless there's a solution before June 1st, next time I buy a laptop, it will contain an NVIDIA videocard.

But also, why is Canonical (or the Ubuntu-crew) not outraged by this themselves? They surely will loose Ubuntu users because of this. And Linux gets a serious hit as a 'difficult platform' and a platform 'that does not support all hardware'. The clichés are becoming true with this d*ck move.

I am a big supporter and promotor of Ubuntu myself, but I cannot promote it as it does not support even the simplest of videocards anymore (because of a third party, but not supported nonetheless...)

---

### Post by c1k2j3c4 on 2009-05-22
Most manufactures put a lease a 3 year warranty on there ATI cards and motherboards. So I don't understand why ATI would quit supporting something that not even out of warranty yet!

Part of the problem can be put to Ubuntu or at lease to debian. My 780G Motherboard and 3450 Video Card combo works well with PClinuxOS 2009. So maybe ATI tested there drivers on RPM based distro and assumed they would run fine on debian based distros or debian/Ubuntu droped the ball.

---

### Post by ssri on 2009-05-22
> **c1k2j3c4 said:**
> My 780G Motherboard and 3450 Video Card combo works well with PClinuxOS 2009. So maybe ATI tested there drivers on RPM based distro and assumed they would run fine on debian based distros or debian/Ubuntu droped the ball.


Umm, no.  PClinuxOS is running xserver 1.4.0 by default.  The last xserver to support ATI proprietary drivers for our "legacy" cards (Catalyst 9.3) is version 1.5.x.  Unfortunately, Jaunty installs xserver 1.6.0 by default.  I guess PClinuxOS gone with the tried and true approach, even with the 2.6.29.4 kernel (same as Jaunty)!  Very interesting.  Probably time to go distro hopping, as this ATI fiasco prevented me from upgrading to Jaunty.  Reason being, kernel versions after Intrepid seem to have cool features for laptop users, especially driveguard-like features.

---

### Post by Cyb3rD0n Architectus on 2009-05-22
> **ssri said:**
> Probably time to go distro hopping, as this ATI fiasco prevented me from upgrading to Jaunty.  Reason being, kernel versions after Intrepid seem to have cool features for laptop users, especially driveguard-like features.

Hmmm... My opinion excactly. I'm downloading the PClinuxOS 2009-iso at the moment to try it out.

---

### Post by XPM on 2009-05-22
My 4850 X2 will not work. X-server crashes
Using the opensource drivers makes the system unstable after 20 minutes until it locks up.
It works perfectly under other OS's and the card is brand new.

What gives ATI?

It did not work with 9.4 and having wasting my time for a month...I found out that it didn't work with 9.5 either!

---

### Post by shrndegruv on 2009-05-22
I was originally so angry with this issue that I went back to windows.  Then I realized how uncomfortable I am without bash and went back to intrepid.  Following these threads, I am beginning to think that for ati users that have performance issues (slow maximizing/resizing) it is a compiz issue and not a driver issue.  So I am going to try another upgrade and just use metacity or xfce and see if the performance issue goes away.

I fully believe that some ati users are SOL, those that can't even get a display, which of course is poo.  But for some of us it might be compiz and unrelated to the driver.

---

### Post by ssri on 2009-05-22
> **XPM said:**
> My 4850 X2 will not work. X-server crashes
Using the opensource drivers makes the system unstable after 20 minutes until it locks up.
It works perfectly under other OS's and the card is brand new.

What gives ATI?

It did not work with 9.4 and having wasting my time for a month...I found out that it didn't work with 9.5 either!

As much as I complained about ATI leaving us laptop owners with 1.5-2years GPUs in the cold, even their support for adopters of their recent hardware is shoddy.  At least there are opensource drivers for us legacy folks, screen artifacts and powerplay support be damned, right? ;)  With that being said, did you try to build the debs from the proprietary installer file?  I never had satisfactory results when using ATI's installer program in a x86_64 kubuntu environment.  Building the debs from 9.3 and installing it manually has yielded a pretty stable system.  Yeah FPS is considerably lower according to glxgears, but I do not notice any change when using googleearth or other 3D programs.  In fact, they ran smoother and faster in 9.3 than in 8.11 (the one included in intrepid).

Create debs manually from here (under manual install): [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide).

I made a bash batch script to run the following commands.  For example, after making the debs from Catalyst 9.3 (8.543):

1) sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb fglrx-kernel-source_8.593-0ubuntu1_amd64.deb fglrx-amdcccle_8.593-0ubuntu1_amd64.deb
2) sudo dpkg-reconfigure -phigh xserver-xorg
3) sudo aticonfig --initial -f

If 3) gives you a message about not being able to detect your card, then you are SOL.  To remove the packages, just sudo dpkg -P names.deb

good luck

---

### Post by Mark Phelps on 2009-05-22
Ordinarily, I stay out of these debates, but in this case, I have to admit, the critics of Canonical have a good point.

Consider the following:
1) It's possible to determine which ATI card is installed in the machine
2) It's possible to determine if the ATI restricted driver (fglrx) is running on the machine -- and what version
3) It's possible to determine which ATI card are no longer supported under the new drivers.
4) It's already know which driver versions will no longer work with the new Xorg under 9.04.

Given this information, what Canonical SHOULD have done with 9.04 is embedd a detection script as part of the install/upgrade that checked this information, and if it determined all of these to be the case, put up a panel (or message in the text installer) informing the user that their card and restricted drivers are not supported in 9.04, and telling them  that they must remove the drivers before installing, and terminate the install.

To continue an install and leave folks with a machine that no longer boots into a working desktop is just plain sloppy work.

Ok, so maybe we don't care if the Ubuntu community grows in leaps and bounds or not (meaning we don't care if 9.04 leaves new folks with a really bad taste in their mouth regarding Ubuntu) -- but still, the OS developers need to do a better job of preventing OS upgrades from "breaking" existing installations.

Just my 2-cents.

---

### Post by moster on 2009-05-22
In septembar 2007 on some kernel summit report it was told that AMD opened drivers for all of their graphic card from radeon 500 to up. Is it true or not?

here is link
[http://lwn.net/Articles/248227/]("http://lwn.net/Articles/248227/")

And why there is somewhere here some black list and white list of graphic cards and versions of ubuntu so people have less frustration. Is that so hard to do that_ We can all vote or something.

---

### Post by XPM on 2009-05-23
I'm downloading 8.10 again.
That'll work right?

---

### Post by XPM on 2009-05-23
> **ssri said:**
> As much as I complained about ATI leaving us laptop owners with 1.5-2years GPUs in the cold, even their support for adopters of their recent hardware is shoddy.  At least there are opensource drivers for us legacy folks, screen artifacts and powerplay support be damned, right? ;)  With that being said, did you try to build the debs from the proprietary installer file?  I never had satisfactory results when using ATI's installer program in a x86_64 kubuntu environment.  Building the debs from 9.3 and installing it manually has yielded a pretty stable system.  Yeah FPS is considerably lower according to glxgears, but I do not notice any change when using googleearth or other 3D programs.  In fact, they ran smoother and faster in 9.3 than in 8.11 (the one included in intrepid).

Create debs manually from here (under manual install): [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide).

I made a bash batch script to run the following commands.  For example, after making the debs from Catalyst 9.3 (8.543):

1) sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb fglrx-kernel-source_8.593-0ubuntu1_amd64.deb fglrx-amdcccle_8.593-0ubuntu1_amd64.deb
2) sudo dpkg-reconfigure -phigh xserver-xorg
3) sudo aticonfig --initial -f

If 3) gives you a message about not being able to detect your card, then you are SOL.  To remove the packages, just sudo dpkg -P names.deb

good luck

Ok thanks I'll try that :D

Edit: Did not work.
But atleast this time the screen started with a message telling me it would not work and not all garbled up

---

### Post by jrusso2 on 2009-05-23
> **sgosnell said:**
> This is an ATI problem, not a Ubuntu problem.  The hardware manufacturer has the responsibility of making the drivers available, or at least the necessary information for open-source developers to make a driver.  The long-term solution is to stop buying anything with an ATI card.

ATI did give the specs to open source their driver a year ago.  That's what all the Open Source Advocates wanted.

---

### Post by deruberhanyok on 2009-05-24
AMD has delivered thousands of pages of documentation to allow development of open source drivers. Cards not supported with the newer catalyst (9.4 and newer) releases - anything earlier than Radeon HD 2x00 series - are already fairly well supported by the open source drivers.

If you have pre HD 2x00 hardware that isn't recognized by the [open source radeon driver]("http://www.x.org/wiki/radeon") then you should contact the developers with the information on your display adapter so that they can add support.

The open source support for the cards pre HD 2x00 series is really quite good. The Catalyst drivers really aren't needed for them anymore.

Open source support for the HD 2x00 series and up are being added to both radeon and [radeonhd]("http://www.x.org/wiki/radeonhd").

Keep in mind that some Radeon HD 2000 series devices (I believe 2100 and 2300 but I'm not 100% certain about that) are based on the older r500 architecture and so if you are experiencing a problem where Catalyst doesn't recognize them that may be the reason (r500 support was dropped in Catalyst 9.4).

As for newer devices not being supported, well, that is being added all the time. But if you have a device that isn't recognized, I'd very much suggest contact the radeon or radeonhd developers, or both, to get device ID numbers and such added to the open source drivers. Everyone benefits from users doing this.

---

### Post by ssri on 2009-05-24
> **deruberhanyok said:**
> AMD has delivered thousands of pages of documentation to allow development of open source drivers. Cards not supported with the newer catalyst (9.4 and newer) releases - anything earlier than Radeon HD 2x00 series - are already fairly well supported by the open source drivers.

If you have pre HD 2x00 hardware that isn't recognized by the [open source radeon driver]("http://www.x.org/wiki/radeon") then you should contact the developers with the information on your display adapter so that they can add support.

When you said fairly well supported, did you mean video tearing, horizontal lines and refresh issues that crop up with my supposedly fairly supported mobility radeon x2300 (RV575/M64)?  Yeah, I played around with xorg.conf (accelmethods, migrationheuristics, etc) after the default one netted me the errors I listed above.  The opensource drivers included in Jaunty (6.12.0) and one that appeared shortly after (6.12.1) in launchpad ppa's did not improve anything.  Transparency effects in kwin are convenient when analyzing sequential medical image sets for my research, so please do not tell me that I just need to switch off desktop effects in order to have the opensource drivers "working" properly.

I am not blaming the driver devs since they have a monumental task ahead of them.  I question ATI's and Canonical's collective wisdom in not seeing the breakage that will occur after dropping support in Catalyst 9.4 and pushing out Xorg 1.6, respectively, before the opensource drivers were close to parity with their proprietary counterparts.  So, please none of this "all is well" message that will ultimately confuse and alienate ATI users.  

My advice is to everyone is to download the livecd to determine whether the included drivers just work.  If not, keep your stable install.  Or, for the more adventurous, test the latest versions of the opensource drivers (from git) on your stable install, and rollback to the previous driver, open or proprietary, if their performance is not up to par.

---

### Post by tommo12 on 2009-05-25
Please ATI get your Drivers working better, Its really bad having dodgy video playback. It makes me cry its so bad sometimes. Its the least you can do considering we are still supporting your products even though we know they are less compatible than other brands.

---

### Post by redjam on 2009-05-25
Does anyone know if replacing my existing ATI card with a new card would fix my newly upgraded (and now broken) 9.04 system? (I have a black screen when I get to login).

Thanks for any help.

---

### Post by PGHammer on 2009-05-25
> **ssri said:**
> When you said fairly well supported, did you mean video tearing, horizontal lines and refresh issues that crop up with my supposedly fairly supported mobility radeon x2300 (RV575/M64)?  Yeah, I played around with xorg.conf (accelmethods, migrationheuristics, etc) after the default one netted me the errors I listed above.  The opensource drivers included in Jaunty (6.12.0) and one that appeared shortly after (6.12.1) in launchpad ppa's did not improve anything.  Transparency effects in kwin are convenient when analyzing sequential medical image sets for my research, so please do not tell me that I just need to switch off desktop effects in order to have the opensource drivers "working" properly.

I am not blaming the driver devs since they have a monumental task ahead of them.  I question ATI's and Canonical's collective wisdom in not seeing the breakage that will occur after dropping support in Catalyst 9.4 and pushing out Xorg 1.6, respectively, before the opensource drivers were close to parity with their proprietary counterparts.  So, please none of this "all is well" message that will ultimately confuse and alienate ATI users.  

My advice is to everyone is to download the livecd to determine whether the included drivers just work.  If not, keep your stable install.  Or, for the more adventurous, test the latest versions of the opensource drivers (from git) on your stable install, and rollback to the previous driver, open or proprietary, if their performance is not up to par.

I have had NO such issues with the Catalyst 9.4 (fglrx) drivers in any *buntu for which they were available (Hardy, Intrepid, and now Jaunty); and my situation was further compounded by my monitor NOT being Plug and Play (IE: compatible with the DDC1/2B specification, which all operating systems, including the open-source ones, support), and I have the HD3450 (PCIe 256 MB).  The issues I *was* having (support of the same resolution and refresh-rates as Windows) were corrected when I replaced the display itself, as my new Acer H233H.bmid is connected digitally via DVI-D dual-link (which *buntu and Catalyst support), which means I have the same drop-dead gorgeous 1920x1080 non-interlaced loveliness in *buntu as in Windows (both 64-bit, by the way).

However, I have noticed that the largest number of complaints are from owners of portable computers (laptops and notebooks) and the newest desktop GPUs (HD48xx) more so than the older GPUs (which are supported better by the open-source drivers (radeon and radeonhd).

Here's my general Advice Of Thumb for driver selection for AMD GPUs:

1.  For HD2xxx and older, consider the open-source radeon driver *first* (with HD2xxx, consider radeonhd only if the radeon driver doesn't work).
2.  For HD4xxx (especially HD48xx) go with the proprietary driver first *only* if you use compiz or do a lot of gaming/video (Ubuntu Studio users, this means you); otherwise, go with the radeonhd driver if you have HD45xx or less.
3.  For HD3xxx (my own situation), I've found the current fglrx (Catalyst 9.5) drivers in the repositories work just fine with Jaunty 64-bit (in fact, I've used them since Jaunty RC), and I do use Compiz by default.  Surprisingly, I would avoid the open-source radeon *and* radeonhd drivers (while they are great for 2D/3D for HD2xxx and less, and 2D-only for HD4xxx, they just plain blow chunks, in both areas, for HD3xxx, which is why I tried the Catalyst drivers in the first place).

---

### Post by deruberhanyok on 2009-05-26
> **ssri said:**
> When you said fairly well supported, did you mean video tearing, horizontal lines and refresh issues that crop up with my supposedly fairly supported mobility radeon x2300 (RV575/M64)?

I'm not familiar with that spin of the r500 architecture. Have you contacted the devs behind the radeon (not radeonhd) driver with info from your display adapter?

> so please do not tell me that I just need to switch off desktop effects in order to have the opensource drivers "working" properly.

I wasn't go to suggest that. I think it's a band aid on the bugs, a crummy solution at best, and I've been annoyed when that has appeared the only option in my own troubleshooting. My understanding of things is that there will be much larger gains in performance and stability when all of the current work (DRI2, KMS, GEM, etc) starts showing up in the mainstream kernel and such, which I believe is with 2.6.31.

That said, your combativeness is appreciated. :)

> I question ATI's and Canonical's collective wisdom in not seeing the breakage that will occur after dropping support in Catalyst 9.4 and pushing out Xorg 1.6, respectively, before the opensource drivers were close to parity with their proprietary counterparts.

If they'd waited for parity with the fglrx drivers we'd probably never have seen this happen. I agree that this could have been delayed a little longer - 9.6 or 9.7 maybe, to allow for the current iterations of the major distros to release and hit the development cycle of the next ones - but in much the same way that Canonical decided to push Compiz enabled by default when people said it wasn't ready, this was done now and they'll sort out the kinks with time.

Although I don't think Canonical was really involved in ATI's decision to do this. Support for the older hardware was also removed from the Windows drivers starting with Catalyst 9.4, so it seems that was something ATI wanted to do all around.

> So, please none of this "all is well" message that will ultimately confuse and alienate ATI users.

As you've pointed out, "fairly well supported" is not "all is well." If this sarcasm has made you feel better, however, then I guess I've helped in some way.

---

### Post by gary987 on 2009-07-06
Little slow on the bandwagon here... I was trying out the open source drivers.


For what its worth... 

The radeon 2100

is not working on radeonhd driver.
works on radeon, but 3D rendering still has some serious performance issues.


As for the ati catalyst driver... sure I can use 9.3, but they still don't have a patch to use with newer kernels (2.6.29) C'mon ati, this is even pitiful for you!

---

### Post by jb510 on 2009-07-08
This seems to be the best thread... but since this is a long post I'll start with my question...

Simple question: For an ATI X1400 (in a Acer 5672 Laptop) should I/can I use the Radeon or RadeonHD driver under Unbuntu 9.04?

Longer story:

I've been running Ubuntu via VMWare on my mac for a while to test it out, and I used Unix back in the early 90's (wow I'm getting old), but generally I'm still a linux newbie. 

Anyway, I have a Acer 5672 (ATI x1400 Mobility) which is attached to my TV as a media server.  I use it for playing/downloading media and generally access it via VNC.  Regardless last month it got fubar'd due to a nasty virus (rootkit/tojans/the whole nine yards).  Anyway, I finally had to give up removing it and decided to reinstall windows on a new hard drive, it was time anyway.  It  seemed like a perfect time to also install Ubuntu 9.04 as a dual boot, something I've wanted to do for a year or more.  Well after 3 days of googling and fiddling to get video and SPDIF audio out working, I'm more than a little frustrated.

The first thing I tried to do was setup dual monitors and found the default driver wouldn't do what I wanted, so I installed the ATI drivers from the ATI website. (note the x1400 is NOT listed on thier discontinued support page, but any idiot would guess that when the entire rest of the x1k line is discountinued, so would the x1400).  I not being an idiot, at least at this momment, relaized this but figured there would be no harm in trying... wrong...  couldn't boot into the desktop due to corrupted video.  Uninstalling the messed up fglrx install proved nearly impossible.  I found and ran an uninstall/remove script at command line in recovery mode finally worked.  

At this point I have to say that both ATI and Canonical screwed up.

After the script removed fglrx drivers I could login, but still had some problems so sine I didn't have much useful invested in the install at this point, so I did a fresh install...  how very MS Windows that felt.

All of this began simply because I needed a way to configure dual monitors and I thought something other than the default driver would do this better.   I want the menu bar on my laptop (right screen) and the TV (left screen) the second extended monitor.  This is so I can run things as I did in windows where menus/apps show up on the laptop screen (which I actually access via VNC) and my video output displays on the TV.  Maybe this has nothing to do with drivers and I need something else (twinview??).

Anyway...  again I'm still left wondering if I should use Radeon or RadeonHD?

---

### Post by Mark Phelps on 2009-07-08
You would do much better starting your own thread on multiple monitors, since your question really has nothing to do with petitioning ATI or Canonical, and folks who know how to handle multiple monitors are not likely to read this thread.

Also, unless you're running an "HD" card, I doubt that the radeonhd driver would work ... but you never know.

---

### Post by schnelle on 2009-07-08
Never an ATI again! I have bought laptop first, and then I have discavered wonders of (K)Ubuntu. But then was to late, and I am stuck now with ATI Mobility Radeon HD 2400. With fglrx driver i cannot play videos well, with radeon video works but everything else don't or sucks.
Yesterday I installed Kubuntu Jaunty on mine friend's ancient pc with geforce 6200. WOW! Desktop effects and everything else works out of box.
So I am waiting Ubuntu 9.10 and 3D support in opensource driver... if it sucks... bye bye ATI.

---

### Post by Crystal7769 on 2009-07-08
It may or may not be of some interest to this forum, but NVidia bought out ATI some many months ago, same as TigerDirect bought out CompUSA due to the economy.  As for drivers and Linux, the problem isn't with the manufacturers, who could care less for this forum; it is for money...plain & simple, and M/S and Bill Gates still have their undivided attention.
On a separate note, I've just tried to install 9.04 or 8.04.1 on my AMD 64 machine, with NVidia M/B but doesn't seem to want to work and won't boot from "go" even after disabling "OS Plug 'N Play" option in Bios...any ideas where and how I can get some help here??
Crystal7769 could use your help here....):P

---

### Post by jb510 on 2009-07-08
> **Crystal7769 said:**
> It may or may not be of some interest to this forum, but NVidia bought out ATI some many months ago, same as TigerDirect bought out CompUSA due to the economy.
I think you're confused.  AMD bought ATI some years ago (2006).  

> On a separate note, I've just tried to install 9.04 or 8.04.1 on my AMD 64 machine, with NVidia M/B but doesn't seem to want to work and won't boot from "go" even after disabling "OS Plug 'N Play" option in Bios...any ideas where and how I can get some help here??
Crystal7769 could use your help here....):P
Wow, I knew I thought I was a little OT...  

@Mark Phelps - I will research existing threads on multiple monitors, and maybe start one if necessary regarding the multiple monitor question, however I was asking in this thread "What is the best alternative driver until ATI listens to our entreaties for a 9.04 compatible driver?" which seemed relevant.  

I'm just hoping either Canoncial or ATI comes up with a solution, either by offering a rollback to xserver 1.5 under 9.04, or ATI offer a 9.X driver that works with 1.6 (I hope I have the version numbers right, going from memory)

---

### Post by Derviansoul on 2009-07-08
> **chudak said:**
> I sent them email from their support form to complain. I'd suggest that others do the same. My 2 year old T60 with a Mobility Radeon X1400 had support dropped in the new driver. This is inexcusable.

If they fail to respond to this situation I'd suggest that people rethink the purchases of ATI video cards or laptops containing them. It really pisses me off that a two year old laptop that cost upwards of $2k is now unsupported by the manufacturer of one of the primary components.

Me too i two X1300 on two computers and now i had to replace them for an nvidia since there is no support for the card with the new driver. As far as it concerns me i will never buy nothing of amd ever again. Maybe if the whole linux community do not buys amd cards, maybe then they will have some respect to the costumers then.

By the way, i only have a cheap nvidia card, and the difference in quality and stability is enormous, even when playing x264 720p movies, there is no framing in the movie. Kde does not crashes as much as before. 

Best regards.

---

### Post by jrusso2 on 2009-07-08
> **sgosnell said:**
> This is an ATI problem, not a Ubuntu problem.  The hardware manufacturer has the responsibility of making the drivers available, or at least the necessary information for open-source developers to make a driver.  The long-term solution is to stop buying anything with an ATI card.

How come no one seems to know that ATI gave the open source community the specs to produce an open source driver over a year ago?

What has not happened is the open source community has not finished a suitable driver yet.

---

### Post by jrusso2 on 2009-07-08
> **Crystal7769 said:**
> It may or may not be of some interest to this forum, but NVidia bought out ATI some many months ago, same as TigerDirect bought out CompUSA due to the economy.  As for drivers and Linux, the problem isn't with the manufacturers, who could care less for this forum; it is for money...plain & simple, and M/S and Bill Gates still have their undivided attention.
On a separate note, I've just tried to install 9.04 or 8.04.1 on my AMD 64 machine, with NVidia M/B but doesn't seem to want to work and won't boot from "go" even after disabling "OS Plug 'N Play" option in Bios...any ideas where and how I can get some help here??
Crystal7769 could use your help here....):P

AMD bought out ATI over a year ago.  Nvidia owning ATI?  Not sure where you heard that one.

---

### Post by Derviansoul on 2009-07-09
> **jrusso2 said:**
> How come no one seems to know that ATI gave the open source community the specs to produce an open source driver over a year ago?

What has not happened is the open source community has not finished a suitable driver yet.

If we pay for a product we should have support for it, an open source driver will never be as good or as stable as the one that hardware manufacter will produce, since ati as quite a few products every year with different characteristics, it would be impossible for the opensource community release an updated and stable driver, with the same pace as the ati was launching one.

What the opensource community should focus, would be in somehow a way that would force manufacters to provide at least binaries for linux, that would allow distribution to create packages.

Best Regards

---

### Post by racerraul on 2009-07-09
> **jrusso2 said:**
> How come no one seems to know that ATI gave the open source community the specs to produce an open source driver over a year ago?

What has not happened is the open source community has not finished a suitable driver yet.

To the best of my knowledge, they only released docs to the open source community for legacy unsupported chipsets.  For those the opensourcce driver even support 3d accel...

for the latest chipsets, AMD\ATI has not released everything if anything at all.

---

### Post by sdowney717 on 2009-07-09
yeah, mad, very mad about it. I paid a lot of money on ebay for this used x1300 256mb agp card. I got it for 13$ and you cant even use it properly. Now I keep an eye out for a used nvidia on the cheap. I will never buy another cheap ATI card again. the whole experience is ghoulish.

---

### Post by [h2o] on 2009-07-09
> **racerraul said:**
> To the best of my knowledge, they only released docs to the open source community for legacy unsupported chipsets.  For those the opensourcce driver even support 3d accel...

for the latest chipsets, AMD\ATI has not released everything if anything at all.

That is simply not true. You can check for yourself here:
[http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)

Notice how a lot of these documents mention r6xx and r7xx which are the latest chipsets.

---

### Post by racerraul on 2009-07-09
> **'[h2o] said:**
> That is simply not true. You can check for yourself here:
[http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)

Notice how a lot of these documents mention r6xx and r7xx which are the latest chipsets.

I see, they just recently released more docs 2 months ago... so I wasn't entirely wrong.
[http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

In any case... not enough time for the open source community to make any significant ground with HW accel...

Good News nonetheless...

---

### Post by jb510 on 2009-07-09
> **jrusso2 said:**
> How come no one seems to know that ATI gave the open source community the specs to produce an open source driver over a year ago?

What has not happened is the open source community has not finished a suitable driver yet.

Releasing the SPECS and releasing the SOURCE are very different things.  What the open source community needs is the source to work with, not to have to start at scratch based solely on the specs.  I thought ATI had released some of their source but could not release it all as as some of it is licensed proprietary tech.

Regardless expecting the open source community to write a complex video driver from scratch based the published specs alone in a year, let alone a few months, is overly optimistic.

---

### Post by jb510 on 2009-07-09
Not sure it'll do any good... but...  I noticed on the ATI Linux page, [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx) under helpful links there is a link to SEND FEEDBACK TO THE LINUX CREW.

[http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36](http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36)

I filled it out and in the end there is a comment section where I complained about dropping support prior to have a Ubuntu 9.04 / Xorg 1.6 compatiable driver...

---

### Post by aouie on 2009-07-09
I can't play the games on Ubuntu 9.04 that I used to on Ubuntu 8.10 with ATI x1950GT. With the Open Source drivers I finally have good vertical sync for watching videos on the Linux side.  I can still use a dual head, and just configured it to support 1920x1080 on one monitor and 1280x1024 on the other (wish better instructions were available).

It is still not good of AMD to drop the support relatively soon on the X1k series. Ideally, they would pay some people to work on the Open Source drivers into the longer term. Over the years, I would expect older ATI cards to work better on the newer Gnu / Linux OSes than with older NVidia cards. For now, I settle for doing most of my gaming on the MS Windows XP OS.

Sincerely,
Aouie

---

### Post by [h2o] on 2009-07-10
> **racerraul said:**
> I see, they just recently released more docs 2 months ago... so I wasn't entirely wrong.
[http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

In any case... not enough time for the open source community to make any significant ground with HW accel...
No but at least they are giving out their specs so that a good open source driver is possible. Compared to nvidias linux policies lately I know where I am shopping for GPUs in the next few years. :)

---

### Post by rob12424 on 2009-10-27
Maybe it is a better option and possible to ask to amd/ati and or nvidia if they can release the source of the old drivers!? Even if there is a patent or something secret maybe it is for them an option to release a driver in more then one package to for example:

Core package (different for each card and only not supported anymore released so sourcecode released by AMD/ATi)

Central package (only released By AMD/ATI but card indipended)

Extra feateres Package (different for each card and only not supported anymore so sourcecode released by AMD/ATi for example cross fire technologie)

They can´t support a card for eternity but if you do suggestions they maybe are willing to take it!

I have a ati radeon 9800 pro se By the way and find the open source drivers far more better!! Does anyone know the command for getting back-up from Xserver? : I thought it whas: Sudo apt-get dpkg --reinstall xserver.org -f but I´m not sure!?

---

### Post by Tesla Trooper on 2009-11-19
Ok, nothing has changed, AMD still brain dead, FOSS still silent and weak.
my A+ course instructor is a Window$ fan, he just keep mocking and telling me that Linux and all opensource gonna be extinct during the next five years, due to "some activities" that Micro$oft doing right now, which still far away from the web audience.. as we see, hardware manufacturers are significantly dropping Linux support.. Nvidia is not much better then AMD.
Petitions are useless now, contracts are much stronger then petitions. and even if one of them responded, they gonna tell you: "unfortunately, we doesn't support your operating system, go bite the dust"
FOSS better start making their own hardware that doesn't support windows..[COLOR=Blue]
[/COLOR]

---

### Post by mivo on 2009-11-19
Why bring Windows and MS into the discussion? AMD/ATI's poor decisions have nothing to do with it. Try to understand that MS has no reason to be worried of the "less than 1%" desktop market share of Linux. It has stagnated for a while now, too.  This is AMD/ATI's doing, probably to lower support and development costs.

FOSS is popular on Windows as well. Firefox, Open Office, Thunderbird, Pidgin, VLC, Python, etc. Far more people use them on Windows than on Linux (in absolute numbers, not percentages).

---

### Post by Grenage on 2009-11-19
> **Tesla Trooper said:**
> Ok, nothing has changed, AMD still brain dead, FOSS still silent and weak.
my A+ course instructor is a Window$ fan, he just keep mocking and telling me that Linux and all opensource gonna be extinct during the next five years, due to "some activities" that Micro$oft doing right now, which still far away from the web audience.. as we see, hardware manufacturers are significantly dropping Linux support.. Nvidia is not much better then AMD.
Petitions are useless now, contracts are much stronger then petitions. and even if one of them responded, they gonna tell you: "unfortunately, we doesn't support your operating system, go bite the dust"
FOSS better start making their own hardware that doesn't support windows..[COLOR=Blue]
[/COLOR]

Linux driver support has improved over the years, what on earth are you talking about?

---

